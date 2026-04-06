# 📋 Statement of Applicability (SoA) – SecureNusantara Sdn. Bhd.

**Document ID:** SN-ISMS-003  
**Version:** 2.0  
**Classification:** Confidential – Internal  
**Owner:** CISO  
**Last Reviewed:** 2025-01-15  

---

## Introduction

This Statement of Applicability (SoA) documents all ISO/IEC 27001:2022 Annex A controls,
their applicability to SecureNusantara's ISMS, and the justification for inclusion or
exclusion. Where applicable, the implementation status and relevant evidence are noted.

**Total Annex A controls:** 93  
**Applicable:** 91 (97.8%)  
**Not applicable:** 2 (2.2%)  

---

## Legend

| Column | Description |
|--------|-------------|
| **Applicable** | Whether the control is applicable (Yes/No) |
| **Justification** | Reason for inclusion/exclusion |
| **Implementation Status** | Implemented / Partial / Planned / N/A |
| **Evidence Reference** | Document or artefact supporting implementation |

---

## Section A.5 – Organisational Controls

| Control | Title | Applicable | Justification | Status | Evidence |
|---------|-------|-----------|---------------|--------|---------|
| A.5.1 | Policies for IS | ✅ Yes | Core requirement; all MSSP operations | Implemented | SN-POL-001 (IS Policy) |
| A.5.2 | IS roles & responsibilities | ✅ Yes | Required for ISMS operation | Implemented | SN-ORG-001 |
| A.5.3 | Segregation of duties | ✅ Yes | Critical for SOC/GRC independence | Implemented | Access matrix |
| A.5.4 | Management responsibilities | ✅ Yes | ISO clause 5 requirement | Implemented | Management review minutes |
| A.5.5 | Contact with authorities | ✅ Yes | NACSA, PDRM, CyberSecurity Malaysia | Implemented | Authority contact register |
| A.5.6 | Contact with special interest groups | ✅ Yes | CyberSecurity Malaysia, FIRST membership | Partial | Membership records |
| A.5.7 | Threat intelligence | ✅ Yes | Core MSSP service; MISP/OpenCTI | Implemented | TI platform records |
| A.5.8 | IS in project management | ✅ Yes | All platform projects require security review | Partial | Project templates |
| A.5.9 | Inventory of information and other assets | ✅ Yes | Asset management is fundamental | Implemented | CMDB in Confluence |
| A.5.10 | Acceptable use of information | ✅ Yes | All staff must accept AUP | Implemented | AUP + sign-off records |
| A.5.11 | Return of assets | ✅ Yes | Off-boarding controls | Implemented | Off-boarding checklist |
| A.5.12 | Classification of information | ✅ Yes | Client data classification required | Implemented | Classification policy |
| A.5.13 | Labelling of information | ✅ Yes | Digital document labelling | Partial | Label scheme documented; physical pending |
| A.5.14 | Information transfer | ✅ Yes | Client data transfer controls; PDPA S.129 | Implemented | Data transfer agreements |
| A.5.15 | Access control | ✅ Yes | Multi-tenant SOC requires strict access | Implemented | Access control policy |
| A.5.16 | Identity management | ✅ Yes | Azure AD; PAM | Implemented | IAM records |
| A.5.17 | Authentication information | ✅ Yes | Password policy; MFA | Implemented | Auth policy |
| A.5.18 | Access rights | ✅ Yes | RBAC; quarterly reviews | Implemented | Access review reports |
| A.5.19 | IS in supplier relationships | ✅ Yes | Critical suppliers include AWS, Microsoft | Partial | Supplier register; 3/12 assessed |
| A.5.20 | IS within supplier agreements | ✅ Yes | DPA clauses required | Implemented | Contract templates |
| A.5.21 | IS in ICT supply chain | ✅ Yes | Open-source supply chain risk | Partial | SBOM planned |
| A.5.22 | Monitoring of supplier services | ✅ Yes | Annual supplier review | Partial | Review schedule exists; 2 completed |
| A.5.23 | IS for cloud services | ✅ Yes | AWS/Azure are core infrastructure | Implemented | CSPM reports |
| A.5.24 | IS incident management – planning | ✅ Yes | Core SOC function | Implemented | IR Plan SN-IRP-001 |
| A.5.25 | Assessment of IS events | ✅ Yes | TheHive triage workflow | Implemented | TheHive records |
| A.5.26 | Response to IS incidents | ✅ Yes | IR playbooks; NACSA reporting | Implemented | IR procedure SN-PROC-002 |
| A.5.27 | Learning from incidents | ✅ Yes | Post-incident reviews | Partial | PIR reports (8/12 completed) |
| A.5.28 | Collection of evidence | ✅ Yes | Digital forensics; chain of custody | Implemented | Evidence procedure |
| A.5.29 | IS during disruption | ✅ Yes | BCP required for SOC availability | Implemented | BCP SN-BCP-001 |
| A.5.30 | ICT readiness for BCP | ✅ Yes | DR tested annually | Implemented | DR test report |
| A.5.31 | Legal, statutory, regulatory requirements | ✅ Yes | PDPA, Act 854, contracts | Implemented | Legal register |
| A.5.32 | Intellectual property rights | ✅ Yes | Software licensing; open-source compliance | Partial | Licence audit Q4 2024 |
| A.5.33 | Protection of records | ✅ Yes | Audit trail requirements; Act 854 | Implemented | Retention policy |
| A.5.34 | Privacy and protection of PII | ✅ Yes | PDPA obligations; client data | Partial | PIA not yet formalised |
| A.5.35 | Independent review of IS | ✅ Yes | Internal + external audit | Implemented | Audit programme |
| A.5.36 | Compliance with IS policies | ✅ Yes | Wazuh compliance monitoring | Implemented | Compliance dashboard |
| A.5.37 | Documented operating procedures | ✅ Yes | All SOPs documented in Confluence | Implemented | Document register |

