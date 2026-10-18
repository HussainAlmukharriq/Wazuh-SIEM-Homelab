# 01 - Wazuh Installation

## Purpose

Document the Wazuh SIEM server deployed in my Proxmox homelab. This is a record of my learning process, including configuration, verification, problems, and fixes.

## Environment

| Item | Configuration |
| --- | --- |
| Hypervisor | Proxmox |
| VM ID | 103 |
| Operating system | Ubuntu Server 24.04.5 LTS |
| CPU | 4 vCPU |
| Memory | 8 GB |
| Storage | 60 GB |
| Wazuh version | 4.14.8 |
| Components | Wazuh Manager, Indexer, Dashboard |

The VM is connected to the lab environment. Real internal IP addresses are intentionally omitted from this public repository.

## Installation Status

**Completed:** Wazuh 4.14.8 was installed, and the Manager, Indexer, and Dashboard were configured.

> Note: Exact installation commands and the sequence of installer prompts still need to be reconstructed from my notes or screenshots. I am not listing guessed commands as if I ran them.

## Verification

After installation, I was able to use Wazuh for endpoint monitoring. Three agents were connected and active:

- DC01 — Windows Server domain controller
- WIN11 — Windows 11 workstation
- KALI — Kali Linux

Initial Windows security log review included failed sign-in events (Windows Event ID 4625).

## Installation Screenshots

Screenshots will be added after reviewing them for credentials, tokens, public addresses, and other sensitive information.

## Troubleshooting and Lessons Learned

This section will preserve actual errors, attempted fixes, and successful corrections from the installation. Detailed notes are pending review; I will not invent troubleshooting steps.

## Next Documentation

- Agent deployment and enrollment
- Security event monitoring
- Troubleshooting
- SOC-style incident investigations
