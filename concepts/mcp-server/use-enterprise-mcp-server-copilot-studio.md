---
title: "Use Microsoft MCP Server for Enterprise from Copilot Studio"
description: "Learn how to connect a Microsoft Copilot Studio agent to the Microsoft MCP Server for Enterprise to query Microsoft Graph data using natural language."
author: msewaweru
ms.author: eunicewaweru
ms.subservice: ent-mcp-server
ms.topic: how-to
ms.date: 03/12/2026

#customer intent: As a developer or an IT administrator, I want to connect a Copilot Studio agent to the Microsoft MCP Server for Enterprise so that I can query Microsoft Graph data using natural language.
---

# Use Microsoft MCP Server for Enterprise from Copilot Studio

The [Microsoft MCP Server for Enterprise](/graph/mcp-server/overview) enables AI agents to query enterprise data in your Microsoft Entra tenant by using natural language. In this article, you learn how to connect a Microsoft Copilot Studio agent to the Microsoft MCP Server for Enterprise using a custom connector.

## Prerequisites

Before you begin, make sure you have the following:

- A Microsoft Entra tenant.
- An admin user account in the tenant with the following roles assigned in the [Microsoft Entra admin center](https://entra.microsoft.com):
  - **Cloud Application Administrator** and **Privileged Role Administrator** — required to create and configure the connector.
  - Appropriate  directory roles for the Graph operations your agent performs — required so the MCP Server can execute Graph API calls on behalf of the signed-in user.
  Sign in to both Copilot Studio and Power Apps with this tenant admin account.
- Complete the MCP Server provisioning steps in [Get started with the Microsoft MCP Server for Enterprise](/graph/mcp-server/get-started), including assigning the `MCP.*` API permissions to your app registration and granting admin consent. For more information, see [MCP Server for Enterprise documentation](https://aka.ms/MCPServerForEnterprise).
- A [client app registration](/entra/identity-platform/quickstart-register-app) in Microsoft Entra. You need the following from your app registration:
  - **Application (client) ID**
  - **Federated credentials** (recommended) or a **client secret** (from **Certificates & secrets**). Federated credentials are more secure and don't require secret rotation. To use federated credentials, first create the custom connector to obtain the redirect URL, then create a managed identity and configure the federated credential on your app registration. If your organization permits client secrets, you can use a client secret as a simpler alternative.
- A Power Platform environment that isn't blocked by Data Loss Prevention (DLP) policies. Avoid using the default environment, as tenant-level DLP policies often restrict custom connectors there. Use a **Developer** or **Sandbox** environment instead. If needed, create one from the [Power Platform Admin Center](https://admin.powerplatform.microsoft.com) > **Environments** > **+ New**.

## Create the MCP connector from Copilot Studio

Create a connector to the Microsoft MCP Server for Enterprise directly from Copilot Studio.

1. In [Copilot Studio](https://copilotstudio.microsoft.com), make sure you select the environment where you want to create the connector (for example, a Developer or Sandbox environment). Use the environment picker in the top-right corner.
1. Open your agent and select the **Tools** tab.
1. Select **+ Add a tool**.
1. Select **+ New tool**, then select **Model Context Protocol**. The MCP onboarding wizard opens.
1. Fill in the following required fields:

    | Field | Value |
    |---|---|
    | **Server name** | `MCP Server for Enterprise` |
    | **Server description** | `A Model Context Protocol (MCP) server that enables AI assistants to securely interact with Microsoft Graph API for enterprise identity and access management operations.` |
    | **Server URL** | `https://mcp.svc.cloud.microsoft/enterprise` |

1. In the **Authentication** section, select **OAuth 2.0** > **Manual**.
1. Fill in the following OAuth fields:

    | Field | Value |
    |---|---|
    | **Client ID** | The Application (client) ID of your client app registration. |
    | **Client secret** | The client secret value of your client app registration. If you use federated credentials, enter a placeholder value to proceed with connector creation; you update the authentication method later in Power Apps. |
    | **Authorization URL** | `https://login.microsoftonline.com/organizations/oauth2/v2.0/authorize` |
    | **Token URL template** | `https://login.microsoftonline.com/organizations/oauth2/v2.0/token` |
    | **Refresh URL** | `https://login.microsoftonline.com/organizations/oauth2/v2.0/token` |
    | **Scopes** | `api://e8c77dc2-69b3-43f4-bc51-3213c9d915b4/.default` |

1. Select **Create**. Wait for the connector to initialize.
1. Copy the **Redirect URL** from the confirmation page. You need this URL in the next step.

## Add the redirect URL to your app registration

After you create the connector, add the redirect URL to your client app registration.

1. In the [Microsoft Entra admin center](https://entra.microsoft.com), go to your client app registration.
1. Select **Authentication**.
1. Select **+ Add a platform** > **Web**. If the Web platform already exists, select **+ Add URI** instead. Don't add redirect URIs under **Mobile and Desktop applications**, as those indicate a public client and aren't supported.
1. Paste the redirect URL you copied from Copilot Studio.
1. Select **Configure**.
1. Go back to Copilot Studio and select **Next**.
1. In the **Add tool** dialog, select **Create new connection**. A sign-in pop-up appears.
1. Sign in with your tenant admin account.
1. After sign-in succeeds, select **Add and configure** to finish adding the MCP tool to your agent.

## Add the connector to your Copilot Studio agent

Connect the MCP tool to your agent so it can query Microsoft Graph data.

1. In [Copilot Studio](https://copilotstudio.microsoft.com), make sure you select the same environment where you created the connector.
1. Open your agent and go to **Tools** > **+ Add a tool**.
1. In the **Add tool** dialog, select the **Model Context Protocol** filter tab (not **Connector**).
1. Find your **MCP Server for Enterprise** connector and select it to add it to the agent.

> [!TIP]
> For testing purposes, you can instruct the agent to always use the custom connector so the MCP server is invoked for every request. Add this instruction to the agent's system instructions.

## Configure the custom connector in Power Apps

After you create the connector from Copilot Studio, finalize the configuration in Power Apps.

### Navigate to the custom connector

1. Sign in to the [Power Apps portal](https://make.powerapps.com).
1. Make sure you're in the same environment where you created the connector in Copilot Studio. To check or change the environment, use the environment picker in the top-right corner.
1. On the left pane, select **More** > **Discover all**.
1. Under **Data**, select **Custom connectors**.
1. Find your connector (named **MCP Server for Enterprise**) in the list.
1. Select the pencil (**Edit**) icon next to your connector to open the connector wizard.

### Update the Security tab

1. In the connector wizard, select the **2. Security** tab at the top.
1. Verify that the **Authentication type** is set to **OAuth 2.0** and **Identity Provider** is set to **Azure Active Directory**.
1. Re-enter the **Client secret** value from your app registration. The client secret isn't persisted and must be re-entered each time you edit the connector.
1. Update the following fields:

    | Field | Value |
    |---|---|
    | **Resource URL** | `https://mcp.svc.cloud.microsoft/enterprise/` |
    | **Enable on-behalf-of login** | Set to **true**. |

1. (Optional) If you use federated credentials instead of a client secret, select **Enable Service Principal Support** and choose **Use Managed Identity**.
1. Select **Update Connector** in the top-right corner of the page. Wait for the update to complete before proceeding.

## Test the connection

Before you verify end-to-end functionality, confirm that the connector can establish a connection.

1. Still in the connector wizard in Power Apps, select the **5. Test** tab at the top.
1. Select **+ New connection**. A dialog box appears showing the connector name.
1. Select **Create**. A sign-in pop-up appears. Sign in with your tenant admin account.
1. After the connection is created, return to the **Test** tab. Select the refresh icon to update the connection information if needed.
1. Verify that the connection status shows **Connected**.

> [!NOTE]
> Running **Test operation** from Power Apps may return a 500 error with an empty body. This is expected because the Power Apps test page sends an empty request, and the MCP server requires a properly formatted JSON-RPC payload. As long as the connection status shows **Connected** and schema validation succeeds, the connector is configured correctly. You verify end-to-end functionality from Copilot Studio in the next step.

## Verify the setup

After you add the connector, test the agent by asking a tenant-specific question.

1. In Copilot Studio, select **Test** to open a test session.
1. Ask a question such as, "How many users are in my tenant?"
1. The agent should:
    1. Invoke the MCP Server tools to understand the intent.
    1. Execute the appropriate Microsoft Graph API call.
    1. Return a natural language answer that summarizes the tenant data.

> [!NOTE]
> The Microsoft MCP Server for Enterprise currently supports **read-only** operations. Write actions aren't yet allowed.

## Troubleshooting

| Issue | Cause | Resolution |
|---|---|---|
| Custom connector creation blocked by DLP policy | Tenant-level Data Loss Prevention policies restrict custom connectors in the current environment. | Create a Developer or Sandbox environment from the [Power Platform Admin Center](https://admin.powerplatform.microsoft.com) and recreate the connector there. |
| 403 Forbidden when the agent queries Graph data | The signed-in user lacks the necessary Entra directory roles, or the connection token doesn't reflect recently assigned permissions. | Verify the user has the appropriate Entra roles for the requested Graph operations. If roles were recently assigned, delete the existing connection in Power Apps and create a new one to obtain a fresh token. |
| MCP tool not visible when adding a tool to the agent | The tool doesn't appear under the default **Connector** filter in the Add tool dialog. | Select the **Model Context Protocol** filter tab instead. |

## Related content

- [Overview of Microsoft MCP Server for Enterprise](/graph/mcp-server/overview)
- [Get started with the Microsoft MCP Server for Enterprise](/graph/mcp-server/get-started)
- [Use a custom connector from a Power Automate flow](/connectors/custom-connectors/use-custom-connector-flow)

