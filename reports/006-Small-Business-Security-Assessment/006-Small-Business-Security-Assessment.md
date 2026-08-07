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

  ---

# Finding 3 – Endpoint Detection and Centralised Security Monitoring

## Severity

**High**

## Evidence

Microsoft Defender Antivirus is enabled on company Windows 11 Pro laptops.

The organisation could not confirm whether Microsoft Defender for Endpoint is licensed or deployed.

Defender alerts are not currently forwarded to a central security platform. Users are instructed to notify the Office Manager if a Defender alert is displayed.

No dedicated Security Information and Event Management (SIEM) platform is currently deployed.

## Risk

Reliance on individual users to identify and report security alerts introduces a significant detection gap.

Security events may be missed if:

- a user does not recognise the alert;
- the device is unattended;
- the user dismisses the notification;
- an attacker disables or interferes with endpoint security controls;
- multiple alerts occur across different devices without central visibility.

The absence of confirmed EDR capability also limits the organisation's ability to perform centralised endpoint investigation, threat hunting and endpoint isolation.

## Business Impact

Delayed detection may allow malicious activity to remain active for longer, increasing the potential for credential theft, malware execution, lateral movement and data loss.

## Recommendation

### Immediate

1. Confirm the organisation's Microsoft licensing.
2. Confirm whether Microsoft Defender for Endpoint is currently deployed.
3. Review Defender configuration and endpoint coverage.
4. Establish centralised monitoring of security alerts.

### Medium Term

Evaluate whether Microsoft Defender for Endpoint and/or a SIEM solution such as Microsoft Sentinel is appropriate for the organisation's size, risk profile and budget.

Security alerts should be routed to a designated security administrator or monitored service rather than relying on end users.

## Framework Mapping

- ACSC Essential Eight – Malware Protection
- NIST CSF – Detect (DE.CM)
- CIS Control 8 – Audit Log Management
- CIS Control 13 – Network Monitoring and Defense

---

# Finding 4 – BitLocker Deployment and Recovery Key Management Cannot Be Verified

## Severity

**High**

## Evidence

The client advised that BitLocker is enabled on some company laptops but could not confirm deployment across all endpoints.

Recovery keys are stored in different locations depending on the device. Some keys may be stored in Intune while others were recorded manually by IT during device setup.

No centralised compliance report was provided to demonstrate full endpoint coverage.

## Risk

A lost or stolen laptop without verified full-disk encryption may expose locally stored business information.

Inconsistent recovery-key management may also prevent authorised administrators from recovering an encrypted device when required.

## Business Impact

The organisation handles financial and potentially sensitive client information. Loss of an unencrypted endpoint could therefore result in data exposure, operational disruption and potential notification or regulatory obligations depending on the information involved.

## Recommendation

1. Audit BitLocker status across all company endpoints.
2. Enforce BitLocker through Microsoft Intune.
3. Standardise recovery-key storage within the organisation's approved management platform.
4. Restrict access to recovery keys to authorised administrators.
5. Establish a documented recovery procedure.
6. Periodically verify encryption compliance.

## Verification Requirement

The current assessment does **not** conclude that specific endpoints are unencrypted.

The organisation should perform an endpoint-by-endpoint verification to establish the actual compliance rate.

## Framework Mapping

- ACSC Essential Eight – Restrict Administrative Privileges
- NIST CSF – Protect (PR.DS)
- CIS Control 3 – Data Protection

---

# Finding 5 – Patch Compliance Is Not Formally Monitored

## Severity

**Medium**

## Evidence

Windows Update is enabled on company laptops and updates are generally installed automatically.

However, the organisation does not have:

- a documented patching SLA;
- formal critical vulnerability remediation timeframes;
- central reporting demonstrating patch compliance;
- a documented process for handling failed or delayed updates.

Third-party applications such as Chrome and Adobe Reader are generally configured to update automatically where supported.

## Risk

Automatic updates reduce exposure but do not guarantee that all endpoints are patched within an acceptable timeframe.

Without centralised compliance monitoring, vulnerable or failed endpoints may remain unidentified.

## Business Impact

