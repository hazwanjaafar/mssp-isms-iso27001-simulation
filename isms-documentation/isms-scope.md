# 🎯 ISMS Scope Statement – SecureNusantara Sdn. Bhd.

**Document ID:** SN-ISMS-001  
**Version:** 1.3  
**Classification:** Internal  
**Owner:** CISO  
**Last Reviewed:** 2025-01-15  

---

## 1. Scope Statement

The Information Security Management System (ISMS) of SecureNusantara Sdn. Bhd. covers
the **design, delivery, operation, and support of managed cybersecurity services**,
including Security Operations Centre (SOC) monitoring, threat intelligence, vulnerability
management, incident response retainer, and cloud security advisory services.

The ISMS boundary encompasses:

- **Headquarters:** Level 8, Menara Cyber, Cyberjaya, Selangor (primary ISMS boundary)
- **Cloud infrastructure:** AWS ap-southeast-1 (Singapore) and Azure Southeast Asia
  (Malaysia) environments used for SOC platform hosting and data processing
- **On-premises SOC components:** Network taps, Wazuh agent hosts, and SOC workstations
  at Cyberjaya HQ

---

## 2. Boundaries and Interfaces

### 2.1 In Scope

| Component | Description |
|-----------|-------------|
| SOC Platform | Wazuh SIEM, TheHive, Shuffle, Elasticsearch — production instances |
| Threat Intelligence Platform | MISP, OpenCTI — production instances |
| Vulnerability Management | Nessus, OpenVAS — scanning infrastructure |
| Cloud Infrastructure | AWS and Azure tenancies used for MSSP platform hosting |
| Corporate IT | Laptops, email, collaboration tools (Microsoft 365), Confluence, Jira |
| People | All SecureNusantara employees, contractors, and interns |
| Physical Premises | Cyberjaya HQ SOC floor and server room |
| Client-facing Interfaces | SOC portal, API integrations, VPN tunnels to client environments |

### 2.2 Explicitly Out of Scope

| Component | Reason |
|-----------|--------|
| Client-owned infrastructure | Clients retain responsibility for their own ISMS |
| Penang and JB satellite offices | No significant IS processing; covered under corporate IT policy |
| Third-party managed services (e.g., Microsoft 365 cloud infra) | Supplier responsibility; covered under supplier agreements |

---

## 3. Context of the Organisation

### 3.1 Internal Context

| Factor | Relevance |
|--------|-----------|
| Growth trajectory | Rapid headcount and client growth increases attack surface |
| Open-source tooling | Engineering overhead; requires disciplined patch management |
| Multi-tenant SOC | Client data segregation is a critical control requirement |
| Talent constraints | Staff turnover affects security posture and knowledge continuity |

### 3.2 External Context

| Factor | Relevance |
|--------|-----------|
| Malaysian regulatory environment | PDPA, Act 854, BNM RMiT (for financial clients) |
| Threat landscape | MSSPs are high-value targets; supply chain attacks are rising |
| Client procurement requirements | ISO 27001 increasingly mandatory for government tenders |
| Technology evolution | Cloud-native shifts require continuous architecture review |

---

## 4. Interested Parties

| Interested Party | IS Requirements |
|-----------------|----------------|
| Clients (government, finance, SME) | Confidentiality of their data; reliable SOC service; incident notification |
| Employees | Safe working environment; personal data protection |
| Regulators (NACSA, PDPD, BNM) | Compliance with Act 854, PDPA, RMiT |
| Shareholders / Board | Risk management; business continuity; reputational protection |
| Suppliers | Clear contractual IS requirements; payment terms |
| NACSA | CSSP licence compliance; incident reporting |

---

## 5. Certification Boundary

The ISO/IEC 27001:2022 certification is sought for the following scope statement
(as it will appear on the certificate):

> *"The provision of managed cybersecurity services including Security Operations Centre
> (SOC) monitoring, threat intelligence, vulnerability management, incident response
> retainer, and cloud security advisory services, delivered from SecureNusantara's
> headquarters at Cyberjaya, Selangor and supporting cloud infrastructure."*

---

## 6. Exclusions

No Annex A controls are excluded from consideration. Controls assessed as not applicable
are documented in the Statement of Applicability (SoA) with justification.

---

*Document Owner: CISO | Approved by: CEO | Next Review: 2026-01-15*
