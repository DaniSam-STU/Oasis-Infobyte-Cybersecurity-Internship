# Task 3: SQL Injection on DVWA (Low Security)

## Overview
Demonstration of SQL Injection vulnerability in Damn Vulnerable Web Application (DVWA) with security level set to LOW.

## Environment Setup
- **OS**: Kali Linux 2024.3
- **DVWA**: Version 1.0.1 (Docker container)
- **Security Level**: Low
- **Database**: MySQL

## Steps Performed

### 1. DVWA Setup & Configuration
- Launched DVWA via Docker container
- Accessed web interface at http://localhost:8080
- Set security level to LOW via DVWA Security page

### 2. SQL Injection Tests

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