Unpatched endpoints may provide attackers with opportunities to exploit known vulnerabilities, potentially resulting in malware execution, credential theft or unauthorised access.

## Recommendation

- Define patching SLAs based on severity.
- Use Intune to monitor update compliance.
- Establish an exception process for devices that fail to patch.
- Prioritise critical security updates.
- Include commonly used third-party applications in patch monitoring.

## Suggested Target

A formal target should be established by management. As an example, critical security updates could be targeted for deployment within 14 days, subject to testing and operational requirements.

## Framework Mapping

- ACSC Essential Eight – Patch Operating Systems
- ACSC Essential Eight – Patch Applications
- NIST CSF – Protect (PR.IP)
- CIS Control 7 – Continuous Vulnerability Management

---

# Finding 6 – Unrestricted Removable Media Usage

## Severity

**Medium**

## Evidence

Employees are permitted to use USB storage devices.

The organisation does not currently have:

- a formal removable-media policy;
- technical restrictions on USB storage;
- centralised USB activity monitoring;
- documented approval requirements for removable media.

## Risk

Uncontrolled removable media can introduce malware or enable unauthorised transfer of business information.

The risk is increased where employees have not received specific guidance regarding unknown or found USB devices.

## Business Impact

A malicious or compromised USB device could introduce malware onto a corporate endpoint. Unauthorised copying of information to removable media could also create a data-loss risk.

## Recommendation

1. Develop a formal removable-media policy.
2. Explicitly instruct employees never to connect unknown or found USB devices.
3. Determine whether USB storage is required for legitimate business operations.
4. Restrict removable storage where practical.
5. Require organisation-approved encrypted devices where USB storage is necessary.
6. Investigate whether Intune/Defender policies can provide appropriate device control and monitoring.

## Framework Mapping

- ACSC Essential Eight – User Application Hardening / Malware Protection
- NIST CSF – Protect (PR.AT / PR.DS)
- CIS Control 10 – Malware Defenses

---

# Finding 7 – Backup Architecture Creates a Single Network Failure Domain

## Severity

**High**

## Evidence

The Windows file server is backed up nightly to an encrypted NAS located within the same office.

The NAS is connected to the corporate network.

The organisation does not currently maintain a documented immutable or offline backup copy.

## Risk

If an attacker compromises the corporate network and obtains sufficient privileges, the attacker may potentially access, encrypt or delete both production data and its backup destination.

Encryption of the backup data protects confidentiality but does not by itself protect the backups from deletion or ransomware.

## Business Impact

A successful ransomware attack affecting both production systems and the NAS could significantly reduce the organisation's ability to recover operations.

For an accounting firm, prolonged loss of client files and business records could result in significant operational and financial consequences.

## Recommendation

Implement a resilient backup strategy that includes:

- an isolated backup copy;
- an immutable or offline copy where appropriate;
- separate administrative credentials;
- MFA for backup administration where supported;
- restricted network access to backup infrastructure;
- monitoring of backup deletion and configuration changes.

The organisation should consider applying the **3-2-1 backup principle** as an architectural baseline.

## Framework Mapping

- NIST CSF – Protect / Recover
- CIS Control 11 – Data Recovery
- ACSC Essential Eight – Regular Backups

---

# Finding 8 – Backup Restoration Has Not Been Recently Validated

## Severity

**High**

## Evidence

The organisation performs nightly backups.

However, a full restoration test has not been performed for approximately 18 months.

No recent evidence was provided demonstrating that a complete recovery of critical business data can be achieved within a defined recovery timeframe.

## Risk

The existence of successful backup jobs does not demonstrate that the organisation can successfully restore its data following an incident.

Potential issues may remain undiscovered until recovery is urgently required.

## Business Impact

Failure of the restoration process during a ransomware, hardware failure or accidental deletion event could substantially extend business downtime.

## Recommendation

Establish a documented backup restoration testing programme.

Testing should include:

- restoration of representative files;
- restoration of critical business data;
- validation of file integrity;
- validation of permissions;
- recording restoration time;
- identification of failed backup jobs;
- documented remediation of issues.

