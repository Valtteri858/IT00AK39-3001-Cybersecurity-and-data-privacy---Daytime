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
- ZAP report: App_second_test.md

  # Part 2

## Introduction

This report documents the findings of penetration testing using ZAP. This test specifically focuses on vulnerabilities and their potential impact on system security. The test was conducted on March 5, 2025. The testing environment was a VirtualBox at http://0.0.0.0:8000/. The tool used during the testing was ZAP by Checkmarx. The primary goal of the test was to identify different vulnerabilities that could affect the application's security.

## Summary of Alerts

| Risk Level   | Number of Alerts |
|--------------|------------------|
| High         | 0                |
| Medium       | 0                |
| Low          | 0                |
| Informational| 1                |

# Findings and Categorization

## Informational (Low-Impact) Alert  

### User Agent Fuzzer  
- **Risk Level:** Informational (Medium)  
- **Impact:** The test identified variations in application responses based on different **User-Agent headers**.  
  This could indicate inconsistencies in how the system processes requests from different sources (e.g., mobile devices, bots, or search engine crawlers).  
- **Affected URL:** [http://0.0.0.0:8000/register](http://0.0.0.0:8000/register)  
- **Attack Method:** `POST` request with different `User-Agent` headers.  
- **Recommendation:** Review handling of **User-Agent inputs** to ensure **consistent responses** and prevent **unintended information leakage**.  

### Attack Instances:  

| **User-Agent String** | **Response Evidence** |
|----------------------|----------------------|
| Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1) | - |
| Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0) | - |
| Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1) | - |
| Mozilla/5.0 (Windows NT 10.0; Trident/7.0; rv:11.0) like Gecko | - |


## Appendices

- ZAP report: [App_first_test.md](App_first_test.md)
- ZAP report: [App_second_test.md](App_second_test.md)
  # Second_test

ZAP by [Checkmarx](https://checkmarx.com/).


## Summary of Alerts

| Risk Level | Number of Alerts |
| --- | --- |
| High | 0 |
| Medium | 0 |
| Low | 0 |
| Informational | 1 |




## Alerts

| Name | Risk Level | Number of Instances |
| --- | --- | --- |
| Authentication Request Identified | Informational | 1 |




## Alert Detail



### [ Authentication Request Identified ](https://www.zaproxy.org/docs/alerts/10111/)



##### Informational (High)

### Description

The given request has been identified as an authentication request. The 'Other Info' field contains a set of key=value lines which identify any relevant fields. If the request is in a context which has an Authentication Method set to "Auto-Detect" then this rule will change the authentication to match the request identified.

* URL: http://localhost:8000/login
  * Method: `POST`
  * Parameter: `username`
  * Attack: ``
  * Evidence: `password`
  * Other Info: `userParam=username
userValue=foo-bar@example.com
passwordParam=password
referer=http://localhost:8000/login`

Instances: 1

### Solution

This is an informational alert rather than a vulnerability and so there is nothing to fix.

### Reference


* [ https://www.zaproxy.org/docs/desktop/addons/authentication-helper/auth-req-id/ ](https://www.zaproxy.org/docs/desktop/addons/authentication-helper/auth-req-id/)



#### Source ID: 3



