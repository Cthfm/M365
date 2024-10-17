# Enable UAL

## Overview

Audit logging is **enabled by default** in Microsoft 365 organizations. However, if you are setting up a **new Microsoft 365 organization**, it’s important to verify whether auditing is active. This article provides step-by-step instructions for verifying, enabling, or disabling auditing, and highlights key considerations to ensure compliance with your organization’s policies.

When auditing is active, **user and admin activities** are recorded and stored in the **audit log**. These records are retained for up to **180 days**, although retention policies and user licensing can affect this duration.

{% hint style="warning" %}
The default retention for **Audit (Standard)** logs was updated from **90 days to 180 days** for logs generated on or after October 17, 2023. Logs generated before this date will retain the old 90-day limit.
{% endhint %}

Turning off auditing has significant consequences, including the inability to access logs via the **Office 365 Management Activity API**, **Microsoft Sentinel**, or PowerShell.

### Before You Enable or Disable Auditing

To modify auditing settings, you must have the **Audit Logs** role in **Exchange Online**. By default, this role is assigned to the **Compliance Management** and **Organization Management** groups on the **Permissions** page of the Exchange Admin Center.

* **Reference:**
  * Search the Audit Log
  * Get Started with Microsoft 365 Management APIs

### How to Verify Auditing Status

To confirm whether auditing is enabled, run the following command in **Exchange Online PowerShell**:

```powershell
Get-AdminAuditLogConfig | Format-List UnifiedAuditLogIngestionEnabled
```

* **Output:**
  * **True:** Auditing is enabled
  * **False:** Auditing is not enabled

{% hint style="info" %}
This command must be run in **Exchange Online PowerShell**. If executed in **Security & Compliance PowerShell**, the property will always return **False** even if auditing is enabled.
{% endhint %}

### Turn On Auditing

If auditing is not active, you can enable it via the **Microsoft Purview portal**, **Compliance portal**, or **Exchange Online PowerShell**.

#### Enabling Auditing via the Purview Portal

1. **Sign in** to the Microsoft Purview Portal.
2. Select the **Audit** solution card.
   * If it's not visible, click **View all solutions** and choose **Audit** from the **Core** section.
3. If auditing is not enabled, a **banner** will prompt you to start recording activities.
4. Click **Start recording user and admin activity**.

{% hint style="info" %}
**Note:** It may take **up to 60 minutes** for the changes to take effect.
{% endhint %}

#### Enabling Auditing via Compliance Portal

1. In the Microsoft Purview compliance portal at [https://compliance.microsoft.com](https://compliance.microsoft.com/), go to **Solutions** > **Audit**. Or to go directly to the **Audit** page, use [https://compliance.microsoft.com/auditlogsearch](https://compliance.microsoft.com/auditlogsearch).
2. If auditing isn't turned on for your organization, a banner is displayed prompting you start recording user and admin activity.
3. Select the **Start recording user and admin activity** banner.

{% hint style="info" %}
**Note:** It may take **up to 60 minutes** for the changes to take effect.
{% endhint %}

### Enable Auditing via PowerShell

1. **Connect** to Exchange Online PowerShell.
2.  Run the following command to enable auditing:

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
    ```
3. A message will confirm that the change may take up to **60 minutes** to become effective.

### Turn Off Auditing

To disable auditing, use **Exchange Online PowerShell**. This process removes the ability to retrieve audit data for your organization.

1. **Connect** to Exchange Online PowerShell.
2.  Run the following command:

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
    ```
3.  Verify that auditing is turned off using one of the following methods:

    **Method 1:** Run this PowerShell command:

    ```powershell
    Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
    ```

    * **False** indicates that auditing is disabled.

    **Method 2:** Go to the **Audit** page in the Compliance Portal.

    * If auditing is off, a **banner** will prompt you to enable it.

{% hint style="danger" %}
Disabling auditing prevents access to logs through the **Microsoft Purview portal**, **Microsoft Sentinel**, and the **Search-UnifiedAuditLog** cmdlet.
{% endhint %}

### Audit Records of Changes to Auditing Status

Changes to your organization’s auditing status are also logged in the audit records. You can search the **Exchange admin audit log** to see when auditing was enabled or disabled, who made the change, and from which IP address.

To search for these events, run the following command:

```powershell
Search-UnifiedAuditLog -Operations Set-AdminAuditLogConfig
```

* **Audit Record Details:**
  * **Confirm** value in the **CmdletParameters** field indicates that auditing was turned **on**.
  * If **Confirm** is absent, auditing was turned **off**.
