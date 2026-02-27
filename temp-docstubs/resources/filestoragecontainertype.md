---
title: "fileStorageContainerType resource type"
description: "Represents a container type in SharePoint Embedded that defines the billing, settings, and ownership configuration for file storage containers."
author: "grjoseph"
ms.date: 02/27/2026
ms.localizationpriority: medium
ms.subservice: "sharepoint-embedded"
doc_type: resourcePageType
---

# fileStorageContainerType resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents a container type in SharePoint Embedded that defines the billing, settings, and ownership configuration for file storage containers. A container type is registered by an owning application and controls the lifecycle, billing tier, and access policies for all [fileStorageContainer](../resources/filestoragecontainer.md) instances created under it.

Each application can own only one container type. The container type determines the billing relationship (standard, trial, or direct-to-customer), expiration behavior, and sharing and access settings for all containers of that type.

Container types use an ownership-based authorization model. Access is controlled through a **permissions** collection on each container type. Users listed in the permissions collection with the `owner` role can manage the container type (read, update, delete, and manage permissions). SharePoint Embedded Administrators and Global Administrators bypass the permissions check and can manage all container types in the tenant. Guest users cannot perform any container type operations.

Inherits from [entity](../resources/entity.md).

## Methods

|Method|Return type|Description|
|:---|:---|:---|
|[List](../api/filestorage-list-containertypes.md)|[fileStorageContainerType](../resources/filestoragecontainertype.md) collection|Get a list of the [fileStorageContainerType](../resources/filestoragecontainertype.md) objects and their properties.|
|[Create](../api/filestorage-post-containertypes.md)|[fileStorageContainerType](../resources/filestoragecontainertype.md)|Create a new [fileStorageContainerType](../resources/filestoragecontainertype.md) object.|
|[Get](../api/filestoragecontainertype-get.md)|[fileStorageContainerType](../resources/filestoragecontainertype.md)|Read the properties and relationships of a [fileStorageContainerType](../resources/filestoragecontainertype.md) object.|
|[Update](../api/filestoragecontainertype-update.md)|[fileStorageContainerType](../resources/filestoragecontainertype.md)|Update the properties of a [fileStorageContainerType](../resources/filestoragecontainertype.md) object.|
|[Delete](../api/filestorage-delete-containertypes.md)|None|Delete a [fileStorageContainerType](../resources/filestoragecontainertype.md) object.|
|[List permissions](../api/filestoragecontainertype-list-permissions.md)|[permission](../resources/permission.md) collection|Get the list of permissions on a [fileStorageContainerType](../resources/filestoragecontainertype.md).|
|[Create permission](../api/filestoragecontainertype-post-permissions.md)|[permission](../resources/permission.md)|Add an owner permission to a [fileStorageContainerType](../resources/filestoragecontainertype.md).|
|[Get permission](../api/filestoragecontainertype-get-permission.md)|[permission](../resources/permission.md)|Read a specific permission on a [fileStorageContainerType](../resources/filestoragecontainertype.md).|
|[Delete permission](../api/filestoragecontainertype-delete-permissions.md)|None|Remove a permission from a [fileStorageContainerType](../resources/filestoragecontainertype.md).|

## Properties

|Property|Type|Description|
|:---|:---|:---|
|billingClassification|fileStorageContainerBillingClassification|Indicates the billing tier for the container type. The possible values are: `standard`, `trial`, `directToCustomer`, `unknownFutureValue`.|
|billingStatus|fileStorageContainerBillingStatus|The current billing status of the container type. Read-only. The possible values are: `invalid`, `valid`, `unknownFutureValue`.|
|createdDateTime|DateTimeOffset|Date and time when the container type was created. Read-only.|
|etag|String|An opaque string value used for optimistic concurrency control during updates. Pass this value in the `If-Match` request header when updating the container type. Read-only.|
|expirationDateTime|DateTimeOffset|Date and time when the container type expires. Read-only.|
|id|String|The unique identifier for the container type. Read-only. Inherited from [entity](../resources/entity.md).|
|name|String|The display name of the container type.|
|owningAppId|Guid|The identifier of the application that owns this container type. Read-only.|
|settings|[fileStorageContainerTypeSettings](../resources/filestoragecontainertypesettings.md)|Configuration settings for the container type, including sharing and access policies.|

## Relationships

|Relationship|Type|Description|
|:---|:---|:---|
|permissions|[permission](../resources/permission.md) collection|The collection of user permissions on this container type. Only users with the `owner` role are supported. A maximum of three permissions can be assigned to a container type. Not returned by default. Use `$expand=permissions` to include this relationship in the response.|

## Authorization model

Container types use a two-tier authorization model:

1. **Application-level**: The container type is bound to its owning application through `owningAppId`. The calling application must match.
2. **User-level**: The calling user must appear in the `permissions` collection with the `owner` role, unless the user is a SharePoint Embedded Administrator or Global Administrator, who bypass the permissions check.

Guest users are blocked from all container type operations.

For container types without any permissions (legacy or after all permissions are removed), only administrators can manage the container type.

> [!NOTE]
> The ability for non-admin users to create container types is controlled by the `canDevelopersCreateContainerTypes` feature flag in your tenant's SharePoint Embedded settings. When this flag is disabled, only SharePoint Embedded Administrators and Global Administrators can create container types.

## JSON representation

The following JSON representation shows the resource type.

<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.fileStorageContainerType",
  "baseType": "microsoft.graph.entity",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.fileStorageContainerType",
  "id": "String (identifier)",
  "name": "String",
  "owningAppId": "Guid",
  "billingClassification": "String",
  "billingStatus": "String",
  "createdDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)",
  "settings": {
    "@odata.type": "microsoft.graph.fileStorageContainerTypeSettings"
  },
  "etag": "String"
}
```
