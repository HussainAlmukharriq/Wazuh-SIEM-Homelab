# Wazuh SIEM Homelab

A hands-on cybersecurity homelab for security monitoring, log analysis, threat detection, and incident response using Wazuh.

## Project Goal

Build practical SOC analyst skills by deploying Wazuh, connecting endpoints, reviewing security events, investigating alerts, and documenting troubleshooting and lessons learned.

## Lab Environment

- **Hypervisor:** Proxmox
- **Wazuh VM:** VM 103, Ubuntu Server 24.04.5 LTS
- **Resources:** 4 vCPU, 8 GB RAM, 60 GB disk
- **Wazuh:** 4.14.8, Manager + Indexer + Dashboard
- **Dashboard network IP:** 10.0.0.232
- **Lab network IP:** 10.10.10.102
- **Lab network:** Isolated from the home network for testing

## Connected Agents

| Agent | System | Lab IP | Status |
| --- | --- | --- | --- |
| 001 / DC01 | Windows Server | 10.10.10.10 | Active |
| 002 / WIN11 | Windows 11 Pro | 10.10.10.100 | Active |
| 003 / KALI | Kali Linux | 10.10.10.101 | Active |

## Completed Work

- [x] Deploy Ubuntu Server VM in Proxmox
- [x] Install Wazuh Manager, Indexer, and Dashboard
- [x] Connect DC01, WIN11, and KALI agents
- [x] Verify DC01 event collection
- [x] Investigate Windows Event ID 4625 (failed logon)
- [x] Troubleshoot Windows 11 agent installation

## Next Steps

- [ ] Write detailed setup notes and add sanitized screenshots
- [ ] Document the Windows 11 agent troubleshooting steps
- [ ] Expand controlled security-event simulations
- [ ] Produce SOC-style investigation reports

## Documentation Approach

This repository records actual work, including mistakes, failed attempts, troubleshooting, corrections, and lessons learned. No uncompleted tasks are presented as finished.

## Safety

Security testing is limited to owned or authorized lab systems. Logs and screenshots should be reviewed before publication to avoid leaking passwords, tokens, and other sensitive information.
