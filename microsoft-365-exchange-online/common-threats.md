# Common Threats

### **Overview:**

This section of the manual goes over Exchange Online common threats. This is not an exhaustive list but will get you started.

### **Phishing Attacks**

Phishing is one of the most common threats in any email service, and Exchange Online is no exception. Attackers send fraudulent emails to trick users into providing sensitive information or downloading malicious software.

**Key Topics:**

* **Definition:** Phishing involves sending emails that appear to be from a legitimate source, such as a bank or trusted colleague, to deceive recipients into taking harmful actions (e.g., clicking on a malicious link or downloading malware).
* **Spear Phishing:** A more targeted form of phishing where attackers focus on specific individuals or organizations. The email often contains highly personalized content, making it more convincing.
* **Whaling:** A type of spear phishing that targets high-level executives (e.g., CEOs, CFOs) with the goal of gaining access to sensitive corporate information or finances.
* **Indicators of Phishing:**
  * **Suspicious URLs:** Links that appear legitimate but redirect to malicious sites.
  * **Spoofed Sender Addresses:** Email addresses that appear similar to legitimate domains (e.g., “micros0ft.com” instead of “microsoft.com”).
  * **Urgency or Threats:** Emails that create a sense of urgency, demanding immediate action (e.g., "Your account has been compromised. Click here to reset your password").
  * **Unsolicited Attachments:** Emails with attachments that the recipient did not request or expect.

### **Business Email Compromise (BEC)**

Business Email Compromise is a sophisticated attack where an attacker gains control of a legitimate email account, often through phishing or brute force. Once they have access, they exploit the trust between the victim and their colleagues or external business partners to initiate fraudulent transactions or request sensitive information.

**Key Topics:**

* **Definition:** BEC occurs when an attacker compromises a business email account and impersonates the account owner to defraud the organization or its partners. Often, attackers focus on financial gain, such as wire transfer fraud.
* **Tactics:**
  * **Email Forwarding Rules:** Attackers may create rules that forward copies of all incoming emails to an external account without the user’s knowledge.
  * **Impersonation of Executives:** Attackers may pose as high-level executives requesting urgent financial transactions (e.g., CEO fraud).
  * **Invoice Scams:** Attackers send fraudulent invoices from compromised accounts to trick businesses into sending payments to attacker-controlled bank accounts.
* **Indicators of BEC:**
  * **Unusual Login Activity:** Logins from unfamiliar locations or devices.
  * **Unauthorized Email Rules:** Creation of email forwarding or deletion rules.
  * **Requests for Financial Transfers:** Unexpected or urgent requests to wire funds to new accounts, often targeting finance or HR departments.

### **Malware Delivery via Email**

Email is a primary vector for distributing malware, including ransomware, Trojans, and viruses. Attackers use malicious attachments or links within emails to compromise users' systems.

**Key Topics:**

* **Definition:** Malware delivery through email involves sending harmful attachments (e.g., Word documents with macros) or links to malicious websites that deliver malware upon visiting.
* **Common Malware Types:**
  * **Ransomware:** Encrypts the user’s files and demands payment for decryption keys.
  * **Trojans:** Malicious software disguised as legitimate programs to gain access to users’ systems.
  * **Viruses:** Self-replicating malware that infects systems and spreads through email attachments or compromised websites.
* **Techniques for Malware Delivery:**
  * **Malicious Attachments:** Attachments may contain harmful macros, embedded executables, or other types of malware.
  * **Malicious Links:** Emails may include links to compromised or attacker-controlled websites where malware is downloaded.
  * **Zero-Day Exploits:** Some malware is designed to exploit vulnerabilities that are not yet known to security vendors (zero-day vulnerabilities).
* **Indicators of Malware Delivery:**
  * **Unexpected Attachments:** Emails from known or unknown senders containing attachments, especially executable files or documents requiring macros to be enabled.
  * **Links to Unfamiliar Websites:** Shortened or obfuscated URLs that redirect users to malicious websites.
  * **Suspicious Behavior in Email Clients:** Unusual activity like the automatic opening of attachments or pop-ups asking for login credentials.

### **Spoofing and Impersonation Attacks**

Spoofing occurs when an attacker forges email headers to make an email appear as though it is from a trusted source. Impersonation attacks involve sending emails that mimic the communication style of legitimate individuals, often to deceive the recipient.

**Key Topics:**

* **Spoofing:** Attackers falsify email sender addresses or domains to trick recipients into believing the email came from a legitimate source. For example, an attacker might send an email that looks like it came from “[support@microsoft.com](mailto:support@microsoft.com)” but was actually sent from a malicious domain.
* **Impersonation:** Attackers imitate well-known individuals, like executives or business partners, to deceive victims into providing sensitive information or transferring money.
* **Indicators of Spoofing/Impersonation:**
  * **Inconsistent Email Addresses:** Small differences in email addresses (e.g., "support@m1crosoft.com" instead of "[support@microsoft.com](mailto:support@microsoft.com)").
  * **Unusual Language or Formatting:** Messages that don’t match the typical communication style of the sender.
  * **Requests for Sensitive Information:** Emails requesting credentials, bank account numbers, or payment details.

### **Credential Harvesting**

Credential harvesting is a method used by attackers to collect usernames, passwords, and other login details, often through fake login pages designed to mimic legitimate websites.

**Key Topics:**

* **Definition:** Attackers send emails containing links to fake login pages that closely resemble official websites (e.g., a fake Microsoft 365 login page) to capture the user’s credentials.
* **Methods Used:**
  * **Phishing Links:** Direct users to a login page that looks legitimate but is controlled by the attacker.
  * **Man-in-the-Middle (MitM) Attacks:** Attackers intercept communication between the user and a legitimate website to steal login credentials.
* **Indicators of Credential Harvesting:**
  * **Login Page Mismatches:** URLs that don’t match the legitimate service’s domain (e.g., “microsoftsupport-login.com” instead of “microsoft.com”).
  * **Unexpected Login Prompts:** Being prompted to re-enter credentials unexpectedly, especially after clicking on an email link.
  * **Multiple Failed Login Attempts:** A potential sign that an attacker is testing or using stolen credentials.

