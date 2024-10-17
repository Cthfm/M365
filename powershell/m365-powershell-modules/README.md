# M365 Powershell Modules

## Overview

The following is a list of Powershell modules that are utilized for M365.&#x20;

### 1. **Microsoft Graph PowerShell Module**

* **Module Name:** `Microsoft.Graph`
* **Purpose:** Allows interaction with Microsoft Graph API, which provides unified access to Microsoft 365 services.
*   **Usage Example:**

    ```powershell
    Connect-MgGraph -Scopes "User.Read.All"
    Get-MgUser -UserId user@domain.com
    ```
* **Key Features:** Unified access to Azure AD, Exchange, Teams, SharePoint, and more through a single API.

***

### 2. **Exchange Online PowerShell Module**

* **Module Name:** `ExchangeOnlineManagement` (also referred to as `EXO V2`)
* **Purpose:** Used for managing Exchange Online resources, mailboxes, and settings.
*   **Usage Example:**

    ```powershell
    Connect-ExchangeOnline -UserPrincipalName admin@domain.com
    Get-Mailbox -RecipientTypeDetails UserMailbox
    ```
* **Key Features:**
  * Supports modern authentication.
  * Used for email flow, mailbox permissions, and message trace activities.

***

### 3. **Microsoft Teams PowerShell Module**

* **Module Name:** `MicrosoftTeams`
* **Purpose:** Used for managing Microsoft Teams settings and policies.
*   **Usage Example:**

    ```powershell
    Connect-MicrosoftTeams
    Get-Team
    ```
* **Key Features:**
  * Manage Teams, channels, policies, and users.
  * Control guest access and Teams usage.

***

### 4. **SharePoint Online PowerShell Module**

* **Module Name:** `SharePointPnPPowerShell` (for PnP operations) and `Microsoft.Online.SharePoint.PowerShell`
* **Purpose:** Used for managing SharePoint Online sites, libraries, and permissions.
*   **Usage Example:**

    ```powershell
    Connect-PnPOnline -Url https://tenant.sharepoint.com
    Get-PnPSite
    ```
* **Key Features:**
  * PnP module provides enhanced capabilities for automation.
  * Manage document libraries, site collections, and access policies.

***

### 5. **Azure AD (Entra ID) PowerShell Module**

* **Module Name:** `AzureAD` (for legacy operations) and `AzureAD.Standard.Preview`
* **Purpose:** Used for managing Azure AD users, groups, and devices.
*   **Usage Example:**

    ```powershell
    Connect-AzureAD
    Get-AzureADUser -ObjectId user@domain.com
    ```
* **Key Features:**
  * Manage users and group memberships.
  * Enforce Conditional Access policies.

### 6. **Security & Compliance PowerShell Module**

* **Module Name:** `ExchangeOnlineManagement` (for compliance) and `Security & Compliance PowerShell`
* **Purpose:** Used for managing Microsoft 365 Security and Compliance settings, including DLP, audits, and eDiscovery.
*   **Usage Example:**

    ```powershell
    Connect-IPPSSession
    Get-ComplianceSearch
    ```
* **Key Features:**
  * Manage data loss prevention (DLP) policies.
  * Perform eDiscovery searches and manage audit logs.
