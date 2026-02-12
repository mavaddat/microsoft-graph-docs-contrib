---
description: "Automatically generated file. DO NOT MODIFY"
---

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Permission;
use Microsoft\Graph\Beta\Generated\Models\SharePointGroupIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Permission();
$grantedToIdentitiesV2 = new SharePointIdentitySet();
$grantedToIdentitiesV2SharePointGroup = new SharePointGroupIdentity();
$grantedToIdentitiesV2SharePointGroup->setId('ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0');
$grantedToIdentitiesV2->setSharePointGroup($grantedToIdentitiesV2SharePointGroup);
$requestBody->setGrantedToIdentitiesV2($grantedToIdentitiesV2);
$requestBody->setRoles(['write', 	]);

$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->permissions()->post($requestBody)->wait();

```