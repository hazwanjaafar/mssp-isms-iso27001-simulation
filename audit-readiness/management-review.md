# 📊 Management Review – SecureNusantara ISMS

**Document ID:** SN-MR-001  
**Meeting Date:** 15 December 2024 (Quarterly)  
**Chair:** COO (Rashdan Ismail)  
**Attendees:** CEO, CISO, COO, SOC Manager, GRC Lead, Platform Eng Lead, Cloud Security Lead  
**Classification:** Confidential – Internal  
**Minuted by:** GRC Analyst (Zulaikha Noor)  

---

## 1. Purpose of Management Review

To evaluate the continuing suitability, adequacy, and effectiveness of the ISMS, and
to make decisions about continual improvement and resource allocation. Required by
ISO/IEC 27001:2022 Clause 9.3.

---

## 2. Review Inputs

### 2.1 Status of Previous Management Review Actions

| Action | Owner | Status | Notes |
|--------|-------|--------|-------|
| Implement SOAR playbooks for top 5 alert types | Platform Eng | ✅ Complete | 5 playbooks deployed; false positive rate reduced from 75% to 65% |
| Conduct supplier assessment for AWS and Microsoft | GRC Lead | ✅ Complete | Assessments completed Oct/Nov 2024 |
| Develop PDPA breach notification procedure (draft) | GRC Lead | 🟡 In Progress | Draft at 50%; target Jan 2025 |
| Act 854 CSSP licence application submission | CEO | ✅ Complete | Application submitted 30 Nov 2024 |
| Multi-AZ Wazuh deployment | Platform Eng | ✅ Complete | Deployed Dec 2024 |

### 2.2 Changes in External and Internal Issues

| Factor | Change | ISMS Impact |
|--------|--------|------------|
| Act 854 gazetted | Cybersecurity Act 2024 came into force | CSSP licence now mandatory; incident reporting obligations active |
| MITRE ATT&CK v15 released | New techniques added | TI team updating OpenCTI detection rules |
| 3 new government clients | Increased scope of monitored environments | Alert volume +30%; staffing review initiated |
| 2 SOC T1 analysts departed | Staff turnover | MTTD for P3/P4 increased; 2 new hires initiated |

### 2.3 IS Performance and Effectiveness

#### 2.3.1 Security KPIs (Q4 2024)

| KPI | Target | Q4 Actual | Trend | Comment |
|-----|--------|----------|-------|---------|
| MTTD (P1 incidents) | < 15 min | 12 min | ✅ Green | |
| MTTD (P2 incidents) | < 60 min | 48 min | ✅ Green | |
| MTTR (P1 incidents) | < 4 hours | 3.2 hours | ✅ Green | |
| MTTR (P2 incidents) | < 8 hours | 7.1 hours | ✅ Green | |
| Alert false positive rate | < 20% | 65% | 🔴 Red | SOAR partially deployed; still significant gap |
| Client SLA breach rate | 0% | 0% | ✅ Green | No SLA breaches this quarter |
| IS awareness training completion | 100% | 90% | 🟡 Amber | 12 Q4 joiners pending |
| Critical CVE patch SLA | 100% within 30 days | 85% | 🟡 Amber | 2 CVEs overdue (year-end freeze) |
| Incident PIR completion | 100% within 5 days | 67% | 🟡 Amber | 4 PIRs overdue |
| Supplier assessments | 100% of critical | 25% | 🔴 Red | Only 3/12 assessed — major gap |

#### 2.3.2 Incidents (Q4 2024)

| Severity | Count | Notable Incidents |
|----------|-------|-----------------|
| P1 | 1 | Client A: Ransomware (contained within 3h; PIR completed) |
| P2 | 3 | Credential compromise × 2; C2 beacon × 1 |
| P3 | 12 | Various phishing, scan, failed brute force |
| P4 | 89 | Informational/failed attacks |

