# 🔧 SOC Integration – ISMS Embedded in Operations

**Document ID:** SN-SOC-001  
**Version:** 1.0  
**Classification:** Internal  
**Owner:** SOC Manager / CISO  
**Approved by:** CISO  
**Last Reviewed:** 2025-01-15  

---

## 1. Overview

This document demonstrates how ISO 27001:2022 controls are embedded in SecureNusantara's
day-to-day SOC operations — not as a paper exercise, but as operational reality.

The goal is to show **Compliance ≠ Paper. Compliance = Operations.**

---

## 2. SOC Alert Lifecycle (ISO 27001 Control Touchpoints)

```
External Threat / Internal Event
           │
           ▼
    ┌──────────────────────────────────────────────────────────┐
    │  WAZUH SIEM (A.8.15 – Logging / A.8.16 – Monitoring)    │
    │  • Collects logs from: endpoints, servers, firewalls,    │
    │    cloud (CloudTrail, Azure Monitor), network devices     │
    │  • Applies detection rules (custom + OOTB)               │
    │  • Generates alert → webhook to Shuffle                  │
    └───────────────────────┬──────────────────────────────────┘
                            │
                            ▼
    ┌──────────────────────────────────────────────────────────┐
    │  SHUFFLE SOAR (A.5.7 – Threat Intelligence integration)  │
    │  Automated enrichment:                                   │
    │  • MISP IOC lookup (IP, domain, hash)                    │
    │  • AbuseIPDB reputation score                            │
    │  • CMDB asset lookup (Confluence API)                    │
    │  • Azure AD user info (account status, department)       │
    │  • Deduplication check (TheHive existing cases)          │
    │  Creates/updates TheHive alert with enriched context     │
    └───────────────────────┬──────────────────────────────────┘
                            │
                            ▼
    ┌──────────────────────────────────────────────────────────┐
    │  THEHIVE CASE MANAGEMENT (A.5.25 – Assessment of events) │
    │  Tier 1 triage:                                          │
    │  • Classify: FP / Informational / Incident               │
    │  • Assign severity: P1 / P2 / P3 / P4                   │
    │  • Document triage reasoning                             │
    │  • Escalate to T2 if incident                            │
    └───────────────────────┬──────────────────────────────────┘
                            │
                  ┌─────────▼──────────┐
                  │  P1/P2 Incident?   │
                  └─────────┬──────────┘
                        Yes │            No → Close / Monitor
                            ▼
    ┌──────────────────────────────────────────────────────────┐
    │  INCIDENT RESPONSE (A.5.26 – Response to IS incidents)   │
    │  T2/T3 investigation:                                    │
    │  • MITRE ATT&CK mapping                                  │
    │  • Evidence collection (A.5.28)                          │
    │  • Containment actions via Shuffle playbooks             │
    │  • Client notification (SLA-driven)                      │
    │  • NACSA notification if qualifying (Act 854, T+6h)      │
    │  • Recovery and eradication                              │
    └───────────────────────┬──────────────────────────────────┘
                            │
                            ▼
    ┌──────────────────────────────────────────────────────────┐
    │  POST-INCIDENT REVIEW (A.5.27 – Learning from incidents) │
    │  • Root cause analysis                                   │
    │  • Wazuh rule updates (detection improvement)            │
    │  • Corrective actions tracked in Jira                    │
    │  • Threat intel contribution to MISP                     │
    └──────────────────────────────────────────────────────────┘
```

---

## 3. Vulnerability Management Process

### 3.1 Weekly Scan Cycle

```
Monday: Nessus credentialed scan (internal + client environments)
          │
          ▼
    Nessus exports to SecureNusantara vulnerability management Jira project
          │
          ▼
    Shuffle playbook: auto-create Jira tickets for Critical/High CVEs
    with:
    • CVE details and CVSS score
    • Affected asset (from CMDB)
    • Asset owner (from CMDB)
    • Patch SLA (Critical: 30d, High: 90d, Medium: 180d)
          │
          ▼
    Asset owner notified via Jira ticket
          │
          ▼
    Patch applied → Jira ticket updated → Verification scan
          │
          ▼
    Overdue tickets → Jira SLA breach flag → SOC Manager escalation
          │
          ▼
    Monthly: Grafana vulnerability KPI dashboard updated
```

### 3.2 ISO 27001 Controls Demonstrated

| Process Step | ISO Control | Evidence |
|-------------|-------------|---------|
| Continuous scanning | A.8.8 – Technical vulnerability management | Nessus scan schedules; reports |
| Asset-linked findings | A.5.9 – Asset inventory | CMDB ↔ Nessus integration |
| SLA-driven patching | A.8.8 | Jira SLA tracking |
| Management reporting | A.9.1 – Monitoring and measurement | Grafana vulnerability dashboard |

---

## 4. Threat Intelligence Integration

### 4.1 Intelligence Lifecycle

```
OSINT / Commercial Feeds / ISAC Sources
           │
           ▼
    MISP Platform (IOC ingestion + deduplication)
           │
    ┌──────▼──────────────────────────────────┐
    │  TI Analyst processes:                  │
    │  • IOC validation (false positive check) │
    │  • Attribution and context (OpenCTI)     │
    │  • Sector tagging (finance/govt/health)  │
    └──────────────────┬──────────────────────┘
                       │
          ┌────────────┼──────────────────┐
          │            │                  │
          ▼            ▼                  ▼
    Wazuh SIEM   Shuffle SOAR      Client Threat
    (detection    (alert           Bulletin
    rules update) enrichment)      (monthly)
```

### 4.2 IOC Lifecycle in MISP

