# Sharepoint Online Powershell

## Overview

SharePoint Online PowerShell is a set of cmdlets for managing and automating tasks related to **SharePoint Online**, which is part of the Microsoft 365 ecosystem. These cmdlets offer administrative control over SharePoint sites, libraries, users, permissions, and content, allowing you to perform operations in bulk or automate routine tasks.

#### **Getting Started with SharePoint Online PowerShell**

1.  **Installing the SharePoint Online PowerShell Module**\
    To manage SharePoint Online with PowerShell, you need to install the **SharePoint Online Management Shell** or use **Microsoft.Online.SharePoint.PowerShell**:

    **Install the module from PowerShell Gallery**:

    ```powershell
    Install-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

    You may need to run PowerShell as an Administrator and allow `PSRepository` trust prompts.
2.  **Connecting to SharePoint Online**\
    You need to authenticate with SharePoint Online to perform administrative tasks.

    **Connect to a tenant:**

    ```powershell
    $adminUrl = "https://<tenant>-admin.sharepoint.com"
    Connect-SPOService -Url $adminUrl -Credential (Get-Credential)
    ```


3. Replace `<tenant>` with your organization’s tenant name. This prompts for your Microsoft 365  credentials.

{% embed url="https://learn.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online" %}

{% embed url="https://learn.microsoft.com/en-us/powershell/module/sharepoint-online/?view=sharepoint-ps" %}
