---
title: "contentActivityMetadata resource type"
description: "Represents metadata for a content entry of enforcement result status."
author: "zhengnlu"
ms.date: 12/20/2025
ms.localizationpriority: medium
ms.subservice: "security"
doc_type: resourcePageType
---

# Enforcement Result Status is used when:
A DLP policy matched, and enforcement is done by another system (browser, network, app), not Purview itself

Tells the admin:
Was the action actually enforced?
Did the user override?
Did enforcement fail?
Did we never get confirmation?

Typical examples:
Browser DLP block succeeded or failed
User clicked Override
Enforcement timed out or agent failed
No enforcement confirmation was ever received

So:
1. RuleMatch = "policy matched"
2. Enforcement Result Status = "what really happened during enforcement"

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
| enforcementResultStatus          | microsoft.graph.security.enforcementResultStatus                                                                         | The status of the enforcement result. The possible values are: `success`, `missingOrInvalidConfiguration`, `userOverride`, `agentFailure`, `enforcementTimeout`, `oSOverride`, `processNonExistent`, `other`, `unknownFutureValue`.                                           |
| identifier       | String                                                                         | A unique identifier for this specific content entry within the context of the calling application or the enforcement plane; for example, message ID, file path, or file URL. Required. Inherited from [processContentMetadataBase](../resources/processcontentmetadatabase.md).|
| isTruncated      | Boolean                                                                        | Indicates whether the provided **content** was shortened from its original form; for example, due to size limits. Required. Inherited from [processContentMetadataBase](../resources/processcontentmetadatabase.md).|
| length           | Int64                                                                          | The length of the original content in bytes. Inherited from [processContentMetadataBase](../resources/processcontentmetadatabase.md). |
| modifiedDateTime | DateTimeOffset                                                                 | Date and time when the original content was last modified. For ephemeral content, such as messages, this property might be the same as **createdDateTime**. Required. Inherited from [processContentMetadataBase](../resources/processcontentmetadatabase.md).|
| name             | String                                                                         | A descriptive name for the content; for example, file name, web page title, or `Chat message`. Required. Inherited from [processContentMetadataBase](../resources/processcontentmetadatabase.md).|
| recordType       | microsoft.graph.security.auditLogRecordType                                    | The type of operation indicated by the record, currently it's reserved to indicate the ComplianceDLPEnforcement. |
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

Example of request body call to PICS Tier 0 ContentActivity API,
``` json
{
    "userId": "2c0dace9-c689-4d01-b5da-e95f10eff879",
    "contentMetadata": {
        "contentEntries": [
            {
                "accessedResources": [],
                "plugins": [
                    {
                        "identifier": "123123123",
                        "name": "Test plugin",
                        "version": "1.0.0"
                    }
                ],
                "identifier": "0",
                "name": "subject",
                "correlationId": "03402456-0126-4404-be03-429bfe211a24",
                "sequenceNumber": 0,
                "length": 0,
                "isTruncated": false,
                "createdDateTime": "2025-07-03T22:02:08.5393995+00:00",
                "modifiedDateTime": "2025-07-03T22:02:08.5393995+00:00",
                "RecordType": "ComplianceDLPEnforcement",
                "EnforcementResultStatus": "Success",
                "@odata.type": "microsoft.graph.contentActivityMetadata"
            }
        ],
        "activityMetadata": {
            "activity": "UploadFile"
        },
        "deviceMetadata": {
            "ipAddress": "10.0.0.0",
            "operatingSystemSpecifications": {
                "operatingSystemPlatform": "windows",
                "operatingSystemVersion": "11"
            }
        },
        "protectedAppMetadata": {
            "version": "1.0"
        },
        "integratedAppMetadata": {
            "name": "integratedApp",
            "version": "1.0"
        }
    }
}
```
