# Incident Response Report: Exchange Server Compromise

## 1. Executive Summary
Our organization's Exchange server was compromised by the Conti ransomware group, leveraging vulnerabilities **CVE-2020-0796, CVE-2018-13374, and CVE-2018-13379**.  
As a result, employees were unable to access **Outlook and Exchange Admin Center**. A ransomware note was left on the compromised server.  
The attack was investigated using **Splunk**, identifying attack vectors, execution methods, and persistence mechanisms.

---

## 2. Incident Overview
- **Incident Type:** Ransomware Attack  
- **Impacted System:** Exchange Server  
- **Affected Services:** Outlook Web Access, Exchange Admin Center  
- **Root Cause:** Exploitation of known vulnerabilities (**CVE-2020-0796, CVE-2018-13374, CVE-2018-13379**)  
- **Detection Tool:** Splunk  

---

## 3. Indicators of Compromise (IOCs)

| Indicator Type            | Indicator Value |
|---------------------------|----------------|
| **Ransomware Path**       | `C:\Users\Administrator\Documents\cmd.exe` |
| **Sysmon Event ID**       | `11` |
| **MD5 Hash**              | `290C7DFB01E50CEA9E19DA81A781AF2C` |
| **Malicious File**        | `readme.txt` |
| **Attacker Added User**   | `securityninja` |
| **Command Used**          | `net user /add securityninja hardToHack123$` |
| **Process Migration**     | `powershell.exe → unsecapp.exe` |
| **Hash Dumping Process**  | `lsass.exe` |
| **Web Shell Deployed**    | `i3gfPctK1c2x.aspx` |
| **Web Shell Command**     | `attrib.exe -r ...\owa\auth\i3gfPctK1c2x.aspx` |
| **Exploited CVEs**        | `CVE-2020-0796, CVE-2018-13374, CVE-2018-13379` |

---

## 4. Attack Timeline
1. **Exploitation** of Exchange server vulnerabilities.
2. **Deployment** of web shell (`i3gfPctK1c2x.aspx`) for remote execution.
3. **Execution** of malicious commands using `cmd.exe`.
4. **Creation** of unauthorized user `"securityninja"` for persistence.
5. **Process migration** to maintain access.
6. **Dumping** of system hashes using `lsass.exe`.
7. **Ransomware execution** and encryption.
8. **Readme.txt ransomware note** placed on the server.

---

## 5. Recommendations
- **🔹 Patch Management:** Apply security patches for `CVE-2020-0796`, `CVE-2018-13374`, and `CVE-2018-13379`.
- **🔹 Access Control:** Disable unnecessary admin accounts and enforce strong password policies.
- **🔹 Endpoint Detection:** Deploy advanced security tools to detect malicious activity.
- **🔹 Network Monitoring:** Implement real-time network traffic analysis.
- **🔹 Backup Strategy:** Maintain regular, encrypted, and offline backups.
- **🔹 Security Awareness:** Train employees on phishing and credential security.
- **🔹 Incident Response Plan:** Develop and test a strong incident response plan.

---

## 6. Conclusion
The Exchange server compromise highlights the importance of **timely patching, network monitoring, and security controls**. By implementing these recommendations, the organization can **reduce risks and improve cybersecurity resilience**.
