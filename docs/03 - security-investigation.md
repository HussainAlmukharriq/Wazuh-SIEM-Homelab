# 03 - Security Investigation: Windows Event ID 4625

## Objective

Practice an entry-level SOC investigation by reviewing Windows failed-logon activity collected through Wazuh.

## Lab Context

- **SIEM:** Wazuh 4.14.8
- **Monitored endpoints:** DC01, WIN11, and Kali
- **Relevant Windows event:** Security Event ID 4625 (failed account logon)
- **Environment:** Isolated cybersecurity homelab

## What Event ID 4625 Means

Windows records Event ID 4625 when an account logon fails. A failed logon is not, by itself, proof of an attack. The surrounding context—such as the account, source, logon type, failure reason, and frequency—helps determine whether it warrants investigation.

## Evidence Captured

The following screenshots were uploaded during the investigation. Their precise contents and conclusions still need to be reviewed before assigning more specific captions.

![Investigation evidence screenshot 1](../screenshots/Screenshot%202026-10-17%20121856.png)

![Investigation evidence screenshot 2](../screenshots/Screenshot%202026-10-17%20132318.png)

## Investigation Checklist

- [ ] Identify the affected host and account
- [ ] Record the event timestamp and logon type
- [ ] Identify the source network address, if recorded
- [ ] Review failure status and substatus codes
- [ ] Check whether failures repeat or cluster in time
- [ ] Compare with related successful logons, if available
- [ ] Decide whether the evidence suggests a user error, configuration problem, or suspicious activity
- [ ] Record findings and any recommended next steps

## Findings

**Pending evidence review.** No source IP, account, event count, attacker attribution, or root cause is claimed without supporting event data.

## Lessons Learned

A SOC investigation should distinguish an observed alert from a confirmed security incident. Screenshots, event fields, and a documented reasoning process make the investigation reproducible and defensible.
