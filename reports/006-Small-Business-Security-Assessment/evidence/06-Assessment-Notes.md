# Assessment Notes

**Assessment:** 006 – Small Business Security Assessment  
**Analyst:** Joshi Sigley  
**Date:** August 2026

> Portfolio simulation. All client, system and configuration information is fictional.

---

## Initial Assessment

The organisation has several security technologies already deployed, particularly Microsoft 365, Intune and Microsoft Defender Antivirus.

The main concern is not the complete absence of security controls. The greater concern is inconsistent implementation, lack of verification and limited monitoring.

---

## Identity

### Observation

MFA is enabled for 9/15 users.

### Analyst Reasoning

Six accounts remain dependent on passwords.

Need to determine whether Conditional Access can be used to enforce MFA.

### Risk

Credential compromise.

### Action

Recommend organisation-wide MFA enforcement.

---

## Privileged Access

### Observation

Three Global Administrators.

Managing Director and Office Manager use normal accounts for administrative tasks.

### Analyst Reasoning

Need separation between normal user activity and privileged administration.

### Risk

Compromise of a normal account could have greater consequences if the account has administrative privileges.

### Action

Dedicated administrative accounts and reduction of Global Administrator membership.

---

## Endpoint Monitoring

### Observation

Defender Antivirus is enabled.

Defender for Endpoint status is unknown.

### Analyst Reasoning

Do not assume EDR is absent.

Need licensing and deployment verification.

### Action

Confirm Microsoft licensing and Defender for Endpoint deployment.

---

## BitLocker

### Observation

Client says BitLocker is enabled on some laptops.

### Analyst Reasoning

Cannot conclude that specific machines are unencrypted.

Need endpoint-level compliance evidence.

### Action

Audit all endpoints through Intune.

---

## USB

### Observation

USB storage is unrestricted.

### Analyst Reasoning

Potential malware and data-loss vector.

Need to determine whether business operations actually require USB storage.

### Action

Develop policy and evaluate technical restrictions.

---

## Backups

### Observation

Nightly backups to an encrypted NAS.

NAS is located on the same network.

### Analyst Reasoning

Encryption protects confidentiality but does not prevent an attacker with sufficient access from deleting or encrypting the backup.

### Action

Recommend isolated/immutable/offline backup copy.

---

## Backup Testing

### Observation

Last full restore approximately 18 months ago.

### Analyst Reasoning

Backup existence does not equal recoverability.

### Action

Schedule restoration testing and document results.

---

## Microsoft 365

### Observation

No independent Microsoft 365 backup.

### Analyst Reasoning

Need to assess actual retention and recovery requirements before recommending a product.

### Action

Perform Microsoft 365 recovery assessment.

---

## Security Awareness

### Observation

Onboarding briefing only.

No annual training or phishing simulation.

### Analyst Reasoning

Users remain a significant attack surface.

### Action

Formalise awareness programme.

---

## Firewall

### Observation

ISP-supplied firewall.

Remote administration enabled.

No routine log or rule review.

### Analyst Reasoning

Need to verify model, firmware, administrative controls and actual rules before making a stronger technical conclusion.

### Action

Perform firewall configuration review.

---

# Analyst Quality-Control Notes

Before finalising the assessment:

- Do not state unknown controls as absent.
- Do not assign Critical severity without evidence supporting immediate catastrophic impact.
- Separate confirmed weaknesses from verification requirements.
- Recommendations should be proportional to a 15-person organisation.
- Avoid recommending expensive technologies without first determining whether existing Microsoft licensing can satisfy the requirement.
- Ensure each finding has evidence, risk, impact and remediation.
