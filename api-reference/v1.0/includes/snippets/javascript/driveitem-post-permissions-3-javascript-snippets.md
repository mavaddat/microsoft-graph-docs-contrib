---
description: "Automatically generated file. DO NOT MODIFY"
---

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const permission = {
  grantedToIdentitiesV2: {
    sharePointGroup: {
      id: 'ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0'
    }
  },
  roles: ['write']
};

await client.api('/drives/b!s8RqPCGh0ESQS2EYnKM0IKS3lM7GxjdAviiob7oc5pXv_0LiL-62Qq3IXyrXnEop/items/1/permissions')
	.version('beta')
	.post(permission);

```