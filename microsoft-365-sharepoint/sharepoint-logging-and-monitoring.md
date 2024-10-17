# Sharepoint: Logging and Monitoring

**Key Log Sources in SharePoint Online**

To conduct effective threat hunting, it's essential to understand the various logging capabilities and data sources available in SharePoint Online. These logs capture user activities and system events, providing vital information for identifying potential threats.

**Unified Audit Log (UAL)**

The Unified Audit Log in Microsoft 365 is a comprehensive logging mechanism that tracks user and admin activities across various Microsoft 365 services, including SharePoint Online.

**Features of the UAL:**

* Logs activities such as file access, sharing, permission changes, and site modifications.
* Integrates with other Microsoft services like OneDrive, Teams, and Exchange.
* Can be queried using tools like PowerShell, the Security & Compliance Center, or the Microsoft Graph API.

**How to Enable the UAL:**

1. Navigate to the **Microsoft 365 Compliance Center**.
2. Under **Solutions**, select **Audit**.
3. Click **Start recording user and admin activity** if it's not already enabled.
4. Once enabled, SharePoint activities will be logged and searchable within the audit log.

**Key Activities Logged in UAL for SharePoint Online:**

* **File and Folder Operations:** Access, modification, and deletion of files or folders.
* **Sharing Events:** Creation or modification of file sharing links, whether internal or external.
* **Permission Changes:** Updates to document libraries or specific file permissions.
* **Site and Document Library Modifications:** Actions that change site or library configurations.

**SharePoint Usage Logs**

SharePoint Online generates usage logs that provide insights into how files, libraries, and sites are being used.

**Key Usage Metrics:**

* **Page Views and Hits:** Number of times pages and documents are viewed.
* **File Uploads and Downloads:** Tracking who uploaded or downloaded files.
* **Search Queries:** Recording of user search behavior within SharePoint.

These logs are typically available through the SharePoint Admin Center and are useful for identifying trends and anomalies.

**Security & Compliance Center Logs**

The Microsoft 365 Security & Compliance Center provides a central location for managing compliance features and reviewing security-related logs.

**Key Logs from the Compliance Center:**

* **DLP (Data Loss Prevention) Events:** Captures when sensitive data (e.g., PII) is shared outside the organization.
* **Alerts:** Notifications of potential security risks, such as suspicious sharing patterns or privilege escalations.

**Unified Audit Log for SharePoint Online**

The Unified Audit Log is a central source for hunting threats in SharePoint Online. It contains detailed records of user actions, making it an indispensable tool for identifying anomalies.

**Core Events Logged in UAL:**

* **File Access:** Tracks when files or folders are accessed or downloaded.
* **File Sharing:** Logs when users create links to share files, including whether they shared them externally or internally.
* **File Deletion and Restoration:** Logs when files are deleted, moved, or restored from the recycle bin.
* **Permission Changes:** Tracks updates to sharing permissions or access control lists (ACLs).
* **Site and Library Changes:** Monitors modifications to sites, libraries, or settings that may indicate misconfigurations or compromise.

**Key Fields in the UAL:**

* **User ID:** The identifier of the user who performed the action.
* **Operation:** The specific activity (e.g., FileAccess, SharingSet, or PermissionChange).
* **Object ID:** The resource or file affected by the action.
* **Client IP:** The originating IP address of the action, useful for identifying external or unexpected locations.
* **Date and Time:** Timestamps that allow for tracking when actions occurred.
* **Target User or Group:** Identifies users or groups involved, particularly useful in tracking permissions and external sharing.

**Hands-on Lab: Accessing and Analyzing the Unified Audit Log**

1.  **Access the UAL via PowerShell:**

    * Use the following PowerShell commands to export audit logs related to SharePoint:

    ```powershell
    Search-UnifiedAuditLog -StartDate "YYYY-MM-DD" -EndDate "YYYY-MM-DD" -RecordType SharePoint -Operations FileAccessed, SharingSet, PermissionChange
    ```
2. **Review Logs in the Security & Compliance Center:**
   * Navigate to the **Audit** section in the Compliance Center, filter for SharePoint Online activities, and export results.
3. **Graph API Queries:**
   * Use Microsoft Graph API to query the audit log for specific SharePoint events and perform more granular filtering.

**Threat Detection Using Logs**

Threat hunting in SharePoint Online is powered by effectively querying and analyzing the available logs to detect unusual or suspicious activities. The following detection techniques can help identify threats early.

**Identifying Anomalous File Access**

Unusual file access, such as a user accessing many sensitive files in a short period, could indicate a compromised account or insider threat.

**Sample KQL Query:**

```kusto
AuditLogs
| where RecordType == "SharePoint"
| where Operation == "FileAccessed"
| summarize AccessCount = count() by UserId, FileName, Timestamp
| where AccessCount > 10 and Timestamp between (startDate..endDate)
```

This query helps identify users accessing a large number of files in a short period, potentially indicating data exfiltration attempts.

**Detecting Suspicious Sharing Events**

External sharing of files, especially sensitive documents, may be indicative of an attack.

**Sample KQL Query:**

```kusto
AuditLogs
| where RecordType == "SharePoint"
| where Operation == "SharingSet"
| where SharingType == "External"
| summarize ExternalShares = count() by UserId, FileName, SharingLinkType
| where ExternalShares > 5
```

This query detects excessive external sharing by users, a potential indicator of data theft.

**Tracking Privilege Escalation**

If a user suddenly gains administrative permissions or the ability to access sensitive files, it could be a sign of privilege escalation.

**Sample KQL Query:**

```kusto
AuditLogs
| where RecordType == "SharePoint"
| where Operation == "PermissionChange"
| where UserId != "admin"
| summarize ChangeCount = count() by UserId, TargetUserOrGroup, PermissionLevel
| where PermissionLevel == "Admin"
```

This query helps detect unauthorized users who gain admin privileges unexpectedly.

&#x20;**Using SharePoint Usage Logs for Anomaly Detection**

SharePoint usage logs offer insights into how users are interacting with files and sites, allowing threat hunters to spot suspicious trends and usage patterns.

**Anomaly Detection Examples:**

* **Unusual File Downloads:** A spike in file downloads from an external IP could indicate an attacker attempting to steal data.
* **Repeated Failed Logins:** A user experiencing multiple failed login attempts might be the target of a brute-force attack.

**Sample KQL Query for Download Anomalies:**

```kusto
AuditLogs
| where RecordType == "SharePoint"
| where Operation == "FileDownloaded"
| summarize DownloadCount = count() by UserId, ClientIP, Timestamp
| where DownloadCount > 50 and ClientIP != "InternalRange"
```

This query identifies large-scale downloads from external IP addresses.
