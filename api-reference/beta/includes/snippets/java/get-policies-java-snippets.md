---
description: "Automatically generated file. DO NOT MODIFY"
---

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConditionalAccessPolicyCollectionResponse result = graphClient.identity().conditionalAccess().policies().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "displayName eq 'SimplePolicy1' or displayName eq 'SimplePolicy2'";
});


```