---
title: "dnsEvidence resource type"
description: "A DNS that is reported in the alert as evidence."
author: "OfirBelenky"
ms.localizationpriority: medium
ms.subservice: "security"
doc_type: resourcePageType
ms.date: 05/07/2026
---

# dnsEvidence resource type

Namespace: microsoft.graph.security

A DNS that is reported in the alert as evidence.

Inherits from [alertEvidence](../resources/security-alertevidence.md).

## Properties

|Property|Type|Description|
|:------------|:-------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------|
|domainName|String|The name of the DNS record associated with the alert.|
|ipAddresses|[microsoft.graph.security.ipEvidence](security-ipevidence.md) collection|Entities of type 'ip' for the resolved IP address.|
|dnsServerIp|[microsoft.graph.security.ipEvidence](security-ipevidence.md)|An entity of type 'ip' for the DNS server resolving the request.|
|hostIpAddress|[microsoft.graph.security.ipEvidence](security-ipevidence.md)|An entity of type 'ip' for the DNS request client.|

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.security.dnsEvidence"
}
-->

``` json
{
  "@odata.type": "#microsoft.graph.security.dnsEvidence",
  "domainName": "String",
  "ipAddresses": [
    {
      "@odata.type": "microsoft.graph.security.ipEvidence"
    }
  ],
  "dnsServerIp": {
    "@odata.type": "microsoft.graph.security.ipEvidence"
  },
  "hostIpAddress": {
    "@odata.type": "microsoft.graph.security.ipEvidence"
  }
}
```