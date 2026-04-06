# 🏗️ Organisational Structure – SecureNusantara Sdn. Bhd.

**Document ID:** SN-ORG-001  
**Version:** 1.1  
**Classification:** Internal  
**Owner:** Chief Executive Officer  
**Last Reviewed:** 2025-01-15  

---

## 1. Organisational Chart

```
                        ┌─────────────────────┐
                        │  Board of Directors  │
                        └──────────┬──────────┘
                                   │
                        ┌──────────▼──────────┐
                        │  Chief Executive     │
                        │  Officer (CEO)       │
                        └──────────┬──────────┘
                                   │
          ┌────────────────────────┼─────────────────────────┐
          │                        │                         │
┌─────────▼──────────┐  ┌──────────▼──────────┐  ┌──────────▼──────────┐
│  Chief Information  │  │  Chief Operating    │  │  Chief Financial    │
│  Security Officer   │  │  Officer (COO)      │  │  Officer (CFO)      │
│  (CISO / vCISO)    │  └──────────┬──────────┘  └─────────────────────┘
└─────────┬──────────┘             │
          │              ┌─────────▼──────────┐
          │              │  SOC Manager        │
          │              └─────────┬──────────┘
          │                        │
          │         ┌──────────────┼──────────────┐
          │   ┌──────▼──────┐ ┌────▼──────┐ ┌────▼──────┐
          │   │  Tier 1     │ │  Tier 2   │ │  Tier 3   │
          │   │  Analysts   │ │  Analysts │ │  Analysts │
          │   │  (×8)       │ │  (×5)     │ │  (×3)     │
          │   └─────────────┘ └───────────┘ └───────────┘
          │
    ┌─────▼──────────────────────────────────────────┐
    │               CISO Direct Reports              │
    │                                                │
    │  ┌──────────────┐  ┌──────────────┐            │
    │  │ GRC Team     │  │ Threat Intel │            │
    │  │ (×3)         │  │ Team (×4)    │            │
    │  └──────────────┘  └──────────────┘            │
    │                                                │
    │  ┌──────────────┐  ┌──────────────┐            │
    │  │ Platform Eng │  │ Cloud        │            │
    │  │ Team (×5)    │  │ Security (×3)│            │
    │  └──────────────┘  └──────────────┘            │
    └────────────────────────────────────────────────┘
```

---

## 2. Leadership Team

| Role | Name (Fictional) | Responsibilities |
|------|-----------------|-----------------|
| CEO | Hafiz Ramli | Overall company direction, board reporting, client relationships |
| CISO / vCISO | Nadia Sulaiman | ISO 27001 ownership, GRC oversight, security strategy |
| COO | Rashdan Ismail | SOC operations, SLA management, delivery quality |
| CFO | Siti Aminah | Financial management, contract commercials |
| SOC Manager | Amirul Hazwan | Day-to-day SOC management, escalation handling |

---

## 3. Security Operations Centre (SOC)

### 3.1 Tier Structure

| Tier | Count | Role | MTTD Target |
|------|-------|------|-------------|
| **Tier 1** | 8 analysts | Initial triage, alert qualification, ticket creation | 15 min |
| **Tier 2** | 5 analysts | In-depth investigation, threat hunting, escalation | 60 min |
| **Tier 3** | 3 analysts | Advanced IR, malware analysis, threat research | Situational |

**Shift pattern:** 3 shifts × 24 hours. Weekday shifts covered by 3–4 T1 analysts + 1–2 T2.
Weekends/holidays: reduced to 2 T1 + 1 T2, with T3 on-call.

### 3.2 SOC Tooling Responsibilities

| Tool | Primary Owner | Backup |
|------|--------------|--------|
| Wazuh (SIEM) | Platform Eng | SOC Manager |
| TheHive (Case Mgmt) | SOC Manager | T2 Lead |
| Shuffle (SOAR) | Platform Eng | T3 Lead |
| MISP (TI) | Threat Intel Team | T3 Lead |
| OpenCTI (TI) | Threat Intel Team | T3 Lead |

---

## 4. Governance, Risk & Compliance (GRC) Team

