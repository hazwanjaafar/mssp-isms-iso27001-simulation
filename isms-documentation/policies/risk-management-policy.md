# ⚖️ Risk Management Policy

**Document ID:** SN-POL-005  
**Version:** 1.2  
**Classification:** Internal  
**Owner:** CISO  
**Approved by:** CEO  
**Last Reviewed:** 2025-01-15  
**Next Review:** 2026-01-15  

---

## 1. Purpose

This policy establishes SecureNusantara's framework for identifying, assessing, treating,
and monitoring information security risks. It ensures that risk management is systematic,
consistent, and aligned with the organisation's risk appetite and business objectives.

---

## 2. Scope

This policy applies to all information security risks associated with SecureNusantara's
operations within the ISMS boundary, including risks arising from:
- Internal processes and people
- Technology and infrastructure
- Third-party suppliers and clients
- Legal and regulatory obligations

---

## 3. Risk Appetite

SecureNusantara's board has defined the following risk appetite:

| Risk Domain | Appetite | Rationale |
|-------------|---------|-----------|
| Client data confidentiality | **Zero tolerance** | Breach would be catastrophic to business reputation |
| SOC service availability | **Low** | SLA breaches have direct financial and contractual consequences |
| Regulatory compliance | **Low** | Non-compliance threatens operating licence and client contracts |
| Operational efficiency | **Moderate** | Accepts some operational risk to support innovation |
| Financial risk (non-security) | **Moderate** | Normal commercial risk tolerance |

**Residual risk threshold:** Risks with a residual score > 0.30 (post-treatment) are considered
**unacceptable** and require escalation to the CISO and CEO for decision.

---

## 4. Risk Management Process

### 4.1 Risk Identification

Risks are identified through:
- Annual risk assessment workshops (facilitated by GRC team)
- Continuous monitoring outputs (Wazuh alerts, vulnerability scans, audit findings)
- Incident post-reviews (lessons learned)
- Supplier assessments
- Regulatory and threat landscape changes
- Staff-reported concerns (via GRC email or anonymised channel)

### 4.2 Risk Assessment

All identified risks are assessed using the following scoring methodology:

| Factor | Scale | Guidance |
|--------|-------|---------|
| **Likelihood (L)** | 0.1 – 1.0 | 0.1 = Rare, 0.3 = Unlikely, 0.5 = Possible, 0.7 = Likely, 1.0 = Almost certain |
| **Impact (I)** | 0.1 – 1.0 | 0.1 = Negligible, 0.3 = Minor, 0.5 = Significant, 0.7 = Major, 1.0 = Catastrophic |
| **Risk Score** | L × I | Inherent risk score before controls |

All risks are documented in the Risk Register (SN-ISMS-002).

### 4.3 Risk Treatment

| Treatment Option | When to Apply | Example |
|-----------------|---------------|---------|
| **Mitigate** | Risk score is reducible with reasonable controls | Implement MFA to reduce credential theft risk |
| **Transfer** | Risk can be shifted to a third party (insurance, contract) | Cyber insurance for breach liability |
| **Accept** | Residual risk is within appetite and treatment cost exceeds benefit | Accept low-likelihood, low-impact risks |
| **Avoid** | Risk source can be eliminated | Discontinue a service that creates unmanageable risk |

Treatment options must be approved by:
- **CISO:** Risks with residual score ≤ 0.30
- **CEO:** Risks with residual score > 0.30 or risks classified as "Unacceptable"

### 4.4 Risk Monitoring and Review

| Activity | Frequency | Responsible |
|----------|-----------|------------|
| Risk register update | Quarterly | GRC Team |
| Full risk assessment | Annually | GRC Team + CISO |
| Risk treatment progress review | Monthly | GRC Lead |
| Management risk review | Quarterly (at Management Review) | CISO → CEO |
| Post-incident risk review | Within 5 days of P1/P2 incident | GRC Lead |

---

## 5. Risk Ownership

Every risk in the Risk Register must have:
- A named **Risk Owner** (individual accountable for managing the risk)
- Defined treatment actions with owners and deadlines
- Regular status updates

Risk owners cannot delegate accountability (though they may delegate actions).

---

## 6. Risk Communication

Risk status is communicated:
- **Monthly:** GRC risk dashboard (Grafana) available to leadership
- **Quarterly:** Risk Register reviewed at Management Review
- **Ad-hoc:** CISO briefing to CEO for new high/critical risks

---

## 7. Integration with Business Processes

Risk management is embedded in:
- **Project management:** Security risk assessment at project initiation
- **Change management:** Risk assessment for significant changes via CAB
- **Supplier onboarding:** Third-party risk assessment before contracting
- **Product/service development:** Privacy and security by design

---

## 8. References

- ISO/IEC 27001:2022: Clause 6.1 (Actions to address risks), Clause 8.2 (Risk assessment), Clause 8.3 (Risk treatment)
- ISO 31000:2018 (Risk Management – Guidelines)
- NIST CSF 2.0: GV.RM (Govern: Risk Management)
- Related documents: Risk Register (SN-ISMS-002), Risk Management Procedure (SN-PROC-004)

---

*Document Owner: CISO | Approved by: CEO | Next Review: 2026-01-15*
