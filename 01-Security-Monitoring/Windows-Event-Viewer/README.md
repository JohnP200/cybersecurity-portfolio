# Windows Event Viewer — Authentication Log Investigation

**Focus:** Security monitoring / introductory SOC analysis  
**Environment:** Windows 11 virtual machine in VirtualBox  
**Tools:** Windows Event Viewer  
**Scope:** Authorized local lab; no external systems tested

## Objective

Use Windows Security auditing events to identify successful and failed logons, filter relevant event IDs, and inspect the account, failure code, and recorded source of failed authentication attempts.

## What I did

1. Opened **Event Viewer → Windows Logs → Security**.
2. Located **4624** (successful logon) records, including **logon types 2 and 5**.
3. Examined **4625** (failed logon) details from intentional incorrect-password tests.
4. Used **Filter Current Log** to select `4624,4625`; the view showed **284 matching events** at the time of that capture (not necessarily all failed logons).
5. Filtered specifically for `4625`; the later view showed **two matching events**.
6. Compared their timestamps, account field, and authentication failure codes.
7. Reviewed the first event's reported network source and logon process.

## Observations

| Attribute | Observation |
| --- | --- |
| Failed event count in 4625-only filter | 2 |
| First event | Nov 12, 2026, 12:01:35 PM |
| Second event | Nov 12, 2026, 12:01:41 PM |
| Time separation | 6 seconds |
| Account | Same local lab account in both records (name masked in screenshots) |
| Status | `0xC000006D` — logon failure |
| Substatus | `0xC000006A` — incorrect password |
| First event reported source IP | `127.0.0.1` (loopback) |
| First event logon process | `User32` |
| First event authentication package | `Negotiate` |

## Analysis

The two failed logon records occurred six seconds apart, involved the same account, and reported the same incorrect-password substatus. The first reported source address was the local loopback address, which is consistent with a local authentication test. The captured events also match the intentional incorrect-password exercise performed in this lab.

**Limits of the evidence:** Two closely timed failures are not proof of brute force. The second record's source information was not separately verified, and the screenshots do not establish the cause of unrelated events. The count of 284 refers to a combined 4624/4625 filter at a different point in time, not to 284 failed attempts.

## Evidence

- [Failed logon overview](screenshots/01-failed-logon-overview.png)
- [Incorrect-password failure codes](screenshots/02-failure-code-details.png)
- [Filtered list of two failed events](screenshots/03-failed-events-filter.png)
- [First failure details](screenshots/04-first-failure-details.png)
- [First failure network source (`127.0.0.1`)](screenshots/05-source-information.png)

## Skills practiced

- Navigating Event Viewer and filtering security logs
- Interpreting Windows authentication Event IDs and failure status codes
- Comparing timestamps and account fields across events
- Distinguishing observed evidence from an unproven attack hypothesis
- Writing a short evidence-based investigation report

## Next steps

Continue practice with logon source comparison, broader event correlation, and alert triage; document each new finding separately.

**Privacy:** Public screenshots have had lab account and computer identifiers masked. Original captures are kept out of this repository.
