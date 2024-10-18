# Retention Labels for Exceptions to Retention Policies

## Overview

Retention labels in Microsoft 365 allow organizations to manage **exceptions to retention policies** by applying customized retention settings to **individual items** (e.g., specific documents or emails). While **retention policies** apply broadly at the **container level** (like entire SharePoint sites or mailboxes), retention labels offer **granular control** over particular content, ensuring that specific items follow different retention rules when needed.

### **When to Use Retention Labels**

* **Override retention policies**: Apply a longer or different retention period for specific items.\
  **Example**: Most documents on a SharePoint site follow a 3-year retention policy, but **contract documents** need to be retained for **7 years**. A retention label can ensure these contracts remain accessible beyond the default policy period.
* **Prevent automatic deletion**: Use labels to override automatic deletion at the end of a retention period.
* **Apply different deletion periods**: Assign shorter or longer deletion periods based on business needs.

Retention labels also offer **additional capabilities** such as **event-based retention** and **disposition reviews**, which are not available with standard retention policies.

### **Creating Retention Labels: Steps and Guidelines**

1. **Access the Portal:**\
   Use either the **Microsoft Purview portal** or **Microsoft Purview compliance portal**.
   * **Purview Portal**: Navigate to Data Lifecycle Management > Retention labels.
   * **Compliance Portal**: Solutions > Data lifecycle management > Microsoft 365 > Labels tab.
2. **Create the Label:**
   * Select **Create a label** and follow the prompts.
   * Choose the **label name carefully**—it **cannot be changed** after saving.
   * Configure retention settings, such as how long to retain the item or when to delete it.
   * **Save the label** (you can publish or auto-apply it later).
3. **Editing Labels:**
   * Some settings can be edited after creation, including label descriptions and retention periods.
   * However, **key settings** like the label name and core retention logic cannot be changed after saving.

### **Next Steps: Applying Retention Labels**

Once created, retention labels can be applied in one of two ways:

* **Manual Publication:** Make the label available for users to apply directly within apps (e.g., SharePoint, OneDrive).
* **Auto-application:** Configure rules to apply labels automatically based on content conditions (e.g., keywords or sensitive data).

### **Tip for High-Value Records**

For managing **high-value business or legal records**, create retention labels through the **Records Management** solution instead of Data Lifecycle Management. This allows for advanced options like **event-based retention** and **disposition reviews**.
