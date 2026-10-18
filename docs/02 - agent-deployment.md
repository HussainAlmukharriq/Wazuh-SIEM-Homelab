# 02 - Wazuh Agent Deployment

## Goal

Connect three endpoints to Wazuh 4.14.8 and verify that they are actively reporting to the manager.

## Environment

| Agent ID | Host | Operating system reported by Wazuh | Status |
| --- | --- | --- | --- |
| 001 | DC01 | Windows Server 2025 Standard Evaluation | Active |
| 002 | WIN11 | Windows 11 Pro | Active |
| 003 | Kali | Kali GNU/Linux 2026.2 | Active |

All three endpoints appeared under the default group on node01. Real internal IP addresses are omitted from this public document.

## DC01: First Connected Agent

The first dashboard verification showed DC01 as the only active agent. Later, DC01 and WIN11 both appeared as active.

## WIN11: Installation and Troubleshooting

The Windows 11 installation did not succeed on the first attempt. The following is preserved as an actual troubleshooting record.

1. Downloaded the Wazuh 4.14.8 Windows installer using PowerShell and attempted a silent installation with `msiexec.exe`.
2. Checked the service using `Get-Service -Name WazuhSvc`. PowerShell reported that no matching service was found, so the agent was not yet installed as a working Windows service.
3. Inspected the downloaded file in the temporary directory using `Get-Item`.
4. Checked Windows Installer event logs. Event ID 1033 recorded Wazuh Agent 4.14.8 with installation status **1602** (installation canceled). The event does not identify the underlying reason for cancellation.
5. Retried installation using `msiexec.exe` with logging enabled. A screenshot shows `$LASTEXITCODE` being checked, but does not show its resulting value.
6. Started the service with `Start-Service -Name WazuhSvc` and confirmed with `Get-Service -Name WazuhSvc` that it was **Running**.
7. Confirmed that WIN11 appeared alongside DC01 in the Wazuh dashboard, both marked active.

### Commands used for diagnosis

```powershell
Get-Service -Name WazuhSvc
Get-Item "$env:TEMP\wazuh-agent"
Test-Path "$env:TEMP\wazuh-agent"
Start-Service -Name WazuhSvc
```

- `Get-Service` queries a Windows service; `-Name` selects the service's internal name.
- `Get-Item` inspects the downloaded file or folder.
- `$env:TEMP` refers to the current user's temporary directory.
- `Test-Path` checks whether a path exists.
- `Start-Service` attempts to start the specified service.

The screenshots also contain a `Test-Path` command left at the PowerShell continuation prompt; it should not be presented as a successful check.

## Kali Linux: Agent Installation

The Kali screenshots show a Wazuh agent 4.14.8 Debian package being downloaded using `wget` and installed using `dpkg -i` with `WAZUH_MANAGER` and `WAZUH_AGENT_NAME` environment variables.

- `wget` downloads the package from the Wazuh package server.
- `sudo` runs the installation with elevated privileges.
- `dpkg -i` installs the downloaded Debian package.
- `WAZUH_MANAGER` supplies the manager address.
- `WAZUH_AGENT_NAME` sets the endpoint's registered name.

After installation, the command `sudo systemctl status wazuh-agent` showed the service **active (running)** and enabled. `systemctl status` displays the current systemd service state.

## Final Verification

The Wazuh dashboard showed **three active agents**, zero disconnected, zero pending, and zero never connected. It identified two Windows endpoints and one Kali Linux endpoint, all on Wazuh 4.14.8.

## Evidence to Add

- [ ] Initial DC01-only dashboard screenshot
- [ ] Windows 11 installer errors and MSI event
- [ ] Windows 11 running service confirmation
- [ ] Two-active-agent dashboard screenshot
- [ ] Kali package installation and running service
- [ ] Final three-active-agent dashboard screenshot

Screenshots will be added after filenames are established and any sensitive details are reviewed. Their original errors and intermediate states will be retained.

## Lessons Learned

A downloaded installer is not proof that an agent is installed. Service checks, installer logs, and confirmation in the Wazuh dashboard helped distinguish installation failures from successful endpoint enrollment.
