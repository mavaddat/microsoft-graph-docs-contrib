---
description: "Automatically generated file. DO NOT MODIFY"
---

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

NamedLocationCollectionResponse result = graphClient.identity().conditionalAccess().namedLocations().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "isof('microsoft.graph.compliantNetworkNamedLocation')";
});


```