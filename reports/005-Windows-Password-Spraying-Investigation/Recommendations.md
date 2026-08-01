# Recommendations

## Immediate containment

### 1. Isolate `RG-LAPTOP-12`

Remove the endpoint from normal network access while preserving forensic evidence.

### 2. Protect affected credentials

Immediately disable or reset credentials where compromise is suspected, prioritising:

- `j.smith`
- `r.brown`

Review the other targeted accounts before determining whether broader credential resets are required.

### 3. Investigate `10.10.20.15`

Identify the system, owner, role, and reason it served `update.ps1`.

Search network and endpoint telemetry for other systems communicating with it.

### 4. Preserve evidence

Preserve:

- Windows Security logs
- PowerShell Operational logs
- 4103/4104 events where available
- 4688 process-creation events
- process trees
- command lines
- `update.ps1`
- file hashes
- network telemetry
- DNS records
- endpoint/EDR alerts
- relevant scheduled tasks/services and persistence artefacts

Avoid unnecessarily wiping or reimaging the endpoint before evidence collection.

## Eradication

After evidence preservation and investigation:

- remove confirmed malicious tooling;
- eliminate persistence;
- reset compromised credentials;
- review and remediate affected endpoints;
- validate endpoint security controls;
- patch identified vulnerabilities;
- rotate secrets/tokens if exposure is suspected.

## Recovery

- Rebuild/reimage the endpoint if integrity cannot be trusted.
- Restore it to a known-good state.
- Reconnect only after validation.
- Monitor affected accounts and hosts closely.
- Confirm MFA is enforced for relevant remote and privileged access.

## Detection improvements

Create detections for:

- rapid failed authentications across multiple accounts from one source;
- successful authentication following a password-spraying pattern;
- PowerShell spawning `cmd.exe` in unusual user contexts;
- PowerShell downloading remote content;
- suspicious `IEX` / `Invoke-Expression` usage;
- unusual PowerShell activity originating from Office applications;
- `whoami /all`, process discovery, and service discovery following suspicious authentication.

## What not to recommend without evidence

Avoid recommending:

- company-wide password resets solely because several accounts were targeted;
- restricting all accounts to business hours as the primary control;
- assuming an internal IP is geographically trusted;
- declaring a file malware before analysing it;
- deleting or reimaging the endpoint before preserving evidence.
