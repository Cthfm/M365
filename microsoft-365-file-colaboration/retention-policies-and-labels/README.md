# Retention Policies and Labels

### **Retention Management**

Data retention serves several **important functions**:

1. **Compliance with Laws and Regulations:**\
   Many industries are governed by strict regulatory frameworks, such as the **Sarbanes-Oxley Act** (SOX), which requires certain records to be retained for a minimum of seven years. Failure to comply can result in penalties or legal challenges.
2. **Risk Mitigation and Litigation Readiness:**\
   Retaining relevant data and discarding obsolete content helps reduce risks in the event of litigation or **data breaches**. Deleting older content also reduces storage costs and improves security by limiting exposure to outdated information.
3. **Operational Efficiency and Improved Collaboration:**\
   When users only engage with current, useful data, they become more productive. Timely removal of unnecessary data ensures that employees can quickly locate relevant files and documents.

### **Retention Policies vs. Retention Labels: Understanding the Tools**

Microsoft 365 provides two primary retention tools, **retention policies** and **retention labels**. Each tool offers unique capabilities and can be used together for a comprehensive data retention strategy.

#### **Retention Policies**

Retention policies are **broad, location-based** policies that apply to entire containers such as:

* **Mailboxes (Exchange)**
* **SharePoint sites**
* **OneDrive accounts**
* **Teams channels and chats**
* **Viva Engage messages**

They ensure consistency across large data sets and reduce administrative overhead by automating retention across multiple locations. However, policies do not transfer when content moves to another location.

#### **Retention Labels**

Retention labels allow for **fine-grained, item-level control**. Labels are applied to individual files, folders, emails, or documents, offering greater flexibility than policies.\
Labels:

* Can move with the content across locations within the tenant.
* Provide **event-based triggers** to start retention when a specific event occurs (e.g., **employee separation** or **contract expiration**).
* Can mark content as **records** or **regulatory records**, restricting further edits or deletions.

#### **Comparison: Key Differences**

| **Feature**                       | **Retention Policies**               | **Retention Labels**                                     |
| --------------------------------- | ------------------------------------ | -------------------------------------------------------- |
| **Scope**                         | Entire containers (mailboxes, sites) | Individual items (emails, files)                         |
| **Control Over Content Movement** | Does not move with content           | Moves with content across tenant locations               |
| **Manual Application by Users**   | Not supported                        | Users can apply labels in apps like SharePoint, OneDrive |
| **Event-based Retention**         | Not supported                        | Supported for events like contract expiry                |
| **Mark as Record**                | Not supported                        | Supported to restrict editing/deletion                   |
| **Disposition Review**            | Not available                        | Provides review before deletion                          |

***

### **Using Retention Policies and Labels Together**

Organizations often **combine policies and labels** to achieve more granular control and flexibility. Below are examples of how they can work in tandem:

#### **Scenario 1: User Overrides Policy-Driven Deletion in OneDrive**

* **Retention Policy:** Automatically deletes all OneDrive files after 5 years.
* **Retention Label:** Users can manually apply a label to specific files, keeping them indefinitely.\
  **Benefit:** This gives users the flexibility to preserve important files beyond the policy-defined period.

#### **Scenario 2: Different Retention Periods for SharePoint Content**

* **Retention Policy:** Retains all content in SharePoint for 5 years, then deletes it.
* **Retention Label:** Automatically retains content for 10 years in specific document libraries.\
  **Benefit:** Helps ensure that certain documents remain accessible longer while following default policies for most content.

### **Adaptive vs. Static Scopes in Retention Policies**

Retention policies can use **static or adaptive scopes** to define their application.

1. **Adaptive Scopes:**\
   These scopes use **queries** to dynamically adjust to changes in attributes, such as job roles or departments. For example, a policy can apply to all **executives** based on their **job title** in Microsoft Entra ID. If new executives join or leave, the scope updates automatically.
2. **Static Scopes:**\
   Static scopes are **manually configured** to include specific users, mailboxes, or sites. These scopes are less flexible since changes in the organization (e.g., new hires) require manual updates to the policy.

**Example:**\
An adaptive scope ensures that the policy will always apply to **executives’ mailboxes**, without needing manual updates, while a static scope might require identifying and including individual users or URLs.

### **Automated Risk Mitigation with Adaptive Protection**

**Adaptive Protection** in Microsoft 365 enhances retention management by applying **retention labels** automatically to content based on **risk levels**.

* If high-risk users (e.g., flagged by **Insider Risk Management**) attempt to delete content, Adaptive Protection assigns a **120-day retention label** to ensure it isn’t lost.
* After the 120-day period, the content is eligible for deletion unless further action is taken.

This feature ensures that important data isn’t inadvertently or maliciously deleted by insiders.

### **Conflict Resolution: Principles of Retention**

When multiple policies and labels apply to the same content, Microsoft 365 follows specific **rules to resolve conflicts**:

1. **Retention Wins Over Deletion:**\
   Content cannot be deleted if a retention policy or label requires it to be retained.
   * **Example:** If a retention label mandates that a document is retained for 5 years but a policy attempts to delete it after 3 years, the item will be retained for 5 years.
2. **Longest Retention Period Wins:**\
   When multiple policies or labels define different retention periods, the content is retained for the longest period.
   * **Example:** A document subject to two policies (one for 5 years and another for 10 years) will be retained for 10 years.
3. **Labels Take Precedence Over Policies for Deletion:**\
   If a retention label and a policy have conflicting deletion dates, the **label’s delete action takes precedence**.

### **Auditing and Monitoring Retention Activities**

Microsoft 365 offers **extensive monitoring and auditing tools** through the **Microsoft Purview compliance portal**:

* **Content Search:** Locate all items with a specific retention label.
* **Activity Explorer:** Track actions like applying, changing, or removing labels.
* **Power Automate Integration:** Automate workflows for actions at the end of the retention period.

Auditing provides visibility into both **admin activities** (e.g., creating or deleting policies) and **user actions** (e.g., applying labels).

### **Retention vs. eDiscovery Holds**

Both retention settings and **eDiscovery holds** prevent permanent deletion, but they serve different purposes:

| **Aspect**           | **Retention Policies**     | **eDiscovery Holds**                  |
| -------------------- | -------------------------- | ------------------------------------- |
| **Purpose**          | Long-term compliance       | Short-term legal investigation        |
| **Scope**            | Broad (location-based)     | Specific to individual users or cases |
| **Content Deletion** | Optional (based on policy) | No deletion while hold is active      |

If content is subject to both **retention policies** and an **eDiscovery hold**, the hold takes precedence until manually released. However, for **long-term compliance**, retention policies are recommended over eDiscovery holds.

### **Preservation Lock: Regulatory Compliance**

Some industries require policies to be locked and **unchangeable** after being enabled (e.g., SEC Rule 17a-4). **Preservation Lock** ensures that policies can’t be disabled or modified, even by administrators, to meet these compliance standards.

### **Transitioning from Legacy Features**

Microsoft recommends using **retention policies and labels** instead of legacy tools like:

* **Litigation holds**
* **Journaling**
* **Document deletion policies**
