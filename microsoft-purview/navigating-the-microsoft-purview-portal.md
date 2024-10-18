# Navigating the Microsoft Purview Portal

## Overview

Once your Purview account is set up and data sources are connected, you’ll want to familiarize yourself with the key components of the Purview portal. This section introduces the core areas you’ll interact with regularly.&#x20;

### **Data Map**

The **Data Map** is the core feature of Microsoft Purview, providing a real-time view of your organization’s data estate. It automatically discovers, scans, and classifies data from the connected sources. The Data Map allows you to:

* Visualize how data flows through your organization.
* Identify key data assets and their relationships.
* Discover sensitive data locations for focused threat hunting.

As a threat hunter, you’ll rely on the Data Map to understand where your most sensitive data is stored and identify potential attack surfaces.

### **Assets**

In Purview, **Assets** represent individual data items or entities within your connected data sources, such as tables, files, or databases. Each asset can have specific metadata and classifications attached to it. From the **Assets** tab, you can:

* Browse or search through your organization’s assets.
* View detailed metadata for each asset, including classification, sensitivity, and ownership.
* Tag assets with labels such as **PII** (Personally Identifiable Information) or **Confidential** to ensure proper tracking and governance.

Tracking assets and their classifications is critical when identifying high-value targets for threat hunting.

### **Classifications**

The **Classifications** feature in Purview allows you to apply predefined or custom labels to your data, such as “Confidential,” “Finance,” or “Customer Data.” These labels enable:

* **Automatic Data Labeling**: Purview can automatically scan data for specific patterns (like credit card numbers or social security numbers) and apply the appropriate classification.
* **Custom Classifications**: You can also create custom classifications based on your organization’s unique data governance requirements.

These classifications will become a critical part of your threat hunting activities, allowing you to quickly identify sensitive data at risk of exposure.

### **Insights**

Purview provides **Insights** dashboards that summarize key data governance metrics. These dashboards allow you to:

* Monitor data access patterns across your environment.
* View a breakdown of classifications and sensitive data locations.
* Identify potential policy violations or non-compliance risks.

Insights give threat hunters a bird’s-eye view of potential security issues, making it easier to focus on areas that might be under threat.

### **Key Initial Configurations for Threat Hunting**

Once you’ve familiarized yourself with the basic features of Microsoft Purview, it’s important to set up a few initial configurations to get the most out of your threat hunting efforts:

**Configure Sensitivity Labels**

Incorporate **sensitivity labels** to classify your data based on how sensitive it is. Start by applying these labels to your most critical data sources, such as financial data or personal identifiable information (PII).

**Enable Audit Logging**

Make sure **audit logging** is enabled for each of your registered data sources. This will allow you to track all user access and activity on your data, providing an essential layer of visibility when hunting for threats.

**Set Up Alerts for Anomalous Activity**

As a threat hunter, it’s important to set up automated alerts for any unusual data access patterns or policy violations. You can create custom policies within Purview to notify your security team whenever sensitive data is accessed in unexpected ways.
