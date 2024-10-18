# Table of contents

* [Welcome](README.md)

## Getting Started M365

* [Microsoft 365 Overview](getting-started-m365/microsoft-365-overview.md)
* [Microsoft 365: Authentication](getting-started-m365/microsoft-365-authentication.md)
* [Microsoft 365 Session Times](getting-started-m365/microsoft-365-session-times.md)
* [Microsoft 365 Licensing](getting-started-m365/microsoft-365-licensing.md)
* [Microsoft 365: Tenant Setup](getting-started-m365/microsoft-365-tenant-setup.md)

## Powershell

* [Powershell Documentation](powershell/powershell-documentation.md)
* [Powershell Basics](powershell/powershell-basics.md)
* [Understanding Powershell Variables](powershell/understanding-powershell-variables.md)
* [Understanding Cmdlets](powershell/understanding-cmdlets.md)
* [Powershell Console & ISE](powershell/powershell-console-and-ise.md)
* [M365 Powershell Modules](powershell/m365-powershell-modules/README.md)
  * [OneDrive Powershell](powershell/m365-powershell-modules/onedrive-powershell.md)
  * [Exchange Online Powershell](powershell/m365-powershell-modules/exchange-online-powershell/README.md)
    * [Security & Compliance PowerShell](powershell/m365-powershell-modules/exchange-online-powershell/security-and-compliance-powershell.md)
    * [Exchange Online Protection PowerShell](powershell/m365-powershell-modules/exchange-online-powershell/exchange-online-protection-powershell.md)
  * [Sharepoint Online Powershell](powershell/m365-powershell-modules/sharepoint-online-powershell.md)
  * [Microsoft Graph SDK](powershell/m365-powershell-modules/microsoft-graph-sdk/README.md)
    * [Graph SDK Setup and Permission References](powershell/m365-powershell-modules/microsoft-graph-sdk/graph-sdk-setup-and-permission-references.md)
    * [Security API](powershell/m365-powershell-modules/microsoft-graph-sdk/security-api.md)
    * [Common API Reference](powershell/m365-powershell-modules/microsoft-graph-sdk/common-api-reference.md)
  * [Az PowerShell Purview](powershell/m365-powershell-modules/az-powershell-purview.md)

## Microsoft 365: UAL

* [Unified Audit Log (UAL) Overview](microsoft-365-ual/unified-audit-log-ual-overview.md)
* [Enable UAL](microsoft-365-ual/enable-ual.md)
* [Audited Activities](microsoft-365-ual/audited-activities.md)
* [Supported Services](microsoft-365-ual/supported-services.md)
* [UAL Schema](microsoft-365-ual/ual-schema.md)
* [UAL Schema: Service Specific Parameters](microsoft-365-ual/ual-schema-service-specific-parameters.md)
* [Mailbox Auditing](microsoft-365-ual/mailbox-auditing.md)
* [Azure Monitor: M365 UAL](microsoft-365-ual/azure-monitor-m365-ual.md)

## MICROSOFT 365: EXCHANGE ONLINE

* [Exchange Online](microsoft-365-exchange-online/exchange-online.md)
* [Common Threats](microsoft-365-exchange-online/common-threats.md)
* [Exchange Online: Security Features](microsoft-365-exchange-online/exchange-online-security-features.md)
* [Exchange Admin Audit Logs](microsoft-365-exchange-online/exchange-admin-audit-logs.md)
* [Mailbox Audit Logs](microsoft-365-exchange-online/mailbox-audit-logs.md)
* [EOL Hunting](microsoft-365-exchange-online/eol-hunting/README.md)
  * [EOL Hunting: Phishing Campaign Detection](microsoft-365-exchange-online/eol-hunting/eol-hunting-phishing-campaign-detection.md)
  * [EOL Hunting: Malware Detection and Analysis](microsoft-365-exchange-online/eol-hunting/eol-hunting-malware-detection-and-analysis.md)
  * [EOL Hunting: Unusual User Behavior](microsoft-365-exchange-online/eol-hunting/eol-hunting-unusual-user-behavior.md)
  * [EOL Hunting: Business Email Compromise (BEC)](microsoft-365-exchange-online/eol-hunting/eol-hunting-business-email-compromise-bec.md)
* [Reporting, Audit Log, Email Tracing Reference](microsoft-365-exchange-online/reporting-audit-log-email-tracing-reference.md)

## Microsoft 365: OneDrive

