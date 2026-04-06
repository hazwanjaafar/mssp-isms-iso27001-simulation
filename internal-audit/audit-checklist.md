# ✅ Internal Audit Checklist – ISO/IEC 27001:2022

**Document ID:** SN-AUD-002  
**Version:** 1.0  
**Audit Reference:** AU-2025-01  
**Audit Date:** 10–14 February 2025  
**Auditor:** External Consultant (Azmi Consulting Sdn. Bhd.)  
**Classification:** Confidential – Internal  

---

## Legend

| Rating | Code | Description |
|--------|------|-------------|
| Conforming | ✅ C | Requirement fully met with adequate evidence |
| Minor Non-Conformity | 🟡 MNC | Requirement partially met; systematic gap |
| Major Non-Conformity | 🔴 MAC | Requirement not met; significant gap |
| Observation | 🔵 OBS | No NCR; improvement opportunity noted |
| Not Applicable | ➖ N/A | Control assessed as not applicable |

---

## Part 1: ISO 27001:2022 Clause Audit

### Clause 4 – Context of the Organisation

| Ref | Requirement | Evidence Requested | Rating | Finding |
|-----|------------|-------------------|--------|---------|
| 4.1 | Organisation and its context documented | SN-ISMS-001 (Scope); company profile | ✅ C | Context documented; internal/external factors identified |
| 4.2 | Interested parties identified | Interested parties register in SN-ISMS-001 | ✅ C | 6 interested parties documented with requirements |
| 4.3 | ISMS scope defined | SN-ISMS-001 Scope Statement | ✅ C | Scope statement clear; boundaries defined |
| 4.4 | ISMS established | ISMS documentation suite | ✅ C | ISMS implemented across scope |

### Clause 5 – Leadership

| Ref | Requirement | Evidence Requested | Rating | Finding |
|-----|------------|-------------------|--------|---------|
| 5.1 | Top management demonstrates leadership | IS Policy signed by CEO; management review minutes | ✅ C | Policy signed Jan 2025; management review conducted Dec 2024 |
| 5.2 | IS policy established and communicated | SN-POL-001; staff acknowledgement records | 🟡 MNC | IS Policy communicated to 108/120 staff (90%). 12 staff overdue for acknowledgement. **NCR-001** |
| 5.3 | Roles, responsibilities assigned | SN-ORG-001; RACI | ✅ C | ISMS roles clearly assigned |

### Clause 6 – Planning

| Ref | Requirement | Evidence Requested | Rating | Finding |
|-----|------------|-------------------|--------|---------|
| 6.1.1 | Risks and opportunities identified | Risk register | ✅ C | 18 risks documented with assessment |
| 6.1.2 | Risk assessment conducted | Risk Register SN-ISMS-002; workshop minutes | ✅ C | Workshop conducted Nov 2024; methodology consistent |
| 6.1.3 | Risk treatment options selected | Risk treatment plan in SN-ISMS-002 | 🟡 MNC | 3 risks with RR > 0.30 have no board sign-off on acceptance. **NCR-002** |
| 6.2 | IS objectives established | Management review; KPI register | 🔵 OBS | KPIs defined but not formally documented as ISMS objectives per 6.2 |
| 6.3 | Changes to ISMS planned | Change management records | ✅ C | CAB process covers ISMS changes |

### Clause 7 – Support

| Ref | Requirement | Evidence Requested | Rating | Finding |
|-----|------------|-------------------|--------|---------|
| 7.1 | Resources determined and provided | Budget allocation; staffing records | ✅ C | GRC team, tooling budget evidenced |
| 7.2 | Competence | CV/qualifications; training records | 🔵 OBS | No formal competence requirements defined for SOC Tier 1. Recommended: document minimum qualifications |
| 7.3 | Awareness | Training completion records; phishing simulation results | 🟡 MNC | 12 staff not completed IS awareness training. Links to NCR-001. **NCR-003** |
| 7.4 | Communication | Communication plan | ✅ C | Communication plan in ISMS documentation |
| 7.5 | Documented information | Document register; version control | ✅ C | Confluence version control; document register maintained |

### Clause 8 – Operation

| Ref | Requirement | Evidence Requested | Rating | Finding |
|-----|------------|-------------------|--------|---------|
| 8.1 | Operational planning and control | Procedures; SOPs | ✅ C | 4 core procedures implemented |
| 8.2 | IS risk assessment performed | Risk register update records | ✅ C | Quarterly updates evidenced |
| 8.3 | IS risk treatment | Treatment tracking in Jira | 🟡 MNC | R-018 (supply chain) has no treatment action started. **NCR-004** |

### Clause 9 – Performance Evaluation

| Ref | Requirement | Evidence Requested | Rating | Finding |
|-----|------------|-------------------|--------|---------|
| 9.1 | Monitoring and measurement | Grafana dashboards; KPI reports | 🔵 OBS | Dashboards comprehensive but KPI baselines not formally set |
| 9.2 | Internal audit conducted | Audit programme; previous audit reports | ✅ C | This audit is AU-2025-01; previous: consultant audit Sept 2024 |
| 9.3 | Management review conducted | Management review minutes | ✅ C | Minutes from Dec 2024 management review provided |

### Clause 10 – Improvement

| Ref | Requirement | Evidence Requested | Rating | Finding |
|-----|------------|-------------------|--------|---------|
| 10.1 | Non-conformity and corrective action | Jira ISMS-AUDIT project | ✅ C | Previous NCRs tracked; 7 closed, 2 in progress |
| 10.2 | Continual improvement | Improvement log; management review outputs | ✅ C | Improvement items from previous audit tracked |

