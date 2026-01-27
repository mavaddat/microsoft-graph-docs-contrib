---
title: "onPasswordSubmitHandler resource type"
description: "Abstract base type for handlers that process the OnPasswordSubmit authentication event."
author: "diadabal"
ms.date: 01/13/2026
ms.localizationpriority: medium
ms.subservice: "entra-sign-in"
doc_type: resourcePageType
---

# onPasswordSubmitHandler resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Abstract base type for handlers that can be invoked when an OnPasswordSubmit authentication event occurs. This type defines the contract for all handlers that process password submission events in the authentication flow.

Concrete implementations of this handler type include:
- [onPasswordMigrationCustomExtensionHandler](../resources/onpasswordmigrationcustomextensionhandler.md) - Invokes a custom extension API for password validation during Just-In-Time migration scenarios

This is an abstract type and cannot be instantiated directly. Use one of the derived types to configure a handler for the OnPasswordSubmit event.

## Properties

This is an abstract type with no properties. Derived types may define additional properties.

## Relationships
None.

## JSON representation

This is an abstract type. The JSON representation is determined by the derived type.
