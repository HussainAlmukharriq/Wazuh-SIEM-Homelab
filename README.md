# Wazuh SIEM Homelab

A hands-on cybersecurity homelab project focused on learning security monitoring, threat detection, log analysis, and incident response using Wazuh.

## Project Goal

Build a practical security monitoring environment and document the process of learning skills used by SOC analysts. This repository will include setup notes, experiments, investigation results, troubleshooting, and lessons learned.

## Existing Homelab Environment

My lab uses Proxmox virtualization and includes:

- Windows Server 2022 domain controller (Active Directory and DNS)
- Windows 11 domain-joined workstation
- Kali Linux virtual machine
- A separate lab network for testing

Wazuh integration and any additional systems will be documented as they are configured.

## Planned Work

- [ ] Install and configure Wazuh
- [ ] Connect Windows and Linux endpoints for log collection
- [ ] Explore alerts and security events
- [ ] Simulate authorized security events inside the isolated lab
- [ ] Investigate alerts and document findings
- [ ] Create SOC-style incident reports

## Documentation Approach

This is a learning project, not a polished production deployment. I will keep track of mistakes, failed attempts, troubleshooting steps, and fixes alongside successful results. Completed work will be documented as it happens.

## Safety

All security testing will be limited to systems I own or am authorized to test. Screenshots and logs will be reviewed to avoid publishing passwords, tokens, or other sensitive information.
