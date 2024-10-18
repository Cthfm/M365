# Sharepoint: Advanced Hunting

## **Building Dashboards for SharePoint Security**

Dashboards provide critical visibility into your SharePoint Online environment. They allow you to track key metrics, monitor user activity, and visualize trends that could indicate a security breach.

### **Key Metrics and KPIs for Monitoring SharePoint Online**

When building security dashboards, it's important to focus on the metrics and KPIs that align with your threat hunting goals.

**Key Metrics to Monitor:**

* **File Access Activity:** Track the volume and types of files being accessed, focusing on spikes or unusual access patterns.
* **External Sharing Events:** Monitor who is sharing files externally and how often, especially for sensitive data.
* **Permission Changes:** Keep an eye on permissions modifications, particularly changes to administrative privileges or sensitive document libraries.

**Example KPIs:**

* **Average Number of External Sharing Events per User:** A high value could indicate increased risk of data leakage.
* **Percentage of Files Labeled as Sensitive Accessed by External IPs:** This helps identify potential data exfiltration attempts.
* **Number of Unauthorized Permission Changes:** Tracks administrative actions that may indicate an insider threat or compromised account.

### **Visualizing Suspicious Activity and Trends**

Creating dashboards that highlight suspicious trends makes it easier for security teams to identify patterns that may require further investigation.

**Example Dashboard Visualizations:**

* **Heatmaps for File Access:** Highlight days or times when file access spikes, indicating unusual activity.
* **Bar Graphs for External Sharing:** Show the volume of files shared with external parties, categorized by sensitivity level.
* **Line Graphs for Permission Changes:** Track changes in file or folder permissions over time to detect anomalies.

These visualizations provide a quick overview of the security posture in SharePoint Online and help security teams focus on high-priority events.

### **Creating Reports for Stakeholders**

In addition to dashboards, generating reports for key stakeholders is essential for ensuring security policies are followed and vulnerabilities are addressed. Reports should summarize key incidents, trends, and mitigation steps taken.

### **Best Practices for Security Reporting:**

* **Tailor Reports to Your Audience:** For executive teams, focus on high-level KPIs and risk factors. For IT teams, provide more detailed insights into specific incidents and trends.
* **Automate Reporting:** Set up automated reporting workflows in Sentinel or Power BI to generate regular security summaries and incident reviews.
