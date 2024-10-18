# Data Lineage

## **Overview**

Data lineage in Microsoft Purview provides a clear picture of how data flows through an organization, from its origin to its final destination. For threat hunters and incident responders, data lineage is a critical tool for investigating security incidents, as it helps trace the movement of sensitive data and identify potential points of compromise. This lesson explores how to use data lineage within Microsoft Purview to track data activity, uncover security vulnerabilities, and conduct incident investigations.

### **What is Data Lineage?**

**Data lineage** is the detailed record of data’s lifecycle, showing how it moves across different systems, applications, and users within an organization. In Microsoft Purview, data lineage allows organizations to visualize the flow of data from its creation, through transformations and processes, to its storage or final use.

**Key benefits of data lineage:**

* **Track data movement**: Identify how data moves between databases, applications, and services.
* **Visualize transformations**: See how data is transformed or processed as it moves through your organization.
* **Understand dependencies**: Discover how data in different systems is connected and dependent on other assets.

For threat hunters, data lineage helps answer critical questions during incident investigations, such as:

* Where did sensitive data originate from?
* Who accessed the data and when?
* How was the data transferred or shared between systems?

### **How Data Lineage Supports Incident Investigation**

Data lineage is especially valuable for investigating incidents involving data breaches, data exfiltration, or unauthorized access. It allows security teams to trace the flow of compromised data and determine how and where an attack might have occurred.

Here’s how data lineage supports incident investigations:

### **Identifying the Source of a Breach**

When a data breach occurs, the first question to answer is where the compromised data originated. Data lineage in Purview allows you to trace the breached data back to its source, whether it’s a database, file system, or cloud storage service.

**Tracing Data Movement**

If sensitive data was exfiltrated or moved to an unauthorized location, data lineage helps you trace its journey through your systems:

* **Movement across systems**: Did the data move between internal systems or external services?
* **User involvement**: Which users or systems had access to the data as it moved? Were there any suspicious actors involved?

By visualizing this data flow, you can pinpoint when and where the data was compromised, enabling you to take appropriate action.

**Detecting Transformation or Manipulation**

Data lineage also helps detect whether sensitive data was transformed or manipulated during its journey:

* **Was the data altered?**: Did any processes or applications modify the data as it moved through the environment?
* **Data integrity**: Ensuring that data wasn’t tampered with during its flow helps you maintain data integrity and uncover potential malicious behavior.

### **Navigating Data Lineage in Microsoft Purview**

Microsoft Purview provides an interactive view of data lineage that allows you to visualize how data moves across systems. Here’s how to navigate and use the lineage feature:

**Step 1: Accessing Data Lineage**

* In the **Purview portal**, navigate to the **Data Map** and select a specific data asset you’re interested in investigating.
* In the asset details, click on the **Lineage** tab to view the data’s journey through various systems, transformations, and processes.

**Step 2: Visualizing the Data Flow**

The data lineage view presents a visual map of how the selected data asset moves between systems. It includes:

* **Source systems**: Where the data originated (e.g., databases, storage accounts).
* **Processes**: Any transformations or modifications applied to the data.
* **Destinations**: Where the data was eventually stored, transferred, or used.

You can interact with the map to drill down into specific processes or systems to get more granular details about each step of the data’s journey.

**Step 3: Investigating User Access**

In addition to visualizing how data moves, you can also trace **user activity** related to the data. The lineage map will show which users or systems accessed the data at each stage, helping you identify whether an unauthorized user was involved in the incident.

### **Using Data Lineage to Identify Vulnerabilities**

Data lineage not only helps trace incidents but also allows you to proactively identify potential vulnerabilities in your organization’s data flow. Here’s how to use lineage for threat detection and vulnerability identification:

**Step 1: Spotting Unusual Data Movement**

Unexpected data movement can indicate a security threat, such as an insider threat or external attacker attempting to exfiltrate data. Use lineage to spot:

* **Unusual data transfers**: Look for data moving to external or unauthorized systems.
* **Inconsistent data flow**: Identify data flows that deviate from the organization’s typical data movement patterns.

**Step 2: Analyzing Data Dependencies**

Data lineage helps you understand how different systems and data assets depend on each other. A compromised system might expose sensitive data in connected systems:

* **Cross-system dependencies**: If one system in the data flow is vulnerable, it could expose sensitive data in other connected systems.
* **Application interactions**: Analyze how applications or processes interact with data and whether any of these interactions present security risks.

**Step 3: Identifying Bottlenecks or Choke Points**

Data lineage can reveal bottlenecks where data is being processed or transferred through a vulnerable system. These choke points are potential targets for attackers:

* **Concentrated data flow**: If large amounts of sensitive data pass through a single system or service, it could be a target for attackers.
* **System vulnerabilities**: Systems that play a critical role in the data flow should be regularly assessed for vulnerabilities.

### **Incident Investigation Workflow Using Data Lineage**

Let’s walk through a sample workflow for using data lineage to investigate a potential data breach:

**Scenario: Suspected Data Exfiltration**

Your security team has detected that sensitive financial data was accessed and potentially exfiltrated by an external party. You need to investigate the breach, trace the data’s movement, and identify the source of the attack.

**Step 1: Identify the Compromised Data Asset** In Microsoft Purview, navigate to the compromised financial data asset. Check its **Lineage** tab to visualize its data flow.

**Step 2: Trace the Data Flow** Use the data lineage view to trace how the data moved across systems:

* Identify the source where the data was created.
* Follow its journey through systems, databases, and applications.
* Note any unusual data transfers, especially to external or unauthorized systems.

**Step 3: Investigate User Access** Check the users and systems that interacted with the data at each stage:

* Look for unauthorized users or unexpected systems accessing the data.
* Investigate any unusual activity, such as data access at odd times or from external IP addresses.

**Step 4: Identify Potential Vulnerabilities** Examine the systems or processes involved in the data flow. Were any of these systems known to be vulnerable, or had they recently experienced security issues?

**Step 5: Respond to the Incident** Based on your findings, take appropriate action:

* Revoke access for unauthorized users.
* Secure vulnerable systems.
* Notify stakeholders of the breach and begin remediation.

### **Best Practices for Using Data Lineage in Threat Hunting**

To maximize the value of data lineage for incident investigation, follow these best practices:

1. **Regularly Review Data Lineage**: Don’t wait for an incident to occur. Regularly review the data flow in your organization to identify potential vulnerabilities before they’re exploited.
2. **Correlate with Audit Logs**: Use data lineage in conjunction with **audit logs** from Purview to get a complete picture of who accessed the data and how it moved through your systems.
3. **Set Alerts for Anomalies**: Use Purview to set up alerts for unusual data movements, such as sensitive data being transferred to unauthorized locations.
4. **Use Lineage for Compliance**: Ensure that sensitive data is flowing in compliance with internal policies and regulations, especially for highly regulated data like financial or healthcare information.
