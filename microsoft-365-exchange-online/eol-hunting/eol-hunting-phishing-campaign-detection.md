# EOL Hunting: Phishing Campaign Detection

#### **Detecting Phishing Campaigns in Exchange Online**

Phishing campaigns are a prevalent attack method in Exchange Online environments. As a threat hunter, it’s essential to identify phishing emails and the indicators that suggest phishing activities within an organization.

**Key Topics:**

1. **Phishing Indicators to Look For:**
   * **Suspicious Links and Attachments:** Phishing emails often contain malicious links or attachments designed to trick users into providing sensitive information or installing malware.
   * **Spoofed Email Addresses:** Attackers use domains or email addresses that closely resemble legitimate ones (e.g., "support@m1crosoft.com").
   * **Urgency and Threatening Language:** Phishing emails often create a sense of urgency (e.g., “Your account will be locked unless you update your credentials now”).
2. **Hunting for Phishing Emails Using Message Trace:**
   * Use **Message Trace** to follow the path of a phishing email through the organization.
   *   Example PowerShell command to trace emails sent by a suspicious sender:

       ```powershell
       Get-MessageTrace -SenderAddress "phishing-sender@malicious.com"
       ```
   * Review the details of delivered messages, recipients, and whether any messages were quarantined or blocked.
3. **Using Unified Audit Log for Phishing Detection:**
   * Search the **Unified Audit Log (UAL)** for activities such as users clicking on suspicious links or opening phishing attachments.
   *   Example PowerShell  query in the UAL to find if the user interacted with the message.

       ```powershell
       Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <username> -Operations MailItemsAccessed -ResultSize 1000
       ```
4. **Safe Links and Safe Attachments Insights:**
   * **Safe Links:** Tracks and reports when users click on potentially dangerous links in emails. Use threat explorer to investigate clicks that led to malicious URLs.
   * **Safe Attachments:** Monitors and quarantines suspicious email attachments before they are delivered to users.
5. **Threat Hunting Insight:**
   * **Phishing Campaign Spread:** Use message trace and audit logs to track the extent of a phishing campaign within the organization, identifying which users have been targeted and whether any have clicked on phishing links.
