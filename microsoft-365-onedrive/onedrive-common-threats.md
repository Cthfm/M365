# OneDrive Common Threats

## **Overview**

The following section goes over the common threats observed with OneDrive devices.&#x20;

### **Data Exfiltration Through Unauthorized Sharing:**

* Attackers or malicious insiders can exfiltrate sensitive data by sharing files or folders outside the organization.
* **Indicators of Compromise (IoCs):** Suspicious or unauthorized external sharing of sensitive files, often to unfamiliar domains or personal email accounts.

### **Ransomware Attacks on Synced Files:**

* Ransomware can infect local devices and propagate to OneDrive via file synchronization. Once infected, ransomware can encrypt OneDrive files, locking users out of their data.
* **IoCs:** Sudden large-scale file modifications, unusual file extensions, or file access spikes.

### **Insider Threats:**

* Insider threats can come from employees intentionally or unintentionally leaking data, deleting critical files, or misusing sharing capabilities.
* **IoCs:** Abnormal behavior such as mass file deletions, unsanctioned sharing of sensitive documents, or suspicious access to critical files during off-hours.

### **External Threats (Compromised Accounts, Malware Infected File Uploads):**

* **Compromised Accounts:** Attackers gain access to OneDrive through phishing, brute-force attacks, or credential stuffing, allowing them to steal or tamper with files.
* **Malware-Infected File Uploads:** Users can accidentally or intentionally upload files containing malware, spreading it to other users or devices.
* **IoCs:** Unexpected file uploads, user activity from unfamiliar locations or IP addresses, and unusual access patterns.
