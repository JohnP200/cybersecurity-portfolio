# Cybersecurity Portfolio

Welcome to my cybersecurity portfolio!

I'm currently learning cybersecurity and building my skills through hands-on labs and personal projects. I'm especially interested in security monitoring, network security, Linux, and understanding how cybersecurity professionals investigate suspicious activity.

I created this portfolio to document what I've learned, practice using different security tools, and show the progress I'm making.

## My Projects

### 01 — Windows Event Viewer: Authentication Log Investigation

[View Project](01-Security-Monitoring/Windows-Event-Viewer/README.md)

In this project, I used Windows Event Viewer to investigate authentication activity inside my Windows 11 virtual machine.

I focused on identifying successful and failed login attempts, understanding Windows Security event IDs, and learning how to recognize unusual authentication activity.

**What I practiced:**
- Using Windows Event Viewer
- Investigating Event IDs 4624 and 4625
- Filtering Windows Security logs
- Reviewing failed login attempts
- Understanding why multiple failed logins might need further investigation

**Tools:** Windows 11, Event Viewer, VirtualBox

### 02 — Network Fundamentals & Wireshark Traffic Analysis

[View Project](02-Network-Security/Network-Fundamentals/README.md)

For this project, I focused on understanding how computers communicate over networks.

I started by using PowerShell to examine IP addresses, network connections, DNS lookups, and running processes.

After that, I installed Wireshark and practiced capturing and analyzing network packets.

One of the more interesting parts was learning about QUIC traffic and seeing how encrypted communication appears in Wireshark.

**What I practiced:**
- Understanding IPv4 and IPv6 addresses
- Testing network connectivity
- Using PowerShell networking commands
- Investigating TCP and UDP connections
- Identifying processes and Windows services
- Capturing packets with Wireshark
- Analyzing DNS requests and responses
- Using Wireshark display filters
- Examining QUIC network traffic

**Tools:** Windows 11, PowerShell, Wireshark, Npcap, VirtualBox

### 03 — Linux Security Baseline Assessment

[View Project](03-Linux-Security/Linux-Security-Baseline/README.md)

For this project, I completed 26 Linux Fundamentals exercises using an Ubuntu virtual machine.

I started by learning basic Linux commands, including how to navigate directories, create files, and manage file permissions.

As I became more comfortable using the terminal, I started learning how to investigate running processes, system services, authentication logs, and network connections.

For my final exercise, I performed a basic security assessment of my Ubuntu system. I checked the operating system version, Linux kernel, available software updates, and package health. I also reviewed some of the security-related findings from my earlier exercises.

One thing I learned was that not every error message or unfamiliar service means something malicious is happening. It's important to understand what the results actually show before making assumptions.

**What I practiced:**
- Navigating Linux using the terminal
- Creating files and directories
- Understanding and changing file permissions
- Checking user accounts and group memberships
- Investigating running processes
- Reviewing system services
- Reading system logs and authentication events
- Checking TCP and UDP listening ports
- Examining network interfaces and routing
- Reviewing firewall configuration using UFW
- Checking available software updates
- Identifying potential security and system maintenance concerns
- Documenting findings from a basic security investigation

**Tools:** Ubuntu Desktop, Linux Terminal, VirtualBox

## Skills I'm Learning

I'm currently building my knowledge in several areas of cybersecurity.

**Security Monitoring**
- Windows Security logs
- Authentication events
- Basic security investigations
- Reviewing system activity

**Networking**
- TCP/IP
- DNS
- TCP and UDP
- IP addressing
- Network troubleshooting

**Network Analysis**
- Wireshark
- Packet captures
- Network protocols
- TCP flags
- DNS traffic analysis

**Linux Fundamentals**
- Linux terminal commands
- File and directory permissions
- User accounts and groups
- Running processes and services
- System and authentication logs
- Network connections and listening ports
- Basic firewall configuration
- Software updates and package management

I'm still developing these skills and plan to continue adding projects as I learn more.

## My Lab Setup

For my projects, I use Windows 11 and Ubuntu virtual machines in VirtualBox.

This gives me a controlled environment where I can practice commands, explore security tools, and investigate system and network activity.

I also use GitHub to organize my projects and Obsidian to keep track of what I'm learning.

All projects are completed in my own authorized lab environment.

## What I'm Working Toward

My goal is to continue improving my technical skills and eventually work in cybersecurity.

I'm particularly interested in security monitoring, investigating suspicious activity, and understanding how businesses can better protect their systems.

I also enjoy learning how different operating systems and networks work.

I'm still learning, and I know there's a lot more to cybersecurity than what I've practiced so far.

I'll continue updating this portfolio as I complete more labs, learn new tools, and work on more challenging projects.

---

*These projects are part of my learning experience. They represent hands-on practice rather than professional incident-response work. I review screenshots before publishing to avoid sharing unnecessary personal or system information. Raw authentication logs and packet captures are not included.*
