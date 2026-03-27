---
title: "Workflow: cancelProcessing"
description: "Cancel workflow runs that are currently in progress or queued."
author: "KristinaSmith"
ms.localizationpriority: medium
ms.subservice: "entra-id-governance"
doc_type: apiPageType
ms.date: 03/26/2026
---

# Workflow: cancelProcessing

Namespace: microsoft.graph.identityGovernance

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Cancel one or more [workflow](../resources/identitygovernance-workflow.md) runs that are currently in progress or queued. This action allows administrators to stop processing of workflow runs on demand.

Only runs in `queued` or `inProgress` status can be canceled. Completed, failed, or already canceled runs can't be canceled. Currently limited to canceling one run per request.

[!INCLUDE [national-cloud-support](../../includes/all-clouds.md)]

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](/graph/permissions-reference).

<!-- { "blockType": "permissions", "name": "identitygovernance_workflow_cancelprocessing" } -->

[!INCLUDE [permissions-table](../includes/permissions/identitygovernance-workflow-cancelprocessing-permissions.md)]

[!INCLUDE [rbac-lifecycle-workflows-apis-write](../includes/rbac-for-apis/rbac-lifecycle-workflows-apis-write.md)]

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
```http
POST /identityGovernance/lifecycleWorkflows/workflows/{workflow-id}/cancelProcessing
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required. Learn more about [authentication and authorization](/graph/auth/auth-concepts).|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that are required with this action.

|Parameter|Type|Description|
|:---|:---|:---|
|scope|[microsoft.graph.identityGovernance.cancelScope](../resources/identitygovernance-cancelscope.md)|Defines the scope of workflow runs to cancel. Currently only [cancelRunsScope](../resources/identitygovernance-cancelrunsscope.md) is supported. Required.|

### cancelRunsScope properties

When using [cancelRunsScope](../resources/identitygovernance-cancelrunsscope.md), the `@odata.type` property is required in the request body.

|Property|Type|Description|
|:---|:---|:---|
|@odata.type|String|Must be `#microsoft.graph.identityGovernance.cancelRunsScope`. Required.|
|runs|[microsoft.graph.identityGovernance.run](../resources/identitygovernance-run.md) collection|The workflow runs to cancel. Currently limited to one run per request. Required.|

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Example 1: Successfully cancel a workflow run

The following example shows a request that successfully cancels a single workflow run.

#### Request

The following example shows a request.

# [HTTP](#tab/http)
<!-- {
  "blockType": "request",
  "name": "lifecycleworkflows_workflow_cancelprocessing_success"
}
-->
```http
POST https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/cancelProcessing
Content-Type: application/json

{
  "scope": {
    "@odata.type": "#microsoft.graph.identityGovernance.cancelRunsScope",
    "runs": [
      {
        "id": "8cdf25a8-c9d2-423e-a03d-3f39f03c3e97"
      }
    ]
  }
}
```

---

#### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 204 No Content
```

### Example 2: Workflow not found

The following example shows a request where the specified workflow doesn't exist.

#### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "lifecycleworkflows_workflow_cancelprocessing_workflownotfound"
}
-->
```http
POST https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/workflows/00000000-0000-0000-0000-000000000000/cancelProcessing
Content-Type: application/json

{
  "scope": {
    "@odata.type": "#microsoft.graph.identityGovernance.cancelRunsScope",
    "runs": [
      {
        "id": "8cdf25a8-c9d2-423e-a03d-3f39f03c3e97"
      }
    ]
  }
}
```

#### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 404 Not Found
Content-Type: application/json

{
  "error": {
    "code": "Resource not found",
    "message": "Workflow with id '00000000-0000-0000-0000-000000000000' was not found."
  }
}
```

### Example 3: No valid runs provided

The following example shows a request where no valid run IDs are provided. An error is returned when a request contains zero valid runs, either from an empty runs array or only invalid run IDs.

#### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "lifecycleworkflows_workflow_cancelprocessing_novalid"
}
-->
```http
POST https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/cancelProcessing
Content-Type: application/json

{
  "scope": {
    "@odata.type": "#microsoft.graph.identityGovernance.cancelRunsScope",
    "runs": [
      {
        "id": "00000000-0000-0000-0000-000000000001"
      },
      {
        "id": "00000000-0000-0000-0000-000000000002"
      }
    ]
  }
}
```

#### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 406 Not Acceptable
Content-Type: application/json

{
  "error": {
    "code": "Not Acceptable Request",
    "message": "No valid runs in cancelRunsScope supplied. 2 runs were specified and none were valid."
  }
}
```

### Example 4: Run doesn't belong to workflow

The following example shows a request where the provided run doesn't belong to the specified workflow.

#### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "lifecycleworkflows_workflow_cancelprocessing_wrongworkflow"
}
-->
```http
POST https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/cancelProcessing
Content-Type: application/json

{
  "scope": {
    "@odata.type": "#microsoft.graph.identityGovernance.cancelRunsScope",
    "runs": [
      {
        "id": "8cdf25a8-c9d2-423e-a03d-3f39f03c3e97"
      }
    ]
  }
}
```

#### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
  "error": {
    "code": "Bad Request",
    "message": "Run with id '8cdf25a8-c9d2-423e-a03d-3f39f03c3e97' does not belong to workflow '14879e66-9ea9-48d0-804d-8fea672d0341'."
  }
}
```

### Example 5: Run not in cancelable state

The following example shows a request where the run isn't in a cancelable state. Only runs with status `queued` or `inProgress` can be canceled.

#### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "lifecycleworkflows_workflow_cancelprocessing_notcancellable"
}
-->
```http
POST https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/cancelProcessing
Content-Type: application/json

{
  "scope": {
    "@odata.type": "#microsoft.graph.identityGovernance.cancelRunsScope",
    "runs": [
      {
        "id": "8cdf25a8-c9d2-423e-a03d-3f39f03c3e97"
      }
    ]
  }
}
```

#### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
  "error": {
    "code": "Conflict",
    "message": "Run with id '8cdf25a8-c9d2-423e-a03d-3f39f03c3e97' is not in a cancellable state. Current status: 'completed'. Must be 'queued' or 'in-progress' to cancel."
  }
}
```

### Example 6: Too many runs

The following example shows a request that exceeds the maximum number of runs allowed per request. Currently, only one run can be canceled per request.

#### Request

The following example shows a request.

<!-- {
  "blockType": "request",
  "name": "lifecycleworkflows_workflow_cancelprocessing_toomany"
}
-->
```http
POST https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/cancelProcessing
Content-Type: application/json

{
  "scope": {
    "@odata.type": "#microsoft.graph.identityGovernance.cancelRunsScope",
    "runs": [
      {
        "id": "8cdf25a8-c9d2-423e-a03d-3f39f03c3e97"
      },
      {
        "id": "2b08131a-8083-450d-9a1f-2aecb406a6f4"
      },
      {
        "id": "e7904bb5-df48-48ee-a0e1-264d5c121355"
      }
    ]
  }
}
```

#### Response

The following example shows the response.

<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
  "error": {
    "code": "Bad Request",
    "message": "Too many runs provided. Received 3, but the maximum allowed in a single cancelProcessing call is 1."
  }
}
```
