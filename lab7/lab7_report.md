# Lab 7 — Risk Assessment Notes
**Date:** 17 April 2025

## Goal
Review the scan results from Labs 3–6 and write risk notes for the top 5 most dangerous services found.

## Steps
1. Reviewed all nmap output from previous labs
2. Identified the 5 most risky open services
3. Rated each by risk level and explained why it is dangerous
4. Wrote a specific recommendation for each

## Result

**1. SMB — Port 445 — CRITICAL**
SMB has the worst history of any Windows service (EternalBlue, WannaCry). Signing is not required, enabling NTLM relay attacks.

**2. MSRPC — Port 135 — HIGH**
RPC endpoint mapper reveals internal services and has had remote code execution vulnerabilities (MS03-026).

**3. VMware Auth — Port 902 — HIGH**
Exposes hypervisor management to the network. Guest-to-host escape is possible via VMware CVEs.

**4. VMware Auth — Port 912 — MEDIUM**
Older unencrypted version (1.0). Credentials could be captured in plaintext.

**5. DVWA — Port 80 — HIGH**
Running with default credentials (admin/password). Contains intentional SQL injection and XSS vulnerabilities.

## What I Learned
Not all open ports are equal risk. The service type, version, known CVEs, and whether encryption is used all affect how dangerous a port is. SMB is consistently the most dangerous Windows service to expose. Writing risk notes with a level and recommendation is the real output of a security scan.