---

## Part 2: Annex A Control Sample Audit

### Access Control (A.5.15 – A.5.18, A.8.1 – A.8.5)

| Control | Requirement | Evidence | Rating | Finding |
|---------|------------|---------|--------|---------|
| A.5.15 | Access control policy implemented | SN-POL-002 | ✅ C | Policy in place; signed |
| A.5.16 | Identity management | Azure AD records | ✅ C | All users have unique accounts; no shared accounts found |
| A.5.17 | Authentication information | Password policy; MFA records | ✅ C | MFA enforced on all sampled accounts |
| A.5.18 | Access rights management | Access review Q4 2024 | 🟡 MNC | 3 users with access exceeding current role requirements found in access review. Review not completed in time. **NCR-005** |
| A.8.1 | User endpoint devices | MDM enrolment; Wazuh agent | ✅ C | 118/120 laptops MDM enrolled; 2 missing (investigated: 2 new joiners pending) |
| A.8.2 | Privileged access rights | PAM records; JIT logs | ✅ C | JIT access working; all sessions logged |
| A.8.5 | Secure authentication | Auth config; MFA policy | ✅ C | MFA enforced; FIDO2 for PAM admin access |

### Supplier Management (A.5.19 – A.5.22)

| Control | Requirement | Evidence | Rating | Finding |
|---------|------------|---------|--------|---------|
| A.5.19 | IS in supplier relationships | Supplier register; assessment records | 🔴 MAC | Only 3 of 12 critical suppliers have completed IS assessments. Policy requires all critical suppliers assessed annually. **NCR-006 (MAJOR)** |
| A.5.20 | IS within supplier agreements | Contract templates with DPA clauses | ✅ C | Standard DPA clause in all new contracts; 1 legacy contract pending update (noted as OBS) |
| A.5.22 | Monitoring of supplier services | Supplier review schedule | 🟡 MNC | Only 2 of 5 scheduled annual supplier reviews completed. **NCR-007** |

### Incident Management (A.5.24 – A.5.28)

| Control | Requirement | Evidence | Rating | Finding |
|---------|------------|---------|--------|---------|
| A.5.24 | IR planning and preparation | SN-IRP-001; SN-PROC-002 | ✅ C | IR plan and procedure in place |
| A.5.25 | Assessment of IS events | TheHive records | ✅ C | 47 incidents reviewed; triage process followed |
| A.5.26 | Response to IS incidents | TheHive case records; NACSA notifications | 🔵 OBS | NACSA notifications timely in 2 of 2 qualifying incidents; recommend adding a NACSA notification checklist to the IR procedure |
| A.5.27 | Learning from incidents | PIR reports | 🟡 MNC | Only 8/12 P1/P2 PIRs completed within 5-day SLA. **NCR-008** |
| A.5.28 | Collection of evidence | Chain of custody records in TheHive | ✅ C | Evidence handling procedure followed |

### Logging and Monitoring (A.8.15, A.8.16)

| Control | Requirement | Evidence | Rating | Finding |
|---------|------------|---------|--------|---------|
| A.8.15 | Logging | Wazuh configuration; retention policy | ✅ C | Centralised logging; 12-month hot retention confirmed |
| A.8.16 | Monitoring activities | Grafana dashboards; SOC shift logs | ✅ C | 24×7 monitoring evidenced; shift handover records reviewed |

### Network Security (A.8.20 – A.8.22)

| Control | Requirement | Evidence | Rating | Finding |
|---------|------------|---------|--------|---------|
| A.8.20 | Network security | Firewall architecture diagram; config | ✅ C | Network segmented; default-deny firewall policy |
| A.8.21 | Security of network services | Firewall rule review Q4 2024 | 🔵 OBS | Firewall rule review completed but 4 deprecated rules not yet removed |
| A.8.22 | Segregation of networks | VLAN architecture; client isolation config | ✅ C | Client environments logically isolated; tested |

### Vulnerability Management (A.8.8)

| Control | Requirement | Evidence | Rating | Finding |
|---------|------------|---------|--------|---------|
| A.8.8 | Technical vulnerability management | Nessus scan reports; patch records | 🟡 MNC | 2 critical CVEs (CVSS 9.1) outstanding > 30 days. Patch SLA breached. **NCR-009** |

---

## Part 3: Physical Security Walkthrough

| Area | Observation | Rating |
|------|-------------|--------|
| SOC floor entry | Badge access operational; visitor log maintained | ✅ C |
| SOC workstations | Screen locks active; clean desk generally observed | 🔵 OBS – 1 workstation with visible credential Post-it note |
| Server room entry | Biometric + badge access; visitor log | ✅ C |
| Server room environment | Temperature monitoring active; UPS operational | ✅ C |
| Cabling | Structured cabling; labelled | ✅ C |
| Fire suppression | Gaseous suppression system; last tested Oct 2024 | ✅ C |

---

## Audit Summary

| Finding Type | Count |
|-------------|-------|
| 🔴 Major Non-Conformity (MAC) | 1 |
| 🟡 Minor Non-Conformity (MNC) | 7 |
| 🔵 Observation (OBS) | 5 |
| ✅ Conforming | 37 |

**Overall audit opinion:** The ISMS is substantially implemented and operational.
One major non-conformity (supplier assessment gap) requires urgent remediation before
the certification audit. Seven minor non-conformities must be addressed with corrective
actions within 60 days. The ISMS demonstrates a genuine commitment to information
security management beyond paper compliance.

---

*Auditor: Azmi Consulting Sdn. Bhd. | Audit Date: 10–14 Feb 2025 | Report Date: 21 Feb 2025*
