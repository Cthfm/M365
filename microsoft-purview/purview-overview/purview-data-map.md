# Purview Data Map

## **Overview**

The **Purview Data Map** is the heart of Microsoft Purview, providing an interactive, real-time view of your organization’s entire data estate. It allows you to track where data resides, how it moves through various systems, and how it is classified. For threat hunters, the Data Map serves as a crucial tool for visualizing sensitive data, discovering potential security gaps, and identifying vulnerabilities that could be exploited by malicious actors.

## **What is the Purview Data Map?**

The **Purview Data Map** is a dynamic map that provides visibility into the organization’s data assets, their classifications, and their relationships across various data sources. It automatically scans, catalogs, and classifies data from cloud and on-premises environments, allowing threat hunters to track sensitive data and its flow throughout the organization.

**Key functions of the Purview Data Map:**

* **Data Discovery**: The Data Map scans and catalogs all data assets, helping you locate sensitive information that may be at risk.
* **Data Classification**: It tags assets with sensitivity labels (e.g., confidential, financial) to help you prioritize threat hunting.
* **Data Lineage**: The Data Map shows how data moves between systems, providing valuable insight into where potential vulnerabilities exist.
* **Data Relationships**: It identifies how different data assets are connected, offering a broader understanding of how data flows through the organization.

By giving threat hunters a centralized view of the entire data estate, the Data Map helps ensure that no critical data is left unmonitored or unprotected.

## **How the Purview Data Map Supports Threat Hunting**

For threat hunters, the Purview Data Map is a powerful tool for discovering potential vulnerabilities and understanding how sensitive data is stored, accessed, and transferred across systems. The map provides several benefits in threat hunting, such as:

* **Identifying High-Risk Data**: By categorizing and labeling sensitive data (e.g., PII, intellectual property), the Data Map highlights the most critical assets for threat hunters to monitor.
* **Tracking Data Movement**: The map helps you see how data moves through your infrastructure, making it easier to detect data exfiltration attempts or unusual access patterns.
* **Detecting Misconfigurations**: Misconfigured access controls or data stores can lead to vulnerabilities. The Data Map helps you spot such weaknesses and address them before they are exploited.
* **Investigating Data Breaches**: If a data breach occurs, the Data Map’s lineage tracking allows you to trace the flow of compromised data and understand how the breach happened.

With real-time insights, the Purview Data Map enhances your ability to detect threats and respond to incidents before they escalate.

## **Navigating the Purview Data Map**

The Purview Data Map offers several views and features that help you explore, analyze, and manage your organization’s data. Here’s how to effectively navigate and use it.

**Step 1: Access the Data Map**

To access the Purview Data Map:

* In the Purview portal, navigate to the **Data Map** section.
* You’ll be presented with an overview of all the data sources and assets that Purview has scanned and cataloged.

The main dashboard provides a high-level summary of your data estate, showing the number of data sources, classified assets, and sensitive data.

**Step 2: Exploring Data Assets**

From the Data Map, you can drill down into specific data sources and explore the assets they contain. Here’s what you can do:

* **Search for Assets**: Use the search bar to locate specific data assets by name, type, or classification.
* **View Asset Details**: Click on an asset to view detailed metadata, including its classification, sensitivity labels, and the data source it belongs to.
* **Filter by Classification**: Filter assets by sensitivity labels to focus on high-risk data, such as confidential documents or customer information.

**Step 3: Analyzing Data Lineage**

One of the most powerful features of the Purview Data Map is its **Data Lineage** view, which shows how data flows between systems, applications, and users.

* **Track Data Movement**: By viewing data lineage, you can track how a particular asset has moved through your organization, from its point of origin to its current location. This helps you identify how data flows across systems and detect potential choke points or vulnerabilities.
* **Detect Unauthorized Transfers**: The lineage view can help you detect if sensitive data has been moved to an unapproved location, which could indicate a security incident or data leak.
* **Investigate Data Usage**: If a data breach occurs, you can use lineage to see where the compromised data came from and how it was used, aiding in incident response.

**Step 4: Discovering Data Relationships**

The Data Map also helps you understand how different assets are related, providing insight into:

* **Data Dependencies**: It shows dependencies between data assets, helping you identify critical links between systems. This is valuable for understanding how a breach in one area could impact other parts of your organization.
* **Data Access Patterns**: By analyzing relationships, you can identify unusual access patterns. For example, if sensitive data is accessed by a system or user that typically doesn’t interact with that data, this could be a sign of a security issue.

## **Using Data Map Insights for Threat Hunting**

The Purview Data Map provides several key insights that can support threat hunting efforts:

**Identify Vulnerable Data Sources**

Use the Data Map to pinpoint high-risk or vulnerable data sources. These might include:

* **Unclassified or Unlabeled Data**: Data that hasn’t been classified may not be adequately protected. Ensure that all critical data is tagged with sensitivity labels.
* **Misconfigured Data Stores**: Look for data sources that have weak or misconfigured access controls. These could be easy targets for attackers.

**Monitor Data Movement for Exfiltration Attempts**

Track how data flows through your organization and look for suspicious movements. For example:

* **Unexpected Data Transfers**: If sensitive data suddenly moves to a location outside of the organization or is accessed by an unknown entity, this could indicate an exfiltration attempt.
* **Cross-Boundary Data Flow**: Monitor data that crosses geographic or network boundaries. For example, data being transferred from on-premises systems to the cloud or from the EU to the U.S. could be a red flag.

**Detect Insider Threats**

The Data Map’s activity and lineage views can help detect insider threats by:

* **Unusual Access Patterns**: If an internal user accesses data that doesn’t align with their role or typical behavior, this may indicate a potential insider threat.
* **Abnormal Data Usage**: Large volumes of sensitive data being accessed or transferred in a short amount of time could signal suspicious activity.

## **Best Practices for Using the Purview Data Map**

To maximize the effectiveness of the Purview Data Map for threat hunting, follow these best practices:

1. **Regularly Scan Data Sources**: Ensure that your data sources are regularly scanned and updated within the Data Map. This keeps the map current and ensures you are monitoring the most up-to-date information.
2. **Review Data Lineage Regularly**: Analyze data lineage frequently to track data movement, especially for high-risk or sensitive data. Understanding how data flows between systems can reveal potential vulnerabilities.
3. **Set Alerts for Data Movements**: Use Purview to set up alerts for unusual data movements. For example, if sensitive data is transferred to a new, unauthorized location, you should be notified immediately.
4. **Integrate with Other Tools**: Integrate Purview with other Microsoft security tools like **Microsoft Sentinel** or **Defender for Cloud** to correlate data movement with broader network and security events.
5. **Focus on High-Risk Data**: Use sensitivity labels to prioritize your monitoring efforts. Ensure that all critical or confidential data is classified and that any unusual access to this data is investigated promptly.
