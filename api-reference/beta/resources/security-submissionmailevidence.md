---
title: "submissionMailEvidence resource type"
description: "Represents a user-reported concern over an email, such as reporting an email as Junk/Phish."
author: "MSLironLevy"
ms.localizationpriority: medium
ms.prod: "security"
doc_type: resourcePageType
---

# submissionMailEvidence resource type

Namespace: microsoft.graph.security

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a user-reported concern over an email, such as reporting an email as Junk/Phish.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

| Property           | Type           | Description                                                                                |
|:-------------------|:---------------|:-------------------------------------------------------------------------------------------|
| submissionId       | String         | The Submission Id.                                                                         |
| submissionDateTime | DateTimeOffset | Reported Date time for this submission.                                                    |
| submitter          | String         | The submitter email address.                                                               |
| networkMessageId   | String         | The network message id of email to which submission belongs.                               |
| recipient          | String         | The recipient of the mail.                                                                 |
| sender             | String         | The sender of the mail.                                                                    |
| senderIp           | String         | The sender's IP.                                                                           |
| subject            | String         | The subject of submission mail.                                                            |
| reportType         | String         | The submission type for the given instance. This maps to Junk, Phish, Malware, or NotJunk. |

## Relationships

None.

## JSON representation

The following is a JSON representation of the resource.
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