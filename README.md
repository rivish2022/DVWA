🛡️ DVWA SQL Injection Penetration Testing Project
<div align="center">








Manual SQL Injection Exploitation & Security Assessment
Security Level: LOW | March 2026

</div>
📌 Project Overview

This project demonstrates a manual SQL Injection penetration test conducted against Damn Vulnerable Web Application (DVWA) in a controlled lab environment.

The objective was to:

Identify SQL injection vulnerabilities

Confirm exploitability

Enumerate database structure

Extract sensitive data

Analyze business impact

Provide remediation recommendations

This project simulates a real-world web application security assessment aligned with OWASP testing methodology.

🖥️ Lab Environment

Host Machine: Windows
Virtualization: Oracle VirtualBox
Attacker Machine: Parrot OS 6.0
Target Application: DVWA (localhost)
Security Level: LOW

🔧 Tools Used

Oracle VirtualBox

Parrot OS

Mozilla Firefox

DVWA

Browser Developer Tools

🔎 Methodology

The assessment followed a structured penetration testing workflow:

Phase 1 — Discovery

Tested input field with '

Triggered 500 Internal Server Error

Confirmed improper input sanitization

Phase 2 — Confirmation

Payload used:

' OR '1'='1' -- -

Result:

All users displayed

Authentication bypass confirmed

Phase 3 — Enumeration

Identified:

2 database columns

Database name

Table names via information_schema

Users table structure

Phase 4 — Exploitation

Payload used:

1' UNION SELECT user, password FROM users -- -

Result:

Extracted usernames

Extracted MD5 password hashes

🚨 Key Finding
🔴 Critical — SQL Injection

Location: /vulnerabilities/sqli/
Impact Level: Critical

The application directly concatenates user input into SQL queries, allowing:

Authentication bypass

Full database enumeration

Credential extraction

Potential data modification/deletion

📊 Extracted Sample Data
Username	Password Hash
admin	5f4dcc3b5aa765d61d8327deb882cf99
gordonb	e99a18c428cb38d5f260853678922e03
pablo	0d107d09f5bbe40cade3de5c71e9e9b7
smithy	5f4dcc3b5aa765d61d8327deb882cf99
💥 Impact Analysis
Technical Impact

🔴 Complete database compromise

🔴 Credential theft

🔴 Authentication bypass

🟠 Potential data destruction

Business Impact

Data breach risk

Account takeover

Reputational damage

Regulatory penalties

Financial loss

🛡️ Remediation
1️⃣ Use Prepared Statements (Critical Fix)

Vulnerable Code

$id = $_GET['id'];
$query = "SELECT * FROM users WHERE id = '$id'";

Secure Code

$stmt = $conn->prepare("SELECT * FROM users WHERE id = ?");
$stmt->bind_param("s", $_GET['id']);
$stmt->execute();
2️⃣ Input Validation

Accept only expected formats

Reject special characters when unnecessary

3️⃣ Additional Security Controls

Principle of Least Privilege

Secure error handling

Web Application Firewall

Regular security testing

Security headers implementation

📂 Repository Structure
DVWA-SQL-Injection-Project/
│
├── README.md
├── PENETRATION_TEST_REPORT.pdf
├── screenshots/
├── payloads.txt
└── methodology.md
🏆 Skills Demonstrated
Technical

Manual SQL Injection

Database Enumeration

OWASP Top 10 Understanding

Web Application Security Testing

Vulnerability Exploitation

Professional

Structured Testing Methodology

Technical Documentation

Impact Assessment

Security Reporting

📚 Key Learning Outcomes

✔ Built isolated pentesting lab
✔ Performed end-to-end SQL injection testing
✔ Extracted and analyzed sensitive data
✔ Translated technical findings into business impact
✔ Produced professional penetration test report

🔗 Connect: https://www.linkedin.com/in/rivishka-pabasarani/

Actively building practical cybersecurity skills through hands-on labs and security research.
