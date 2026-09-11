# Lab 15 — Log Inspection
**Date:** 27 August 2025

## Goal
Use `journalctl` to read Kali Linux system logs and identify security-relevant events, errors, and authentication activity.

## Steps
1. Opened a terminal in Kali Linux
2. Ran `journalctl -n 50` to view the last 50 log entries
3. Ran `journalctl -k -n 30` to see kernel-level messages
4. Ran `journalctl -p err -n 20` to filter for errors only
5. Looked for authentication events, service starts, and hardware warnings

## Result
Key log entries found:
```
kernel: acpi PNP0A03: fail to add MMCONFIG — hardware config warning (normal in VM)
kernel: vmwgfx *ERROR* unsupported hypervisor — VMware graphics in VirtualBox (expected)
kernel: vmwgfx *ERROR* This configuration is likely broken — cosmetic warning
systemd[1]: Started polkit.service — privilege manager started normally
virtualbox-guest-utils: error: XDG_RUNTIME_DIR is invalid — cosmetic VBox issue
```

No authentication failures or suspicious login attempts found.

## What I Learned
`journalctl` is the systemd log viewer — it replaces the old `/var/log/syslog` on modern Linux systems. The kernel errors about vmwgfx are expected and harmless when running inside VirtualBox. In a real incident, logs are the most important source of evidence because they record exactly what happened and when. Monitoring for "Failed password for" or unexpected `sudo` usage in logs can catch attackers early.
