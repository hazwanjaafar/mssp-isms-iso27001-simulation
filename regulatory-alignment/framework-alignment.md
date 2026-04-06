# 📐 Regulatory & Framework Alignment Strategy

**Document ID:** SN-REG-001  
**Version:** 1.2  
**Classification:** Internal  
**Owner:** CISO  
**Last Reviewed:** 2025-01-15  

---

## 1. Why Each Framework Applies

### 1.1 ISO/IEC 27001:2022

**Why it applies:**  
SecureNusantara is pursuing ISO 27001 certification for two reasons:
1. **Commercial:** Government and financial sector clients increasingly mandate ISO 27001
   as a supply chain security prerequisite in tender evaluations.
2. **Operational:** The structured ISMS provides a systematic approach to managing the
   inherent risks of an MSSP — handling sensitive client data, operating critical security
   infrastructure, and maintaining service continuity.

**Scope applicability:** The standard applies to all aspects of SecureNusantara's ISMS,
covering its SOC, threat intelligence, vulnerability management, and cloud security
services within the defined ISMS boundary.

### 1.2 NIST Cybersecurity Framework (CSF) 2.0

**Why it applies:**  
Many of SecureNusantara's clients (particularly CII operators and government-linked
companies) reference NIST CSF in their security programmes. Aligning SecureNusantara's
controls and service delivery to NIST CSF functions allows:
- A common language with clients for security posture assessment
- Easier mapping when providing vCISO services
- Strengthened SOC service design (Identify → Protect → Detect → Respond → Recover → Govern)

**Note:** NIST CSF 2.0 is not a regulatory requirement for Malaysian companies — it is
adopted by SecureNusantara voluntarily as an operational best practice and service
differentiator.

### 1.3 Malaysia Personal Data Protection Act 2010 (PDPA)

**Why it applies:**  
SecureNusantara processes personal data in two capacities:
- **Data Processor:** Handling client employee/customer personal data as part of SOC
  monitoring (logs may contain personal data such as usernames, IP addresses, email content)
- **Data Controller:** Managing personal data of its own staff, prospects, and clients

PDPA obligations include: lawful processing, purpose limitation, consent management,
data subject rights, cross-border transfer restrictions, and breach notification.

> **Critical gap:** SecureNusantara's current log handling procedures do not consistently
> distinguish between security telemetry (not personal data) and logs containing personal
> data (e.g., email subject lines in mail gateway logs). This is flagged as a corrective
> action in the internal audit.

### 1.4 Malaysia Cybersecurity Act 2024 (Act 854)

**Why it applies:**  
Act 854 imposes obligations on:
- **National Critical Information Infrastructure (NCII) entities** (SecureNusantara's
  government/CII clients fall under this)
- **Cybersecurity service providers** — MSSPs providing services to NCII entities must
  be licensed under the Act

SecureNusantara is in the process of obtaining its NACSA Cybersecurity Service Provider
(CSSP) licence, which requires demonstrating adequate security practices — overlapping
substantially with ISO 27001 controls.

---

## 2. Control Alignment Strategy Overview

### 2.1 ISO 27001:2022 ↔ NIST CSF 2.0

| ISO 27001 Clause / Control Domain | NIST CSF 2.0 Function |
|-----------------------------------|-----------------------|
| Clause 6.1 – Risk assessment and treatment | GV.RM (Govern: Risk Management) |
| Clause 9.1 – Monitoring, measurement | ID.AM (Identify: Asset Management) |
| A.5 – Organisational controls | GV (Govern) |
| A.6 – People controls | PR.AT (Protect: Awareness Training) |
| A.7 – Physical controls | PR.IR (Protect: Infrastructure Resilience) |
| A.8.1–8.9 – Asset management, encryption | PR (Protect broadly) |
| A.8.15–8.16 – Logging, monitoring | DE.AE (Detect: Adverse Event Analysis) |
| A.8.22–8.26 – Network security, app security | PR.IR, PR.PS |
| A.5.24–5.28 – Incident management | RS (Respond), RC (Recover) |
| A.5.29–5.30 – BCP/DR | RC.RP (Recover: Recovery Planning) |
| A.5.35–5.36 – IS review, compliance | GV.PO (Govern: Policy) |
| A.5.19–5.22 – Supplier relations | GV.SC (Govern: Supply Chain) |

### 2.2 ISO 27001:2022 ↔ Malaysia PDPA

| ISO 27001 Control Area | PDPA Principle / Section |
|------------------------|--------------------------|
| A.5.33 – Protection of records | Section 10 – Retention principle |
| A.5.34 – Privacy / PII protection | Section 6 – General principle; Section 7 – Notice & Choice |
| A.5.14 – Information transfer | Section 129 – Restriction on transfer outside Malaysia |
| A.8.10 – Information deletion | Section 10 – Retention / right to erasure (implied) |
| A.5.9 – Information assets inventory | Section 7 – Data subjects must be informed of data categories |
| A.6.1 – Screening | Section 6 – Security principle (data processor obligations) |
| A.5.24–5.28 – Incident response | Section 12 – Breach notification (pending amendment) |
| A.5.31 – Legal requirements | Section 4 – Lawful basis for processing |

