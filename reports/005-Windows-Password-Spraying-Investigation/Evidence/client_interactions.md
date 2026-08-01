# Synthetic Client Interactions

> These communications are fictional and were created to simulate a realistic small-business Upwork-style engagement.

## Client — Initial request

**Client: Redgum Accounting Pty Ltd**

> Hi,
>
> We've noticed some unusual login activity on one of our Windows computers.
>
> One employee mentioned that their account was temporarily locked yesterday, and our IT guy noticed a large number of failed login attempts.
>
> We don't know whether this was just someone entering the wrong password repeatedly or something more serious.
>
> Can you analyse the supplied Windows security events and tell us what happened?
>
> We'd like a short report covering what happened, affected accounts, timing, source IP, whether the activity appears malicious, severity, and recommended actions.

## Analyst — Initial response

> I will first establish a timeline from the authentication events, correlate source IPs and accounts, and distinguish observed facts from hypotheses. I will then assess severity and recommend containment and additional evidence collection.

## Client — Additional evidence

> Thanks. We pulled some additional events from the domain controller and workstation. We also checked with John Smith.
>
> John says he was not using his account at 9:14 PM and was actually at home.
>
> The additional events show failed authentication attempts against several different accounts and a successful authentication to `r.brown` from the same internal IP.

## Analyst — Updated assessment

> The activity is more consistent with password spraying than repeated brute-force attempts against a single account. The successful `r.brown` authentication materially increases the risk of credential compromise. I recommend treating the incident as High severity pending endpoint investigation and confirming the source system.

## Client — Endpoint identification

> We identified `192.168.1.44` as `RG-LAPTOP-12`, which is assigned to John Smith. The laptop was in the office while John was at home.

## Analyst — Endpoint investigation request

> Please preserve the endpoint and provide relevant process-creation and PowerShell telemetry. In particular, I would like to determine what PowerShell actually executed rather than treating the presence of PowerShell itself as evidence of malware.

## Client — Final evidence

> We found PowerShell Script Block Logging showing the host retrieving `update.ps1` from `10.10.20.15` and passing the returned content to `IEX`. Additional commands enumerated processes, services, and the current user/security context.

## Analyst — Final assessment

> The evidence now supports treating the event as a Critical security incident. The investigation indicates password spraying followed by successful authentication and suspicious post-authentication PowerShell activity, including remote script retrieval and execution. The endpoint should be isolated immediately, affected credentials protected, evidence preserved, and `10.10.20.15` investigated as a priority.
