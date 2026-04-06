# 🚨 Incident Response Procedure

**Document ID:** SN-PROC-002  
**Version:** 1.5  
**Classification:** Confidential – Internal  
**Owner:** SOC Manager / CISO  
**Approved by:** CISO  
**Last Reviewed:** 2025-01-15  
**Next Review:** 2026-01-15  

---

## 1. Purpose & Scope

This procedure provides step-by-step guidance for SOC analysts and incident commanders
to handle information security incidents from detection through closure. It implements
the Incident Response Policy (SN-POL-003).

---

## 2. Incident Lifecycle Overview

```
     WAZUH ALERT
          │
          ▼
    ┌─────────────┐
    │  T1 TRIAGE  │─── False positive? ──► Close alert in TheHive
    │  (15 min)   │
    └──────┬──────┘
           │ Qualified alert
           ▼
    ┌─────────────┐
    │ T2 ANALYSIS │─── Informational? ──► Log in TheHive; no IR
    │  (60 min)   │
    └──────┬──────┘
           │ Confirmed/suspected incident
           ▼
    ┌─────────────────┐
    │ INCIDENT         │
    │ CLASSIFICATION   │◄── Assign P1/P2/P3/P4
    │ & COMMANDER      │
    └──────┬──────────┘
           │
    ┌──────▼──────────────────────────────┐
    │           IR WORKFLOW               │
    │  Contain → Investigate → Eradicate  │
    │  → Recover → Post-Incident Review   │
    └─────────────────────────────────────┘
```

---

## 3. Phase 1: Detection & Triage (Tier 1)

### 3.1 Wazuh Alert → TheHive

Shuffle SOAR automatically:
1. Receives Wazuh alert via webhook
2. Enriches alert with: IP reputation (MISP/AbuseIPDB), asset info (CMDB lookup), user info (Azure AD)
3. Deduplicates against open TheHive alerts (same IP/rule within 1 hour)
4. Creates TheHive alert with enriched context

**Tier 1 Action (within 15 minutes of alert creation):**

| Decision | Action |
|----------|--------|
| False positive (known benign activity) | Close TheHive alert with reason; update Wazuh exclusion if recurring |
| Informational (no threat action required) | Acknowledge; add observation note; close |
| Suspicious / unresolved | Escalate to Tier 2; promote to Case in TheHive |
| Critical (ransomware, active exfil, known IOC) | Immediate escalation to T2 + SOC Manager; classify P1 |

### 3.2 Tier 1 Triage Checklist (TheHive)

- [ ] Alert source and rule ID reviewed
- [ ] Asset identified in CMDB (client/internal)
- [ ] User/account identified and checked in Azure AD
- [ ] MISP IOC lookup completed (via Shuffle enrichment)
- [ ] AbuseIPDB score checked for external IPs
- [ ] Alert disposition: FP / Informational / Escalate
- [ ] TheHive case created and assigned to T2 (if escalating)
- [ ] Client notified (for P1 client incidents — T1 sends template notification)

---

## 4. Phase 2: Analysis & Investigation (Tier 2)

### 4.1 Case Investigation Steps

1. **Review the TheHive case** — read T1 triage notes and enriched context
2. **Expand Wazuh query** — search for related events: same source IP, same user, same host (24h window)
3. **Review SIEM timeline** — construct event timeline in TheHive tasks
4. **Check OpenCTI** — look for threat actor or campaign associations
5. **Correlate logs** — cross-reference firewall, proxy, endpoint logs (Wazuh agents)
6. **Classify incident** — confirm severity: P1 / P2 / P3 / P4

### 4.2 MITRE ATT&CK Mapping

All P1/P2 incidents must be mapped to MITRE ATT&CK techniques:
- Identify tactics, techniques, and sub-techniques observed
- Record in TheHive case (custom field: `mitre_techniques`)
- Used for: threat intelligence contribution, client reporting, SOC improvement

### 4.3 Client Notification (P1/P2 — Client Environment)

T2 analyst (or SOC Manager if T2 is unavailable) sends initial notification to client:

> **Subject:** [SECURENUSANTARA SOC] Security Incident Alert – [Client Name] – [Severity]  
> **Body:**  
> Dear [Client Contact],  
> We have detected a potential security incident in your environment. Our SOC team is actively investigating.  
> **Incident ID:** [TheHive case ID]  
> **Detected:** [Timestamp UTC+8]  
> **Severity:** [P1/P2]  
> **Initial observations:** [2–3 sentence factual summary — no speculation]  
> We will provide an update within [1 hour for P1 / 2 hours for P2].  
> Do not take any remediation actions without coordinating with our team.  
> **Incident Hotline:** +60-3-XXXX-XXXX

---

## 5. Phase 3: Containment

### 5.1 Containment Actions (Examples by Scenario)

