# Key Events in OneDrive

## **Understanding Key Events in OneDrive Logs**

OneDrive logs a variety of events that provide insights into user activities, file interactions, and potential security threats. By understanding these key events, threat hunters can monitor abnormal behavior, detect unauthorized access, and mitigate risks effectively.

Here are the most important event types in OneDrive logs:

### **File Access Events**

*   **FileAccessed:**

    * This event logs every instance when a user accesses a file in OneDrive. Monitoring these logs is essential for identifying unauthorized access to sensitive documents or unusual access patterns.

    **Significance:**

    * **Threat Hunting Focus:** Suspicious access by unrecognized users or abnormal access times (e.g., access during non-working hours).
    * **Example Use Case:** Detecting a compromised user account that is accessing confidential files.

### **File Download Events**

*   **FileDownloaded:**

    * This event tracks when a file is downloaded from OneDrive to a user’s device. Monitoring for mass file downloads is important for detecting potential data exfiltration, insider threats, or compromised accounts.

    **Significance:**

    * **Threat Hunting Focus:** Sudden spikes in the number of downloaded files or downloads from unusual IP addresses.
    * **Example Use Case:** Detecting an insider threat where an employee is downloading a large volume of sensitive data before leaving the company.

### **File Deletion Events**

*   **FileDeleted:**

    * This event logs when a file is deleted from OneDrive. Mass file deletions can signal malicious activities such as insider attacks or ransomware infections, where files are either deleted or encrypted as part of the attack.

    **Significance:**

    * **Threat Hunting Focus:** Large-scale deletions, deletions of critical or sensitive files, or deletions that happen shortly after files are modified.
    * **Example Use Case:** Detecting a ransomware attack by identifying mass file deletions or abnormal file deletion behavior.

### **File Modification Events**

*   **FileModified:**

    * This event tracks when a file is modified in OneDrive. Monitoring these events is critical for detecting tampering or unauthorized changes to important documents, such as financial reports or intellectual property.

    **Significance:**

    * **Threat Hunting Focus:** Unusual modifications to sensitive files, modifications followed by file deletions, or modifications outside regular working hours.
    * **Example Use Case:** Detecting an external attacker or insider threat modifying files to sabotage data integrity or introduce backdoors into shared documents.

### **Sharing Events**

*   **SharingInvitationCreated:**

    * This event logs when a user shares a file or folder, either with internal users or external parties. Monitoring sharing invitations is crucial for identifying unauthorized external sharing, which can lead to data breaches.

    **Significance:**

    * **Threat Hunting Focus:** Unusual or excessive external sharing of sensitive files, sharing with unapproved external domains, or the creation of public links.
    * **Example Use Case:** Detecting unauthorized sharing of confidential company documents with external domains or competitors.
*   **SharingLinkCreated:**

    * This event logs the creation of sharing links for files or folders. If a public sharing link is created (i.e., “Anyone with the link” access), it could expose sensitive data to the public internet.

    **Significance:**

    * **Threat Hunting Focus:** Creation of public or anonymous links for files that should remain private or restricted. Public links for sensitive or confidential documents should be immediately investigated.
    * **Example Use Case:** Detecting when an employee accidentally (or maliciously) creates a public link to a sensitive company report or intellectual property.

### **Synchronization Events**

*   **FileSync:**

    * This event logs when files are synced between OneDrive and a user’s device. Sync events should be monitored to detect unauthorized devices attempting to sync sensitive files or abnormal sync activity from known users.

    **Significance:**

    * **Threat Hunting Focus:** Syncing from unfamiliar devices, syncing sensitive files to unapproved devices, or abnormal volumes of synced data.
    * **Example Use Case:** Detecting compromised user accounts or stolen credentials used to sync confidential files to an unauthorized device.

### **Permission Changes**

*   **PermissionChanged:**

    * This event logs any changes to file or folder permissions, such as when a user grants edit rights to a file that should only be viewed, or when public access is enabled.

    **Significance:**

    * **Threat Hunting Focus:** Unwarranted changes to permission levels that grant more access than necessary (e.g., converting view-only permissions to edit permissions).
    * **Example Use Case:** Detecting when a user inadvertently grants external users full edit permissions on a sensitive financial document.

### **Building Queries to Focus on Key Events**

To monitor OneDrive for suspicious activity, it is important to build targeted queries that focus on high-risk events. Here are a few practical examples:

* **Monitoring External Sharing**
* **Detecting Mass File Downloads by a User**
* **Tracking Abnormal File Deletions:**

### **Practical Steps for Threat Hunting Using Key Events**

1. **Establish a Baseline for Normal Behavior:**
   * Monitor standard user behavior, such as average file access, sharing patterns, and synchronization volumes. This helps in identifying abnormal activity that deviates from the norm.
2. **Focus on High-Risk Activities:**
   * Prioritize tracking activities such as external sharing of sensitive data, mass file downloads, and file deletions. These are often indicators of data exfiltration or malicious behavior.
3. **Set Up Alerts and Automation:**
   * Use tools like Microsoft Sentinel or Power Automate to set up real-time alerts for specific key events (e.g., when a file is downloaded by an unrecognized user or an external sharing link is created).
4. **Regularly Review Logs:**
   * Schedule periodic reviews of key OneDrive events, particularly focusing on suspicious patterns such as abnormal file access or unauthorized sharing activities.
