# 🛡️ Linux Operating System Hardening & Security Configuration Lab

## 📌 Executive Summary
This project demonstrates practical **Operating System (OS) Hardening** techniques applied to a **Kali Linux Rolling (v2026.2)** environment running kernel `5.19.14+kali-amd64`. The primary goal of this project is to reduce system vulnerability surfaces by enforcing strict firewall access controls, disabling non-essential services, implementing principle of least privilege user management, and verifying file data integrity.

---

## 🛠️ Hardening Implementations

### 1. System Information & Environment Baseline
- Audited release specs (`/etc/os-release`) and running Linux kernel details (`uname -r`).
- Audited the `/home` directory structure to establish baseline local user privileges.

### 2. Service & Process Auditing
- Monitored active system units with `systemctl list-units --type=service --state=running`.
- Audited legacy and unnecessary services (such as `cups.service` print daemon) to prevent unneeded background process exposure.

### 3. Open Port & Sockets Verification
- Identified local listening ports using `ss -tuln`.
- Verified that sensitive daemon ports are bound exclusively to local interface sockets (`127.0.0.1`) where appropriate.

### 4. Firewall Engineering (UFW)
- Enabled Uncomplicated Firewall (`ufw enable`).
- Set standard security policies: **Default Deny Incoming**, **Default Allow Outgoing**.
- Created specific drop rules targeting potentially untrusted host IPs (e.g., `203.0.133.10`).
- Configured explicit port rules for standard communication protocols (`80`, `22/tcp`, `53`, `443`).

### 5. Identity & Access Management (IAM)
- Provisioned new non-root, restricted user accounts (`kosi`) using `sudo adduser` to adhere to the Principle of Least Privilege (PoLP).

### 6. File Integrity Baselines
- Generated SHA-256 cryptographic hashes (`sha256sum`) on system files to create cryptographic baselines for detecting unauthorized tampering.

---

## 📂 Additional Documentation
- [Detailed Command Walkthrough](LAB_GUIDE.md)
- [OS Hardening Verification Log](VERIFICATION.md)
