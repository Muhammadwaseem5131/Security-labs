# Lab 12 — Mini Exposure Report
**Date:** 15 July 2025

## Goal
Write a short structured security report summarising all findings from the previous labs as a real deliverable.

## Steps
1. Collected all findings from Labs 2–11
2. Sorted findings by risk level (Critical to Low)
3. Wrote a short description and recommendation for each finding
4. Summarised the overall network risk

## Result

**CRITICAL — DVWA default credentials (10.0.2.15:80)**
Login works with admin/password. Full web app compromise possible.
Fix: Change credentials immediately. Isolate to lab network.

**HIGH — SMB exposed (10.0.2.2:445)**
SMB signing not required. Known history of remote exploitation.
Fix: Enable SMB signing. Block port 445 from untrusted hosts.

**HIGH — MSRPC exposed (10.0.2.2:135)**
Reveals internal RPC endpoints. History of RCE vulnerabilities.
Fix: Firewall port 135 from untrusted networks.

**MEDIUM — VMware ports exposed (10.0.2.2:902,912)**
Hypervisor management reachable from guest VM.
Fix: Bind to localhost only.

**GOOD — No Telnet, FTP, SNMP, or UPnP found.**

Overall risk rating: **HIGH**

## What I Learned
A real security report must be readable by someone who did not do the testing. Each finding needs: what it is, why it matters, and exactly how to fix it. Sorting by severity tells the reader where to focus first. The best reports are short and specific — not long lists of technical details that nobody reads.
