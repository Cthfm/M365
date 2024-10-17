# OneDrive and UAL

#### **Why is UAL Important for OneDrive Security?**

OneDrive is a highly dynamic environment where users frequently upload, modify, and share files. The UAL provides detailed insights into all these activities, making it a crucial tool for:

* **Detecting Suspicious File Access or Sharing:**\
  UAL logs every file access and sharing event, which can help identify unauthorized users or abnormal access patterns.
* **Monitoring File Modifications and Deletions:**\
  Security teams can detect unusual file modifications or mass deletions, often indicative of insider threats, malware, or ransomware attacks.
* **Tracking Synchronization and External Sharing:**\
  Logs provide details on file synchronization activities, which is important for spotting potential risks such as unsanctioned devices syncing sensitive data or external sharing that violates security policies.

***

#### **Types of OneDrive Events Captured by UAL**

The UAL captures a wide range of OneDrive-specific events that are vital for threat detection. Key event types include:

* **File and Folder Operations:**
  * **FileAccessed:** Logs every time a user accesses a file.
  * **FileDownloaded:** Records file download activities. Unusual or mass downloads may indicate data exfiltration attempts.
  * **FileModified:** Tracks changes made to files, which can help identify tampering or unauthorized edits.
  * **FileDeleted:** Logs file deletions, which could be indicative of malicious intent or attempts to cover up data theft.
* **Sharing and Permissions Changes:**
  * **SharingInvitationCreated:** Logs when a sharing invitation is created, providing details on the shared file, the recipient, and the permissions granted.
  * **SharingLinkCreated:** Tracks the creation of shareable links, including the access level (e.g., view-only or edit) and whether the link is public or restricted to specific users.
* **Sync Activity:**
  * **FileSync:** Logs synchronization events when files are synced between OneDrive and a user’s device. Monitoring this is critical for spotting potential ransomware infections or unauthorized syncing from unmanaged devices.
* **User Access and Authentication:**
  * **Login Events:** Logs details of user login attempts, including the IP address and device used. This can help detect unauthorized or risky access, such as logins from suspicious locations or devices.

***

#### **How to Enable and Configure UAL for OneDrive**

To fully utilize the UAL for OneDrive threat hunting, it must be enabled and configured properly. Here’s a step-by-step guide:

1. **Enable Unified Audit Logging (If Not Already Enabled):**
   * UAL is enabled by default for Microsoft 365 tenants, but it’s essential to verify its status.
   *   Use PowerShell to check and enable the Unified Audit Log if necessary:

       ```PowerShell
       PowerShellCopy codeSet-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
       ```
2. **Configuring Audit Log Retention:**
   * The default retention period for UAL data varies based on the type of Microsoft 365 license:
     * **Microsoft 365 E3/E5:** 90 days of retention.
     * **Microsoft 365 Compliance Add-ons:** Extended retention periods of up to a year or more.
   * Adjust retention policies based on your organization’s compliance and audit requirements.
3. **Accessing the Unified Audit Log:**
   * **Microsoft 365 Compliance Center:**
     * Go to the **Microsoft 365 Compliance Center** and navigate to **Audit Log Search** to access the UAL.
     * You can filter logs based on specific user activities, timeframes, or event types related to OneDrive.
   * **PowerShell:**
     *   Use PowerShell to query UAL data directly for more flexibility and automation. Here’s an example to search for OneDrive file access events:

         ```PowerShell
         PowerShellCopy codeSearch-UnifiedAuditLog -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" -RecordType SharePoint -Operations FileAccessed
         ```
4. **Configuring Advanced Filters:**
   * UAL provides advanced filtering options that allow you to focus on specific types of events, users, or activities. Filters include:
     * **Start and End Dates:** Define specific time periods for analysis.
     * **Users:** Focus on high-risk users or roles (e.g., admins or those with access to sensitive data).
     * **Event Types:** Isolate particular events like file downloads or sharing activities.

***

#### **Accessing UAL via PowerShell and Microsoft Graph API**

**1. PowerShell Commands for OneDrive Audit Logs:**

PowerShell provides a flexible way to query the UAL, enabling automation and tailored queries for specific OneDrive events.

*   **Example: Query for File Download Events**

    ```PowerShell
    Search-UnifiedAuditLog -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" -RecordType SharePoint -Operations FileDownloaded -UserIds user@example.com
    ```
*   **Example: Query for External Sharing Invitations**

    ```PowerShell
    Search-UnifiedAuditLog -Operations SharingInvitationCreated -ExternalAccess True
    ```

**2. Using Microsoft Graph API for Advanced Queries:**

The **Microsoft Graph API** allows organizations to programmatically access UAL data, which can be especially useful for integrating OneDrive logs into custom security dashboards or SIEM systems.

*   **Example Query to Retrieve OneDrive Events Using Graph API:**

    ```bash
    GET https://graph.microsoft.com/v1.0/auditLogs/signIns
    ```

    Adjust the query to retrieve specific events related to OneDrive, such as file accesses, sharing activities, or sync events.
* **Automating Log Extraction and Analysis:**
  * Leverage APIs to automate daily or weekly extraction of OneDrive logs.
  * Integrate this data into SIEM platforms like Microsoft Sentinel or Splunk for advanced threat detection and analysis.

***

#### **Practical Steps for Leveraging UAL in Threat Hunting**

* **Identify Baseline Activity:**
  * Establish normal usage patterns, such as typical login times, average file access, and regular sharing behavior. This will help identify anomalies.
* **Monitor Key Security Events:**
  * Focus on high-risk events, such as large-scale file downloads, external sharing of sensitive documents, and access attempts from unknown IP addresses.
* **Regular Log Reviews:**
  * Schedule regular reviews of OneDrive activity logs using the UAL, and investigate any anomalies or suspicious patterns. Automate log reviews with PowerShell or API integrations where possible.
