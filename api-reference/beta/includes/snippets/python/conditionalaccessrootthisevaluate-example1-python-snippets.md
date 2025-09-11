---
description: "Automatically generated file. DO NOT MODIFY"
---

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.identity.conditionalaccess.evaluate.evaluate_post_request_body import EvaluatePostRequestBody
from msgraph_beta.generated.models.user_sign_in import UserSignIn
from msgraph_beta.generated.models.application_context import ApplicationContext
from msgraph_beta.generated.models.sign_in_conditions import SignInConditions
from msgraph_beta.generated.models.conditional_access_device_platform import ConditionalAccessDevicePlatform
from msgraph_beta.generated.models.conditional_access_client_app import ConditionalAccessClientApp
from msgraph_beta.generated.models.risk_level import RiskLevel
from msgraph_beta.generated.models.insider_risk_level import InsiderRiskLevel
from msgraph_beta.generated.models.authentication_flow import AuthenticationFlow
from msgraph_beta.generated.models.conditional_access_transfer_methods import ConditionalAccessTransferMethods
from msgraph_beta.generated.models.device_info import DeviceInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EvaluatePostRequestBody(
	sign_in_identity = UserSignIn(
		odata_type = "#microsoft.graph.userSignIn",
		user_id = "15dc174b-f34c-4588-ac45-61d6e05dce93",
	),
	sign_in_context = ApplicationContext(
		odata_type = "#microsoft.graph.applicationContext",
		include_applications = [
			"00000003-0000-0ff1-ce00-000000000000",
		],
	),
	sign_in_conditions = SignInConditions(
		device_platform = ConditionalAccessDevicePlatform.Android,
		client_app_type = ConditionalAccessClientApp.Browser,
		sign_in_risk_level = RiskLevel.High,
		user_risk_level = RiskLevel.High,
		country = "US",
		ip_address = "40.77.182.32",
		insider_risk_level = InsiderRiskLevel.Elevated,
		authentication_flow = AuthenticationFlow(
			transfer_method = ConditionalAccessTransferMethods.DeviceCodeFlow,
		),
		device_info = DeviceInfo(
			is_compliant = True,
		),
	),
	applied_policies_only = True,
)

result = await graph_client.identity.conditional_access.evaluate.post(request_body)


```