# 🗄️ Asset Management Policy

**Document ID:** SN-POL-004  
**Version:** 1.1  
**Classification:** Internal  
**Owner:** Platform Engineering Lead  
**Approved by:** CISO  
**Last Reviewed:** 2025-01-15  
**Next Review:** 2026-01-15  

---

## 1. Purpose

This policy establishes requirements for the identification, classification, ownership,
and lifecycle management of all information assets within SecureNusantara's ISMS boundary.
Accurate asset management is the foundation of effective risk assessment and security control.

---

## 2. Scope

This policy covers all information assets including:
- Hardware (servers, laptops, network equipment, physical media)
- Software (applications, SaaS, open-source tools)
- Data (client logs, internal records, configuration data)
- Services (cloud services, third-party managed services)
- People (as assets in terms of knowledge and skills)

---

## 3. Asset Classification

### 3.1 Information Classification Levels

| Level | Label | Description | Examples |
|-------|-------|-------------|---------|
| **Level 1** | Public | Approved for public release | Website content, published reports |
| **Level 2** | Internal | For internal use only | Policies, procedures, staff guides |
| **Level 3** | Confidential | Sensitive business or client information | Client incident reports, contracts, IR plans |
| **Level 4** | Restricted | Highest sensitivity; strictly need-to-know | Client credentials in PAM, key management material, board reports |

### 3.2 Asset Criticality Tiers

| Tier | Description | Recovery Priority |
|------|-------------|-----------------|
| **Tier 1 – Critical** | Service delivery depends on this asset; failure impacts client SLAs | Immediate (RTO < 4h) |
| **Tier 2 – Important** | Significant impact if unavailable; workarounds exist | Priority (RTO < 24h) |
| **Tier 3 – Standard** | Normal operations; manageable impact | Standard (RTO < 72h) |

---

## 4. Asset Register Requirements

All assets must be recorded in the CMDB (maintained in Confluence) with:
- Unique asset ID
- Asset name and description
- Asset type (hardware/software/data/service)
- Classification level
- Criticality tier
- Asset owner (named individual)
- Location (physical or cloud region)
- Date acquired/deployed
- Warranty/licence expiry
- Date last reviewed

---

## 5. Asset Ownership

| Asset Type | Default Owner |
|-----------|--------------|
| IT infrastructure (servers, network) | Platform Engineering Lead |
| Laptops and endpoint devices | IT Operations |
| Cloud services (AWS/Azure) | Cloud Security Lead |
| SOC platform tools | Platform Engineering Lead |
| Client data | CISO (as Data Controller/Processor) |
| ISMS documents | GRC Lead |
| Intellectual property | CEO |

Asset owners are accountable for:
- Ensuring the asset is accurately registered
- Applying the appropriate security controls
- Reviewing asset classification annually
- Approving access to assets under their ownership

---

## 6. Acceptable Use

All assets must be used in accordance with:
- The Acceptable Use Policy (AUP) signed by all employees
- The Access Control Policy
- The applicable classification handling requirements

Personal use of company assets is permitted in moderation but must not:
- Compromise the security of the asset
- Involve storing personal data on company systems
- Circumvent security controls

---

## 7. Asset Lifecycle

| Phase | Requirements |
|-------|-------------|
| **Procurement** | Security review before acquisition; licence/open-source compliance check |
| **Deployment** | Configuration baseline applied; asset registered in CMDB; owner assigned |
| **Operation** | Vulnerability scanning; patch management; access reviews |
| **Change** | Change Advisory Board (CAB) approval for significant changes |
| **Disposal** | NIST SP 800-88 data sanitisation; removal from CMDB; disposal record |

---

## 8. Physical Media

1. All removable media (USB drives, external HDD) must be encrypted before use
2. Only company-approved USB devices (encrypted) may be used
3. Media containing Confidential or Restricted data must be physically destroyed
   (cross-cut shredding for paper; degaussing/destruction for digital media)
4. A media disposal record must be maintained for all Confidential and Restricted media

---

## 9. Cloud Assets

1. All cloud assets must be tagged with: Owner, Environment (prod/dev/test), Classification, CostCentre
2. Shadow IT (unsanctioned cloud services) is prohibited
3. Cloud assets must be discovered via CSPM and reconciled with the CMDB quarterly

---

## 10. References

- ISO/IEC 27001:2022: A.5.9, A.5.10, A.5.11, A.5.12, A.5.13, A.7.10, A.7.14, A.8.1
- NIST CSF 2.0: ID.AM-01, ID.AM-02, ID.AM-07
- Related documents: Asset Management Procedure (SN-PROC-003)

---

*Document Owner: Platform Engineering Lead | Approved by: CISO | Next Review: 2026-01-15*
