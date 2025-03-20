
## Introduction
This report documents the findings of penetration testing using ZAP. The test was conducted on March 5, 2025, focusing on identifying vulnerabilities and assessing their potential impact on system security. The testing environment was a VirtualBox running at `http://0.0.0.0:8000/`. The tool used for testing was **ZAP by Checkmarx**. The primary objective was to detect vulnerabilities that could compromise the security of the application.

## Summary of Alerts

| Risk Level   | Number of Alerts |
|-------------|----------------|
| High        | 0              |
| Medium      | 0              |
| Low         | 0              |
| Informational | 1              |

## Findings and Categorization

### Informational (Low-Impact) Alert

#### Authentication Request Identified

- **Risk Level:** Informational (High)
- **Description:**
  The given request has been identified as an authentication request. The 'Other Info' field contains a set of key-value lines identifying relevant fields. If the request is in a context with an Authentication Method set to "Auto-Detect," this rule will adjust authentication to match the request identified.

- **Affected URL:**
  - `http://localhost:8000/login`

- **Method:**
  - `POST`

- **Parameter:**
  - `username`

- **Attack:**
  ```
  
  ```

- **Evidence:**
  - `password`

- **Other Info:**
  ```
  userParam=username
  userValue=foo-bar@example.com
  passwordParam=password
  referer=http://localhost:8000/login
  ```

- **Instances:** 1

- **Solution:**
  This is an informational alert rather than a vulnerability, so no action is required.

- **Reference:**
  - ZAP Authentication Request Identification

## Appendices

- **ZAP report:** [App_first_test.md](App_first_test.md)
- **ZAP report:** [App_second_test.md](App_second_test.md)
