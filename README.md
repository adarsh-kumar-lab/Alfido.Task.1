# Alfido.Task.1
I did my first real recon and vulnerability scan using Nmap and Nikto on my own Kali Linux lab. Found some interesting stuff — SMB open, VMware ports exposed, and more. Part of my Alfido Tech cybersecurity internship.

# Task 1 — Recon & Vulnerability Scanning

This is my first task for the Alfido Tech Cybersecurity Internship.
I'm Adarsh Kumar Tiwari (ID: BS/REG/117244) and this is where I document what I did.

## What this task was about

I had to do a proper reconnaissance and vulnerability scan on a network — 
but obviously not on any real-world system. So I set up a virtual lab on 
VirtualBox using Kali Linux and scanned my own machines. Everything was 
contained inside my local lab network (10.0.2.0/24).

## Tools I used

- **Nmap 7.98** — for scanning ports, detecting services, and OS guessing
- **Nikto v2.6.0** — for checking web vulnerabilities (spoiler: no web server was found)
- **Kali Linux** — my main attacking machine running on VirtualBox

## What I actually did

First I ran a ping sweep to see who's alive on the network. Found 3 hosts.
Then I picked the most interesting one (10.0.2.15) and hit it with a full 
SYN scan — service versions, OS detection, default scripts, everything.

Here's what was open on the target:
- **Port 445** — SMB (this is the WannaCry port, definitely worth flagging)
- **Port 135** — MSRPC (Windows remote communication)
- **Ports 902 & 912** — VMware authentication services
- **Port 3090** — something wrapped/hidden, couldn't identify it

I also scanned the DNS server (10.0.2.3) and found it was leaking its 
server ID — small thing but real attackers notice stuff like that.

Nikto failed because there was no web server running. I still documented 
it because in real pentests you document everything, even the things that 
don't work.

## What I found (risks)

| Issue | How bad | Quick fix |
|-------|---------|-----------|
| SMB port 445 open | 🔴 High | Firewall it, patch Windows, disable SMBv1 |
| VMware ports exposed | 🟡 Medium | Lock to management network only |
| DNS leaking server ID | 🟡 Medium | Disable server-id in Unbound config |
| MSRPC port 135 | 🟢 Low | Block from untrusted networks |
| Unknown port 3090 | 🟢 Low | Figure out what's using it, close if not needed |

## Files in this repo

- `Vulnerability_Report_Student.docx` — my full written report with everything explained
- `nmap.docx` — screenshots of all the Nmap scans I ran

## Quick note

Everything here was done on my own virtual machines inside VirtualBox.
No real systems, no internet targets — just my lab. I'm still learning 
but I made sure to do this properly and ethically.
