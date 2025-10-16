---
description: "Automatically generated file. DO NOT MODIFY"
---

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationEventListener = {
    '@odata.type': '#microsoft.graph.onAttributeCollectionSubmitListener',
    priority: 500,
    conditions: {
        applications: {
            includeAllApplications: false,
            includeApplications: [
                {
                    appId: '0001111-aaaa-2222-bbbb-3333cccc4444'
                }
            ]
        }
    },
    handler: {
        '@odata.type': '#microsoft.graph.onAttributeCollectionSubmitCustomExtensionHandler',
        customExtension: {
            id: '66867d1f-7824-4f38-aad1-75da1ad09ee2'
        }
    }
};

await client.api('/identity/authenticationEventListeners')
	.version('beta')
	.post(authenticationEventListener);

```