# SecurityTrainee-Assessment-bWAPP-AccuKnox
Security assessment of **http://www.itsecgames.com** — vulnerability scan, SSL/TLS analysis, and mitigation recommendations (AccuKnox Security Officer Trainee Task)  

**AccuKnox Security Officer Trainee – Problem Statement**  

**Submission By:** *Gundeep Kaur Bindra*  

---

## Executive Summary  
This repository contains a public security posture evaluation of the endpoint **http://www.itsecgames.com**.  
The assessment was performed using publicly available, non-intrusive tools and manual verification. Key findings included insecure communication channels, outdated services, missing security headers, SSL/TLS misconfigurations, and information disclosure.  

No critical vulnerabilities were found, but several **high- and medium-risk issues** require remediation to reduce exposure to common web application and network-level attacks.  

---

## Objectives  
- Identify vulnerabilities on the domain using open-source and free tools.  
- Detect misconfigurations, outdated software, and known CVEs.  
- Assess SSL/TLS configuration and certificate health.  
- Highlight exposed information (headers, banners, error messages).  
- Provide a prioritized list of findings and actionable remediation steps.  

---

## Tools Used  
- **Kali Linux** – testing environment  
- **OpenVAS** – vulnerability scanning  
- **PentestTools Website Scanner (Light)** – web vulnerability & header checks  
- **PentestTools Port Scanner (Light)** – open port & service enumeration  
- **SSL Labs (Qualys)** – SSL/TLS analysis  
- **SecurityHeaders.io** – HTTP header security check  
- **VirusTotal** – URL reputation check  
- **Nmap** – service discovery & version detection  
- **Nikto Web Server Scanner** – common misconfigurations and file checks  
- **MXToolbox / DNS Lookup** – DNS records analysis  
- **WhatWeb / Wappalyzer** – technology fingerprinting  

---

## 📁 Repo Structure  

```
Security-Assessment-itsecgames/
├── README.md
├── assesment.pdf
├── PentestTools-WebsiteScanner-report.pdf
├── PentestTools-PortScanner-report.pdf
└── Screenshots/
    ├── openvas_findings.png
    ├── ssl_labs.png
    ├── headers.png
    ├── nmap_scan.png
    ├── dns_lookup.png
    └── nikto_scan.png
```  

---

## 📑 Quick Findings (Executive)  

| Priority | Finding | Tool / Evidence |  
|----------|---------|-----------------|  
| **High** | HTTP traffic not encrypted (no forced HTTPS) | Website Scanner / SSL Labs |  
| **High** | Outdated **OpenSSH 6.7p1** on port 22 (known CVEs) | Port Scanner / OpenVAS |  
| **Medium** | Missing security headers: CSP, Referrer-Policy, X-Content-Type-Options | SecurityHeaders.io / Website Scanner |  
| **Medium** | SSL/TLS lacks HSTS and supports weak ciphers | SSL Labs |  
| **Medium** | Server banner reveals **Apache HTTP Server** | Headers / Nmap |  
| **Low** | Absence of `security.txt` for vulnerability reporting | Website Scanner |  
| **Low** | HTTP `OPTIONS` method enabled | Website Scanner |  

> Full prioritized list and remediation details are provided in `assesment.pdf` and scanner reports.  

---

## Report Contents  
The attached reports provide detailed findings:  
 
- Screenshots uploaded with reports

---

## Recommended Next Steps

1. **Enforce HTTPS & HSTS** – Redirect all HTTP traffic to HTTPS and implement HSTS.  
2. **Patch & Update** – Upgrade **OpenSSH** and Apache to latest stable versions.  
3. **Harden SSL/TLS** – Disable weak ciphers and enforce modern TLS protocols.  
4. **Implement Security Headers** – Add CSP, Referrer-Policy, X-Content-Type-Options, Strict-Transport-Security.  
5. **Restrict Services** – Disable unused HTTP methods (OPTIONS).  
6. **Improve Reporting** – Add a `/.well-known/security.txt` file for responsible disclosure.  
7. **Reduce Information Leakage** – Suppress Apache and software version banners.  
8. **Continuous Monitoring** – Integrate periodic vulnerability scans and monitoring.  

---

## Note  
This assessment was performed strictly within the scope provided for the assignment.
No exploitative actions were taken. Outputs are provided for educational and assignment purposes only.
