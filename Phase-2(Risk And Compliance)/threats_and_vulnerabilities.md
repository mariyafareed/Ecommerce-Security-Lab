# Phase 2 – Threats and Vulnerabilities

In this document, I’ve listed the major cybersecurity threats that can affect my e-commerce setup (OpenCart hosted on Apache, using MySQL on Ubuntu), along with the vulnerabilities that can be exploited, the affected asset, and the overall risk level.

---

## 🔐 Web Server (Apache2)

| Threat                | Vulnerability                      | Affected Asset | Description                                                  | Risk Level |
|-----------------------|------------------------------------|----------------|--------------------------------------------------------------|------------|
| DoS Attack            | No rate limiting or firewall       | Apache2        | Too many requests can crash the server                       | Medium     |
| Directory Traversal   | Misconfigured file permissions     | Apache2        | Attacker can read sensitive files from server                | High       |
| Version Exploits      | Outdated Apache installation       | Apache2        | Attackers can exploit known bugs in unpatched versions       | High       |

---

## 🗃️ Database Server (MySQL)

| Threat                | Vulnerability                     | Affected Asset | Description                                                  | Risk Level |
|-----------------------|-----------------------------------|----------------|--------------------------------------------------------------|------------|
| SQL Injection         | Lack of input validation          | MySQL          | Attacker can execute harmful queries via form inputs         | High       |
| Data Leakage          | No encryption or DB backups       | MySQL          | Data may be stolen or viewed in plaintext                    | High       |
| Privilege Escalation  | Over-permissive DB user roles     | MySQL          | Limited users can gain full access to sensitive data         | Medium     |

---

## 🧾 OpenCart Application

| Threat                | Vulnerability                     | Affected Asset | Description                                                  | Risk Level |
|-----------------------|-----------------------------------|----------------|--------------------------------------------------------------|------------|
| Cross-Site Scripting  | User input not sanitized          | OpenCart Pages | JavaScript code can be injected into pages                   | High       |
| Weak Authentication   | Default or weak admin passwords   | Admin Panel    | Easy to brute-force or guess admin access                    | High       |
| CSRF                  | No CSRF tokens on forms           | Admin Panel    | Malicious requests can be sent from another site             | Medium     |

---

## 🖥️ Host Operating System (Ubuntu VM)

| Threat                | Vulnerability                    | Affected Asset | Description                                                   | Risk Level |
|-----------------------|----------------------------------|----------------|---------------------------------------------------------------|------------|
| Unauthorized Access   | SSH open without firewall        | Ubuntu OS      | SSH login exposed to public network                           | High       |
| Privilege Escalation  | Sudo access misconfigured        | Ubuntu OS      | Attacker can gain root access                                | High       |
| Malware Installation  | No antivirus or monitoring tools | Ubuntu OS      | System may be infected and used for botnet or crypto mining   | Medium     |

---

## 💡 Notes

- This threat modeling is based on a default installation of OpenCart on Apache, MySQL, and Ubuntu.
- Most of the vulnerabilities are preventable through basic security practices such as:
  - Keeping software updated
  - Enabling firewalls (like UFW or pfSense in Phase 4)
  - Enforcing strong passwords
  - Validating user input

