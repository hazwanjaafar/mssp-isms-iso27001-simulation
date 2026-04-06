# 🗄️ Asset Management Procedure

**Document ID:** SN-PROC-003  
**Version:** 1.1  
**Classification:** Internal  
**Owner:** Platform Engineering Lead  
**Approved by:** CISO  
**Last Reviewed:** 2025-01-15  
**Next Review:** 2026-01-15  

---

## 1. Purpose & Scope

This procedure provides step-by-step guidance for managing the lifecycle of SecureNusantara's
information assets from procurement through secure disposal. It implements the Asset
Management Policy (SN-POL-004).

---

## 2. Asset Register Maintenance

The CMDB is maintained in Confluence (Space: `IT Operations > Asset Register`).

### 2.1 Asset Registration (New Asset)

**Trigger:** New asset procured or new cloud service provisioned.

| Step | Action | Responsible |
|------|--------|------------|
| 1 | Complete the Asset Registration Form in Confluence | Requesting team |
| 2 | Assign unique Asset ID (format: `SN-[TYPE]-[YYYY]-[SEQ]`, e.g., `SN-HW-2025-042`) | IT Operations |
| 3 | Classify asset (Public / Internal / Confidential / Restricted) | Asset Owner |
| 4 | Assign criticality tier (1 / 2 / 3) | Asset Owner |
| 5 | Record in CMDB | IT Operations |
| 6 | Apply configuration baseline (see Section 4) | Platform Eng |
| 7 | Confirm CMDB entry with Asset Owner | IT Operations |

### 2.2 Quarterly CMDB Reconciliation

1. Export current CMDB from Confluence
2. Compare against:
   - AWS/Azure resource inventory (from Security Hub / Defender)
   - Nessus discovered assets
   - MDM enrolled devices (Intune)
3. Identify: new assets (add), decommissioned assets (mark retired), discrepancies (investigate)
4. CMDB discrepancy report submitted to CISO
5. Cloud shadow IT flagged to asset owner's manager

---

## 3. Asset Lifecycle Stages

### 3.1 Hardware Assets

```
PROCUREMENT → DEPLOYMENT → OPERATION → CHANGE → DECOMMISSION → DISPOSAL
```

| Stage | Key Actions |
|-------|------------|
| **Procurement** | Security requirements included in purchase spec; vendor reputation checked |
| **Deployment** | Asset registered; CIS benchmark hardening applied; MDM enrolled (endpoints) |
| **Operation** | Vulnerability scanning; patch management; access control maintained |
| **Change** | CAB approval; configuration baseline updated post-change |
| **Decommission** | Access revoked; asset marked retired in CMDB; data sanitisation initiated |
| **Disposal** | NIST SP 800-88 wipe; disposal certificate obtained; CMDB closed |

### 3.2 Software/SaaS Assets

| Stage | Key Actions |
|-------|------------|
| **Approval** | GRC + Platform Eng review before procurement (security questionnaire for SaaS) |
| **Provisioning** | SSO integration where possible; MFA enforced; data classification reviewed |
| **Operation** | Annual review of necessity and security controls |
| **Termination** | Data export/deletion verified; account terminated; CMDB updated |

### 3.3 Cloud Resources

| Stage | Key Actions |
|-------|------------|
| **Provisioning** | Terraform or approved console; mandatory tagging applied |
| **Operation** | CSPM scanning (Security Hub / Defender) continuous; monthly review |
| **Decommission** | Data deletion verified; S3/blob storage emptied; resource terminated |

---

## 4. Configuration Baseline

### 4.1 Windows Endpoints (Laptops)

Baseline applied via Microsoft Intune configuration profiles:
- [ ] BitLocker full-disk encryption enabled
- [ ] Windows Defender enabled and policies applied
- [ ] Wazuh agent deployed and reporting
- [ ] Microsoft 365 apps only; no local admin rights (standard users)
- [ ] Screen lock after 5 minutes
- [ ] CIS Level 1 benchmark applied via Intune

### 4.2 Linux Servers (On-Prem and Cloud)

Baseline applied via Ansible playbook `sn-server-baseline.yml`:
- [ ] Wazuh agent installed and reporting
- [ ] Auditd enabled with SecureNusantara audit rules
- [ ] SSH: key-based authentication only; root login disabled; allowed users restricted
- [ ] Firewall (ufw/nftables): default deny; only required ports open
- [ ] Automatic security updates enabled (unattended-upgrades)
- [ ] Fail2ban enabled
- [ ] CIS Level 1 benchmark applied

### 4.3 Cloud Resources (AWS)

- [ ] All S3 buckets: Block Public Access enabled; server-side encryption (SSE-S3 or SSE-KMS)
- [ ] IAM: no long-lived access keys for users; use roles; MFA enabled on all IAM users
- [ ] CloudTrail: enabled in all regions; logs sent to Wazuh
- [ ] Security Hub: enabled; CIS AWS Foundations Benchmark active
- [ ] VPC: no resources in default VPC; security groups follow least-privilege

---

## 5. Vulnerability Management Integration

Asset management feeds directly into vulnerability management:

1. **Wazuh agent inventory** — all registered assets with Wazuh agents appear in the Wazuh dashboard
2. **Nessus scans** — asset list seeded from CMDB; discovered assets reconciled monthly
3. **Critical patch SLA:**
   - Critical/High CVEs (CVSS 9.0+): patch within **30 days**
   - Medium CVEs: patch within **90 days**
   - Low CVEs: patch within **180 days** or at next maintenance window
4. Unpatched assets beyond SLA flagged as Risk Register items

---

## 6. Physical Media Handling

| Action | Procedure |
|--------|-----------|
| Storing removable media | Encrypted USB only; labelled with classification level |
| Transferring media | Encrypted; chain of custody documented |
| Sanitising media | NIST 800-88 Guidelines for Media Sanitisation (Clear/Purge/Destroy) |
| Destroying media | Cross-cut shred (paper); physical destruction certificate for HDDs/SSDs |
| Disposal record | Maintained in CMDB for 3 years |

---

## 7. Asset Disposal Procedure

### 7.1 Hardware Disposal

| Step | Action | Responsible |
|------|--------|------------|
| 1 | Submit disposal request in Jira (IT-DISPOSE template) | Asset Owner |
| 2 | Confirm all data backed up (if required) | Asset Owner |
| 3 | Apply NIST 800-88 data sanitisation (Purge for HDDs; Destroy for SSDs containing Confidential/Restricted) | IT Operations |
| 4 | Generate sanitisation certificate (Eraser/DBAN report) | IT Operations |
| 5 | Remove from CMDB (mark as Disposed with date) | IT Operations |
| 6 | Hand over to certified e-waste disposal vendor | IT Operations |
| 7 | Obtain disposal certificate from vendor | IT Operations |
| 8 | Store disposal certificate in Confluence | IT Operations |

---

## 8. Evidence & Records

| Record | Storage | Retention |
|--------|---------|-----------|
| Asset register (CMDB) | Confluence | Ongoing (3 years post-disposal) |
| Quarterly reconciliation report | Confluence | 3 years |
| Disposal certificate | Confluence | 5 years |
| Configuration baseline evidence | Ansible/Intune reports | 3 years |
| Vulnerability scan reports | Elasticsearch (Nessus logs) | 12 months |

---

*Document Owner: Platform Engineering Lead | Approved by: CISO | Next Review: 2026-01-15*
