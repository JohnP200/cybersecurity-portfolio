# Commands and Wireshark Filters

All commands were run inside an authorized Windows 11 VM. Outputs shown in the project README are from the recorded lab observations; results may differ on another machine.

| Command or filter | What it does |
| --- | --- |
| `ipconfig` | Shows basic network configuration. |
| `ipconfig /all` | Shows detailed adapter, DNS and DHCP configuration. `/all` requests expanded detail. |
| `ping 10.0.2.2` | Tests ICMP echo replies from the VM's default gateway. |
| `ping 1.1.1.1` | Tests ICMP echo replies from an external IP. |
| `nslookup example.com` | Requests DNS information for a domain. |
| `tracert 1.1.1.1` | Attempts to reveal intermediate network hops. |
| `netstat -ano` | Shows network endpoints, numeric addresses and ports, and process IDs. |
| `Get-Process -Id 3760` | Looks up a running process by PID (earlier lab snapshot). |
| `Get-CimInstance Win32_Service \| Where-Object ProcessId -eq 3760` | Filters service information to a PID (earlier snapshot). |
| `nslookup 104.208.203.88` | Attempts reverse DNS lookup for a numeric IP. |
| `Get-NetTCPConnection -State Established` | Lists currently established TCP connections. |
| `Get-NetTCPConnection -State Established \| Select-Object LocalAddress, LocalPort, RemotePort, OwningProcess` | Shows selected connection properties including owning PID; the practiced command does not include `RemoteAddress`. |
| `Get-Process -Id 3128` | Looks up PID 3128 in the later snapshot. |
| `Get-CimInstance Win32_Service \| Where-Object ProcessId -eq 3128` | Retrieves services reporting PID 3128. |
| Wireshark `tcp` | Displays TCP packets. |
| Wireshark `udp` | Displays UDP packets. |
| Wireshark `dns` | Displays packets identified as DNS. |
| Wireshark `ip.addr == 10.0.2.15` | Displays IPv4 packets with the VM's address as source or destination. |
| Wireshark `quic` | Displays packets Wireshark identifies as QUIC. |
| Wireshark `ip.addr == 23.219.160.9` | Displays IPv4 packets involving that external IP. |

**Interpretation notes**

- PowerShell `|` pipes objects to another command. `Where-Object` filters objects; `-eq` means equals; `Select-Object` chooses which properties to show.
- Display filters are not capture filters. They do not remove packets from the saved capture.
- `ACK` means acknowledgment; `FIN` indicates that one TCP endpoint is finished sending in that direction.
- A = IPv4 address lookup, AAAA = IPv6 address lookup, PTR = reverse DNS mapping.
- QUIC uses UDP and integrates TLS 1.3, but a QUIC observation alone does not prove that the application was HTTP/3.
