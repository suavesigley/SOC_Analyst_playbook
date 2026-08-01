# Lessons Learned

## Analyst development

This investigation highlighted several important SOC analysis principles.

### 1. Start with the timeline

The investigation became meaningful when authentication events were ordered chronologically.

### 2. Look for patterns, not isolated events

Seven failures against one account could have several explanations. Failures across multiple accounts from the same source provide much stronger evidence of password spraying.

### 3. Correlate authentication with endpoint activity

The investigation escalated when the source IP was linked to `RG-LAPTOP-12`, and then to PowerShell process creation.

### 4. Do not overstate evidence

An analyst should distinguish between:

- observed behaviour;
- supported hypothesis;
- confirmed finding;
- unknowns requiring further investigation.

For example, suspicious PowerShell execution is not automatically proof of malware.

### 5. Successful authentication changes the investigation

A successful login following credential-targeting activity should trigger investigation into what happened after authentication.

### 6. PowerShell command content matters

Knowing that `powershell.exe` ran is less useful than knowing what it executed. Script Block Logging and command-line telemetry can provide much stronger investigative evidence.

## Personal reflection

This simulated engagement was designed to practise the transition from technical learning to client-ready analysis.

The investigation required progressively updating the hypothesis as new evidence became available rather than committing prematurely to an explanation.

## Portfolio limitations

This is a simulated case study. It demonstrates investigative methodology but does not constitute professional incident-response experience or a real client engagement.
