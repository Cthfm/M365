# Monitoring File Access Patterns

#### **Monitoring File Access Patterns**

***

**Objective:**

Teach students how to monitor and analyze file access patterns in OneDrive to detect suspicious or unauthorized activity. This lesson will cover how to identify unusual file access, investigate potential security incidents, and respond to threats.

***

#### **Introduction to File Access Monitoring in OneDrive**

Monitoring file access patterns in OneDrive is crucial for detecting both external and internal threats. Abnormal file access can signal various types of risks, including account compromise, insider threats, and potential data exfiltration. By identifying deviations from normal access patterns, security teams can quickly identify and mitigate potential security incidents.

**Common Threats Detected via File Access Monitoring:**

* **Compromised Accounts:** Unauthorized users accessing files through a hijacked account.
* **Insider Threats:** Employees accessing files without proper authorization or outside their regular duties.
* **Data Exfiltration:** Large volumes of files accessed or downloaded in a short time period.

***

#### **Identifying Normal vs. Suspicious File Access Patterns**

Before detecting suspicious activity, it’s essential to establish a baseline of normal file access behavior in the organization. This includes typical working hours, locations, access frequencies, and files accessed by different user roles.

**Steps to Establish a Baseline:**

1. **User Roles:** Define which files are typically accessed by specific users or departments (e.g., finance, HR).
2. **Access Timing:** Identify normal working hours for accessing sensitive files.
3. **Access Frequency:** Track the usual number of file accesses by user, department, or role.
4. **Geolocation and Device:** Monitor where users typically access OneDrive from (e.g., office networks, known devices).

Once the baseline is established, deviations from these patterns can be flagged as suspicious.

***

#### **Detecting Unusual File Access Behavior**

Several file access scenarios should be closely monitored to identify suspicious activities:

**1. Access from Unrecognized Locations or IP Addresses**

If a user accesses OneDrive files from an unexpected geographic location or an unfamiliar IP address, it could indicate account compromise.

**Indicators:**

* Access from regions or countries where the organization doesn’t operate.
* Sudden file access from multiple locations within a short timeframe (impossible travel).

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileAccessed -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.IPAddress -notlike "KnownIPRange"}
```

***

**2. Access During Unusual Hours**

Users accessing files outside of regular working hours, especially late at night or during holidays, can be a sign of malicious activity. This could indicate unauthorized access or a compromised account.

**Indicators:**

* Access to sensitive files during unusual times (e.g., after business hours).
* Access to files that are typically not accessed during weekends or holidays.

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileAccessed -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.CreationTime -like "*:00:00 AM"}
```

***

**3. Accessing High-Value or Sensitive Files**

Sensitive files, such as financial records, intellectual property, or personal data, require special attention. Unauthorized access to these files should trigger immediate alerts.

**Indicators:**

* Users accessing files they don’t typically work with.
* Access to highly sensitive documents, such as HR records or financial reports.

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileAccessed -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.FileName -match "sensitive_filename"}
```

***

**4. Mass File Access or Downloads**

Unusually large numbers of files being accessed or downloaded in a short period of time can indicate a potential data exfiltration attempt. This is often a sign of compromised accounts or insider threats.

**Indicators:**

* Large volumes of files being accessed or downloaded in a short period.
* A user who doesn’t normally access a lot of files suddenly performing bulk downloads.

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileDownloaded -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Group-Object -Property UserId | Where-Object {$_.Count -gt 50}
```

***

#### **Case Study: Detecting Abnormal File Access Patterns**

**Scenario:**\
A marketing team employee suddenly begins accessing confidential financial files, which they have no business need to view. These accesses occur late at night, outside of normal working hours. Security analysts need to determine whether this is a case of account compromise or insider threat.

**Steps for Investigation:**

1. **Query File Access Events:**
   *   Use PowerShell to identify file access events from the employee:

       ```PowerShell
       PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileAccessed -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" -UserIds marketing_employee@example.com
       ```
2. **Identify Unusual Access Times:**
   *   Filter results to find access events occurring outside of regular working hours:

       ```PowerShell
       PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileAccessed -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" -UserIds marketing_employee@example.com | Where-Object {$_.CreationTime -like "*:00:00 AM"}
       ```
3. **Check the Files Accessed:**
   * Review which files were accessed to ensure they align with the employee’s job responsibilities. Focus on sensitive or high-value documents.
4. **Respond to the Threat:**
   * If the access pattern indicates potential account compromise or insider threat, consider immediately disabling the account, revoking access to the files, and escalating the investigation.

***

#### **Best Practices for Monitoring File Access in OneDrive**

1. **Automate Alerts for Suspicious Access:**
   * Set up automated alerts using tools like **Microsoft Defender for Cloud Apps** (formerly MCAS) or **Microsoft Sentinel** to flag unusual file access patterns, such as access from unfamiliar locations or during off-hours.
2. **Use Conditional Access Policies:**
   * Enforce **Conditional Access** policies to restrict file access to trusted locations and devices. For example, require that sensitive files are only accessible from the corporate network or require multi-factor authentication (MFA) for external access.
3. **Leverage Data Loss Prevention (DLP) Policies:**
   * Implement **DLP** policies to automatically monitor and block unauthorized access or sharing of sensitive files, especially personal data, intellectual property, or financial information.
4. **Regularly Review Access Logs:**
   * Conduct regular audits of OneDrive access logs to ensure users are following company policies and that sensitive files are not being accessed improperly.
5. **Investigate Abnormal Access Immediately:**
   * Any abnormal file access should be investigated as soon as possible. Use real-time monitoring tools to spot potential threats and respond quickly to mitigate risks.
