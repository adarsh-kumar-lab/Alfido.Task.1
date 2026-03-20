# Alfido.Task.1
Reconnaissance &amp; Vulnerability Scanning using Nmap and Nikto on a Kali Linux virtual lab | Alfido Tech Cybersecurity Internship - Task 1
# 🔐 Task 1 — Reconnaissance & Vulnerability Scanning

**Alfido Tech Cybersecurity Internship**
**Candidate:** Adarsh Kumar Tiwari | ID: BS/REG/117244

## 📌 Overview
Performed network reconnaissance and vulnerability scanning on a controlled virtual lab using Kali Linux.

## 🛠️ Tools Used
- **Nmap 7.98** — Port scanning, service detection, OS fingerprinting
- **Nikto v2.6.0** — Web vulnerability scanning
- **Environment:** Kali Linux on VirtualBox (isolated lab network 10.0.2.0/24)

## 🔍 What I Did
- Ran a ping sweep to discover live hosts on the network
- Performed deep SYN scan with version detection on target 10.0.2.15
- Identified open ports: 135 (MSRPC), 445 (SMB), 902/912 (VMware), 3090 (unknown)
- Attempted Nikto web scan (no web server found — documented)

## ⚠️ Vulnerabilities Found
| Risk | Issue | Severity |
|------|-------|----------|
| SMB port 445 open | EternalBlue/WannaCry risk | 🔴 HIGH |
| VMware ports 902/912 | Should be restricted | 🟡 MEDIUM |
| DNS server ID exposed | Info leak | 🟡 MEDIUM |
| MSRPC port 135 | Enumeration risk | 🟢 LOW |

## 📄 Files
- `Vulnerability_Report_Student.docx` — Full written report
- `nmap.docx` — Nmap scan screenshots

> ⚠️ All scans performed only on personal virtual lab machines. No external systems were targeted.
