---
description: "Automatically generated file. DO NOT MODIFY"
---

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TimeOffReason timeOffReason = new TimeOffReason();
timeOffReason.setDisplayName("Vacation");
timeOffReason.setIconType(TimeOffReasonIconType.Plane);
timeOffReason.setIsActive(true);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("code", "VacationCode");
timeOffReason.setAdditionalData(additionalData);
TimeOffReason result = graphClient.teams().byTeamId("{team-id}").schedule().timeOffReasons().post(timeOffReason);


```