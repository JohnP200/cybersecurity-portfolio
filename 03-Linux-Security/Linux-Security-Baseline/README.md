# Linux Security Baseline Assessment (Ubuntu VM)

This is a **beginner, authorized security review of my own Ubuntu virtual machine**. I completed 26 guided Linux Fundamentals exercises and used the results to document system configuration, security-relevant logs, listening sockets, and basic software-maintenance checks.

I focused on understanding what the commands actually showed. I did **not** run a penetration test, demonstrate an exploit, scan third-party hosts, or confirm a compromise.

## Environment

| Item | Observed result |
|---|---|
| Platform | Ubuntu Desktop 26.04.1 LTS (VirtualBox lab) |
| Kernel | `7.0.0-43-generic` |
| Network | VirtualBox-style NAT configuration, private IPv4 address |
| Assessment scope | My own VM, command-line inspection only |
| Assessment date | November 2026 |

Exact hostnames, usernames, MAC addresses, local IPs, unique machine identifiers, and full authentication records have intentionally been omitted from this public version.

## Skills demonstrated

- Navigate Linux, create files, and inspect file permissions (`pwd`, `ls`, `cd`, `mkdir`, `touch`, `cat`, `chmod`).
- Review account identity and groups (`whoami`, `groups`).
- Investigate processes and services (`ps`, `top`, `grep`, `systemctl`).
- Examine system and authentication logs (`journalctl`, `tail`, `grep`).
- Review login history and sessions (`last`, `who`, `w`).
- Inspect network interfaces, routing, TCP/UDP sockets, and owning processes (`ip`, `ss`, `ping`).
- Review UFW and package-maintenance status (`ufw`, `apt`, `dpkg`).

## Findings (limited, evidence-based)

| Observation | Evidence | Interpretation |
|---|---|---|
| UFW reported `inactive` with no user-added rules | `sudo ufw status verbose`; `sudo ufw show added` | Hardening opportunity, **not proof** there is no other firewall or that the VM is publicly exposed. |
| One local discovery service listened on wildcard UDP interfaces | `sudo ss -lntup` | Review whether mDNS is needed; NAT/firewall/routing determine actual reachability. |
| Journal included CPU stalls, soft lockups, and watchdog timeouts | `journalctl -p err -n 15 --no-pager` | Reliability/availability concern in the VM; root cause not confirmed. |
| One failed graphical authentication record was observed | `sudo grep -i "authentication failure" /var/log/auth.log` | A single failure; no evidence in this sample of brute force or an attacker. |
| APT listed multiple upgradable packages | `apt list --upgradable` | Review updates with refreshed package lists; not all are security fixes. |
| `dpkg --audit` produced no findings | `dpkg --audit` | No inconsistent package states reported by this check; not a full security assessment. |
| No non-listening TCP sockets were shown in two snapshots | `ss -tn`; `ss -tn state established` | Momentary observation only, **not** evidence of no network activity. |

## What I would do next

1. Preserve a working VM snapshot and investigate virtualization stability before heavier exercises.
2. Refresh package metadata, review security advisories, and apply appropriate updates with a rollback plan.
3. Review the need for network-discovery and printing services; validate network reachability before changing anything.
4. Decide on appropriate host firewall policy, then verify it without interrupting required services.
5. Compare authentication events over time before making security claims.

## Evidence and privacy

The images in [`Screenshots/`](Screenshots/) are **cropped output excerpts from my actual lab screenshots**. They are not fabricated console output. Full terminal prompts were excluded to avoid publishing local account and machine names. Screenshots with authentication logs, MAC/IP identifiers, or other host-specific fields are **deliberately not included**; their findings are summarized above. Cropping is not a guarantee that every future screenshot is safe, so all added images should be checked manually before publication.

This portfolio documents a learning lab. It is not an audit opinion, a vulnerability scan, or a claim that the VM is secure.
