# OneDrive Synchronization

#### **OneDrive Synchronization**

OneDrive allows users to sync files between their devices and the cloud, ensuring that files are up-to-date across multiple devices. While this feature enhances productivity, it also introduces potential security risks. Malicious actors can exploit synchronization to propagate ransomware, insiders can sync and exfiltrate sensitive data, and compromised devices can sync files without the user’s knowledge.

**Key Risks of Unmonitored Synchronization:**

* **Ransomware Propagation:** Files infected with ransomware on a local device can be synced to the cloud, encrypting files across all devices.
* **Data Exfiltration:** Employees may use the sync feature to download sensitive data to unauthorized devices.
* **Compromised Devices:** If a compromised device syncs with OneDrive, it can lead to data theft or malware spread.

***

#### **Key Events to Monitor for Sync Issues**

The Unified Audit Log (UAL) in OneDrive logs synchronization events, providing critical insights into the syncing behavior of users and devices. By focusing on sync-related events, security teams can detect and respond to potential threats.

**1. FileSync Event**

* **Definition:**
  * The `FileSync` event logs when a file is synced between OneDrive and a user’s device. Monitoring these events is crucial for identifying suspicious synchronization patterns, such as syncing from unapproved devices or syncing a large volume of files in a short period.
* **Significance:**
  * **Threat Hunting Focus:** Abnormal syncing activity, such as excessive file syncs, syncs from unknown or unmanaged devices, or syncing sensitive files outside of approved locations.
  * **Example Threats:** A compromised device syncing malware-infected files or an insider syncing confidential documents to a personal device.

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileSync -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY"
```

***

**2. FileModified and FileDeleted Events in Sync**

* **FileModified:** This event logs when files are modified during the sync process. Large-scale or unusual modifications can signal potential issues such as ransomware encryption.
* **FileDeleted:** This event logs when files are deleted during the sync process. Monitoring for mass deletions can help identify insider threats or ransomware attacks trying to erase data.

**Significance:**

* **Threat Hunting Focus:** Mass file modifications or deletions that coincide with sync events can indicate the presence of ransomware or an insider trying to cover their tracks.
* **Example Threats:** Files being encrypted during a ransomware attack or an insider maliciously deleting files after syncing them to a local device.

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileModified, FileDeleted -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY"
```

***

**3. Sync Activity from Unapproved Devices**

Users typically sync OneDrive files from company-managed devices. Syncing from unknown or unmanaged devices can be a sign of a security breach, especially if sensitive files are being accessed.

* **Significance:**
  * **Threat Hunting Focus:** Detect sync events from devices that are not recognized or managed by the organization.
  * **Example Threats:** A compromised account syncing sensitive files to a personal or unknown device.

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileSync -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.ClientApp -notlike "ManagedDevices"}
```

***

#### **Detecting and Investigating Abnormal Sync Patterns**

Monitoring sync patterns can help detect various types of threats, including ransomware, insider attacks, and account compromise. Here are common scenarios to watch for:

**1. Large-Scale Syncing of Files**

Unusually large sync operations, especially involving sensitive files, can indicate data exfiltration. This can be performed by a malicious insider, or a compromised account may be used to sync and steal company data.

**Indicators:**

* A large number of files synced in a short period.
* Syncs involving sensitive files that the user typically doesn’t access.

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileSync -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Group-Object -Property UserId | Where-Object {$_.Count -gt 100}
```

***

**2. Syncing from Unfamiliar Locations**

Sync activity from unfamiliar geographic locations can signal compromised credentials being used by attackers to download company data. Monitoring for syncing from unusual IP addresses or countries can help spot these activities early.

**Indicators:**

* Syncing from locations outside the normal operating regions of the organization.
* Syncing from suspicious IP addresses not commonly associated with legitimate users.

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileSync -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.IPAddress -notlike "KnownIPRange"}
```

***

**3. Ransomware Propagation via Sync**

Ransomware infections can spread rapidly through file synchronization. As infected or encrypted files are synced across devices, they can lock down access to critical files in the cloud and across user devices.

**Indicators:**

* Multiple files being modified and synced in rapid succession, particularly if filenames or extensions change unexpectedly (e.g., `.lock`, `.enc`).
* Files being deleted en masse shortly after sync events.

**PowerShell Query Example:**

```PowerShell
PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileModified, FileDeleted -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.ResultSize -gt 50}
```

***

#### **Case Study: Detecting Ransomware Spread via OneDrive Sync**

**Scenario:** A user’s laptop becomes infected with ransomware. As files on the laptop are encrypted, the ransomware spreads by syncing the encrypted files back to OneDrive, locking out access to shared files for the entire team. This behavior needs to be detected and stopped quickly to prevent further damage.

**Steps for Investigation:**

1. **Query for Sync Activity:**
   *   Use the following PowerShell command to identify all sync events from the user’s account:

       ```PowerShell
       PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileSync -UserIds user@example.com -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY"
       ```
2. **Check for Mass Modifications:**
   *   Review logs for mass file modifications, especially changes in file names or extensions:

       ```PowerShell
       PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileModified -UserIds user@example.com -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY" | Where-Object {$_.FileExtension -match ".lock|.enc"}
       ```
3. **Investigate File Deletions:**
   *   Check for mass deletions occurring after the sync, which could indicate further ransomware activity:

       ```PowerShell
       PowerShellCopy codeSearch-UnifiedAuditLog -Operations FileDeleted -UserIds user@example.com -StartDate "MM/DD/YYYY" -EndDate "MM/DD/YYYY"
       ```
4. **Respond to the Threat:**
   * Suspend the affected user’s OneDrive account to stop the sync process, then initiate recovery efforts by restoring file versions from before the ransomware infection.

***

#### **Best Practices for Monitoring and Managing Sync Activity**

1. **Monitor for Large Sync Operations:**
   * Set up alerts for large sync operations, especially when sensitive data is involved. Unusual sync activity can indicate data exfiltration or malware propagation.
2. **Restrict Sync to Managed Devices:**
   * Enforce Conditional Access policies that limit synchronization to approved, managed devices. This reduces the risk of data being synced to unauthorized devices.
3. **Automate Alerts for Sync Issues:**
   * Use tools like **Microsoft Sentinel** or **Microsoft Defender for Cloud Apps** (formerly MCAS) to set up real-time alerts for suspicious sync patterns, such as mass file deletions or syncs from unfamiliar locations.
4. **Leverage File Versioning:**
   * Enable file versioning in OneDrive to protect against ransomware attacks. By restoring files to previous versions, you can recover from ransomware without having to pay a ransom.
5. **Regularly Audit Sync Activity:**
   * Conduct regular audits of sync logs to ensure that only authorized devices and users are syncing files. Investigate any unusual or abnormal sync activity immediately.
