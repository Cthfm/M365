# Sharepoint Admin Portal and RBAC

## Overview

The following section goes over the Sharepoint Administrator role and what access is has to. A link is provided to the Sharepoint Admin center.&#x20;

### Sharepoint Administrator Role

The **SharePoint Administrator role** grants access to the **SharePoint admin center**, allowing users to manage various aspects of SharePoint and OneDrive, including:

* **Creating and deleting sites**
* **Managing site admins** (adding/removing)
* **Adjusting sharing settings** across the organization
* **Managing Microsoft 365 groups**, including creating, deleting, restoring groups, and changing group owners
* **Setting storage limits** for sites

### **Key Permissions and Roles**

1. **Global Administrators**:
   * Have **all permissions** available to SharePoint Administrators.
   * Can assign the SharePoint Administrator role to other users.
   * **Best Practice**: Use Global Administrator privileges sparingly to improve security.
2. **Site Admins**:
   * Manage individual sites but **don't require** Microsoft 365 admin roles.
   * Don't have access to the **SharePoint admin center**.
3. **Term Store Administrators**:
   * Manage the **term store** (a collection of standardized terms for consistent usage across the organization).
4. **API Access**:
   * API management in SharePoint might require the **Application Administrator role** or higher.

### **Managing Access and Permissions**

* Global and SharePoint Administrators **don’t have automatic access** to all sites or users' OneDrive accounts but can **grant themselves access** via Microsoft PowerShell.
* Changes in admin roles (granting or revoking access to the SharePoint admin center) can take **up to an hour** to apply.

For more details, see:

* **Assign admin roles**: Microsoft 365 admin center
* **Manage site admins**: SharePoint documentation

### **Best Practices**

* Use **roles with minimal permissions** to improve security.
* Reserve **Global Administrator** permissions for **emergency scenarios** only.

### Sharepoint Admin Portal Link

{% embed url="https://go.microsoft.com/fwlink/?linkid=2185219" %}

