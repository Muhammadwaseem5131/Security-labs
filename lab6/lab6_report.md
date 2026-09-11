# Lab 6 — Full Aggressive Scan
**Date:** 02 April 2025

## Goal
Run a full nmap aggressive scan on the gateway to get OS detection, service versions, default scripts, and traceroute in one command.

## Steps
1. Opened a terminal in Kali Linux
2. Ran: `sudo nmap -A 10.0.2.2`
3. Waited for the complete scan (OS detection, scripts, traceroute all run automatically)
4. Saved output: `sudo nmap -A 10.0.2.2 | tee /tmp/lab6_scan.txt`

## Result
- **OS detected:** Microsoft Windows 10 (97% confidence)
- **Open ports:** 135, 445, 902, 912
- **SMB:** SMB2 enabled, signing not required (relay attack possible)
- **Traceroute:** 1 hop to 10.0.2.2 (same subnet, 0.4ms)
- **NetBIOS name** visible via SMB script

## What I Learned
`-A` is shorthand for four flags combined: OS detection (`-O`), version detection (`-sV`), default scripts (`--script=default`), and traceroute (`--traceroute`). It gives a complete picture of a target in one scan. SMB signing not required means an attacker on the same network could intercept and relay authentication — a real-world attack known as NTLM relay.
