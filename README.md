# PortSwigger Web Security Academy

Welcome to my **PortSwigger Web Security Academy Labs**, featuring practical web application security labs, detailed vulnerability analysis, exploitation methodologies, proof-of-concept examples, and remediation guidance.

<div align="center">

# 🛡️ PortSwigger Web Security Academy

### Web Application Security Research & Lab Write-ups

<p align="center">
  <img src="https://img.shields.io/badge/Platform-PortSwigger_Web_Academy-FF6633?style=for-the-badge&logo=burpsuite&logoColor=white">
  <img src="https://img.shields.io/badge/Focus-Web_Application_Security-0078D4?style=for-the-badge&logo=owasp&logoColor=white">
  <img src="https://img.shields.io/badge/Tools-Burp_Suite-FF6633?style=for-the-badge&logo=burpsuite&logoColor=white">
  <img src="https://img.shields.io/badge/Purpose-Security_Learning-2EA44F?style=for-the-badge">
</p>

*Breaking down web vulnerabilities, understanding exploitation techniques, and learning how to secure web applications.*

</div>

---

## 📜 [ 0x01 ] About This Repository

> **Research Log:** Initializing Web Security Lab Notes... 🟢

This repository documents my hands-on journey through **PortSwigger Web Security Academy**. It contains structured lab write-ups, vulnerability analysis, exploitation steps, payload examples, and recommended remediation techniques.

The primary objective is to develop practical skills in web application penetration testing, understand how common and advanced vulnerabilities work, and learn how to identify and prevent security weaknesses.

Each write-up aims to explain the vulnerability in simple, understandable language, making the learning process useful for both technical and non-technical readers.

## 📊 [ 0x02 ] Learning Progress

| Platform                         | Progress         | Lab Experience                  |
| :------------------------------- | :--------------- | :------------------------------ |
| PortSwigger Web Security Academy | **45% Complete** | 76 Practitioner + 4 Expert labs |

*Progress figures reflect my current learning record and will be updated as I complete more labs.*

## 🎯 [ 0x03 ] Core Focus Areas

| Security Domain                   | Learning Focus                                                                                   |
| :-------------------------------- | :----------------------------------------------------------------------------------------------- |
| 💉 **SQL Injection**              | Identifying injection points, exploiting database queries, and understanding defensive controls. |
| 🌐 **Cross-Site Scripting (XSS)** | Reflected, stored, and DOM-based XSS vulnerabilities and prevention techniques.                  |
| 🔐 **Authentication**             | Authentication flaws, password-related weaknesses, and session management.                       |
| 🚪 **Access Control**             | IDOR, privilege escalation, and authorization bypass vulnerabilities.                            |
| 🔄 **CSRF**                       | Cross-site request forgery techniques and effective mitigations.                                 |
| 🌍 **SSRF**                       | Server-side request forgery, request manipulation, and security controls.                        |
| 📁 **File Upload**                | File upload validation weaknesses and secure upload handling.                                    |
| 🧭 **Path Traversal**             | Directory traversal vulnerabilities and file access restrictions.                                |
| ⚙️ **Business Logic**             | Logic flaws, workflow abuse, and application-level weaknesses.                                   |
| 📡 **API Security**               | API testing, authorization issues, and insecure endpoint behavior.                               |
| 📨 **HTTP Request Smuggling**     | HTTP message parsing inconsistencies and their security implications.                            |
| 🧩 **XXE Injection**              | XML external entity vulnerabilities and secure XML parsing.                                      |

## ⚔️ [ 0x04 ] Tools & Arsenal

```bash
root@munna:~# cat web-security-arsenal.txt

[+] Web Security Platform : PortSwigger Web Security Academy
[+] Interception Proxy    : Burp Suite
[+] Browser Analysis      : Browser Developer Tools
[+] HTTP Testing          : Burp Repeater, Burp Intruder, curl
[+] Scripting             : Python, Bash
[+] Documentation         : Markdown, Git, GitHub
[+] Methodology            : Identify -> Analyze -> Test -> Document -> Remediate
```

## 🧪 [ 0x05 ] Lab Write-up Methodology

Each lab write-up follows a structured approach:

1. **Lab Overview** — Lab name, vulnerability category, and difficulty.
2. **Objective** — What the lab requires and what needs to be demonstrated.
3. **Vulnerability Analysis** — Why the vulnerability exists and how it works.
4. **Steps to Reproduce** — Clear, numbered steps to reproduce the issue in the lab.
5. **Payloads and Requests** — Relevant test inputs and HTTP request examples.
6. **Evidence** — Screenshots or relevant request/response excerpts.
7. **Root Cause** — The underlying security weakness.
8. **Remediation** — Recommended fixes and defensive measures.
9. **Key Takeaways** — Important lessons learned from the lab.

## 📂 [ 0x06 ] Repository Structure

```text
PortSwigger-Web-Security-Academy-Labs/
│
├── README.md
│
├── SQL-Injection/
│   ├── README.md
│   └── images/
│
├── Cross-Site-Scripting/
│   ├── README.md
│   └── images/
│
├── Authentication/
│   └── README.md
│
├── Access-Control/
│   └── README.md
│
├── CSRF/
│   └── README.md
│
├── SSRF/
│   └── README.md
│
├── File-Upload/
│   └── README.md
│
├── Path-Traversal/
│   └── README.md
│
├── Business-Logic/
│   └── README.md
│
└── API-Testing/
    └── README.md
```

*The directory structure will expand as additional labs are completed.*

## 📝 [ 0x07 ] Documentation Standards

* Write-ups are organized by vulnerability category.
* Reproduction steps are documented in a clear and repeatable format.
* Screenshots are included where they improve understanding.
* Payloads and technical observations are explained with context.
* Remediation guidance is included wherever applicable.
* Lab solutions and external references are properly distinguished.

## 🛡️ [ 0x08 ] Ethical Use & Disclaimer

This repository is intended for **educational purposes, authorized security testing, and responsible vulnerability research**.

All testing documented here is performed within PortSwigger Web Security Academy labs or other environments where testing is explicitly authorized.

The techniques and payloads must not be used against systems without proper permission. Always follow applicable laws, platform rules, and responsible disclosure practices.

## 📚 [ 0x09 ] Learning Resources

* **PortSwigger Web Security Academy:** https://portswigger.net/web-security
* **Burp Suite Documentation:** https://portswigger.net/burp/documentation
* **OWASP Web Security Testing Guide:** https://owasp.org/www-project-web-security-testing-guide/
* **OWASP Top 10:** https://owasp.org/www-project-top-ten/

---

<div align="center">

### 🚀 Continuous Learning. Practical Testing. Better Security.

*Building hands-on web application security skills, one lab at a time.*

**Maintained by MR-ROOTX**

</div>
