# ⚖️ Risk Management Procedure

**Document ID:** SN-PROC-004  
**Version:** 1.1  
**Classification:** Internal  
**Owner:** GRC Lead  
**Approved by:** CISO  
**Last Reviewed:** 2025-01-15  
**Next Review:** 2026-01-15  

---

## 1. Purpose & Scope

This procedure provides step-by-step guidance for conducting information security risk
assessments and managing risk treatments. It implements the Risk Management Policy (SN-POL-005).

---

## 2. Annual Risk Assessment Process

### 2.1 Preparation (Month 1, Weeks 1–2)

| Step | Action | Responsible |
|------|--------|------------|
| 1 | GRC Lead schedules annual risk assessment workshop (2 days) | GRC Lead |
| 2 | Invite: CISO, SOC Manager, Platform Eng Lead, Cloud Security Lead, TI Lead | GRC Lead |
| 3 | Distribute Risk Register (SN-ISMS-002) for pre-workshop review | GRC Lead |
| 4 | Collect threat intelligence inputs (TI Lead provides current threat landscape briefing) | TI Lead |
| 5 | Review previous year's incident log for risk validation | GRC Analyst |
| 6 | Review regulatory changes (PDPA, Act 854 updates) | GRC Analyst |

### 2.2 Risk Identification Workshop (Day 1)

**Facilitation method:** Structured brainstorming by asset category

Asset categories to cover:
1. SOC Platform (Wazuh, TheHive, Shuffle, Elasticsearch)
2. Threat Intelligence Platform (MISP, OpenCTI)
3. Cloud Infrastructure (AWS, Azure)
4. Corporate IT (laptops, M365, network)
5. Client Data and Client Interfaces
6. People and Organisational
7. Third-party Suppliers
8. Regulatory and Legal

For each category, identify:
- **Threats:** What could go wrong? (Wazuh outage, data breach, ransomware, regulatory fine...)
- **Vulnerabilities:** What weakness enables the threat? (Unpatched software, lack of MFA...)
- **Impacts:** What is the consequence? (Financial, operational, reputational, legal)

**Output:** Longlist of risks (minimum 15; typically 30–50 for MSSP scope)

### 2.3 Risk Scoring Workshop (Day 2)

For each risk on the longlist:

| Step | Action |
|------|--------|
| 1 | Assign Likelihood (L) using 0.1–1.0 scale (group consensus) |
| 2 | Assign Impact (I) using 0.1–1.0 scale (group consensus) |
| 3 | Calculate inherent risk score: R = L × I |
| 4 | Identify existing controls and estimate residual risk (RR) |
| 5 | Assign Risk Owner |
| 6 | Shortlist risks requiring treatment (RR > 0.15) |

**Scoring guidance:**

| Likelihood | Score | Example |
|-----------|-------|---------|
| Rare (once in 5+ years) | 0.1 | Lightning strike on data centre |
| Unlikely (once in 2–5 years) | 0.3 | Advanced nation-state attack on MSSP |
| Possible (once per year) | 0.5 | Phishing leading to credential compromise |
| Likely (several times per year) | 0.7 | SOC alert fatigue incident |
| Almost certain (monthly) | 1.0 | Wazuh false positive events |

| Impact | Score | Example |
|--------|-------|---------|
| Negligible | 0.1 | Minor inconvenience; no data affected |
| Minor | 0.3 | Service degraded; no client data affected |
| Significant | 0.5 | Client SLA breach; internal data exposed |
| Major | 0.7 | Client data breach; regulatory penalty |
| Catastrophic | 1.0 | Multiple client breaches; company viability threatened |

---

## 3. Risk Treatment Planning

### 3.1 Selecting Treatment Options

For risks with RR > 0.15 (requiring treatment):

```
               High Likelihood
                    │
      ┌─────────────▼─────────────────┐
      │       MITIGATE                │ ← Reduce likelihood or impact
      │  (controls, procedures,       │   through technical or
      │   automation, training)       │   organisational controls
      └──────────────────────────────┘
               Low Likelihood
                    │
      ┌─────────────▼─────────────────┐
      │  TRANSFER or ACCEPT           │ ← Insurance; contractual
      │  (if impact is high:          │   transfer; or accept if
      │   transfer via insurance)     │   within risk appetite
      └──────────────────────────────┘
```

