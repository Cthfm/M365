# Deploying Microsoft Cloud App Security

## **Deployment Overview: Setting Up MCAS for Microsoft 365**

To secure Microsoft 365 environments using Microsoft Cloud App Security (MCAS), the first step is to properly deploy and configure MCAS. This involves connecting the relevant Microsoft 365 apps (such as Exchange Online, SharePoint, OneDrive, and Teams) to the MCAS platform.

### **Steps to Deploy MCAS for Microsoft 365**

1. **Access the MCAS Portal**:
   * Navigate to the MCAS portal via the Microsoft 365 admin center or through a direct link. You will need admin permissions for your Microsoft 365 tenant to make configuration changes.
2. **Onboard Microsoft 365 Apps**:
   * **Automatically connect Microsoft 365 apps**: By default, Microsoft Cloud App Security automatically connects to Microsoft 365 apps (Exchange Online, SharePoint, OneDrive, and Teams). No additional setup is required for these integrations.
   * **Manually connecting other apps**: For third-party or custom apps that require monitoring within Microsoft 365, you can manually configure them in the "Connected apps" section.
3. **Set Up Cloud Discovery**:
   * Cloud Discovery is a critical feature that provides visibility into the applications being accessed within your Microsoft 365 tenant.
   * **Enabling Cloud Discovery for Microsoft 365**:
     * Upload firewall and proxy logs from your network infrastructure to identify unsanctioned apps (Shadow IT).
     * Enable continuous log collection for real-time monitoring of app usage across the organization.
   * **Analyzing Shadow IT**: MCAS helps track non-sanctioned apps in the organization, providing insights into potential security risks.
4. **Configuring Admin Permissions**:
   * Ensure that necessary permissions are granted to MCAS for access to Microsoft 365 services.
   * Use Azure Active Directory (AAD) roles to assign admin privileges to specific users responsible for configuring MCAS.

### **Configuring MCAS with Microsoft 365 Applications**

Once MCAS is deployed, you’ll need to ensure it is properly configured to monitor specific Microsoft 365 applications.

**Integrating Exchange Online with MCAS**

* **Monitoring Email Activities**:
  * Enable monitoring of user activities related to email security, such as abnormal login attempts or suspicious email forwarding rules.
* **Phishing Protection**:
  * Utilize built-in alerts to detect phishing emails that bypassed initial protection, leveraging integration with Microsoft Defender for Office 365.

**Integrating SharePoint and OneDrive with MCAS**

* **File Monitoring and Data Protection**:
  * Configure MCAS to monitor file sharing and access within SharePoint and OneDrive. MCAS can detect and block unauthorized sharing of sensitive files.
* **Versioning and Encryption Protection**:
  * Detect ransomware attacks by monitoring encryption and abnormal file versioning behaviors in OneDrive and SharePoint document libraries.

**Integrating Teams with MCAS**

* **Monitoring Team Chats and File Sharing**:
  * MCAS enables activity monitoring within Teams, identifying suspicious behaviors such as mass file downloads or unauthorized external sharing.
* **Collaboration Security**:
  * Apply policies that monitor and control external sharing and access to Microsoft Teams data.

### **Enabling Continuous Cloud Discovery for Microsoft 365 Apps**

Continuous Cloud Discovery is essential for maintaining up-to-date visibility on how apps are being used within your organization.

**Continuous Log Collection**

* **Automating Log Collection**:
  * Set up continuous log collection for Microsoft 365 services. This allows MCAS to automatically pull logs from your Microsoft 365 environment and analyze them for potential threats and unsanctioned app usage.
* **Data Sources**:
  * Logs from Microsoft 365 apps like Exchange, SharePoint, OneDrive, and Teams are automatically ingested, while logs from firewalls and proxies may need to be configured for ingestion.

**Shadow IT Discovery**

* **Analyzing Non-Sanctioned App Usage**:
  * Use the Cloud Discovery feature to monitor usage of unsanctioned apps that employees might be using outside of Microsoft 365. This helps identify risks from external applications that could compromise data.
* **Evaluating Risk Scores**:
  * MCAS assigns risk scores to detected apps based on factors like compliance, security certifications, and industry standards. These scores help in decision-making for app approval or blocking.

### **Configuring MCAS Alerts for Microsoft 365**

Setting up alerts is crucial for timely detection and response to threats or policy violations within Microsoft 365. MCAS provides customizable alerts based on user activity, data sharing, or policy violations.

**Configuring Built-In Alerts**

* MCAS comes with built-in alerts that you can enable for quick detection of common issues:
  * **Suspicious Inbox Rules**: Detects if an attacker has set forwarding rules to exfiltrate emails.
  * **Impossible Travel Alerts**: Flags when a user appears to log in from geographically distant locations within a short time frame.
  * **Mass Download Alerts**: Detects when a user downloads an unusually large volume of files from OneDrive or SharePoint.

**Creating Custom Alerts**

* You can create custom alerts tailored to your organization’s specific security needs, such as:
  * Monitoring external sharing of confidential documents.
  * Alerting on unusual file access patterns within Teams and SharePoint.

### **Securing Admin and User Sessions in Microsoft 365**

Session controls help monitor and manage active sessions for Microsoft 365 apps, providing administrators with the ability to enforce security measures in real-time.

**Session Policy Configuration**

* **Real-Time Session Controls**:
  * MCAS allows you to apply session policies that control how users interact with Microsoft 365 apps in real-time. This includes blocking or restricting access based on location, device, or user behavior.
  * Example: A user accessing SharePoint from an untrusted device could be allowed read-only access or fully blocked from accessing sensitive files.
* **Integration with Conditional Access**:
  * Use Azure Active Directory Conditional Access to enforce session controls based on factors like user risk level, device security, or location.

### **Testing Your MCAS Deployment**

Before going live, it’s crucial to test your MCAS deployment within Microsoft 365 to ensure that policies, alerts, and session controls are working correctly.

**Running Simulated Attacks**

* **Phishing and Account Takeover Simulations**:
  * Use Microsoft’s Attack Simulator or other tools to test how MCAS responds to phishing emails, suspicious logins, or attempted data exfiltration.
* **File Sharing Simulations**:
  * Simulate unauthorized sharing of sensitive files within OneDrive and SharePoint to test your DLP policies.

**Reviewing Alerts and Logs**

* Once simulations are complete, review alerts, logs, and the actions taken by MCAS to ensure everything is configured properly for real-world usage.
