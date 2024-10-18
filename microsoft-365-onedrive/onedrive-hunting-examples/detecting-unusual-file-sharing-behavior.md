# Detecting Unusual File Sharing Behavior

## **Introduction to File Sharing in OneDrive**

OneDrive’s collaboration features allow users to easily share files with both internal and external users. While this is a key productivity feature, it also presents significant security risks if not properly monitored. Attackers or insiders may attempt to exfiltrate data by sharing sensitive files, or users may inadvertently share files externally without proper access controls.

### **Key Risks of Uncontrolled File Sharing:**

* **Data Leakage:** Sensitive files may be shared with unauthorized users or external domains.
* **Insider Threats:** Employees with access to critical data may maliciously or unintentionally share it with external parties.
* **Account Compromise:** If an account is compromised, an attacker could share files with themselves or external entities without detection.

### **Identifying Abnormal File Sharing Patterns**

To detect unauthorized file sharing, it's essential to establish a baseline of normal sharing behavior, then look for anomalies or deviations from this baseline. Unusual sharing patterns might include:

**1. External Sharing with Unfamiliar Domains**

External sharing can pose a serious security threat, especially when files are shared with domains outside the organization. It’s important to monitor for:

* **Sharing to personal email accounts** (e.g., Gmail, Yahoo).
* **Unusual external domains** that are not part of the regular business communication.

**Example Threats:**

* An insider trying to exfiltrate data to a personal email.
* A compromised account sharing files with external parties.

**PowerShell Query Example:**

```powershell
Search-UnifiedAuditLog -Operations SharingInvitationCreated -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.ExternalAccess -eq $true}
```

**2. Mass Sharing of Files**

If a user suddenly shares a large number of files, especially externally, it could be a sign of data exfiltration. A compromised account might be used to send sensitive documents out of the organization or an insider may attempt to offload company data before departing.

**Indicators:**

* **High Volume Sharing Events:** Sharing a large number of files in a short time frame.
* **Sharing Sensitive Data:** Files containing sensitive information such as financial reports or personal identification details shared externally.

**PowerShell Query Example:**

```powershell
Search-UnifiedAuditLog -Operations SharingLinkCreated -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.ResultSize -gt 50}
```

**3. Creation of Public Links ("Anyone with the link")**

Creating links that allow anyone with the link to access a file is risky, especially if used on sensitive documents. These links are hard to control once created and can be forwarded to unintended recipients.

**Example Threats:**

* A user accidentally creates a public link for a confidential document.
* A malicious insider creates a public link to expose sensitive company information.

**Indicators:**

* Public links created for files that should remain internal.
* Multiple public links created by the same user in a short time frame.

**PowerShell Query Example:**

```powershell
Search-UnifiedAuditLog -Operations SharingLinkCreated -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.SharingLinkPermission -eq "Anyone"}
```

**4. Unusual Frequency of Sharing Invitations**

Monitoring the frequency of sharing invitations helps detect unusual patterns, such as a compromised account sharing files repeatedly in a short period. Sudden spikes in sharing behavior, especially with external users, should raise red flags.

**Indicators:**

* A user who typically shares few files suddenly sends out multiple sharing invitations.
* A high number of sharing invitations sent to external recipients in a short window.

**PowerShell Query Example:**

```powershell
Search-UnifiedAuditLog -Operations SharingInvitationCreated -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Group-Object -Property UserId | Where-Object {$_.Count -gt 10}
```

### **Case Study: Detecting Unauthorized External Sharing**

**Scenario:**\
A finance department employee, who typically does not share files externally, suddenly shares multiple sensitive financial reports with a personal email account (e.g., user@gmail.com). This behavior raises suspicions of potential data exfiltration.

**Steps for Investigation:**

1. **Query Sharing Invitations:**
   *   Use the following PowerShell command to search for external sharing invitations:

       ```powershell
       Search-UnifiedAuditLog -Operations SharingInvitationCreated -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.ExternalAccess -eq $true}
       ```
2. **Filter for the Specific User:**
   *   Narrow the query down to the finance employee:

       ```powershell
       Search-UnifiedAuditLog -Operations SharingInvitationCreated -UserIds finance_employee@example.com -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY"
       ```
3. **Identify the Shared Files and Recipients:**
   * Review the logs to determine which files were shared and to whom. Look for patterns such as personal email addresses.
4. **Revoke Access and Conduct a Deeper Investigation:**
   * If unauthorized external sharing is confirmed, revoke sharing permissions immediately. Escalate the incident for further investigation, particularly to check if the user account has been compromised.

### **Best Practices for Detecting and Preventing Unauthorized Sharing**

1. **Monitor External Sharing Activities:**
   * Continuously monitor sharing invitations, especially those that involve external domains. Use automated alerts to flag any unusual or high-volume sharing events.
2. **Restrict Public Links:**
   * Disable the ability for users to create public links ("Anyone with the link") for sensitive data. Use policies to enforce restricted sharing only with specific users.
3. **Set Sharing Limits:**
   * Enforce limitations on the number of files that can be shared in a short period. Set alerts for when users attempt to share an excessive number of files, especially externally.
4. **Use Conditional Access and DLP Policies:**
   * Enforce **Conditional Access** policies that require users to be on a trusted network or device before sharing files externally. Implement **Data Loss Prevention (DLP)** policies to block the sharing of sensitive information like credit card numbers, social security numbers, or proprietary company data.
5. **Regularly Audit Sharing Activities:**
   * Schedule regular reviews of sharing activities to ensure that sensitive documents are not being shared improperly. Use automated tools like Microsoft Defender for Cloud Apps (formerly MCAS) to generate alerts for abnormal sharing patterns.
