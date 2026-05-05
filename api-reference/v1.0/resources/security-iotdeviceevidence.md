---
title: "ioTDeviceEvidence resource type"
description: "Represents an IoT Device reported in a security detection alert."
author: "Lirlev48"
ms.localizationpriority: medium
ms.prod: "security"
doc_type: resourcePageType
---

# ioTDeviceEvidence resource type

Namespace: microsoft.graph.security

Represents an IoT Device that is reported in the security detection alert.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

|Property|Type|Description|
|:-------|:---|:----------|
|deviceId|String|The ID of the device resource.|
|deviceName|String|The friendly name of the device.|
|devicePageLink|String|A URL to the device page in IoT Defender portal.|
|deviceSubType|String|The name of the device subtype.|
|deviceType|String|The type of the device. For example, 'temperature sensor', 'freezer', 'wind turbine', and so on.|
|importance|[microsoft.graph.security.ioTDeviceImportanceType](#iotdeviceimportancetype-values )|The importance of the IoT Device.|
|ioTHub|[microsoft.graph.security.azureResourceEvidence](./security-azureresourceevidence.md)|The AzureResource entity that represents the IoT Hub the device belongs to.|
|ioTSecurityAgentId|String|The ID of the Azure Security Center for IoT agent running on the device.|
|ipAddress|[microsoft.graph.security.ipEvidence](./security-ipevidence.md)|The current IP address of the device.|
|isAuthorized|Boolean|Whether the device is an authorized device.|
|isProgramming|Boolean|Whether the device is a programming device.|
|isScanner|Boolean|Whether the device is a scanner device.|
|macAddress|String|The MAC address of the device.|
|manufacturer|String|The manufacturer of the device.|
|model|String|The model of the device.|
|nics|[microsoft.graph.security.nicEvidence](./security-nicevidence.md)|The current NICs on the device.|
|operatingSystem|String|The operating system the device is running.|
|owners|String Collection|The owners of the device.|
|protocols|String Collection|A list of protocols that the device supports.|
|purdueLayer|String|The Purdue Layer of the device.|
|sensor|String|The sensor that monitors the device.|
|serialNumber|String|The serial number of the device.|
|site|String|The site location of the device.|
|source|String|The source of the device entity. The  possible values are: 'microsoft', 'vendor'.|
|sourceRef|[microsoft.graph.security.urlEvidence](./security-urlevidence.md)|A URL reference to the source item where the device is managed.|
|zone|String|The zone location of the device within a site.|

#### ioTDeviceImportanceType values

|Member|Description|
|:-----|:----------|
|unknown|The importance is unknown. Default value.|
|low|The importance is low.|
|normal|The importance is normal.|
|high|The importance is high.|
|unknownFutureValue|Evolvable enumeration value. Don't use.|

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.security.ioTDeviceEvidence"
}
-->

``` json
{
  "@odata.type": "#microsoft.graph.security.ioTDeviceEvidence",
  "ioTHub": {
    "@odata.type": "microsoft.graph.security.azureResourceEvidence"
  },
  "deviceId": "String",
  "deviceName": "String",
  "owners": ["String"],
  "ioTSecurityAgentId": "String",
  "deviceType": "String",
  "source": "String",
  "sourceRef": {
    "@odata.type": "microsoft.graph.security.urlEvidence"
  },
  "manufacturer": "String",
  "model": "String",
  "operatingSystem": "String",
  "ipAddress": {
    "@odata.type": "microsoft.graph.security.ipEvidence"
  },
  "macAddress": "String",
  "nics": {
    "@odata.type": "microsoft.graph.security.nicEvidence"
  },
  "protocols": ["String"],
  "serialNumber": "String",
  "site": "String",
  "zone": "String",
  "sensor": "String",
  "importance": "String",
  "purdueLayer": "String",
  "isProgramming": "Boolean",
  "isAuthorized": "Boolean",
  "isScanner": "Boolean",
  "devicePageLink": "String",
  "deviceSubType": "String"
}
```