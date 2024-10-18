# Information Barriers

#### **Overview of Information Barriers in Microsoft Purview**

**Information Barriers (IB)** in Microsoft Purview are **compliance policies** designed to control communication and collaboration between specific users, departments, or groups within an organization. This feature is essential for organizations that need to prevent conflicts of interest or restrict the flow of sensitive information, especially in highly regulated industries such as **financial services, education, and healthcare**.

***

#### **Core Capabilities**

1. **Segmentation of Users and Groups**:
   * Users can be assigned to **segments** (e.g., “HR,” “Sales”) which dictate who they can collaborate with.
   * IB policies ensure **segmented users** cannot share files, chat, or access content across prohibited segments in **Teams, SharePoint, and OneDrive**.
2. **Enforcement of Communication and Collaboration Rules**:
   * Prevents actions like:
     * **Adding users to Teams** or group chats.
     * **Sharing documents across departments**.
     * **Accessing restricted sites or folders**.
     * **Calling or chatting with specific users in Teams**​[Microsoft Learn](https://learn.microsoft.com/en-us/purview/information-barriers)​[Microsoft Learn](https://learn.microsoft.com/en-us/purview/information-barriers-onedrive).
   * Users subject to these policies may also be **blocked from finding or selecting restricted users** within organizational tools.

***

#### **Supported Scenarios**

Examples where IB policies are applied:

* **Financial services**: Prevent day traders from communicating with marketing teams to avoid insider trading risks.
* **Education**: Ensure teachers from one school cannot share content with students from another school in the same district.
* **Internal teams**: Restrict research teams from accessing trade secrets or sensitive product development files​[Microsoft Learn](https://learn.microsoft.com/en-us/purview/information-barriers)​[Microsoft Learn](https://learn.microsoft.com/en-us/purview/information-barriers-onedrive).

***

#### **IB Modes and Policy Management**

1. **Modes**:
   * **Explicit Mode**: Only users within the same segment can access shared content.
   * **Mixed Mode**: Provides flexible access to content for certain users across segments.
   * **Owner Moderated Mode**: Allows site owners to override restrictions for specific users when necessary​[Microsoft Learn](https://learn.microsoft.com/en-us/purview/information-barriers-onedrive).
2. **Configuration and Administration**:
   * IB policies can be managed through **Microsoft Purview's compliance portal** and **PowerShell**.
   * Organizations in **Legacy mode** are limited to 250 segments with single-segment assignments per user, while **modern multi-segment mode** supports up to 5,000 segments and multiple segment assignments​[Microsoft Learn](https://learn.microsoft.com/en-us/purview/information-barriers).

***

#### **Why Use Information Barriers?**

* **Compliance**: Meet legal and regulatory requirements by restricting unauthorized communication.
* **Risk Mitigation**: Reduce the risk of data leakage and insider trading by controlling access.
* **Security**: Ensure sensitive information is only accessible by authorized personnel.
