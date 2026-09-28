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
<img width="930" height="420" alt="Screenshot 2026-09-26 201127" src="https://github.com/user-attachments/assets/7c158c2d-abff-4bc7-891e-f1fae2f499d7" />
<img width="933" height="277" alt="Screenshot 2026-09-26 200612" src="https://github.com/user-attachments/assets/e35484fb-de92-4155-a8fe-fe8f71c76501" />
<img width="935" height="842" alt="Screenshot 2026-09-26 200348" src="https://github.com/user-attachments/assets/64119440-70c2-417f-b0d7-3ce5a4eb0f09" />
<img width="924" height="812" alt="Screenshot 2026-09-26 200327" src="https://github.com/user-attachments/assets/ac5e153b-43b2-416c-8284-2f4dee2397fe" />
<img width="931" height="796" alt="Screenshot 2026-09-26 200312" src="https://github.com/user-attachments/assets/40d7ab55-d458-4562-95a3-0893cef7c325" />
<img width="921" height="752" alt="Screenshot 2026-09-26 200221" src="https://github.com/user-attachments/assets/c28b5262-0d24-4c7d-9e72-bbf99dab9efd" />
<img width="928" height="451" alt="Screenshot 2026-09-26 195940" src="https://github.com/user-attachments/assets/d4758ac7-6874-4f56-9acc-0d55e1e2c971" />
<img width="923" height="456" alt="Screenshot 2026-09-26 195841" src="https://github.com/user-attachments/assets/a4c5980d-ddcc-4914-ac21-1ceba2698375" />
<img width="929" height="237" alt="Screenshot 2026-09-26 193233" src="https://github.com/user-attachments/assets/5dc72b80-acd0-4e5f-b036-eebbcab63355" />
<img width="928" height="570" alt="Screenshot 2026-09-26 192624" src="https://github.com/user-attachments/assets/b65b179f-f488-438b-b2c4-451b245a0e7b" />
<img width="936" height="710" alt="Screenshot 2026-09-26 192353" src="https://github.com/user-attachments/assets/e3301a95-0e6a-4ac6-bc00-4cae7d71f930" />
<img width="923" height="430" alt="Screenshot 2026-09-26 191936" src="https://github.com/user-attachments/assets/65d43f3e-6740-42cd-863c-870c45291b22" />
<img width="927" height="85" alt="Screenshot 2026-09-26 191807" src="https://github.com/user-attachments/assets/4cf4372e-9966-44f9-bb6a-f76642137dba" />
<img width="927" height="492" alt="Screenshot 2026-09-26 191707" src="https://github.com/user-attachments/assets/0c4a86b7-5f49-4a33-a963-b2357472d8a3" />
<img width="924" height="272" alt="Screenshot 2026-09-26 191501" src="https://github.com/user-attachments/assets/f62dd544-74fb-4f13-97fe-f89cb5cc705e" />
<img width="921" height="597" alt="Screenshot 2026-09-26 190321" src="https://github.com/user-attachments/assets/f2433594-70e5-4e5b-9cfe-01777560e51a" />
