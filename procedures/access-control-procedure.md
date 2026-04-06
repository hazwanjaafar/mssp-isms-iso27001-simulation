# 🔑 Access Control Procedure

**Document ID:** SN-PROC-001  
**Version:** 1.3  
**Classification:** Internal  
**Owner:** IT Operations / CISO  
**Approved by:** CISO  
**Last Reviewed:** 2025-01-15  
**Next Review:** 2026-01-15  

---

## 1. Purpose & Scope

This procedure provides step-by-step guidance for managing user access to SecureNusantara
systems, including provisioning, modification, review, and revocation of access rights.
It implements the Access Control Policy (SN-POL-002).

---

## 2. Procedure: User Onboarding (Access Provisioning)

### 2.1 Trigger
New employee or contractor joining SecureNusantara.

### 2.2 Steps

| Step | Action | Responsible | System | SLA |
|------|--------|------------|--------|-----|
| 1 | HR submits onboarding request in Jira (IT-ONBOARD template) | HR | Jira | Day before start date |
| 2 | IT Operations creates Azure AD account with standard role | IT Operations | Azure AD | Day 1, 09:00 |
| 3 | IT Operations assigns role-based groups per job title | IT Operations | Azure AD | Day 1, 09:00 |
| 4 | MFA enrolment sent to personal email + enforced | IT Operations | Azure AD MFA | Day 1, before first login |
| 5 | Microsoft 365 licence assigned (Jira, Confluence included) | IT Operations | M365 | Day 1 |
| 6 | SOC tool access provisioned (if applicable): Wazuh, TheHive, Shuffle | Platform Eng | Wazuh/TheHive | Day 1–2 |
| 7 | PAM account created for privileged roles (Tier 2+, Platform Eng, Cloud Security) | IT Operations | PAM | Day 1–2 |
| 8 | Laptop and MDM enrolment | IT Operations | Intune/MDM | Day 1 |
| 9 | New user signs AUP and Access Control acknowledgement | HR | DocuSign | Day 1 |
| 10 | Onboarding ticket closed; CISO notified for privileged access provisioning | IT Operations | Jira | Day 2 |

### 2.3 Role-Based Access Groups

| Role | Access Group | Systems |
|------|-------------|---------|
| Tier 1 SOC Analyst | `SOC-T1` | Wazuh (read+triage), TheHive (analyst), Confluence (read) |
| Tier 2 SOC Analyst | `SOC-T2` | Above + Wazuh (advanced), TheHive (investigator), Shuffle (view) |
| Tier 3 SOC Analyst | `SOC-T3` | Above + Wazuh (admin), Shuffle (run), forensics tools |
| Threat Intel Analyst | `TI-Analyst` | MISP (read+submit), OpenCTI (analyst), Confluence |
| Platform Engineer | `PLAT-ENG` | All SOC tools (admin), AWS (developer), Azure (developer) |
| GRC Analyst | `GRC-Analyst` | Confluence (full), Jira (GRC projects), read-only SIEM |
| Cloud Security Eng | `CLOUD-SEC` | AWS Security Hub, Azure Defender, Wazuh (read) |
| Management | `MGMT-READ` | Grafana dashboards, Confluence (read), executive reports |

---

## 3. Procedure: Access Modification

### 3.1 Trigger
Employee changes role, department, or project assignment.

### 3.2 Steps

1. Manager submits access change request in Jira (IT-ACCESS-CHANGE template)
2. CISO approves for privileged access changes (within 24 hours)
3. IT Operations implements changes in Azure AD (within 24 hours of approval)
4. Old access group removed; new group assigned — verified by requester
5. PAM adjustments made if privileged access scope changes (Platform Eng Lead approves)
6. Change logged in audit trail (Azure AD audit log + Jira ticket)

---

## 4. Procedure: Access Review

### 4.1 Quarterly Privileged Access Review

| Step | Action | Responsible |
|------|--------|------------|
| 1 | GRC generates privileged access report from Azure AD + PAM | GRC Analyst |
| 2 | Report sent to each team lead for review (within 5 working days) | GRC Analyst |
| 3 | Team leads confirm, remove, or flag changes | Department Heads |
| 4 | IT Operations implements approved changes | IT Operations |
| 5 | Review completion documented in Jira; signed off by CISO | GRC Lead |

### 4.2 Annual Standard User Access Review

Same process as above, covering all standard user accounts. Department heads must certify
that each user's access is still required for their current role.

### 4.3 Dormant Account Review

1. IT Operations runs monthly dormant account report (>90 days no login)
2. Account owners notified; if no response within 5 days, account disabled
3. If account disabled for 30 days with no business justification, account deleted

---

## 5. Procedure: User Off-boarding (Access Revocation)

### 5.1 Trigger
Employee departure (resignation, termination, end of contract).

### 5.2 Steps

| Step | Action | Responsible | SLA |
|------|--------|------------|-----|
| 1 | HR notifies IT Operations of departure via Jira (IT-OFFBOARD template) | HR | Day of notice |
| 2 | **For terminations:** All access revoked immediately (Day 0) | IT Operations | Immediate |
| 3 | **For resignations:** Access revoked on last working day by 17:00 | IT Operations | Last working day |
| 4 | Azure AD account disabled; password reset; MFA cleared | IT Operations | Per above |
| 5 | PAM access revoked; PAM vault reviewed for shared secrets | Platform Eng | Per above |
| 6 | All SOC tool accounts disabled | Platform Eng | Per above |
| 7 | Microsoft 365 mailbox converted to shared mailbox (30-day retention) | IT Operations | Per above |
| 8 | Laptop retrieved and wiped (NIST 800-88) | IT Operations | Within 3 working days |
| 9 | Asset register updated (CMDB) | IT Operations | Within 3 working days |
| 10 | Off-boarding checklist signed off by HR, IT, and direct manager | HR | Within 5 working days |

> **Critical control:** For SOC analysts, access to client environments must be revoked
> simultaneously with Azure AD — not sequentially. Client-specific VPN credentials must
> be changed within 4 hours if the departing analyst had client environment access.

---

## 6. Integration with SOC Operations

### 6.1 Wazuh SIEM Rules for Access Control
Wazuh is configured to alert on:
- Multiple failed authentication attempts (rule ID: 2502) → TheHive auto-case
- Privileged account usage outside business hours → T2 investigation
- Access to client environments outside analyst's assigned shift → T2 escalation
- New admin account creation → GRC notified

### 6.2 SOC Analyst Context
Access control monitoring is a core SOC function. Tier 1 analysts triage access-related
Wazuh alerts. Tier 2 analysts investigate anomalous access patterns. The GRC team
reviews the quarterly privileged access report using exported data from Wazuh and Azure AD.

---

## 7. Evidence & Records

| Record | Storage | Retention |
|--------|---------|-----------|
| Onboarding Jira ticket | Jira | 3 years |
| Azure AD audit logs | Elasticsearch (via Wazuh) | 12 months hot, 36 months cold |
| PAM session recordings | PAM vault | 12 months |
| Access review sign-off | Jira | 3 years |
| Off-boarding checklist | HR system | 5 years |

---

*Document Owner: IT Operations / CISO | Approved by: CISO | Next Review: 2026-01-15*
