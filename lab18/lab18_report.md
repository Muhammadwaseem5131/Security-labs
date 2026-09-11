# Lab 18 — Malware Analysis Notes
**Date:** 11 November 2025

## Goal
Examine a running system for behavioural signs of malware infection: unusual processes, unexpected network connections, suspicious files, and persistence mechanisms.

## Steps
1. Ran `ps aux --sort=-%cpu` to list all processes sorted by CPU usage
2. Ran `ss -tulnp` to see all open network ports and the process that owns each one
3. Checked `ls -la /tmp/` for unexpected executable files
4. Ran `crontab -l` to look for hidden persistence via scheduled jobs
5. Read `cat /etc/hosts` to check for DNS hijacking
6. Ran `systemctl list-units --state=running` to see all active services

## Result
- **Processes:** All identified — gnome-shell, VBoxService, Firefox, no unknown processes
- **Network:** MySQL on 127.0.0.1:3306 (local only), Apache on :80, no unknown outbound connections
- **Ports flagged:** 4444, 1337 not present (common malware ports — all clear)
- **Cron:** No user cron jobs configured
- **/etc/hosts:** Clean — only standard localhost entries
- **Services:** All standard Kali services, nothing unexpected

No indicators of compromise found on this system.

## What I Learned
Malware leaves traces in three places: processes, network, and files. Knowing what is "normal" on a clean system is essential — you cannot spot anomalies without a baseline. Malware commonly listens on port 4444 (Metasploit default) or connects outbound to unknown IPs. Cron jobs and systemd services are the two main ways malware survives reboots (persistence). Tools like Volatility (memory forensics) and YARA (signature matching) extend this kind of manual analysis in real investigations.