### 2.3 ISO 27001:2022 ↔ Act 854 (Cybersecurity Act 2024)

| ISO 27001 Control Area | Act 854 Obligation |
|------------------------|-------------------|
| Clause 6.1 – Risk assessment | Section 28 – NCII risk assessment obligations |
| A.5.24–5.28 – Incident management | Section 29 – Cyber incident reporting to NACSA (within 6 hours of detection) |
| A.5.35 – Information security review | Section 26 – NCII audit requirements |
| A.8.15 – Logging | Section 30 – Audit trail preservation |
| A.5.19–5.22 – Supplier management | Section 31 – Supply chain cybersecurity |
| Clause 9.3 – Management review | Section 27 – Annual compliance reporting |

---

## 3. Overlaps, Conflicts, and Gaps

### 3.1 Overlaps (Positive — Reduce Duplication)

| Area | ISO 27001 | NIST CSF | PDPA | Act 854 |
|------|-----------|----------|------|---------|
| Incident response | ✅ A.5.24–5.28 | ✅ RS.MA | ✅ Implied | ✅ S.29 |
| Risk management | ✅ Clause 6 | ✅ GV.RM | ✅ Implied | ✅ S.28 |
| Logging & monitoring | ✅ A.8.15 | ✅ DE.AE | ✅ Implied | ✅ S.30 |
| Supplier management | ✅ A.5.19 | ✅ GV.SC | ✅ S.129 | ✅ S.31 |
| Awareness & training | ✅ A.6.3 | ✅ PR.AT | ✅ Implied | ✅ S.26 |

These overlaps are efficiency wins — a single control satisfies multiple requirements.

### 3.2 Conflicts (Require Careful Navigation)

| Conflict | Description | Resolution |
|----------|-------------|------------|
| **Data retention** | ISO 27001 requires keeping records (e.g., audit logs) for sufficient periods. PDPA requires personal data not be retained beyond purpose. | Define clear data classification: security telemetry (not PD) vs. logs containing PD. Apply PDPA retention limits only to PD-containing logs; retain pure security logs per ISO requirements. |
| **Incident disclosure** | Act 854 requires reporting to NACSA within 6 hours of a significant cyber incident. ISO 27001 incident procedure may have longer internal review cycles. | Update incident response procedure to include an immediate NACSA notification step at T+4h, before full IR review is complete. |
| **Cross-border data** | PDPA restricts transfer of personal data outside Malaysia. Wazuh indexer is on AWS Singapore. | Contractual safeguard with AWS (Standard Contractual Clauses); explicit client consent in service agreement; explore Azure Malaysia as primary for PD-heavy clients. |

### 3.3 Gaps (Require Remediation)

| Gap | Framework | Description | Risk Level |
|----|-----------|-------------|-----------|
| **PDPA Breach Notification procedure** | PDPA | No formal breach notification procedure exists. The PDPA amendment (pending) will require notification within 72 hours. | High |
| **Act 854 CSSP Licence** | Act 854 | Licence application submitted but not yet approved. Operating without licence creates regulatory risk. | High |
| **Formal Privacy Impact Assessment (PIA)** | PDPA / ISO A.5.34 | No PIA conducted for new SOC monitoring services. | Medium |
| **NIST CSF GV (Govern) function** | NIST CSF 2.0 | CSF 2.0 added Govern as a new function. SecureNusantara's current service offering does not explicitly reference GV controls in client reports. | Medium |
| **Supply chain security assessments** | ISO A.5.19 / Act 854 S.31 | Only 3 of 12 critical suppliers have been formally assessed. | High |

---

## 4. Multi-Framework Compliance Strategy

Rather than treating each framework independently, SecureNusantara adopts a
**"Comply Once, Report Many"** approach:

1. **ISO 27001 as the foundation:** All controls are implemented to ISO 27001 standards
2. **NIST CSF as the operational lens:** SOC workflows and client reporting use CSF language
3. **PDPA as a data handling overlay:** Data classification and consent mechanisms layered on top
4. **Act 854 as the regulatory gatekeeper:** Incident reporting and licensing obligations enforced

This approach avoids duplicated effort but requires the GRC team to maintain a living
cross-reference matrix (see `control-mapping-matrix.md`).

> **Critical thinking:** Is ISO 27001 certification sufficient to establish MSSP trust?
> No. Certification demonstrates a baseline of security process maturity, but does not
> guarantee security outcomes. Clients should also consider: SOC 2 Type II (process and
> operational effectiveness), penetration test results, incident history, and reference
> checks. SecureNusantara should be transparent about this distinction with all clients.

---

*Document Owner: CISO | Approved by: CEO | Next Review: 2026-01-15*
