---
title: "ioTDeviceEvidence resource type"
description: "Represents an IoT Device reported as part of a security detection alert."
author: "MSLironLevy"
ms.localizationpriority: medium
ms.prod: "security"
doc_type: resourcePageType
---

# ioTDeviceEvidence resource type

Namespace: microsoft.graph.security

Represents an IoT Device that is reported as part of the security detection alert.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

| Property           | Type                                                                                  | Description                                                                                                                                                |
|:-------------------|:--------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| ioTHub             | [microsoft.graph.security.azureResourceEvidence](./security-azureresourceevidence.md) | The AzureResource entity representing the IoT Hub the device belongs to.                                                                                   |
| deviceId           | String                                                                                | The ID of the device resource.                                                                                                                             |
| deviceName         | String                                                                                | The friendly name of the device.                                                                                                                           |
| owners             | String Collection                                                                     | The owners for the device.                                                                                                                                 |
| ioTSecurityAgentId | String                                                                                | The ID of the Azure Security Center for IoT agent running on the device.                                                                                   |
| deviceType         | String                                                                                | The type of the device ('temperature sensor', 'freezer', 'wind turbine' etc.).                                                                             |
| source             | String                                                                                | The source (microsoft/vendor) of the device entity.                                                                                                        |
| sourceRef          | [microsoft.graph.security.urlEvidence](./security-urlevidence.md)                     | A URL reference to the source item where the device is managed.                                                                                            |
| manufacturer       | String                                                                                | The manufacturer of the device.                                                                                                                            |
| model              | String                                                                                | The model of the device.                                                                                                                                   |
| operatingSystem    | String                                                                                | The operating system the device is running.                                                                                                                |
| ipAddress          | [microsoft.graph.security.ipEvidence](./security-ipevidence.md)                       | The current IP address of the device.                                                                                                                      |
| macAddress         | String                                                                                | The MAC address of the device.                                                                                                                             |
| nics               | [microsoft.graph.security.nicEvidence](./security-nicevidence.md)                     | The current Nics on the device.                                                                                                                            |
| protocols          | String Collection                                                                     | A list of protocols that the device supports.                                                                                                              |
| serialNumber       | String                                                                                | The serial number of the device.                                                                                                                           |
| site               | String                                                                                | The site location of the device.                                                                                                                           |
| zone               | String                                                                                | The zone location of the device within a site.                                                                                                             |
| sensor             | String                                                                                | The sensor the device is monitored by.                                                                                                                     |
| importance         | [microsoft.graph.security.ioTDeviceImportanceType](#ioTDeviceImportanceType-values)   | The importance of the IoT Device.                                                                                                                          |
| purdueLayer        | String                                                                                | The Purdue Layer of the device.                                                                                                                            |
| isProgramming      | Boolean                                                                               | Determines whether the device is classified as a programming device.                                                                                       |
| isAuthorized       | Boolean                                                                               | Determines whether the device is classified as an authorized device.                                                                                       |
| isScanner          | Boolean                                                                               | Determines whether the device is classified as a scanner device.                                                                                           |
| devicePageLink     | String                                                                                | A URL to the device page in IoT Defender portal.                                                                                                           |
| deviceSubType      | String                                                                                | The name of the device sub type.                                                                                                                           |

#### ioTDeviceImportanceType values

| Member             | Description                             |
|:-------------------|:----------------------------------------|
| unknown            | Unknown - Default value                 |
| low                | Low                                     |
| normal             | Normal                                  |
| high               | High                                    |
| unknownFutureValue | Evolvable enumeration value. Don't use. |

## Relationships

None.

## JSON representation

The following is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.security.kubernetesServiceEvidence"
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