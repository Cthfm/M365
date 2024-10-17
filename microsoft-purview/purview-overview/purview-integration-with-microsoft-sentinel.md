# Purview Integration with Microsoft Sentinel

#### **Integrating Microsoft Purview with Microsoft Sentinel**

***

**Overview**

Integrating Microsoft Purview with **Microsoft Sentinel**, a cloud-native security information and event management (SIEM) solution, allows you to combine data governance insights with broader threat detection and response capabilities. This integration enhances your ability to correlate data access events from Purview with other security signals, providing a more comprehensive view of potential security threats across your environment. In this lesson, we’ll cover how to set up the integration between Microsoft Purview and Sentinel and how to leverage this integration for advanced threat hunting and incident response.

***

#### **1. Why Integrate Microsoft Purview with Microsoft Sentinel?**

Integrating Microsoft Purview with Microsoft Sentinel provides several key benefits for threat hunters and security analysts. Purview focuses on data governance and provides detailed insights into sensitive data access and classification, while Sentinel collects and correlates security events across your entire environment, including network traffic, endpoints, and cloud services.

**Key benefits of the integration:**

* **Unified Threat Detection**: Sentinel can correlate Purview’s data access logs with other security signals (e.g., network anomalies, endpoint activity) to detect potential security incidents such as insider threats, data exfiltration, or malicious access attempts.
* **Advanced Analytics**: Sentinel’s built-in machine learning and threat detection capabilities can be applied to Purview audit logs to identify suspicious patterns and raise alerts.
* **Comprehensive Incident Response**: By integrating Purview data access insights into Sentinel’s incident response workflows, security teams can investigate and respond to incidents with a more complete picture of what occurred.

***

#### **2. Setting Up the Integration Between Purview and Sentinel**

To start leveraging Microsoft Sentinel with Microsoft Purview, you’ll need to configure the integration between the two services. This involves connecting your Purview account to Sentinel and setting up data ingestion for audit logs and insights.

**Step 1: Ensure Prerequisites**

Before you can integrate Purview with Sentinel, ensure that:

* You have an active **Microsoft Purview** account with audit logging enabled.
* You have a **Microsoft Sentinel** workspace set up in your Azure environment.
* You have the appropriate permissions to manage both Purview and Sentinel resources (typically **Security Administrator** or **Data Contributor** roles).

**Step 2: Configure Data Connectors in Microsoft Sentinel**

Microsoft Sentinel uses **Data Connectors** to bring in logs and data from various sources, including Purview. Here’s how to configure the data connector for Purview:

1. In the **Microsoft Sentinel** portal, navigate to your Sentinel workspace.
2. Go to **Data Connectors** and search for "Microsoft Purview."
3. Select the **Microsoft Purview Data Connector** and click **Open Connector Page**.
4. Follow the instructions to authenticate and connect your Microsoft Purview environment to Sentinel.

Once the connector is set up, Sentinel will start ingesting data from Purview, including audit logs and sensitive data access events.

**Step 3: Configure Log Ingestion**

You’ll need to configure which specific logs from Microsoft Purview will be ingested into Sentinel. The primary logs to focus on include:

* **Audit Logs**: These logs capture all access, modification, and sharing events related to sensitive data.
* **Data Activity Logs**: Logs that track data movement, including transfers, copies, and exports of classified data.

By ingesting these logs, Sentinel will have visibility into critical data access activities, enabling advanced analytics and alerting.

***

#### **3. Monitoring Purview Data in Microsoft Sentinel**

Once Purview data is flowing into Sentinel, you can start using Sentinel’s powerful monitoring, analysis, and threat detection features to correlate data access events with other security signals.

**Step 1: Build Queries in Sentinel**

Microsoft Sentinel uses **Kusto Query Language (KQL)** to query and analyze data. Here’s how you can build basic queries to monitor Purview-related activities:

