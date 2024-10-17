# Policies

## **Understanding Policies in Microsoft Cloud App Security**

Policies in Microsoft Cloud App Security (MCAS) are the foundation for monitoring and controlling activities across Microsoft 365 apps like Exchange Online, SharePoint, OneDrive, and Teams. These policies help organizations detect and respond to threats, protect sensitive data, and enforce security protocols.

### **Types of Policies in MCAS**

MCAS offers several types of policies specifically designed to enhance security within Microsoft 365:

* **Activity Policies**: Monitor user behaviors and flag or block suspicious activities, such as mass file downloads or unusual sign-ins.
* **File Policies**: Track and control the sharing, access, and usage of files across OneDrive, SharePoint, and Teams.
* **Session Policies**: Control and monitor active user sessions, enabling real-time restriction of access to apps or data.

### **Activity Policies for Microsoft 365**

Activity policies are used to monitor and detect unusual or risky behaviors within Microsoft 365 services. These policies are essential for identifying account compromises, data exfiltration attempts, or other suspicious activities.

### **Common Activity Policies for Microsoft 365**

1. **Impossible Travel Activity**:
   * Detects when a user logs in from two different geographic locations in a timeframe that is impossible to travel between. This is a common sign of account compromise.
2. **Mass Download of Files**:
   * Monitors and flags when a user downloads a large volume of files from OneDrive or SharePoint. This could indicate potential data theft or ransomware activity.
3. **Unusual Login Activity**:
   * Tracks unusual login behavior, such as failed login attempts or logins from new devices or locations.
4. **Unusual File Sharing**:
   * Detects when files in SharePoint or OneDrive are being shared externally or with many users in a short period, which could indicate unauthorized file access.

### **Creating Custom Activity Policies**

* In MCAS, you can create custom activity policies based on your organization's needs:
  1. **Define a scope**: Choose the Microsoft 365 apps and activities you want to monitor (e.g., SharePoint uploads, OneDrive downloads).
  2. **Set conditions**: Define triggers for the activity policy, such as geographic location, file type, or user behavior.
  3. **Configure actions**: Decide whether the policy should generate an alert, block the activity, or initiate an automated response (e.g., log out the user).

### **File Policies for Data Protection in Microsoft 365**

File policies help protect sensitive data within Microsoft 365 apps, including SharePoint, OneDrive, and Teams. These policies ensure that unauthorized sharing or access to sensitive documents is detected and mitigated.

**Key File Policies for Microsoft 365**

1. **Confidential Files Shared Externally**:
   * Tracks files labeled as “confidential” and alerts administrators when these files are shared with external users or domains.
2. **Public Sharing of Files**:
   * Detects when files in OneDrive or SharePoint are made publicly accessible, preventing unintended data exposure.
3. **Sensitive Data Upload**:
   * Monitors for the upload of sensitive data (e.g., credit card information, Social Security numbers) into SharePoint or Teams channels, and triggers alerts or blocks the upload based on predefined DLP policies.

### **Creating Custom File Policies**

Creating custom file policies allows you to tailor protection to your organization's specific needs:

1. **Select a file type or location**: Choose the files or folders in OneDrive or SharePoint that need monitoring.
2. **Specify sensitivity labels**: Use Microsoft Information Protection (MIP) labels to define sensitive files (e.g., confidential or PII).
3. **Define actions**: Decide whether to alert, quarantine, or block file sharing.

### **Session Policies for Controlling Microsoft 365 Access**

Session policies allow organizations to control and restrict access to Microsoft 365 apps in real-time based on user behavior or risk level. These policies can be applied dynamically to block or limit actions like file downloads or external sharing based on the device, location, or user profile.

**Example Session Policies for Microsoft 365**

1. **Restrict Access from Untrusted Devices**:
   * Blocks access to sensitive files in SharePoint or OneDrive when users are logging in from untrusted devices.
2. **Limit External Sharing in Microsoft Teams**:
   * Prevents users from sharing files or adding external guests to Teams meetings from untrusted locations or devices.
3. **Enforce Read-Only Access**:
   * Enables read-only access to OneDrive or SharePoint files for users accessing data from risky networks (e.g., public Wi-Fi).

### **Configuring Session Policies**

* **Define session conditions**: Choose conditions like device type, IP address, location, or user behavior that will trigger the session policy.
* **Apply controls**: Set actions like read-only access, session termination, or file download blocking for sessions that match the policy conditions.
* **Monitor sessions**: Use real-time monitoring to watch for abnormal session behaviors and respond accordingly.

### **Enforcing Conditional Access and Session Controls in Microsoft 365**

To strengthen security, session policies can be combined with Conditional Access controls in Azure Active Directory (AAD). This integration allows you to enforce strict session controls for users based on their risk level, ensuring that only trusted devices and users can access critical Microsoft 365 data.

**Example Use Cases**

* **High-Risk Users**: Use Conditional Access to require Multi-Factor Authentication (MFA) for users deemed high-risk by Azure AD Identity Protection, while MCAS enforces session controls to block sensitive data access.
* **Unmanaged Devices**: Prevent users from downloading or editing files in OneDrive or SharePoint when accessing from unmanaged or non-corporate devices.

### **Real-World Application of Policies in Microsoft 365**

To see how these policies work in practice, here are real-world scenarios where MCAS policies provide protection within Microsoft 365:

**Scenario 1: Detecting Account Compromise in Exchange Online**

* **Problem**: A user’s account has been compromised, and the attacker is forwarding emails to an external address.
* **Solution**: An activity policy is triggered by the creation of suspicious inbox rules that forward emails. The policy generates an alert and automatically blocks the rule until the security team can investigate.

**Scenario 2: Protecting Sensitive Files in OneDrive**

* **Problem**: A confidential document is uploaded to a public folder in OneDrive and is shared externally.
* **Solution**: A file policy detects the public sharing of a file labeled as “confidential” and immediately revokes external access. An alert is also generated for the security team to follow up.

**Scenario 3: Limiting File Access from Untrusted Devices**

* **Problem**: An employee tries to download sensitive files from OneDrive using a personal device while traveling.
* **Solution**: A session policy limits the user’s access to read-only mode since they are on an untrusted device and network. File downloads are blocked until the user switches to a corporate device.
