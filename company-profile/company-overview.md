# 🏢 Company Profile: SecureNusantara Sdn. Bhd.

**Document ID:** SN-CP-001  
**Version:** 1.0  
**Classification:** Internal  
**Owner:** Chief Executive Officer  
**Last Reviewed:** 2025-01-15  

---

## 1. Company Overview

| Field | Detail |
|-------|--------|
| **Legal Name** | SecureNusantara Sdn. Bhd. |
| **Registration No.** | 202201034871 (SSM) |
| **Founded** | 2019 |
| **Headquarters** | Level 8, Menara Cyber, Persiaran APEC, 63000 Cyberjaya, Selangor, Malaysia |
| **Operational Regions** | Klang Valley (primary), Penang, Johor Bahru, East Malaysia (Kuching/KK satellite) |
| **Employees** | ~120 FTE |
| **Annual Revenue** | ~RM 18M (FY2024) |
| **Industry** | Cybersecurity / Managed Security Services |
| **MSC Status** | MSC Malaysia Certified (Bill of Guarantee holder) |

---

## 2. Mission & Vision

**Mission:**  
To deliver reliable, transparent, and operationally excellent managed security services that
enable Malaysian organisations to operate securely in a digital-first world.

**Vision:**  
To be Malaysia's most trusted MSSP, recognised for our open, auditable, and human-centred
approach to cybersecurity — without compromising on technical depth.

---

## 3. Core Services

### 3.1 Security Operations Centre (SOC)
- 24×7×365 monitoring across client environments
- Tiered analyst model (Tier 1–3) with defined escalation SLAs
- SIEM-driven correlation (Wazuh) with SOAR automation (Shuffle)
- Multi-tenant architecture with strict client data segregation

### 3.2 Vulnerability Management
- Continuous scanning (Nessus, OpenVAS)
- Risk-prioritised remediation advisory
- Monthly vulnerability reports with executive summaries
- Integration with client patch management workflows

### 3.3 Threat Intelligence
- Tactical, operational, and strategic threat intelligence
- OSINT + commercial feed aggregation via MISP and OpenCTI
- Sector-specific threat bulletins (finance, government, healthcare)
- IOC enrichment and dissemination to SOC analysts

### 3.4 Incident Response (IR)
- Retainer-based IR for Priority clients
- 4-hour on-site/remote response SLA (Platinum tier)
- Digital forensics capability (FTK Imager, Volatility)
- Post-incident reports mapped to MITRE ATT&CK

### 3.5 Cloud Security
- Cloud Security Posture Management (CSPM) — AWS Security Hub, Azure Defender
- IAM review and least-privilege assessment
- CIS Benchmark hardening for cloud workloads
- DevSecOps advisory for client development teams

---

## 4. Customer Segments

| Segment | Representative Clients | Contract Type |
|---------|------------------------|---------------|
| **Government (Federal)** | Ministries, statutory bodies | Annual retainer + MoU |
| **Government (State/Local)** | State digital agencies | Annual retainer |
| **Financial Services** | Licensed banks, e-wallet operators | SLA-based retainer |
| **Critical Information Infrastructure (CII)** | Telco, energy, water utilities | Multi-year retainer |
| **SME** | FinTech startups, e-commerce | Tiered monthly subscription |
| **Healthcare** | Private hospitals | Annual retainer |

> **Business reality check:** Government contracts offer revenue stability but suffer from
> slow procurement cycles (often 9–18 months). SME clients churn at higher rates and
> require more hand-holding. The healthy mix is ~45% government, ~35% financial, ~20% SME.

---

## 5. Technology Stack

### 5.1 Open-Source Tools (Priority)

| Tool | Category | Usage |
|------|----------|-------|
| **Wazuh** | SIEM / EDR | Central log management, rule-based detection, compliance checks |
| **MISP** | Threat Intelligence Platform | IOC sharing, threat feed ingestion, client dissemination |
| **OpenCTI** | Cyber Threat Intelligence | Structured threat intelligence, STIX/TAXII, analyst workflows |
| **TheHive** | Case Management / SOAR | Incident case management, alert triage, evidence tracking |
| **Shuffle** | SOAR / Automation | Playbook automation, API integrations, enrichment workflows |
| **OpenVAS / GVM** | Vulnerability Scanner | Internal network vulnerability scanning |
| **Grafana** | Dashboarding | SOC KPI dashboards, SLA tracking, compliance metrics |
| **Elasticsearch** | Log Storage | Hot/warm/cold log retention architecture |

### 5.2 Commercial Tools

