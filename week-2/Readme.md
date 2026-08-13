# DG Interns Hub — Cybersecurity Internship: Week 2

**Advanced Networking, Traffic Analysis & Security Concepts**

Prepared as part of the DG Interns Hub free Cybersecurity Internship program. All practicals were performed using free tools in a safe, simulated/authorized environment — no unauthorized systems were scanned or attacked.

## 🎯 Objective

Understand advanced networking concepts, analyze real network traffic, perform basic scanning, and learn core security-attack concepts (MITM, DoS, packet sniffing) along with their prevention measures.

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| **Wireshark** | Captured & analyzed live DNS and TLS/HTTPS traffic |
| **Nmap** | Scanned the authorized target `scanme.nmap.org` for open ports & services |
| **Cisco Packet Tracer** | Built LAN topologies, configured IPs, verified connectivity, modeled the MITM concept |

## 📋 Tasks Covered

1. **Ports & Services** — Documented 25+ common TCP/UDP ports (SSH, DNS, HTTP/HTTPS, SMTP, DHCP, RDP, SMB, etc.) with protocol and usage.
2. **Networking Devices** — Router (Layer 3), Switch (Layer 2), and Firewall (L3–L7): functions, real-world examples, and a router vs. switch comparison.
3. **Network Security Basics** — Core attack concepts: Man-in-the-Middle, Denial of Service, and Packet Sniffing, plus prevention measures (HTTPS, VPN, WPA2/WPA3, Dynamic ARP Inspection, firewalls/IDS-IPS).
4. **Packet Analysis (Wireshark)** *— Practical* — Captured live traffic, filtered on `dns` and `tls`, and inspected a TLS 1.3 Client Hello (SNI = `github.com`) to confirm source/destination IPs while payload stayed encrypted.
5. **Network Scanning (Nmap)** *— Practical* — Ran a basic scan and a service/version detection scan (`-sV`) against `scanme.nmap.org`, identifying open ports (SSH, HTTP) and fingerprinting the OS as Linux.
6. **Packet Tracer LAN Setup** *— Practical* — Built a two-PC LAN via a single switch (PC0: `192.168.1.10`, PC1: `192.168.1.11`); verified connectivity with a 4/4 successful ping, 0% packet loss.
7. **MITM Concept** *— Safe Simulation* — Modeled attacker/victim/router topology to visualize how ARP spoofing enables traffic interception, without generating any real attack traffic.

## 🔑 Key Learnings

- Saw how DNS resolution and TLS-encrypted traffic actually appear on the wire using Wireshark.
- Used Nmap to discover open ports and fingerprint services on an authorized target.
- Built and verified LAN connectivity in Cisco Packet Tracer with real IP addressing.
- Understood MITM, DoS, and packet sniffing concepts, and how HTTPS/VPN/ARP protections defend against them.

## ⚠️ Disclaimer

All scanning and traffic-capture activity was performed only against explicitly authorized/self-owned targets (e.g., `scanme.nmap.org`, personal traffic, isolated Packet Tracer simulations). No real-world systems were scanned, intercepted, or attacked without permission.

## 👤 Author

DG Interns Hub — Cybersecurity Internship, Week 2 Submission