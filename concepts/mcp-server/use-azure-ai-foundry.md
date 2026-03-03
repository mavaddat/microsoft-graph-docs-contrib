---
title: Use Microsoft MCP Server for Enterprise in Azure AI Foundry
description: "Learn how to add Microsoft MCP Server for Enterprise as a tool in your Azure AI Foundry AI Agent to query enterprise identity data using natural language."
author: msewaweru
ms.author: eunicewaweru
ms.reviewer: FaithOmbongi
ms.subservice: ent-mcp-server
ms.topic: how-to
ms.date: 03/03/2026

#customer intent: As a developer or IT administrator, I want to integrate Microsoft MCP Server for Enterprise into my Azure AI Foundry agent so that I can query Microsoft Entra data using natural language.
---

# Use Microsoft MCP Server for Enterprise in Azure AI Foundry (preview)

Microsoft MCP Server for Enterprise can be integrated with Azure AI Foundry as a tool, enabling your AI agents to query Microsoft Entra data using natural language. This article explains how to configure and use the MCP Server in your Azure AI Foundry project.

> [!IMPORTANT]
> Microsoft MCP Server for Enterprise is currently in Preview.
> This information relates to a prerelease product that may be substantially modified before it's released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.
>
> Microsoft MCP Server for Enterprise is offered under the [Microsoft APIs Terms of Use](/legal/microsoft-apis/terms-of-use).

## Prerequisites

Before you begin, ensure you have:

- An Azure AI Foundry project and agent
- Completed the [quick start steps](get-started.md) to provision the Microsoft MCP Server for Enterprise
- **Application Administrator** or **Cloud Application Administrator** role in your Microsoft Entra tenant to create and configure app registrations and grant admin consent for API permissions
- **Contributor** or higher permissions on the Azure AI Foundry project resource to connect tools

## Create and configure an app registration

To enable authentication between Azure AI Foundry and Microsoft MCP Server for Enterprise, you need to create a Microsoft Entra app registration and configure the necessary API permissions.

1. Follow the [app registration guide](../app-registration.md) to create a Microsoft Entra app and obtain the client ID.

1. In your app registration, navigate to **Manage** > **API Permissions**.

1. Select **Add a permission**, then search for **Microsoft MCP Server for Enterprise**.

1. Select the permissions required for your scenarios.

1. Select **Grant admin consent for [your tenant]** to authorize the permissions.

## Connect the MCP Server as a tool in Azure AI Foundry

After creating and configuring your app registration, connect the Microsoft MCP Server for Enterprise as a tool in your Azure AI Foundry project.

1. In the [Azure AI Foundry portal](https://ai.azure.com/), ensure you're using the "New Foundry" UI and navigate to your project.

1. In the sidebar menu, select **Tools**, then search for **Microsoft MCP Server for Enterprise** in the **Catalog**.

1. Select **Connect** to begin the configuration.

1. Provide the following configuration:
   - **Name**: Enter a unique identifier for the tool
   - **Client ID**: Enter the app registration client ID from the previous section
   - **Token URL, Auth URL, and Refresh URL**: Replace `organizations` with your tenant ID if your Azure AI Foundry project and app registration are in different tenants; otherwise, leave as `organizations`

1. Select **Connect** and copy the **Redirect URL** provided.

1. Return to your Microsoft Entra app registration, navigate to **Authentication**, add the Redirect URL, and save your changes.

## Query Microsoft Entra data

After connecting the Microsoft MCP Server for Enterprise tool to your Azure AI Foundry agent, you can query your organization's data using natural language.

### Sign in and authorize access

When you first invoke the tool, you need to sign in and authorize access.

1. Select **Open consent** when prompted to sign in.

1. Follow the authentication prompts to grant access.

1. If sign-in fails, an error code appears in the `/closeme` window. Decode this base64-encoded value to view detailed error information.

1. Approve each MCP tool call as prompted during query execution.

### Example queries

You can ask questions such as:

- "How many users are in my tenant?"
- "Which users haven't signed in for the last 30 days?"
- "Show me all guest users with admin roles"

## Next steps

- [Overview of Microsoft MCP Server for Enterprise](overview.md)
- [Sample prompts for Microsoft MCP Server for Enterprise](mcp-server-sample-prompts.md)
