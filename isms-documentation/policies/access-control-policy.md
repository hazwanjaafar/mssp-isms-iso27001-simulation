# 🔐 Access Control Policy

**Document ID:** SN-POL-002  
**Version:** 1.4  
**Classification:** Internal  
**Owner:** CISO  
**Approved by:** CEO  
**Last Reviewed:** 2025-01-15  
**Next Review:** 2026-01-15  

---

## 1. Purpose

This policy establishes SecureNusantara's requirements for controlling access to
information systems, data, and physical facilities. It ensures that access is granted
on the principles of **least privilege**, **need-to-know**, and **accountability**.

---

## 2. Scope

This policy applies to:
- All SecureNusantara employees, contractors, and third parties
- All information systems within the ISMS boundary
- Physical access to SecureNusantara premises (SOC floor, server room)
- Cloud infrastructure (AWS, Azure) and SaaS applications

---

## 3. Principles

| Principle | Description |
|-----------|-------------|
| **Least Privilege** | Users are granted only the minimum access required to perform their role |
| **Need-to-Know** | Access to sensitive information requires a justified business need |
| **Segregation of Duties** | Critical functions must not be controlled by a single individual |
| **Default Deny** | Access is denied unless explicitly granted |
| **Accountability** | All access is tied to an individual identity; shared accounts are prohibited |

---

## 4. Access Control Requirements

### 4.1 User Account Management

1. All user accounts must be created via the formal onboarding process (IT Operations)
2. Shared/generic accounts are **prohibited** — each person must have a unique account
3. Service accounts must be documented with a named owner and approved by the CISO
4. Accounts must be disabled within **4 hours** of an employee's departure (same-day)
5. Dormant accounts (no login in 90 days) must be disabled and reviewed

### 4.2 Privileged Access

1. Privileged accounts (admin access to SOC platform, cloud, network devices) must be:
   - Separate from the user's standard account (e.g., `admin-username@securenusantara.com`)
   - Managed through the Privileged Access Management (PAM) solution
   - Subject to Just-In-Time (JIT) access — elevated privileges expire after the task
2. All privileged access sessions must be recorded and retained for 12 months
3. Privileged accounts must use FIDO2 hardware keys (e.g., YubiKey) as MFA

### 4.3 Multi-Factor Authentication (MFA)

| System | MFA Requirement |
|--------|----------------|
| Corporate email (Microsoft 365) | Mandatory — Authenticator app |
| VPN | Mandatory — Authenticator app |
| AWS Console | Mandatory — Virtual MFA or hardware key |
| Azure Portal | Mandatory — Authenticator app |
| Wazuh Manager | Mandatory — Authenticator app |
| TheHive | Mandatory — Authenticator app |
| PAM Solution | Mandatory — FIDO2 hardware key |

### 4.4 Remote Access

1. Remote access to SecureNusantara systems is only permitted via approved VPN
2. Split-tunnelling is disabled for VPN connections to SOC platform
3. Remote working endpoints must comply with the endpoint security baseline
4. Remote access to client environments requires client-specific VPN credentials,
   separate from SecureNusantara internal VPN

### 4.5 Client Environment Access (SOC Context)

1. SOC analyst access to client environments is governed by the client Service Agreement
2. Client-specific access credentials are stored in the PAM vault, not in personal password managers
3. Access to client environments must be logged; logs retained for 12 months
4. Analysts may only access client environments when performing authorised SOC activities

---

## 5. Access Review

| Review Type | Frequency | Responsible |
|-------------|-----------|-------------|
| Privileged access review | Quarterly | CISO + IT Operations |
| Standard user access review | Annually | Department Heads |
| Client environment access review | Semi-annually | SOC Manager |
| Service account review | Annually | IT Operations |

---

## 6. Password Requirements

| Parameter | Requirement |
|-----------|-------------|
| Minimum length | 14 characters |
| Complexity | Upper + lower + number + special character |
| History | 12 previous passwords cannot be reused |
| Maximum age | 90 days (privileged); 365 days (standard, with MFA) |
| Account lockout | 5 failed attempts → 15-minute lockout |

> **Note:** Where MFA is enforced, password complexity is the secondary control.
> The primary objective is unique, non-reused passwords — a password manager is
> strongly recommended and provided to all staff.

---

## 7. Exceptions

Exceptions to this policy must be:
1. Submitted in writing to the CISO with business justification
2. Approved by the CISO
3. Reviewed quarterly and renewed or revoked

Exceptions are tracked in the Risk Register as an accepted risk.

---

## 8. Violations

Violations of this policy are subject to the Disciplinary Policy. Intentional violations
(e.g., sharing credentials, bypassing MFA) may result in immediate suspension and
referral to HR for further action.

---

## 9. References

- ISO/IEC 27001:2022: A.5.15, A.5.16, A.5.17, A.5.18, A.8.2, A.8.3, A.8.5
- NIST CSF 2.0: PR.AA-01, PR.AA-02, PR.AA-03, PR.AA-05
- Related documents: Access Control Procedure (SN-PROC-001), Remote Working Policy

---

*Document Owner: CISO | Approved by: CEO | Next Review: 2026-01-15*