* [OneDrive](microsoft-365-onedrive/onedrive.md)
* [OneDrive Security Architecture](microsoft-365-onedrive/onedrive-security-architecture.md)
* [OneDrive Common Threats](microsoft-365-onedrive/onedrive-common-threats.md)
* [OneDrive and UAL](microsoft-365-onedrive/onedrive-and-ual.md)
* [Key Events in OneDrive](microsoft-365-onedrive/key-events-in-onedrive.md)
* [OneDrive Hunting Examples](microsoft-365-onedrive/onedrive-hunting-examples/README.md)
  * [Detecting Unusual File Sharing Behavior](microsoft-365-onedrive/onedrive-hunting-examples/detecting-unusual-file-sharing-behavior.md)
  * [Monitoring File Access Patterns](microsoft-365-onedrive/onedrive-hunting-examples/monitoring-file-access-patterns.md)
  * [OneDrive Synchronization](microsoft-365-onedrive/onedrive-hunting-examples/onedrive-synchronization.md)
  * [OneDrive Insider Threat & Data Exfiltration](microsoft-365-onedrive/onedrive-hunting-examples/onedrive-insider-threat-and-data-exfiltration.md)
* [OneDrive Security Features](microsoft-365-onedrive/onedrive-security-features.md)

## Microsoft 365: Sharepoint

* [Sharepoint](microsoft-365-sharepoint/sharepoint/README.md)
  * [Sharepoint Admin Portal and RBAC](microsoft-365-sharepoint/sharepoint/sharepoint-admin-portal-and-rbac.md)
  * [Microsoft 365: Sharepoint Security](microsoft-365-sharepoint/sharepoint/microsoft-365-sharepoint-security.md)
  * [Sharepoint Threat Hunting](microsoft-365-sharepoint/sharepoint/sharepoint-threat-hunting.md)
  * [Sharepoint: Logging and Monitoring](microsoft-365-sharepoint/sharepoint/sharepoint-logging-and-monitoring.md)
  * [Sharepoint Threat Detection Techniques](microsoft-365-sharepoint/sharepoint/sharepoint-threat-detection-techniques.md)
  * [Sharepoint: Advanced Hunting](microsoft-365-sharepoint/sharepoint/sharepoint-advanced-hunting.md)
  * [Sharepoint Powershell](microsoft-365-sharepoint/sharepoint/sharepoint-powershell.md)
  * [SharePoint Security Configuration Recommendations](microsoft-365-sharepoint/sharepoint/sharepoint-security-configuration-recommendations.md)

## MICROSOFT 365: File Colaboration

* [File Collaboration Security Controls](microsoft-365-file-colaboration/file-collaboration-security-controls.md)
* [Retention Policies and Labels](microsoft-365-file-colaboration/retention-policies-and-labels/README.md)
  * [Retention Policy Flowchart](microsoft-365-file-colaboration/retention-policies-and-labels/retention-policy-flowchart.md)
  * [Powershell: Retention CMDLets](microsoft-365-file-colaboration/retention-policies-and-labels/powershell-retention-cmdlets.md)
  * [Limits for Retention Policies and Retention Label Policies in Microsoft 365](microsoft-365-file-colaboration/retention-policies-and-labels/limits-for-retention-policies-and-retention-label-policies-in-microsoft-365.md)
  * [Retention Labels for Exceptions to Retention Policies](microsoft-365-file-colaboration/retention-policies-and-labels/retention-labels-for-exceptions-to-retention-policies.md)
* [Information Barriers](microsoft-365-file-colaboration/information-barriers/README.md)
  * [Information Barriers: Sharepoint](microsoft-365-file-colaboration/information-barriers/information-barriers-sharepoint.md)
  * [Information Barriers: OneDrive](microsoft-365-file-colaboration/information-barriers/information-barriers-onedrive.md)
  * [Information Barriers: Teams](microsoft-365-file-colaboration/information-barriers/information-barriers-teams.md)
* [Security Control References](microsoft-365-file-colaboration/security-control-references.md)

## Microsoft Purview

* [Purview Overview](microsoft-purview/purview-overview.md)
* [Microsoft Purview eDiscovery](microsoft-purview/microsoft-purview-ediscovery.md)
* [Setting Up Microsoft Purview](microsoft-purview/setting-up-microsoft-purview.md)
* [Navigating the Microsoft Purview Portal](microsoft-purview/navigating-the-microsoft-purview-portal.md)
* [Data Classification](microsoft-purview/data-classification.md)
* [Sensitivity Labels](microsoft-purview/sensitivity-labels.md)
* [Purview Data Map](microsoft-purview/purview-data-map.md)
* [Purview Insights](microsoft-purview/purview-insights.md)
* [Auditing With Purview](microsoft-purview/auditing-with-purview.md)
* [Purview Integration with Microsoft Sentinel](microsoft-purview/purview-integration-with-microsoft-sentinel.md)
* [Data Lineage](microsoft-purview/data-lineage.md)
* [Responding to Data Access Violations](microsoft-purview/responding-to-data-access-violations.md)
* [Purview Licensing](microsoft-purview/purview-licensing.md)
* [Purview and Threat Hunting](microsoft-purview/purview-and-threat-hunting/README.md)
  * [Azure Monitor Purview Table Reference](microsoft-purview/purview-and-threat-hunting/azure-monitor-purview-table-reference.md)
