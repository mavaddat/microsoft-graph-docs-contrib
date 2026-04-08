---
description: "Automatically generated file. DO NOT MODIFY"
---

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
<<<<<<<< HEAD:api-reference/beta/includes/snippets/csharp/completemigration-chat-fail-csharp-snippets.md
await graphClient.Chats["{chat-id}"].CompleteMigration.PostAsync();
========
await graphClient.Teams["{team-id}"].Channels["{channel-id}"].CompleteMigration.PostAsync();
>>>>>>>> 71f0e15f205 (head commits):api-reference/beta/includes/snippets/csharp/completemigration-channel-fail-csharp-snippets.md


```