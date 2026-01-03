# Web Application Vulnerabilities
## Vulnerability Scanning, SQL Injection & Cross-Site Scripting (XSS)

## Objective
The objective of this lab was to understand and practically demonstrate common web application vulnerabilities by reproducing the following attacks in a controlled lab environment:
- Vulnerability scanning using Nikto</li>
- SQL Injection using DVWA</li>
- Cross-Site Scripting (XSS) (Reflected and Stored)</li>
The lab simulates real-world web application weaknesses and demonstrates how attackers exploit them, as well as how increasing security controls mitigates these vulnerabilities.

## Tools Used
- Kali Linux
- Nikto Web Vulnerability Scanner
- DVWA (Damn Vulnerable Web Application)
- Nano text editor
- Web browser (Firefox)
- Apache/MySQL (via DVWA environment)

## Lab 1: Vulnerability Scanning with Nikto
### Purpose
Nikto is an open-source web server scanner used to identify:
- Misconfigurations
- Outdated software
- Dangerous files
- Security headers issues

### Step 1: Basic Nikto Scan
nikto -h scanme.nmap.org
### Observation:
- Detected missing HTTP security headers
- Identified server information disclosure
- Highlighted potential misconfigurations

### Step 2: SSL Website Scan
nikto -h https://nmap.org -ssl
### Observation:
- Verified SSL configuration
- Checked HTTPS-related security headers
- Identified potential cipher and protocol issues

### Step 3: Scanning Multiple URLs from a File
Create a file containing URLs/IPs:
- nano urlscan.txt
Example content:
- scanme.nmap.org
- nmap.org
- 172.17.0.2
- Run Nikto against the file:
- nikto -h urlscan.txt
### Observation:
- Nikto sequentially scanned all listed targets
- Useful for batch scanning in enterprise environments

### Step 4: Save Scan Output to HTML
- nikto -h 172.17.0.2 -o scanresult.html
### Observation:
- Generated a readable HTML report
- Useful for documentation and client reporting

### Key Findings
- Missing security headers
- Information disclosure through server banners
- Potentially dangerous files accessible

### Lab 2: SQL Injection Using DVWA
#### Purpose
SQL Injection occurs when user input is improperly sanitized and directly embedded into SQL queries.

#### Environment Setup
- DVWA Security Level set to Low
- SQL Injection module selected

#### SQL Injection Example
Input:
' OR '1'='1
Result:
- Bypassed authentication
- Returned all database records

#### Increasing Security Levels
- Medium: Basic filtering implemented
- High: Prepared statements and stricter validation
- Impossible: Fully secured with parameterized queries

### Observation:
As security increased, exploitation became impossible, demonstrating best practices for secure database handling.

### Lab 3: Cross-Site Scripting (XSS)
#### XSS (Reflected)
#### Payloads Used
- <ScRipt>alert("You are hacked")</ScRipt>
- <img src=x onerror=alert("Your_are_hacked")>

### Security Level Testing
- Low: Payload executed successfully
- Medium: Some filtering applied, bypass possible
- High: Strong filtering, exploitation difficult
- Impossible: Input validation and output encoding prevented attack

### XSS (Stored)
Stored XSS injects malicious code that is saved in the database and executed whenever the page loads.
### Observation:
- Payload persisted across sessions
- Affects all users viewing the page
- More dangerous than reflected XSS

### Findings and Observations
- Vulnerability scanners are effective for reconnaissance but do not replace manual testing
- SQL Injection can lead to full database compromise
- XSS attacks can steal cookies, session tokens, and user credentials
- Increasing security levels demonstrates the importance of secure coding practices
- DVWA effectively simulates real-world web application vulnerabilities

### Screenshots
- Nikto scan results <img src="https://github.com/Jaybest01/Web-Application-Vulnerabilities/blob/main/images/nikto%20scan%20result.jpg" alt="Nikto scan results" width="1000" height="1200"> <img src="https://github.com/Jaybest01/Web-Application-Vulnerabilities/blob/main/images/nikto%20scan%20result2.jpg" alt="Nikto scan results" width="1000" height="1200"> <img src="https://github.com/Jaybest01/Web-Application-Vulnerabilities/blob/main/images/nikto%20scan%20result3.jpg" alt="Nikto scan results" width="1000" height="1200">
- DVWA SQL Injection exploitation <img src="https://github.com/Jaybest01/Web-Application-Vulnerabilities/blob/main/images/dvwa-xss.jpg" alt="DVWA SQL Injection exploitation" width="1000" height="1200"> <img src="https://github.com/Jaybest01/Web-Application-Vulnerabilities/blob/main/images/dvwa-xss1.jpg" alt="DVWA SQL Injection exploitation" width="1000" height="1200">
- Reflected and Stored XSS alerts <img src="https://github.com/Jaybest01/Web-Application-Vulnerabilities/blob/main/images/hashcat.jpg" alt="Reflected and Stored XSS alerts" width="1000" height="1200"> <img src="https://github.com/Jaybest01/Web-Application-Vulnerabilities/blob/main/images/hashcat1.jpg" alt="Reflected and Stored XSS alerts" width="1000" height="1200"> <img src="https://github.com/Jaybest01/Web-Application-Vulnerabilities/blob/main/images/hashcat2.jpg" alt="Reflected and Stored XSS alerts" width="1000" height="1200"> <img src="https://github.com/Jaybest01/Web-Application-Vulnerabilities/blob/main/images/hashcat3.jpg" alt="Reflected and Stored XSS alerts" width="1000" height="1200"> <img src="https://github.com/Jaybest01/Web-Application-Vulnerabilities/blob/main/images/hashcat4.jpg" alt="Reflected and Stored XSS alerts" width="1000" height="1200">

### Why These Vulnerabilities Matter
In real-world applications:
- SQL Injection can result in data breaches and financial loss
- XSS attacks can hijack user sessions and compromise trust
- Misconfigured servers expose sensitive information to attackers
Testing these vulnerabilities helps security professionals advise clients on secure coding practices and risk mitigation strategies.

### Conclusion
This lab reinforced the importance of web application security testing and demonstrated how attackers exploit weaknesses when security controls are lacking. The DVWA security levels effectively mirror real-world application maturity and highlight why secure development practices are critical.