For risks where the threat source can be eliminated:
→ **AVOID:** Discontinue the service/activity that creates the risk.

### 3.2 Risk Treatment Plan Documentation

For each risk requiring treatment, document in the Risk Register:

| Field | Content |
|-------|---------|
| Treatment option | Mitigate / Transfer / Accept / Avoid |
| Treatment action(s) | Specific, measurable actions |
| Owner | Named individual (not a team) |
| Target date | Specific date |
| Resources required | Budget, tooling, staffing |
| Residual risk (post-treatment) | Expected RR after treatment |

### 3.3 Approval

| Residual Risk Level | Approval Required |
|--------------------|------------------|
| RR ≤ 0.15 (Acceptable) | Risk Owner can accept |
| 0.15 < RR ≤ 0.30 (Monitor) | CISO approval |
| RR > 0.30 (Unacceptable) | CEO + Board sign-off |

---

## 4. Ongoing Risk Monitoring

### 4.1 Monthly Risk Dashboard

GRC publishes monthly risk dashboard in Grafana:
- Total risks by status (Open / In Progress / Treated)
- Risks by residual risk level (Red / Amber / Green)
- Treatment actions due this month (overdue highlighted)
- New risks identified since last month

### 4.2 Quarterly Risk Register Review

| Step | Action | Responsible |
|------|--------|------------|
| 1 | GRC exports current risk register | GRC Analyst |
| 2 | Update treatment action progress | Risk Owners (input to GRC) |
| 3 | Add any new risks identified since last review | GRC Lead |
| 4 | Re-score risks where context has changed (e.g., new threat actor TTP) | GRC Lead + TI Lead |
| 5 | CISO reviews updated register | CISO |
| 6 | Register presented at Management Review | CISO |

### 4.3 Event-Triggered Risk Reviews

A risk review must be triggered by:
- P1 or P2 security incident (within 5 working days post-PIR)
- Significant regulatory change (PDPA amendment, Act 854 guidance update)
- Major infrastructure change (new cloud region, new SOC tool)
- New significant client (large government or financial sector client)
- Near-miss event

---

## 5. Integration with SOC and Threat Intelligence

### 5.1 Threat Intelligence → Risk Inputs

TI Lead provides quarterly threat landscape briefing including:
- Emerging threat actors targeting MSSPs in ASEAN
- New TTPs relevant to SecureNusantara's client sectors
- Vulnerability exploitation trends

These inform likelihood scores in the risk register.

### 5.2 Wazuh → Risk Validation

High-frequency Wazuh alerts (top 20 by volume) are reviewed monthly to:
- Validate that corresponding risks are captured in the Risk Register
- Adjust likelihood scores if alert frequency changes

### 5.3 Risk → SOC Prioritisation

High-residual risks that have SOC detection implications are:
- Translated into Wazuh detection rules (coordinated with Platform Eng)
- Added to SOC analyst training scenarios
- Included in threat hunting focus areas

---

## 6. Risk Statement Format

All risks must be documented using a consistent risk statement format:

> *"The risk of [threat/event] occurring due to [vulnerability/weakness], resulting in [impact on confidentiality/integrity/availability/legal]."*

**Example:**
> *"The risk of a SOC analyst exfiltrating client data occurring due to excessive privileged access and insufficient monitoring, resulting in loss of client confidentiality and regulatory penalties under PDPA."*

---

## 7. Evidence & Records

| Record | Storage | Retention |
|--------|---------|-----------|
| Risk Register (SN-ISMS-002) | Confluence | Ongoing (5 years version history) |
| Risk assessment workshop outputs | Confluence | 5 years |
| Risk treatment sign-off | Jira tickets | 5 years |
| Management review risk reports | Confluence | 5 years |
| Quarterly risk review notes | Confluence | 5 years |

---

*Document Owner: GRC Lead | Approved by: CISO | Next Review: 2026-01-15*
