# Threat Detection

## **Overview of Threat Detection in Microsoft 365**

Microsoft Cloud App Security (MCAS) provides real-time threat detection capabilities to help identify and respond to potential threats within Microsoft 365 services like Exchange Online, SharePoint, OneDrive, and Teams. These capabilities are critical in protecting users and data from external attacks, insider threats, and misconfigurations that could lead to breaches.

**Key Threat Detection Capabilities**

* **Activity Monitoring**: Detects abnormal user behaviors and potential security incidents, such as suspicious sign-ins, excessive downloads, or sharing of sensitive files.
* **Behavioral Analytics**: Uses machine learning to understand user behaviors and detect anomalies, such as impossible travel scenarios or high-risk activities.
* **Data Loss Prevention (DLP)**: Identifies and responds to sensitive data being shared or exposed, either internally or externally.
* **Integration with Microsoft Defender for Office 365**: Strengthens email protection by detecting phishing, malware, and other email-based attacks.

### **Detecting Common Threats in Microsoft 365**

MCAS offers several built-in detections that help monitor the most common types of threats in Microsoft 365. These detections are designed to recognize suspicious behavior across various Microsoft 365 services and trigger alerts that help prevent security incidents.

**Common Threat Detections in Microsoft 365**

1. **Phishing Attacks**:
   * Phishing attacks are one of the most common entry points for attackers into Microsoft 365. MCAS detects suspicious inbox rules, unusual email forwarding, and potential malware attachments that bypass initial email security.
   * Example: MCAS detects an unusual inbox forwarding rule that automatically sends emails to an external email address, potentially indicating a phishing compromise.
2. **Impossible Travel**:
   * MCAS can detect impossible travel scenarios where a user is logged in from two geographically distant locations in a short period, suggesting that the account may have been compromised.
   * Example: A user logs in from New York and, an hour later, logs in from Europe, triggering an impossible travel alert.
3. **Mass Download of Files**:
   * This detection identifies scenarios where a user downloads an unusually large number of files from SharePoint or OneDrive, which could be an indicator of a data exfiltration attempt.
   * Example: A user downloads hundreds of files in a short period from OneDrive after hours, raising suspicion.
4. **External Sharing of Sensitive Files**:
   * MCAS detects when sensitive files, such as those labeled with confidentiality tags, are shared externally with unauthorized users or domains.
   * Example: A user shares a document marked as confidential with an external partner, triggering an alert for potential data leakage.

**Creating Custom Threat Detections**

While MCAS offers many built-in detections, organizations can create custom threat detections tailored to their specific needs:

1. **Define the Detection Scope**: Specify the Microsoft 365 services you want to monitor (e.g., OneDrive, Teams).
2. **Set Detection Rules**: Establish conditions to monitor (e.g., detecting logins from blacklisted IP addresses or unusual file access patterns).
3. **Response Actions**: Determine the automatic response, such as blocking user access, alerting the security team, or restricting file sharing.

### **Real-Time Monitoring and Alerts for Microsoft 365**

MCAS provides real-time monitoring and alerting capabilities, helping security teams quickly detect and respond to suspicious activities across Microsoft 365 services. Alerts can be generated based on policy violations, unusual user behaviors, or automated risk scoring.

**Setting Up Real-Time Alerts**

1. **Configuring Alerts**: Customize alert thresholds for different Microsoft 365 activities, such as abnormal login patterns, file sharing, or mass file deletions.
   * Example: You can set alerts for any user logging into SharePoint from an untrusted location.
2. **Severity Levels**: Assign severity levels to alerts based on the potential risk (low, medium, high), allowing your security team to prioritize the most critical incidents.
3. **Integration with SIEM Solutions**: MCAS alerts can be integrated with Microsoft Sentinel or other Security Information and Event Management (SIEM) solutions for centralized threat monitoring.

### **Investigating Alerts in MCAS**

When an alert is triggered, it’s important to follow a structured investigation process:

1. **Review Activity Logs**: MCAS provides detailed logs showing user actions leading up to and following the alert. These logs are critical for understanding the full scope of the potential threat.
2. **Cross-Check with Microsoft 365 Data**: Correlate the MCAS alert with additional data from Microsoft 365 services, such as sign-in logs from Azure AD, to gain more context.
3. **Take Action**: Depending on the severity of the alert, you can manually or automatically respond by blocking user sessions, resetting passwords, or quarantining files.

### **Automated Response and Workflow Management in Microsoft 365**

One of the key benefits of using MCAS is the ability to automate responses to detected threats. By automating certain workflows, organizations can reduce response times and prevent incidents from escalating.

**Automating Threat Responses**

MCAS allows you to set automated responses to common threats in Microsoft 365:

1. **Automated User Lockout**: Automatically block or log out users if suspicious behavior is detected, such as an impossible travel scenario or an unauthorized login attempt from an untrusted location.
   * Example: A user logging in from multiple countries within a short period is automatically logged out of Microsoft 365 until further investigation is completed.
2. **File Quarantine**: Automatically quarantine files that are suspected of being involved in a data breach, or prevent their sharing until they are reviewed.
   * Example: A confidential file shared externally is automatically blocked from download or access until security reviews the incident.

### **Customizing Automated Playbooks**

Organizations can also create automated playbooks using Microsoft Sentinel or Azure Logic Apps to streamline incident response workflows:

1. **Incident Classification**: Automatically classify incidents based on specific attributes (e.g., user risk level, type of file involved, or geographical location).
2. **Automated Remediation**: Set up automated remediation steps, such as resetting compromised user passwords, restricting access to certain apps, or revoking OAuth app permissions.

### **Integration with Microsoft Defender for Office 365**

MCAS integrates seamlessly with Microsoft Defender for Office 365 to enhance threat detection across email and collaboration tools:

* **Phishing and Malware Protection**: By combining MCAS with Defender for Office 365, organizations can detect and block phishing attempts, malware attachments, and other email-based attacks before they compromise user accounts.
* **End-to-End Threat Protection**: The integration allows for more comprehensive threat monitoring, correlating email activity with other suspicious behaviors across Microsoft 365, such as unusual file sharing or logins.

**Example: Email Account Compromise Detection**

* **Problem**: A user’s Exchange Online account is compromised via a phishing email, and the attacker sets inbox rules to forward emails to an external address.
* **Solution**: Defender for Office 365 detects the phishing email and blocks the malicious attachment. Meanwhile, MCAS identifies the suspicious forwarding rule and automatically blocks it while alerting the security team.

### **Incident Response Playbook for Microsoft 365 Threats**

Creating an incident response playbook helps organizations respond quickly and effectively to threats detected within Microsoft 365. The playbook should outline the steps for identifying, investigating, and responding to incidents in a structured manner.

**Steps in an Incident Response Playbook**

1. **Identification**: Use MCAS to detect and classify the type of threat (e.g., account compromise, data exfiltration, external sharing).
2. **Containment**: Depending on the severity of the threat, take immediate actions to contain the incident (e.g., blocking user access or quarantining files).
3. **Investigation**: Analyze MCAS logs and alerts to understand the scope of the incident. This includes cross-referencing data from Microsoft 365 apps and Azure AD.
4. **Eradication**: Remove the threat by resetting compromised accounts, removing malware, or revoking access to unauthorized users.
5. **Recovery**: Restore normal operations by verifying that the threat is eliminated and ensuring users have access to necessary resources.
6. **Post-Incident Analysis**: Review the incident to identify gaps in security policies and improve response strategies moving forward.
