# Auditing With Purview

## **Overview**

Auditing is a core capability in Microsoft Purview that allows organizations to monitor and log data activity across their entire data estate. For threat hunters, audit logs provide detailed insights into who accessed sensitive data, when it was accessed, and what actions were performed. This lesson will explore how to configure auditing in Microsoft Purview, review audit logs, and use these logs for threat hunting and incident response.

### **What is Auditing in Microsoft Purview?**

Auditing in Microsoft Purview involves logging all data-related activities, such as who accessed, modified, shared, or deleted data assets. These logs provide a detailed history of user interactions with data, enabling organizations to track data usage and detect any unauthorized or suspicious activity.

**Key functions of auditing include:**

* **Tracking user activity**: Logs who accessed or interacted with specific data assets.
* **Monitoring data access patterns**: Auditing reveals when and how frequently data is accessed, allowing you to identify unusual patterns.
* **Detecting potential threats**: Audit logs can be used to spot data exfiltration, unauthorized access, or insider threats by showing what actions were taken on sensitive data.

For threat hunters, audit logs are essential in reconstructing the timeline of events during an investigation and uncovering potential security breaches.

### **Configuring Auditing in Microsoft Purview**

To effectively use auditing for threat hunting, you need to ensure that audit logging is enabled and properly configured in Microsoft Purview. This involves setting up auditing for all relevant data sources and defining what actions should be logged.

**Step 1: Enable Audit Logging for Data Sources**

Audit logging needs to be configured for each data source you want to monitor. Here’s how to enable it:

* In the **Purview portal**, navigate to the **Data Map** and select the data source you want to audit (e.g., Azure SQL Database, Azure Storage, etc.).
* Under the data source settings, locate the **Auditing** section and toggle the auditing feature on.
* Configure which events you want to log, such as:
  * **Read actions**: Who viewed or accessed data.
  * **Write actions**: Who modified, added, or deleted data.
  * **Export actions**: Any data that was exported or shared outside of approved channels.

For threat hunters, it’s essential to audit all actions related to sensitive data, including any attempts to modify or exfiltrate data.

**Step 2: Define Retention Policies**

Once auditing is enabled, define how long audit logs should be retained:

* **Short-term retention**: Logs that cover the last 30–90 days are useful for immediate investigations and ongoing monitoring.
* **Long-term retention**: Keeping logs for a year or more is helpful for compliance purposes and conducting thorough historical investigations.

By configuring retention policies, you can ensure that audit logs remain available for as long as necessary to support incident response or legal investigations.

### **Reviewing and Interpreting Audit Logs**

Once audit logging is enabled, you can start reviewing the logs to identify potential threats or suspicious activities. Purview provides tools for accessing and interpreting audit logs.

**Step 1: Accessing Audit Logs**

You can access the audit logs in Purview by navigating to the **Insights** section or the **Audit Log** tab for each data source.

* **Search**: Use the search functionality to look up specific events, such as access to a particular file or database.
* **Filter**: Apply filters to narrow down logs based on criteria like user, time range, or action type (e.g., read, write, delete).

**Step 2: Interpreting Key Events**

The following are key audit events that threat hunters should focus on:

* **Unauthorized Access Attempts**: Look for failed access attempts to sensitive data by users or systems that shouldn’t have permissions. This can indicate an attack attempt or account compromise.
* **Unusual Data Access**: Sudden or unusual access to sensitive data by users who typically don’t interact with that data may suggest malicious intent.
* **Data Modifications**: Track changes made to sensitive data, especially if these modifications were made outside of normal business hours or by unexpected users.
* **Data Export or Sharing**: Logs showing data being exported or shared with external parties are potential red flags for data exfiltration or breaches.

By focusing on these events, threat hunters can detect signs of compromise and gather evidence for further investigation.

**Step 3: Investigating Suspicious Activity**

Once you’ve identified suspicious activity in the audit logs, you can drill down into the details:

* **Review the timeline**: Look at the sequence of events leading up to the suspicious action. For example, was there an attempt to access data multiple times before success?
* **Correlate with user behavior**: Compare the suspicious activity with the user’s regular behavior. Are they accessing data they typically wouldn’t interact with, or from an unusual location?
* **Trace data movement**: Use audit logs to trace how sensitive data moved through your organization. Was it copied, transferred, or accessed from an external location?

These insights help you build a comprehensive understanding of the incident and determine whether further action is needed.

### **Leveraging Audit Logs for Threat Hunting**

Audit logs are a valuable resource for uncovering threats and investigating potential incidents. Here’s how you can use audit logs in your threat hunting workflow:

**Track High-Risk Users and Actions**

Set up monitoring for **high-risk users** or privileged accounts that have access to sensitive data. If these users perform unusual actions (e.g., accessing a sensitive file after hours), this could signal an insider threat or compromised credentials.

Additionally, track **high-risk actions** such as:

* **Downloading or copying large amounts of data**: This could indicate an attempt at data exfiltration.
* **Unauthorized data sharing**: If sensitive data is shared outside the organization, it could represent a data breach.

### **Detect Data Exfiltration Attempts**

Audit logs can help detect **data exfiltration** by showing how data is being accessed and transferred. For example:

* A user accesses large volumes of sensitive data and downloads or exports it to an external device.
* An unusual pattern of accessing sensitive data from an external IP address.

By reviewing audit logs for these activities, threat hunters can identify exfiltration attempts before significant damage occurs.

### **Investigate Data Breaches**

In the event of a data breach, audit logs provide a detailed timeline of how the incident unfolded. For example:

* **Entry point**: Use logs to identify how the attacker gained initial access to the data.
* **Data compromised**: Determine which sensitive data was accessed, modified, or exfiltrated.
* **User activity**: Analyze which users or systems were involved in the breach, helping you understand the scope of the incident.

By piecing together this information, you can respond to the breach and mitigate the impact.

### **Best Practices for Auditing with Microsoft Purview**

To get the most out of audit logging for threat hunting, follow these best practices:

1. **Enable Auditing on All Critical Data Sources**: Ensure that all data sources containing sensitive or business-critical information are configured for audit logging. This will provide full visibility into all interactions with important data.
2. **Focus on Sensitive Data**: Pay special attention to audit logs for sensitive or classified data. Set up alerts or reports that highlight any unusual activity related to this data.
3. **Regularly Review Logs**: Regularly review audit logs for signs of unusual or unauthorized activity. Automating these reviews with reports or alerts can help streamline this process.
4. **Correlate with Other Security Tools**: Integrate Purview audit logs with other security tools, such as Microsoft Sentinel, to correlate data access events with broader security incidents. This provides a more holistic view of potential threats.
5. **Respond to Alerts Immediately**: Set up real-time alerts for critical audit events, such as unauthorized access or large data transfers. Ensure your security team is ready to investigate and respond quickly to these alerts.
