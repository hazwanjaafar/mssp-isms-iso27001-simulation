# ⚠️ Risk Register – SecureNusantara Sdn. Bhd.

**Document ID:** SN-ISMS-002  
**Version:** 2.1  
**Classification:** Confidential – Internal  
**Owner:** CISO  
**Risk Owner Accountable:** CISO + Department Heads  
**Last Reviewed:** 2025-01-15  

---

## Risk Scoring Methodology

| Factor | Scale | Guidance |
|--------|-------|---------|
| **Likelihood (L)** | 0.1 – 1.0 | 0.1 = Rare, 0.5 = Possible, 1.0 = Almost certain |
| **Impact (I)** | 0.1 – 1.0 | 0.1 = Negligible, 0.5 = Significant, 1.0 = Catastrophic |
| **Risk Score (R)** | L × I | Inherent risk before controls |
| **Residual Risk (RR)** | Post-control score | Target < 0.25 (Medium) |

**Risk Appetite:**
- **Acceptable (Green):** RR ≤ 0.15
- **Monitor (Amber):** 0.15 < RR ≤ 0.30
- **Unacceptable (Red):** RR > 0.30 — Treatment required

---

## Risk Register

### Category 1: SOC Operations

| ID | Risk Description | Asset | Threat | Vulnerability | L | I | Score | Treatment | ISO Control | NIST CSF | Risk Owner | Residual Risk | Status |
|----|-----------------|-------|--------|--------------|---|---|-------|-----------|-------------|----------|------------|--------------|--------|
| **R-001** | SOC analyst alert fatigue leads to missed critical incident | SOC Platform | Insider failure | High alert volume; insufficient tuning | 0.7 | 0.9 | **0.63** | Mitigate: SOAR automation via Shuffle; Wazuh rule tuning; analyst rotation | A.8.16, A.5.25 | DE.AE | SOC Manager | 0.25 | 🔴 Open |
| **R-002** | Wazuh SIEM goes offline (unplanned) causing detection gap | Wazuh Platform | System failure | Single point of failure in agent-manager comm | 0.4 | 0.8 | **0.32** | Mitigate: HA Wazuh cluster (multi-node); alerting on agent disconnect | A.8.14, A.8.16 | DE.CM | Platform Eng Lead | 0.10 | 🟡 In Progress |
| **R-003** | Unauthorised access to multi-tenant SOC platform | SOC Platform | External attacker | Insufficient tenant isolation | 0.3 | 1.0 | **0.30** | Mitigate: Network segmentation; RBAC; penetration test | A.8.22, A.5.15 | PR.AA | CISO | 0.12 | 🟢 Treated |
| **R-004** | SOC analyst exfiltrates client data | Client Data | Malicious insider | Excessive privileged access | 0.2 | 1.0 | **0.20** | Mitigate: PAM, DLP, access reviews; background checks | A.8.2, A.6.1 | PR.AA | CISO | 0.08 | 🟢 Treated |
| **R-005** | TheHive case management system compromised | Case Data | External attacker | Known CVE in TheHive version | 0.3 | 0.7 | **0.21** | Mitigate: Patch within 30 days; restrict internet access to TheHive | A.8.8, A.8.19 | ID.RA | Platform Eng Lead | 0.09 | 🟢 Treated |

### Category 2: Cloud Infrastructure

| ID | Risk Description | Asset | Threat | Vulnerability | L | I | Score | Treatment | ISO Control | NIST CSF | Risk Owner | Residual Risk | Status |
|----|-----------------|-------|--------|--------------|---|---|-------|-----------|-------------|----------|------------|--------------|--------|
| **R-006** | Misconfigured AWS S3 bucket exposes client log data | AWS S3 | Misconfiguration | Lack of CSPM alerting | 0.4 | 0.9 | **0.36** | Mitigate: AWS Security Hub CSPM; bucket policy enforcement; S3 Block Public Access enabled | A.5.23, A.8.9 | PR.DS | Cloud Security Lead | 0.10 | 🟡 In Progress |
| **R-007** | AWS IAM privilege escalation leading to full account compromise | AWS Account | External attacker | Overly permissive IAM roles | 0.3 | 1.0 | **0.30** | Mitigate: IAM least privilege review; CloudTrail + Wazuh integration; SCPs | A.8.2, A.5.15 | PR.AA | Cloud Security Lead | 0.09 | 🟢 Treated |
| **R-008** | Data residency violation — Malaysian client PD stored in AWS Singapore | Client PD | Regulatory breach | Data classification gap | 0.5 | 0.8 | **0.40** | Mitigate: Data classification policy; route PD-heavy clients to Azure Malaysia; client consent | A.5.14, A.5.34 | GV.PO | CISO (DPO) | 0.20 | 🔴 Open |
| **R-009** | Cloud service provider outage (AWS/Azure) affecting SOC operations | SOC Availability | Supplier failure | Single-cloud dependency for some services | 0.3 | 0.7 | **0.21** | Mitigate: Multi-cloud architecture for critical components; BCP procedures | A.5.29, A.5.30 | RC.RP | Platform Eng Lead | 0.12 | 🟡 In Progress |

### Category 3: Client Data Handling

