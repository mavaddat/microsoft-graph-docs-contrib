---
title: "What's new in Microsoft Graph"
description: "Find out what's new in Microsoft Graph APIs, SDKs, documentation, and other resources."
author: "lauragra"
ms.localizationpriority: high
ms.date: 07/03/2025
ms.topic: whats-new
---

# What's new in Microsoft Graph

Microsoft Graph provides a unified programmability model that you can use to access data in Microsoft 365, Windows, and Enterprise Mobility + Security. This article provides information about what's new in Microsoft Graph APIs, documentation, SDKs, and more.

For more detailed API-level updates, see the [Microsoft Graph API changelog](https://developer.microsoft.com/graph/changelog/).

For details about previous updates to Microsoft Graph, see [Microsoft Graph what's new history](whats-new-earlier.md).

> [!IMPORTANT]
> Features in _preview_ status are subject to change without notice, and might not be promoted to generally available (GA) status. Don't use preview features in production apps.

## September 2025: New and generally available

### Applications

From the end of September 2025, the maximum page size for the [List servicePrincipals API](/graph/api/serviceprincipal-list) will be 100 objects from 999 objects.

### Backup storage

Added a note to the **artifactCount** property of the [granularMailboxRestoreArtifact](/graph/api/resources/granularmailboxrestoreartifact) about its upcoming deprecation.

### Device and app management | Cloud PC

- Added the `cloudPcUserSettingsPersistenceUsageThreshold`, `cloudPcDeprovisionedThreshold`, and `cloudPcReserveDeprovisionFailedThreshold` as supported values for the **conditionCategory** property of [ruleCondition](/graph/api/resources/devicemanagement-rulecondition?view=graph-rest-beta&preserve-view=true).
- Added the `cloudPcUserSettingsPersistenceScenario` and `cloudPcDeprovisionFailedScenario` as supported values for the **alertRuleTemplate** properties of [alertRecord](/graph/api/resources/devicemanagement-alertrecord?view=graph-rest-beta&preserve-view=true) and [alertRule](/graph/api/resources/devicemanagement-alertrule?view=graph-rest-beta&preserve-view=true).
- Use the **provisioningSourceType** property on [cloudPcUserSetting](/graph/api/resources/cloudpcusersetting?view=graph-rest-beta&preserve-view=true) to indicate the provisioning source of the Cloud PC prepared for an end user.

### Education

- The assignment service in the education APIs in Microsoft Graph has updated its throttling limits: per app per tenant requests are now limited to 350 per 10 seconds and 10,000 per hour. Per tenant for all apps, the limits are now 700 per 10 seconds and 20,000 per hour. A new limit of 25 requests per 10 seconds is also introduced for POST `/publish` operations.
- [Get](/graph/api/reportsroot-list-readingcoachpassages) a list of Reading Coach passages that were practiced by a student.
- [Get](/graph/api/reportsroot-list-speakerassignmentsubmissions) a list of speaker assignments that were submitted by a student.
- Use the [educationSpeakerProgressResource](/graph/api/resources/educationspeakerprogressresource) to help students gain confidence and reduce anxiety with AI-powered real-time feedback on public speaking skills, such as pace, pitch, and filler words. Speaker Progress also saves educators time and creates more opportunities for independent practice during in-class presentations.

### Employee experience | Employee engagement

Use the [onlineMeetingEngagementConversation](/graph/api/resources/onlinemeetingengagementconversation) APIs to [get all Teams question and answer (Q&A) conversation messages in a tenant](/graph/api/cloudcommunications-getallonlinemeetingmessages) and [list reactions](/graph/api/engagementconversationdiscussionmessage-list-reactions) in an online meeting.

### Files

Defined the following endpoints as supported for the [driveItem: discardCheckout](/graph/api/driveitem-discardcheckout) API:
- `/drives/{driveId}/items/{itemId}/discardCheckout`
- `/groups/{groupId}/drive/items/{itemId}/discardCheckout`
- `/me/drive/items/{item-id}/discardCheckout`
- `/sites/{siteId}/drive/items/{itemId}/discardCheckout`
- `/users/{userId}/drive/items/{itemId}/discardCheckout`

### Security | Alerts and incidents

- Added the following new properties to the [securityGroupEvidence](/graph/api/resources/security-securitygroupevidence) resource:
  - Use the **activeDirectoryObjectGuid** property to get the unique group identifier assigned by the on-premises Active Directory.
  - Use the **distinguishedName** property to identify the distinguished name of the security group.
  - Use the **friendlyName** property to identify the friendly name of the security group.	
  - Use the **sid** property to get the security identifier of the group.
- Use the **activeDirectoryObjectGuid** property on [userAccount](/graph/api/resources/security-useraccount) to get the unique user identifier assigned by the on-premises Active Directory.

### Security | eDiscovery

- Use the **caseType** property on [ediscoveryCaseSettings](/graph/api/resources/security-ediscoverycasesettings) to get or set the type of an eDiscovery case.
- Use the **reviewSetSettings** property on [ediscoveryCaseSettings](/graph/api/resources/security-ediscoverycasesettings) to get or set the review set settings for a case.

### Teamwork and communications | Calls and online meetings

- Removed `inACall`, `inAConferenceCall`, `inactive`, `inAMeeting`, `presenting`, `urgentInterruptionsOnly`, and `offWork` as supported values for the **activity** property of [presence](/graph/api/resources/presence).
- Removed `availableIdle` and `busyIdle` as supported values for the **availability** property of [presence](/graph/api/resources/presence).
- Added `focusing`, `inACall`, `inAMeeting`, and `presenting` as supported values to the **availability** property of [presence](/graph/api/resources/presence).
- The throttling limit for the [presence](/graph/api/resources/presence) resource increased from 1,500 to 10,000 requests per 30 seconds, per application per tenant.
- Use the **allowCopyingAndSharingMeetingContent** property on [onlineMeeting](/graph/api/resources/onlinemeeting) and [virtualEventSession](/graph/api/resources/virtualeventsession) to indicate whether the ability to copy and share meeting content is enabled for a meeting or virtual event session.

### Teamwork and communications | Messaging

- [Create a one-on-one or group chat with installed apps](/graph/api/chat-post#example-3-create-a-one-on-one-chat-with-installed-apps).
- [Create a one-on-one or group chat with RSC-granted apps](/graph/api/chat-post#example-4-create-a-one-on-one-chat-with-rsc-granted-apps).

## September 2025: New in preview only

### Backup storage

Added a note to the **artifactCount** property of the [granularMailboxRestoreArtifact](/graph/api/resources/granularmailboxrestoreartifact?view=graph-rest-beta&preserve-view=true) about its upcoming deprecation.

### Device and app management | Cloud PC

- Added `reserve` as a supported value for the **provisioningType** property of the [cloudPC](/graph/api/resources/cloudpc?view=graph-rest-beta&preserve-view=true) and [cloudPcServicePlan](/graph/api/resources/cloudpcserviceplan?view=graph-rest-beta&preserve-view=true).
- Use the **createdBy**, **createdDateTime**, **lastModifiedBy**, and **lastModifiedDateTime** properties to determine when and by whom a [cloudPcProvisioningPolicy](/graph/api/resources/cloudpcprovisioningpolicy?view=graph-rest-beta&preserve-view=true) was created or modified.

### Education

- [Create](/graph/api/educationassignmentsettings-post-gradingschemes?view=graph-rest-beta&preserve-view=true) a new [educationGradingScheme](/graph/api/resources/educationgradingscheme?view=graph-rest-beta&preserve-view=true) on an [educationClass](/graph/api/resources/educationclass?view=graph-rest-beta&preserve-view=true).
- [Add](/graph/api/educationassignment-put-gradingscheme?view=graph-rest-beta&preserve-view=true) an existing [educationGradingScheme](/graph/api/resources/educationgradingscheme?view=graph-rest-beta&preserve-view=true) to an existing [educationAssignment](/graph/api/resources/educationassignment?view=graph-rest-beta&preserve-view=true).
- [Add](/graph/api/educationassignmentsettings-put-defaultgradingscheme?view=graph-rest-beta&preserve-view=true) the default [educationGradingScheme](/graph/api/resources/educationgradingscheme?view=graph-rest-beta&preserve-view=true) to an [educationAssignmentSettings](/graph/api/resources/educationassignmentsettings?view=graph-rest-beta&preserve-view=true) object.

### Files

Defined the following endpoints as supported for the [driveItem: discardCheckout](/graph/api/driveitem-discardcheckout?view=graph-rest-beta&preserve-view=true) API:
- `/drives/{driveId}/items/{itemId}/discardCheckout`
- `/groups/{groupId}/drive/items/{itemId}/discardCheckout`
- `/me/drive/items/{item-id}/discardCheckout`
- `/sites/{siteId}/drive/items/{itemId}/discardCheckout`
- `/users/{userId}/drive/items/{itemId}/discardCheckout`

### Calendars | Places

- The new map APIs in Places enable applications with appropriate read or write permissions to interact with map feature objects. For more information, see [Working with the Places API in Microsoft Graph](/graph/api/resources/places-api-overview?view=graph-rest-beta&preserve-view=true#map-feature-types).
- Use the [checkInClaim](/graph/api/resources/checkinclaim?view=graph-rest-beta&preserve-view=true) resource to represent the check-in status of an Outlook calendar [event](/graph/api/resources/event?view=graph-rest-beta&preserve-view=true) booked at a place. For more information see, [Create checkInClaim](/graph/api/place-post-checkins?view=graph-rest-beta&preserve-view=true) and [Get checkInClaim](/graph/api/checkinclaim-get?view=graph-rest-beta&preserve-view=true).

### Device and app management | Cloud PC

- Use the **groupDetail** property on [cloudPC](/graph/api/resources/cloudpc?view=graph-rest-beta&preserve-view=true) to get the Microsoft Entra group details associated with a Reserve Cloud PC assignment.
- Use the **userDetail** property on [cloudPC](/graph/api/resources/cloudpc?view=graph-rest-beta&preserve-view=true) to get the Microsoft Entra user details associated with a Reserve Cloud PC assignment.

### Teamwork and communications | Calls and online meetings

- Removed `inACall`, `inAConferenceCall`, `inactive`, `inAMeeting`, `presenting`, `urgentInterruptionsOnly`, and `offWork` as supported values for the **activity** property of [presence](/graph/api/resources/presence).
- Removed `availableIdle` and `busyIdle` as supported values for the **availability** property of [presence](/graph/api/resources/presence?view=graph-rest-beta&preserve-view=true).
- Added `focusing`, `inACall`, `inAMeeting`, and `presenting` as supported values to the **availability** property of [presence](/graph/api/resources/presence?view=graph-rest-beta&preserve-view=true).
- The throttling limit for the [presence](/graph/api/resources/presence?view=graph-rest-beta&preserve-view=true) resource increased from 1,500 to 10,000 requests per 30 seconds, per application per tenant.

### Teamwork and communications | Messaging

- [Create a one-on-one or group chat with installed apps](/graph/api/chat-post?view=graph-rest-beta&preserve-view=true#example-3-create-a-one-on-one-chat-with-installed-apps).
- [Create a one-on-one or group chat with RSC-granted apps](/graph/api/chat-post?view=graph-rest-beta&preserve-view=true#example-4-create-a-one-on-one-chat-with-rsc-granted-apps).

### Workbooks and charts

- Create a new [workbookComment](/graph/api/workbookcomment-post-comments?view=graph-rest-beta&preserve-view=true).
- Use the **cellAddress** property on [workbookComment](/graph/api/resources/workbookcomment?view=graph-rest-beta&preserve-view=true) to get the cell where the comment is located.
- Use the **mentions** property on [workbookComment](/graph/api/resources/workbookcomment?view=graph-rest-beta&preserve-view=true) or [workbookCommentReply](/graph/api/resources/workbookcommentreply?view=graph-rest-beta&preserve-view=true) to get all the people mentioned within the comment or reply.
- Use the **richContent** property on [workbookComment](/graph/api/resources/workbookcomment?view=graph-rest-beta&preserve-view=true) or [workbookCommentReply](/graph/api/resources/workbookcommentreply?view=graph-rest-beta&preserve-view=true) to get the rich content of the comment or reply.

## August 2025: New and generally available

### Backup storage

- Use the **offboardRequestedDateTime** property on [driveProtectionUnit](/graph/api/resources/driveprotectionunit), [mailboxProtectionUnit](/graph/api/resources/mailboxprotectionunit), and [siteProtectionUnit](/graph/api/resources/siteprotectionunit) to get the date and time when protection unit offboard was requested.
- Added `offboardRequested`, `offboarded`, and `cancelOffboardRequested` as supported values for the **status** property of [driveProtectionUnit](/graph/api/resources/driveprotectionunit), [mailboxProtectionUnit](/graph/api/resources/mailboxprotectionunit), and [siteProtectionUnit](/graph/api/resources/siteprotectionunit).

### Device and app management | Cloud PC

Use the [resize](/graph/api/cloudpc-resize) operation of [cloudPC](/graph/api/resources/cloudpc) to upgrade or downgrade an existing Cloud PC to a configuration with a new virtual CPU (vCPU) and storage size.

### Sites and lists

Removed support for delegated permissions in the [List sites](/graph/api/site-list) and [site: delta](/graph/api/site-delta) APIs.


### Teamwork and communications | Calls and online meetings

- Use the **isInteractiveRosterEnabled** property on [incomingCallOptions](/graph/api/resources/incomingcalloptions) and [outgoingCallOptions](/graph/api/resources/outgoingcalloptions) to indicate whether delta roster filtering by participant interactivity is enabled.
- Use the **outOfOfficeSettings** property on [presence](/graph/api/resources/presence) to get the out-of-office settings for a user.
- Use the **sequenceNumber** property on [presence](/graph/api/resources/presence) to get the lexicographically sortable String stamp that represents the version of a **presence** object.
- Use the **isEndToEndEncryptionEnabled** property on [onlineMeeting](/graph/api/resources/onlinemeeting) and [virtualEventSession](/graph/api/resources/virtualeventsession) to indicate whether end-to-end encryption (E2EE) is enabled for a meeting or virtual event session.

## August 2025: New in preview only

### Backup storage

- Use the **isEnabled** property on [exchangeProtectionPolicy](/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-beta&preserve-view=true), [oneDriveForBusinessProtectionPolicy](/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-beta&preserve-view=true), and [sharePointProtectionPolicy](/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-beta&preserve-view=true) to get whether the policy is enabled.
- Use the **protectionPolicyArtifactCount** property on [exchangeProtectionPolicy](/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-beta&preserve-view=true), [oneDriveForBusinessProtectionPolicy](/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-beta&preserve-view=true), and [sharePointProtectionPolicy](/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-beta&preserve-view=true) to get the count of artifacts in the protection policy by status.

### Calendars | Places

[Create](/graph/api/place-post?view=graph-rest-beta&preserve-view=true), [get descendants](/graph/api/place-descendants?view=graph-rest-beta&preserve-view=true), and [delete](/graph/api/place-delete?view=graph-rest-beta&preserve-view=true) a [place](/graph/api/resources/place?view=graph-rest-beta&preserve-view=true) and its derived objects (for example, [building](/graph/api/resources/building?view=graph-rest-beta&preserve-view=true), [desk](/graph/api/resources/desk?view=graph-rest-beta&preserve-view=true), [floor](/graph/api/resources/floor?view=graph-rest-beta&preserve-view=true), or [section](/graph/api/resources/section?view=graph-rest-beta&preserve-view=true)). These APIs enable scalable onboarding and management of the Places directory.

### Device and app management | Cloud PC

- Deprecated the `/deviceManagement/virtualEndpoint/cloudPCs/{cloudPCId}/getCloudPcLaunchInfo` endpoint in favor of delegated permission requests using either `/me/cloudPCs/{cloudPCId}/getCloudPcLaunchInfo` or `/users/{userId}/cloudPCs/{id}/getCloudPcLaunchInfo` in the [getCloudPcLaunchInfo](/graph/api/cloudpc-getcloudpclaunchinfo) method.
- Use the **provisioningSourceType** property on [cloudPcUserSetting](/graph/api/resources/cloudpcusersetting?view=graph-rest-beta&preserve-view=true) to indicate the provisioning source of the Cloud PC prepared for an end user.

### Files

Learn how to [add an application permission to a driveItem in OneDrive or SharePoint Online](/graph/api/driveitem-post-permissions?view=graph-rest-beta&preserve-view=true#example-1-add-an-application-permission-to-a-driveitem-in-onedrive-or-sharepoint-online) and how to [add a SharePoint group permission to a driveItem in a SharePoint Embedded container](/graph/api/driveitem-post-permissions?view=graph-rest-beta&preserve-view=true#example-2-add-a-sharepoint-group-permission-to-a-driveitem-in-a-sharepoint-embedded-container).

### Identity and access | Identity and sign-in

The [federatedTokenValidationPolicy](/graph/api/resources/federatedtokenvalidationpolicy?view=graph-rest-beta&preserve-view=true) APIs now support management by lesser-privileged Microsoft Entra roles including Security Administrator, Hybrid Identity Administrator, and External Identity Provider Administrator roles, removing dependency on the Global Administrator role.

### Mail

Deprecated the [markAsJunk](/graph/api/message-markasjunk?view=graph-rest-beta&preserve-view=true) and [markAsNotJunk](/graph/api/message-markasnotjunk?view=graph-rest-beta&preserve-view=true) actions in favor of the [reportMessage](/graph/api/message-reportmessage?view=graph-rest-beta&preserve-view=true) API.

### Security | Identities

Added the [identityAccounts](/graph/api/resources/security-identityaccounts?view=graph-rest-beta&preserve-view=true) and its related methods that lets you retrieve details of user accounts observed by Microsoft Defender for Identity and apply response actions such as disabling accounts and forcing password reset. 

### Sites and lists

Removed support for delegated permissions in the [List sites](/graph/api/site-list?view=graph-rest-beta&preserve-view=true) and [site: delta](/graph/api/site-delta?view=graph-rest-beta&preserve-view=true) APIs.

### Teamwork and communications | Calls and online meetings

Use the [adhocCall](/graph/api/resources/adhoccall?view=graph-rest-beta&preserve-view=true) resource to subscribe to transcripts and recordings at the tenant level, for a specific call, or per user. For more information, see [Get change notifications for transcripts and recordings using Microsoft Graph](/graph/teams-changenotifications-callrecording-and-calltranscript).

### Terraform Templates for Microsoft Graph resources

[Terraform templates for Microsoft Graph resources](/graph/templates/terraform/overview-terraform-for-graph) is now in preview. Using Terraform templates, you can deploy the following Microsoft Graph resources for your infrastructure as code (IaC) projects:

- Applications
- App role assignments
- Federated identity credentials
- Groups
- OAuth2 permissions grants (delegated permissions grants)
- Service principals
- Users

## Contribute to Microsoft Graph

Are there scenarios you'd like Microsoft Graph to support?

- Suggest and vote for new features by using the [Microsoft Graph Feedback Portal](https://aka.ms/graphfeedback). Some new features originate as popular requests from the developer community. The Microsoft Graph team regularly evaluates customer needs and releases new features to the beta (`https://graph.microsoft.com/beta`) and v1.0 (`https://graph.microsoft.com/v1.0`) endpoints.

- [Join](https://aka.ms/m365-dev-call) the weekly Microsoft 365 platform community call and become an active member of the Microsoft Graph community. To discover the full calendar of developer calls, visit the [Microsoft 365 and Power Platform community page](https://aka.ms/community/calls).

- [Join](https://ux.microsoft.com/Panel/M365Devs?utm_source=graphDocs) our research panel to provide your input on our developer experiences.

## Related content
- [Microsoft Graph developer blog](https://devblogs.microsoft.com/microsoft365dev/category/microsoft-graph/).
- [Microsoft Graph API changelog](https://developer.microsoft.com/graph/changelog/).
- [Microsoft Graph what's new history](whats-new-earlier.md).
