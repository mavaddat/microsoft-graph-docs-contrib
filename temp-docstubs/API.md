# SharePoint Embedded - FileStorageContainerType Permissions Property and Authorization Updates

[Related Work Item](https://dev.azure.com/microsoftgraph/c524a71e-ec9c-42bd-936b-81233fb9baf8/_workitems/edit/29400)


## Contacts

| Role | Name                   |
| ---- | ---------------------- |
| PM  | Marc Windle mawin |
| Eng   | Gregory Joseph grjoseph |
| Eng  | Diego Luces dilucesr |

## API quality checklist

[API quality checklist](https://microsoft.sharepoint-df.com/:x:/t/MicrosoftGraphAPIQuality/EUaezq2RgIlIg4C7NF0ThSMBrDMDivrQX18sfU_QGHdrFg?e=AvniYR)

## Scenarios and personas

The updated `FileStorageContainerType.Manage.All` permission introduces an ownership-based authorization model for SharePoint Embedded Container Types through the new `permissions` navigation property, enabling applications to manage container types without requiring SharePoint Embedded Admin or Global Admin roles. This update removes the administrative role requirement while maintaining secure access control through ownership tracking.

The authorization model works to ensure:

1. The user in the delegated scenario must be a member of the `permissions` navigation property of the file storage container type.

There are 2 caveats:

1. A `SharePoint Embedded or Global Administrator` will bypass the `permissions` property user access check
2. A `Guest user in the tenant` can NOT perform any file storage container type operations (Create, Get, List, Update, or Delete).

**Key Value Proposition:**

- **Developer Empowerment**: Non-admin developers can create and manage container types for their applications without requiring SharePoint Embedded Admin or Global Admin roles
- **Ownership-Based Security**: The new `permissions` navigation property tracks users with management rights, providing granular access control without requiring new permission scopes
- **Backwards Compatible**: Existing implementations continue to work unchanged, with the `permissions` navigation property seamlessly integrated into the authorization flow
- **Delegated Authentication**: Supports delegated (user context) authentication flows with ownership-based authorization

**Target Personas:**

- **Developers**: "As a developer creating SPE applications, I would like to create and manage container types for my application without requiring admin dependencies or elevated privileges."
- **Tenant Administrators**: "As a tenant admin, I am confident granting consent to the FileStorageContainerType.Manage.All permission knowing that non-admin users can only manage container types they own through the `permissions` property, reducing security risk in my tenant."
- **System Integrators**: "As a system integrator migrating millions of documents from legacy systems (like Hyland OnBase) to SharePoint Embedded for government health records, I need to create container types with specific compliance settings and bulk ingestion capabilities without requiring elevated admin privileges for each migration project."
- **DevX Tooling Users**: "As a developer using the SPE VSCode extension and other developer tools, I want to create and manage my own container types directly without requiring Admins to do the work on my behalf through the SharePoint Online Admin PowerShell."

The `FileStorageContainerType.Manage.All` permission now implements an ownership model where:

- Non-guest users can create container types (automatically added to the `permissions` navigation property with the `owner` role)
- Users can only manage container types where they appear in the `permissions` property (unless they have SPE/Global Admin roles)
- This enables secure self-service scenarios without requiring additional permission scopes

| Resource | Description | Link |
|----------|-------------|------|
| **Feature Specifications** | Detailed requirements and technical specifications for developer container type creation | [Technical Specifications](https://microsoft-my.sharepoint-df.com/:w:/p/mawin/ET_MAjvrDAtEpEG80-1d2oUBL4pLpn-3AUXcOuqhbuIwjQ?e=28cOnY) |
| **Design Document** | Architecture, security considerations, and implementation details | [Design Document](https://microsoft.sharepoint-df.com/:w:/t/odspcomet/ETFSm-Jk4exMkygmyXPJPwEBqmduHggqOGf7oYczgnRvOg?e=2EKKfm) |
| **Security Review** | Security assessment and approval for the feature implementation | [Security Review](https://microsoft.sharepoint-df.com/teams/ODSPSecurityReviews/Lists/Review%20requests/DispForm.aspx?ID=2679) |
| **Privacy Review** | Privacy assessment and compliance evaluation for personal data handling | *[Link to be added]* |
| **Sequence Diagrams** | Visual workflows for delegated authentication flows | [Sequence Diagrams](https://dev.azure.com/onedrive/SharePoint%20Online/_wiki/wikis/SharePoint-Online.wiki/131951/-Graph-fileStorageContainerType) |

### 1: Create a fileStorageContainerType resource

Creates a FileStorageContainerType in the owning tenant using the `FileStorageContainerType.Manage.All` permission. This scenario demonstrates how developers can create container types they own without requiring SharePoint Embedded Admin or Global Admin roles. The created container type will automatically include the creating user in the `permissions` navigation property with the `owner` role.

#### 1.1 Permissions

|Permission type                       | Permissions (from least to most privileged)|
|:-------------------------------------|:-----------------|
|Delegated (work or school account)    | FileStorageContainerType.Manage.All |
|Delegated (personal Microsoft account) | Not Supported.         |
|Application                           | Not Supported |

> **Note**: The `FileStorageContainerType.Manage.All` permission no longer requires SharePoint Embedded Admin or Global Admin roles for non-admin users. Users can create and manage container types where they appear in the `permissions` navigation property. If the calling user is a SPE/Global admin, the `permissions` property access control list check is bypassed.

#### 1.2 Request example

> **Important:** The `permissions` navigation property is **not** returned in the response by default. To include permissions in the response, append `?$expand=permissions` to the request URL. This is required because the OData serialization framework only includes navigation properties when explicitly expanded — even if `permissions` is provided in the request body, it will be stripped from the response without `$expand`.

```http
POST https://graph.microsoft.com/beta/storage/fileStorage/containerTypes?$expand=permissions
Authorization: Bearer {token-with-FileStorageContainerType.Manage.All with uid: 87654321-4321-4321-4321-210987654321 for `John Doe`}
Content-Type: application/json
{
  "name": "Test Trial Container",
  "owningApplicationId": "11335700-9a00-4c00-84dd-0c210f203f00",
  "billingClassification": "trial",
  "settings": {
    "isItemVersioningEnabled": true,
    "isSharingRestricted": false,
    "consumingTenantOverridables": "isSearchEnabled,itemMajorVersionLimit",
    "agent": {
      "chatEmbedAllowedHosts": ["https://localhost:3000"]
    }
  },
  "permissions": [
    {
      "roles": ["owner"],
      "grantedToV2": {
        "user": {
          "id": "87654321-4321-4321-4321-210987654321"
        }
      }
    }
  ]
}
```

#### 1.3 Response example

```http
HTTP/1.1 201 Created
Content-Type: application/json
{
  "@odata.type": "microsoft.graph.fileStorageContainerType",
  "etag": "W/\"abc12345-6789-0123-4567-89abcdef0123\"",
  "id": "de988700-d700-020e-0a00-0831f3042f00",
  "name": "Test Trial Container",
  "owningApplicationId": "11335700-9a00-4c00-84dd-0c210f203f00",
  "billingClassification": "trial",
  "billingStatus": "valid",
  "createdDateTime": "2025-01-20T10:30:00Z",
  "expirationDateTime": "2026-01-20T10:30:00Z",
  "permissions": [
    {
      "id": "b3duZXJfODc2NTQzMjEtNDMyMS00MzIxLTQzMjEtMjEwOTg3NjU0MzIx",
      "roles": ["owner"],
      "grantedToV2": {
        "user": {
          "id": "87654321-4321-4321-4321-210987654321"
        }
      }
    }
  ],
  "settings": {
    "@odata.type": "microsoft.graph.fileStorageContainerTypeSettings"
  }
}
```

### 2: Get owned fileStorageContainerType resource

Retrieves a FileStorageContainerType using the Id, but only if the requesting user is listed in the `permissions` navigation property. This demonstrates the ownership-based access control that restricts access to only owned container types. The `permissions` navigation property is not returned by default and requires `$expand=permissions`. The response includes the `owningApplicationId` value for context, although `FileStorageContainerType.Manage.All` does not currently validate that the calling application matches this value.

#### 2.1 Permissions

|Permission type                       | Permissions (from least to most privileged)|
|:-------------------------------------|:--------------------|
|Delegated (work or school account)    | FileStorageContainerType.Manage.All |
|Delegated (personal Microsoft account) | Not Supported.      |
|Application                           | Not Supported |

#### 2.2 Request example

```http
GET https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00?$expand=permissions
Authorization: Bearer {token-with-FileStorageContainerType.Manage.All}
```

#### 2.3 Response example

```http
HTTP/1.1 200 OK
Content-Type: application/json
{
  "@odata.type": "#microsoft.graph.fileStorageContainerType",
  "id": "de988700-d700-020e-0a00-0831f3042f00",
  "name": "Test Trial Container",
  "owningApplicationId": "11335700-9a00-4c00-84dd-0c210f203f00",
  "billingClassification": "trial",
  "billingStatus": "valid",
  "createdDateTime": "2025-01-20T10:30:00Z",
  "expirationDateTime": "2026-01-20T10:30:00Z",
  "etag": "RVRhZw==",
  "permissions": [
    {
      "id": "b3duZXJfODc2NTQzMjEtNDMyMS00MzIxLTQzMjEtMjEwOTg3NjU0MzIx",
      "roles": ["owner"],
      "grantedToV2": {
        "user": {
          "id": "87654321-4321-4321-4321-210987654321"
        }
      }
    }
  ],
  "settings": {
    "urlTemplate": "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}",
    "isDiscoverabilityEnabled": true,
    "isSearchEnabled": true,
    "isItemVersioningEnabled": true,
    "itemMajorVersionLimit": 50,
    "maxStoragePerContainerInBytes": 104857600,
    "isSharingRestricted": false,
    "consumingTenantOverridables": "isSearchEnabled,itemMajorVersionLimit",
    "agent": {
      "chatEmbedAllowedHosts": ["https://localhost:3000"]
    }
  }
}
```

### 3: List owned fileStorageContainerType resources

List the ContainerTypes registered in the current tenant that are owned by the requesting user. For non-admin users, this endpoint automatically filters results based on the `permissions` navigation property, ensuring users only see container types they have permission to manage. For SPE/Global Admin users, all container types in the tenant are returned. For non-admin users, this will only return container types where the user appears in the `permissions` property. Use `$expand=permissions` to include permissions in the response.

#### 3.1 Permissions

|Permission type                       | Permissions (from least to most privileged)|
|:-------------------------------------|:--------------------|
|Delegated (work or school account)    | FileStorageContainerType.Manage.All |
|Delegated (personal Microsoft account) | Not Supported.      |
|Application                           | Not Supported |

#### 3.2 Request example

```http
GET https://graph.microsoft.com/beta/storage/fileStorage/containerTypes?$expand=permissions
Authorization: Bearer {token-with-FileStorageContainerType.Manage.All}
```

#### 3.3 Response example

```http
HTTP/1.1 200 OK
Content-Type: application/json
{
  "value": [
    {
      "@odata.type": "#microsoft.graph.fileStorageContainerType",
      "id": "de988700-d700-020e-0a00-0831f3042f00",
      "name": "Test Trial Container",
      "owningApplicationId": "11335700-9a00-4c00-84dd-0c210f203f00",
      "billingClassification": "trial",
      "billingStatus": "valid",
      "createdDateTime": "2025-01-20T10:30:00Z",
      "expirationDateTime": "2026-01-20T10:30:00Z",
      "etag": "RVRhZw==",
      "permissions": [
        {
          "id": "b3duZXJfODc2NTQzMjEtNDMyMS00MzIxLTQzMjEtMjEwOTg3NjU0MzIx",
          "roles": ["owner"],
          "grantedToV2": {
            "user": {
              "id": "87654321-4321-4321-4321-210987654321"
            }
          }
        }
      ],
      "settings": {
        "urlTemplate": "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}",
        "isDiscoverabilityEnabled": true,
        "isSearchEnabled": true,
        "isItemVersioningEnabled": true,
        "itemMajorVersionLimit": 50,
        "maxStoragePerContainerInBytes": 104857600,
        "isSharingRestricted": false,
        "consumingTenantOverridables": "isSearchEnabled,itemMajorVersionLimit",
        "agent": {
          "chatEmbedAllowedHosts": ["https://localhost:3000"]
        }
      }
    }
  ]
}
```

### 4: Update owned fileStorageContainerType resource

Updates the specified properties from a FileStorageContainerType that is owned by the requesting user. This demonstrates how the ownership model allows modification of owned container types without requiring additional admin privileges.

#### 4.1 Permissions

|Permission type                       | Permissions (from least to most privileged)|
|:-------------------------------------|:--------------------|
|Delegated (work or school account)    | FileStorageContainerType.Manage.All |
|Delegated (personal Microsoft account) | Not Supported.      |
|Application                           | Not Supported |

#### 4.2 Request example

```http
PATCH https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00
Authorization: Bearer {token-with-FileStorageContainerType.Manage.All}
Content-Type: application/json
{
  "settings": {
    "isItemVersioningEnabled": true,
    "isSharingRestricted": false
  },
  "etag": "RVRhZw=="
}
```

#### 4.3 Response example

```http
HTTP/1.1 200 OK
Content-Type: application/json
{
  "@odata.type": "#microsoft.graph.fileStorageContainerType",
  "id": "de988700-d700-020e-0a00-0831f3042f00",
  "name": "Test Trial Container",
  "owningApplicationId": "11335700-9a00-4c00-84dd-0c210f203f00",
  "billingClassification": "trial",
  "billingStatus": "valid",
  "createdDateTime": "2025-01-20T10:30:00Z",
  "expirationDateTime": "2026-01-20T10:30:00Z",
  "etag": "RVRhZw==",
  "settings": {
    "urlTemplate": "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}",
    "isDiscoverabilityEnabled": true,
    "isSearchEnabled": true,
    "isItemVersioningEnabled": true,
    "itemMajorVersionLimit": 50,
    "maxStoragePerContainerInBytes": 104857600,
    "isSharingRestricted": false,
    "consumingTenantOverridables": "isSearchEnabled,itemMajorVersionLimit",
    "agent": {
      "chatEmbedAllowedHosts": ["https://localhost:3000"]
    }
  }
}
```

> **Note:** The `permissions` navigation property requires `$expand=permissions` on the request URL to be included in the response (see [Scenario 1](#12-request-example) for details).

### 5: Delete owned fileStorageContainerType resource

Deletes a FileStorageContainerType resource that is owned by the user. It requires that all containers in the tenant have been deleted, even from the recycle bin. Only users listed in the `permissions` navigation property can perform this operation with `FileStorageContainerType.Manage.All`.

#### 5.1 Permissions

|Permission type                       | Permissions (from least to most privileged)|
|:-------------------------------------|:--------------------|
|Delegated (work or school account)    | FileStorageContainerType.Manage.All |
|Delegated (personal Microsoft account) | Not Supported.      |
|Application                           | Not Supported |

#### 5.2 Request example

```http
DELETE https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00
Authorization: Bearer {token-with-FileStorageContainerType.Manage.All}
```

#### 5.3 Response example

```http
HTTP/1.1 204 No Content
```

### 6: Add a permission to fileStorageContainerType

Adds a user permission to a container type via a dedicated POST endpoint. Only existing owners (users with the `owner` role in the `permissions` collection) or SPE/Global Admins can add permissions.

**Key constraints**:
- Maximum **3 permissions** per container type
- Duplicate permissions are silently ignored (idempotent)
- Adding a 4th permission returns an error
- Currently only the `owner` role is supported

#### 6.1 Permissions

|Permission type                       | Permissions (from least to most privileged)|
|:-------------------------------------|:--------------------|
|Delegated (work or school account)    | FileStorageContainerType.Manage.All |
|Delegated (personal Microsoft account) | Not Supported.      |
|Application                           | Not Supported |

#### 6.2 AuthZ Requirements

- **User AuthZ**: Caller must be an existing owner of the container type, OR be an SPE Admin / Global Admin
- **App AuthZ**: App must have `FileStorageContainerType.Manage.All` delegated scope

#### 6.3 Request example

```http
POST https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00/permissions
Authorization: Bearer {token-with-FileStorageContainerType.Manage.All}
Content-Type: application/json
{
  "roles": ["owner"],
  "grantedToV2": {
    "user": {
      "id": "11111111-1111-1111-1111-111111111111"
    }
  }
}
```

#### 6.4 Response example

```http
HTTP/1.1 201 Created
Content-Type: application/json
{
  "@odata.type": "#microsoft.graph.fileStorageContainerTypePermission",
  "id": "b3duZXJfMTExMTExMTEtMTExMS0xMTExLTExMTEtMTExMTExMTExMTEx",
  "roles": ["owner"],
  "grantedToV2": {
    "user": {
      "id": "11111111-1111-1111-1111-111111111111"
    }
  }
}
```

### 7: Remove a permission from fileStorageContainerType

Removes a user permission from a container type by deleting the specific permission resource. Only existing owners (users with the `owner` role in the `permissions` collection) or SPE/Global Admins can remove permissions.

**Key behaviors**:
- Owners can remove their own permission (remove themselves)
- Removing a non-existent permission returns 404
- Permissionless container types are technically allowed (see FAQ below)

#### 7.1 Permissions

|Permission type                       | Permissions (from least to most privileged)|
|:-------------------------------------|:--------------------|
|Delegated (work or school account)    | FileStorageContainerType.Manage.All |
|Delegated (personal Microsoft account) | Not Supported.      |
|Application                           | Not Supported |

#### 7.2 AuthZ Requirements

- **User AuthZ**: Caller must be an existing owner of the container type, OR be an SPE Admin / Global Admin
- **App AuthZ**: App must have `FileStorageContainerType.Manage.All` delegated scope

#### 7.3 Request example

```http
DELETE https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00/permissions/b3duZXJfMTExMTExMTEtMTExMS0xMTExLTExMTEtMTExMTExMTExMTEx
Authorization: Bearer {token-with-FileStorageContainerType.Manage.All}
```

#### 7.4 Response example

```http
HTTP/1.1 204 No Content
```

### Permissions Navigation Property FAQ

#### Are permissionless container types allowed?

**Yes, for backwards compatibility.** Container types created before the `permissions` navigation property existed will have an empty permissions collection. In this case, management defaults to SPE Admin or Global Admin users only. This ensures existing container types continue to work unchanged.

For newly created container types, the creator is automatically added as the first permission (with the `owner` role) at creation time.

#### Can owners remove their own permission?

**Yes.** There is no restriction preventing an owner from removing their own permission. The owner simply calls `DELETE /fileStorageContainerTypes/{id}/permissions/{permissionId}` with their own permission ID. This allows for ownership transfer scenarios where the original owner wants to hand off management to another user.

**Note**: If an owner removes their own permission and is not an SPE/Global Admin, they will lose access to manage the container type.

## Design details

The updated `FileStorageContainerType.Manage.All` permission introduces an ownership-based authorization model for SharePoint Embedded Container Types through the new `permissions` navigation property.

### Key Design Decisions

**Permissions Model**: Container types include a `permissions` navigation property that contains a collection of `fileStorageContainerTypePermission` entities, each representing a user with management rights to that specific container type. Currently only the `owner` role is supported.

**Automatic Permission Assignment**: When a container type is created using the `FileStorageContainerType.Manage.All` permission, the creating user is automatically added to the `permissions` collection with the `owner` role, and the application ID is set in the `owningApplicationId` property.

**Navigation Property Behavior**: The `permissions` property is a navigation property and is **NOT returned by default**. Clients must use `$expand=permissions` to include permissions in the response, or use the dedicated `GET /fileStorageContainerTypes/{id}/permissions` endpoint. This applies to all HTTP methods including POST and PATCH (see [Scenario 1](#12-request-example) for the full rationale).

**Filtered Operations**: For non-admin users, all operations (GET, PATCH, DELETE, LIST) automatically filter results based on the `permissions` navigation property, ensuring users and applications can only access container types they own in delegated scenarios. `SharePoint Embedded or Global Admin` user roles bypass the `permissions` user access check.

**Backwards Compatibility**: Existing container types continue to work unchanged. The `permissions` collection will be empty, requiring an admin user to manage them unless they add a non-admin user via `POST /fileStorageContainerTypes/{id}/permissions`.

## Error conditions and messages

The ownership-based authorization model using the `permissions` navigation property introduces specific error conditions related to permission validation and access control.

### 1: Access denied for non-owned container type

When a user or application attempts to access a container type they don't own, a 403 Forbidden error is returned with a clear ownership-related message. Users are verified through the `permissions` navigation property in delegated scenarios.

#### E1.1 Request example

```http
GET https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/88aeae-d700-020e-0a00-0831f3042f01
Authorization: Bearer {token-with-FileStorageContainerType.Manage.All}
```

#### E1.2 Error response example

```http
HTTP/1.1 403 Forbidden
Content-Type: application/json
{
  "error": {
    "code": "Forbidden",
    "message": "Access denied. You can only manage container types that you own.",
    "details": [
      {
        "code": "ContainerTypeNotOwnedByRequester",
        "message": "The requested container type is not owned by the current user or application. Users must have a permission entry in the permissions collection, and applications must match the owningApplicationId property.",
        "target": "containerTypeId"
      }
    ],
    "innerError": {
      "date": "2025-01-15T14:20:00Z",
      "request-id": "12345678-1234-1234-1234-123456789012",
      "client-request-id": "87654321-4321-4321-4321-210987654321"
    }
  }
}
```

### 2: Attempt to manage permissions by unauthorized user

When a user who does not have a permission in the `permissions` collection attempts to add or remove permissions, a 403 Forbidden error is returned. Only users with an existing permission (owner role) can manage permissions.

#### E2.1 Request example

```http
POST https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00/permissions
Authorization: Bearer {token-from-unauthorized-user-with-FileStorageContainerType.Manage.All}
Content-Type: application/json
{
  "roles": ["owner"],
  "grantedToV2": {
    "user": {
      "id": "99999999-9999-9999-9999-999999999999"
    }
  }
}
```

#### E2.2 Error response example

```http
HTTP/1.1 403 Forbidden
Content-Type: application/json
{
  "error": {
    "code": "Forbidden",
    "message": "Access denied. You can only manage container types that you own.",
    "details": [
      {
        "code": "ContainerTypeNotOwnedByRequester",
        "message": "The requested container type is not owned by the current user or application. Only users with a permission entry in the permissions collection and applications matching the owningApplicationId property in delegated scenarios can manage permissions.",
        "target": "permissions"
      }
    ],
    "innerError": {
      "date": "2025-01-15T14:20:00Z",
      "request-id": "12345678-1234-1234-1234-123456789012",
      "client-request-id": "87654321-4321-4321-4321-210987654321"
    }
  }
}
```

### 3: Guest user creation attempt (Delegated only)

When a guest user attempts to create a container type using delegated authentication, a 403 Forbidden error is returned as guest users cannot perform any container type operations.

#### E3.1 Request example

```http
POST https://graph.microsoft.com/beta/storage/fileStorage/containerTypes
Authorization: Bearer {guest-user-delegated-token-with-FileStorageContainerType.Manage.All}
Content-Type: application/json
{
  "name": "Test Container",
  "owningApplicationId": "11335700-9a00-4c00-84dd-0c210f203f00",
  "billingClassification": "trial"
}
```

#### E3.2 Error response example

```http
HTTP/1.1 403 Forbidden
Content-Type: application/json
{
  "error": {
    "code": "Forbidden",
    "message": "Guest users cannot create container types.",
    "details": [
      {
        "code": "GuestUserCreationNotAllowed",
        "message": "Container type operations are not permitted for guest users in this tenant.",
        "target": "user"
      }
    ],
    "innerError": {
      "date": "2025-01-15T14:20:00Z",
      "request-id": "12345678-1234-1234-1234-123456789012",
      "client-request-id": "87654321-4321-4321-4321-210987654321"
    }
  }
}
```

### 4: Feature disabled for non-admin users (Delegated only)

When a regular (non-admin) user attempts to create a container type but the `canDevelopersCreateContainerTypes` feature flag is disabled, a 403 Forbidden error is returned.

#### E4.1 Request example

```http
POST https://graph.microsoft.com/beta/storage/fileStorage/containerTypes
Authorization: Bearer {regular-user-delegated-token-with-FileStorageContainerType.Manage.All}
Content-Type: application/json
{
  "name": "Test Container",
  "owningApplicationId": "11335700-9a00-4c00-84dd-0c210f203f00",
  "billingClassification": "trial"
}
```

#### E4.2 Error response example

```http
HTTP/1.1 403 Forbidden
Content-Type: application/json
{
  "error": {
    "code": "Forbidden",
    "message": "Container type creation is currently disabled for non-administrator users.",
    "details": [
      {
        "code": "FeatureDisabledForRegularUsers",
        "message": "The ability for developers to create container types is not enabled in this tenant. Contact your administrator or use an account with SharePoint Embedded Admin or Global Admin roles.",
        "target": "user"
      }
    ],
    "innerError": {
      "date": "2025-01-15T14:20:00Z",
      "request-id": "12345678-1234-1234-1234-123456789012",
      "client-request-id": "87654321-4321-4321-4321-210987654321"
    }
  }
}
```

### 5: Application already owns a container type

When an application attempts to create a second container type but already owns one, a 409 Conflict error is returned as each application can only own one container type.

#### E5.1 Request example

```http
POST https://graph.microsoft.com/beta/storage/fileStorage/containerTypes
Authorization: Bearer {token-with-FileStorageContainerType.Manage.All}
Content-Type: application/json
{
  "name": "Second Container",
  "owningApplicationId": "11335700-9a00-4c00-84dd-0c210f203f00",
  "billingClassification": "trial"
}
```

#### E5.2 Error response example

```http
HTTP/1.1 409 Conflict
Content-Type: application/json
{
  "error": {
    "code": "Conflict",
    "message": "The application already owns a container type.",
    "details": [
      {
        "code": "ApplicationAlreadyOwnsContainerType",
        "message": "Each application can only own one container type. The calling application already has an existing container type resource.",
        "target": "owningApplicationId"
      }
    ],
    "innerError": {
      "date": "2025-01-15T14:20:00Z",
      "request-id": "12345678-1234-1234-1234-123456789012",
      "client-request-id": "87654321-4321-4321-4321-210987654321"
    }
  }
}
```

### 6: Container type not found

When attempting to access a container type that doesn't exist, a 404 Not Found error is returned.

#### E6.1 Request example

```http
GET https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/00000000-0000-0000-0000-000000000000
Authorization: Bearer {token-with-FileStorageContainerType.Manage.All}
```

#### E6.2 Error response example

```http
HTTP/1.1 404 Not Found
Content-Type: application/json
{
  "error": {
    "code": "NotFound",
    "message": "The requested container type was not found.",
    "details": [
      {
        "code": "ContainerTypeNotFound",
        "message": "No container type exists with the specified ID.",
        "target": "containerTypeId"
      }
    ],
    "innerError": {
      "date": "2025-01-15T14:20:00Z",
      "request-id": "12345678-1234-1234-1234-123456789012",
      "client-request-id": "87654321-4321-4321-4321-210987654321"
    }
  }
}
```

### 7: Guest user access restriction (Delegated only)

When a guest user attempts to perform any operation (GET, List, Update, Delete) on container types using delegated authentication, a 403 Forbidden error is returned as guest users cannot perform any container type operations.

#### E7.1 Request example

```http
GET https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00
Authorization: Bearer {guest-user-delegated-token-with-FileStorageContainerType.Manage.All}
```

#### E7.2 Error response example

```http
HTTP/1.1 403 Forbidden
Content-Type: application/json
{
  "error": {
    "code": "Forbidden",
    "message": "Guest users cannot access container types.",
    "details": [
      {
        "code": "GuestUserAccessNotAllowed",
        "message": "Container type operations are not permitted for guest users in this tenant.",
        "target": "user"
      }
    ],
    "innerError": {
      "date": "2025-01-15T14:20:00Z",
      "request-id": "12345678-1234-1234-1234-123456789012",
      "client-request-id": "87654321-4321-4321-4321-210987654321"
    }
  }
}
```

### 8: Guest user deletion restriction (Delegated only)

When a guest user attempts to delete a container type using delegated authentication, a 403 Forbidden error is returned as guest users cannot perform any container type operations.

#### E8.1 Request example

```http
DELETE https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00
Authorization: Bearer {guest-user-delegated-token-with-FileStorageContainerType.Manage.All}
```

#### E8.2 Error response example

```http
HTTP/1.1 403 Forbidden
Content-Type: application/json
{
  "error": {
    "code": "Forbidden",
    "message": "Guest users cannot delete container types.",
    "details": [
      {
        "code": "GuestUserDeletionNotAllowed",
        "message": "Container type operations are not permitted for guest users in this tenant.",
        "target": "user"
      }
    ],
    "innerError": {
      "date": "2025-01-15T14:20:00Z",
      "request-id": "12345678-1234-1234-1234-123456789012",
      "client-request-id": "87654321-4321-4321-4321-210987654321"
    }
  }
}
```

### 9: Insufficient user privileges for owned container type

When a regular user attempts to access a container type owned by their application but they do not have a permission entry in the `permissions` collection, a 403 Forbidden error is returned.

#### E9.1 Request example

```http
GET https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00
Authorization: Bearer {regular-user-delegated-token-with-FileStorageContainerType.Manage.All}
```

#### E9.2 Error response example

```http
HTTP/1.1 403 Forbidden
Content-Type: application/json
{
  "error": {
    "code": "Forbidden",
    "message": "Insufficient user privileges to access this container type.",
    "details": [
      {
        "code": "UserNotInPermissionsCollection",
        "message": "While the container type is owned by your application, your user account does not have the required user-level permissions to access it. Contact an administrator to be added to the container type's permissions via POST /fileStorageContainerTypes/{id}/permissions.",
        "target": "user"
      }
    ],
    "innerError": {
      "date": "2025-01-15T14:20:00Z",
      "request-id": "12345678-1234-1234-1234-123456789012",
      "client-request-id": "87654321-4321-4321-4321-210987654321"
    }
  }
}
```

### 10: Maximum permissions limit exceeded

When attempting to add more than 3 permissions to a container type, a 400 Bad Request error is returned as each container type can have a maximum of 3 permissions.

#### E10.1 Request example

```http
POST https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00/permissions
Authorization: Bearer {token-with-FileStorageContainerType.Manage.All}
Content-Type: application/json
{
  "roles": ["owner"],
  "grantedToV2": {
    "user": {
      "id": "44444444-4444-4444-4444-444444444444"
    }
  }
}
```

#### E10.2 Error response example

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json
{
  "error": {
    "code": "BadRequest",
    "message": "Cannot add permission. Maximum number of permissions (3) has been reached.",
    "details": [
      {
        "code": "MaxPermissionsExceeded",
        "message": "Container types can have a maximum of 3 permissions. Remove an existing permission before adding a new one.",
        "target": "permissions"
      }
    ],
    "innerError": {
      "date": "2025-01-15T14:20:00Z",
      "request-id": "12345678-1234-1234-1234-123456789012",
      "client-request-id": "87654321-4321-4321-4321-210987654321"
    }
  }
}
```

## Appendix

### Additional design details

#### Authorization model

The `FileStorageContainerType.Manage.All` permission now implements a two-tier authorization model through the new `permissions` navigation property:

1. **Application-level authorization**: Determined by the `owningApplicationId` property validation
2. **User-level authorization**: Determined by the `permissions` navigation property for delegated scenarios (non-admin users only)

##### Key authorization rules

- **Admin Users (SPE Admin/Global Admin)**: Bypass the `permissions` navigation property user-level ACL checks in delegated scenarios
- **Regular Users**: Require both application-level authorization (`owningApplicationId` match) and user-level access (having a permission entry in the `permissions` collection) in delegated scenarios
- **Guest Users**: Cannot perform any container type operations (Create, Get, List, Update, or Delete)
- **Delegated Scenarios**: Use both application-level authorization and user-level checks (unless user is SPE/Global Admin)
- **Feature Flag**: The `canDevelopersCreateContainerTypes` flag only applies to delegated CREATE operations for non-admin users

#### Ownership model

- Each application can own exactly **one** container type
- The `owningApplicationId` property links container types to their owning application
- Applications can only manage container types they own in delegated scenarios
- The `permissions` navigation property controls user-level access in delegated scenarios and is automatically populated during creation with the creating user (with the `owner` role)

#### Permissions management

The `permissions` navigation property is a collection of `fileStorageContainerTypePermission` entities that tracks users with management rights to a container type. Each permission has an `id` (Base64Url-encoded), `roles` (currently only `["owner"]`), and `grantedToV2` (containing the user identity). Permissions are managed via dedicated CRUD endpoints.

##### Key constraints

| Constraint | Value | Behavior |
|------------|-------|----------|
| Maximum permissions | 3 | Adding a 4th permission returns `400 Bad Request` |
| Minimum permissions | 0 | Permissionless container types are technically allowed |
| Duplicate handling | Ignored | Adding an existing permission is silently ignored (idempotent) |
| Self-removal | Allowed | Owners can delete their own permission |

##### Management operations

| Operation | Method | Endpoint | Description |
|-----------|--------|----------|-------------|
| Add permission | POST | `/fileStorageContainerTypes/{id}/permissions` | Create a new permission for a user |
| List permissions | GET | `/fileStorageContainerTypes/{id}/permissions` | List all permissions |
| Get permission | GET | `/fileStorageContainerTypes/{id}/permissions/{permissionId}` | Get a specific permission |
| Remove permission | DELETE | `/fileStorageContainerTypes/{id}/permissions/{permissionId}` | Delete a specific permission |

##### Audit logging

All permission changes are audit logged, capturing:
- Tenant ID
- Container Type ID  
- Old permissions list (before change)
- New permissions list (after change)

