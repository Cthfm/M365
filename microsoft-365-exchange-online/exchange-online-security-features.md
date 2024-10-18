# Exchange Online: Security Features

## Overview

Email is a critical communication tool for organizations, often storing valuable data. To ensure proper use, organizations should establish messaging policies that govern usage, outline user behavior, and address any restricted communication types. Policies should also manage the email lifecycle, ensure retention for legal and regulatory reasons, and preserve emails for litigation and eDiscovery.

Sensitive information, such as intellectual property and personal data, must be safeguarded to prevent leaks.

**Key Security and Compliance Features:**

1. **Archive Mailboxes:** In-Place Archiving offers additional storage for users, accessible via Outlook.
2. **Litigation Hold:** Preserves mailbox content for compliance and eDiscovery.
3. **Inactive Mailboxes:** Maintains deleted mailbox data indefinitely using In-Place or Litigation Hold.
4. **Data Loss Prevention (DLP):** Identifies and monitors sensitive information like credit card or ID numbers, blocking unauthorized transmissions.
5. **Auditing:** Tracks configuration changes and mailbox access by non-owners, viewable via reports.
6. **Messaging Records Management (MRM):** Helps manage email lifecycle, archiving, and deletion according to business needs.
7. **Information Rights Management (IRM):** Controls who can access, forward, or print sensitive data within emails.
8. **Message Encryption:** Encrypts emails sent both inside and outside the organization, allowing recipients to send encrypted replies.
9. **S/MIME:** Provides signed and encrypted emails for secure internal communication.
10. **Journaling:** Logs inbound and outbound email communications for compliance purposes.
11. **Mail Flow Rules (Transport Rules):** Allows actions on messages based on predefined conditions, such as blocking or holding messages for review.

### **Anti-Phishing Policies**

Anti-phishing policies in Exchange Online help prevent users from falling victim to phishing attacks. These policies analyze email behavior and content to detect and block phishing emails.

**Key Features of Anti-Phishing Policies:**

* **Impersonation Protection:**
  * This feature identifies and blocks attempts to impersonate trusted senders, such as executives or partners, in phishing emails.
  * **Threat Hunting Insight:** Monitoring impersonation-related detections helps identify targeted phishing campaigns (e.g., executive spoofing or business email compromise).
* **User-Reported Phishing Detection:**
  * Users can report suspicious emails directly to Microsoft through the Report Message add-in. This creates an immediate alert for further analysis.
  * **Threat Hunting Insight:** User-reported phishing attempts provide valuable insights into potential attacks, allowing hunters to correlate reported messages with broader campaign indicators.

### **Anti-Spam Policies**

Anti-spam policies are designed to filter out unsolicited and potentially harmful messages from reaching users' inboxes. These policies are based on heuristic analysis, content filtering, and real-time spam protection updates.

**Key Features of Anti-Spam Policies:**

* **Content Filtering:**
  * Examines the body of emails for spam-like characteristics, including excessive use of certain keywords, images, or unusual formatting.
* **Spam Quarantine:**
  * Suspicious emails are sent to a quarantine folder for review by administrators. This provides an extra layer of protection for high-confidence spam or potentially dangerous emails.
  * **Threat Hunting Insight:** Quarantine analysis can reveal whether specific users are being targeted by spam campaigns, helping identify social engineering or low-level phishing attempts.

### **Role-Based Access Control (RBAC)**

RBAC is a key administrative feature within Exchange Online that ensures only authorized personnel can make changes to mailboxes, policies, and other critical components of the service.

**Key Features of Role-Based Access Control:**

* **Admin Roles:**
  * Admins can assign specific permissions to users or groups based on roles, such as the Exchange administrator, compliance officer, or security officer. This limits what actions users can perform, helping reduce the risk of insider threats or privilege abuse.
* **Mail Flow Permissions**
  * Control which users can create or modify transport rules, forwarding rules, and message trace permissions.

**Threat Hunting Insight:**

* **Tracking Admin Changes:** Reviewing changes made by high-privileged accounts can help identify potential insider threats or unauthorized activity.
* **Monitoring Permission Changes:** Monitoring updates to RBAC policies or user roles can reveal signs of privilege escalation by malicious actors.
