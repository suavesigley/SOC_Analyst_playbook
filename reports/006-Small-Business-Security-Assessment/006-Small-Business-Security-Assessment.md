# 006 – Small Business Security Assessment

**Prepared by:** Joshi Sigley  
**Role:** Junior SOC Analyst (Portfolio Simulation)  
**Assessment Type:** Security Posture Assessment  
**Assessment Date:** August 2026  
**Classification:** Portfolio Project (Simulated Client Engagement)

---

# Executive Summary

## Overview

A fictional Australian accounting firm engaged a Junior SOC Analyst to perform a high-level security posture assessment of its Microsoft 365 environment, Windows endpoints, network infrastructure and operational security controls.

The objective of this assessment was to identify weaknesses that could increase the organisation's exposure to cyber threats and provide practical recommendations to improve its overall security posture.

The assessment focused on reviewing identity and access management, endpoint security, network security, backup and recovery, user awareness and security monitoring. No penetration testing or exploitation activities were performed.

---

## Overall Assessment

The organisation has implemented several positive foundational security controls, including:

- Microsoft Intune device management
- Microsoft Defender Antivirus
- Individual Microsoft 365 user accounts
- Guest Wi-Fi separation
- Encrypted file server backups
- Windows 11 Pro endpoints

However, the assessment identified several areas where inconsistent implementation or lack of governance significantly increases organisational risk.

The most significant findings include:

- Multi-Factor Authentication (MFA) is not enforced for all users.
- Privileged administrative accounts are used for day-to-day activities.
- Backup resilience has not been validated through recent restoration testing.
- Microsoft 365 data is not independently backed up.
- Endpoint monitoring relies primarily on end-user reporting.
- Security awareness training is limited and not regularly reinforced.
- Removable media usage is unrestricted and unsupported by formal policy.
- BitLocker deployment cannot be consistently verified across all endpoints.

---

## Overall Risk Rating

**Overall Risk: HIGH**

Although several foundational security controls are present, inconsistent implementation of identity, monitoring and recovery controls creates an elevated likelihood of successful compromise and limits the organisation's ability to rapidly detect and recover from security incidents.

---

# Assessment Objectives

The objectives of this engagement were to:

- Assess the organisation's current cybersecurity posture.
- Identify security control weaknesses.
- Evaluate identity and access management practices.
- Review endpoint security controls.
- Assess backup and recovery capabilities.
- Review network security controls.
- Assess security monitoring capabilities.
- Evaluate user security awareness.
- Provide prioritised recommendations for remediation.

---

# Scope

## In Scope

- Microsoft 365 tenant
- Windows 11 Pro endpoints
- Windows Server 2022 file server
- Microsoft Intune
- Microsoft Defender Antivirus
- Identity and Access Management
- Backup and Recovery
- Corporate Network
- Wireless Networks
- Endpoint Security
- Security Awareness
- Security Monitoring

## Out of Scope

- Penetration Testing
- Social Engineering
- Physical Security Testing
- Vulnerability Exploitation
- Production System Attacks

---

# Assessment Methodology

The assessment was conducted using a documentation review and structured client interview.

Evidence was collected through:

- Client interviews
- Configuration summaries
- Asset information
- Identity configuration
- Backup configuration
- Endpoint security configuration
- Network architecture review

Findings were evaluated against recognised cybersecurity guidance including:

- Australian Cyber Security Centre (ACSC) Essential Eight
- NIST Cybersecurity Framework (CSF)
- CIS Critical Security Controls
- Microsoft Security Best Practices

This assessment was conducted as a portfolio simulation designed to reflect a realistic junior cybersecurity consultant engagement.

---

# Risk Rating Methodology

Findings identified during this assessment were assigned a qualitative risk rating based on the likelihood of exploitation and the potential business impact should the identified weakness be successfully exploited.

| Likelihood | Description |
|------------|-------------|
| Low | Unlikely under normal operating conditions. |
| Medium | Reasonably possible if exploited by a capable attacker. |
| High | Likely to be exploited or already presents significant exposure. |

| Impact | Description |
|---------|-------------|
| Low | Minimal operational impact. |
| Medium | Noticeable disruption or limited data exposure. |
| High | Significant operational disruption, financial loss or compromise of sensitive information. |

Overall Severity was determined by considering both likelihood and impact together, while taking into account the organisation's current security posture.

---

# Finding 1 – Multi-Factor Authentication Not Fully Enforced

## Severity

**High**

## Evidence

The client confirmed that only 9 of 15 Microsoft 365 user accounts are currently enrolled in Multi-Factor Authentication (MFA). Six user accounts continue to authenticate using passwords alone.

## Risk

Accounts protected only by passwords are more susceptible to credential theft, password spraying and phishing attacks.

## Business Impact

Successful compromise of a Microsoft 365 account may provide an attacker with access to email, SharePoint, OneDrive and other cloud resources, increasing the likelihood of business disruption and unauthorised disclosure of sensitive information.

## Recommendation

- Enforce MFA for all users.
- Implement Conditional Access policies where appropriate.
- Remove legacy authentication methods if present.
- Monitor MFA registration compliance.

## Framework Mapping

- ACSC Essential Eight
- NIST CSF – Protect (PR.AA)
- CIS Control 6

---

# Finding 2 – Privileged Access Management

## Severity

**High**

## Evidence

Three Global Administrator accounts exist.

The Managing Director and Office Manager perform privileged administrative tasks using their standard user accounts rather than dedicated administrative identities.

Quarterly access reviews are not currently performed.

## Risk

Excessive privileged access increases the potential impact of credential compromise and administrative misuse.

## Business Impact

Compromise of a privileged account may allow attackers to modify Microsoft 365 security settings, create new accounts or disable security controls.

## Recommendation

- Reduce the number of Global Administrators.
- Use dedicated administrative accounts.
- Introduce quarterly access reviews.
- Review privileged group membership regularly.

## Framework Mapping

- ACSC Essential Eight
- CIS Control 5
- NIST CSF – Protect (PR.AA)
