---
description: "Automatically generated file. DO NOT MODIFY"
---

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const whatIfAnalysisResult = {
    signInIdentity: {
        '@odata.type': '#microsoft.graph.userSignIn',
        userId: '15dc174b-f34c-4588-ac45-61d6e05dce93'
    },
    signInContext: {
        '@odata.type': '#microsoft.graph.authContext',
        authenticationContextValue: 'c37'
    },
    signInConditions: {
        devicePlatform: 'windows',
        clientAppType: 'mobileAppsAndDesktopClients',
        signInRiskLevel: 'medium',
        userRiskLevel: 'none',
        country: 'US',
        ipAddress: '40.77.182.32',
        insiderRiskLevel: 'moderate',
        authenticationFlow: {
            transferMethod: 'authenticationTransfer'
        },
        deviceInfo: {
            profileType: 'Standard'
        }
    },
    appliedPoliciesOnly: true
};

await client.api('/identity/conditionalAccess/evaluate')
	.version('beta')
	.post(whatIfAnalysisResult);

```