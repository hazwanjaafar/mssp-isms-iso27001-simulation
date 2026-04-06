# 🚨 Incident Response Policy

**Document ID:** SN-POL-003  
**Version:** 1.2  
**Classification:** Internal  
**Owner:** CISO  
**Approved by:** CEO  
**Last Reviewed:** 2025-01-15  
**Next Review:** 2026-01-15  

---

## 1. Purpose

This policy establishes SecureNusantara's approach to managing information security
incidents in a consistent, timely, and effective manner — protecting client data,
maintaining service availability, meeting regulatory obligations, and enabling continuous
improvement.

---

## 2. Scope

This policy covers all security incidents affecting:
- SecureNusantara's own infrastructure and data
- Client environments monitored under SOC retainer agreements
- Information processed by SecureNusantara personnel (regardless of location)

---

## 3. Incident Classification

| Severity | Description | Response SLA | Example |
|----------|-------------|-------------|---------|
| **P1 – Critical** | Significant breach; active ransomware; data exfiltration | 15-minute acknowledgement; 4-hour containment | Active ransomware in client environment |
| **P2 – High** | Confirmed intrusion; significant service disruption | 30-minute acknowledgement; 8-hour containment | Confirmed lateral movement in client network |
| **P3 – Medium** | Suspected breach; policy violation; minor service impact | 2-hour acknowledgement; 24-hour investigation | Phishing email with credential capture |
| **P4 – Low** | Failed attack; informational; near-miss | 8-hour acknowledgement; 72-hour documentation | Port scan; failed brute force |

---

## 4. Incident Response Principles

1. **Safety first:** If an incident poses physical safety risk, contact emergency services (999) before any technical response
2. **Contain before eradicate:** Do not attempt to remove malware or threat actors before containing the spread
3. **Preserve evidence:** All forensic evidence must be preserved using documented chain-of-custody procedures
4. **Communicate clearly:** Internal and client communications must be factual and timely; avoid speculation
5. **Learn and improve:** Every P1/P2 incident must result in a Post-Incident Review within 5 working days

---

## 5. Roles and Responsibilities

| Role | Responsibility |
|------|---------------|
| **Incident Commander** | Overall incident ownership; client communication; escalation decisions |
| **Lead Analyst (T2/T3)** | Technical investigation and containment |
| **SOC Manager** | Resource allocation; escalation to CISO |
| **CISO** | Senior management escalation; regulatory notifications (NACSA, PDPD) |
| **GRC Lead (DPO)** | PDPA breach assessment; regulatory notification |
| **Communications Lead** | Client-facing and PR communications (P1/P2 only) |

For SecureNusantara-side incidents: CISO is Incident Commander.  
For client-side incidents: Senior T2/T3 analyst is Incident Commander; SOC Manager escalates as needed.

---

## 6. Notification Requirements

| Stakeholder | Trigger | Timeframe |
|-------------|---------|-----------|
| Client (SOC customer) | Any P1/P2 in their environment | Within 1 hour of incident classification |
| NACSA | Significant cybersecurity incident (as defined in Act 854) | Within 6 hours of detection |
| PDPD (Personal Data Dept.) | Personal data breach (if PDPA amendment enacted) | Within 72 hours of detection |
| SecureNusantara Board | P1 incident in SecureNusantara's own infrastructure | Within 4 hours |

> **Critical constraint:** The 6-hour NACSA notification requirement under Act 854 is
> tight for complex incidents. The IR procedure mandates a preliminary NACSA notification
> (even if incomplete) at T+4h, with a full report following within 72 hours.

---

## 7. Evidence Handling

All digital evidence must be handled in accordance with the Evidence Handling Procedure:
1. Create forensic image before any remediation
2. Document chain of custody in TheHive case record
3. Store evidence in designated secure storage (access-controlled, tamper-evident)
4. Retain evidence for a minimum of 12 months or until any legal proceedings conclude

---

## 8. External Assistance

SecureNusantara maintains relationships with the following external IR resources:
- **CyberSecurity Malaysia (CSM):** For national-level incidents
- **NACSA:** For NCII-related incidents
- **External Forensics Retainer:** [Vendor name — confidential] for cases beyond internal capability

---

## 9. Post-Incident Review (PIR)

All P1 and P2 incidents must have a PIR completed within 5 working days:
- Root cause analysis (using 5-Why or fishbone method)
- Timeline reconstruction
- Lessons learned
- Corrective actions with owners and deadlines (tracked in Jira)
- Update to IR runbooks if applicable

---

## 10. References

- ISO/IEC 27001:2022: A.5.24, A.5.25, A.5.26, A.5.27, A.5.28
- NIST CSF 2.0: RS.MA, RS.AN, RS.CO, RS.IM
- Malaysia Cybersecurity Act 2024 (Act 854): Section 29
- Related documents: Incident Response Procedure (SN-PROC-002), Evidence Handling Procedure

---

*Document Owner: CISO | Approved by: CEO | Next Review: 2026-01-15*
