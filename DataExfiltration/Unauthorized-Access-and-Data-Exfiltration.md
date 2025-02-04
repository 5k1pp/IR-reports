# Slingway Inc. Web Server Compromise: Unauthorized Access and Data Exfiltration Incident

## Incident Summary
On **July 26, 2023**, Slingway Inc., a leading toy company, detected suspicious activity on its e-commerce web server, leading to a SOC investigation. The attacker exploited vulnerabilities in the server’s admin panel, using tools like the **Nmap Scripting Engine** and **Gobuster** for directory enumeration. They accessed the `/admin-login.php` page, successfully brute-forced the admin credentials (`admin:thx1138`), and gained unauthorized access.

Once inside, the attacker uploaded a malicious file and extracted database credentials via **Local File Inclusion (LFI)**. They accessed phpMyAdmin and exported the `customer_credit_cards` database while also inserting additional fraudulent credit card credentials into it. The attacker's **IP address** was identified as `10.0.2.15`, with **1867 failed requests** logged during the attack.

## Indicators of Compromise (IOCs)
| **Indicator** | **Description** |
|-------------|----------------|
| `10.0.2.15` | Attacker's IP Address |
| `Nmap Scripting Engine` | First scanner used against the web server |
| `Mozilla/5.0 (Gobuster)` | User agent of the directory enumeration tool |
| `1867` | Total failed requests |
| `a76637b62ea99acda12f5859313f539a` | Interesting directory discovered |
| `/admin-login.php` | Discovered login page |
| `Mozilla/4.0 (Hydra)` | User agent of the brute-force tool |
| `admin:thx1138` | Credentials used for unauthorized access |
| `THM{ecb012e53a58818cbd17a924769ec447}` | Flag from uploaded file |
| `whoami` | First command executed via web shell |
| `/etc/phpmyadmin/config-db.php` | File location of extracted database credentials |
| `/phpmyadmin` | Directory accessed to manage database |
| `customer_credit_cards` | Exported database name |
| `c6aa3215a7d519eeb40a660f3b76e64c` | Flag inserted into the database |

## Attack Timeline and Analysis
### 1. Initial Scanning:
- **First scanner used**: `Nmap Scripting Engine`
- **User agent of directory enumeration tool**: `Mozilla/5.0 (Gobuster)`
- **Total failed requests**: `1867`
- **Interesting directory discovered**: `a76637b62ea99acda12f5859313f539a`

### 2. Brute-Force Attack and Unauthorized Access:
- **Discovered login page**: `/admin-login.php`
- **User agent of brute-force tool**: `Mozilla/4.0 (Hydra)`
- **Credentials used**: `admin:thx1138`
- **File uploaded containing flag**: `THM{ecb012e53a58818cbd17a924769ec447}`

### 3. Post-Exploitation Activities:
- **First command executed via web shell**: `whoami`
- **Database credentials extracted from**: `/etc/phpmyadmin/config-db.php`
- **Database manager accessed via**: `/phpmyadmin`
- **Exported database name**: `customer_credit_cards`
- **Flag inserted into the database**: `c6aa3215a7d519eeb40a660f3b76e64c`

## Recommendations & Remediation Steps
### 1. Secure Authentication Mechanisms:
- Enforce **strong passwords** and rotate credentials regularly.
- Implement **multi-factor authentication (MFA)** for admin access.
- Limit login attempts to prevent **brute-force attacks**.

### 2. Enhance Web Server Security:
- Regularly **update and patch** software to address vulnerabilities.
- Restrict access to **sensitive directories** and enforce **least privilege principles**.
- Monitor and log all **administrative activities** for anomaly detection.

### 3. Strengthen Network and File Security:
- Restrict **file upload permissions** and validate input to prevent malicious scripts.
- Implement **Web Application Firewalls (WAF)** to detect and block threats in real time.
- Encrypt **sensitive data at rest and in transit** to prevent unauthorized access.

### 4. Incident Response & Notification:
- **Notify affected customers** about the data breach and provide necessary support.
- Conduct a **full forensic investigation** to determine the extent of data compromise.
- Establish a **dedicated incident response team** to improve future detection and response capabilities.

## Conclusion
This incident highlights the vulnerabilities in **Slingway Inc.'s** web server that were exploited by the attacker to gain **unauthorized access**, **exfiltrate customer data**, and **compromise the system**. By implementing the recommended security measures, **Slingway Inc.** can **mitigate the damage** from this breach and prevent future attacks of a similar nature.

Your investigation's comprehensive findings and actionable insights will enable **Slingway Inc.** to bolster its **cybersecurity posture**, safeguard its customers' trust, and enhance overall **data protection strategies**. **Well done!**
