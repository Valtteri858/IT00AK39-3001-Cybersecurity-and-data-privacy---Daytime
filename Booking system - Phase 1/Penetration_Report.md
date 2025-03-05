# Introduction
The purpose of this report is to document the findings of penetration testing, using ZAP. This test specifically focuses on vulnerabilities and their potential impact on system security. The test was conducted on **February 20, 2025**. The testing environment was a **VirtualBox** at `http://localhost:8000`. The tool used during the testing was **ZAP by Checkmarx**. The primary goal of the test was to identify different vulnerabilities that could affect the security of the application.

# Summary
## Path Traversal
- **Impact**: This vulnerability allows an attacker to access system files and directories outside the web application’s root directory.
- **Recommendations**: Implement strong input validation and strictly limit access to authorized locations.

## SQL Injection
- **Impact**: SQL injection vulnerability allows attackers to execute malicious SQL queries and potentially access database information.
- **Recommendations**: Avoid dynamic SQL queries and always use prepared statements.

## Format String Error
- **Impact**: This type of error can allow data manipulation or execution of malicious commands on the server.
- **Recommendations**: Modify the application code to sanitize invalid strings before execution.

# Findings and Categorization
## Path Traversal  
- **URL**: `http://localhost:8000/register`  
- **Parameter**: `username`  
- **Attack**: `../`  
- **Findings**: An attacker can manipulate the URL to access files that are not normally available to users.  
- **Solution**: Implement strict input validation and limit file handling to authorized directories.  

## SQL Injection  
- **URL**: `http://localhost:8000/register`  
- **Parameter**: `username`  
- **Attack**: `ccc AND 1=1 --`  
- **Findings**: An attacker can execute SQL queries that may manipulate database contents or expose sensitive information.  
- **Solution**: Avoid dynamic SQL query creation and use prepared statements or stored procedures.  

## Format String Error  
- **URL**: `http://localhost:8000/register`  
- **Parameter**: `username`  
- **Attack**: `ZAP%n%s%n%s%n%s%n%s%n%s%n%s%n%s%n%s%n%s%n%s%n%s%n%s%n%s%n%s%n%s%n%s%n%s%n%s%n%s%n%s%n%s`  
- **Findings**: This vulnerability could be exploited to execute potentially dangerous commands.  
- **Solution**: Sanitize invalid strings in the code and ensure that only allowed inputs are accepted.
## Appendices
- ZAP report: App_first_test.md
- - ZAP report: App_second_test.md