## Section A.6 – People Controls

| Control | Title | Applicable | Justification | Status | Evidence |
|---------|-------|-----------|---------------|--------|---------|
| A.6.1 | Screening | ✅ Yes | All staff/contractors | Implemented | HR screening records |
| A.6.2 | Terms and conditions of employment | ✅ Yes | NDA + IS obligations in contracts | Implemented | Employment contracts |
| A.6.3 | IS awareness, education, training | ✅ Yes | Security awareness programme | Implemented | Training records; LMS |
| A.6.4 | Disciplinary process | ✅ Yes | IS policy violations | Implemented | HR disciplinary policy |
| A.6.5 | Responsibilities after termination | ✅ Yes | Access revocation; NDA continuation | Implemented | Off-boarding procedure |
| A.6.6 | Confidentiality or NDA | ✅ Yes | All staff, contractors, third parties | Implemented | NDA templates |
| A.6.7 | Remote working | ✅ Yes | SOC analysts work from home shifts | Implemented | Remote working policy |
| A.6.8 | IS event reporting | ✅ Yes | Staff security hotline + TheHive | Implemented | Reporting procedure |

## Section A.7 – Physical Controls

| Control | Title | Applicable | Justification | Status | Evidence |
|---------|-------|-----------|---------------|--------|---------|
| A.7.1 | Physical security perimeters | ✅ Yes | SOC floor; server room | Implemented | Physical security review |
| A.7.2 | Physical entry | ✅ Yes | Badge access; visitor management | Implemented | Access logs |
| A.7.3 | Securing offices, rooms, facilities | ✅ Yes | SOC is sensitive area | Implemented | Physical inspection report |
| A.7.4 | Physical security monitoring | ✅ Yes | CCTV at SOC; server room | Implemented | CCTV records |
| A.7.5 | Protecting against physical threats | ✅ Yes | Fire, flood, environmental | Implemented | Facilities report |
| A.7.6 | Working in secure areas | ✅ Yes | SOC floor access restrictions | Implemented | Access control records |
| A.7.7 | Clear desk and clear screen | ✅ Yes | SOC handles sensitive data | Implemented | Policy + spot checks |
| A.7.8 | Equipment siting and protection | ✅ Yes | Server room controls | Implemented | Physical inspection |
| A.7.9 | Security of assets off-premises | ✅ Yes | Laptops for remote work | Implemented | Laptop encryption records |
| A.7.10 | Storage media | ✅ Yes | Encrypted USB policy | Implemented | Media control policy |
| A.7.11 | Supporting utilities | ✅ Yes | UPS; generator | Implemented | UPS test records |
| A.7.12 | Cabling security | ✅ Yes | Structured cabling | Implemented | Cabling documentation |
| A.7.13 | Equipment maintenance | ✅ Yes | Vendor maintenance contracts | Implemented | Maintenance records |
| A.7.14 | Secure disposal or re-use | ✅ Yes | NIST 800-88 wipe | Implemented | Disposal records |

## Section A.8 – Technological Controls

