# Week 3 – Advanced Cybersecurity Practical: Network Security Assessment & Traffic Investigation

## Project Title
Week 3 Advanced Cybersecurity Practical – Network Discovery, Traffic Analysis, Vulnerability Assessment & Security Hardening

## Objective
This project simulates a real-world security analyst workflow inside an authorized virtual lab. It covers discovering live hosts and exposed services with Nmap, capturing and analyzing live network traffic with Wireshark, correlating an active scan with its packet-level footprint, performing a basic vulnerability assessment with risk classification, and implementing and verifying security hardening measures.

All scanning, traffic capture, and vulnerability testing were performed exclusively against virtual machines owned and controlled by the intern, on an isolated host-only/NAT lab segment. No public or third-party systems were tested at any point.

## Lab Environment
- **Platform:** VMware Workstation
- **Network:** 192.168.17.0/24 (isolated host-only / NAT lab segment)
- **VMs:**
  - Kali Linux 2026 – 192.168.17.128 – Attacker / analyst workstation (Nmap, Wireshark)
  - Metasploitable2-Linux – 192.168.17.129 – Intentionally vulnerable target
- Default gateway: 192.168.17.1
- Local DNS/NAT resolver: 192.168.17.2

## Tools Used
- Nmap 7.98 – host discovery, port scanning, service/version detection, NSE vulnerability scripts
- Wireshark – live packet capture and protocol/traffic analysis (.pcapng)
- UFW (Uncomplicated Firewall) – host-based firewall used for hardening
- systemctl / systemd – service management used to disable an unnecessary service
- VMware Workstation – virtualization platform hosting the isolated lab

## Tasks Completed
- [x] Task 7 – Network Discovery & Basic Nmap Scanning
- [x] Task 8 – Advanced Nmap Security Assessment (service/version scan, NSE vulnerability scan)
- [x] Task 9 – Wireshark Network Traffic Capture
- [x] Task 10 – Nmap + Wireshark Investigation
- [x] Task 11 – Advanced Network Traffic Investigation
- [x] Task 12 – Vulnerability Assessment
- [x] Task 13 – Security Hardening & Before/After Testing
- [x] Task 14 – Final Mini Security Assessment

## Key Findings
Seven security findings were documented and risk-classified:

| # | Finding | Risk |
|---|---------|------|
| 1 | vsFTPd 2.3.4 backdoor (21/tcp) – CVE-2011-2523, verified root shell | Critical |
| 2 | Unauthenticated root bindshell (1524/tcp) | Critical |
| 3 | Backdoored UnrealIRCd build (6667/tcp) | Critical |
| 4 | Telnet enabled (23/tcp) – cleartext credentials | High |
| 5 | Outdated Samba 3.X–4.X (139/445 tcp) | High |
| 6 | Weak-authentication VNC protocol 3.3 (5900/tcp) | Medium |
| 7 | Excessive service exposure – 23 open ports on one host | Medium |

Traffic analysis of the 2,238-packet capture confirmed an authorized Nmap SYN scan (192.168.17.128 → 192.168.17.129) accounting for ~92% of captured packets, and flagged a DNS/ICMP inconsistency on the local resolver worth follow-up.

## Security Improvements
1. **Disabled unnecessary SSH service** on the Kali analyst VM (`systemctl disable --now ssh`)
2. **Enabled UFW host firewall** on the Metasploitable target with an explicit SSH allow rule (`ufw allow ... proto tcp`, `ufw enable`)
3. **Blocked insecure Telnet** at the firewall (`ufw deny 23/tcp`)

## Before/After Results
| Issue | Before | After |
|-------|--------|-------|
| SSH on Kali | Enabled, active at boot | Disabled & stopped |
| Host firewall on target | Not loaded; SSH open to subnet | Loaded; explicit SSH allow rule |
| Telnet (23/tcp) | Open, reachable | Blocked (DENY) |

The three Critical, service-level backdoors (vsFTPd, bindshell, UnrealIRCd) remain and require software-level remediation — the top priority for the next hardening pass.

## Conclusion
This assessment walked a full network-security workflow end to end: discovery, traffic capture, packet-level scan correlation, risk-classified vulnerability assessment, and verified hardening. Three Critical unauthenticated remote-compromise paths were confirmed on the target, and firewall-based hardening measurably reduced exposure on the two riskiest network-reachable legacy services, while the service-level backdoors remain flagged for follow-up remediation.

## Contents
- `01-Nmap/` – Nmap scan outputs and screenshots
- `02-Wireshark/` – Packet capture (.pcapng) and screenshots
- `03-Vulnerability-Assessment/` – Findings and risk classification
- `04-Hardening/` – Before/after hardening evidence
- `Network-Diagram/` – Lab topology diagram
- `Week-3-Report.pdf` – Full written report
- `Week-3-Presentation.pptx` – Summary presentation

## Disclaimer
All testing was performed in an isolated, authorized lab environment against virtual machines owned by the intern. No public or third-party systems were scanned or tested.