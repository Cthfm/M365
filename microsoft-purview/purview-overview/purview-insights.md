# Purview Insights

## **Overview**

Microsoft Purview Insights offers dashboards and reports that provide a comprehensive view of your organization’s data governance posture, including the classification and usage of sensitive data. For threat hunters, Purview Insights serves as a vital tool to detect anomalies, monitor compliance, and identify potential threats related to data access and usage. In this lesson, you will learn how to set up and customize Purview Insights to aid in your threat hunting efforts.

### **What is Microsoft Purview Insights?**

Microsoft **Purview Insights** provides a detailed, real-time overview of your organization’s data estate. It includes dashboards and reports that highlight key metrics such as:

* **Data classification**: What percentage of your data is classified or unclassified, and how data is being labeled.
* **Sensitive data monitoring**: Activity and usage patterns for sensitive data (e.g., PII, confidential information).
* **Data access trends**: How frequently and by whom data is being accessed, modified, or shared.
* **Compliance posture**: How well your organization adheres to policies such as GDPR, HIPAA, or internal data governance rules.

For threat hunters, Purview Insights offers crucial information on where potential security issues may arise, such as unusual access to sensitive data or non-compliance with data protection policies.

### **Setting Up Purview Insights**

To get started with Microsoft Purview Insights, you’ll first need to configure your Purview account to capture the necessary data and enable insights. Here’s how to set it up:

**Step 1: Accessing Purview Insights**

* In the **Microsoft Purview portal**, navigate to the **Insights** section on the main dashboard.
* If this is your first time setting up insights, you’ll be prompted to configure certain aspects of your data environment to enable comprehensive monitoring.

**Step 2: Configure Data Sources for Insights**

Purview Insights can gather data from a variety of sources, including cloud storage, databases, on-premises systems, and more. To ensure you’re getting the most out of Insights, make sure the following are configured:

* **Register Data Sources**: Ensure that all critical data sources (such as Azure Storage, SQL databases, and SharePoint) are registered and scanned within Purview.
* **Enable Data Classification**: Set up automatic or manual data classification to ensure that sensitive information is properly labeled.
* **Enable Auditing**: Configure auditing for sensitive data to track access patterns, modifications, and other activity. This enables Purview Insights to provide meaningful analysis on data usage and security.

**Step 3: Configure Permissions**

To ensure the right team members have access to Insights, configure user permissions appropriately:

* Assign **Data Reader** roles to security analysts or threat hunters who need access to the Insights dashboard but do not need to modify data sources.
* Assign **Data Contributor** or **Administrator** roles to users who need full access to modify or manage the configuration of insights.

### **Exploring Purview Insights Dashboards**

Once your data sources are configured, you’ll be able to access a variety of built-in dashboards in the Purview portal. These dashboards provide visibility into several key areas of your data estate.

**Key Dashboards in Purview Insights:**

1. **Data Classification Overview**
   * This dashboard shows a breakdown of your organization’s classified vs. unclassified data.
   * You’ll see which sensitivity labels (e.g., Confidential, Internal, PII) are being applied and to which assets.
   * For threat hunters, this overview helps you prioritize efforts around monitoring sensitive data.
2. **Sensitive Data Activity**
   * This dashboard tracks activity related to sensitive data. You’ll see how frequently sensitive data is being accessed, modified, or shared.
   * You can filter by specific sensitivity labels, such as PII, to narrow down the data types that are most critical.
   * The activity section helps identify unusual access patterns that could indicate insider threats or data leakage.
3. **Data Access Trends**
   * Here, you’ll find a timeline of data access activities, including which users, groups, or systems are interacting with sensitive data.
   * This helps detect anomalies, such as spikes in access from unexpected users or locations.
   * For threat hunting, this dashboard helps you spot patterns in data usage that could signal a potential security incident.
4. **Compliance Dashboard**
   * This dashboard focuses on compliance with industry standards and internal governance policies. It shows whether sensitive data is being stored, shared, and accessed according to compliance requirements (e.g., GDPR, HIPAA).
   * You’ll also see any violations of data policies, such as unauthorized access or unencrypted sensitive data.

### **Customizing Insights for Threat Hunting**

Purview Insights can be customized to focus on the metrics that matter most to your threat hunting efforts. You can create custom views, set up alerts, and drill down into specific data points.

**Step 1: Customizing Dashboards**

To tailor the dashboards to your organization’s needs:

* **Add or remove metrics**: Customize the existing dashboards by adding or removing specific metrics. For example, you can add a chart that focuses on access to a particular sensitivity label, such as **Highly Confidential**.
* **Set date ranges**: Adjust the date ranges on the dashboards to track activity over a specific period, such as the past 30 days or the last quarter.

**Step 2: Creating Custom Insights**

Purview allows you to create custom insights based on specific criteria relevant to your threat hunting activities:

* **Create custom queries**: Use filters to narrow down the focus of your insights. For example, create a query that shows all activity related to a specific data source or user group.
* **Monitor specific data types**: If you are focused on protecting customer PII, configure custom insights to monitor access and activity specific to that data type.

**Step 3: Set Up Alerts for Anomalies**

Alerts in Purview Insights are critical for proactively detecting and responding to potential security threats:

* **Define alert triggers**: Set up alerts for unusual data activity, such as when sensitive data is accessed outside of normal working hours, or when large amounts of data are accessed in a short period.
* **Configure notifications**: Ensure that the right team members receive notifications when alerts are triggered. Alerts can be configured to notify via email, or integrated into a broader security monitoring solution like Microsoft Sentinel.

### **Using Purview Insights for Threat Hunting**

Once Purview Insights is fully configured, you can leverage it to streamline your threat hunting efforts and quickly identify security risks related to data activity.

**Monitoring for Anomalous Activity**

* **Detect unusual data access**: If a sensitivity label such as **Confidential** is accessed by an unexpected user or system, it could indicate a security breach or insider threat.
* **Spot spikes in data usage**: Sudden spikes in access to specific sensitive data could signal a data exfiltration attempt, especially if it involves downloading or copying large amounts of information.

**Identifying Policy Violations**

Purview Insights helps you detect violations of internal data governance policies:

* **DLP policy violations**: If sensitive data is shared outside of authorized groups or systems, Purview Insights can flag this as a potential data leak.
* **Non-compliance with encryption policies**: Insights can highlight instances where sensitive data is not being properly encrypted or stored in compliance with regulatory requirements.

**Tracking Data Access Over Time**

Use Purview Insights to build a timeline of data access:

* This timeline can be used to investigate incidents by seeing who accessed specific sensitive data and when.
* It also helps identify patterns of data usage, allowing you to track whether the same users are repeatedly accessing sensitive data in suspicious ways.

### **Best Practices for Using Purview Insights in Threat Hunting**

1. **Regularly Review Dashboards**: Make it a habit to regularly check the Purview Insights dashboards for any signs of unusual activity or potential security incidents.
2. **Set Up Alerts for Critical Data**: Configure alerts for the most sensitive or high-risk data, ensuring that your team is immediately notified of any suspicious behavior.
3. **Correlate Insights with Other Security Tools**: Integrate Purview Insights with tools like Microsoft Sentinel to correlate data activity with broader network or endpoint security events. This provides a more complete picture of potential threats.
4. **Drill Down Into Anomalies**: Don’t just rely on the high-level metrics. Use the drill-down features in Purview Insights to investigate specific incidents and gather the details you need for a thorough threat hunt.
