# EOL Hunting: Business Email Compromise (BEC)

#### **Hunting for Business Email Compromise (BEC)**

Business Email Compromise (BEC) attacks are a sophisticated form of phishing, where attackers gain access to a legitimate user’s email account and use it to carry out fraudulent activities, often financial in nature.

**Key Topics:**

1. **Indicators of Business Email Compromise (BEC):**
   * **Unusual Login Locations:** Logins from unexpected IP addresses, geolocations, or devices.
   * **Forwarding Rules:** BEC attacks often involve setting up forwarding rules that automatically send emails to external addresses without the user’s knowledge.
   * **Spoofed Emails from Executives:** Attackers may send urgent requests for money transfers or sensitive information, impersonating senior leadership.
2. **Detecting BEC using Mailbox Audit Logs:**
   * Review mailbox audit logs for abnormal login activity, such as logins from locations where the legitimate user isn’t based.
   *   Example PowerShell command to check login activity:

       ```powershell
       powershellCopy codeSearch-MailboxAuditLog -Mailbox "executive@company.com" -LogonTypes Admin, Delegate, Owner
       ```
3. **Hunting for Unauthorized Forwarding Rules:**
   * Search for email forwarding rules created by unauthorized users.
   *   Example KQL query for detecting auto-forwarding rules:

       ```kusto
       kustoCopy codeAuditLogs 
       | where Operation == "Set-Mailbox"
       | where Parameters contains "ForwardingSMTPAddress"
       ```
4. **Monitoring Safe Links and Attachments for BEC:**
   * Review Safe Links and Safe Attachments activities to detect if compromised accounts were used to send phishing emails with dangerous links or attachments to other employees or external partners.
5. **Threat Hunting Insight:**
   * **Compromised Account Behavior:** Focus on mailboxes showing signs of account compromise, such as new forwarding rules, abnormal login locations, or attempts to send sensitive emails externally.
