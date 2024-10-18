# OneDrive and UAL

## Overview

The following section goes over OneDrive and its relationship to UAL. It briefly touches on the detections that are logged in OneDrive as well as best practices for specific activities to hunt for.&#x20;

## **Why is UAL Important for OneDrive Security?**

OneDrive is a highly dynamic environment where users frequently upload, modify, and share files. The UAL provides detailed insights into all these activities, making it a crucial tool for:

* **Detecting Suspicious File Access or Sharing:**\
  UAL logs every file access and sharing event, which can help identify unauthorized users or abnormal access patterns.
* **Monitoring File Modifications and Deletions:**\
  Security teams can detect unusual file modifications or mass deletions, often indicative of insider threats, malware, or ransomware attacks.
* **Tracking Synchronization and External Sharing:**\
  Logs provide details on file synchronization activities, which is important for spotting potential risks such as unsanctioned devices syncing sensitive data or external sharing that violates security policies.

### **Types of OneDrive Events Captured by UAL**

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

### **Practical Steps for Leveraging UAL in Threat Hunting**

* **Identify Baseline Activity:**
  * Establish normal usage patterns, such as typical login times, average file access, and regular sharing behavior. This will help identify anomalies.
* **Monitor Key Security Events:**
  * Focus on high-risk events, such as large-scale file downloads, external sharing of sensitive documents, and access attempts from unknown IP addresses.
* **Regular Log Reviews:**
  * Schedule regular reviews of OneDrive activity logs using the UAL, and investigate any anomalies or suspicious patterns. Automate log reviews with PowerShell or API integrations where possible.
