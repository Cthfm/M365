# OneDrive Insider Threat & Data Exfiltration

#### **Introduction to Insider Threats & Data Exfiltration in OneDrive**

Insider threats are a significant risk to organizations because they often involve users who already have authorized access to sensitive data. These threats can be malicious, such as employees attempting to steal data before leaving a company, or unintentional, where users inadvertently share confidential files outside the organization.

**Key Types of Insider Threats:**

* **Malicious Insiders:** Employees or contractors who intentionally exfiltrate data for personal gain, to harm the organization, or as part of corporate espionage.
* **Accidental Insiders:** Employees who unintentionally share sensitive data externally without understanding the risks.
* **Compromised Accounts:** Attackers who gain access to an employee’s account and use it to steal data without detection.

***

#### **Identifying Key Indicators of Insider Threats**

Insider threats in OneDrive often manifest through unusual user behavior, such as accessing, downloading, or sharing sensitive files in abnormal ways. Key indicators to monitor include:

**1. Unusual Access to Sensitive Files**

Insiders may access files they don’t usually need for their daily tasks, particularly sensitive files like financial records, HR data, or intellectual property.

**Indicators:**

* A user who typically doesn’t interact with sensitive files suddenly starts accessing them.
* Access to files outside the user’s department or job role.

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileAccessed -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" -UserIds user@example.com | Where-Object {$_.FileName -match "sensitive_filename"}
```

***

**2. Large-Scale File Downloads**

Mass file downloads can signal a data exfiltration attempt, especially when performed by users who don’t normally download large volumes of data. These downloads could be an insider preparing to leave the company or a compromised account exfiltrating data for malicious purposes.

**Indicators:**

* Large numbers of files being downloaded in a short period.
* Users downloading sensitive files they don’t typically need.

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileDownloaded -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" -UserIds user@example.com | Where-Object {$_.ResultSize -gt 100}
```

***

**3. Unauthorized External Sharing of Files**

One of the clearest indicators of a potential insider threat is when users share sensitive data externally, especially with personal email accounts or unfamiliar domains. Unauthorized external sharing may be done maliciously or accidentally.

**Indicators:**

* Sharing sensitive files with personal email addresses (e.g., Gmail, Yahoo).
* Sharing with external domains that aren’t part of the organization’s trusted partners.

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations SharingInvitationCreated -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.ExternalAccess -eq $true}
```

***

**4. Abnormal File Deletions**

Insiders or compromised accounts may delete large numbers of files to cover their tracks or sabotage the organization. Monitoring for unusual file deletion patterns is crucial in identifying potential threats.

**Indicators:**

* Users deleting files they normally wouldn’t interact with.
* Large-scale deletions of critical or sensitive files.

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileDeleted -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.ResultSize -gt 50}
```

***

**5. Syncing Sensitive Files to Unmanaged Devices**

OneDrive’s sync feature allows users to access files offline, but if sensitive files are synced to unmanaged or unauthorized devices, it could lead to data exfiltration. Monitoring syncing behavior is critical to ensure files are only synced to trusted devices.

**Indicators:**

* Syncing of sensitive files to personal or unrecognized devices.
* Users syncing large volumes of data without a legitimate business reason.

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileSync -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.ClientApp -notlike "ManagedDevices"}
```

***

#### **Case Study: Detecting Insider Data Exfiltration via OneDrive**

**Scenario:**\
A departing employee in the HR department, who has access to sensitive employee records, begins downloading a large volume of files and sharing some of them with an external email address. The security team must investigate this activity and prevent further data exfiltration.

**Steps for Investigation:**

1. **Query File Downloads:**
   *   Identify all file download events for the user in question:

       ```PowerShell
       PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileDownloaded -UserIds hr_employee@example.com -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY"
       ```
2. **Review Sharing Invitations:**
   *   Check for any external sharing invitations created by the employee:

       ```PowerShell
       PowerShellCopy codeSearch-UnifiedAuditLog -Operations SharingInvitationCreated -UserIds hr_employee@example.com -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.ExternalAccess -eq $true}
       ```
3. **Monitor for File Deletions:**
   *   Ensure that the employee hasn’t deleted critical files to cover their tracks:

       ```PowerShell
       PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileDeleted -UserIds hr_employee@example.com -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY"
       ```
4. **Respond to the Threat:**
   * If unauthorized external sharing or mass downloads are detected, revoke the user’s access immediately. Recover deleted files and escalate the investigation for further analysis.

***

#### **Best Practices for Mitigating Insider Threats and Data Exfiltration**

1. **Automate Alerts for Unusual Behavior:**
   * Set up automated alerts using **Microsoft Defender for Cloud Apps** or **Microsoft Sentinel** to flag suspicious activities such as large file downloads, external sharing, or mass deletions.
2. **Limit Access to Sensitive Files:**
   * Implement strict access controls and **Role-Based Access Control (RBAC)** to ensure that only authorized users can access sensitive files. Regularly audit user permissions to ensure compliance.
3. **Use Conditional Access Policies:**
   * Enforce **Conditional Access** policies that limit file access to trusted devices and locations. Require multi-factor authentication (MFA) for users accessing sensitive data, particularly from external networks.
4. **Implement Data Loss Prevention (DLP):**
   * Use **DLP policies** to automatically detect and block the sharing or downloading of sensitive information such as personal identification numbers (PINs), credit card numbers, or proprietary business data.
5. **Regularly Review File Access and Sharing Logs:**
   * Schedule periodic reviews of file access and sharing activities. Focus on high-risk users, departments, or roles that handle sensitive data. Identify and address any anomalous behavior before it leads to data loss.