*   **Query for Data Access Events**:

    ```kql
    kqlCopy codePurviewAuditLogs
    | where EventAction == "DataAccess"
    | where SensitivityLabel == "Confidential" or SensitivityLabel == "HighlyConfidential"
    | summarize Count = count() by UserPrincipalName, DataAsset, Timestamp
    | order by Timestamp desc
    ```

    This query returns recent data access events for sensitive data, helping you track which users have accessed confidential information.
*   **Query for Data Policy Violations**:

    ```kql
    kqlCopy codePurviewAuditLogs
    | where EventAction == "PolicyViolation"
    | summarize Count = count() by UserPrincipalName, ViolationType, Timestamp
    | order by Timestamp desc
    ```

    This query helps you monitor for policy violations, such as unauthorized access or data sharing.

**Step 2: Set Up Alerts for Critical Events**

In Sentinel, you can create **alerts** to notify your security team of critical events based on the queries you’ve built. For example, you can configure alerts for:

* **Unauthorized access attempts**: Trigger an alert when a user without permission attempts to access data labeled as "Confidential."
* **Sensitive data exports**: Trigger an alert if data labeled "PII" or "Financial" is downloaded or exported outside the organization.

Here’s how to set up an alert:

1. Navigate to **Analytics** in Sentinel and select **Create Alert Rule**.
2. Choose the **query** you built to monitor specific Purview events.
3. Define the conditions under which the alert should trigger (e.g., whenever an unauthorized access event occurs).
4. Configure notifications to ensure the right team members are alerted.

**Step 3: Correlate Purview Data with Other Security Events**

One of the key advantages of integrating Purview with Sentinel is the ability to correlate data access events with broader security signals. For example:

* If a user accesses sensitive data and shortly after, there’s a suspicious login attempt from an unusual location, this could indicate a compromised account or insider threat.
* Correlate Purview data movement logs with network traffic patterns to detect large data transfers that may signal data exfiltration.

Use Sentinel’s **Fusion detection** and **correlation rules** to combine insights from different sources (network, endpoint, cloud services) for a more comprehensive analysis.

***

#### **4. Leveraging Sentinel’s Incident Response Capabilities**

Microsoft Sentinel offers advanced incident management features that allow you to investigate and respond to security incidents in real time. By integrating Purview’s data access insights, you can enrich your incident response process with detailed data governance information.

**Step 1: Investigate Incidents**

When an alert is triggered, you can drill down into the incident to gather more information. Here’s how to investigate an incident in Sentinel:

1. Go to the **Incidents** tab in Sentinel and select the incident triggered by a Purview-related alert.
2. Review the **Timeline** of events leading up to the incident, including data access logs from Purview.
3. Analyze the **Entities** involved in the incident (e.g., users, IP addresses, data assets) to determine the scope and severity.

**Step 2: Take Action with Playbooks**

Sentinel allows you to automate incident response using **Playbooks**. Playbooks are workflows that automatically trigger actions when an alert is raised. For example:

* If unauthorized access to sensitive data is detected, a playbook could automatically block the user’s account and send a notification to the security team.
* If a data export policy is violated, the playbook could revoke access to the data source and initiate an investigation.

Here’s how to create a Playbook:

1. In Sentinel, navigate to **Playbooks** and select **Create Playbook**.
2. Define the actions that should be taken when an alert is triggered (e.g., disabling user accounts, notifying administrators).
3. Connect the Playbook to the relevant Purview alert to ensure it automatically triggers in response to the event.

***

#### **5. Best Practices for Using Purview with Sentinel**

1. **Correlate Multiple Data Sources**: Use Sentinel to combine Purview audit logs with other security signals, such as network traffic, endpoint activity, or identity logs, for a more holistic view of potential threats.
2. **Automate Response Actions**: Take advantage of Sentinel’s Playbooks to automate responses to Purview-related incidents, ensuring faster and more consistent remediation.
3. **Use Custom Queries**: Build custom KQL queries in Sentinel to track the specific data access patterns and policy violations that are most relevant to your organization’s security posture.
4. **Set Thresholds for Alerts**: Ensure you configure meaningful thresholds for alerts, such as flagging multiple unauthorized access attempts within a short time period, to avoid alert fatigue while still catching potential incidents.
