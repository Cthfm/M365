# Mailbox Audit Logs

## **Mailbox Audit Logs**

Mailbox audit logs track actions that users or administrators perform on mailboxes, providing detailed visibility into email activities such as message deletions, reads, and forwarding.

### **What are Mailbox Audit Logs?**

* Mailbox audit logs capture user and admin activities related to specific mailboxes. These logs are essential for detecting unauthorized access or unusual activity in sensitive mailboxes.

### **Types of Activities Logged:**

* **SendAs and SendOnBehalf Actions:** Logs when a user sends an email on behalf of another user or using their mailbox.
* **Message Deletions:** Tracks when emails are soft-deleted (moved to the deleted items folder) or hard-deleted (permanently removed).
* **Mailbox Access by Delegates:** Captures when a delegate accesses a mailbox, reads messages, or takes other actions.
* **Message Forwarding:** Detects when a rule is set to forward messages to another email address.

### **How to Enable Mailbox Audit Logs:**

* Mailbox auditing is enabled by default for user mailboxes in Exchange Online, but auditing for certain events (e.g., admin access) might require manual configuration.
*   Example PowerShell cmdlet to enable mailbox auditing:

    ```powershell
    Set-Mailbox -Identity <user> -AuditEnabled $true
    ```

## **Seaching Mailbox Audit Logs:**

* You can use the **Audit Log Search** tool in the Security & Compliance Center or PowerShell to search mailbox audit logs.
*   Example PowerShell cmdlet to search mailbox audit logs:

    ```powershell
    Search-MailboxAuditLog -Mailbox <user> -LogonTypes Owner, Delegate, Admin
    ```

### **Threat Hunting Insight:**

* **Detecting Unauthorized Access:** Reviewing logs of who accessed sensitive mailboxes can help identify unauthorized users.
* **Tracking Suspicious Email Deletions:** High-volume email deletions could indicate an attempt to cover tracks during an insider threat or compromised account scenario.

### Reference

{% embed url="https://learn.microsoft.com/en-us/exchange/policy-and-compliance/mailbox-audit-logging/mailbox-audit-logging?view=exchserver-2019" %}
