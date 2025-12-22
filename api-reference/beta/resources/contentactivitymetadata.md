---
title: "contentActivityMetadata resource type"
description: "Represents metadata for a content entry of enforcement result status."
author: "zhengnlu"
ms.date: 12/20/2025
ms.localizationpriority: medium
ms.subservice: "security"
doc_type: resourcePageType
---

# contentActivityMetadata resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents metadata for a content entry of an enforcement result status.

Inherits from [processContentMetadataBase](../resources/processcontentmetadatabase.md).

## Properties

| Property         | Type                                                                                                     | Description                                                                                                           |
| :--------------- | :------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------- |
| content          | [contentBase](../resources/contentbase.md)  | Represents the actual content, either as text ([textContent](../resources/textcontent.md)) or binary data ([binaryContent](../resources/binarycontent.md)). Optional if metadata alone is sufficient for policy evaluation. *Don't use to [Create contentActivity](../api/activitiescontainer-post-contentactivities.md).* Inherited from [processContentMetadataBase](../resources/processcontentmetadatabase.md).|
| correlationId    | String                                                                         | An identifier used to group multiple related content entries; for example, different parts of the same file upload or messages in a conversation. Inherited from [processContentMetadataBase](../resources/processcontentmetadatabase.md). |
| createdDateTime  | DateTimeOffset                                                                 | The date and time when the original content was created; for example, file creation time or message sent time. Required. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [processContentMetadataBase](../resources/processcontentmetadatabase.md). |
| enforcementResultStatus          | String                                                                         | The status of the enforcement result.                                            |
| identifier       | String                                                                         | A unique identifier for this specific content entry within the context of the calling application or the enforcement plane; for example, message ID, file path, or file URL. Required. Inherited from [processContentMetadataBase](../resources/processcontentmetadatabase.md).|
| isTruncated      | Boolean                                                                        | Indicates whether the provided **content** was shortened from its original form; for example, due to size limits. Required. Inherited from [processContentMetadataBase](../resources/processcontentmetadatabase.md).|
| length           | Int64                                                                          | The length of the original content in bytes. Inherited from [processContentMetadataBase](../resources/processcontentmetadatabase.md). |
| modifiedDateTime | DateTimeOffset                                                                 | Date and time when the original content was last modified. For ephemeral content, such as messages, this property might be the same as **createdDateTime**. Required. Inherited from [processContentMetadataBase](../resources/processcontentmetadatabase.md).|
| name             | String                                                                         | A descriptive name for the content; for example, file name, web page title, or `Chat message`. Required. Inherited from [processContentMetadataBase](../resources/processcontentmetadatabase.md).|
| recordType  | microsoft.graph.security.auditLogRecordType                              | The type of operation indicated by the record. The possible values are: `exchangeAdmin`, `exchangeItem`, `exchangeItemGroup`, `sharePoint`, `syntheticProbe`, `sharePointFileOperation`, `oneDrive`, `azureActiveDirectory`, `azureActiveDirectoryAccountLogon`, `dataCenterSecurityCmdlet`, `complianceDLPSharePoint`, `sway`, `complianceDLPExchange`, `sharePointSharingOperation`, `azureActiveDirectoryStsLogon`, `skypeForBusinessPSTNUsage`, `skypeForBusinessUsersBlocked`, `securityComplianceCenterEOPCmdlet`, `exchangeAggregatedOperation`, `powerBIAudit`, `crm`, `yammer`, `skypeForBusinessCmdlets`, `discovery`, `microsoftTeams`, `threatIntelligence`, `mailSubmission`, `microsoftFlow`, `aeD`, `microsoftStream`, `complianceDLPSharePointClassification`, `threatFinder`, `project`, `sharePointListOperation`, `sharePointCommentOperation`, `dataGovernance`, `kaizala`, `securityComplianceAlerts`, `threatIntelligenceUrl`, `securityComplianceInsights`, `mipLabel`, `workplaceAnalytics`, `powerAppsApp`, `powerAppsPlan`, `threatIntelligenceAtpContent`, `labelContentExplorer`, `teamsHealthcare`, `exchangeItemAggregated`, `hygieneEvent`, `dataInsightsRestApiAudit`, `informationBarrierPolicyApplication`, `sharePointListItemOperation`, `sharePointContentTypeOperation`, `sharePointFieldOperation`, `microsoftTeamsAdmin`, `hrSignal`, `microsoftTeamsDevice`, `microsoftTeamsAnalytics`, `informationWorkerProtection`, `campaign`, `dlpEndpoint`, `airInvestigation`, `quarantine`, `microsoftForms`, `applicationAudit`, `complianceSupervisionExchange`, `customerKeyServiceEncryption`, `officeNative`, `mipAutoLabelSharePointItem`, `mipAutoLabelSharePointPolicyLocation`, `microsoftTeamsShifts`, `secureScore`, `mipAutoLabelExchangeItem`, `cortanaBriefing`, `search`, `wdatpAlerts`, `powerPlatformAdminDlp`, `powerPlatformAdminEnvironment`, `mdatpAudit`, `sensitivityLabelPolicyMatch`, `sensitivityLabelAction`, `sensitivityLabeledFileAction`, `attackSim`, `airManualInvestigation`, `securityComplianceRBAC`, `userTraining`, `airAdminActionInvestigation`, `mstic`, `physicalBadgingSignal`, `teamsEasyApprovals`, `aipDiscover`, `aipSensitivityLabelAction`, `aipProtectionAction`, `aipFileDeleted`, `aipHeartBeat`, `mcasAlerts`, `onPremisesFileShareScannerDlp`, `onPremisesSharePointScannerDlp`, `exchangeSearch`, `sharePointSearch`, `privacyDataMinimization`, `labelAnalyticsAggregate`, `myAnalyticsSettings`, `securityComplianceUserChange`, `complianceDLPExchangeClassification`, `complianceDLPEndpoint`, `mipExactDataMatch`, `msdeResponseActions`, `msdeGeneralSettings`, `msdeIndicatorsSettings`, `ms365DCustomDetection`, `msdeRolesSettings`, `mapgAlerts`, `mapgPolicy`, `mapgRemediation`, `privacyRemediationAction`, `privacyDigestEmail`, `mipAutoLabelSimulationProgress`, `mipAutoLabelSimulationCompletion`, `mipAutoLabelProgressFeedback`, `dlpSensitiveInformationType`, `mipAutoLabelSimulationStatistics`, `largeContentMetadata`, `microsoft365Group`, `cdpMlInferencingResult`, `filteringMailMetadata`, `cdpClassificationMailItem`, `cdpClassificationDocument`, `officeScriptsRunAction`, `filteringPostMailDeliveryAction`, `cdpUnifiedFeedback`, `tenantAllowBlockList`, `consumptionResource`, `healthcareSignal`, `dlpImportResult`, `cdpCompliancePolicyExecution`, `multiStageDisposition`, `privacyDataMatch`, `filteringDocMetadata`, `filteringEmailFeatures`, `powerBIDlp`, `filteringUrlInfo`, `filteringAttachmentInfo`, `coreReportingSettings`, `complianceConnector`, `powerPlatformLockboxResourceAccessRequest`, `powerPlatformLockboxResourceCommand`, `cdpPredictiveCodingLabel`, `cdpCompliancePolicyUserFeedback`, `webpageActivityEndpoint`, `omePortal`, `cmImprovementActionChange`, `filteringUrlClick`, `mipLabelAnalyticsAuditRecord`, `filteringEntityEvent`, `filteringRuleHits`, `filteringMailSubmission`, `labelExplorer`, `microsoftManagedServicePlatform`, `powerPlatformServiceActivity`, `scorePlatformGenericAuditRecord`, `filteringTimeTravelDocMetadata`, `alert`, `alertStatus`, `alertIncident`, `incidentStatus`, `case`, `caseInvestigation`, `recordsManagement`, `privacyRemediation`, `dataShareOperation`, `cdpDlpSensitive`, `ehrConnector`, `filteringMailGradingResult`, `publicFolder`, `privacyTenantAuditHistoryRecord`, `aipScannerDiscoverEvent`, `eduDataLakeDownloadOperation`, `m365ComplianceConnector`, `microsoftGraphDataConnectOperation`, `microsoftPurview`, `filteringEmailContentFeatures`, `powerPagesSite`, `powerAppsResource`, `plannerPlan`, `plannerCopyPlan`, `plannerTask`, `plannerRoster`, `plannerPlanList`, `plannerTaskList`, `plannerTenantSettings`, `projectForTheWebProject`, `projectForTheWebTask`, `projectForTheWebRoadmap`, `projectForTheWebRoadmapItem`, `projectForTheWebProjectSettings`, `projectForTheWebRoadmapSettings`, `quarantineMetadata`, `microsoftTodoAudit`, `timeTravelFilteringDocMetadata`, `teamsQuarantineMetadata`, `sharePointAppPermissionOperation`, `microsoftTeamsSensitivityLabelAction`, `filteringTeamsMetadata`, `filteringTeamsUrlInfo`, `filteringTeamsPostDeliveryAction`, `mdcAssessments`, `mdcRegulatoryComplianceStandards`, `mdcRegulatoryComplianceControls`, `mdcRegulatoryComplianceAssessments`, `mdcSecurityConnectors`, `mdaDataSecuritySignal`, `vivaGoals`, `filteringRuntimeInfo`, `attackSimAdmin`, `microsoftGraphDataConnectConsent`, `filteringAtpDetonationInfo`, `privacyPortal`, `managedTenants`, `unifiedSimulationMatchedItem`, `unifiedSimulationSummary`, `updateQuarantineMetadata`, `ms365DSuppressionRule`, `purviewDataMapOperation`, `filteringUrlPostClickAction`, `irmUserDefinedDetectionSignal`, `teamsUpdates`, `plannerRosterSensitivityLabel`, `ms365DIncident`, `filteringDelistingMetadata`, `complianceDLPSharePointClassificationExtended`, `microsoftDefenderForIdentityAudit`, `supervisoryReviewDayXInsight`, `defenderExpertsforXDRAdmin`, `cdpEdgeBlockedMessage`, `hostedRpa`, `cdpContentExplorerAggregateRecord`, `cdpHygieneAttachmentInfo`, `cdpHygieneSummary`, `cdpPostMailDeliveryAction`, `cdpEmailFeatures`, `cdpHygieneUrlInfo`, `cdpUrlClick`, `cdpPackageManagerHygieneEvent`, `filteringDocScan`, `timeTravelFilteringDocScan`, `mapgOnboard`, `complianceDLPEnforcement`, `unknownFutureValue`. |
| sequenceNumber   | Int64                                                                          | A sequence number that indicates the order in which content was generated or should be processed. Required when **correlationId** is used. Inherited from [processContentMetadataBase](../resources/processcontentmetadatabase.md).            |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.contentActivityMetadata",
  "baseType": "microsoft.graph.processContentMetadataBase",
  "openType": false
}-->
``` json
{
  "@odata.type": "#microsoft.graph.contentActivityMetadata",
  "content": { "@odata.type": "microsoft.graph.binaryContent" }, 
  "correlationId": "String",
  "createdDateTime": "String (timestamp)",
  "enforcementResultStatus": "String",
  "identifier": "String", 
  "isTruncated": "Boolean",
  "length": "Int64",
  "modifiedDateTime": "String (timestamp)",
  "name": "String", 
  "recordType": "String",
  "sequenceNumber": "Int64"
}
```
