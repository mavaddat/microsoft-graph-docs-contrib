---
title: Use Microsoft MCP Server for Enterprise in Azure AI Foundry
description: "Learn how to add Microsoft MCP Server for Enterprise as a tool in your Azure AI Foundry AI Agent to query enterprise identity data using natural language."
author: junruotian
ms.author: junruotian
ms.reviewer: FaithOmbongi
ms.subservice: ent-mcp-server
ms.topic: how-to
ms.date: 02/17/2026

#customer intent: As a developer or IT administrator, I want to integrate Microsoft MCP Server for Enterprise into my Azure AI Foundry agent so that I can query Microsoft Entra data using natural language.
---

# Use Microsoft MCP Server for Enterprise in Azure AI Foundry (preview)

Microsoft MCP Server for Enterprise can be integrated with Azure AI Foundry as a tool, enabling your AI agents to query Microsoft Entra data using natural language. This article explains how to configure and use the MCP Server in your Azure AI Foundry project.

> [!IMPORTANT]
> Microsoft MCP Server for Enterprise is currently in PREVIEW.
> This information relates to a prerelease product that may be substantially modified before it's released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.
>
> Microsoft MCP Server for Enterprise is offered under the [Microsoft APIs Terms of Use](/legal/microsoft-apis/terms-of-use).

## Prerequisites

Before you begin, ensure you have:

- An Azure AI Foundry project and agent
- Permissions to create and configure Microsoft Entra app registrations
- Completed the [quick start steps](get-started.md) to provision the Microsoft MCP Server for Enterprise

## Create and configure an app registration

1. Follow the [app registration guide](../app-registration.md) to create a Microsoft Entra app and obtain the client ID.

1. In your app registration, navigate to **Manage** > **API Permissions**.

1. Select **Add a permission**, then search for **Microsoft MCP Server for Enterprise**.

1. Select the permissions required for your scenarios.

1. Select **Grant admin consent for [your tenant]** to authorize the permissions.

## Connect the MCP Server as a tool in Azure AI Foundry

1. In the Azure AI Foundry portal, ensure you're using the "New Foundry" UI and navigate to your project.

1. In the **Tools** section, select **Connect a tool**.

1. Under **Catalog**, search for **Microsoft MCP Server for Enterprise** and select **Create**.

1. Provide the following configuration:
   - **Name**: Enter a unique identifier for the tool
   - **Client ID**: Enter the app registration client ID from the previous section
   - **Token URL, Auth URL, and Refresh URL**: Replace `organizations` with your tenant ID if your Azure AI Foundry project and app registration are in different tenants; otherwise, leave as `organizations`

1. Select **Connect** and copy the **Redirect URL** provided.

1. Return to your Microsoft Entra app registration, navigate to **Authentication**, add the Redirect URL, and save your changes.

## Use the tool to query Microsoft Entra data

After adding the Microsoft MCP Server for Enterprise tool to your Azure AI Foundry agent, you can query your organization's data using natural language. Example questions include:

- "How many users are in my tenant?"
- "Which users haven't signed in for the last 30 days?"
- "Show me all guest users with admin roles"

### Sign in and authorize access

When you first invoke the tool:

1. Select **Open consent** when prompted to sign in.

1. Follow the authentication prompts to grant access.

1. If sign-in fails, an error code appears in the `/closeme` window. Decode this base64-encoded value to view detailed error information.

1. Approve each MCP tool call as prompted during query execution.

## Next steps

- [Overview of Microsoft MCP Server for Enterprise](overview.md)
- [Sample prompts for Microsoft MCP Server for Enterprise](mcp-server-sample-prompts.md)
