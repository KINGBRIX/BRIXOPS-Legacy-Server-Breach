
# Legacy Server Breach — Incident Response Capstone

**Group cybersecurity capstone | August 2026 | Simulated environment**

> **Portfolio edition.** This repository summarizes an educational group project. It is not a report of a real breach at a real company. The original class report was labeled **Confidential / Internal Use Only** and is intentionally **not included** here. Publish only material approved for public sharing.

## Project overview

A simulated Network Operations Center (NOC) reported unusual network traffic from an unpatched Ubuntu legacy server supporting an older application. The team investigated exposed services, mapped potential vulnerabilities to public CVEs, assessed an **attack-path hypothesis**, and documented containment and remediation controls for a system that could not be patched normally.

**Scenario severity:** High (as assigned in the group report)  
**Environment:** Isolated VirtualBox lab with Kali Linux and a legacy Ubuntu target  
**Focus:** Incident response, network analysis, vulnerability research, Linux administration, and evidence validation

## My role and team collaboration

I contributed as a **Systems/Network Administrator** and **Digital Forensics** team member alongside other group members. Our assigned responsibilities included providing access and log sources, supporting host containment and evidence collection, and validating AI-assisted observations against manual tool output. The team shared responsibility for the investigation and final report.

**Attribution note:** This was a **group** capstone. Team-level results are described as team work; this portfolio summary does not claim that I independently performed every scan, containment step, or finding. Exact individual command outputs and screenshots can be added later where verified.

## Investigation workflow

1. **Prepare:** Create an isolated VirtualBox network containing Kali Linux and a vulnerable legacy Ubuntu host; verify connectivity before testing.
2. **Detect and analyze:** Review the simulated traffic anomaly; enumerate ports and service versions using Nmap; review relevant traffic using Wireshark and Linux tools.
3. **Research:** Cross-reference exposed service versions with CVE records and MITRE/NVD resources; manually validate AI-suggested findings rather than treating them as evidence.
4. **Contain:** Document host-based filtering and process/service restriction for high-risk legacy services, with attention to preserving business application availability.
5. **Eradicate and recover:** Recommend removing vulnerable services, restricting network exposure, verifying functionality, and rescanning after changes.
6. **Report:** Produce a vulnerability matrix, attack-path hypothesis, prevention recommendations, and lessons learned.

## Selected findings from the group report

| Observed service/version in report | Port(s) | Associated CVE / concern | Response proposed or documented |
|---|---|---|---|
| vsftpd 2.3.4 | 21/TCP | CVE-2011-2523 — backdoored distribution / RCE | Filter FTP; replace with secure SFTP/SSH |
| Samba 3.0.20 | 139, 445/TCP | CVE-2007-2447 — username map script command injection | Restrict SMB; disable vulnerable configuration; upgrade/replace |
| UnrealIRCd 3.2.8.1 | 6667/TCP | CVE-2010-2075 — backdoored software | Remove service / terminate unauthorized process |
| Telnet | 23/TCP | Cleartext protocol risk | Disable and require secure remote administration |
| ProFTPD | 2121/TCP | Legacy FTP exposure | Decommission if not needed |

**Interpretation:** The report associates exposed software with known vulnerabilities; that does **not** establish that any specific CVE was exploited during the simulated incident. The exact initial access method was presented as a hypothesis, not a confirmed root cause.

## Attack-path hypothesis (not confirmed)

The group report considered **MITRE ATT&CK T1190 (Exploit Public-Facing Application)** for initial access through vulnerable legacy services and **T1071 (Application Layer Protocol)** for possible command-and-control via a backdoored IRC service. These were research-driven hypotheses, not a demonstrated full attacker timeline.

## Tools and techniques

- **Nmap:** Host/service enumeration and vulnerability-oriented scan output (`nmap -sV --script=vuln` appears in the report)
- **Wireshark:** Packet inspection and anomaly investigation workflow
- **Linux CLI:** Host inspection, connectivity, process and service checks
- **NVD / MITRE CVE:** Cross-checking CVE identifiers, versions, and exploitability
- **iptables:** Host-based containment documented by the group
- **MITRE ATT&CK:** Mapping potential attacker behaviors

## What I learned

- A legacy host can remain high risk even when it cannot be patched; compensating controls such as segmentation, firewall restrictions, service removal, and monitoring are essential.
- A CVSS score alone does not capture the full operational risk of a vulnerable, exposed service.
- AI-generated threat intelligence is a **lead**, not proof: verify against primary sources and actual host/network evidence.
- A professional incident report must separate **observations**, **hypotheses**, **actions taken**, and **recommended future work**.
- Group incident response requires coordination across technical investigation, systems administration, forensics, and reporting.

## Evidence and publication notes

The original 11-page group report included screenshots of the VirtualBox lab, connectivity tests, Nmap/terminal output, and supporting evidence. Those screenshots are **not redistributed here** pending review for publication permission, attribution, and sensitive details. See [`evidence/README.md`](evidence/README.md) for a checklist.

### Limitations and verification needed

- The scenario began with a suspected unauthorized-access event, but the initial access vector was **not conclusively identified** in the report.
- Some sections describe remediation as completed while others present steps as recommendations. This public summary avoids asserting independently verified remediation or a final clean rescan without matching evidence.
- The original report does not distinguish each teammate's individual command execution in all sections. Personal contributions should be clarified before expanding resume claims.

## Related project

My separate **BRIXOPS Enterprise Security Lab** focuses on deploying enterprise-style infrastructure, Active Directory, Windows auditing, and Wazuh SIEM telemetry. This capstone demonstrates the incident-response and vulnerability-analysis side of my cybersecurity training.

---

*Prepared as a public-facing summary of a collaborative educational capstone. Original group report and materials remain separate.*
$90K