Management should establish appropriate **Recovery Point Objectives (RPOs)** and **Recovery Time Objectives (RTOs)** for critical systems.

## Framework Mapping

- NIST CSF – Recover (RC.RP)
- CIS Control 11 – Data Recovery
- ACSC Essential Eight – Regular Backups

---

# Finding 9 – Microsoft 365 Backup and Recovery Strategy Requires Review

## Severity

**Medium**

## Evidence

The organisation does not maintain an independent backup solution for Microsoft 365 mailboxes.

Management stated that they believed Microsoft provided sufficient backup capabilities.

No documented Microsoft 365 recovery requirements, retention assessment or restoration testing evidence was provided.

## Risk

Microsoft 365 provides service resilience and native recovery capabilities, but these should not automatically be treated as equivalent to an organisation-controlled independent backup strategy.

The organisation may have insufficient recovery capability for certain deletion, corruption or account-compromise scenarios depending on its configured retention and recovery controls.

## Business Impact

Loss of important email or cloud data could affect client communications, financial records, operational continuity and the organisation's ability to meet business or regulatory requirements.

## Recommendation

Conduct a Microsoft 365 data-protection review covering:

- Exchange Online;
- SharePoint;
- OneDrive;
- Teams;
- retention policies;
- deletion and recovery scenarios;
- legal/business retention requirements.

Determine whether an independent Microsoft 365 backup service is required based on the organisation's recovery requirements.

## Important Assessment Note

This assessment does **not** conclude that Microsoft 365 data cannot currently be recovered.

The finding is that the organisation has not demonstrated that its existing Microsoft 365 recovery capabilities meet its defined business requirements.

## Framework Mapping

- NIST CSF – Protect / Recover
- CIS Control 11 – Data Recovery

---

# Finding 10 – Security Awareness Training Requires Formalisation

## Severity

**Medium**

## Evidence

New employees receive a short security briefing during onboarding.

The organisation does not currently conduct mandatory annual cybersecurity awareness training.

No phishing simulation programme has been implemented.

Training completion records were not provided.

Employees are generally instructed not to open suspicious links or attachments.

## Risk

One-time security awareness training may not provide sufficient reinforcement against evolving phishing, credential theft and social-engineering techniques.

## Business Impact

Users remain an important attack surface. Successful phishing or social engineering could result in credential compromise, malware execution or unauthorised disclosure of information.

## Recommendation

Establish a formal security awareness programme incorporating:

- mandatory onboarding training;
- annual refresher training;
- periodic phishing awareness exercises;
- reporting procedures for suspected phishing;
- training completion tracking;
- targeted education following security incidents.

Training should specifically address the risks associated with suspicious attachments, credential requests, MFA prompts and unknown removable media.

## Framework Mapping

- NIST CSF – Protect (PR.AT)
- CIS Control 14 – Security Awareness and Skills Training
- ACSC Essential Eight – User Application Hardening

---

# Finding 11 – Firewall Administration and Monitoring Requires Improvement

## Severity

**Medium**

## Evidence

The organisation uses a business-grade firewall supplied by its Internet Service Provider.

Remote administration is enabled for the external IT contractor.

Firewall logs are not routinely reviewed and there is no documented firewall rule review schedule.

The exact firewall model and current rule configuration were not independently verified during this assessment.

## Risk

Unreviewed firewall configurations may contain unnecessary access rules or outdated administrative access.

Remote administration also represents an additional management interface that should be appropriately secured and monitored.

## Business Impact

Weak firewall administration could increase the likelihood of unauthorised network access or make malicious activity more difficult to detect.

## Recommendation

- Identify and document the firewall model and firmware version.
- Review all firewall rules.
- Remove unnecessary rules.
- Restrict administrative access to authorised personnel.
- Enforce MFA where supported.
- Restrict remote administration to trusted sources or VPN access where practical.
- Enable appropriate logging.
- Establish periodic firewall rule reviews.

## Framework Mapping

- NIST CSF – Protect (PR.AC)
- CIS Control 4 – Secure Configuration
- CIS Control 12 – Network Infrastructure Management
