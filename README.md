# 🛡️ ISO/IEC 27001:2022 Implementation Simulation – MSSP (Malaysia)

> **⚠️ DISCLAIMER: This repository is strictly for educational and learning purposes only.**
> All company names, personnel, clients, and scenarios are entirely fictional. No real
> credentials, sensitive data, or proprietary information is included.

---

## Overview

This repository is a fictional ISO/IEC 27001:2022 implementation simulation for **SecureNusantara Sdn. Bhd.**, a Malaysia-based Managed Security Service Provider (MSSP). It is designed for educational use and includes documentation for ISMS scope, risk management, policies, internal audit activities, and pre-certification readiness.

It also demonstrates alignment with **ISO/IEC 27001:2022**, **NIST CSF 2.0**, **Malaysia PDPA (2010)**, and **Malaysia Act 854 (Cybersecurity Act 2024)**.

This repository simulates a **real-world ISO/IEC 27001:2022 implementation** for a fictional
Managed Security Service Provider (MSSP) based in Malaysia — **SecureNusantara Sdn. Bhd.**

The simulation covers end-to-end ISMS implementation from scoping through pre-certification
audit readiness, including alignment with:

| Framework / Regulation | Relevance |
|---|---|
| ISO/IEC 27001:2022 | Core ISMS certification standard |
| NIST CSF 2.0 | Operational security framework alignment |
| Malaysia PDPA (2010) | Personal data protection obligations |
| Malaysia Act 854 (Cybersecurity Act 2024) | National cybersecurity regulatory compliance |

---

## 📁 Repository Structure

```
mssp-iso27001-simulation/
│
├── README.md                          ← This file
├── .gitignore
├── securenusantara.html               ← Consolidated HTML simulation document
│
├── company-profile/
│   └── company-overview.md            ← Fictional MSSP company profile
│
├── org-structure/
│   └── organizational-structure.md   ← Org chart, roles & responsibilities
│
├── regulatory-alignment/
│   ├── framework-alignment.md         ← Why each framework applies & alignment strategy
│   └── control-mapping-matrix.md      ← ISO ↔ NIST ↔ PDPA ↔ Act 854 control matrix
│
├── isms-documentation/
│   ├── isms-scope.md                  ← ISMS scope statement
│   ├── risk-register.md               ← Full risk register (likelihood × impact)
│   ├── statement-of-applicability.md  ← SoA (Annex A controls)
│   └── policies/
│       ├── access-control-policy.md
│       ├── incident-response-policy.md
│       ├── asset-management-policy.md
│       └── risk-management-policy.md
│
├── procedures/
│   ├── access-control-procedure.md    ← Step-by-step access control procedures
│   ├── incident-response-procedure.md ← SOC alert → incident → closure workflow
│   ├── asset-management-procedure.md  ← Asset lifecycle management
│   └── risk-management-procedure.md  ← Risk assessment & treatment procedure
│
├── internal-audit/
│   ├── audit-program.md               ← Annual internal audit programme
│   ├── audit-checklist.md             ← ISO 27001:2022 control checklist
│   └── audit-findings.md              ← Findings, NCRs, corrective actions
│
├── audit-readiness/
│   ├── management-review.md           ← Management review meeting simulation
│   └── audit-readiness-checklist.md   ← Pre-certification readiness checklist
│
└── soc-integration/
    └── soc-integration.md             ← ISMS embedded in SOC operations
```

---

## 🎯 Scope of Simulation

This simulation covers **Steps 4–7** of the ISO 27001 implementation lifecycle immediately
preceding an external certification audit:

| Step | Description |
|------|-------------|
| **Step 4** | Develop supporting procedures (Access Control, IR, Asset Mgmt, Risk Mgmt) |
| **Step 5** | Establish and control ISMS documentation (scope, risk register, SoA, policies) |
| **Step 6** | Internal audit simulation with findings, NCRs, and corrective actions |
| **Step 7** | Final management review and audit readiness preparation |

---

## 🏢 Fictional Company: SecureNusantara Sdn. Bhd.

- **HQ:** Cyberjaya, Selangor, Malaysia
- **Services:** SOC, Vulnerability Management, Threat Intelligence, Incident Response, Cloud Security
- **Clients:** Government agencies, financial institutions, SMEs
- **Tech Stack:** Wazuh · MISP · OpenCTI · TheHive · Shuffle · Nessus · OpenVAS
- **Infrastructure:** AWS + Azure hybrid cloud + on-prem SOC

See [`company-profile/company-overview.md`](company-profile/company-overview.md) for full details.

---

## 🧩 Key Deliverables

| # | Deliverable | Location |
|---|-------------|----------|
| 1 | Organizational Structure | [`org-structure/organizational-structure.md`](org-structure/organizational-structure.md) |
| 2 | Risk Register | [`isms-documentation/risk-register.md`](isms-documentation/risk-register.md) |
| 3 | Control Mapping Matrix | [`regulatory-alignment/control-mapping-matrix.md`](regulatory-alignment/control-mapping-matrix.md) |
| 4 | Sample Policy (Access Control) | [`isms-documentation/policies/access-control-policy.md`](isms-documentation/policies/access-control-policy.md) |
| 5 | Internal Audit Checklist | [`internal-audit/audit-checklist.md`](internal-audit/audit-checklist.md) |
| 6 | Statement of Applicability | [`isms-documentation/statement-of-applicability.md`](isms-documentation/statement-of-applicability.md) |
| 7 | Audit Readiness Checklist | [`audit-readiness/audit-readiness-checklist.md`](audit-readiness/audit-readiness-checklist.md) |

---

## 🚀 Future Planning

- [ ] Add interactive HTML/dashboard version of the Risk Register
- [ ] Add SOAR playbook examples (Shuffle workflows)
- [ ] Add Wazuh SIEM rule examples aligned to ISO controls
- [ ] Add sample evidence artefacts (anonymised log excerpts, report templates)
- [ ] Add gap analysis tool (Python/spreadsheet)
- [ ] Translate key documents to Bahasa Malaysia
- [ ] Add supplier/third-party risk assessment template

---

## 📄 Licence & Usage

This project is released for **educational purposes only** under the
[MIT Licence](https://opensource.org/licenses/MIT).

You are free to adapt, fork, and build upon this simulation for learning,
training, or academic work. **Do not** use any content here as-is in a real
certification engagement without independent review by a qualified ISMS consultant.

---

*Maintained by [@hazwanjaafar](https://github.com/hazwanjaafar)*

