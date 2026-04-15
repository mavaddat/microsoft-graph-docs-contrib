---
title: Use Microsoft MCP Server for Enterprise in Azure AI Foundry
description: "Learn how to connect Microsoft MCP Server for Enterprise as a tool in your Azure AI Foundry agent to query enterprise identity data using natural language."
author: msewaweru
ms.author: eunicewaweru
ms.reviewer: FaithOmbongi
ms.subservice: ent-mcp-server
ms.topic: how-to
ms.date: 04/15/2026
ms.custom: msecd-doc-authoring-106

#customer intent: As a developer or IT administrator, I want to integrate Microsoft MCP Server for Enterprise into my Azure AI Foundry agent so that I can query Microsoft Entra data using natural language.
---

# Use Microsoft MCP Server for Enterprise in Azure AI Foundry (preview)

Microsoft MCP Server for Enterprise integrates with Azure AI Foundry as a tool, enabling your AI agents to query Microsoft Entra data using natural language. Connect the MCP Server as a tool in your project and query your organization's data using natural language.

## Prerequisites

- A Microsoft Entra tenant.
- Complete the MCP Server provisioning steps in [Get started with the Microsoft MCP Server for Enterprise](get-started.md). For more information, see [MCP Server for Enterprise documentation](https://aka.ms/MCPServerForEnterprise).
- A [client app registration](/entra/identity-platform/quickstart-register-app) in Microsoft Entra with the following configuration:
  - **Application (client) ID** — Note this value for use during setup.
  - **Client secret** — Go to **Certificates & secrets** > **Client secrets** and create a new secret. Copy the secret **value** for use during setup.
  - Assign the `MCP.*` API permissions to your app registration and grant admin consent. For more information, see [MCP Server for Enterprise documentation](https://aka.ms/MCPServerForEnterprise).
  - At least [**Cloud Application Administrator**](/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) role to create the app registration and grant admin consent.
- An Azure AI Foundry project with at least one agent configured.
- At least [**Azure AI Developer**](/azure/role-based-access-control/built-in-roles/ai-machine-learning#azure-ai-developer) role scoped to the Azure AI Foundry project resource to connect tools and use agents.

## Connect the MCP Server as a tool in Azure AI Foundry

Use the custom OAuth provider option to connect your app registration to the Microsoft MCP Server for Enterprise endpoint.

1. In the [Azure AI Foundry portal](https://ai.azure.com/), make sure you're using the **New Foundry** UI and navigate to your project.

1. In the sidebar menu, select **Tools**, and then select **Connect a tool**.

1. Under **Catalog**, search for **Microsoft MCP Server for Enterprise**, and then select **Create**.

1. For **OAuth Provider**, select **Custom** to use your own OAuth app registration for token exchange.

1. Provide the following configuration:
   - **Name**: Enter a unique identifier for the tool connection.
   - **Client ID**: Enter the application (client) ID from your app registration.
   - **Client Secret**: Enter the client secret value from your app registration.
   - **Token URL, Auth URL, and Refresh URL**: Replace `organizations` with your tenant ID if your Azure AI Foundry project and app registration are in different tenants. Otherwise, leave `organizations` as the default value.

1. Select **Connect**, and then copy the **Redirect URL** provided.

1. Return to your Microsoft Entra app registration, go to **Authentication**, add the redirect URL as a redirect URI, and save your changes.

## Query Microsoft Entra data

After you connect the Microsoft MCP Server for Enterprise tool, add it to an agent and start querying your organization's data using natural language.

1. In the Azure AI Foundry sidebar, go to **Agents** and select an existing agent or create a new one.

1. In the agent configuration, add the Microsoft MCP Server for Enterprise tool you connected in the previous section.

### Sign in and authorize access

When you first use the tool, the agent prompts you to sign in and authorize access.

1. Select **Open consent** when prompted to sign in.

1. Follow the authentication prompts to grant access. After you consent, you don't need to sign in again for future queries in the same project.

1. Approve each MCP tool call as prompted during query execution.

### Example queries

After you sign in, you can ask questions such as:

- "How many users are in my tenant?"
- "Which users haven't signed in for the last 30 days?"
- "Show me all guest users with admin roles."

## Related content

- [Overview of Microsoft MCP Server for Enterprise](overview.md)
- [Sample prompts for Microsoft MCP Server for Enterprise](mcp-server-sample-prompts.md)
- [Set up authentication for MCP tools in Azure AI Foundry](/azure/foundry/agents/how-to/mcp-authentication)
