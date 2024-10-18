# Microsoft 365: Tenant Setup

## Overview

The following are instructions to setup a M365 tenant as well as some recommended security settings to enable.&#x20;

### Instructions

To set up a Microsoft 365 (M365) tenant, follow these steps:

### 1. **Sign up for Microsoft 365**

* **Visit the Microsoft 365 page**: Go to [Microsoft 365](https://www.microsoft.com/en/microsoft-365).
* **Select a plan**: Choose the appropriate plan for your organization, such as Microsoft 365 Business, Enterprise, or Education.
* **Start free trial or purchase**: Click "Try free" or "Buy now" and follow the steps to sign up for an account. You'll need to provide some personal and business information, including your email address and contact details.

### 2. **Create a New Domain**

During the setup, you’ll be prompted to either:

* **Use an existing domain**: If your organization already has a domain (e.g., `companyname.com`), you can enter it here.
* **Create a new domain**: Microsoft also offers an option to create a temporary `onmicrosoft.com` domain (e.g., `yourcompany.onmicrosoft.com`), but it’s best to use your own domain for professional purposes.

After specifying your domain, you will need to verify ownership by updating the DNS records through your domain registrar (e.g., GoDaddy, Namecheap).

### 3. **Set Up the Tenant**

Once your domain is verified, your Microsoft 365 tenant is set up, and you can begin configuring it.

### 4. **Configure Users and Groups**

* **Add Users**: You can manually add users or use bulk upload options. Go to **Microsoft 365 Admin Center** (admin.microsoft.com) > **Users** > **Active users** > **Add a user**.
* **Create Security Groups**: Organize users into groups for easier management. This can be done under **Groups** > **Add a group**.

### 5. **Set Up Email (Exchange Online)**

If you’re using Microsoft 365 for email:

* **DNS Records Setup**: Update your domain’s DNS settings (MX, CNAME, and TXT records) through your domain registrar to point to Microsoft 365. Microsoft provides step-by-step instructions specific to your registrar during the setup.
* **Test Email**: Send test emails to ensure the configuration is correct.

### 6. **Configure SharePoint, OneDrive, and Teams**

* **SharePoint Online**: SharePoint will automatically be set up for document management and collaboration. You can start configuring sites for different departments or projects.
* **OneDrive**: Ensure that each user has access to OneDrive for personal file storage.
* **Microsoft Teams**: Enable Microsoft Teams for collaboration and communication. You can configure channels, teams, and permissions as needed.

### 7. **Secure Your Tenant**

* **Enable MFA (Multi-Factor Authentication)**: Enforce MFA for added security in your organization. You can do this in the **Microsoft 365 Admin Center** > **Active Users** > **Multi-factor authentication**.
* **Conditional Access**: Use Conditional Access to enforce policies for how and when users can access company resources.
* **Microsoft Defender for Office 365**: Consider enabling security features like Microsoft Defender to protect your environment from threats such as phishing or ransomware.

### 8. **Assign Licenses to Users**

Ensure that each user has the necessary licenses. Go to the **Admin Center** > **Billing** > **Licenses** and assign licenses to users.

### 9. **Set Up Policies and Compliance**

* **Data Loss Prevention (DLP)**: Configure DLP policies to protect sensitive information.
* **Retention Policies**: Set up retention policies for emails and files to comply with legal or company requirements.

### 10. **Configure Microsoft Entra ID (formerly Azure AD)**

* **User and Group Management**: Set up Entra ID to manage users, groups, and devices. You can configure additional security settings like Conditional Access here.
* **Self-service password reset**: Enable self-service password reset for users.

### 11. **Monitor and Maintain**

* **Audit Logs**: Enable and review audit logs regularly to monitor user activities.
* **Security Alerts**: Use Microsoft Defender for Cloud Apps to set up alerts for suspicious activities.
