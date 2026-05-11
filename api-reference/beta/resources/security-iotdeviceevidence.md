---
title: "ioTDeviceEvidence resource type"
description: "Represents an IoT device that is reported as part of the security detection alert."
author: "hareldamti"
ms.localizationpriority: medium
ms.subservice: "security"
doc_type: resourcePageType
ms.date: 05/11/2026
---

# ioTDeviceEvidence resource type

Namespace: microsoft.graph.security

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents an IoT device that is reported as part of the security detection alert.

Inherits from [alertEvidence](./security-alertevidence.md).

## Properties

|Property|Type|Description|
|:-------|:---|:----------|
|createdDateTime|DateTimeOffset|The date and time when the evidence was created and added to the alert. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024 is `2024-01-01T00:00:00Z`. Inherited from [alertEvidence](security-alertevidence.md).|
|detailedRoles|String collection|Detailed description of the entity role or roles in an alert. Values are free-form. Inherited from [alertEvidence](security-alertevidence.md).|
|deviceId|String|The device ID.|
|deviceName|String|The friendly name of the device.|
|devicePageLink|String|The URL to the device page in the IoT Defender portal.|
|deviceSubType|String|The device subtype.|
|deviceType|String|The type of the device. For example, "temperature sensor," "freezer," "wind turbine," and so on.|
|importance|[microsoft.graph.security.ioTDeviceImportanceType](#iotdeviceimportancetype-values)|The importance level for the IoT device. The possible values are: `unknown`, `low`, `normal`, `high`, `unknownFutureValue`.|
|ioTHub|[microsoft.graph.security.azureResourceEvidence](./security-azureresourceevidence.md)|The **azureResourceEvidence** entity that represents the IoT Hub that the device belongs to.|
|ioTSecurityAgentId|String|The ID of the Azure Security Center for the IoT agent that is running on the device.|
|ipAddress|[microsoft.graph.security.ipEvidence](./security-ipevidence.md)|The current IP address of the device.|
|isAuthorized|Boolean|Indicates whether the device classified as an authorized device.|
|isProgramming|Boolean|Indicates whether the device classified as a programming device.|
|isScanner|Boolean|Indicates whether the device classified as a scanner.|
|macAddress|String|The MAC address of the device.|
|manufacturer|String|The manufacturer of the device.|
|model|String|The model of the device.|
|nics|[microsoft.graph.security.nicEvidence](./security-nicevidence.md) collection|The current network interface controllers on the device.|
|operatingSystem|String|The operating system the device is running.|
|owners|String collection|The owners for the device.|
|protocols|String collection|The list of protocols that the device supports.|
|purdueLayer|String|The Purdue Layer of the device.|
|remediationStatus|[microsoft.graph.security.evidenceRemediationStatus](security-alertevidence.md#evidenceremediationstatus-values)|Status of the remediation action taken. The possible values are: `none`, `remediated`, `prevented`, `blocked`, `notFound`, `unknownFutureValue`, `active`, `pendingApproval`, `declined`, `unremediated`, `running`, `partiallyRemediated`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `active`, `pendingApproval`, `declined`, `unremediated`, `running`, `partiallyRemediated`. Inherited from [alertEvidence](security-alertevidence.md).|
|remediationStatusDetails|String|Details about the remediation status. Inherited from [alertEvidence](security-alertevidence.md).|
|roles|[microsoft.graph.security.evidenceRole](security-alertevidence.md#evidencerole-values) collection|The role or roles that an evidence entity represents in an alert, for example, an IP address that is associated with an attacker has the evidence role **Attacker**. Inherited from [alertEvidence](security-alertevidence.md).|
|sensor|String|The sensor that monitors the device.|
|serialNumber|String|The serial number of the device.|
|site|String|The site location of the device.|
|source|String|The source (microsoft/vendor) of the device entity.|
|sourceRef|[microsoft.graph.security.urlEvidence](./security-urlevidence.md)|A URL reference to the source item where the device is managed.|
|tags|String collection|Array of custom tags associated with an evidence instance, for example, to denote a group of devices and high-value assets. Inherited from [alertEvidence](security-alertevidence.md).|
|verdict|[microsoft.graph.security.evidenceVerdict](security-alertevidence.md#evidenceverdict-values)|The decision reached by automated investigation. The possible values are: `unknown`, `suspicious`, `malicious`, `noThreatsFound`, `unknownFutureValue`. Inherited from [alertEvidence](security-alertevidence.md).|
|zone|String|The zone location of the device within a site.|

### ioTDeviceImportanceType values

|Member|Description|
|:-----|:----------|
|unknown|The importance is unknown. Default value.|
|low|The importance is low.|
|normal|The importance is normal.|
|high|The importance is high.|
|unknownFutureValue|Evolvable enumeration sentinel value. Don't use.|

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.security.ioTDeviceEvidence",
  "baseType": "microsoft.graph.security.alertEvidence"
}
-->

``` json
{
  "@odata.type": "#microsoft.graph.security.ioTDeviceEvidence",
  "createdDateTime": "String (timestamp)",
  "verdict": "String",
  "remediationStatus": "String",
  "remediationStatusDetails": "String",
  "roles": [
    "String"
  ],
  "detailedRoles": [
    "String"
  ],
  "tags": [
    "String"
  ],
  "ioTHub": {
    "@odata.type": "microsoft.graph.security.azureResourceEvidence"
  },
  "deviceId": "String",
  "deviceName": "String",
  "owners": [
    "String"
  ],
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
  "nics": [
    {
      "@odata.type": "microsoft.graph.security.nicEvidence"
    }
  ],
  "protocols": [
    "String"
  ],
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
