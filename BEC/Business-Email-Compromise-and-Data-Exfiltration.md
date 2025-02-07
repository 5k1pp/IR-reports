# ⚙️ SwiftSpend Phishing Breach: Unauthorized Access and Financial Data Exfiltration 

## 🔥 Incident Summary
On **Friday, September 15, 2023**, Michael Ascot, a **Senior Finance Director** at SwiftSpend, encountered a **phishing email** 📢 impersonating Abotech Waste Management. The email contained a **fraudulent invoice attachment** 📄, which Michael unknowingly downloaded and executed. This resulted in **unauthorized access** ❌ to the SwiftSpend domain, **data exfiltration** 📦, and potential compromise of sensitive financial records.

---

## 🔒 Indicators of Compromise (IoCs)

| **🔍 Indicator**                      | **ℹ️ Description**                                   |
|-------------------------------------|-------------------------------------------------|
| **Invoice_AT_2023-227[.]zip**        | 📡 Malicious ZIP file downloaded from the email.  |
| **Payment_Invoice[.]pdf[.]lnk[.]lnk**    | 🎮 Extracted file containing hidden payload.      |
| **powershell[.]exe**                 | 🛠️ Executed from the malicious attachment.        |
| **https[:]//raw[.]githubusercontent[.]com/besimorhino/powercat/master/powercat[.]ps1** | 💀 Attacker’s reverse shell script. |
| **19282**                          | 🔌 Port used for reverse shell connection.        |
| **systeminfo[.]exe**                 | 🔍 First native Windows binary used for enumeration. |
| **https[:]//raw[.]githubusercontent.com/PowerShellEmpire/PowerTools/master/PowerView/powerview[.]ps1** | 📁 Domain enumeration script. |
| **SSF-FinancialRecords**           | 💼 File share accessed by the attacker.           |
| **C[:]\\Users\\michael.ascot\\downloads\\exfiltration** | 💾 Directory where attacker stored exfiltrated data. |
| **ClientPortfolioSummary[.]xlsx**     | 📑 Sensitive file extracted from the file share. |
| **exfilt8me[.]zip**                   | 🔐 Archive created for data exfiltration.        |
| **T1048**                           | 🌐 MITRE ATT&CK technique used for exfiltration (Exfiltration Over Alternative Protocol). |
| **haz4rdw4re[.]io**                   | 🛡️ Attacker’s server domain for data exfiltration. |

---

## ⏰ Incident Timeline
1. **⌚ September 15, 2023:** Phishing email received and invoice ZIP file downloaded.
2. **📝 ZIP Extracted:** Payment_Invoice.pdf.lnk.lnk executed, spawning PowerShell.
3. **🔧 Reverse Shell Established:** Powercat script downloaded and executed.
4. **📊 System Enumeration:** Attacker ran systeminfo.exe and downloaded PowerView[.]ps1.
5. **📂 File Share Mapped:** SSF-FinancialRecords share accessed and data copied.
6. **📃 Exfiltration Preparation:** ClientPortfolioSummary[.]xlsx archived as exfilt8me[.]zip.
7. **🛠️ Data Exfiltrated:** ZIP file sent via DNS-based exfiltration to haz4rdw4re[.]io.

---

## ⚠️ Recommendations
1. **👨‍👩‍👦 User Awareness Training:** Conduct phishing awareness programs to prevent similar attacks.
2. **🔌 Email Filtering:** Implement advanced email security to detect phishing attempts.
3. **🔦 Endpoint Monitoring:** Deploy endpoint detection & response (EDR) to monitor suspicious activity.
4. **🔒 Network Segmentation:** Limit access to sensitive file shares and apply least privilege principles.
5. **🏢 Incident Response Playbook:** Develop and enforce standardized procedures for incident handling.
6. **🔖 Threat Intelligence Integration:** Utilize threat intelligence feeds to detect known IoCs.

---

## 🔐 Conclusion
This incident highlights the necessity of **cybersecurity awareness** and **technical controls** to mitigate phishing attacks. SwiftSpend must take **immediate action** ⚠️ to enhance **email security**, **endpoint monitoring**, and **user education** to prevent future breaches.

