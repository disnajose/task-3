# Vulnerability Scan Report – Task 3

## **Overview**
This report documents the results of a **Basic Network Scan** performed on my local machine using **Tenable Nessus Essentials**.  
The scan targeted the local host (`127.0.0.1`) to identify potential vulnerabilities, configuration issues, and informational findings.

**Scan Details:**
- **Tool:** Nessus Essentials
- **Scan Type:** Basic Network Scan
- **Target:** 127.0.0.1 (Localhost)
- **Date:** 13 August 2025
- **Policy:** CVSS v3.0
- **Duration:** ~8 minutes

---

## **Summary of Findings**
| Severity  | Count |
|-----------|-------|
| Critical  | 0     |
| High      | 0     |
| Medium    | 1     |
| Low       | 0     |
| Info      | 22    |

---

## **Top Vulnerability Identified**
### 1. SMB Signing Not Required
- **Severity:** Medium
- **CVSS v3.0 Score:** 5.3
- **Description:**  
  SMB (Server Message Block) signing is not enforced. Without signing, a remote attacker could perform man-in-the-middle attacks against SMB traffic, potentially altering communications.
- **Impact:**  
  This could allow attackers to intercept or modify SMB traffic between the client and server.
- **Solution (Windows):**
  1. Open **Local Group Policy Editor** (`gpedit.msc`).
  2. Navigate to:  
     `Computer Configuration → Windows Settings → Security Settings → Local Policies → Security Options`.
  3. Find the setting:  
     **"Microsoft network server: Digitally sign communications (always)"**
  4. Set it to **Enabled**.
  5. Restart the computer.
- **Reference Links:**
  - [Microsoft SMB Signing Documentation](https://technet.microsoft.com/en-us/library/cc731957.aspx)
  - [Samba Server Signing](https://www.samba.org/samba/docs/current/man-html/smb.conf.5.html)

---

## **Informational Findings**
The scan also reported **22 informational findings** such as:
- Open ports
- Service version detection
- Operating system fingerprinting

These are not direct vulnerabilities but can be useful for attackers in reconnaissance.

---

## **Remediation Plan**
1. Enable **SMB Signing** to prevent MITM attacks on SMB connections.
2. Keep Windows up-to-date with the latest security patches.
3. Review and disable unnecessary open services.

---

## **Screenshots**
### Scan Summary
![Scan Summary](screenshots/scan_summary.png)

### Vulnerabilities List
![Vulnerability List](screenshots/vulnerability_list.png)

### SMB Signing Not Required (Details)
![SMB Signing Details](screenshots/smb_signing.png)

---

## **Conclusion**
The scan identified no critical or high-risk vulnerabilities, and only one medium-risk vulnerability related to SMB Signing configuration.  
Enforcing SMB signing significantly improves the security posture against network-based attacks.
