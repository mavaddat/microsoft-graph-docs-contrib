---
title: Use Microsoft MCP Server for Enterprise in Azure AI Foundry
description: "Learn how to add Microsoft MCP Server for Enterprise as a tool in your Azure AI Foundry AI Agent to query enterprise identity data using natural language."
author: msewaweru
ms.author: eunicewaweru
ms.reviewer: FaithOmbongi
ms.subservice: ent-mcp-server
ms.topic: how-to
ms.date: 04/08/2026
ms.custom: msecd-doc-authoring-106

#customer intent: As a developer or IT administrator, I want to integrate Microsoft MCP Server for Enterprise into my Azure AI Foundry agent so that I can query Microsoft Entra data using natural language.
---

# Use Microsoft MCP Server for Enterprise in Azure AI Foundry (preview)

Microsoft MCP Server for Enterprise integrates with Azure AI Foundry as a tool, enabling your AI agents to query Microsoft Entra data using natural language. This article walks you through creating an app registration, connecting the MCP Server as a tool, and querying your organization's data from your Azure AI Foundry project.

## Prerequisites

> [!IMPORTANT]
> Microsoft MCP Server for Enterprise is currently in preview. This information relates to a prerelease product that might be substantially modified before it's released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.
>
> Microsoft MCP Server for Enterprise is offered under the [Microsoft APIs Terms of Use](/legal/microsoft-apis/terms-of-use).

- An Azure AI Foundry project and agent.
- Completion of [Get started with the Microsoft MCP Server for Enterprise](get-started.md) to provision the MCP Server.
- At least **Application Administrator** or **Cloud Application Administrator** role in your Microsoft Entra tenant to create and configure app registrations and grant admin consent for API permissions.
- At least [**Contributor**](/azure/role-based-access-control/built-in-roles/general#contributor) permissions scoped to the Azure AI Foundry project resource to connect tools.

## Create and configure an app registration

To enable authentication between Azure AI Foundry and Microsoft MCP Server for Enterprise, create a Microsoft Entra app registration and grant the necessary API permissions.

1. Follow the [app registration guide](../app-registration.md) to create a Microsoft Entra app and get the client ID.

1. In your app registration, go to **Manage** > **API Permissions**.

1. Select **Add a permission**, and then search for **Microsoft MCP Server for Enterprise**.

1. Select the permissions required for your scenarios, and then select **Grant admin consent for [your tenant]** to authorize the permissions.

## Connect the MCP Server as a tool in Azure AI Foundry

After you configure your app registration, connect the Microsoft MCP Server for Enterprise as a tool in your Azure AI Foundry project.

1. In the [Azure AI Foundry portal](https://ai.azure.com/), make sure you're using the **New Foundry** UI and navigate to your project.

1. In the sidebar menu, select **Tools**, and then select **Connect a tool**.

1. Under **Catalog**, search for **Microsoft MCP Server for Enterprise**, and then select **Create**.

1. Provide the following configuration:
   - **Name**: Enter a unique identifier for the tool.
   - **Client ID**: Enter the app registration client ID from the previous section.
   - **Token URL, Auth URL, and Refresh URL**: Replace `organizations` with your tenant ID if your Azure AI Foundry project and app registration are in different tenants. Otherwise, leave `organizations` as the default value.

1. Select **Connect**, and then copy the **Redirect URL** provided.

1. Return to your Microsoft Entra app registration, go to **Authentication**, add the Redirect URL, and save your changes.

## Query Microsoft Entra data

After you connect the Microsoft MCP Server for Enterprise tool, add it to your agent and start querying your organization's data using natural language.

### Sign in and authorize access

When you first use the tool, sign in and authorize access.

1. Select **Open consent** when prompted to sign in.

1. Follow the authentication prompts to grant access.

1. If sign-in fails, an error code appears in the `/closeme` window. Decode this base64-encoded value to view the detailed error information.

1. Approve each MCP tool call as prompted during query execution.

### Example queries

After you sign in, you can ask questions such as:

- "How many users are in my tenant?"
- "Which users haven't signed in for the last 30 days?"
- "Show me all guest users with admin roles."

## Related content

- [Overview of Microsoft MCP Server for Enterprise](overview.md)
- [Sample prompts for Microsoft MCP Server for Enterprise](mcp-server-sample-prompts.md)