**P1 incident (Client A — Ransomware):**
- Detection via Wazuh behavioural rule (mass file rename event)
- Contained via endpoint isolation (Wazuh active response)
- Client notified within 12 minutes of detection
- NACSA notified within 5 hours
- No data exfiltration confirmed
- Root cause: Unpatched SMB vulnerability on client server (patch was in client's scope, not ours)
- Corrective action: Expanded scope of SecureNusantara's vulnerability advisory to include client patch status alerts

#### 2.3.3 Vulnerability Management (Q4 2024)

| Severity | Found | Remediated | % Closed | Avg Days to Patch |
|----------|-------|-----------|---------|------------------|
| Critical | 23 | 19 | 83% | 28 days |
| High | 67 | 58 | 87% | 52 days |
| Medium | 189 | 145 | 77% | 72 days |

> **Comment from CISO:** Critical vulnerability remediation is at 83% — below the 100%
> target. The 4 outstanding criticals include 2 on client-managed systems (not within
> SecureNusantara's patch authority) and 2 on internal systems (addressed in Q1 2025).

### 2.4 Risk Treatment Status

| Risk Category | Open Risks | Risks In Treatment | Residual Risk > 0.30 |
|--------------|------------|-------------------|---------------------|
| SOC Operations | 2 | 3 | 1 (R-001) |
| Cloud Infrastructure | 1 | 2 | 1 (R-008) |
| Client Data | 0 | 2 | 0 |
| People & Org | 0 | 2 | 0 |
| Regulatory | 1 | 1 | 1 (R-016) |

Three risks with residual > 0.30 require board sign-off (identified as NCR-002 in internal audit).

### 2.5 Opportunities for Improvement

| Opportunity | Proposed Action | Priority |
|------------|----------------|---------|
| Alert fatigue (FP rate 65%) | Accelerate Shuffle SOAR deployment; engage TI team for rule tuning | High |
| PDPA breach notification gap | Complete BN procedure by Jan 2025; test scenario by Feb 2025 | High |
| Supplier assessment backlog | Engage GRC contractor; complete all 12 by April 2025 | High |
| Staff retention (SOC T1) | HR to review compensation benchmarking; mentorship programme | Medium |
| SBOM for open-source tools | Initiate pilot with Wazuh dependency mapping | Low |

### 2.6 Staff Awareness & Training Validation

| Training | Q4 Completion | Previous Quarter |
|---------|--------------|----------------|
| IS Policy acknowledgement | 90% | 98% |
| IS Awareness (e-learning) | 90% | 98% |
| Phishing simulation (click rate) | 8% | 12% |
| IR tabletop exercise | 100% (SOC team) | N/A (first time) |
| PDPA awareness (all staff) | 75% | 60% |

> **CISO observation:** Phishing click rate improving (12% → 8%). IR tabletop conducted
> for first time — positive outcome with identified gaps in client communication template.

---

## 3. Management Decisions

| Decision | Owner | Deadline |
|----------|-------|---------|
| Approve engagement of GRC contractor (budget: RM 15,000) to address supplier assessment gap | CEO | 20 Dec 2024 |
| Add risk acceptance agenda item to January board meeting for R-001, R-008, R-016 | CEO | 15 Jan 2025 |
| Approve Q1 2025 SOAR acceleration project (budget: RM 8,000 Platform Eng overtime) | COO | 20 Dec 2024 |
| Initiate HR benchmarking review for SOC T1 compensation | COO | 31 Jan 2025 |
| Approve external internal auditor for AU-2025-01 (budget: RM 15,000) | CEO | 20 Dec 2024 ✅ |

---

## 4. ISMS Continual Improvement Plan (Q1 2025 Priority Actions)

| Action | Owner | Target | KPI |
|--------|-------|--------|-----|
| Complete PDPA breach notification procedure | GRC Lead | 31 Jan 2025 | Procedure published; test completed |
| Deploy 5 additional Shuffle SOAR playbooks (top 5 by volume) | Platform Eng | 31 Mar 2025 | FP rate target: 50% |
| Complete supplier assessments for remaining 9 critical suppliers | GRC Lead | 30 Apr 2025 | 12/12 assessed |
| Complete IS awareness training for Q4 joiners | HR / GRC | 15 Jan 2025 | 100% completion |

---

## 5. Next Management Review

**Date:** March 2025 (Q1 review) — to be scheduled by GRC Lead  
**Key agenda items:** 
- Internal audit (AU-2025-01) findings review
- SOAR progress update
- Supplier assessment completion update
- Pre-certification readiness assessment

---

*Minutes approved by: COO | Distributed to: All attendees | Filing: Confluence > ISMS > Management Review*
