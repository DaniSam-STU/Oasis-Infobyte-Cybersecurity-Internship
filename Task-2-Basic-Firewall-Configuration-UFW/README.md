# Task 2: Basic Firewall Configuration using UFW

## 📌 Objective
The objective of this task is to configure a basic firewall using **UFW (Uncomplicated Firewall)** to control incoming and outgoing network traffic and understand firewall rules in a Linux environment.

---

## 🛠️ Tools Used
- **UFW (Uncomplicated Firewall)**
- **Kali Linux**
- Terminal (Bash)

---

## 🔧 Firewall Installation

UFW was installed using the following command:

```bash
sudo apt install ufw -y
```
## Enabling the Firewall

The firewall was enabled to start enforcing rules:
```bash
sudo ufw enable
```
## Default policies applied:

Deny all incoming connections

Allow all outgoing connections

## 🔐 Configuring Firewall Rules
Allow SSH (Port 22)
-
To maintain remote access, SSH traffic was allowed:
```bash
sudo ufw allow ssh
```
 Deny HTTP (Port 80)
-
HTTP traffic was blocked to demonstrate firewall filtering:
```bash
sudo ufw deny http
```
## 📊 Firewall Status Verification

Firewall status and rules were verified using:
```bash
sudo ufw status verbose
```

This confirmed:
-
Firewall is active

- SSH allowed

- HTTP denied

Default policies enforced

## 📷 Screenshots

All relevant screenshots showing firewall installation, rule configuration, and status verification are included in the screenshots directory.

## ✅ Conclusion

This task provided practical experience in:

- Installing and enabling a firewall

- Creating allow and deny rules

- Verifying firewall configurations

- Understanding basic network security controls

**Firewall configuration is a critical first step in securing Linux systems against unauthorized access.**