| ID | Risk Description | Asset | Threat | Vulnerability | L | I | Score | Treatment | ISO Control | NIST CSF | Risk Owner | Residual Risk | Status |
|----|-----------------|-------|--------|--------------|---|---|-------|-----------|-------------|----------|------------|--------------|--------|
| **R-010** | Accidental disclosure of Client A's data to Client B | Client Data | Insider failure | Insufficient data segregation in reports | 0.3 | 0.9 | **0.27** | Mitigate: Automated client tagging in Wazuh; report generation review process | A.8.22, A.5.12 | PR.DS | SOC Manager | 0.09 | 🟢 Treated |
| **R-011** | Client personal data not deleted after contract termination | Client PD | Regulatory breach | No automated data deletion process | 0.5 | 0.7 | **0.35** | Mitigate: Off-boarding checklist; automated deletion at retention expiry | A.8.10, A.5.33 | PR.DS | GRC Lead | 0.14 | 🟡 In Progress |
| **R-012** | Incident response evidence chain of custody broken | IR Evidence | Legal/regulatory | No formal evidence handling procedure | 0.4 | 0.6 | **0.24** | Mitigate: Chain of custody procedure; evidence storage in TheHive with audit log | A.5.28 | RS.AN | SOC Manager | 0.10 | 🟢 Treated |

### Category 4: People & Organisational

| ID | Risk Description | Asset | Threat | Vulnerability | L | I | Score | Treatment | ISO Control | NIST CSF | Risk Owner | Residual Risk | Status |
|----|-----------------|-------|--------|--------------|---|---|-------|-----------|-------------|----------|------------|--------------|--------|
| **R-013** | Key person dependency — single SOC Manager holds critical knowledge | Operations | Staff departure | Knowledge not documented | 0.4 | 0.7 | **0.28** | Mitigate: Documented runbooks; cross-training; succession planning | A.5.37 | GV.RR | COO | 0.14 | 🟡 In Progress |
| **R-014** | Security awareness training not completed by all staff | People | Social engineering | Phishing susceptibility | 0.4 | 0.6 | **0.24** | Mitigate: Monthly phishing simulations; mandatory annual training; completion tracking | A.6.3 | PR.AT | GRC Lead | 0.10 | 🟢 Treated |
| **R-015** | Contractor onboarded without background check | People | Malicious insider | Inconsistent screening process | 0.3 | 0.8 | **0.24** | Mitigate: All contractors subject to screening policy; tracked in Jira | A.6.1 | GV.RR | HR / GRC | 0.08 | 🟢 Treated |

### Category 5: Regulatory & Legal

| ID | Risk Description | Asset | Threat | Vulnerability | L | I | Score | Treatment | ISO Control | NIST CSF | Risk Owner | Residual Risk | Status |
|----|-----------------|-------|--------|--------------|---|---|-------|-----------|-------------|----------|------------|--------------|--------|
| **R-016** | Act 854 CSSP licence not obtained before regulatory deadline | NACSA Licence | Regulatory | Application pending | 0.4 | 0.9 | **0.36** | Transfer: Engage legal counsel; expedite NACSA application; accept risk with board sign-off | A.5.31 | GV.PO | CEO | 0.25 | 🔴 Open |
| **R-017** | PDPA breach notification failure (within required timeframe) | Regulatory | Regulatory penalty | No formal BN procedure | 0.4 | 0.8 | **0.32** | Mitigate: Create and test breach notification procedure; train GRC team | A.5.24, A.5.34 | RS.CO | CISO (DPO) | 0.16 | 🟡 In Progress |
| **R-018** | Supply chain attack via compromised open-source tool (e.g., Wazuh) | SOC Platform | Supply chain threat | Delayed patching; no SBOM | 0.3 | 0.9 | **0.27** | Mitigate: 30-day patch SLA; verify checksums; SBOM initiative planned | A.5.21, A.8.8 | GV.SC | Platform Eng Lead | 0.15 | 🟡 In Progress |

---

## Risk Summary

| Risk Level | Count | IDs |
|-----------|-------|-----|
| 🔴 Open (RR > 0.20) | 3 | R-001, R-008, R-016 |
| 🟡 In Progress | 6 | R-002, R-006, R-009, R-011, R-013, R-017, R-018 |
| 🟢 Treated | 9 | R-003, R-004, R-005, R-007, R-010, R-012, R-014, R-015 |

> **Management note:** The three open high-residual risks (R-001, R-008, R-016) have
> been accepted by the Board pending remediation. R-001 (alert fatigue) is the most
> operationally significant and is subject to a dedicated SOAR implementation project
> (Q1 2025 target). R-016 (Act 854 licence) is beyond SecureNusantara's direct control
> but is actively managed via legal escalation.

---

## Risk Treatment Plan Schedule

| ID | Treatment Action | Owner | Target Date | Progress |
|----|-----------------|-------|------------|---------|
| R-001 | Deploy Shuffle SOAR playbooks for top 10 alert types | Platform Eng | 2025-03-31 | 60% |
| R-001 | Reduce Wazuh false positive rate to <30% | Platform Eng | 2025-06-30 | 20% |
| R-006 | Enable AWS Security Hub CSPM for all client accounts | Cloud Security | 2025-02-28 | 80% |
| R-008 | Implement PD-aware data routing (Azure Malaysia for PD logs) | Platform Eng | 2025-04-30 | 30% |
| R-009 | Multi-AZ deployment for Wazuh indexer | Platform Eng | 2025-02-28 | 90% |
| R-011 | Automated data deletion job at contract termination + 90 days | Platform Eng | 2025-05-31 | 10% |
| R-013 | Document SOC runbooks in Confluence (all Tier 2 procedures) | SOC Manager | 2025-03-31 | 40% |
| R-016 | Submit NACSA CSSP licence application (full) | CEO / Legal | 2025-01-31 | 95% |
| R-017 | Develop and test PDPA breach notification procedure | GRC Lead | 2025-02-28 | 50% |
| R-018 | Establish SBOM process for open-source tools | Platform Eng | 2025-06-30 | 5% |

---

*Document Owner: CISO | Approved by: CEO | Next Review: Quarterly (next: 2025-04-15)*
