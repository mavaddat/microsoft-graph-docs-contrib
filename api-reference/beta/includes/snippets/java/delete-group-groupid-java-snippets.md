---
description: "Automatically generated file. DO NOT MODIFY"
---

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.policies().mobileAppManagementPolicies().byMobileAppManagementPolicyId("{mobileAppManagementPolicy-id}").includedGroups().byGroupId("{group-id}").ref().delete();


```