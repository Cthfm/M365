# Information Barriers: Sharepoint

## Overview

Information Barriers (IB), part of Microsoft Purview, are compliance policies designed to **restrict communication and collaboration** between specific users or groups within Microsoft Teams, SharePoint, OneDrive, and other Microsoft 365 services. These policies are especially useful for **regulated industries** to prevent conflicts of interest and ensure that sensitive information does not cross organizational boundaries.

### **Key Capabilities of Information Barriers in SharePoint and OneDrive**

1. **Segmentation and Access Control**:
   * Users are assigned **segments** (like “HR” or “Sales”), which dictate who they can interact with across SharePoint or OneDrive.
   * IB policies can block users from **accessing sites, adding members**, or **sharing content** across segments.
2. **Modes of IB Policies**:
   * **Explicit Mode**: Users can only access content if they belong to the same segment as the site.
   * **Mixed Mode**: Allows more flexible access for specific users or segments.
   * **Owner Moderated Mode**: Site owners can grant access to users from otherwise restricted segments.
3. **Global Management**:
   * Administrators (Global or SharePoint) can create and manage segments and IB policies using **PowerShell**.
   * IB policies apply uniformly across **SharePoint and OneDrive**; enabling IB for one automatically applies it to both.
4. **Restrictions in Legacy vs. Modern Modes**:
   * In **Legacy mode**, organizations are limited to 250 segments with users allowed only one segment assignment.
   * In **modern multi-segment mode**, up to 5,000 segments are supported, with users able to belong to multiple segments, providing more flexibility.
5. **IB Policy Enforcement**:
   * Changes to IB policies (like adding or removing segments) may take up to 24 hours to propagate across the system.
   * For organizations needing enhanced visibility and compliance management, **Microsoft Purview compliance reports** help monitor IB policy effectiveness.

These barriers enhance both **security and compliance** by ensuring that unauthorized collaboration or data sharing is blocked automatically.