| Tool | Category | Usage |
|------|----------|-------|
| **Nessus Professional** | Vulnerability Scanner | External/credentialed scanning for clients |
| **AWS Security Hub** | CSPM | Cloud posture management for AWS clients |
| **Microsoft Defender for Cloud** | CSPM | Cloud posture management for Azure clients |
| **Jira** | Project / Ticketing | GRC tasks, audit tracking, corrective actions |
| **Confluence** | Documentation | ISMS document repository |

> **Trade-off note:** The heavy reliance on open-source tools reduces licensing costs
> significantly (~RM 400K/year savings vs. full commercial stack), but increases the
> engineering burden. SecureNusantara maintains a dedicated Platform Engineering team
> for tuning, updating, and integrating these tools. Alert tuning in Wazuh alone
> consumes ~20% of a senior engineer's time.

---

## 6. Infrastructure Architecture

### 6.1 Cloud Footprint

```
┌─────────────────────────────────────────────────────────────────┐
│                    SecureNusantara Infrastructure                │
│                                                                 │
│  ┌──────────────────┐   ┌──────────────────┐   ┌────────────┐  │
│  │   AWS ap-          │   │  Azure Southeast │   │  On-Prem   │  │
│  │   southeast-1      │   │  Asia            │   │  SOC (CJ)  │  │
│  │  (Singapore)       │   │  (Malaysia)      │   │            │  │
│  │                  │   │                  │   │            │  │
│  │  - Wazuh indexer │   │  - Azure AD      │   │  - Wazuh   │  │
│  │  - OpenCTI       │   │  - Defender      │   │    agent   │  │
│  │  - MISP          │   │  - Sentinel      │   │    hosts   │  │
│  │  - Elasticsearch │   │    (selective)   │   │  - Network │  │
│  │  - Shuffle       │   │                  │   │    taps    │  │
│  └──────────────────┘   └──────────────────┘   └────────────┘  │
│                                                                 │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │         Client-facing SOC portal (HTTPS/mTLS)           │   │
│  └──────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```

### 6.2 Data Residency
- Malaysian client data is preferentially stored in Azure Malaysia (Kuala Lumpur region)
- Cross-border data transfers require explicit client consent and are governed by PDPA
- ISMS boundary includes AWS Singapore instances with contractual safeguards under PDPA

---

## 7. Revenue Model

| Revenue Stream | % of Revenue | Description |
|----------------|-------------|-------------|
| SOC Retainer | 45% | Monthly fixed fee; tiered (Silver/Gold/Platinum) |
| IR Retainer | 20% | Annual retainer with SLA commitments |
| Vulnerability Management | 15% | Monthly subscription + quarterly reports |
| Threat Intelligence | 10% | Feed + analyst service subscription |
| Professional Services | 10% | One-off assessments, GRC consulting, cloud reviews |

**SLA tiers:**

| Tier | MTTD Target | MTTR Target | Monthly Fee (est.) |
|------|-------------|-------------|-------------------|
| Silver | 4 hours | 24 hours | RM 8,000 |
| Gold | 1 hour | 8 hours | RM 18,000 |
| Platinum | 15 minutes | 4 hours | RM 35,000+ |

---

## 8. Key Business Challenges

### 8.1 Talent Shortage
Malaysia's cybersecurity talent pool is thin. SecureNusantara competes with government
agencies (NACSA, MAMPU) and large MNCs for qualified analysts. Tier 1 SOC roles see
~40% annual turnover. Mitigation: internship pipeline with local universities (UTM, UPM,
UiTM), in-house training programme, and competitive retention packages.

### 8.2 Alert Fatigue
With 200+ Wazuh rules enabled per client environment, analysts face up to 3,000 alerts/day
across all clients. Without aggressive tuning and SOAR automation, analyst burnout is
inevitable. Current false positive rate: ~65% (target: <20%). This is a recognised gap
entering the ISO 27001 audit.

### 8.3 Compliance Pressure
Government clients increasingly require ISO 27001 certification as a tender pre-qualification
criterion. Some financial clients require concurrent alignment with BNM RMiT and PCI-DSS.
Managing multi-framework compliance simultaneously strains the small GRC team (3 persons).

### 8.4 Client Expectations vs. Reality
Clients routinely expect "zero breach" guarantees, which no MSSP can responsibly promise.
Managing client expectations around residual risk, shared responsibility, and detection
(not prevention) as the primary SOC value proposition is an ongoing challenge.

---

## 9. Organisational Culture (Security)

SecureNusantara has a "security-first but not security-only" culture. Security decisions
are always weighed against business impact. The ISO 27001 project is driven by both
genuine security improvement goals and commercial necessity (client procurement
requirements). This dual motivation is healthy — but the team must guard against treating
certification as a destination rather than a continuous journey.

---

*Document Owner: CEO | Approved by: Board of Directors | Next Review: 2026-01-15*
