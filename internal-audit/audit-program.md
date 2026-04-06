# 📅 Internal Audit Programme – FY2025

**Document ID:** SN-AUD-001  
**Version:** 1.0  
**Classification:** Internal  
**Owner:** GRC Lead  
**Approved by:** CISO  
**Last Reviewed:** 2025-01-15  

---

## 1. Purpose

This document establishes SecureNusantara's annual internal audit programme for the ISMS.
It defines the audit scope, schedule, methodology, and responsibilities to ensure the ISMS
is operating effectively and in conformance with ISO/IEC 27001:2022.

---

## 2. Audit Objectives

1. Verify that the ISMS is implemented and operating as intended
2. Identify non-conformities, observations, and opportunities for improvement
3. Provide evidence to support the external certification audit
4. Drive continuous improvement in information security management

---

## 3. Audit Independence

| Audit | Conducted by | Rationale |
|-------|-------------|-----------|
| Internal Audit 1 (H1) | External consultant (RM 15,000) | Independence from ISMS implementation team |
| Internal Audit 2 (H2, pre-certification) | GRC Lead + External consultant | Final check before certification |

> **Justification for external consultant:** The GRC Lead is also the ISO 27001 project
> lead — auditing their own work would compromise independence (ISO 27001 Clause 9.2
> requirement). The additional cost is accepted as necessary for audit credibility.

---

## 4. Audit Schedule – FY2025

| Audit No. | Timing | Scope | Lead Auditor | Status |
|-----------|--------|-------|-------------|--------|
| **AU-2025-01** | Feb 2025 (Week 2–3) | ISMS Clauses 4–10; Annex A sample (50 controls) | External Consultant | Completed |
| **AU-2025-02** | Jul 2025 (Week 2–3) | Full Annex A (all 93 controls); pre-certification focus | GRC Lead + External Consultant | Planned |

---

## 5. Audit Scope

### 5.1 Audit 1 (AU-2025-01) — H1 Internal Audit

**ISO 27001:2022 Clauses reviewed:**
- Clause 4: Context of the organisation
- Clause 5: Leadership
- Clause 6: Planning (risk assessment, SoA)
- Clause 7: Support (awareness, documentation)
- Clause 8: Operation (risk treatment, procedures)
- Clause 9: Performance evaluation (monitoring, management review)
- Clause 10: Improvement (corrective actions)

**Annex A sample (50 controls — risk-based selection):**

Priority areas based on Risk Register high-residual risks:
- A.5.7, A.5.15–5.18, A.5.19–5.22 (access control, supplier management)
- A.5.24–5.28 (incident management)
- A.8.1–8.5 (endpoint, access)
- A.8.8, A.8.15, A.8.16, A.8.20, A.8.22 (vuln mgmt, logging, network)

### 5.2 Audit 2 (AU-2025-02) — H2 Pre-Certification Internal Audit

Full scope: All 93 Annex A controls + all ISO 27001 clauses.  
Focus areas (based on AU-2025-01 findings):
- Corrective action verification
- Partial controls from SoA (19 identified)
- Documentation completeness and version control

---

## 6. Audit Methodology

### 6.1 Evidence Collection Methods

| Method | Application |
|--------|-------------|
| **Document review** | Policies, procedures, SOPs, risk register, SoA — version control verified |
| **Interview** | SOC Manager, Platform Eng Lead, GRC Lead, sample SOC analysts |
| **System demonstration** | Live Wazuh dashboard, TheHive cases, PAM session logs, CMDB |
| **Log review** | Access logs, audit logs, incident logs — sampling approach |
| **Observation** | SOC floor walkthrough; physical security check; clean desk check |
| **Record sampling** | Access reviews, training records, change management records |

### 6.2 Sampling Approach

- Access review records: Last 2 completed reviews (100% of records)
- Incident records: Last 12 incidents in TheHive (all P1/P2; random sample of P3/P4)
- Change records: Last quarter's changes (random sample of 10)
- Training records: All staff (completion %) — verify against HR training register

---

## 7. Audit Reporting

| Report Section | Content |
|----------------|---------|
| Executive Summary | Overall ISMS conformance status; major findings |
| Scope and Methodology | What was audited and how |
| Findings | Non-conformities (major/minor), observations, OFIs |
| Corrective Action Plan | Each NCR with proposed action, owner, and deadline |
| Audit Opinion | Overall readiness opinion (for pre-certification audit) |

**Reporting timelines:**
- Draft report: 5 working days after audit completion
- Management response: 5 working days after draft received
- Final report: 3 working days after management response

---

## 8. Corrective Action Tracking

All findings are entered into Jira (project: `ISMS-AUDIT`):
- **Major NCR:** Must be resolved within 30 days; CISO must sign off closure
- **Minor NCR:** Must be resolved within 60 days; GRC Lead signs off closure
- **Observation:** Tracked for improvement; no mandatory deadline
- **OFI:** Tracked in backlog; prioritised by GRC Lead

---

## 9. Audit Competency Requirements

Internal auditors must demonstrate:
- Understanding of ISO/IEC 27001:2022 requirements
- Familiarity with SecureNusantara's ISMS scope and operations
- Impartiality — no audit of their own work
- ISO 27001 Lead Auditor qualification (preferred for external consultant)

---

*Document Owner: GRC Lead | Approved by: CISO | Next Review: 2026-01-15*