| Stage | Action | Tool |
|-------|--------|------|
| Ingestion | Pull from threat feeds (AlienVault OTX, Abuse.ch, etc.) | MISP feeds |
| Validation | TI analyst reviews; tags with sector/confidence | MISP |
| Distribution | Push to Shuffle for enrichment; push to Wazuh for detection | MISP → Shuffle → Wazuh |
| Expiry | IOCs expire after 30/90/180 days based on confidence | MISP TTL |
| Contribution | Novel IOCs from SecureNusantara incidents shared (with client consent) | MISP community sharing |

### 4.3 ISO 27001 Controls Demonstrated

| Activity | ISO Control |
|----------|-------------|
| TI ingestion and analysis | A.5.7 – Threat intelligence |
| IOC-based detection in Wazuh | A.8.16 – Monitoring activities |
| Sector-specific client bulletins | A.5.6 – Contact with special interest groups |
| MITRE ATT&CK TTP mapping | A.5.25 – Assessment of IS events |

---

## 5. Automation Workflows (Shuffle SOAR)

### 5.1 Key Playbooks in Production

| Playbook | Trigger | Actions | ISO Control |
|----------|---------|---------|-------------|
| **Alert Enrichment** | Any new Wazuh alert | MISP, AbuseIPDB, CMDB, Azure AD lookup → TheHive alert | A.5.25 |
| **Credential Compromise** | Wazuh rule: successful login after multiple failures from malicious IP | Azure AD account disable → TheHive case → Client notification email → Slack alert to SOC | A.5.26 |
| **Critical Vulnerability** | Nessus: Critical CVE found | Jira ticket creation → Asset owner notification → CISO alert | A.8.8 |
| **NACSA Notification** | P1 incident classified | Generate NACSA notification template → GRC email → Reminder at T+5h if not sent | A.5.26 |
| **Firewall Block** | Confirmed C2 / malicious IP (high confidence) | Firewall API call → Block IP → Log to TheHive → Notify analyst | A.8.20 |
| **Evidence Collection** | P1 incident declared | Trigger memory dump on affected endpoint → Upload to evidence store → Create TheHive task | A.5.28 |
| **PIR Reminder** | Incident closed (P1/P2) | Create TheHive PIR task → Assign to T2 Lead → Set due date (5 working days) | A.5.27 |

### 5.2 Automation Coverage

| Alert Type | Volume (monthly) | Automated % | Manual Review % |
|-----------|-----------------|-------------|----------------|
| Failed login (non-malicious pattern) | ~1,800 | 95% auto-closed | 5% T1 review |
| Successful login from known malicious IP | ~50 | 70% automated | 30% T1 → T2 |
| File integrity change (FIM) | ~500 | 85% auto-classified | 15% T1 |
| Critical vulnerability found | ~25 | 100% Jira ticket auto-created | T2 validates |
| Suspicious process execution | ~120 | 60% enriched | 40% T1 → T2 |
| Port scan detected | ~200 | 90% auto-closed (external) | 10% T1 |

> **Reality check:** Even with SOAR, manual analyst capacity is the constraining factor.
> The 65% false positive rate means analysts are still spending significant time on noise.
> Target for FY2025: reduce FP rate to 30% through continued Wazuh rule tuning and SOAR
> playbook expansion. This is not just an operational metric — it's an ISO A.8.8 and A.8.16
> control effectiveness measure.

---

## 6. Critical Thinking: Does ISO 27001 Make SecureNusantara More Secure?

### 6.1 The Honest Assessment

**What ISO 27001 certification has improved:**
- Formalised risk management — previously ad hoc; now systematic
- Documentation of procedures — SOC analysts now follow written runbooks
- Supplier management — previously no formal assessment; now has structure
- Management attention — CISO now has board visibility for security investments
- Client confidence — government tenders require ISO 27001; certification directly supports revenue

**What ISO 27001 certification has NOT (yet) improved:**
- Alert fatigue (FP rate 65%) — structural problem requiring SOAR investment, not a paperwork problem
- Staff retention — no framework fixes talent market competition
- Threat landscape exposure — being an MSSP makes SecureNusantara a high-value target regardless

### 6.2 ISO 27001 vs. Alternatives

| Framework | Strengths | Weaknesses | Fit for MSSP |
|-----------|-----------|-----------|--------------|
| **ISO 27001** | International recognition; comprehensive ISMS; client-required | Process-focused; not outcome-focused; expensive to maintain | ✅ High (client procurement) |
| **SOC 2 Type II** | Operational effectiveness focus; US market recognition | Less known in Malaysia; audit cost | 🔵 Medium (future consideration) |
| **CREST Membership** | Specific to offensive/defensive security services | Narrow scope; not comprehensive ISMS | 🔵 Medium (complementary) |
| **Custom framework** | Tailored to MSSP specifics | Not externally verifiable; clients won't accept | ❌ Low |

**SecureNusantara's position:** ISO 27001 is the right choice for the Malaysian market.
SOC 2 Type II should be considered for FY2026 as the company targets international clients.

### 6.3 Compliance ≠ Security

> *"Compliance is the floor, not the ceiling."*

The most dangerous outcome of ISO 27001 certification is believing that compliance means
security. SecureNusantara's leadership has been explicitly briefed:

- Certification validates **process maturity**, not **absence of breaches**
- The threat landscape evolves faster than annual certification cycles
- Continuous improvement (Clause 10) is not optional — it's the mechanism that keeps
  the ISMS relevant
- Client SLAs should be based on response capability, not certification status

---

*Document Owner: SOC Manager / CISO | Approved by: CISO | Next Review: 2026-01-15*
