# Limits for Retention Policies and Retention Label Policies in Microsoft 365

## Overview

Microsoft 365 enforces specific limits for managing data retention policies to ensure security, compliance, and performance.

## **1. Retention Labels and Policies**

* **Retention Labels**: Maximum of 1,000 per tenant.
* **Policies per Tenant**: Up to **10,000** total policies, covering:
  * Retention, DLP, eDiscovery, In-Place Holds, sensitivity labels, etc.
* Exclusions: Policies for auto-labeling, Exchange MRM, and Teams/Viva Engage mailboxes are not counted within the 10,000-policy limit.

### **2. Retention Policies by Workload**

* **Exchange (email)**: 1,800 policies; up to **50 policies per mailbox** (performance impact may occur beyond 25).
* **SharePoint/OneDrive (all sites)**: 13 policies.
*   **SharePoint/OneDrive (specific locations)**: 2,600 policies.

    _Note_: These numbers also apply to eDiscovery and In-Place Hold policies.

### **3. Maximum Items per Policy (Static Scope)**

* **Exchange mailboxes**: 1,000
* **Microsoft 365 Groups**: 1,000
* **Teams (messages, chats, Copilot)**: 1,000
* **Viva Engage**: 1,000
* **SharePoint sites**: 100
* **OneDrive accounts**: 100
*   **Skype for Business**: 1,000 users per policy

    _Solution_: Create multiple policies if these limits are exceeded, or use adaptive scopes for more flexibility.

### **4. Example Solutions for Policy Limits**

* **Exchange**:
  * Create two policies if different retention periods are needed (e.g., 7 years for most users, 5 years for a subset).
* **SharePoint**:
  * Divide retention across multiple policies (e.g., 20 policies for 2,000 sites with 10-year retention, and 80 policies for 8,000 sites with 4-year retention).

### **5. Disposition Review Limits**

* **Items for Disposition Review**:
  * 16 million items pending or approved.
  * 16 million automatically disposed without review.
* **Reviewers**:
  * 10 reviewers per stage (individuals or security groups).
  * 200 reviewers per tenant. _Recommendation_: Use mail-enabled security groups for larger organizations.
* **Proof of Disposition**: Retain records for up to 7 years.