| Control | Title | Applicable | Justification | Status | Evidence |
|---------|-------|-----------|---------------|--------|---------|
| A.8.1 | User endpoint devices | ✅ Yes | All staff laptops; MDM | Implemented | MDM enrolment records |
| A.8.2 | Privileged access rights | ✅ Yes | SOC, Platform Eng, Cloud Security | Implemented | PAM records |
| A.8.3 | Information access restriction | ✅ Yes | RBAC across all systems | Implemented | Access matrix |
| A.8.4 | Access to source code | ✅ Yes | Internal tools development | Implemented | Git access controls |
| A.8.5 | Secure authentication | ✅ Yes | MFA enforced; FIDO2 for admins | Implemented | Auth configuration |
| A.8.6 | Capacity management | ✅ Yes | SOC platform scalability | Implemented | Capacity reports |
| A.8.7 | Protection against malware | ✅ Yes | Wazuh FIM + AV | Implemented | Wazuh rules; AV records |
| A.8.8 | Management of technical vulnerabilities | ✅ Yes | Vulnerability management service | Implemented | Nessus scan reports |
| A.8.9 | Configuration management | ✅ Yes | Ansible baselines | Implemented | Configuration records |
| A.8.10 | Information deletion | ✅ Yes | Data retention/deletion | Partial | Manual process; automation planned |
| A.8.11 | Data masking | ✅ Yes | PII in non-production | Partial | Dev environment only |
| A.8.12 | Data leakage prevention | ✅ Yes | DLP on email; partial endpoint | Partial | Email DLP active; endpoint partial |
| A.8.13 | Information backup | ✅ Yes | 3-2-1 backup | Implemented | Backup logs |
| A.8.14 | Redundancy of processing facilities | ✅ Yes | Multi-AZ; multi-cloud | Partial | AWS HA deployed; Azure DR pending |
| A.8.15 | Logging | ✅ Yes | Centralised Wazuh logging | Implemented | Log retention policy; Wazuh records |
| A.8.16 | Monitoring activities | ✅ Yes | 24×7 SOC; Grafana dashboards | Implemented | SOC monitoring records |
| A.8.17 | Clock synchronisation | ✅ Yes | NTP for all systems | Implemented | NTP configuration |
| A.8.18 | Use of privileged utility programs | ✅ Yes | Approved tools list | Implemented | Tools register |
| A.8.19 | Installation of software | ✅ Yes | Change management process | Implemented | Change records |
| A.8.20 | Networks security | ✅ Yes | Firewall; VLAN segmentation | Implemented | Network diagrams |
| A.8.21 | Security of network services | ✅ Yes | Firewall rules; quarterly review | Implemented | Firewall rule reviews |
| A.8.22 | Segregation of networks | ✅ Yes | Client isolation in SOC | Implemented | VLAN architecture |
| A.8.23 | Web filtering | ✅ Yes | DNS filtering | Implemented | Filtering records |
| A.8.24 | Use of cryptography | ✅ Yes | AES-256; TLS 1.3 | Implemented | Cryptography policy |
| A.8.25 | Secure development lifecycle | ✅ Yes | Internal tooling development | Partial | SDL policy exists; SAST partial |
| A.8.26 | Application security requirements | ✅ Yes | SOC portal; client APIs | Partial | OWASP baseline applied |
| A.8.27 | Secure system architecture | ✅ Yes | Architecture review board | Partial | 2/5 reviews conducted |
| A.8.28 | Secure coding | ✅ Yes | Internal developers | Partial | Training done; code review enforced |
| A.8.29 | Security testing | ✅ Yes | Pen test before production | Partial | Annual pen test; last: Nov 2024 |
| A.8.30 | Outsourced development | ✅ Yes | Third-party dev contractors | Implemented | Supplier security requirements |
| A.8.31 | Separation of dev/test/prod | ✅ Yes | Separate AWS accounts | Implemented | AWS account structure |
| A.8.32 | Change management | ✅ Yes | Change Advisory Board | Implemented | CAB records |
| A.8.33 | Test information | ✅ Yes | No production PD in test | Implemented | Data masking records |
| A.8.34 | Protection of IS during audit | ✅ Yes | Audit access controls | Implemented | Audit access logs |

---

## Controls Assessed as Not Applicable

| Control | Title | Justification |
|---------|-------|---------------|
| *(none)* | — | All 93 Annex A controls have been assessed as applicable. Two controls are **Partially implemented** and require further work before the certification audit. |

> **Note:** Having zero exclusions is unusual. SecureNusantara chose to include all
> controls because the MSSP business model creates applicability for virtually every
> control category. The auditor will scrutinise partial implementations more closely
> than exclusions — these must be supported with concrete remediation timelines.

---

## Implementation Summary

| Status | Count | Percentage |
|--------|-------|-----------|
| Implemented | 72 | 77.4% |
| Partial | 19 | 20.4% |
| Planned | 2 | 2.2% |
| N/A | 0 | 0% |

> **Certification readiness concern:** 19 partial controls entering the external audit
> creates significant risk of minor non-conformities. The GRC team has assessed that
> all partial controls can be evidenced with a credible implementation plan and partial
> evidence, which is generally acceptable for certification. However, any partial control
> with **no** evidence or plan will be raised as a non-conformity.

---

*Document Owner: CISO | Approved by: CEO | Next Review: 2025-06-15 (pre-certification)*
