# Exchange Admin Audit Logs

**Exchange Admin Audit Logs**

The Exchange Admin Audit Log tracks actions performed by Exchange administrators. It is especially important for monitoring changes to the configuration of mailboxes, transport rules, and organizational settings.

**Key Topics:**

1. **What are Exchange Admin Audit Logs?**
   * These logs record administrative actions performed by users with elevated permissions (e.g., Exchange admins or global admins) within the Exchange Online environment.
   * Admin audit logs track actions such as creating or deleting mailboxes, modifying transport rules, and adjusting anti-phishing policies.
2. **Types of Admin Activities Logged:**
   * **Mailbox Management:** Creation, deletion, and modification of user mailboxes.
   * **Transport Rule Changes:** Modifications to the organization’s email routing and spam filtering rules.
   * **Permissions Changes:** Granting or revoking permissions for users, groups, or mailboxes.
   * **Anti-Phishing Policy Updates:** Adjustments to spam filtering or impersonation protection settings.
3. **How to Access Exchange Admin Audit Logs:**
   * Admin audit logs can be accessed via the **Exchange Admin Center (EAC)** or by using PowerShell cmdlets.
   *   Example PowerShell cmdlet to retrieve admin audit logs:

       ```powershell
       Search-AdminAuditLog -Cmdlets Set-Mailbox, New-TransportRule
       ```
   * Filtering by date range or specific commands can help identify suspicious administrative activities.
4. **Threat Hunting Insight:**
   * **Unauthorized Admin Changes:** Reviewing admin actions can reveal unauthorized changes, such as adding mail forwarding rules or granting permissions to external users.
   * **Abuse of Privileges:** Detecting patterns of admin abuse, such as frequent modifications to mailboxes without proper authorization.

### Reference

{% embed url="https://learn.microsoft.com/en-us/exchange/policy-and-compliance/admin-audit-logging/admin-audit-logging?view=exchserver-2019" %}

