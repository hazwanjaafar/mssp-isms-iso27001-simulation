# 🔍 Internal Audit Findings & Corrective Actions – AU-2025-01

**Document ID:** SN-AUD-003  
**Audit Reference:** AU-2025-01  
**Audit Period:** 10–14 February 2025  
**Report Date:** 21 February 2025  
**Auditor:** Azmi Consulting Sdn. Bhd.  
**Classification:** Confidential – Internal  
**Tracking:** Jira project `ISMS-AUDIT`  

---

## 1. Executive Summary

The internal audit of SecureNusantara's ISMS (AU-2025-01) has been completed.
Overall, the ISMS is substantially implemented with genuine security management
practices evident. The audit identified:

- **1 Major Non-Conformity** — requiring urgent remediation (target: 30 days)
- **7 Minor Non-Conformities** — requiring corrective action (target: 60 days)
- **5 Observations** — improvement opportunities (no mandatory deadline)

The most significant finding is the gap in supplier security assessments (NCR-006),
which represents a systemic failure to apply the supplier management procedure to the
majority of critical suppliers. If not remediated, this finding alone could result in
an ISO 27001 certification non-conformance.

---

## 2. Non-Conformity Register

### NCR-001 (Minor) – IS Policy Not Communicated to All Staff

| Field | Detail |
|-------|--------|
| **NCR ID** | NCR-001 |
| **Severity** | Minor |
| **ISO Clause** | 5.2, 7.3 |
| **Finding** | 12 staff members (10% of workforce) have not signed the IS Policy acknowledgement. All 12 are staff who joined in Q4 2024. Policy awareness training not completed. |
| **Evidence** | HR training register: 108/120 completed; policy sign-off log: 108/120 signed |
| **Root Cause** | Onboarding checklist does not include a hard deadline for policy acknowledgement. IT Operations processes the Jira onboarding ticket without checking training completion. |
| **Risk** | Uncertified staff may not understand IS obligations — creates accountability gap and risk of accidental policy violation. |

**Corrective Action Plan:**

| Action | Owner | Deadline |
|--------|-------|---------|
| Update onboarding Jira template to include mandatory IS training completion within 5 working days | GRC Lead | 28 Feb 2025 |
| Chase 12 outstanding staff — complete training within 10 working days | HR | 7 Mar 2025 |
| Add automated reminder from LMS after 3 working days without completion | Platform Eng | 15 Mar 2025 |
| Verify 100% completion; GRC Lead sign-off | GRC Lead | 21 Mar 2025 |

**Closure Criterion:** 120/120 staff have completed IS training and signed policy acknowledgement; onboarding template updated with mandatory deadline.

---

### NCR-002 (Minor) – High-Residual Risks Without Board Sign-Off

| Field | Detail |
|-------|--------|
| **NCR ID** | NCR-002 |
| **Severity** | Minor |
| **ISO Clause** | 6.1.3, 8.3 |
| **Finding** | Three risks with residual score > 0.30 (R-001, R-008, R-016) do not have formal board sign-off on acceptance, as required by the Risk Management Policy. |
| **Evidence** | Risk Register SN-ISMS-002; Risk Management Policy (SN-POL-005, Section 4.3) |
| **Root Cause** | Board risk acceptance procedure was not communicated to CISO during policy drafting. CISO was unaware that any residual risk > 0.30 requires board sign-off specifically (as opposed to CEO sign-off). |

**Corrective Action Plan:**

| Action | Owner | Deadline |
|--------|-------|---------|
| Schedule board agenda item for risk acceptance review | CEO | 28 Feb 2025 |
| Prepare board risk briefing pack for R-001, R-008, R-016 | CISO | 28 Feb 2025 |
| Obtain board sign-off (minutes) at next board meeting | CEO | 15 Mar 2025 |
| Update Risk Management Policy to clarify board vs CEO approval thresholds | GRC Lead | 21 Mar 2025 |

**Closure Criterion:** Board meeting minutes confirm acceptance of R-001, R-008, R-016; Risk Management Policy updated.

---

### NCR-003 (Minor) – IS Awareness Training Incomplete

**[Linked to NCR-001]** — Same root cause. Same corrective action. Closure tracked together with NCR-001.

---

### NCR-004 (Minor) – Risk Treatment Action Not Started (R-018)

| Field | Detail |
|-------|--------|
| **NCR ID** | NCR-004 |
| **Severity** | Minor |
| **ISO Clause** | 8.3 |
| **Finding** | Risk R-018 (supply chain attack via open-source tool) has a planned SBOM initiative as treatment action, but no work has commenced and the Jira ticket has not been created. |
| **Evidence** | Risk Register: R-018 treatment column shows "SBOM initiative planned"; Jira search: no SBOM ticket found |
| **Root Cause** | SBOM was treated as a low-priority backlog item by Platform Engineering. No Jira ticket was created at the time of the risk assessment, so it fell off the radar. |

