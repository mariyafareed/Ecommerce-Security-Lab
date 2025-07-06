# Phase 2 – Risk Assessment Matrix

This matrix evaluates and prioritizes the major risks identified in our OpenCart-based e-commerce system.

| Risk Description                      | Likelihood | Impact | Risk Level | Mitigation Strategy |
|--------------------------------------|------------|--------|------------|---------------------|
| SQL Injection via product search box | High       | High   | High       | Input validation and WAF |
| Weak admin password (brute-force)    | High       | High   | High       | Enforce strong passwords, 2FA |
| Apache version outdated              | Medium     | High   | High       | Regular patching |
| Open SSH without firewall            | High       | Medium | High       | Set up UFW or pfSense |
| No encryption in database backups    | Low        | High   | Medium     | Encrypt backups using OpenSSL |
| CSRF on admin forms                  | Medium     | Medium | Medium     | Add CSRF tokens |
| XSS on product review form           | High       | Medium | High       | Sanitize user inputs |
| No antivirus/malware detection       | Low        | Medium | Medium     | Install ClamAV or Wazuh |
| Directory traversal in Apache        | Medium     | High   | High       | Restrict access, use `.htaccess` |
