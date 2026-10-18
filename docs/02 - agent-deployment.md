# 02 - Wazuh Agent Deployment

## Goal

Connect the lab endpoints to the Wazuh manager so I can collect security events and practice monitoring and investigations.

## Lab Endpoints

| Endpoint | Operating system | Purpose | Status |
| --- | --- | --- | --- |
| DC01 | Windows Server 2022 | Domain controller and Windows security events | Connected |
| WIN11 | Windows 11 Pro | Domain-joined workstation | Connected |
| KALI | Kali Linux | Linux endpoint and security testing | Connected |

The agents communicate with the Wazuh server over the lab network. Actual internal IP addresses are omitted from this public documentation.

## Completed Work

- [x] Connected the Windows Server domain controller to Wazuh.
- [x] Connected the Windows 11 workstation to Wazuh.
- [x] Connected the Kali Linux endpoint to Wazuh.
- [x] Verified that all three agents showed as active.
- [x] Reviewed Windows security events from DC01.

## Verification and First Investigation

Windows Event ID **4625** represents a failed account logon. I reviewed these events as an initial exercise in security monitoring. A future incident report will document the investigation evidence, findings, and interpretation in detail.

## Windows 11 Agent Troubleshooting

The Windows 11 agent installation required troubleshooting before the endpoint was successfully connected. The exact error messages, commands attempted, and corrections still need to be recovered from the lab notes or screenshots. I will add them rather than invent a clean installation sequence.

## Evidence to Add

- [ ] Wazuh dashboard showing three active agents
- [ ] Agent details for DC01, WIN11, and KALI
- [ ] Sanitized Windows 11 troubleshooting screenshots or logs
- [ ] Example DC01 Windows Event ID 4625 alert

## Lessons Learned

Connecting endpoints is only the first step. Confirming agent status and reviewing actual collected events are necessary to establish that monitoring is working. This page will be expanded as I recover the original deployment steps and troubleshooting history.
