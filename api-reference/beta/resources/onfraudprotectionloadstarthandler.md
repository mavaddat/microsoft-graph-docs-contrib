---
title: "onFraudProtectionLoadStartHandler resource type"
description: "Used for configuring the third-party fraud protection provider Microsoft Entra external ID tenants."
author: "more-rasika"
ms.date: 08/05/2025
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: resourcePageType
---

# onFraudProtectionLoadStartHandler resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a handler that executes when a fraud protection load start listener is triggered in Microsoft Entra ID. This abstract resource allows you to define third-party integrations for fraud protection.

This is an abstract type from which the [onFraudProtectionLoadStartExternalUsersAuthHandler](../resources/onFraudProtectionLoadStartExternalUsersAuthHandler.md) subtype is derived.


## Properties
None.

## Relationships
None.

## JSON representation
The following JSON representation shows the resource type.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.onFraudProtectionLoadStartHandler"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.onFraudProtectionLoadStartHandler"
}
```