| Role | Name (Fictional) | Focus |
|------|-----------------|-------|
| GRC Lead | Farhana Mohd | ISO 27001 project lead, internal audit coordination |
| GRC Analyst | Zulaikha Noor | Risk register, SoA maintenance, policy review |
| GRC Analyst | Derrick Tan | Regulatory compliance (PDPA, Act 854), training |

**Key responsibilities:**
- Maintaining ISMS documentation and version control
- Scheduling and conducting internal audits
- Tracking corrective actions in Jira
- Preparing evidence packages for external audit
- Client-facing GRC advisory (subset of professional services)

> **Reality check:** Three GRC persons for an MSSP of 120 people, serving 40+ clients,
> is lean. The team is perpetually under pressure. Prioritisation is critical — the ISO
> 27001 certification drive has consumed ~60% of GRC capacity for 5 months. This creates
> a risk of neglecting client-facing GRC obligations.

---

## 5. Threat Intelligence Team

| Role | Name (Fictional) | Focus |
|------|-----------------|-------|
| TI Lead | Izzati Razak | Strategic intelligence, client threat bulletins |
| TI Analyst | Azlan Haris | Tactical intelligence, IOC management (MISP) |
| TI Analyst | Priya Selvam | OSINT, dark web monitoring |
| TI Analyst | Wei Liang Ong | OpenCTI administration, STIX/TAXII feeds |

---

## 6. Platform Engineering Team

| Role | Name (Fictional) | Focus |
|------|-----------------|-------|
| Platform Eng Lead | Farid Kamarudin | Architecture, tool integration, capacity planning |
| Senior Engineer | Nurul Syafiqah | Wazuh administration, SIEM tuning |
| Engineer | Bryan Lim | Shuffle SOAR development, API integrations |
| Engineer | Mohamad Faris | Elasticsearch/OpenSearch cluster management |
| Engineer | Dinesh Kumar | Network security, firewall rule management |

---

## 7. Cloud Security Team

| Role | Name (Fictional) | Focus |
|------|-----------------|-------|
| Cloud Security Lead | Azman Saad | CSPM, cloud architecture review |
| Cloud Security Eng | Mei Ling Chong | AWS Security Hub, DevSecOps |
| Cloud Security Eng | Khairul Anwar | Azure Defender, IAM reviews |

---

## 8. ISMS Roles & Responsibilities

In the context of ISO 27001:2022, specific ISMS roles are assigned:

| ISMS Role | Assigned To | Responsibility |
|-----------|------------|----------------|
| **ISMS Owner** | CISO (Nadia Sulaiman) | Overall ISMS accountability |
| **Risk Owner** | CISO + Department Heads | Own risks within their area |
| **Internal Auditor** | GRC Lead (Farhana Mohd) | Conduct internal audits (independent of operations) |
| **Management Representative** | COO (Rashdan Ismail) | Management review chair |
| **Document Controller** | GRC Analyst (Zulaikha Noor) | Version control, document register |
| **Asset Owner** | Platform Eng Lead | IT asset inventory |
| **Data Protection Officer (DPO)** | GRC Lead | PDPA compliance oversight |

> **Independence note:** The GRC Lead conducting internal audits while also being the ISO
> project lead creates a potential independence conflict. SecureNusantara mitigates this
> by engaging an external consultant for one of two annual internal audits. For the pre-
> certification audit, an external consultant conducted the internal audit to ensure
> objectivity. This cost ~RM 15,000 but is well justified for audit defensibility.

---

## 9. Communication & Escalation Matrix

| Scenario | First Contact | Escalation 1 | Escalation 2 |
|----------|-------------|-------------|-------------|
| Security incident (client) | T1 Analyst | T2 Analyst | SOC Manager → CISO |
| ISMS non-conformity | GRC Analyst | GRC Lead | CISO |
| Regulatory breach | GRC Lead | CISO | CEO + Legal |
| SOC availability < SLA | SOC Manager | COO | CEO |
| Data breach (personal data) | GRC Lead (DPO) | CISO + CEO | NACSA + PDPD |

---

*Document Owner: CEO | Approved by: Board of Directors | Next Review: 2026-01-15*
