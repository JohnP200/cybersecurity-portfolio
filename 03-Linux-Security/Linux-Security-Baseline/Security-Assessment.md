# Security Assessment — Scope, Evidence, and Limits

**Scope:** My own Ubuntu Desktop VM in VirtualBox. The review consisted of the commands I personally ran during 26 Linux Fundamentals exercises. No third-party systems were targeted. No external reachability test or exploitation was performed.

## Evidence register

| ID | Command(s) | What the evidence established | Limit |
|---|---|---|---|
| E01 | `cat /etc/os-release` | Ubuntu 26.04.1 LTS | Version does not prove patch status |
| E02 | `uname -r` | Running kernel release `7.0.0-43-generic` | No CVE applicability assessment |
| E03 | `systemctl list-units --type=service --state=running` | 29 running service units at the time | Does not prove all service configurations are safe |
| E04 | `sudo ufw status verbose` | UFW was inactive | Other network controls not checked |
| E05 | `sudo ufw show added` | No user-added UFW rules | Does not describe all firewall rules |
| E06 | `apt list --upgradable` | APT listed pending upgrades | Package indexes might need refresh |
| E07 | `ss -tn` | No matching sockets at that instant | Does not capture short-lived or UDP traffic |
| E08 | `sudo ss -lntup` | Local DNS, printing, time-management and mDNS sockets/processes | Local port binding is not an external exposure test |
| E09 | `journalctl -p err -n 15 --no-pager` | CPU stalls/lockups and watchdog timeouts | Cause not established |
| E10 | `sudo grep -i "authentication failure" /var/log/auth.log` | One graphical login authentication failure in matching lines | Grep also matched the logged command itself; not proof of an attack |
| E11 | `dpkg --audit` | No output / no reported inconsistent packages | Not a full software integrity test |

E08–E11 are **documented results without public screenshots** to avoid publishing unnecessary local identifiers or authentication details. Original evidence stays on my local computer.

## Key observations

**Availability:** CPU soft lockups, RCU stalls, and service watchdog timeouts were present in journal errors, consistent with the VM freezes I encountered. I did not establish causality or identify malicious activity.

**Network exposure:** UFW was inactive. Local DNS, CUPS, and Chrony-related sockets listened on loopback. Avahi/mDNS had wildcard UDP listeners. This merits reviewing service necessity, but NAT routing and filtering were not independently tested.

**Authentication:** An authentication failure involving the lab user appeared in the graphical-login authentication logs. A separate grep match recorded my own search command. Neither entry establishes unauthorized access.

**Patch maintenance:** Multiple packages had newer versions in APT's local indexes. `dpkg --audit` reported no package-state issues. This is maintenance evidence, not confirmation of a particular CVE.

## Risk wording

This is a **baseline learning assessment**, with observations and follow-up recommendations, not a certified risk rating or penetration-test finding. I would not classify a vulnerability as confirmed without additional validation.
