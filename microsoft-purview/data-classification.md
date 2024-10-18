# Data Classification

## **Overview**

Data classification is a foundational element in any data governance strategy, especially when it comes to threat hunting. In this lesson, we will explore how Microsoft Purview uses data classification to help security teams manage sensitive information, prioritize their threat hunting efforts, and reduce the risk of data breaches. By the end of this lesson, you’ll understand the basics of data classification in Purview and how it can be leveraged for improved security visibility.



## **What is Data Classification?**

**Data classification** is the process of organizing data into categories based on predefined characteristics such as sensitivity, importance, or regulatory requirements. In Microsoft Purview, classification plays a critical role in both data governance and threat hunting by allowing organizations to label and protect sensitive data, ensuring it is properly managed throughout its lifecycle.

Data can be classified based on several factors:

* **Sensitivity**: How confidential or critical the data is (e.g., PII, financial data, intellectual property).
* **Regulatory Compliance**: Whether the data is subject to legal or regulatory requirements (e.g., GDPR, HIPAA).
* **Business Value**: The importance of the data to business operations (e.g., strategic plans, customer contracts).

By classifying data, threat hunters can easily identify high-risk assets, enabling a more focused and efficient investigation.

## **Why Data Classification is Essential for Threat Hunting**

For threat hunters, knowing where sensitive or critical data resides is crucial in identifying potential security threats. Without proper classification, organizations may overlook key data assets that could be vulnerable to insider threats, data exfiltration, or ransomware attacks.

Here’s how data classification helps threat hunters:

* **Prioritizing Investigations**: With data classified by sensitivity, threat hunters can focus on the most critical data first, ensuring that any breach or suspicious activity involving highly sensitive data is prioritized.
* **Detecting Unauthorized Access**: Classifications allow you to monitor and flag access to sensitive data by unauthorized users. This helps detect insider threats or external attackers trying to access high-value assets.
* **Ensuring Compliance**: By classifying data in accordance with regulatory requirements, threat hunters can ensure that sensitive data is being handled properly and that any violations of compliance (such as unauthorized access) are quickly detected.

## **How Data Classification Works in Microsoft Purview**

Microsoft Purview offers several built-in tools and capabilities that make data classification easy and efficient. It automatically scans, discovers, and classifies data across various data sources, including Azure and on-premises repositories.

**Types of Classifications in Purview:**

1.  **System Classifications**: These are predefined data classifications that are built into Microsoft Purview. They include common types like:

    * Personally Identifiable Information (PII)
    * Credit Card Information (PCI)
    * Health Records (HIPAA)
    * Financial Information (SOX)

    These system classifications help you quickly label commonly regulated or sensitive data in your organization.
2. **Custom Classifications**: If your organization has specific needs, you can create custom data classifications based on unique patterns or rules. For example:
   * Custom labels for proprietary business information.
   * Custom patterns for industry-specific compliance.
3. **Sensitive Information Types**: Microsoft Purview also supports the creation of **Sensitive Information Types**, which allow you to define patterns or keywords to automatically classify data. This can be done by:
   * Using built-in sensitive information types (e.g., EU passport number, U.S. Social Security number).
   * Defining custom types (e.g., a specific customer ID format or product code unique to your business).

## **Applying Data Classifications in Microsoft Purview**

**Step 1: Scanning Data Sources**

Before you can apply classifications, you need to scan your connected data sources to identify and catalog the data stored within them. Here’s how:

* In the Purview portal, navigate to **Data Map** and select the **Scan** option for your registered data sources (e.g., Azure SQL, ADLS).
* Configure the scan to identify specific types of data (such as sensitive data or high-value business assets).
* Once the scan is complete, Purview will automatically classify the data based on predefined or custom classification rules.

**Step 2: Managing Classifications**

After the data is scanned, Purview will display the classification results. You can:

* **View classified assets**: Navigate to the **Assets** tab to see the list of classified assets. Here, you’ll see which assets have been automatically labeled as containing sensitive or regulated information.
* **Manually classify assets**: If necessary, you can manually classify data assets by selecting them and applying the appropriate sensitivity labels.
* **Edit or update classifications**: Purview allows you to modify existing classifications or reclassify assets as data governance needs evolve.

**Step 3: Monitoring Classified Data**

Once your data is classified, you can use Purview to continuously monitor classified assets for:

* **Unauthorized access attempts**: Using audit logs and activity insights, you can detect when classified data is accessed by unauthorized users or in unusual ways.
* **Policy enforcement**: Purview ensures that your organization’s data governance policies are applied correctly, restricting access to sensitive or high-value data to only authorized personnel.

## **Real-World Example of Threat Hunting with Data Classification**

Let’s walk through a real-world example where data classification can enhance threat hunting efforts.

**Scenario:** Your organization stores sensitive customer information (PII) in an Azure SQL Database. You’ve classified the customer data using Microsoft Purview’s built-in **PII** classification. Recently, your security team detected unusual activity on the Azure SQL Database—an employee has accessed a large amount of customer data during off-hours.

**Steps:**

1. **Investigate the Classification**: Navigate to the classified PII data in Purview and review its access history through the audit logs. Check if the employee's access aligns with their role and responsibilities.
2. **Analyze the Access Patterns**: Use Purview’s activity insights to detect if this access pattern is part of a broader trend or if it’s an isolated incident. Look for any other sensitive data that the employee may have accessed.
3. **Set up an Alert**: If this activity is deemed suspicious, you can configure custom alerts to notify the security team whenever classified data is accessed outside of normal working hours or by unauthorized individuals.
4. **Take Action**: Based on your findings, you may decide to revoke the employee’s access, perform further investigations, or escalate the incident if you suspect malicious intent.

## **Best Practices for Data Classification in Threat Hunting**

1. **Classify Data Early and Often**: Make data classification a core part of your data governance strategy. The earlier you classify sensitive data, the easier it will be to monitor and protect it.
2. **Automate Classification**: Use Purview’s automated scanning and classification capabilities to reduce the workload on your security team. Automation helps ensure that data is consistently classified as new data sources and assets are added.
3. **Review and Update Classifications Regularly**: Data governance is not a one-time activity. Regularly review your data classifications to ensure they remain accurate and relevant, especially as your organization’s data landscape evolves.
4. **Leverage Classification for Compliance**: Use data classification to enforce compliance with regulatory requirements. Purview can automatically classify and flag data that must adhere to GDPR, HIPAA, or other regulations, ensuring proper handling and security.