| Scenario | Containment Action | Tool |
|----------|-------------------|------|
| Compromised endpoint (malware) | Isolate endpoint from network (quarantine in EDR) | Wazuh active response |
| Compromised user account | Disable Azure AD account; reset password; revoke sessions | Azure AD |
| Suspicious external IP (active connection) | Block IP at firewall (emergency change, CAB waiver) | Firewall API via Shuffle |
| Ransomware spreading | Isolate affected network segment (VLAN block) | Network switch via change |
| C2 communication detected | Null-route C2 domain in DNS filtering | DNS filter |
| Data exfiltration in progress | Block outbound traffic on affected host; preserve logs | Firewall + Wazuh |

### 5.2 Evidence Preservation Before Containment

> ⚠️ **Always collect evidence BEFORE containment where feasible:**
> - Memory dump of affected host (Volatility, WinPMEM)
> - Network traffic capture (tcpdump)
> - Full disk image if legally required
> - Screenshots of active sessions

Evidence must be documented in TheHive with chain of custody:
- SHA256 hash of all forensic images
- Collector name, timestamp, and storage location

---

## 6. Phase 4: Eradication

1. Identify and remove all traces of the threat:
   - Malware files removed; registry entries cleaned
   - Backdoor accounts identified and removed
   - Compromised credentials reset across all systems
   - Malicious scheduled tasks/services removed
2. Root cause identified (see Phase 6 PIR for formal analysis)
3. Patch or configuration fix applied (emergency change via CAB waiver for P1)
4. All eradication steps documented in TheHive tasks

---

## 7. Phase 5: Recovery

1. Restore affected systems from clean backup (verify backup integrity first)
2. Enhanced monitoring applied to recovered systems (Wazuh watchlist)
3. Confirm business functionality restored with asset owner
4. Client sign-off obtained (for client-environment incidents) before monitoring normalises
5. NACSA final report submitted (if applicable) — within 72 hours of initial notification

---

## 8. NACSA Notification Procedure (Act 854)

For incidents qualifying as "significant cybersecurity incidents" under Act 854:

| Notification | Timeframe | Channel | Content |
|-------------|-----------|---------|---------|
| Initial notification | T+6h from detection | NACSA portal / email | Incident ID, brief description, affected systems, initial impact |
| Full report | T+72h | NACSA portal | Full incident timeline, impact assessment, containment actions, root cause |
| Final closure report | T+30 days | NACSA portal | Full PIR findings, corrective actions, recurrence prevention |

---

## 9. Phase 6: Post-Incident Review (PIR)

For all P1 and P2 incidents (mandatory within 5 working days):

**PIR Agenda:**
1. Incident timeline reconstruction (minute-by-minute for P1)
2. 5-Why root cause analysis
3. Effectiveness of detection: Was the alert tuned correctly? Was MTTD within target?
4. Effectiveness of response: Was MTTR within SLA? Were runbooks sufficient?
5. Communication: Were client/NACSA notifications timely and accurate?
6. Lessons learned: What should change in tools, procedures, or training?
7. Corrective actions: Owner, deadline, Jira ticket

**PIR Report** stored in Confluence under: `ISMS > Incident Management > PIR Reports`

---

## 10. Real Scenario Example: Phishing → Credential Compromise

**Timeline:**

```
09:14 – Wazuh alert: Multiple failed logins for user siti.aminah@client.com.my (rule 2502)
09:15 – Shuffle enrichment: IP 185.x.x.x → AbuseIPDB score 90/100 (malicious)
09:15 – TheHive alert auto-created; assigned to T1 queue
09:22 – T1 reviews alert → successful login from 185.x.x.x 3 min after failed attempts
09:23 – T1 escalates to T2; promotes to Case P2
09:25 – SOC Manager notified; client notified (P2 template email)
09:35 – T2 investigates: user siti.aminah received phishing email 08:55; credentials entered
09:40 – Azure AD: account active; no MFA enabled on client's Azure tenant (client-managed)
09:42 – Containment: SOC requests client AD team disables account immediately
09:55 – Client disables account; session tokens revoked
10:10 – T2: reviews email logs; no exfiltration observed; phishing link to fake M365 portal
10:30 – Eradication: client resets password + enables MFA; phishing URL added to block list
11:00 – Client incident update call; scope confirmed limited to one account
13:00 – P2 → P3 downgraded; enhanced monitoring for 48h
Day+5 – PIR completed; corrective action: recommend MFA enablement to all clients (SN-CA-20250115)
```

---

## 11. Key Metrics (SOC SLA Tracking)

| Metric | Target | Measurement |
|--------|--------|-------------|
| MTTD (Mean Time to Detect) | < 15 min (P1), < 60 min (P2) | Wazuh alert time → TheHive case open |
| MTTA (Mean Time to Acknowledge) | < 15 min | Alert created → T1 first action |
| MTTR (Mean Time to Respond/Contain) | < 4h (P1), < 8h (P2) | Incident open → containment confirmed |
| Client notification SLA | < 1h (P1), < 2h (P2) | Incident classified → client email sent |
| PIR completion | < 5 working days (P1/P2) | Incident closed → PIR submitted |

---

*Document Owner: SOC Manager / CISO | Approved by: CISO | Next Review: 2026-01-15*
