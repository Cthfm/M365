# Sensitivity Labels

## **Overview**

Sensitivity labels and policies are critical components in Microsoft Purview that allow organizations to protect their sensitive data. These labels help classify and enforce rules around data access, sharing, and protection, ensuring that sensitive information remains secure. In this lesson, we will explore how sensitivity labels and policies work within Microsoft Purview, how to apply them, and how they can aid in threat hunting by detecting policy violations and securing sensitive data.

## **What Are Sensitivity Labels?**

**Sensitivity labels** in Microsoft Purview are used to classify and protect data based on its level of sensitivity. These labels can be applied to a wide range of data, from documents and emails to structured databases. Once applied, sensitivity labels can control how data is accessed, shared, and protected, ensuring that sensitive information is safeguarded from unauthorized access or misuse.

**Key functions of sensitivity labels include:**

* **Classification**: Sensitivity labels help identify and categorize data based on its level of sensitivity, such as "Confidential," "Internal," or "Public."
* **Protection**: Labels can enforce encryption, control who can access or edit the data, and determine how data can be shared both internally and externally.
* **Tracking**: Sensitivity labels allow you to monitor data activity, track access, and detect when labeled data is moved or shared.

**Common sensitivity labels:**

* **Confidential**: For highly sensitive information, such as intellectual property or PII.
* **Internal**: For data that is restricted to internal users but not as sensitive as confidential data.
* **Public**: For data that can be shared freely without restrictions.

## **How Sensitivity Labels Support Threat Hunting**

For threat hunters, sensitivity labels are crucial as they mark the data that requires the most protection. By focusing on labeled data, security teams can detect potential threats such as:

* **Unauthorized access**: If a user accesses or attempts to access labeled sensitive data without proper authorization, this can indicate a potential breach.
* **Data leakage**: Labels help identify when sensitive data is shared outside the organization, either intentionally or as part of an attack.
* **Policy violations**: Sensitivity labels can trigger alerts if specific policies tied to data protection (like encryption or access controls) are violated.

For example, if a document labeled **Confidential** is accessed by an external user or shared outside of approved channels, threat hunters can investigate the incident and determine if data exfiltration has occurred.

## **Applying Sensitivity Labels in Microsoft Purview**

Microsoft Purview allows sensitivity labels to be applied manually or automatically based on predefined rules or patterns. Here’s how you can start using sensitivity labels to protect your data:

**Step 1: Create or Choose Sensitivity Labels**

You can create new sensitivity labels or use existing ones from Microsoft’s built-in templates.

* In the Purview portal, navigate to **Information Protection** and select **Sensitivity Labels**.
* Create a new label and configure its settings, including:
  * **Name and Description**: Choose a clear label name, such as "Highly Confidential."
  * **Protection Settings**: Configure whether the label enforces encryption, access control, or watermarks on data.
  * **Auto-Labeling**: Set rules for automatically applying the label to documents or emails based on content, such as the presence of PII or credit card numbers.

**Step 2: Apply Sensitivity Labels to Data**

You can apply sensitivity labels manually to files or set up automated processes to label data across your organization.

* **Manual Labeling**: Users can manually apply sensitivity labels to documents or emails from within Microsoft Office apps or the Purview portal.
* **Automated Labeling**: Configure automatic labeling for data stored in Azure, SharePoint, or other integrated systems. For example, all documents containing a Social Security number could automatically receive a “Confidential” label.

**Step 3: Monitor Labeled Data**

Once sensitivity labels are applied, Purview enables you to monitor labeled data for potential risks. By reviewing data activity and access logs, threat hunters can detect unusual behavior, such as an external user attempting to open a document labeled **Confidential**.

## **Implementing Policies to Enforce Data Security**

In addition to sensitivity labels, Microsoft Purview supports **policies** that govern how data is accessed, shared, and managed. These policies enforce security controls and help prevent unauthorized access or sharing of sensitive data.

**Common Types of Policies in Purview:**

* **Data Loss Prevention (DLP) Policies**: DLP policies help prevent sensitive data from being shared outside the organization. For example, a DLP policy might prevent documents labeled **Highly Confidential** from being sent via email to external domains.
* **Access Control Policies**: These policies determine who can access data labeled with specific sensitivity labels. For instance, only specific roles within the organization might be allowed to access files labeled as **Internal Use Only**.
* **Encryption Policies**: Sensitivity labels can enforce encryption, ensuring that any document or email labeled **Confidential** is encrypted and can only be accessed by authorized users.

## **Creating and Managing Policies in Purview:**

To create a policy that enforces data security:

* Navigate to **Policies** within the Purview portal.
* Select **Create Policy** and choose the type of policy (DLP, access control, etc.).
* Configure the policy settings, such as:
  * What sensitivity label(s) the policy applies to.
  * What actions are restricted (e.g., sharing outside the organization, copying to external storage).
  * Who is affected by the policy (e.g., users, groups, roles).
* Set alerts for policy violations, which notify the security team if sensitive data is accessed or shared in a way that violates the policy.

## **Detecting Policy Violations for Threat Hunting**

Sensitivity labels and policies work together to create a strong framework for protecting data. For threat hunters, **policy violations** serve as key indicators of potential security risks. Some examples include:

* **Unauthorized data sharing**: A DLP policy might detect when a user attempts to email a document labeled **Highly Confidential** to an external domain. This could indicate an insider threat or an accidental data leak.
* **Access from unauthorized locations**: Access control policies can detect when sensitive data is accessed from an unusual location (e.g., a country where the organization doesn’t operate). This could be an indicator of a compromised account or an external attack.
* **Unusual activity patterns**: If a document labeled **Confidential** is suddenly accessed by a large number of users or downloaded multiple times, it could suggest a data exfiltration attempt.

Threat hunters should regularly review policy violations to detect potential threats and investigate incidents that involve the improper handling of sensitive data.

## **Best Practices for Using Sensitivity Labels and Policies in Threat Hunting**

1. **Label Data Early**: Apply sensitivity labels as soon as data is created. This ensures that protection is in place before the data is shared or accessed.
2. **Automate Labeling**: Automate the labeling process whenever possible. Automated labels ensure that sensitive data is consistently classified and protected, reducing the risk of human error.
3. **Enforce Strong Policies**: Use DLP and access control policies to restrict the sharing and access of sensitive data. These policies act as a security barrier, preventing data breaches before they occur.
4. **Regularly Review Policy Violations**: Policy violations are often the first sign of a potential breach or insider threat. Set up alerts for policy violations and investigate them immediately to determine if further action is needed.
