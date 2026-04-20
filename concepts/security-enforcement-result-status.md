---
title: "Understand enforcement result status in Microsoft Purview"
description: "Learn when to use enforcement result status and how to interpret enforcement outcomes returned by Microsoft Purview data security and governance APIs."
author: "zhengnlu"
ms.date: 03/12/2026
ms.localizationpriority: medium
ms.subservice: "security"
ms.topic: concept-article
---

# Understand enforcement result status in Microsoft Purview

In Microsoft Purview data security and governance scenarios, an enforcement result status records what actually happened after a data loss prevention (DLP) policy match when enforcement is carried out by an external enforcement plane such as a browser, network control, or app.

Use enforcement result status when your application or enforcement plane must report the final enforcement outcome back to Microsoft Purview after policy evaluation.

## What enforcement result status tells admins

Enforcement result status helps administrators understand the real-world outcome of enforcement, including whether:

- The action was enforced successfully.
- The user overrode the action.
- Enforcement failed.
- No enforcement confirmation was received.

## Typical examples

Common examples include the following scenarios:

- A browser DLP block succeeded or failed.
- A user selected an override option.
- Enforcement timed out or the enforcement agent failed.
- No enforcement confirmation was ever received.

## Enforcement result status compared to rule match

Rule match and enforcement result status describe different stages of policy processing:

- A rule match means that a DLP policy condition matched the content or activity.
- An enforcement result status means that the enforcement plane reported what happened during enforcement.

In other words, a rule match answers "Did the policy match?" and enforcement result status answers "What happened when enforcement was attempted?"

## Related APIs and resources

- [Microsoft Purview data security and governance APIs in Microsoft Graph](/graph/security-datasecurityandgovernance-overview)
- [contentActivityMetadata resource type](/graph/api/resources/contentactivitymetadata)
- [enforcementResultStatus enum](/graph/api/resources/security-enforcementresultstatus)