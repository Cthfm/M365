# OneDrive Security Architecture

#### **Overview**

This section provides an understanding of OneDrive's security architecture, focusing on its built-in security mechanisms, integration with other Microsoft security tools, and how it protects organizational data.

### **How OneDrive Ensures Data Security**

OneDrive offers multiple layers of protection to ensure the security of data, both at rest and in transit. The security features are tightly integrated with Microsoft’s broader security ecosystem, ensuring compliance and protection for organizational data.

**1. Encryption**

* **Encryption in Transit:**
  * All data transmitted between the user’s device and OneDrive is encrypted using **Transport Layer Security (TLS)**. This ensures that data cannot be intercepted or tampered with while in transit over the internet.
* **Encryption at Rest:**
  * Data stored in OneDrive is encrypted at rest using **BitLocker** for full-volume encryption and **File-Level Encryption** to encrypt individual files. This ensures that even if the physical storage is compromised, the data remains secure.
* **File Fragmentation and Encryption:**
  * Files uploaded to OneDrive are split into small chunks, each encrypted separately. This reduces the risk of exposing entire files if an attacker manages to compromise part of the storage.

**2. Identity and Access Management**

OneDrive is tightly integrated with **Microsoft Entra ID (formerly Azure AD)**, providing comprehensive identity and access management capabilities. This allows organizations to enforce strong authentication, conditional access, and granular permissions.

* **Multi-Factor Authentication (MFA):**
  * Organizations can enforce MFA for users accessing OneDrive, ensuring that even if credentials are compromised, attackers cannot access the data without an additional form of verification (e.g., mobile app, SMS, or email).
* **Conditional Access Policies:**
  * Conditional Access allows administrators to define rules that control how and when users can access OneDrive. For example, users can be restricted based on their device compliance, geographic location, or risk level.
  * Example policy: Allow OneDrive access only from managed devices or require MFA if accessing files from an untrusted network.
* **Role-Based Access Control (RBAC):**
  * Administrators can apply **Role-Based Access Control** to ensure that users have appropriate access to files. This minimizes the risk of unauthorized data access by restricting permissions to the least privilege necessary for a user to perform their job.

**3. Data Loss Prevention (DLP)**

OneDrive integrates with **Microsoft 365’s Data Loss Prevention (DLP)** policies to prevent the unintentional sharing of sensitive data. Administrators can create policies that automatically detect and block sensitive data from being shared or downloaded inappropriately.

* **How DLP Works in OneDrive:**
  * DLP scans files stored in OneDrive for sensitive information (e.g., credit card numbers, social security numbers) and applies rules to prevent sharing or downloading that data.
  * Example: A DLP policy can prevent users from sharing files externally if they contain sensitive information like personal identification numbers (PINs) or proprietary business data.

**4. File Versioning and Recovery**

OneDrive provides built-in capabilities for file versioning and recovery, allowing users and administrators to quickly recover from data corruption, accidental deletions, or ransomware attacks.

* **File Versioning:**
  * Every time a file is modified, OneDrive automatically creates a new version. Users can revert to previous versions of a file, allowing them to recover from mistakes or malicious modifications.
  * This is a critical defense against ransomware that might corrupt or encrypt files. By reverting to a previous, uninfected version, organizations can avoid paying a ransom.
* **Recycle Bin and Second-Stage Recycle Bin:**
  * Deleted files are first moved to the **Recycle Bin** and can be restored by users. If the files are removed from the Recycle Bin, they are placed into the **Second-Stage Recycle Bin**, where administrators can restore them.
  * This helps organizations recover from accidental deletions or malicious insider threats trying to erase evidence of data theft.

**5. Compliance and Regulatory Standards**

OneDrive adheres to several industry and regulatory compliance standards, ensuring that organizations can meet their legal and regulatory obligations when storing data in the cloud.

* **Compliance Certifications:**
  * OneDrive is certified under several compliance frameworks, including **ISO 27001**, **HIPAA**, **GDPR**, and **SOC 1/2/3**. These certifications demonstrate that OneDrive follows industry best practices for data security and privacy.
* **Data Residency and Sovereignty:**
  * OneDrive allows organizations to choose where their data is stored geographically. This is crucial for complying with data residency laws, such as GDPR, which requires organizations to store personal data within the European Union.

#### **Microsoft Defender for Office 365**

OneDrive includes threat detection capabilities provided by **Microsoft Defender for Office 365**, which scans for malware and other malicious activities in real-time.

* **Malware Detection and Prevention:**
  * Microsoft Defender scans files stored in OneDrive for malware. If a file is identified as malicious, the system will automatically quarantine it and notify the user and administrator. This prevents the spread of malware through file sharing or syncing to other devices.

***

#### **Conditional Access for OneDrive**

**Conditional Access** is a crucial component of OneDrive’s security architecture, allowing organizations to define and enforce granular access policies.

* **Location-Based Access:**
  * Organizations can create rules to restrict access to OneDrive based on user location. For example, access can be blocked for users attempting to log in from high-risk locations or countries where the organization has no business presence.
* **Device Compliance:**
  * Conditional Access can require that users only access OneDrive from compliant, managed devices. This ensures that only secure devices are used to handle sensitive data, reducing the risk of data breaches from compromised devices.
* **Session Controls:**
  * Administrators can apply session controls that restrict the actions users can take during a session. For instance, users accessing OneDrive from a public network may be allowed to view files but not download or share them.

### **Integration with Microsoft Defender for Cloud Apps**

OneDrive integrates with **Microsoft Defender for Cloud Apps** to provide advanced threat protection and monitoring capabilities.

* **Anomaly Detection:**
  * Defender for Cloud Apps monitors for anomalous behaviors, such as impossible travel (e.g., a user logging in from two distant locations within a short time frame), mass file downloads, or abnormal sharing patterns.
* **Risk Scoring:**
  * Defender for Cloud Apps assigns risk scores to users based on their behavior. High-risk users can be automatically flagged for further investigation, and their access to OneDrive can be restricted until the investigation is complete.
* **Automated Governance Actions:**
  * Based on defined policies, Defender for Cloud Apps can take automated actions in response to threats, such as revoking file sharing permissions, blocking user sessions, or forcing a password reset.
