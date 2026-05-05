---
title: "submissionMailEvidence resource type"
description: "Represents a user-reported concern over an email, such as reporting an email as 'Junk/Phish'."
author: "Lirlev48"
ms.localizationpriority: medium
ms.subservice: "security"
ms.prod: "security"
doc_type: resourcePageType
---

# submissionMailEvidence resource type

Namespace: microsoft.graph.security

Represents a user-reported concern over an email, such as reporting an email as "Junk/Phish".

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

|Property|Type|Description|
|:-------|:---|:----------|
|submissionId|String|The Submission ID.|
|submissionDateTime|DateTimeOffset|The date and time of this submission.|
|submitter|String|The submitter's email address.|
|networkMessageId|String|The network message ID of the email to which the submission belongs.|
|recipient|String|The recipient of the email.|
|sender|String|The sender of the email.|
|senderIp|String|The sender's IP.|
|subject|String|The subject of the submission mail.|
|reportType|String|The submission type for the given instance. That maps to Junk, Phish, Malware, or NotJunk.|

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.security.submissionMailEvidence"
}
-->

``` json
{
"@odata.type": "#microsoft.graph.security.submissionMailEvidence",
"submissionId": "String",
"submissionDateTime": "String (timestamp)",
"submitter": "String",
"networkMessageId": "String",
"recipient": "String",
"sender": "String",
"senderIp": "String",
"subject": "String",
"reportType": "String"
}
```