**Corrective Action Plan:**

| Action | Owner | Deadline |
|--------|-------|---------|
| Create Jira ticket for SBOM initiative with acceptance criteria | Platform Eng Lead | 7 Mar 2025 |
| Define scope of SBOM (which open-source tools; which components) | Platform Eng Lead | 21 Mar 2025 |
| Implement interim control: verify checksums for all Wazuh/MISP/TheHive updates | Platform Eng | 7 Mar 2025 |
| Update Risk Register: interim control reduces likelihood; update RR score | GRC Lead | 7 Mar 2025 |

**Closure Criterion:** Jira ticket created and in active sprint; interim checksum verification process documented and evidenced; Risk Register updated.

---

### NCR-005 (Minor) – Access Rights Exceeding Current Role

| Field | Detail |
|-------|--------|
| **NCR ID** | NCR-005 |
| **Severity** | Minor |
| **ISO Clause** | A.5.18 |
| **Finding** | Q4 2024 access review identified 3 users with access exceeding their current role. Review completed on 20 Jan 2025 but changes not yet implemented (audit conducted 10 Feb 2025 — 21 days overdue). |
| **Evidence** | Access review report Q4 2024; Azure AD current access vs. approved access |
| **Root Cause** | Access review process requires IT Operations to implement changes within 5 working days of review sign-off. IT Operations queue was overloaded with onboarding work in January. |

**Corrective Action Plan:**

| Action | Owner | Deadline |
|--------|-------|---------|
| Immediately remove excess access for 3 identified users | IT Operations | 14 Feb 2025 ✅ Done |
| Review IT Operations workload and implement SLA monitoring | COO | 28 Feb 2025 |
| Add access change SLA to Grafana monitoring dashboard | Platform Eng | 15 Mar 2025 |
| Document root cause in access review SOP | GRC Lead | 21 Mar 2025 |

**Closure Criterion:** Excess access removed (evidenced by Azure AD screenshot); SLA monitoring implemented; SOP updated.

---

### NCR-006 (MAJOR) – Supplier Security Assessments Incomplete

| Field | Detail |
|-------|--------|
| **NCR ID** | NCR-006 |
| **Severity** | **MAJOR** |
| **ISO Clause** | A.5.19, A.5.22 |
| **Finding** | SecureNusantara has 12 critical suppliers. Only 3 have completed security assessments. The Supplier Management Procedure (when it existed) required all critical suppliers to be assessed annually. The procedure was published in Q3 2024 but only 3 assessments were initiated. |
| **Evidence** | Supplier register: 12 critical suppliers listed; assessment records: 3 completed (AWS, Microsoft, ISP); 9 not started |
| **Root Cause (5-Why):** ||
| Why? | 9 critical supplier assessments not completed |
| Why? | GRC team capacity was consumed by ISO 27001 implementation project |
| Why? | ISO 27001 project was not properly resourced — GRC team too small for concurrent workloads |
| Why? | Business decision was made to proceed without additional GRC resourcing |
| Why? | Leadership underestimated GRC workload for simultaneous ISO 27001 + operational compliance |

**Root cause summary:** Structural resourcing problem — GRC team cannot simultaneously implement ISO 27001 and perform all operational GRC activities.

**Corrective Action Plan:**

| Action | Owner | Deadline | Priority |
|--------|-------|---------|---------|
| Immediately initiate supplier assessments for remaining 9 critical suppliers | GRC Lead | 28 Mar 2025 | P1 |
| Engage temporary GRC contractor to support assessment work | COO | 14 Feb 2025 | P1 |
| Complete 5 highest-risk supplier assessments (ranked by data access) | GRC Lead + contractor | 31 Mar 2025 | P1 |
| Complete remaining 4 supplier assessments | GRC Lead + contractor | 30 Apr 2025 | P2 |
| Update supplier management SOP to include resource allocation requirements | GRC Lead | 28 Feb 2025 | P2 |
| Review GRC team headcount with CEO for FY2026 budget | CISO | 30 Apr 2025 | P3 |

**Closure Criterion:** All 12 critical suppliers assessed; records in Confluence; supplier register updated. GRC Lead and CISO sign-off.

> **Auditor note:** This is the most significant finding. The external certification auditor
> will almost certainly review supplier management. If assessments are incomplete at the
> time of certification, this could result in a Major Non-Conformity and delay certification.
> **Immediate remediation is critical.**

---

### NCR-007 (Minor) – Supplier Review Schedule Not Completed

| Field | Detail |
|-------|--------|
| **NCR ID** | NCR-007 |
| **Severity** | Minor (linked to NCR-006) |
| **ISO Clause** | A.5.22 |
| **Finding** | Only 2 of 5 scheduled annual supplier reviews completed by year-end. 3 overdue. |
| **Root Cause** | Same resource constraint as NCR-006. |

