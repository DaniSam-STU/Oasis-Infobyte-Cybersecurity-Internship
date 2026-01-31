# Task 3: SQL Injection on DVWA (Low Security)

## Overview
Demonstration of SQL Injection vulnerability in Damn Vulnerable Web Application (DVWA) with security level set to LOW.

## 📋 Prerequisites
- **Operating System**: Windows 10/11
- **Software**: XAMPP (Apache + MySQL + PHP)
- **Browser**: Chrome/Firefox/Edge
- **Internet Connection**: For downloading DVWA

## 🚀 Quick Start Guide

### Step 1: Install XAMPP
1. Download XAMPP from: https://www.apachefriends.org/download.html
2. Run the installer with default settings
3. Launch **XAMPP Control Panel**

### Step 2: Start Required Services
In XAMPP Control Panel:
- Click **Start** for **Apache**
- Click **Start** for **MySQL**
- Both should turn **GREEN**

### Step 3: Install DVWA
```powershell
# Download DVWA manually:
# 1. Go to: https://github.com/digininja/DVWA/archive/master.zip
# 2. Extract to: C:\xampp\htdocs\dvwa
```
### Step 4: Configure DVWA
- Navigate to: **C:\xampp\htdocs\dvwa\config**
- Copy *config.inc.php.dist* to **config.inc.php**
- Edit *config.inc.php* with these settings:

```php
$_DVWA[ 'db_user' ] = 'root';
$_DVWA[ 'db_password' ] = '';  # Leave empty for XAMPP default
$_DVWA[ 'db_server' ] = '127.0.0.1';
$_DVWA[ 'db_database' ] = 'dvwa';
```
### Step 5: Access DVWA
- Open browser
- Go to: http://localhost/dvwa/
- Click "Create / Reset Database"
- Login with:
```
Username: admin
Password: password
```
### Step 6: Set Security Level to LOW
- After login, click "DVWA Security" in left sidebar
- Select "Low" from dropdown
- Click "Submit"

## SQL Injection Demonstration

#### Test 1: Vulnerability Detection
- **Payload**: `'`
- **Result**: SQL syntax error confirming injection vulnerability
- **Significance**: Single quote breaks SQL query, revealing improper input handling

#### Test 2: Basic SQL Injection
- **Payload**: `' OR '1'='1`
- **Result**: Retrieved ALL user records from database
- **Impact**: Bypasses authentication logic, exposes sensitive data

#### Test 3: Database Information Extraction
- **Payload**: `' UNION SELECT null, version() #`
- **Result**: MySQL version: [Your MySQL Version Here]
- **Significance**: Attackers can gather system information for targeted exploits

#### Test 4: Credential Extraction
- **Payload**: `' UNION SELECT user, password FROM users #`
- **Result**: Retrieved usernames and MD5-hashed passwords
- **Critical Impact**: Complete compromise of user authentication system

## Screenshots
1. **DVWA Setup Page** - Initial configuration
2. **Login Page** - Accessing DVWA interface
3. **Security Level LOW** - Setting vulnerability level
4. **SQL Injection Page** - Target interface
5. **Single Quote Test** - SQL error confirmation
6. **Basic Injection** - All user records exposed
7. **Database Version** - System information leak
8. **User Credentials** - Password hash extraction

## Vulnerability Analysis
- **Root Cause**: Lack of input validation and parameterized queries
- **CVSS Score**: 8.5 (High)
- **Impact**: Confidentiality (High), Integrity (High), Availability (Medium)

## Mitigation Strategies
1. **Use Prepared Statements**: Implement parameterized queries
2. **Input Validation**: Validate and sanitize all user inputs
3. **Least Privilege**: Restrict database user permissions
4. **Web Application Firewall**: Deploy WAF with SQL injection rules
5. **Regular Security Testing**: Conduct penetration testing and code reviews

## Ethical Considerations
- This demonstration was performed on a locally hosted DVWA instance
- DVWA is intentionally vulnerable for educational purposes
- All activities were conducted in an isolated lab environment

## References
- OWASP SQL Injection Prevention Cheat Sheet
- DVWA Official Documentation
- MySQL Security Best Practices
