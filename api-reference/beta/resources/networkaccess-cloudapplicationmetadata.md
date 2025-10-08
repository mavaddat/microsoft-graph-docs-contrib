---
title: "cloudApplicationMetadata resource type"
description: "Represents data related to a SaaS application in Global Secure Access network traffic."
author: "miritsadon"
ms.date: 08/10/2025
ms.localizationpriority: medium
ms.subservice: "entra-global-secure-access"
doc_type: resourcePageType
---

# cloudApplicationMetadata resource type

Namespace: microsoft.graph.networkaccess

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents data related to a SaaS application in Global Secure Access [network traffic](../resources/networkaccess-networkaccesstraffic.md).


## Properties
|Property|Type|Description|
|:---|:---|:---|
|category|microsoft.graph.networkaccess.cloudApplicationCategory|The category of the SaaS application. The possible values are: `hostingServices`, `itServices`, `accountingAndFinance`, `businessManagement`, `productivity`, `eCommerce`, `education`, `marketing`, `humanResourceManagement`, `health`, `security`, `generativeAi`, `newsAndEntertainment`, `operationsManagement`, `contentManagement`, `developmentTools`, `collaboration`, `crm`, `communications`, `dataAnalytics`, `advertising`, `supplyChainAndLogistics`, `projectManagement`, `transportationAndTravel`, `cloudComputingPlatform`, `businessIntelligence`, `cloudStorage`, `propertyManagement`, `contentSharing`, `customerSupport`, `sales`, `productDesign`, `socialNetwork`, `onlineMeetings`, `webmail`, `internetOfThings`, `forums`, `webAnalytics`, `websiteMonitoring`, `vendorManagementSystem`, `personalInstantMessaging`, `codeHosting`, `unknownFutureValue`.|
|cloudApplicationCatalogId|String|The ID of the application in the SaaS application catalog.|
|complianceScore|Int32|The compliance score of the application.|
|generalScore|Int32|The general score of the application.|
|legalScore|Int32|The legal score of the application.|
|loginUser|String|The username that was used to log into the application.|
|name|String|The name of the application (e.g., ChatGPT, Salesforce, Bing).|
|riskScore|Int32|The risk score of the application.|
|securityScore|Int32|The security score of the application.|

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.networkaccess.cloudApplicationMetadata"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.networkaccess.cloudApplicationMetadata",
  "cloudApplicationCatalogId": "String",
  "name": "String",
  "category": "String",
  "generalScore": "Integer",
  "riskScore": "Integer",
  "complianceScore": "Integer",
  "legalScore": "Integer",
  "loginUser": "String",
  "securityScore": "Integer"
}
```