**Corrective Action Plan:** Addressed as part of NCR-006 remediation plan. Remaining reviews scheduled alongside assessments.

---

### NCR-008 (Minor) – PIR Completion SLA Breached

| Field | Detail |
|-------|--------|
| **NCR ID** | NCR-008 |
| **Severity** | Minor |
| **ISO Clause** | A.5.27 |
| **Finding** | 4 of 12 P1/P2 PIRs not completed within the 5-working-day SLA. Delays ranged from 3 to 12 additional days. |
| **Evidence** | TheHive case closure dates; PIR report creation dates in Confluence |
| **Root Cause** | No automated reminder for PIR SLA. T2 analysts responsible for PIR were occupied with subsequent incidents. PIR treated as lower priority than active incident response. |

**Corrective Action Plan:**

| Action | Owner | Deadline |
|--------|-------|---------|
| Add TheHive automation: create PIR task automatically on incident closure | Platform Eng | 28 Feb 2025 |
| Add PIR SLA to SOC SLA dashboard (Grafana) | Platform Eng | 14 Mar 2025 |
| Update IR procedure: PIR responsibility explicitly assigned to T2 Lead | SOC Manager | 28 Feb 2025 |
| SOC Manager reviews PIR completion weekly | SOC Manager | Ongoing |

**Closure Criterion:** PIR automation task deployed in TheHive; Grafana PIR SLA dashboard live; IR procedure updated.

---

### NCR-009 (Minor) – Critical CVE Patch SLA Breached

| Field | Detail |
|-------|--------|
| **NCR ID** | NCR-009 |
| **Severity** | Minor |
| **ISO Clause** | A.8.8 |
| **Finding** | 2 critical CVEs (CVSS 9.1) outstanding beyond the 30-day patch SLA. CVE-2024-XXXX: 47 days outstanding. CVE-2024-YYYY: 38 days outstanding. Both on internal servers (not client-facing). |
| **Evidence** | Nessus scan report Jan 2025; patch log |
| **Root Cause** | Patches require maintenance window approval (CAB). CAB was not convened in December due to year-end freeze. No escalation mechanism for patches approaching SLA breach. |

**Corrective Action Plan:**

| Action | Owner | Deadline |
|--------|-------|---------|
| Emergency CAB approval and patch both CVEs | Platform Eng | 14 Feb 2025 ✅ Done |
| Add automated Jira alert when patch approaches 20-day mark (10-day warning) | Platform Eng | 28 Feb 2025 |
| Policy: Year-end freeze exemption for Critical patches | CISO | 28 Feb 2025 |

**Closure Criterion:** Both CVEs patched and evidenced in Nessus; automated alert deployed; policy updated.

---

## 3. Observations (No Mandatory Action)

| OBS ID | Description | Recommendation |
|--------|-------------|---------------|
| OBS-001 | IS objectives not formally structured per Clause 6.2 | Document ISMS objectives as measurable targets with baselines |
| OBS-002 | No formal competence requirements for Tier 1 SOC analysts | Define minimum qualifications and experience for each SOC tier |
| OBS-003 | NACSA notification checklist not in IR procedure | Add explicit NACSA notification checklist step to SN-PROC-002 |
| OBS-004 | 4 deprecated firewall rules not removed | Schedule firewall rule cleanup; add rule review to quarterly CAB agenda |
| OBS-005 | SOC workstation with credential Post-it note | Reinforce clean desk/clear screen policy; anonymous reporting channel for violations |

---

## 4. Corrective Action Tracking Summary

| NCR | Severity | Owner | Target | Status (as of 21 Feb 2025) |
|-----|----------|-------|--------|--------------------------|
| NCR-001 | Minor | GRC Lead / HR | 21 Mar 2025 | 🟡 In Progress |
| NCR-002 | Minor | CEO / CISO | 21 Mar 2025 | 🟡 In Progress |
| NCR-003 | Minor | (Linked to NCR-001) | 21 Mar 2025 | 🟡 In Progress |
| NCR-004 | Minor | Platform Eng Lead | 21 Mar 2025 | 🟡 In Progress |
| NCR-005 | Minor | IT Operations | 14 Feb 2025 | ✅ Closed |
| NCR-006 | **Major** | GRC Lead / COO | 30 Apr 2025 | 🔴 In Progress (Urgent) |
| NCR-007 | Minor | GRC Lead | 30 Apr 2025 | 🟡 In Progress |
| NCR-008 | Minor | SOC Manager | 14 Mar 2025 | 🟡 In Progress |
| NCR-009 | Minor | Platform Eng | 14 Feb 2025 | ✅ Closed |

---

*Report prepared by: Azmi Consulting Sdn. Bhd. | Reviewed by: GRC Lead | Accepted by: CISO*  
*Next review of corrective action status: 15 March 2025*
