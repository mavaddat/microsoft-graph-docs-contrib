---
description: "Automatically generated file. DO NOT MODIFY"
---

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ConditionalAccessPolicy;
use Microsoft\Graph\Beta\Generated\Models\ConditionalAccessConditionSet;
use Microsoft\Graph\Beta\Generated\Models\RiskLevel;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConditionalAccessPolicy();
$conditions = new ConditionalAccessConditionSet();
$conditions->setSignInRiskLevels([new RiskLevel('high'),new RiskLevel('medium'),new RiskLevel('low'),	]);
$requestBody->setConditions($conditions);

$result = $graphServiceClient->identity()->conditionalAccess()->policies()->byConditionalAccessPolicyId('conditionalAccessPolicy-id')->patch($requestBody)->wait();

```