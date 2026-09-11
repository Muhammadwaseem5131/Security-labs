# Security Labs — Complete Portfolio
**Student:** Waseem  
**Environment:** Kali Linux ("wiki") on Oracle VirtualBox 7.x — Windows 10 Pro host  
**Network:** VirtualBox NAT 10.0.2.0/24 | Kali: 10.0.2.15 | Gateway: 10.0.2.2  
**Completed:** 2025-11-11  

---

## Lab Overview

### Level 1 — Foundation (Reconnaissance & Network Mapping)

| Lab | Title | Key Tool | Screenshot |
|-----|-------|----------|-----------|
| [Lab 1](lab1/lab1_report.md) | Kali Setup & Network Config | `ip addr show` | lab1_ipaddr.png |
| [Lab 2](lab2/lab2_report.md) | Host Discovery | `nmap -sn 10.0.2.0/24` | lab2_host_discovery.png |
| [Lab 3](lab3/lab3_report.md) | Port Scanning | `nmap -p 1-1000 10.0.2.2` | lab3_port_scan.png |
| [Lab 4](lab4/lab4_report.md) | Service Version ID | `nmap -sV -p 135,445,902,912 10.0.2.2` | lab4_service_versions.png |
| [Lab 5](lab5/lab5_report.md) | Network Map | Diagram from scan data | (diagram in report) |

**Key Findings:** 3 live hosts, 5 open ports on gateway, Windows 10 OS identified, VMware management exposed.

---

### Level 2 — Vulnerability Assessment & Web Security

| Lab | Title | Key Tool | Screenshot |
|-----|-------|----------|-----------|
| [Lab 6](lab6/lab6_report.md) | Full Aggressive Scan | `nmap -A 10.0.2.2` | lab6_full_scan.png, lab6_ports_table.png |
| [Lab 7](lab7/lab7_report.md) | Risk Assessment Notes | Analysis | (written report) |
| [Lab 8](lab8/lab8_report.md) | DVWA Setup & Login | Apache2 + PHP + MySQL | lab8_dvwa_*.png |
| [Lab 9](lab9/lab9_report.md) | SQL Injection | DVWA + Firefox | lab9_sqli_*.png |
| [Lab 10](lab10/lab10_report.md) | XSS (Reflected & Stored) | DVWA + Firefox | lab10_xss_*.png |

**Key Findings:** SMB signing not required (relay risk), DVWA exploitable via SQLi and XSS with default creds.

---

### Level 3 — IoT-Style Exposure

| Lab | Title | Key Tool | Screenshot |
|-----|-------|----------|-----------|
| [Lab 11](lab11/lab11_report.md) | IoT Exposure Checklist | nmap port checks | (written checklist) |
| [Lab 12](lab12/lab12_report.md) | Mini Exposure Report | Analysis | (written report) |
| [Lab 13](lab13/lab13_report.md) | Default Service Risk | Documentation | (written catalog) |

**Key Findings:** No Telnet/FTP/SNMP found (good). DVWA with default creds is critical risk. Default configs catalogued.

---

### Level 4 — Digital Forensics

| Lab | Title | Key Tool | Screenshot |
|-----|-------|----------|-----------|
| [Lab 14](lab14/lab14_report.md) | File Hashing | `md5sum`, `sha1sum`, `sha256sum` | lab14_file_hashing.png |
| [Lab 15](lab15/lab15_report.md) | Log Inspection | `journalctl` | lab15_log_inspection.png |
| [Lab 16](lab16/lab16_report.md) | Incident Note | Analysis report | (written report) |

**Key Findings:** Hash comparison detects file tampering. journalctl shows kernel errors (expected in VM). Incident timeline documented.

---

### Level 5 — Malware Awareness

| Lab | Title | Key Tool | Screenshot |
|-----|-------|----------|-----------|
| [Lab 17](lab17/lab17_report.md) | Static File Inspection | `file`, `strings`, `xxd`, `base64` | lab17_static_analysis.png |
| [Lab 18](lab18/lab18_report.md) | Malware Analysis Notes | `ps`, `ss`, `find`, `journalctl` | lab18_malware_analysis.png |

**Key Findings:** MZ header detected; base64 obfuscation decoded; SUID binaries identified; system baseline established.

---

## Skills Demonstrated

| Skill | Labs |
|-------|------|
| Network scanning & host discovery | 1, 2, 3, 4, 5, 6 |
| Service identification & fingerprinting | 4, 6 |
| Risk assessment & documentation | 7, 12, 13 |
| Web application security (SQLi, XSS) | 9, 10 |
| DVWA setup & exploitation | 8, 9, 10 |
| IoT security assessment | 11, 12, 13 |
| File integrity & hashing | 14 |
| Log analysis & forensics | 15, 16 |
| Static malware analysis | 17 |
| Live system behavior analysis | 18 |

## Tools Used
- **nmap** — network scanner
- **DVWA** — vulnerable web application for practice
- **Apache2 + PHP + MySQL** — web stack
- **journalctl** — systemd log inspector
- **md5sum / sha256sum** — file hashing
- **file / strings / xxd** — static file analysis
- **ps / ss / find** — system behavior inspection

