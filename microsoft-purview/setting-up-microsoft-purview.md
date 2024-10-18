# Setting Up Microsoft Purview

## Overview

Before you can start using Microsoft Purview, there are a few foundational setup steps. Here are the steps to ensure you’re ready to begin working with the platform.

### **Step 1: Access Microsoft Purview**

Microsoft Purview is a cloud-native solution, so you’ll need an active Azure subscription to get started. Here’s how to access it:

* **Azure Portal Access**: Log into the [Azure Portal](https://portal.azure.com) with your Azure credentials.
* **Search for Purview**: In the Azure portal, search for “Microsoft Purview” in the search bar and select the **Microsoft Purview Accounts** option from the list.
* **Create a Purview Account**:
  * Click on **Create** to start creating your Purview account.
  * Fill in the required details such as **subscription**, **resource group**, **account name**, and **region**.
  * Click **Review + Create**, then click **Create** to finalize the setup.

### **Step 2: Set Up Permissions**

After creating your Microsoft Purview account, it’s essential to configure the correct permissions for your team to manage and interact with the data:

* **Assign Roles**: Navigate to the **Access Control (IAM)** tab and assign users the appropriate roles. Key roles include:
  * **Purview Data Reader**: Can view Purview assets and insights but cannot make changes.
  * **Purview Data Contributor**: Can add, edit, and manage data sources, assets, and policies.
  * **Purview Administrator**: Can configure and manage all aspects of the Purview account.

Ensure the right permissions are assigned to your security team to facilitate effective threat hunting.

### **Step 3: Connect Data Sources**

To start using Microsoft Purview for data governance and threat hunting, you need to connect your organization’s data sources. Microsoft Purview supports various types of data repositories, including:

* Azure Storage accounts
* Azure SQL Databases
* Azure Data Lake Storage (ADLS)
* On-premises databases (via Azure Data Factory)

Here’s how to add a data source:

* In the Purview portal, navigate to **Data Map** and click on **Register**.
* Select your data source type (e.g., Azure Storage) and follow the steps to register the source by providing necessary credentials or connection details.

This enables Purview to begin scanning and classifying your data, laying the foundation for threat hunting.
