# 03 - Security Investigation: Windows Event ID 4625

## Objective

Investigate a Windows failed-logon event collected from DC01 in Wazuh 4.14.8 and document only conclusions supported by the available evidence.

## Evidence

### Wazuh alert overview

![Wazuh alerts on DC01, including failed logon](../screenshots/Screenshot%202026-10-17%20121856.png)

The Wazuh alert search returned **372 hits** during a one-hour window on October 17, 2026 (11:18:01.904–12:18:01.904). The visible results include successful logons, logoffs, privilege assignments, and a **Logon Failure - Unknown user or bad password** alert. **372 hits is the total number of matching events, not a count of failed logons.**

The visible failed-logon alert is associated with **DC01**, Wazuh **rule ID 60122**, and **rule level 5**.

### Windows event details

![Windows Security Event 4625 fields](../screenshots/Screenshot%202026-10-17%20132318.png)

| Field | Observed value |
| --- | --- |
| Computer | DC01.bunbun.local |
| Windows channel | Security |
| Windows Event ID | 4625 |
| Target username | Administrator |
| Target domain | BUNBUN |
| Workstation name | DC01 |
| Status | `0xC000006D` |
| Substatus | `0xC000006A` |
| Event record ID | 1872974 |
| Subject username | DC01$ |
| Subject SID | S-1-5-18 |

**Interpretation:** Windows status `0xC000006D` indicates a failed logon; substatus `0xC000006A` indicates an incorrect password. The event therefore records an unsuccessful authentication attempt targeting the Administrator account.

The screenshots do **not** establish the source IP address, exact number of failed attempts, logon type, or whether the activity was intentional. The Wazuh alert listing and event detail screenshots are treated as related investigation evidence, but their exact record-level correspondence has not been independently verified.

## Triage Assessment

**Observed:** A Windows Security failed-logon event involving the Administrator account, with a bad-password substatus, and a Wazuh failed-logon alert visible on DC01.

**Confirmed test context:** The lab operator intentionally entered an incorrect Administrator password to generate failed-logon telemetry. This was an authorized simulation, not an unexpected attack.

**Not yet established:** The exact number of attempts, a brute-force pattern, or any account compromise.

**Final classification:** **Authorized failed-login simulation (true-positive detection of deliberately generated failed authentication).** Wazuh displayed the relevant failed-logon alert, and Windows recorded Event ID 4625 with incorrect-password substatus. This is not evidence of an actual hostile intrusion.

## Recommended Next Checks

- [ ] Filter Wazuh results specifically for Windows Event ID 4625 and count matching events.
- [ ] Review timestamps to determine whether failures are clustered.
- [ ] Inspect source network address and logon type if present in the full event.
- [ ] Compare with nearby successful logons (Event ID 4624).
- [x] Confirm with the lab operator that incorrect Administrator passwords were deliberately entered to generate alerts.
- [ ] Record a final disposition after reviewing those fields.

## Outcome

The exercise demonstrated that intentionally generated Windows failed-login activity was visible in Wazuh. It does not establish brute-force detection or incident response to a real attacker. Further analysis of event counts and source fields would make the simulation more complete.

## Lessons Learned

A large number of search hits does not mean the same number of security incidents. A SOC analyst should separate the detection, the underlying Windows event, and any inference about malicious behavior. This case demonstrates how status and substatus codes help explain a failed authentication without overstating what the evidence proves.
