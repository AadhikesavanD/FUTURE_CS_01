# Web Application Security Testing – Internship Task

This repository contains the documentation and findings from a penetration testing task performed as part of a cybersecurity internship at **Future Intern**. The objective was to identify and analyze critical security vulnerabilities in a deliberately insecure web application (DVWA).

## 📌 Task Overview

- **Intern Name**: Aadhikesavan D  
- **Internship Role**: Cybersecurity Intern  
- **Reporting Date**: April 15, 2025  
- **Task ID**: TASK 1  
- **Task Title**: Web Application Security Testing  

## 🎯 Objective

Conduct penetration testing on a sample vulnerable web application to detect:

- SQL Injection (SQLi)
- Cross-Site Scripting (XSS)
- Authentication Bypass

## 🛠️ Tools Used

- [OWASP ZAP](https://www.zaproxy.org/) – Automated vulnerability scanning
- [Burp Suite](https://portswigger.net/burp) – Manual testing and request interception
- [SQLMap](https://sqlmap.org/) – Automated SQL injection exploitation
- [Hydra](https://github.com/vanhauser-thc/thc-hydra) (optional) – Brute force testing

## 🧪 Test Environment

| Component         | Details                     |
|------------------|-----------------------------|
| Attacker Machine | Kali Linux (VirtualBox)     |
| Target Machine   | Metasploitable 2 (VirtualBox) |
| Web App          | DVWA (Damn Vulnerable Web App) |
| Network Setup    | Host-only adapter (same subnet) |

## 🔍 Vulnerability Testing Summary

### ✅ SQL Injection
- **Target**: `DVWA → SQL Injection` module  
- **Tool**: SQLMap  
- **Outcome**: Database names extracted (`dvwa`, `information_schema`)  
- **Severity**: High  
- **Mitigation**:
  - Use prepared statements
  - Input validation
  - Avoid SQL string concatenation

### ✅ Cross-Site Scripting (XSS)
- **Target**: `DVWA → XSS (Reflected)` module  
- **Tool**: OWASP ZAP  
- **Outcome**: Reflected XSS in `name` parameter with payload `<script>alert(1)</script>`  
- **Severity**: Medium to High  
- **Mitigation**:
  - Sanitize and encode user inputs
  - Implement Content Security Policy (CSP)

### ✅ Authentication Bypass
- **Target**: DVWA login page  
- **Tools**: Manual, Burp Suite, Hydra  
- **Outcome**: Login bypass using `' OR '1'='1`  
- **Severity**: High  
- **Mitigation**:
  - Input validation and proper session handling
  - CAPTCHA implementation
  - Account lockout mechanisms
  - Enforcing strong password policies

## 📎 Sample Reports

| Tool        | Format | Filename                     |
|-------------|--------|------------------------------|
| ZAP         | HTML   | `DVWA_ZAP_XSS_Report.html`   |
| SQLMap      | Text   | `SQLMap_DB_Extraction.txt`   |
| Burp Suite  | Text   | `Burp_SQL_Bypass_Logs.txt`   |

## 📸 Screenshots Included

- SQLMap database extraction
- ZAP XSS alerts
- Burp Suite login bypass request
- DVWA interface and results

## ✅ Conclusion

This task offered practical experience in:

- Identifying and exploiting common web app vulnerabilities
- Using industry-standard tools for offensive security
- Documenting findings and proposing secure development practices

---

## 🙏 Acknowledgment

Thanks to **Future Intern** for the opportunity to gain hands-on experience in penetration testing and for providing a real-world simulation environment.

