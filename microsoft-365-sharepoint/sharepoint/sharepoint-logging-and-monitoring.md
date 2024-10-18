# Sharepoint: Logging and Monitoring

## **Key Log Sources in SharePoint Online**

To conduct effective threat hunting, it's essential to understand the various logging capabilities and data sources available in SharePoint Online. These logs capture user activities and system events, providing vital information for identifying potential threats.

### **Unified Audit Log (UAL)**

The Unified Audit Log in Microsoft 365 is a comprehensive logging mechanism that tracks user and admin activities across various Microsoft 365 services, including SharePoint Online.

**Features of the UAL:**

* Logs activities such as file access, sharing, permission changes, and site modifications.
* Integrates with other Microsoft services like OneDrive, Teams, and Exchange.
* Can be queried using tools like PowerShell, the Security & Compliance Center, or the Microsoft Graph API.

## **Key Activities Logged in UAL for SharePoint Online:**

* **File and Folder Operations:** Access, modification, and deletion of files or folders.
* **Sharing Events:** Creation or modification of file sharing links, whether internal or external.
* **Permission Changes:** Updates to document libraries or specific file permissions.
* **Site and Document Library Modifications:** Actions that change site or library configurations.

### **SharePoint Usage Logs**

SharePoint Online generates usage logs that provide insights into how files, libraries, and sites are being used.

**Key Usage Metrics:**

* **Page Views and Hits:** Number of times pages and documents are viewed.
* **File Uploads and Downloads:** Tracking who uploaded or downloaded files.
* **Search Queries:** Recording of user search behavior within SharePoint.

These logs are typically available through the SharePoint Admin Center and are useful for identifying trends and anomalies.

### **Security & Compliance Center Logs**

The Microsoft 365 Security & Compliance Center provides a central location for managing compliance features and reviewing security-related logs.

**Key Logs from the Compliance Center:**

* **DLP (Data Loss Prevention) Events:** Captures when sensitive data (e.g., PII) is shared outside the organization.
* **Alerts:** Notifications of potential security risks, such as suspicious sharing patterns or privilege escalations.

### **Unified Audit Log for SharePoint Online**

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
