# Sharepoint: Advanced Hunting

## **Using Microsoft Sentinel for SharePoint Online**

Microsoft Sentinel is a powerful cloud-native Security Information and Event Management (SIEM) solution that can be used to monitor, detect, and respond to threats in SharePoint Online. In this section, we will explore how to leverage Sentinel for advanced threat hunting and automation.

**1. Configuring Sentinel to Monitor SharePoint Online Logs**

To integrate SharePoint Online with Microsoft Sentinel, you'll need to configure data connectors that can pull relevant logs and activities for analysis. This setup allows you to centralize your security monitoring across multiple Microsoft 365 services.

**Steps to Configure Sentinel for SharePoint Online:**

1. **Data Connector Setup:** Navigate to the **Sentinel Data Connectors** and select the **Microsoft 365** connector to start ingesting logs from SharePoint Online.
2. **Select Log Types:** Choose the types of logs you want to import from SharePoint, such as file access, sharing events, and permission changes.
3. **Set Up Automation Rules:** Create rules to automatically respond to certain activities (e.g., auto-revoke external sharing links if suspicious sharing is detected).

**2. Building Custom Workbooks and Dashboards in Sentinel**

Workbooks in Microsoft Sentinel allow you to visualize your SharePoint security data through custom dashboards, providing real-time insights into user behavior and potential threats.

**Key Metrics to Monitor in SharePoint Online:**

* **File Access Patterns:** Track high-volume file access or unusual access to sensitive documents.
* **External Sharing Activities:** Monitor sharing links, especially those shared with external users.
* **Permission Changes:** Identify users who are modifying permissions frequently or unexpectedly.

**Example Workbook:**

* **Data Sources:** Unified Audit Log, File Access Logs, External Sharing Logs
* **Visualizations:** Graphs tracking spikes in external sharing, tables summarizing permission changes by user, and alerts highlighting suspicious IPs accessing SharePoint.

**3. Automating Threat Detection with Sentinel**

Sentinel allows you to automate responses to potential threats, reducing manual workload and improving response times.

**Using KQL Queries for Automation:**

* Write KQL queries to identify suspicious activities, such as data exfiltration or privilege escalation, and use them to trigger automated responses.

**Sample KQL Query for Automated Detection:**

```kusto
AuditLogs
| where RecordType == "SharePoint"
| where Operation == "FileAccessed"
| where FileSensitivityLabel == "Confidential"
| where ClientIP != "InternalNetwork"
| summarize AccessCount = count() by UserId, ClientIP
| where AccessCount > 10
```

This query identifies users accessing confidential files from external IPs, which could indicate data exfiltration. You can configure Sentinel to automatically trigger a playbook that blocks the user's account and sends an alert to the security team.

**4. Sentinel Playbooks for Automated Responses**

Playbooks in Sentinel allow you to define automatic actions based on detected threats. You can integrate these playbooks with alerts to automatically respond to suspicious activities.

**Example Playbook:**

* **Trigger:** Detection of external sharing of confidential documents.
* **Action:** Automatically revoke the sharing link, block the user’s account, and notify the security team via email or SMS.

By automating responses, you can significantly reduce the time it takes to contain threats and mitigate potential damage.

### **Integrating Third-Party Security Solutions**

In addition to Microsoft Sentinel and Defender for Office 365, third-party security tools can enhance your threat detection and response capabilities in SharePoint Online. Integration with SIEM or SOAR (Security Orchestration, Automation, and Response) platforms allows for more comprehensive monitoring.

**1. Integrating SIEM Tools with SharePoint Online**

Some organizations prefer to use external SIEM solutions in addition to Microsoft Sentinel. These SIEM tools can ingest logs from SharePoint Online and provide additional capabilities such as advanced correlation, machine learning, and threat intelligence.

**Common SIEM Integrations:**

* **Splunk:** SharePoint Online logs can be ingested into Splunk for custom reporting, real-time monitoring, and alerting.
* **QRadar:** IBM’s QRadar can integrate with SharePoint to detect advanced threats and run automated responses.

By integrating with these platforms, you can extend your visibility into security events and enhance your ability to detect complex threats.

**2. Enhancing Incident Response with SOAR Tools**

Security Orchestration, Automation, and Response (SOAR) platforms provide automation capabilities that can complement your SharePoint Online security strategy. SOAR tools can automate complex workflows, coordinate across multiple security tools, and provide faster incident resolution.

**Best Practices for SOAR in SharePoint Online:**

* **Automated Incident Workflows:** Use SOAR platforms to automate threat hunting, incident triage, and response across multiple security solutions.
* **Integrating with Playbooks:** Build playbooks that coordinate actions across Sentinel, Defender, and external tools to respond to incidents in a coordinated manner.

### **Building Dashboards for SharePoint Security**

Dashboards provide critical visibility into your SharePoint Online environment. They allow you to track key metrics, monitor user activity, and visualize trends that could indicate a security breach.

**1. Key Metrics and KPIs for Monitoring SharePoint Online**

When building security dashboards, it's important to focus on the metrics and KPIs that align with your threat hunting goals.

**Key Metrics to Monitor:**

* **File Access Activity:** Track the volume and types of files being accessed, focusing on spikes or unusual access patterns.
* **External Sharing Events:** Monitor who is sharing files externally and how often, especially for sensitive data.
* **Permission Changes:** Keep an eye on permissions modifications, particularly changes to administrative privileges or sensitive document libraries.

**Example KPIs:**

* **Average Number of External Sharing Events per User:** A high value could indicate increased risk of data leakage.
* **Percentage of Files Labeled as Sensitive Accessed by External IPs:** This helps identify potential data exfiltration attempts.
* **Number of Unauthorized Permission Changes:** Tracks administrative actions that may indicate an insider threat or compromised account.

**2. Visualizing Suspicious Activity and Trends**

Creating dashboards that highlight suspicious trends makes it easier for security teams to identify patterns that may require further investigation.

**Example Dashboard Visualizations:**

* **Heatmaps for File Access:** Highlight days or times when file access spikes, indicating unusual activity.
* **Bar Graphs for External Sharing:** Show the volume of files shared with external parties, categorized by sensitivity level.
* **Line Graphs for Permission Changes:** Track changes in file or folder permissions over time to detect anomalies.

These visualizations provide a quick overview of the security posture in SharePoint Online and help security teams focus on high-priority events.

**3. Creating Reports for Stakeholders**

In addition to dashboards, generating reports for key stakeholders is essential for ensuring security policies are followed and vulnerabilities are addressed. Reports should summarize key incidents, trends, and mitigation steps taken.

### **Best Practices for Security Reporting:**

* **Tailor Reports to Your Audience:** For executive teams, focus on high-level KPIs and risk factors. For IT teams, provide more detailed insights into specific incidents and trends.
* **Automate Reporting:** Set up automated reporting workflows in Sentinel or Power BI to generate regular security summaries and incident reviews.
