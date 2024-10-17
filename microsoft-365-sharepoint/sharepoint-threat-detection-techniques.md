# Sharepoint Threat Detection Techniques

Key **Attack Scenarios in SharePoint Online**

In this module, we focus on identifying the key attack scenarios that a threat hunter should be aware of when working with SharePoint Online. Understanding these scenarios will guide the development of detection strategies and enhance your ability to respond effectively to suspicious activities.

**1. Insider Threats**

* **Overview:** Insider threats occur when users with legitimate access to SharePoint data misuse their privileges. This could include accessing sensitive documents, sharing information externally, or escalating their permissions without authorization.
* **Example:** An employee with access to confidential files downloads large quantities of data before resigning from the organization.

**Indicators of Insider Threats:**

* Unusual file access patterns (e.g., large volume of sensitive documents accessed in a short period).
* Files shared externally without clear business justification.
* Unauthorized permission changes by non-admin users.

**2. Account Compromise**

* **Overview:** An external attacker gains access to a legitimate user’s SharePoint account through credential theft (e.g., phishing or brute force) and uses that account to exfiltrate data or escalate privileges.
* **Example:** A phishing attack leads to an attacker compromising an employee’s SharePoint credentials, allowing them to access sensitive files unnoticed.

**Indicators of Account Compromise:**

* Login activity from unusual geolocations or IP addresses.
* Sudden changes in user behavior, such as accessing files they do not typically interact with.
* Unusual file downloads or modifications shortly after account login.

**3. Privilege Escalation**

* **Overview:** Attackers or malicious insiders elevate their permissions within SharePoint Online, allowing them access to sensitive data or control over site settings.
* **Example:** A user without administrative privileges suddenly gains the ability to modify access controls or delete files across multiple document libraries.

**Indicators of Privilege Escalation:**

* Sudden changes in a user's access level or permission sets.
* Non-admin users making permission changes.
* Administrative activities performed by unusual or low-level accounts.

**4. Data Exfiltration via File Sharing**

* **Overview:** Attackers or insiders may attempt to exfiltrate sensitive data by sharing files with external domains, either by creating sharing links or downloading data themselves and distributing it.
* **Example:** A user shares sensitive HR documents with an external email address and later deletes the sharing link to hide the activity.

**Indicators of Data Exfiltration:**

* External sharing of sensitive files.
* Excessive downloads of files from a specific user.
* Sharing links generated for large volumes of files.

**KQL Queries for Detecting Suspicious Activity**

One of the most powerful tools for hunting threats in SharePoint Online is the use of **Kusto Query Language (KQL)** within the Microsoft 365 compliance or audit logs. In this section, we will walk through some practical KQL queries for identifying suspicious activity.

**Detecting Unusual File Access Patterns**

When files are accessed in large quantities or by users who typically don’t interact with them, it could signal an insider threat or compromised account.

**KQL Query Example:**

```kusto
AuditLogs
| where RecordType == "SharePoint"
| where Operation == "FileAccessed"
| summarize AccessCount = count() by UserId, FileName, Timestamp
| where AccessCount > 20 and Timestamp between (datetime("2024-01-01")..datetime("2024-01-02"))
```

This query helps detect users accessing an unusually high number of files in a short period.

**Detecting External Sharing of Sensitive Files**

External sharing is one of the main methods used for data exfiltration. Monitoring file sharing activities to external domains is critical for threat detection.

**KQL Query Example:**

```kusto
AuditLogs
| where RecordType == "SharePoint"
| where Operation == "SharingSet"
| where SharingType == "External"
| summarize ShareCount = count() by UserId, FileName, ExternalUserOrGroup
| where ShareCount > 5
```

This query highlights excessive external sharing by a specific user, which could indicate malicious intent or negligence.

**Detecting Privilege Escalation**

Privilege escalation allows attackers or malicious insiders to elevate their permissions to access restricted areas of SharePoint Online.

**KQL Query Example:**

```kusto
AuditLogs
| where RecordType == "SharePoint"
| where Operation == "PermissionChange"
| where PermissionLevel == "Admin"
| summarize ChangeCount = count() by UserId, TargetUserOrGroup
| where ChangeCount > 1
```

This query identifies users who have suddenly gained or changed administrative permissions, which may indicate an account compromise or malicious insider activity.

**Detecting Anomalous Login Behavior**

Detecting logins from unusual geolocations or devices can help identify account compromise.

**KQL Query Example:**

```kusto
AuditLogs
| where RecordType == "SharePoint"
| where Operation == "Login"
| where UserId != "admin"
| where ClientIP != "InternalIPRange"
| summarize LoginCount = count() by UserId, ClientIP, Timestamp
| where LoginCount > 1 and ClientIP != "InternalNetwork"
```

This query detects logins from external IP ranges that may indicate account compromise.

**Behavioral Analysis in SharePoint Online**

Behavioral analysis involves creating a baseline of normal user behavior and comparing it with current activity to identify deviations that could signify a threat.

**Building Baseline User Activity**

To understand what "normal" looks like for a user, you can use audit logs to track file access, downloads, and sharing over time. Once a baseline is established, deviations from this behavior may indicate suspicious activity.

**Steps for Baseline Creation:**

1. **Collect Data:** Gather data on user activities over several weeks or months using the Unified Audit Log.
2. **Analyze Patterns:** Identify normal patterns for file access, downloads, sharing, and permission changes for each user or group.
3. **Define Thresholds:** Set thresholds for what constitutes abnormal behavior (e.g., downloading more than 50 files in an hour, sharing more than 10 files externally in a day).

**Monitoring Sensitive Data Access**

Users accessing highly sensitive files that they normally don’t interact with should trigger an alert. Behavioral baselines help pinpoint such deviations.

**KQL Query for Monitoring Sensitive Data Access:**

```kusto
AuditLogs
| where RecordType == "SharePoint"
| where Operation == "FileAccessed"
| where FileSensitivityLabel in ("Confidential", "HighlyConfidential")
| summarize AccessCount = count() by UserId, FileName
| where AccessCount > 5
```

This query tracks when a user accesses sensitive files, potentially indicating unauthorized access.

**Detecting Deviations from Normal Usage Patterns**

Using thresholds and baselines, you can detect anomalies such as spikes in file downloads, unusual login times, or unexpected permission changes.

**KQL Query for Usage Anomalies:**

```kusto
AuditLogs
| where RecordType == "SharePoint"
| where Operation == "FileDownloaded"
| summarize DownloadCount = count() by UserId, Timestamp
| where DownloadCount > 50
```

This query flags any user downloading more than 50 files within a given timeframe, which may signal data exfiltration.

#### **Response to Detected Threats**

Once suspicious activity is detected, it’s critical to follow an incident response process to mitigate the threat and secure the environment.

**Steps to Respond to Detected Threats:**

1. **Identify the Source of the Threat:** Determine whether the activity is the result of insider behavior, compromised accounts, or privilege escalation.
2. **Isolate the Threat:** Temporarily suspend the user’s access to SharePoint or quarantine the affected files to prevent further data leakage.
3. **Investigate the Full Scope:** Use logs to trace the attacker’s actions, including all files accessed, shared, or downloaded.
4. **Remediate:** Revoke unauthorized sharing links, reset compromised user accounts, and review permission settings.
5. **Review and Harden Security:** Implement additional controls such as MFA (Multi-Factor Authentication), restricted file sharing policies, and more frequent audit log reviews.
