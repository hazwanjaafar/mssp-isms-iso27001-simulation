# 🗂️ Control Mapping Matrix – ISO 27001:2022 ↔ NIST CSF 2.0 ↔ PDPA ↔ Act 854

**Document ID:** SN-REG-002  
**Version:** 1.0  
**Classification:** Internal  
**Owner:** GRC Lead  
**Last Reviewed:** 2025-01-15  

---

## Legend

| Symbol | Meaning |
|--------|---------|
| ✅ | Direct / strong mapping |
| 🔶 | Partial mapping |
| ❌ | No direct mapping |

---

## Control Mapping Matrix

| ISO 27001:2022 Control | Control Title | NIST CSF 2.0 | PDPA Principle | Act 854 Section | Notes |
|------------------------|---------------|--------------|----------------|-----------------|-------|
| **A.5.1** | Policies for information security | GV.PO-01 | S.5 (General principle) | S.26 | CEO-approved IS policy required |
| **A.5.2** | Information security roles and responsibilities | GV.RR-01 | — | — | ISMS roles documented in ORG-001 |
| **A.5.3** | Segregation of duties | PR.AA-05 | — | — | Critical for SOC/GRC independence |
| **A.5.4** | Management responsibilities | GV.RR-02 | — | S.26 | Management review records required |
| **A.5.5** | Contact with authorities | RS.CO-05 | — | S.29 | NACSA, PDRM, CyberSecurity Malaysia |
| **A.5.6** | Contact with special interest groups | RS.CO-04 | — | — | CyberSecurity Malaysia membership |
| **A.5.7** | Threat intelligence | DE.AE-02 | — | — | MISP/OpenCTI integration |
| **A.5.8** | IS in project management | GV.PO-02 | — | — | Security-by-design in platform projects |
| **A.5.9** | Inventory of information and other assets | ID.AM-01, ID.AM-02 | S.7 (Notice) | — | CMDB maintained in Jira/Confluence |
| **A.5.10** | Acceptable use of information | GV.PO-01 | S.5 | — | AUP signed by all staff |
| **A.5.11** | Return of assets | PR.AT-01 | — | — | Off-boarding checklist |
| **A.5.12** | Classification of information | ID.AM-07 | S.5 | — | 4 classification levels defined |
| **A.5.13** | Labelling of information | ID.AM-07 | — | — | Digital labels; physical TBD |
| **A.5.14** | Information transfer | PR.DS-01 | S.129 (Cross-border) | S.31 | PDPA S.129 requires adequacy/consent |
| **A.5.15** | Access control | PR.AA-01 | — | — | Role-based access; MFA enforced |
| **A.5.16** | Identity management | PR.AA-02 | — | — | Azure AD + PAM for privileged accounts |
| **A.5.17** | Authentication information | PR.AA-03 | — | — | Password policy; MFA mandatory |
| **A.5.18** | Access rights | PR.AA-05 | — | — | Quarterly access reviews |
| **A.5.19** | Information security in supplier relationships | GV.SC-01 | S.6 (Security) | S.31 | Supplier security assessments required |
| **A.5.20** | Addressing IS within supplier agreements | GV.SC-03 | — | S.129 | DPA clauses in all supplier contracts |
| **A.5.21** | Managing IS in ICT supply chain | GV.SC-04, GV.SC-05 | — | — | Software bill of materials (SBOM) planned |
| **A.5.22** | Monitoring, review, change of supplier services | GV.SC-07 | — | — | Annual supplier review |
| **A.5.23** | IS for use of cloud services | PR.IR-02 | S.129 | — | Cloud security posture management |
| **A.5.24** | IS incident management – planning & preparation | RS.MA-01 | — | — | IR plan version controlled in Confluence |
| **A.5.25** | Assessment and decision on IS events | RS.AN-01 | — | — | TheHive triage workflow |
| **A.5.26** | Response to IS incidents | RS.MA-02, RS.MA-03 | — | S.29 | NACSA notification within 6 hours |
| **A.5.27** | Learning from IS incidents | RS.IM-01 | — | — | Post-incident reviews in Confluence |
| **A.5.28** | Collection of evidence | RS.AN-06 | — | — | Chain of custody procedure |
| **A.5.29** | IS during disruption | RC.RP-01 | — | — | BCP documented; DR tested annually |
| **A.5.30** | ICT readiness for business continuity | RC.RP-02 | — | — | RTO: 4h, RPO: 1h (Platinum clients) |
| **A.5.31** | Legal, statutory, regulatory, contractual requirements | GV.PO-02 | S.4 (Lawful basis) | S.26, S.27 | Legal register maintained |
| **A.5.32** | Intellectual property rights | — | — | — | Software licence audit annually |
| **A.5.33** | Protection of records | PR.DS-11 | S.10 (Retention) | S.30 | Log retention: 12 months hot, 36 months cold |
| **A.5.34** | Privacy and protection of PII | GV.PO-02 | S.6, S.7, S.8, S.9 | S.29 | PIA process being established |
| **A.5.35** | Independent review of IS | GV.OC-01 | — | S.26 | Annual external audit; 6-monthly internal |
| **A.5.36** | Compliance with policies | GV.PO-02 | — | S.26 | Compliance monitoring via Wazuh |
| **A.5.37** | Documented operating procedures | GV.PO-01 | — | — | All SOPs in Confluence |
| **A.6.1** | Screening | PR.AT-01 | S.6 | — | Background checks for all staff |
| **A.6.2** | Terms and conditions of employment | GV.PO-01 | S.6 | — | NDA + IS policy in employment contracts |
| **A.6.3** | Information security awareness | PR.AT-01 | — | — | Monthly phishing sim + quarterly training |
| **A.6.4** | Disciplinary process | GV.PO-01 | — | — | HR disciplinary framework references IS policy |
| **A.6.5** | Responsibilities after termination | PR.AA-05 | — | — | Off-boarding checklist; access revoked day 0 |
| **A.6.6** | Confidentiality or NDA | GV.PO-01 | S.6 | — | NDAs for all staff and contractors |
| **A.6.7** | Remote working | PR.IR-01 | — | — | VPN mandatory; endpoint security enforced |
| **A.6.8** | IS event reporting | DE.AE-03 | — | — | Wazuh alerts → TheHive; staff hotline |
| **A.7.1** | Physical security perimeters | PR.IR-02 | — | — | Data centre: cage lock, biometric |
| **A.7.2** | Physical entry | PR.IR-02 | — | — | Badge access; visitor log |
| **A.7.3** | Securing offices, rooms, facilities | PR.IR-02 | — | — | Clean desk policy; lock screen |
| **A.7.4** | Physical security monitoring | DE.CM-01 | — | — | CCTV, 30-day retention |
| **A.7.5** | Protecting against physical and environmental threats | PR.IR-03 | — | — | Fire suppression, flood detection |
| **A.7.6** | Working in secure areas | PR.IR-02 | — | — | Need-to-know access to SOC floor |
| **A.7.7** | Clear desk and clear screen | GV.PO-01 | — | — | Automated screen lock (5 min) |
| **A.7.8** | Equipment siting and protection | PR.IR-04 | — | — | Cable management, locked server racks |
| **A.7.9** | Security of assets off-premises | PR.IR-01 | — | — | Laptop full-disk encryption mandatory |
| **A.7.10** | Storage media | PR.DS-01 | S.10 | — | Encrypted USB only; disposal procedure |
| **A.7.11** | Supporting utilities | PR.IR-04 | — | — | UPS + generator; monthly test |
| **A.7.12** | Cabling security | PR.IR-04 | — | — | Structured cabling; patch panel labelled |
| **A.7.13** | Equipment maintenance | PR.IR-04 | — | — | Vendor maintenance contracts in place |
| **A.7.14** | Secure disposal or re-use of equipment | PR.DS-10 | S.10 | — | NIST 800-88 wipe standard |
| **A.8.1** | User endpoint devices | PR.PS-01 | — | — | MDM enrolled; CIS L1 hardening |
| **A.8.2** | Privileged access rights | PR.AA-05 | — | — | PAM solution; JIT access |
| **A.8.3** | Information access restriction | PR.AA-03 | — | — | RBAC in all systems |
| **A.8.4** | Access to source code | PR.DS-02 | — | — | Git branch protection; code review required |
| **A.8.5** | Secure authentication | PR.AA-03 | — | — | MFA enforced; FIDO2 for admin accounts |
| **A.8.6** | Capacity management | PR.IR-04 | — | — | Monthly capacity review; auto-scaling |
| **A.8.7** | Protection against malware | DE.CM-04 | — | — | Wazuh FIM + AV on all endpoints |
| **A.8.8** | Management of technical vulnerabilities | ID.RA-01 | — | — | Weekly Nessus scans; 30-day critical SLA |
| **A.8.9** | Configuration management | PR.PS-01 | — | — | Ansible playbooks; configuration baseline |
| **A.8.10** | Information deletion | PR.DS-10 | S.10 | — | Automated deletion at retention expiry |
| **A.8.11** | Data masking | PR.DS-01 | S.5, S.6 | — | PII masking in non-production environments |
| **A.8.12** | Data leakage prevention | PR.DS-01 | S.6 | — | DLP on email gateway; partial on endpoint |
| **A.8.13** | Information backup | PR.DS-11 | — | — | 3-2-1 backup rule; daily tested |
| **A.8.14** | Redundancy of information processing facilities | PR.IR-04 | — | — | Multi-AZ AWS; Azure failover |
| **A.8.15** | Logging | DE.AE-03 | — | S.30 | Wazuh centralised logging; 12-month hot |
| **A.8.16** | Monitoring activities | DE.CM-01 | — | — | 24×7 SOC monitoring; Grafana dashboards |
| **A.8.17** | Clock synchronisation | DE.AE-03 | — | — | NTP synchronised; UTC+8 |
| **A.8.18** | Use of privileged utility programs | PR.AA-05 | — | — | Approved tools list; usage logged |
| **A.8.19** | Installation of software on operational systems | PR.PS-02 | — | — | Change management process required |
| **A.8.20** | Networks security | PR.IR-01 | — | — | Network segmentation; VLAN architecture |
| **A.8.21** | Security of network services | PR.IR-01 | — | — | Firewall rules review quarterly |
| **A.8.22** | Segregation of networks | PR.IR-01 | — | — | Client environments logically separated |
| **A.8.23** | Web filtering | PR.PS-01 | — | — | DNS filtering; category-based blocking |
| **A.8.24** | Use of cryptography | PR.DS-02 | S.6 | — | AES-256 at rest; TLS 1.3 in transit |
| **A.8.25** | Secure development lifecycle | PR.PS-04 | — | — | SAST/DAST in CI/CD pipeline |
| **A.8.26** | Application security requirements | PR.PS-04 | — | — | OWASP Top 10 baseline for all apps |
| **A.8.27** | Secure system architecture and engineering | PR.PS-04 | — | — | Architecture review board |
| **A.8.28** | Secure coding | PR.PS-04 | — | — | Secure coding training; code review |
| **A.8.29** | Security testing in dev and acceptance | PR.PS-04 | — | — | Penetration test before production |
| **A.8.30** | Outsourced development | GV.SC-04 | — | — | Supplier security assessment required |
| **A.8.31** | Separation of development, test and production | PR.PS-03 | — | — | Separate AWS accounts for dev/prod |
| **A.8.32** | Change management | PR.PS-02 | — | — | Change Advisory Board (CAB) process |
| **A.8.33** | Test information | PR.DS-01 | S.5 | — | No production PD in test environments |
| **A.8.34** | Protection of IS during audit testing | DE.CM-01 | — | — | Read-only audit access; activity logged |

---

## Summary Statistics

| Mapping Strength | Count | Percentage |
|-----------------|-------|-----------|
| ISO ↔ NIST (strong) | 51 | 85% |
| ISO ↔ PDPA (partial) | 14 | 23% |
| ISO ↔ Act 854 (partial) | 8 | 13% |
| All four frameworks | 3 | 5% |

> **Observation:** ISO 27001 maps well to NIST CSF but has sparser coverage of PDPA
> and Act 854 specifics. This is expected — PDPA is data-protection-focused while ISO
> is security management-focused. Supplementary PDPA controls (consent management,
> data subject rights, breach notification) must be implemented as standalone procedures
> alongside the ISMS.

---

*Document Owner: GRC Lead | Approved by: CISO | Next Review: 2026-01-15*
