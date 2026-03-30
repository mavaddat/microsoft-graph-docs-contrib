---
author: Dongjing-MSIT
ms.topic: include
---

> [!IMPORTANT]
> In delegated scenarios with work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with a supported role permission. *Exchange Administrator* is the least privileged role supported for this operation.
> If you are using **Application Permissions**, you must configure the required **TenantPlacesManagement** role (to manage Places) and **MailRecipient** role (to manage users and mailboxes) by following the [Role Based Access Control (RBAC) for Applications](https://learn.microsoft.com/en-us/exchange/permissions-exo/application-rbac) documentation.

> **Known issue:** Update requests may still succeed without the role assignment but result in unexpected behaviors.
