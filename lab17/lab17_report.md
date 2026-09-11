# Lab 17 — Static File Inspection
**Date:** 23 October 2025

## Goal
Analyse suspicious files without executing them using static analysis tools to identify file type, hidden content, and malicious indicators.

## Steps
1. Created a test Windows executable: `printf 'MZ\x90\x00' > /tmp/suspicious.exe`
2. Created an obfuscated script with a base64-encoded command
3. Used `file` to detect the true type of each file
4. Used `strings` to extract readable text from the binary
5. Used `xxd` to view the raw hex dump of the file header
6. Decoded the base64 payload manually: `echo 'ZWNobyAi...' | base64 -d`
7. Used `find /usr/bin -perm -4000` to find SUID binaries

## Result
- `file suspicious.exe` → **MS-DOS executable, MZ for MS-DOS** (Windows PE confirmed)
- `strings suspicious.exe` → revealed: "This program cannot be run in DOS mode"
- `xxd` hex dump → `4D 5A` = MZ signature (Windows EXE marker in every PE file)
- Base64 decode → `echo "Hello World"` (hidden command revealed)
- SUID binaries found: `su`, `mount`, `gpasswd`, `pkexec`, `newgrp`

## What I Learned
Static analysis means examining a file without ever running it — always the safe first step. The `file` command reads the magic bytes in the file header to identify its true type, ignoring the filename extension. `strings` extracts all readable text embedded in any binary. Base64 is the most common obfuscation trick in malware scripts because it hides the real command from casual inspection. SUID binaries run as root regardless of who launches them — finding unexpected ones is a red flag for privilege escalation.