* [Purview Insider Risk Management](microsoft-purview/purview-insider-risk-management/README.md)
  * [Risk Management Settings](microsoft-purview/purview-insider-risk-management/risk-management-settings.md)
  * [Insider Risk Management Templates](microsoft-purview/purview-insider-risk-management/insider-risk-management-templates.md)

## Microsoft Defender: Office 365

* [Licensing](microsoft-defender-office-365/licensing.md)
* [Key Features](microsoft-defender-office-365/key-features.md)
* [Integration Workflows](microsoft-defender-office-365/integration-workflows.md)

## Microsoft Cloud App Security

* [Microsoft Cloud App Security](microsoft-cloud-app-security/microsoft-cloud-app-security.md)
* [Deploying Microsoft Cloud App Security](microsoft-cloud-app-security/deploying-microsoft-cloud-app-security.md)
* [Data Protection](microsoft-cloud-app-security/data-protection.md)
* [Policies](microsoft-cloud-app-security/policies.md)
* [Threat Detection](microsoft-cloud-app-security/threat-detection.md)
* [Azure Monitor Table Reference](microsoft-cloud-app-security/azure-monitor-table-reference.md)

## Attack Simulator

* [Attack Simulator Overview](attack-simulator/attack-simulator-overview.md)

## Device Management

* [Basic Mobility and Security vs Intune](device-management/basic-mobility-and-security-vs-intune.md)
* [Azure Monitor Intune Tables](device-management/azure-monitor-intune-tables.md)

## Secure Score

* [Secure Score](secure-score/secure-score.md)
* [Secure Score in Threat Hunting](secure-score/secure-score-in-threat-hunting.md)
* [Secure Score References](secure-score/secure-score-references.md)

## Defender XDR

* [Defender XDR](defender-xdr/defender-xdr.md)
* [Defender XDR Licensing](defender-xdr/defender-xdr-licensing.md)
* [Defender XDR Default Retention](defender-xdr/defender-xdr-default-retention.md)
* [Defender XDR Advanced Hunting Table Schemas](defender-xdr/defender-xdr-advanced-hunting-table-schemas.md)
* [Automated Response Requirements](defender-xdr/automated-response-requirements.md)
* [Supported Response Actions](defender-xdr/supported-response-actions.md)

## Threat Hunting in M365

* [Threat Hunting Introduction](threat-hunting-in-m365/threat-hunting-introduction.md)
* [Threat Hunting Process](threat-hunting-in-m365/threat-hunting-process/README.md)
  * [Hypothesis Generation](threat-hunting-in-m365/threat-hunting-process/hypothesis-generation.md)
  * [Investigation](threat-hunting-in-m365/threat-hunting-process/investigation.md)
  * [Identification](threat-hunting-in-m365/threat-hunting-process/identification.md)
  * [Resolution & Follow Up](threat-hunting-in-m365/threat-hunting-process/resolution-and-follow-up.md)
* [Pyramid of Pain](threat-hunting-in-m365/pyramid-of-pain.md)
* [MITRE Att\&ck](threat-hunting-in-m365/mitre-att-and-ck/README.md)
  * [MITRE Att\&ck Concepts](threat-hunting-in-m365/mitre-att-and-ck/mitre-att-and-ck-concepts.md)
  * [MITRE Data Sources](threat-hunting-in-m365/mitre-att-and-ck/mitre-data-sources.md)
  * [MITRE ATT\&CK Mitigations](threat-hunting-in-m365/mitre-att-and-ck/mitre-att-and-ck-mitigations.md)
  * [Office 365 (Microsoft 365) Enterprise Matrix](threat-hunting-in-m365/mitre-att-and-ck/office-365-microsoft-365-enterprise-matrix.md)
  * [MITRE Att\&ck Stack Mappings: M365](threat-hunting-in-m365/mitre-att-and-ck/mitre-att-and-ck-stack-mappings-m365.md)

## Microsoft 365 References

* [Microsoft 365 References: Good UAL Hunting](microsoft-365-references/microsoft-365-references-good-ual-hunting.md)
