# Microsoft Cloud Licensing

## Contacts

| Role | Name                            |
| ---- | ------------------------------- |
| PM   | {Shelley Gu} ({shegu})          |
| PM   | {Armando Valenzuela} ({armanv}) |
| Eng  | {Patrick Starrin} ({pastarri})  |
| Eng  | {Jacob Celletti} ({jcelletti})  |
| Eng  | {Jeesh Nair Murali} ({jeeshn})  |

## Scenarios and personas

Today's licensing model makes no distinction between different subscriptions for the same SKU, requires centralized management of license assignments, and does not allow third-party or device-based offerings. The Microsoft Cloud Licensing (MCL) platform separates licenses from different subscriptions into smaller, independently manageable pools called _allotments_. The association of licenses to their unique subscriptions enables more granular accounting and reporting for our large customers, some of whom have previously enlisted partners to develop solutions on top of Microsoft's licensing platform to provide this capability. This isolation between subscriptions also allows Microsoft to disable assignments in a reliable and predictable manner when subscriptions expire, instead of being forced to choose between taking away access from random users and letting the customer use more licenses than they're paying for. (We choose the latter; this is a known vulnerability for abuse.)

Allotments can be managed at the scope of the whole organization or an individual worker, enabling departmental purchase and management to exist alongside the traditional admin paradigm. Because allotments do not require their backing subscriptions to be provisioned in the directory, they also allow third-party independent software vendors to leverage our licensing platform for their products. This is especially useful for third-party add-ons to extensible Microsoft products such as Teams, Office, and Power BI. We also support subscriptions intended for devices instead of users, which can be incredibly valuable for shared-device scenarios in enterprise and educational settings.

To facilitate management and runtime enforcement of these new licensing capabilities, we are adding several new entity types to Graph that support various perspectives and use cases.

Rowan is a License Admin for Contoso; their job is to ensure Contoso employees have access to the tools they need to be productive in their roles. (Rowan appears in Scenarios 1–9.) Teresa and Ashton, coworkers of Rowan's, are also License Admins at Contoso. (Teresa and Ashton appear in Scenario 9 as second and third actors, to demonstrate how the new entities coexist and interact with the existing licensing properties and actions in Microsoft Graph.)

Petra is a software engineer for a Microsoft partner that offers solutions built on top of our platform to their own clients. She is developing a license management interface to try and make the job of people like Rowan easier. (Petra appears in Scenario 10.)

Nasim is a software engineer for Fabrikam, currently developing the license enforcement component of a new application that her employer plans to sell to enterprise customers. (Nasim appears in Scenarios 11–15.)

### 1. Enumerate the organization's allotments

Rowan wants to review Contoso's allotments to understand their current license positions.

```http
GET https://graph.microsoft.com/v1/admin/cloudLicensing/allotments
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": [
        {
            "id": "2afb23bc-12bb-4e01-ac77-a909d1723756",
            "allottedUnits": 2500,
            "assignableTo": "user,group",
            "catalogId": "ZO93XWY1FXQZ:0001",
            "consumedUnits": 2184,
            "managementScope": "organization",
            "services": [
                {
                    "assignableTo": "user,group",
                    "planId": "55e6ca1f-c33b-452d-b937-7e3543410b1d",
                    "planName": "QUANTUM_ENTANGLED_INBOX"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "6a02f68f-f783-407c-866a-efbc4203b24a",
                    "planName": "CEREBRAL_EMULATOR"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "92e0703e-6eea-4e19-a1e0-9d5e9bffb043",
                    "planName": "SELF_AWARE_VIRTUAL_ASSISTANT_PREMIUM_PLUS"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "a13d48d6-33a7-4e87-8d6d-72ef00a0e7ba",
                    "planName": "QUID_VULPIS_DICIT"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "dd794291-6d32-490e-aa64-6c7bc5e39bdb",
                    "planName": "QUANTUM_ENCRYPTION"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "f1df97e2-b3d9-4c17-b931-30fdbfeb5c18",
                    "planName": "CONSCIOUSNESS_UPLOADER"
                }
            ],
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c",
            "skuPartNumber": "SINGULARITY_BUSINESS_SUITE",
            "subscriptions": [
                {
                    "subscriptionId": "a8d72db0-39ce-485a-97f0-0c6a99929d10",
                    "nextLifecycleDate": "2024-09-05",
                    "startDate": "2023-09-05",
                    "state": "active",
                    "tags": "none"
                }
            ]
        },
        {
            "id": "5df6f595-659f-4c49-a3ec-0792c83c10b0",
            "allottedUnits": 5,
            "assignableTo": "user",
            "catalogId": "ZO93XWY1FXQZ:0002",
            "consumedUnits": 5,
            "managementScope": "individual",
            "services": [
                {
                    "assignableTo": "user",
                    "planId": "1251a70b-94c8-4d07-824f-7be9309deccc",
                    "planName": "SELF_AWARE_VIRTUAL_ASSISTANT_LITE"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "6a02f68f-f783-407c-866a-efbc4203b24a",
                    "planName": "CEREBRAL_EMULATOR"
                },
                {
                    "assignableTo": "user",
                    "planId": "a96ea1dc-a65e-4bb0-9b75-ab20fab9b353",
                    "planName": "QUANTUM_ENTANGLED_INBOX_LITE"
                }
            ],
            "skuId": "d8d9bc3e-ce66-45d5-84a9-d3ac9d4b3741",
            "skuPartNumber": "SINGULARITY_DEPT",
            "subscriptions": [
                {
                    "subscriptionId": "9d11f64b-82f5-4c63-a50b-25d1856fe188",
                    "nextLifecycleDate": "2023-10-28",
                    "startDate": "2023-09-28",
                    "state": "active",
                    "tags": "none"
                }
            ]
        },
        {
            "id": "2b7fc5fe-2267-404e-ada7-32b321f116ee",
            "allottedUnits": 32,
            "assignableTo": "device,group",
            "catalogId": "G2ALO6SPZNK7:0001",
            "consumedUnits": 32,
            "managementScope": "organization",
            "services": [
                {
                    "assignableTo": "device,group",
                    "planId": "ff22ee64-341d-4d78-92d5-7751baea3bbd",
                    "planName": "QUANTUM_TELEPORTER_AUTO_FAILOVER"
                }
            ],
            "subscriptions": [
                {
                    "subscriptionId": "6b7cc9cc-e3ba-4546-aeee-cd8126012e8e",
                    "nextLifecycleDate": "2024-09-05",
                    "startDate": "2023-09-05",
                    "state": "active",
                    "tags": "trial"
                }
            ]
        },
        {
            "id": "58b28998-1ca2-4f65-924c-902812d25692",
            "allottedUnits": 15,
            "assignableTo": "user,group",
            "catalogId": "ZO93XWY1FXQZ:0001",
            "consumedUnits": 14,
            "managementScope": "organization",
            "services": [
                {
                    "assignableTo": "user,group",
                    "planId": "55e6ca1f-c33b-452d-b937-7e3543410b1d",
                    "planName": "QUANTUM_ENTANGLED_INBOX"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "6a02f68f-f783-407c-866a-efbc4203b24a",
                    "planName": "CEREBRAL_EMULATOR"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "92e0703e-6eea-4e19-a1e0-9d5e9bffb043",
                    "planName": "SELF_AWARE_VIRTUAL_ASSISTANT_PREMIUM_PLUS"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "a13d48d6-33a7-4e87-8d6d-72ef00a0e7ba",
                    "planName": "QUID_VULPIS_DICIT"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "dd794291-6d32-490e-aa64-6c7bc5e39bdb",
                    "planName": "QUANTUM_ENCRYPTION"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "f1df97e2-b3d9-4c17-b931-30fdbfeb5c18",
                    "planName": "CONSCIOUSNESS_UPLOADER"
                }
            ],
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c",
            "skuPartNumber": "SINGULARITY_BUSINESS_SUITE",
            "subscriptions": [
                {
                    "subscriptionId": "37092315-0edb-4407-a8d9-d5e8ae592ea3",
                    "nextLifecycleDate": "2023-12-19",
                    "startDate": "2022-12-19",
                    "state": "active",
                    "tags": "trial"
                }
            ]
        },
        {
            "id": "fb879ecd-3aef-4a9e-a227-2e2f988332df",
            "allottedUnits": 129,
            "assignableTo": "user,group",
            "catalogId": "RZD5AJDZ6AFP:0001",
            "consumedUnits": 96,
            "managementScope": "organization",
            "services": [
                {
                    "assignableTo": "user,group",
                    "planId": "1732e0a8-9447-4754-a910-9e4bb05c705c",
                    "planName": "TIME_TRAVEL_BACKUP_RESTORE"
                }
            ],
            "skuId": "f48db87f-583c-486e-a6de-096155d8fb8f",
            "skuPartNumber": "TIME_TRAVEL_BACKUP_RESTORE",
            "subscriptions": [
                {
                    "subscriptionId": "397afa4c-1416-430e-bc09-533b3c2c7c81",
                    "nextLifecycleDate": "2024-09-05",
                    "startDate": "2023-09-05",
                    "state": "active",
                    "tags": "none"
                }
            ]
        }
    ]
}
```

### 2. Get the total license counts per SKU

Rowan wants an aggregated summary view of their organization's allotments, grouping them by skuId and catalogId and calculating the total license counts for each group. They compose the following data aggregation query, using features introduced by [OData Extension for Data Aggregation Version 4.0](https://docs.oasis-open.org/odata/odata-data-aggregation-ext/v4.0/cs03/odata-data-aggregation-ext-v4.0-cs03.html).

```http
GET https://graph.microsoft.com/v1/admin/cloudLicensing/allotments?$apply=groupby((catalogId, skuId), aggregate(allottedUnits with sum as totalAllottedUnits, consumedUnits with sum as totalConsumedUnits))
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": [
        {
            "catalogId": "ZO93XWY1FXQZ:0001",
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c",
            "totalAllottedUnits": 2515,
            "totalConsumedUnits": 2198,
        },
        {
            "catalogId": "ZO93XWY1FXQZ:0002",
            "skuId": "d8d9bc3e-ce66-45d5-84a9-d3ac9d4b3741",
            "totalAllottedUnits": 5,
            "totalConsumedUnits": 5,
        },
        {
            "catalogId": "G2ALO6SPZNK7:0001",
            "totalAllottedUnits": 32,
            "totalConsumedUnits": 32,
        },
        {
            "catalogId": "RZD5AJDZ6AFP:0001",
            "skuId": "f48db87f-583c-486e-a6de-096155d8fb8f",
            "totalAllottedUnits": 129,
            "totalConsumedUnits": 96,
        }
    ]
}
```

Note that there is one fewer result here than in Scenario 1. Two of the allotments have the same catalogId and skuId, so they were grouped and their license counts were added together.

### 3. Gather information about a departmental purchase

Rowan wants to know who purchased 5 licenses of `SINGULARITY_DEPT` and who those licenses were assigned to.

```http
GET https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/5df6f595-659f-4c49-a3ec-0792c83c10b0?$expand=assignments($expand=assignedTo($select=id,displayName)),owner($select=id,displayName)&$select=assignments,owner
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "assignments": [
        {
            "id": "5db49650-5c1e-43ab-ab1e-de992a027fa4",
            "assignedTo": {
                "@odata.type": "#microsoft.graph.user",
                "id": "adc83d59-90ab-4a07-a3c8-6b0a41890154",
                "displayName": "Herbert Pickle (he/him)"
            },
            "disabledServicePlanIds": ["6a02f68f-f783-407c-866a-efbc4203b24a"],
            "skuId": "d8d9bc3e-ce66-45d5-84a9-d3ac9d4b3741"
        },
        {
            "id": "e705569f-8b6f-474c-b969-9aee3912d8c9",
            "assignedTo": {
                "@odata.type": "#microsoft.graph.user",
                "id": "8f7b1010-f98f-49de-87b0-8a5ea493c513",
                "displayName": "Indira Bose (she/her)"
            },
            "disabledServicePlanIds": [],
            "skuId": "d8d9bc3e-ce66-45d5-84a9-d3ac9d4b3741"
        },
        {
            "id": "4b7c27b8-d0a7-4cfe-add8-6be441ebe0bd",
            "assignedTo": {
                "@odata.type": "#microsoft.graph.user",
                "id": "0a7c19be-59e0-4b83-bd12-129fa9d859ea",
                "displayName": "Theodore Fukuyama (he/him)"
            },
            "disabledServicePlanIds": [],
            "skuId": "d8d9bc3e-ce66-45d5-84a9-d3ac9d4b3741"
        },
        {
            "id": "24d5ee32-3d93-46a2-b092-664a5e08f66c",
            "assignedTo": {
                "@odata.type": "#microsoft.graph.user",
                "id": "0c054098-474a-423e-946c-a06b9de78fb3",
                "displayName": "Dahlia Bishop (she/they)"
            },
            "disabledServicePlanIds": [],
            "skuId": "d8d9bc3e-ce66-45d5-84a9-d3ac9d4b3741"
        },
        {
            "id": "6b839f95-11ac-44e6-be0b-db67db0b0249",
            "assignedTo": {
                "@odata.type": "#microsoft.graph.user",
                "id": "f1fab0cc-98bd-4174-8fee-2180424b2f02",
                "displayName": "Yara Figueira Romeiro (she/her)"
            },
            "disabledServicePlanIds": [],
            "skuId": "d8d9bc3e-ce66-45d5-84a9-d3ac9d4b3741"
        }
    ],
    "owner": {
        "@odata.type": "#microsoft.graph.user",
        "id": "9617eccf-f0a6-4110-8907-81bfc19e85a2",
        "displayName": "Steve Fred (he/him)"
    }
}
```

### 4. Identify the allotment with the most available licenses for a SKU

Rowan wants to quickly identify the allotment for SKU `SINGULARITY_BUSINESS_SUITE` that has the most licenses available to assign to new users.

```http
GET https://graph.microsoft.com/v1/admin/cloudLicensing/allotments?&$apply=filter(skuId eq be90d47d-3ed9-44bf-8c6a-4b2a3d07125c)/compute(allottedUnits sub consumedUnits as availableUnits)/topcount(1, availableUnits)
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": [
        {
            "id": "2afb23bc-12bb-4e01-ac77-a909d1723756",
            "allottedUnits": 2500,
            "assignableTo": "user,group",
            "catalogId": "ZO93XWY1FXQZ:0001",
            "consumedUnits": 2184,
            "managementScope": "organization",
            "services": [
                {
                    "assignableTo": "user,group",
                    "planId": "55e6ca1f-c33b-452d-b937-7e3543410b1d",
                    "planName": "QUANTUM_ENTANGLED_INBOX"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "6a02f68f-f783-407c-866a-efbc4203b24a",
                    "planName": "CEREBRAL_EMULATOR"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "92e0703e-6eea-4e19-a1e0-9d5e9bffb043",
                    "planName": "SELF_AWARE_VIRTUAL_ASSISTANT_PREMIUM_PLUS"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "a13d48d6-33a7-4e87-8d6d-72ef00a0e7ba",
                    "planName": "QUID_VULPIS_DICIT"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "dd794291-6d32-490e-aa64-6c7bc5e39bdb",
                    "planName": "QUANTUM_ENCRYPTION"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "f1df97e2-b3d9-4c17-b931-30fdbfeb5c18",
                    "planName": "CONSCIOUSNESS_UPLOADER"
                }
            ],
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c",
            "skuPartNumber": "SINGULARITY_BUSINESS_SUITE",
            "subscriptions": [
                {
                    "subscriptionId": "a8d72db0-39ce-485a-97f0-0c6a99929d10",
                    "nextLifecycleDate": "2024-09-05",
                    "startDate": "2023-09-05",
                    "state": "active",
                    "tags": "none"
                }
            ]
        }
    ]
}
```

### 5. Page through assignments

Rowan decides to page through the users and groups that are assigned licenses from the larger of the two `SINGULARITY_BUSINESS_SUITE` allotments, to see how those 2,184 licenses are currently being consumed. They decide to limit the response size to 3 assignments per page.

```http
GET https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2afb23bc-12bb-4e01-ac77-a909d1723756/assignments?$top=3&$expand=assignedTo($select=id,displayName)
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "@odata.nextLink": "https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2afb23bc-12bb-4e01-ac77-a909d1723756/assignments?$top=3&$expand=assignedTo($select=id,displayName)&$skipToken=x6eCRVFnunybXESDcrnuMIUBYtvc5r7x6eCVbnuBnumbytvxc5r7e6CBnu9cd54BTVNUMubyc6rtv8ex645c6rvTBCReCRFTVGBYHJUYHRFTGYHUCRVBNM",
    "value": [
        {
            "id": "a04fd91d-4615-4afc-9f30-0a7237f2406e",
            "assignedTo": {
                "@odata.type": "#microsoft.graph.user",
                "id": "a81b2f7a-31e7-4c41-8278-0a3127e59b3f",
                "displayName": "Eric Mendoza (he/him)"
            },
            "disabledServicePlanIds": [
                "6a02f68f-f783-407c-866a-efbc4203b24a"
            ],
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c"
        },
        {
            "id": "32aec2ba-433c-497e-ba1f-a023a670deb6",
            "assignedTo": {
                "@odata.type": "#microsoft.graph.group",
                "id": "5d093f1b-61c4-42bd-a864-09123eccc430",
                "displayName": "Contoso FTE"
            },
            "disabledServicePlanIds": [],
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c"
        },
        {
            "id": "40ff2716-2c34-441f-a101-c0d0ab78579f",
            "assignedTo": {
                "@odata.type": "#microsoft.graph.user",
                "id": "15414a3a-5bf0-44ca-a5da-9370d9770f26",
                "displayName": "Vi Park (they/them)"
            },
            "disabledServicePlanIds": [],
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c"
        }
    ]
}
```

Rowan can continue to page through the results by performing a series of GETs at the returned link, as with any other Microsoft Graph resource that supports paging.

### 6. Enumerate assigned group members that are waiting for a license

When a security group is assigned licenses from an allotment, the licensing platform monitors group membership changes to give licenses to new members and take away licenses from former members. If the allotment runs out of available licenses, there are no licenses to give to new members. These group members instead end up the allotment's waiting room, where a timestamp indicates how long they've been waiting.

Rowan notices that the allotment for `QUANTUM_TELEPORTER_AUTO_FAILOVER` is consuming all 32 of its licenses. Rowan knows that there are licenses assigned to security groups from this allotment, which could mean that there are new group members who aren't receiving licenses from that assignment. They decide to check the waiting room.

```http
GET https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2b7fc5fe-2267-404e-ada7-32b321f116ee/waitingMembers?$expand=assignedTo($select=id,displayName)
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": [
        {
            "id": "ae7c488e-a0d7-47fd-b5f9-ab31238e5158",
            "assignedTo": {
                "@odata.type": "#microsoft.graph.device",
                "id": "6e92c739-e5c2-4793-9d77-e364689b41c9",
                "displayName": "Steve's laptop"
            },
            "waitingSinceDateTime": "2023-09-27T16:25:59.5108583+00:00"
        },
        {
            "id": "c714e649-c005-4584-bdbc-a08d152b0dd0",
            "assignedTo": {
                "@odata.type": "#microsoft.graph.device",
                "id": "5d093f1b-61c4-42bd-a864-09123eccc430",
                "displayName": "Lab 4 workstation"
            },
            "waitingSinceDateTime": "2023-09-15T16:25:13.1543522+00:00"
        }
    ]
}
```

### 7. Discover asynchronous assignment errors

If something goes wrong with the creation of a license assignment, the Graph API will immediately return an error. As we saw observed in the previous scenario, however, membership changes in an assigned security group continue to produce licensing updates after that assignment is created. Last time, the group grew beyond the size of the allotment. However, there are other types of errors that can impact individual group members. These are the same types of errors that can happen if an assignment were made directly to that individual, but they happen behind the scenes and can occur for new group members long after the group was originally assigned. Admins need to be able to discover these errors as well.

Rowan hears complaints that some members of one of the groups assigned licenses from the allotment for `TIME_TRAVEL_BACKUP_RESTORE` aren't getting access to the benefits conferred by that license. Rowan decides to investigate, starting by confirming that the group has an assignment.

```http
GET https://graph.microsoft.com/v1/groups/d8ee6ba1-2b90-4e77-90e8-3e52a09bc35a/cloudLicensing/assignments?$expand=allotments($select=id,skuId,skuPartNumber;$filter=skuId eq f48db87f-583c-486e-a6de-096155d8fb8f)
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": [
        {
            "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
            "id": "79aaaa02-ab1c-4e01-ad75-25c857a84625",
            "disabledServicePlanIds": [],
            "allotment": {
                "id": "fb879ecd-3aef-4a9e-a227-2e2f988332df",
                "skuId": "f48db87f-583c-486e-a6de-096155d8fb8f",
                "skuPartNumber": "TIME_TRAVEL_BACKUP_RESTORE"
            }
        }
    ]
}
```

The group does have a license. Perhaps these users are in the waiting room? Rowan checks one of the users that filed a complaint.

```http
GET https://graph.microsoft.com/v1/users/f7bcb3b5-57c3-40e3-8075-4e9060a052ab/cloudLicensing/waitingMembers
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": []
}
```

This user isn't in any waiting rooms. Perhaps something went wrong synchronizing their assignment?

```http
GET https://graph.microsoft.com/v1/users/f7bcb3b5-57c3-40e3-8075-4e9060a052ab/cloudLicensing/assignmentErrors
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": [
        {
            "id": "115bedd6-40d2-45c1-9220-a73c2a8f6226",
            "code": "MissingDependency",
            "message": "Service plan 0337d124-4da1-45e4-9b28-936079cc72bb cannot be assigned without service plan f1df97e2-b3d9-4c17-b931-30fdbfeb5c18, which this user does not currently have.",
            "occurrenceDateTime": "2023-09-22T17:11:10.6635939+00:00",
            "skuId": "f48db87f-583c-486e-a6de-096155d8fb8f"
        }
    ]
}
```

Rowan discovers that the users aren't getting access because `TIME_TRAVEL_BACKUP_RESTORE` depends on a service plan from a different SKU, which is not currently enabled for this user. Rowan queries the count of assignment errors for this SKU in order to understand how widespread the problem is.

```http
GET https://graph.microsoft.com/v1/admin/cloudLicensing/assignmentErrors/$count?$filter=skuId eq f48db87f-583c-486e-a6de-096155d8fb8f
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

35
```

Well, that solves it. Rowan needs to make sure the impacted users have another license with the service plan dependency enabled.

### 8. Manage license assignments

A new employee just started today at Contoso, so Rowan needs to assign them a license for `SINGULARITY_BUSINESS_SUITE`.

```http
POST https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2afb23bc-12bb-4e01-ac77-a909d1723756/assignments
Content-Type: application/json

{
    "assignedTo@odata.bind": "https://graph.microsoft.com/v1/users/d6125d65-8a97-4b1d-b5c9-14d799013255",
    "disabledServicePlanIds": []
}
```

```http
HTTP 1.1/201 Created
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
    "id": "4ad445a2-d3be-4824-9b70-56c1ab692a6f",
    "allotment": {
        "@odata.id": "https://graph.microsoft.com/$metadata#licensing.allotments('2afb23bc-12bb-4e01-ac77-a909d1723756')"
    },
    "assignedTo": {
        "@odata.id": "https://graph.microsoft.com/$metadata#users('d6125d65-8a97-4b1d-b5c9-14d799013255')"
    },
    "disabledServicePlanIds": [],
    "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c"
}
```

Later, Rowan realizes they forgot to disable a service plan that the new employee is not supposed to have.

```http
PATCH https://graph.microsoft.com/v1/admin/cloudLicensing/assignments/4ad445a2-d3be-4824-9b70-56c1ab692a6f
Content-Type: application/json

{
    "disabledServicePlanIds": [
        "a13d48d6-33a7-4e87-8d6d-72ef00a0e7ba"
    ]
}
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
    "id": "4ad445a2-d3be-4824-9b70-56c1ab692a6f",
    "allotment": {
        "@odata.id": "https://graph.microsoft.com/$metadata#licensing.allotments('2afb23bc-12bb-4e01-ac77-a909d1723756')"
    },
    "assignedTo": {
        "@odata.id": "https://graph.microsoft.com/$metadata#users('d6125d65-8a97-4b1d-b5c9-14d799013255')"
    },
    "disabledServicePlanIds": [
        "a13d48d6-33a7-4e87-8d6d-72ef00a0e7ba"
    ],
    "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c"
}
```

Unfortunately, the new employee doesn't stay for very long. Rowan has to remove the license after the employee quits to become a teacher.

```http
DELETE https://graph.microsoft.com/v1/admin/cloudLicensing/assignments/4ad445a2-d3be-4824-9b70-56c1ab692a6f
```

```http
HTTP 1.1/204 No Content
```

### 9. Compatibility with the assignLicense action

Some of Contoso's existing scripts rely on an older method of assigning licenses through Microsoft Graph, and updating or replacing all of them isn't a task that will happen overnight. The assignLicense action predates the introduction of allotments, so it references what is being assigned or removed in terms of skuIds rather than allotmentIds. This still works with allotments—behind the scenes, it will create, update, or delete allotment assignments as needed. Anyone not aware of the new functionality can carry on with their current patterns.

Rowan is not the only license admin at Contoso. Their coworker—Teresa—inspects the licenses for Nora, another new hire. Teresa is still using the older ways of doing things—the assignedLicenses property on the user and the assignLicense OData action.

```http
GET https://graph.microsoft.com/v1/users/cd5762b7-9f3e-474f-b28f-dcbfac9ace1c?$select=id,displayName,assignedLicenses&$expand=cloudLicensing/assignments($expand=allotment)
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "id": "cd5762b7-9f3e-474f-b28f-dcbfac9ace1c",
    "displayName": "Nora Shields (she/her)",
    "assignedLicenses": [],
    "assignments": []
}
```

Seeing that Nora has no licenses assigned, Teresa decides to assign a license for `SINGULARITY_BUSINESS_SUITE` via the assignLicense action. (The properties depicted in the assignLicense responses are limited to those from the previous request in this example, for brevity.)

```http
POST https://graph.microsoft.com/v1/users/cd5762b7-9f3e-474f-b28f-dcbfac9ace1c/assignLicense
Content-Type: application/json

{
    "addLicenses": [
        {
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c",
            "disabledServicePlans": [
                "92e0703e-6eea-4e19-a1e0-9d5e9bffb043"
            ]
        }
    ],
    "removeLicenses": []
}
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "id": "cd5762b7-9f3e-474f-b28f-dcbfac9ace1c",
    "displayName": "Nora Shields (she/her)",
    "assignedLicenses": [
        {
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c",
            "disabledServicePlans": [
                "92e0703e-6eea-4e19-a1e0-9d5e9bffb043"
            ]
        }
    ]
}
```

The assignLicense action returns the user or group which was modified; here, Teresa can see the newly assigned license.

Rowan is also aware that Nora is a new employee, but doesn't know whether another License Admin has already set her up. Rowan checks Nora's allotment assignments.

```http
GET https://graph.microsoft.com/v1/users/cd5762b7-9f3e-474f-b28f-dcbfac9ace1c/cloudLicensing/assignments?$expand=allotment($select=id)
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": [
        {
            "id": "55a14aec-8bb1-400d-937b-6efdab784b2d",
            "allotment": {
                "id": "2afb23bc-12bb-4e01-ac77-a909d1723756"
            },
            "disabledServicePlanIds": [
                "92e0703e-6eea-4e19-a1e0-9d5e9bffb043"
            ],
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c"
        }
    ]
}
```

Rowan sees that Nora has one new assignment for one of the allotments associated with skuId `SINGULARITY_BUSINESS_SUITE`, with the set of disabled service plans that Teresa specified.

Later, a third license admin—Ashton—creates another assignment for Nora from the other allotment associated with skuId `SINGULARITY_BUSINESS_SUITE`. This assignment disables a different service plan. Rowan and Teresa hear that Nora has unexpected access to features granted by the `SELF_AWARE_VIRTUAL_ASSISTANT_PREMIUM_PLUS` (`92e0703e-6eea-4e19-a1e0-9d5e9bffb043`) plan, so they retrieve her license information again to investigate.

```http
GET https://graph.microsoft.com/v1/users/cd5762b7-9f3e-474f-b28f-dcbfac9ace1c?$select=id,displayName,assignedLicenses&$expand=cloudLicensing/assignments($expand=allotment($select=id))
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "id": "cd5762b7-9f3e-474f-b28f-dcbfac9ace1c",
    "displayName": "Nora Shields (she/her)",
    "assignedLicenses": [
        {
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c",
            "disabledPlans": []
        }
    ],
    "assignments": [
        {
            "id": "55a14aec-8bb1-400d-937b-6efdab784b2d",
            "allotment": {
                "id": "2afb23bc-12bb-4e01-ac77-a909d1723756"
            },
            "disabledServicePlanIds": [
                "92e0703e-6eea-4e19-a1e0-9d5e9bffb043"
            ],
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c"
        },
        {
            "id": "c1e420bd-ee38-4753-9b6b-8fd569906fd0",
            "allotment": {
                "id": "58b28998-1ca2-4f65-924c-902812d25692"
            },
            "disabledServicePlanIds": [],
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c"
        }
    ]
}
```

The pair aren't sure why another license admin created a new assignment for Nora, but they'll sort that out later. The second assignment doesn't disable the same service plan as the first, so Nora has unintended access. Teresa invokes assignLicense again, which now updates both assignments.

```http
POST https://graph.microsoft.com/v1/users/cd5762b7-9f3e-474f-b28f-dcbfac9ace1c/assignLicenses
Content-Type: application/json

{
    "addLicenses": [
        {
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c",
            "disabledPlans": [
                "92e0703e-6eea-4e19-a1e0-9d5e9bffb043"
            ]
        }
    ],
    "removeLicenses": []
}
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "id": "cd5762b7-9f3e-474f-b28f-dcbfac9ace1c",
    "displayName": "Nora Shields (she/her)",
    "assignedLicenses": [
        {
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c",
            "disabledPlans": [
                "92e0703e-6eea-4e19-a1e0-9d5e9bffb043"
            ]
        }
    ]
}
```

Now when Rowan gets Nora's assignments, they see the same disabledServicePlanIds array on both.

```http
GET https://graph.microsoft.com/v1/users/cd5762b7-9f3e-474f-b28f-dcbfac9ace1c/cloudLicensing/assignments
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": [
        {
            "id": "55a14aec-8bb1-400d-937b-6efdab784b2d",
            "disabledServicePlanIds": [
                "92e0703e-6eea-4e19-a1e0-9d5e9bffb043"
            ],
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c"
        },
        {
            "id": "c1e420bd-ee38-4753-9b6b-8fd569906fd0",
            "disabledServicePlanIds": [
                "92e0703e-6eea-4e19-a1e0-9d5e9bffb043"
            ],
            "skuId": "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c"
        }
    ]
}
```

Eventually, Nora transfers to another role at the company. She no longer needs a license for skuId `SINGULARITY_BUSINESS_SUITE`, so Teresa invokes assignLicense one final time. Similar to when she used it to update existing license assignments, this removes all of Nora's assignments for this SKU.

```http
POST https://graph.microsoft.com/v1/users/cd5762b7-9f3e-474f-b28f-dcbfac9ace1c/assignLicenses
Content-Type: application/json

{
    "addLicenses": [],
    "removeLicenses": [
        "be90d47d-3ed9-44bf-8c6a-4b2a3d07125c"
    ]
}
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "id": "cd5762b7-9f3e-474f-b28f-dcbfac9ace1c",
    "displayName": "Nora Shields (she/her)",
    "assignedLicenses": []
}
```

Rowan checks Nora's assignments again, revealing that they're both gone.

```http
GET https://graph.microsoft.com/v1/users/cd5762b7-9f3e-474f-b28f-dcbfac9ace1c/cloudLicensing/assignments
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": []
}
```

(Rowan and the other license admins agree to coordinate their efforts better in the future.)

### 10. Distinguish between allotments by their subscription information

Petra is working on an application aimed at license admins to help them with their license management. It is specifically targeted at large customers who may own multiple different subscriptions for the same SKU. Because assignments are associated with specific allotments, which are themselves associated with specific subscriptions, the user experience for her application must help the admin to distinguish between their allotments from different subscriptions so that they can select the right one when creating a new assignment. Customers may have multiple subscriptions of the same SKU for any number of reasons, many of which are related to budgeting. For example, they may have one subscription per subsidiary, per department, or per branch office.

Petra is implementing an allotment picker component for the user interface. At this point in the workflow, the admin will have already selected the SKU they're going to assign and the user, group, or device to whom they're going to assign it. She has her code make a request to get the required information to render the picker.

```http
GET https://graph.microsoft.com/v1/admin/cloudLicensing/allotments?$select=id,allottedUnits,consumedUnits,subscriptions&$expand=allotments($select=id,skuId;$filter=skuId eq d03872db-ff33-4e8b-8f34-d55bfe1e5871)
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": [
        {
            "id": "c316c724-7af7-465b-ad08-a34602231571",
            "allottedUnits": 50,
            "consumedUnits": 17,
            "subscription": {
                "nextLifecycleDate": "2024-07-01",
                "startDate": "2023-07-01",
                "state": "active",
                "tags": "none"
            },
            "allotment": {
                "id": "c316c724-7af7-465b-ad08-a34602231571",
                "skuId": "d03872db-ff33-4e8b-8f34-d55bfe1e5871"
            }
        },
        {
            "id": "a76c5ebc-95ad-42e0-b59c-33a489526b83",
            "allottedUnits": 7,
            "consumedUnits": 3,
            "subscription": {
                "nextLifecycleDate": "2024-10-01",
                "startDate": "2023-10-01",
                "state": "active",
                "tags": "none"
            },
            "allotment": {
                "id": "3c495d1b-b7af-4fa8-a655-23da4aa9975a",
                "skuId": "d03872db-ff33-4e8b-8f34-d55bfe1e5871"
            }
        },
        {
            "id": "f8484ead-dc74-40f1-b630-6f35ea62f919",
            "allottedUnits": 42,
            "consumedUnits": 23,
            "subscription": {
                "nextLifecycleDate": "2024-05-01",
                "startDate": "2023-04-01",
                "state": "warning",
                "tags": "none"
            },
            "allotment": {
                "id": "5ac22a53-7f6d-4379-a8ab-bd75a43dde4e",
                "skuId": "d03872db-ff33-4e8b-8f34-d55bfe1e5871"
            }
        }
    ]
}
```

### 11. Check usage rights from a client application

Nasim needs her code to determine whether the user currently signed in to Fabrikam's client application has any usage rights which might be relevant to Fabrikam services.

```http
GET https://graph.microsoft.com/v1/me/cloudLicensing/usageRights
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": [
        {
            "id": "7e452304-0a58-40d6-8fd2-2afe92d26a3a",
            "services": [
                {
                    "assignableTo": "user,device,group",
                    "planId": "f08373fb-2530-4f97-8aa4-f424f071780d",
                    "planName": "FABRIKAM_TASKS"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "3e315338-9379-453d-ac8f-c75f57ac78a1",
                    "planName": "FABRIKAM_CHAT"
                },
                {
                    "assignableTo": "user,device,group",
                    "planId": "b7786c33-f595-4df5-bed7-9a2c8622df78",
                    "planName": "FABRIKAM_DESKTOP"
                },
                {
                    "assignableTo": "user,device,group",
                    "planId": "f446866a-4b4c-492e-907a-998b3fde5a81",
                    "planName": "FABRIKAM_REMOTE"
                }
            ],
            "skuId": "d3ddfd0c-8902-4682-9dbd-5ce4b50da29c",
            "skuPartNumber": "FABRIKAM_USER"
        }
    ]
}
```

### 12. View a device's usage rights

Nasim's code also needs to check whether the device itself has any usage rights which might be relevant to Fabrikam services. Nasim also decides to filter the results to a particular SKU of interest.

```http
GET https://graph.microsoft.com/v1/devices/0231bf6c-f5ba-4133-80dd-b35d619bb4b5/cloudLicensing/usageRights?$filter=skuId eq a0cfb9b5-427c-4d42-9e6d-6727c6bbd8b5
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": [
        {
            "id": "a8d33537-2833-4f1c-8797-7aa891e15723",
            "services": [
                {
                    "assignableTo": "user,device,group",
                    "planId": "b7786c33-f595-4df5-bed7-9a2c8622df78",
                    "planName": "FABRIKAM_DESKTOP"
                },
                {
                    "assignableTo": "user,device,group",
                    "planId": "f446866a-4b4c-492e-907a-998b3fde5a81",
                    "planName": "FABRIKAM_REMOTE"
                },
                {
                    "assignableTo": "user,device,group",
                    "planId": "f08373fb-2530-4f97-8aa4-f424f071780d",
                    "planName": "FABRIKAM_TASKS"
                }
            ],
            "skuId": "a0cfb9b5-427c-4d42-9e6d-6727c6bbd8b5",
            "skuPartNumber": "FABRIKAM_DEVICE"
        }
    ]
}
```

### 13. Filter usage rights on multiple service plans

As Nasim's work progresses, she realizes that her employer sells multiple SKUs that relate to the application she's working on. It's also available in multiple tiers, each with its own service plan.

She rewrites her code to look for usage rights that grant any of the service plans that she cares about.

```http
GET https://graph.microsoft.com/v1/me/cloudLicensing/usageRights?$filter=services/any(c:c/planId in (b7786c33-f595-4df5-bed7-9a2c8622df78, 189acccd-b5a4-4058-952f-61646d6b5cc1))
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": [
        {
            "id": "7e452304-0a58-40d6-8fd2-2afe92d26a3a",
            "services": [
                {
                    "assignableTo": "user,device,group",
                    "planId": "f08373fb-2530-4f97-8aa4-f424f071780d",
                    "planName": "FABRIKAM_TASKS"
                },
                {
                    "assignableTo": "user,group",
                    "planId": "3e315338-9379-453d-ac8f-c75f57ac78a1",
                    "planName": "FABRIKAM_CHAT"
                },
                {
                    "assignableTo": "user,device,group",
                    "planId": "b7786c33-f595-4df5-bed7-9a2c8622df78",
                    "planName": "FABRIKAM_DESKTOP"
                }
            ],
            "skuId": "d3ddfd0c-8902-4682-9dbd-5ce4b50da29c",
            "skuPartNumber": "FABRIKAM_USER"
        },
        {
            "id": "94d0b585-94b7-4832-a234-745ce5a91652",
            "services": [
                {
                    "assignableTo": "user",
                    "planId": "189acccd-b5a4-4058-952f-61646d6b5cc1",
                    "planName": "FABRIKAM_DESKTOP_LITE"
                },
                {
                    "assignableTo": "user",
                    "planId": "d7db3eb8-aebe-4a79-b0ea-8d81014344c1",
                    "planName": "FABRIKAM_TASKS_LITE"
                }
            ],
            "skuId": "b5d43cfa-2d3f-44b8-a44c-bfca7c3c4210",
            "skuPartNumber": "FABRIKAM_TRIAL"
        }
    ]
}
```

### 14. Investigate the origin of a usage right

Nasim has been asked to add a new feature which shows the user where their usage rights are coming from, to help them investigate unexpected access issues without needing to engage customer support. She decides to write code to include detailed information about the assignments that contribute to a usage right.

```http
GET https://graph.microsoft.com/v1/me/cloudLicensing/usageRights/7e452304-0a58-40d6-8fd2-2afe92d26a3a?$expand=assignments($expand=allotment($select=id),assignedTo($select=id,displayName))
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "id": "7e452304-0a58-40d6-8fd2-2afe92d26a3a",
    "assignments": [
        {
            "id": "1efadc7b-e5b3-48c8-98c3-bb8fb6920e4e",
            "allotment": {
                "id": "d0f17302-135a-4f5d-bce3-eaa3457da64c"
            },
            "assignedTo": {
                "@odata.type": "#microsoft.graph.user",
                "id": "794eed17-2f50-49b9-a20d-8f7253e715ef",
                "displayName": "Nasim Arya (she/her)"
            },
            "disabledServicePlanIds": [
                "f446866a-4b4c-492e-907a-998b3fde5a81"
            ],
            "skuId": "d3ddfd0c-8902-4682-9dbd-5ce4b50da29c"
        },
        {
            "id": "32aec2ba-433c-497e-ba1f-a023a670deb6",
            "allotment": {
                "id": "616b0d70-752c-4720-9e14-a3603362f962"
            },
            "assignedTo": {
                "@odata.type": "#microsoft.graph.group",
                "id": "5d093f1b-61c4-42bd-a864-09123eccc430",
                "displayName": "Nasim's Test Group"
            },
            "disabledServicePlanIds": [
                "3e315338-9379-453d-ac8f-c75f57ac78a1",
                "f446866a-4b4c-492e-907a-998b3fde5a81"
            ],
            "skuId": "d3ddfd0c-8902-4682-9dbd-5ce4b50da29c"
        }
    ],
    "services": [
        {
            "assignableTo": "user,device,group",
            "planId": "f08373fb-2530-4f97-8aa4-f424f071780d",
            "planName": "FABRIKAM_TASKS"
        },
        {
            "assignableTo": "user,device,group",
            "planId": "3e315338-9379-453d-ac8f-c75f57ac78a1",
            "planName": "FABRIKAM_CHAT"
        },
        {
            "assignableTo": "user,device,group",
            "planId": "b7786c33-f595-4df5-bed7-9a2c8622df78",
            "planName": "FABRIKAM_DESKTOP"
        }
    ],
    "skuId": "d3ddfd0c-8902-4682-9dbd-5ce4b50da29c",
    "skuPartNumber": "FABRIKAM_USER"
}
```

Nasim is receiving a license from two different allotments, one via direct assignment and one via group assignment. Because `FABRIKAM_REMOTE`—the service plan with id `"f446866a-4b4c-492e-907a-998b3fde5a81"`—is disabled in both assignments, it is not included in Nasim's usageRight. `FABRIKAM_CHAT`—the service plan with id `"3e315338-9379-453d-ac8f-c75f57ac78a1"`—is included in Nasim's usageRight, despite being disabled in one of the assignments, because it is enabled by the other assignment.

### 15. Provide messaging based on the state of the subscription backing the user's license

Nasim's employer wants their client application to provide alerts and reminders to users based on the condition of the subscription that is the source of their license. They should be directed to purchase a full license if they currently only have access due to a free trial, and they should be warned if their license is expired or expiring soon. The implementation is similar to previous scenarios, but now she's more interested in the subscription information of the allotments than anything else about how they're assigned or to whom.

Nasim tests the same request with two different user accounts.

```http
GET https://graph.microsoft.com/v1/me/cloudLicensing/usageRights?$filter=services/any(c:c/planId in (b7786c33-f595-4df5-bed7-9a2c8622df78, 189acccd-b5a4-4058-952f-61646d6b5cc1))&$expand=assignments($select=id;$expand=allotment($select=subscriptions))
```

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": [
        {
            "id": "458f6e4d-b7b9-4e2c-81b1-942f52e5db46",
            "assignments": [
                {
                    "allotment": {
                        "subscriptions": [
                            {
                                "subscriptionId": "d4cba4df-3ae9-4dbb-8395-8300c91ca5db",
                                "nextLifecycleDate": "2024-05-15",
                                "startDate": "2024-02-15",
                                "state": "active"
                            }
                        ]
                    },
                    "id": "17aeb310-3d11-4e83-a716-9c494041a983"
                }
            ],
            "services": [
                {
                    "assignableTo": "user",
                    "planId": "189acccd-b5a4-4058-952f-61646d6b5cc1",
                    "planName": "FABRIKAM_DESKTOP_LITE"
                }
            ],
            "skuId": "b5d43cfa-2d3f-44b8-a44c-bfca7c3c4210",
            "skuPartNumber": "FABRIKAM_TRIAL"
        }
    ]
}
```

The first user has a trial license, so her code will render the upgrade message.

```http
HTTP 1.1/200 OK
Content-Type: application/json

{
    "value": [
        {
            "id": "89ef03f5-b1d1-48fb-bbae-063eb35a788f",
            "assignments": [
                {
                    "allotment": {
                        "subscriptions": [
                            {
                                "subscriptionId": "4c12d43b-dd0e-4761-bdd0-9450f0622975",
                                "nextLifecycleDate": "2024-05-01",
                                "startDate": "2023-04-01",
                                "state": "warning"
                            }
                        ]
                    },
                    "id": "ecd716cd-40f6-4cfb-9dea-a4331d81732c"
                }
            ],
            "services": [
                {
                    "assignableTo": "user,device,group",
                    "planId": "b7786c33-f595-4df5-bed7-9a2c8622df78",
                    "planName": "FABRIKAM_DESKTOP"
                }
            ],
            "skuId": "d3ddfd0c-8902-4682-9dbd-5ce4b50da29c",
            "skuPartNumber": "FABRIKAM_USER"
        }
    ]
}
```

The second user's subscription is in the grace period that typically follows expiration, so her code will render the renewal warning.

## Design details

### Allotments

It was important to us to have some way of breaking up the existing SKU-level license pool in a meaningful way. There are S500 customers that place a high value on the ability to place firm boundaries between the licenses available to their different divisions, for accounting and other reasons. This is, essentially, where the allotment concept originated. Allotments are initially provisioned 1:1 with their backing subscriptions, but we have an allotment entity instead of a subscription entity so that we can maintain some separation between the licenses and the commerce artifacts that produce them. This flexibility gives us room to grow and innovate.

These independently managed pools called allotments also provided an opportunity to solve another problem—the strict requirement of central purchasing and license management for all tenants. If there is no division between my licenses and your licenses, they aren't really mine or yours. It doesn't make sense to sell software to an individual within an organization if they have no control over how it gets used after the fact. With allotments already providing a way to separate my licenses from your licenses, we were also able to introduce the concept of management scopes—an allotment and its licenses can belong to the whole organization or a single individual within the organization. Microsoft to sell "departmental purchase" SKUs to non-admin users, and enables them to manage said licenses after the fact like a mini license admin.

In the future, we intend to build on these features further with a pair of complementary features—subscription splitting and delegated management. We will allow customers to split an individual subscription into multiple allotments, and we will allow allotment owners (typically organization admins) to delegate license management capabilities for specific allotments to the non-admin users of their choosing.

Decoupling allotments from their backing subscriptions also enables allotments to be created for licensed product-SKUs that are not provisioned in the directory and/or that come from multiple distinct commerce systems. This allows independent software vendors to partner with Microsoft to use our license management platform for their products. Third-party licenses are not provisioned in the directory, but they do create allotments. Third-party licenses can also be provisioned through two distinct subscription registry systems, depending on whether Microsoft is involved in the actual transaction.

#### Data aggregation

While the division into allotments is important to our platform, there is still value in having aggregated summary views of the various allotments for a single product. Existing user experiences for admin license management tend to speak in terms of SKUs before subscriptions. There are numerous questions an admin might want to answer that require aggregating data across multiple allotments that have common properties. How many licenses do they have in total for a particular SKU? How many of those are being consumed? Which subscription for this SKU has the most licenses available to assign? Which allotment comes from the oldest subscription? And so on and so forth.

This is just the sort of thing that the [OData Extension for Data Aggregation Version 4.0](https://docs.oasis-open.org/odata/odata-data-aggregation-ext/v4.0/odata-data-aggregation-ext-v4.0.html) was designed for, so that is the pattern we chose to support.

### Assignments

Even if we hadn't decoupled allotments from the subscriptions that are provisioned into the directory, their introduction still adds another dimension to the ways that a single user can receive a license for a single SKU. Initially, a user could only be assigned a license directly. When Group-Based Licensing was released, users could now also receive a license for the same SKU indirectly through membership in one or more assigned groups. Now, with allotments, there is the added detail of which allotment the assignment is coming from. The same user or group can be assigned a license for the same SKU from multiple different allotments. Just as with the direct or group-based assignments, we also needed to know which service plans were disabled for each one of those assignments so that we can calculate the right set of disabled service plans. On top of that, we also wanted to enable device-based licensing—something the directory does not support. It became clear that we needed to add new entities to describe these assignments in the world of allotments.

The properties of an assignment are essentially the same as the properties that would be provided to the traditional assignLicense action, save that an allotment must be identified instead of a SKU. If we already have these new assignment entities as a way to visualize the assignment paths for an end-user (or device), then it's only natural that these entities would be created and modified directly instead of through a separate action.

### Waiting rooms

With any form of group-based licensing, it is possible for the group to grow to exceed the number of available licenses in some pool to which it is assigned. In the SKU-based licensing model, that meant that new members would eventually be unable to receive licenses for a particular SKU. As with assignments, this becomes more complex with the introduction of allotments. Suppose Allotments A and B contain licenses for the same SKU—Allotment A may be out of licenses while Allotment B is not. If a user is a member of a group that is assigned licenses from Allotment A and another group that is assigned licenses from Allotment B, they may get the license from Allotment B but not the license from Allotment A. It is no longer sufficient to say whether or not they're waiting for a license for the SKU; it also needs to be clear which allotments they're waiting for. Enter the waiting room concept.

When an allotment is out of available licenses, new group members are added to its waiting room. This addition is represented by a simple entity with navigation properties to the allotment and the user (or device) and a timestamp property that indicates how long the member has been waiting. This timestamp is needed for the waiting room to behave in a First-In, First-Out manner; FIFO is more predictable and understandable to customers than other deterministic approaches that don't require a timestamp, such as sorting them by objectId. Technically, we could still achieve this without the timestamp, but it helps admins to visualize the ordering of the queue and the severity of the problem facing users waiting for a license.

### Compatibility

While there is obviously a desire to move all customers and dependent software (management portals, for example), that will be a slow process—the existing paradigm is firmly entrenched. As such, we'll need to smooth that transition as much as we can. That means that, as much as possible, requests to read licensing data should continue to return it and requests to assign licenses should continue to assign them. We can't cover everything, but we can cover what we believe to be the highest priorities.

The way to assign licenses today is through the assignLicense action, where licenses for SKUs are assigned to users or groups. For customers with allotments, that action will be redirected to our implementation. (That work has already been done.) We interpret these requests in a way that best honors the admin's intent and expectations, preserving the idempotency of the action. If a skuId is in the addLicenses list and no assignment currently exists for this SKU for the target entity, we create a new assignment from an organization-scoped allotment for the same SKU with available licenses. If a skuId is in the addLicenses list and one or more applicable assignments to that entity currently exist, we will update the disabledServicePlanIds list on all of the existing assignments to match the one in the request. If a skuId is in the removeLicenses list, we will remove all assignments for that SKU from the target entity.

Note that assignLicense does not work and has never worked for departmental purchase SKUs, with or without this redirection. (Technically it does, but only for a very small list of privileged first party applications. Clients must go through our licensing services to assign licenses for these SKUs, and they must always act in terms of allotments.)

Today, license assignments are primarily through the user and group entities. There are complex type properties on these entities which list everything that is assigned. To ensure that this information is still populated, creating direct user assignment entities will result in an internal assignLicense invocation. Asynchronous membership syncs for group assignments happen in the background, but those will also result in internal assignLicense invocations to write to the user entity.

What's lost, unfortunately, are some of the more recent additions to the API surface related to Group-Based Licensing. It will no longer be possible to distinguish between direct and group-based assignments using existing user entity properties. We don't have a mechanism to update this data directly, and it would be missing the allotment dimension anyway. Errors encountered during asynchronous group membership syncs will also be represented differently. Unlike the basic license checks and license assignment actions, we believe usage of this information is more niche—especially outside of Microsoft's own first-party admin portal experiences, where we have more influence.

It should be noted that all of this only applies to SKUs which are provisioned in the directory. Other SKUs, including all third-party products, have no history here and cannot be translated to skuIds that work elsewhere in Graph.

### Asynchronous assignment errors

Our background processing of group membership changes ultimately results in an internal assignLicense call, which returns errors synchronously to the worker process. As previously mentioned, we don't have a mechanism to update metadata like errors on the user; that means we need to persist these errors and surface them elsewhere. We have introduced an assignmentError entity for just this purpose.

An assignmentError instance is the result of an assignLicense call for a specific combination of user and SKU. As such, we must support enumerating errors by user or by SKU. We have a bidirectional relationship between user and assignmentErrors, so that the user can be identified from the error and the errors can be enumerated from the user. The skuId property is also filterable, so that one can easily query the set of errors (and expand their users, if applicable) for a particular SKU.

### Entity relationships

Different admin user interfaces have different perspectives on what the focal point should be when managing licenses, so we sought to support it from both directions. The allotments entity set is the primary commerce-focused entry point, though the allotments, assignments, and assignmentErrors entity sets can be filtered by skuId to explore from a product-first perspective. The identity-first perspective is facilitated by the addition of new navigation properties from the user, device, and group entity types to some of the new licensing entities.

### Usage rights

The usageRight entity is designed with a tight focus on the client/workload license check scenario, so its relationships only flow in one direction—from the user, group, or device to the usageRight, and from the usageRight to the assignments that combined to form it. Whereas an assignment represents a link between a specific allotment and a specific directory object, many different assignments could be granting access to the same user or device. They could have assignments from multiple different allotments, or perhaps they could be members of various groups that are assigned, or some combination thereof. The usageRight represents the convergence of the various assignment paths, both direct and inherited via group membership.

### Resource diagrams

#### Management-focused

![An entity-relationship diagram showing the relationships between the new entities and existing directory objects, with the exclusion of usageRights.](MclERDiagram_admin.png)

#### Application-focused

![An entity-relationship diagram which is specifically focused on the scenarios supported by the usageRight entity type, excluding unrelated relationships.](MclERDiagram_client.png)

## Error conditions and messages

### Assignment: Mutually Exclusive Service Plan Conflict

During a license assignment, the assigner may encounter an issue where a user, group, or device may already be assigned a service plan that is mutually exclusive with a service plan that is being assigned.

```http
POST https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2afb23bc-12bb-4e01-ac77-a909d1723756/assignments
Content-Type: application/json

{
    "assignedTo@odata.bind": "https://graph.microsoft.com/v1/users/d6125d65-8a97-4b1d-b5c9-14d799013255",
    "disabledServicePlanIds": []
}
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "License assignment failed because service plans 4fa4026d-ce74-4962-a151-8e96d57ea8e4,57ff2da0-773e-42df-b2af-ffb7a2317929 are mutually exclusive",
    "innerError": {
      "code": "mutuallyExclusiveServicePlans",
      "ids": [
        "4fa4026d-ce74-4962-a151-8e96d57ea8e4",
        "57ff2da0-773e-42df-b2af-ffb7a2317929"
      ]
    }
  }
}
```

### Assignment: Proxy Address Conflict

During a license assignment, the assigner may encounter an issue where a user, group, or device does not have an assigned service plan that is required for the assignment to complete successfully.

```http
POST https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2afb23bc-12bb-4e01-ac77-a909d1723756/assignments
Content-Type: application/json

{
    "assignedTo@odata.bind": "https://graph.microsoft.com/v1/users/d6125d65-8a97-4b1d-b5c9-14d799013255",
    "disabledServicePlanIds": []
}
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "Another object with the same value for property proxyAddresses already exists.",
    "innerError": {
      "code": "proxyAddressConflict"
    }
  }
}
```

### Assignment: There are no licenses available in this allotment

During license assignment, the assigner may encounter an issue where the allotment does not have enough seats available to complete the assignment.

```http
POST https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2afb23bc-12bb-4e01-ac77-a909d1723756/assignments
Content-Type: application/json

{
    "assignedTo@odata.bind": "https://graph.microsoft.com/v1/users/d6125d65-8a97-4b1d-b5c9-14d799013255",
    "disabledServicePlanIds": []
}
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "There are no available licenses for the specified allotment",
    "innerError": {
      "code": "noAvailableLicenses"
    }
  }
}
```

### Assignment: The user/group/device being assigned to cannot be found

During license assignment, if the assignee is unable to be found, the assigner will receive an error.

```http
POST https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2afb23bc-12bb-4e01-ac77-a909d1723756/assignments
Content-Type: application/json

{
    "assignedTo@odata.bind": "https://graph.microsoft.com/v1/device/2d566639-ce9c-4b0d-bef2-c1626f32279a",
    "disabledServicePlanIds": []
}
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "Cannot process request because a referenced item was not found.",
    "target": "body",
    "innerError": {
      "code": "notFound",
      "propertyName": "assignedTo"
    }
  }
}
```

### Assignment: The user/group/device does not have a usage location set

During license assignment, if the assignee does not have a usage location set, the assigner will receive an error.

```http
POST https://graph.microsoft.com/v1/assignments
Content-Type: application/json

{
    "allotment@odata.bind": "https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2a6677c7-26a7-42eb-bcef-c00f7462ddbe",
    "assignedTo@odata.bind": "https://graph.microsoft.com/v1/users/cd5762b7-9f3e-474f-b28f-dcbfac9ace1c",
    "disabledServicePlanIds": []
}
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "Cannot process request because a referenced item has an invalid usage location.",
    "target": "query",
    "innerError": {
      "code": "invalidUsageLocation"
    }
  }
}
```

### Assignment: The assignee does not have permissions to assign to specified allotment

During license assignment, if the assigner does not have permissions to assign to the specified allotment, they will receive an error.

```http
POST https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2afb23bc-12bb-4e01-ac77-a909d1723756/assignments
Content-Type: application/json

{
    "assignedTo@odata.bind": "https://graph.microsoft.com/v1/users/d6125d65-8a97-4b1d-b5c9-14d799013255",
    "disabledServicePlanIds": []
}
```

```http
HTTP 1.1/403 Forbidden
Content-Type: application/json

{
  "error": {
    "code": "forbidden",
    "message": "Cannot process request because the user does not have required permissions for referenced allotment.",
    "innerError": {
      "code": "missingRequiredPermission"
    }
  }
}
```

### Assignment: No allotment specified

When an administrator tries to add an assignment for a user, group, or device, the allotment id must be specified. If it is not, the administrator will receive an error.

```http
POST https://graph.microsoft.com/v1/devices/8c057bd7-7560-4e18-b9db-4689efdff6c9/assignments
Content-Type: application/json

{
    "disabledServicePlanIds": []
}
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "Cannot process the request because it is malformed or incorrect.",
    "target": "body",
    "innerError": {
      "code": "requiredFieldOrParameterMissing",
      "propertyName": "allotment"
    }
  }
}
```

### Assignment: No assignee specified

During license assignment, if the assigner does not specify who the assignment is for they will receive an error.

```http
POST https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2afb23bc-12bb-4e01-ac77-a909d1723756/assignments
Content-Type: application/json

{
    "disabledServicePlanIds": []
}
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "Cannot process the request because it is malformed or incorrect.",
    "target": "body",
    "innerError": {
      "code": "requiredFieldOrParameterMissing",
      "propertyName": "assignedTo"
    }
  }
}
```

### Assignment: Assignee does not have permissions to assign this type of entity

During license assignment, if the assigner does not have permissions to assign to the specified allotment, they will receive an error.

```http
POST https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2fceab6d-6f06-486f-888c-f1d656b5c895/assignments
Content-Type: application/json

{
    "assignedTo@odata.bind": "https://graph.microsoft.com/v1/group/d28de39f-5db3-4594-b722-5133094d35bc",
    "disabledServicePlanIds": []
}
```

```http
HTTP 1.1/403 Forbidden
Content-Type: application/json

{
  "error": {
    "code": "forbidden",
    "message": "Cannot process request because the user does not have required permissions to assign to allotment.",
    "innerError": {
      "code": "allotmentPermissions"
    }
  }
}
```

### Assignment: Disabled service plans array not specified

During license assignment, if the assigner does not specify the list of disabled service plans they will receive an error.

```http
POST https://graph.microsoft.com/v1/assignments
Content-Type: application/json

{
    "allotment@odata.bind": "https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2a6677c7-26a7-42eb-bcef-c00f7462ddbe",
    "assignedTo@odata.bind": "https://graph.microsoft.com/v1/users/cd5762b7-9f3e-474f-b28f-dcbfac9ace1c"
}
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "Cannot process the request because it is malformed or incorrect.",
    "target": "body",
    "innerError": {
      "code": "requiredFieldOrParameterMissing",
      "propertyName": "disabledServicePlanIds"
    }
  }
}
```

### Assignment: Disabled service plans array contains invalid service plan

During license assignment, if the assigner specifies a disabled service plan that is not part of the assigned sku they will receive an error.

```http
POST https://graph.microsoft.com/v1/assignments
Content-Type: application/json

{
    "allotment@odata.bind": "https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2a6677c7-26a7-42eb-bcef-c00f7462ddbe",
    "assignedTo@odata.bind": "https://graph.microsoft.com/v1/users/cd5762b7-9f3e-474f-b28f-dcbfac9ace1c",
    "disabledServicePlanIds": [
        "92e0703e-6eea-4e19-a1e0-9d5e9bffb043",
        "dd794291-6d32-490e-aa64-6c7bc5e39bdb"
    ]
}
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "Cannot process request because a referenced item does not exist or is not associated with the request.",
    "target": "body",
    "innerError": {
      "code": "notFound",
      "propertyName": "disabledServicePlanIds[1]"
    }
  }
}
```

### Assignment: The allotment cannot be assigned to this type of entity

During license assignment, if the assigner tries to assign an assignee of the wrong type to the allotment they will receive an error.

Allotments can have restricted assignment types to be one or more of the following: `user`, `group`, `device`.

```http
POST https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2afb23bc-12bb-4e01-ac77-a909d1723756/assignments
Content-Type: application/json

{
    "assignedTo@odata.bind": "https://graph.microsoft.com/v1/device/2d566639-ce9c-4b0d-bef2-c1626f32279a",
    "disabledServicePlanIds": []
}
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "Cannot process the request because the allotment does not support assignee type.",
    "innerError": {
      "code": "invalidAssigneeType",
      "propertyName": "assignedTo"
    }
  }
}
```

### Assignment: The assignment assignee cannot be changed

When an administrator tries to patch an assignment to update the assignee, they will receive an error.

```http
PATCH https://graph.microsoft.com/v1/admin/cloudLicensing/assignments/4ad445a2-d3be-4824-9b70-56c1ab692a6f
Content-Type: application/json

{
    "assignedTo@odata.bind": "https://graph.microsoft.com/v1/device/2d566639-ce9c-4b0d-bef2-c1626f32279a",
    "disabledServicePlanIds": []
}
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "Cannot process the request because an immutable property was modified.",
    "innerError": {
      "code": "immutablePropertyModified",
      "propertyName": "assignedTo"
    }
  }
}
```

### Assignment: The assignment allotment cannot be changed

When an administrator tries to patch an assignment to update the allotment, they will receive an error.

```http
PATCH https://graph.microsoft.com/v1/admin/cloudLicensing/assignments/4ad445a2-d3be-4824-9b70-56c1ab692a6f
Content-Type: application/json

{
    "allotment": "https://graph.microsoft.com/$metadata#licensing.allotments('2afb23bc-12bb-4e01-ac77-a909d1723756')"
}
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "Cannot process the request because an immutable property was modified.",
    "innerError": {
      "code": "immutablePropertyModified",
      "propertyName": "allotment"
    }
  }
}
```

### General: Some Resource in the Path does not exist

If an api is called with an unknown or invalid resource in the path, the caller will receive an error.

```http
GET https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/7f536d7a-46ec-4452-92ca-2ed1504941b0/assignments
Content-Type: application/json
```

```http
HTTP 1.1/404 NotFound
Content-Type: application/json

{
  "error": {
    "code": "notFound",
    "message": "Resource '7f536d7a-46ec-4452-92ca-2ed1504941b0' not found",
    "innerError": {
      "code": "resourceNotFound",
      "propertyName": "allotmentId"
    }
  }
}
```

### General: Method Not Allowed

If an api is called using the wrong HTTP method, the caller will receive an error.

```http
DELETE https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2afb23bc-12bb-4e01-ac77-a909d1723756/assignments
Content-Type: application/json
```

```http
HTTP 1.1/405 MethodNotAllowed
Content-Type: application/json

{
  "error": {
    "code": "methodNotAllowed",
    "message": "Resource '2afb23bc-12bb-4e01-ac77-a909d1723756' does not support deletion",
    "innerError": {
    }
  }
}
```

### General: Invalid Query Parameters: Can't filter on X

If an api call is made using a filter that is an unsupported or invalid property, the caller will receive an error.

```http
GET https://graph.microsoft.com/v1/v1/users/4f7e78ea-75cf-428a-a364-d39f0aca329f/cloudLicensing/assignments?$filter=allotmentId eq 'e7d7d7cb-50c6-4649-bfaf-effaf2e25476'
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "Cannot process the request because it is malformed or incorrect.",
    "target": "query",
    "innerError": {
      "code": "invalidFilter",
      "propertyName": "allotmentId"
    }
  }
}
```

### General: Invalid Query Parameters: Can't expand Y

If an api call is made using an expansion that is unsupported or invalid, the caller will receive an error.

```http
GET https://graph.microsoft.com/v1/me/usageRights/7e452304-0a58-40d6-8fd2-2afe92d26a3a/assignments?$expand=flags($select=id)
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "Cannot process the request because it is malformed or incorrect.",
    "target": "query",
    "innerError": {
      "code": "invalidExpansion",
      "propertyName": "flags.id"
    }
  }
}
```

### General: Invalid Query Parameters: Too Many levels of expansion

If an api call is made using an expansion that has too many levels, the caller will receive an error.

```http
GET https://graph.microsoft.com/v1/users/cd5762b7-9f3e-474f-b28f-dcbfac9ace1c?$select=id,displayName,assignedLicenses&$expand=assignments($expand=cloudLicensing/allotment($expand=id))
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "Cannot process the request because it is malformed or incorrect.",
    "target": "query",
    "innerError": {
      "code": "invalidExpansion",
      "propertyName": "cloudLicensing.assignments.allotment.id"
    }
  }
}
```

### General: Invalid Query Parameters: Some aspect of the query is formatted incorrectly

If an api call is made using an invalid query string, the caller will receive an error.

```http
GET https://graph.microsoft.com/v1/me/usageRights/35aa6d78-186f-4f3e-bc1e-6d3c52975fd8/assignments?$select=$expand=flags($select=id)
```

```http
HTTP 1.1/400 BadRequest
Content-Type: application/json

{
  "error": {
    "code": "badRequest",
    "message": "Cannot process the request because it is malformed or incorrect.",
    "target": "query",
    "innerError": {
      "code": "invalidQuery"
    }
  }
}
```

### General: Throttling

If an api call is made that exceeds the throttling limits, the caller will receive an error.

```http
POST https://graph.microsoft.com/v1/admin/cloudLicensing/allotments/2afb23bc-12bb-4e01-ac77-a909d1723756/cloudLicensing/assignments
Content-Type: application/json

{
    "assignedTo@odata.bind": "https://graph.microsoft.com/v1/users/d6125d65-8a97-4b1d-b5c9-14d799013255",
    "disabledServicePlanIds": []
}
```

```http
HTTP 1.1/429 TooManyRequests
Retry-After: 550
Content-Type: application/json

{
  "error": {
    "code": "tooManyRequests",
    "message": "Please retry again later.",
    "innerError": {
      "code": "tooManyRequests",
      "retryAfterSeconds": 550
    }
  }
}
```

## Appendix

### Consuming licenses of the same SKU from multiple allotments

With the introduction of allotments, it is possible for the same user or device to receive a license from more than one allotment for the same product-SKU. assignLicense will not create this situation, but it is possible to enter this situation by directly creating assignments from different allotments for the same SKU. When this happens, the user or device will consume one license from each allotment. We de-dupe within a single allotment to account for overlapping group memberships, but we do not dedupe across allotments. This is an intentional decision, not a system limitation.

For more information, see [**_Limiting multi-allotment license consumption_**](#limiting-multi-allotment-license-consumption) in the following section.

### Other design patterns or models that were considered

#### Extending assignLicense to support allotments

Early in the design process, we had plans to extend assignLicense to support using allotmentId references instead of skuId references. We had two new properties, addAllotments and removeAllotments, that were mirrors of the other two. This later became a new OData action called assignAllotments. In initial discussions with Graph API representatives, we were instead convinced to move toward a model of representing each individual assignment as a distinct entity.

#### The SKU-default allotment

Before we moved to our current backward compatibility model for assignLicense, where we assign from any allotment with available licenses and then update/delete all existing assignments for that directoryObject+SKU simultaneously, we had initially planned something entirely different. Each SKU would have a configurable "default allotment," and references to that skuId would be translated into references to that allotmentId instead.

While this concept existed, its representation went through a couple of different iterations. It started as a boolean isSkuDefault property on the allotments themselves, and it was later moved a navigation property on the now-defunct allottable entity.

We kept this design in various forms for a long time, but were ultimately convinced that a different approach would make the assignLicense compatibility behavior more seamless.

#### The allottable or licensedProduct entity

We originally had a separate entity which represented a specific product-SKU for which allotments exist in the tenant. There was a bidirectional relationship between this entity and the allotment entity—one allottable to many allotments. It was originally called a "licensedProduct," but once we introduced the "licensing" namespace that felt a bit redundant. Its final name before retirement was "allottable."

The primary purpose of the allottable entity set was grouping allotments based on their contents. It had no meaningful properties other than self-identification—an id and a type—and a variety of navigation properties. We ultimately got rid of it for that reason, as allotments can already be filtered by these product-SKU-identifying properties.

Another point that we went back and forth on—while we still had this entity concept—was how to group the allotments. Does an allottable represent a unique legacy product SKU (provisioned in the directory, skuId GUID), or does it represent a unique modern product SKU (BigCatalog 12-character productId and 4-character skuId)? The widespread use of legacy skuId GUIDs caused us to lean in that direction, but the inclusion of so-called "native modern" products pulled us back the other way. To complicate matters, there is not a 1:1 relationship between these two types of SKUs. We eventually settled on having a type property to help us distinguish between the two groupings, before we ultimately removed the entity anyway.

In subsequent discussions, we decided that having grouping and aggregation capabilities was still valuable, despite our other concerns. When we discovered the [OData Extension for Data Aggregation Version 4.0](https://docs.oasis-open.org/odata/odata-data-aggregation-ext/v4.0/odata-data-aggregation-ext-v4.0.html), it became clear that this was the solution to our problems. From section 2:

> Extending the OData query features with simple aggregation capabilities avoids cluttering OData services with an exponential number of explicitly modeled "aggregation level entities" or else restricting the consumer to a small subset of predefined aggregations.

This approach allows us to avoid designing complicated aggregate entities that attempt to be all things to all consumers. Clients can write their own simple queries that suit their specific needs, grouping allotments and aggregating their data as they see fit.

#### The allotmentSource or subscription entity

Because we plan to support splitting one subscription across multiple allotments in the future, we originally had a separate entity in our design to represent the subscription itself. This subscription would have a navigation property to a collection of allotments. However, this collection would always contain only a single element until we develop and release the split feature and unless the customer in question is actually using it. We decided that it was not worth the added complexity on the API surface to accommodate this future less-common case in this way.

When we do get to the split feature, we can accomplish the same thing without the extra entity. We may choose to highlight that one allotment is the original/primary/parent/source and/or establish a relationship between allotments with the same subscription, but either of these could be achieved by extending the allotment entity.

#### Waiting rooms without the waitingMember entity

The waitingMember entity is rather thin, containing only its own id and a timestamp. We didn't have the timestamp at first; at that time, the relationship could have been expressed as a collection navigation property on the allotment that pointed straight to the users or devices and collection navigation properties on the user and device that pointed straight to the allotments. We deemed the timestamp important, however, and therefore we needed an entity in the middle.

#### Localized display information for product-SKUs and usageRightServices

For developer convenience, we considered including a way to get localized display information for the product-SKU and usageRightServices. The identifiers associated with the SKUs and services these end users are actually receiving are not human readable. Because this data is not in our domain, we would only have included it only when explicitly requested. The first problem was how to indicate the desired locale. Should it be a unique query string? Should it be automatically determined based on the authenticated user? What about localization headers? The final iteration framed it as a collection of displayInfo entities—the id was the specific locale (e.g., "en-US") while the language ("en") and market ("US") were also separate properties that could be used for filter queries.

While this last option seemed to us like the most appropriate design from a Graph API perspective, it was not clear that we could actually pull off such query capabilities. This led to discussion over whether such information even belonged in the licensing namespace. We ultimately decided to remove it, leaving management experiences and client applications to integrate with DisplayCatalog directly. Our first-party portals already do that, and we feel it's reasonable that a client application which relies on usageRights to check its licenses should know the names of its own offerings (if it wants to display them).

#### Limiting multi-allotment license consumption

A user is assigned licenses from multiple different allotments. Do they consume one license total, or one license in each allotment? This is a question that we have debated exhaustively.

It is simply not possible for more than four of the following propositions to be true simultaneously:

1. A licensed user or device will not experience service interruption unless that license is removed or its backing subscription expires.
2. Every license in any allotment can be given to a unique user or device.
3. Licenses cannot be granted to more users or devices than the capacity of the allotment.
4. A user or device can be assigned to multiple allotments for the same product, directly or via group membership.
5. A user or device will never consume more than one license for the same product.

We chose a solution where the first four propositions are true and the fifth is false. For clarity, they will henceforth be referred to as "guarantees."

The importance of the first guarantee is self-evident—if I have a license assignment, it should do something. Likewise, my license assignment should not abruptly stop working. The importance of the second guarantee is also rather obvious; if a customer buys N licenses, then N users (or devices) should be able to benefit from those licenses. If this is not guaranteed, then we have broken our customer's trust. The third guarantee is similarly important, but for different reasons. While some customers would be happy to receive more than they paid for, Microsoft would directly lose money. Clearly, we cannot undermine either of these guarantees.

The fourth guarantee may seem less important at first glance, but it avoids an administrative nightmare for customers. With direct assignments, it is technically feasible to block an assignment from allotment B if the user is already assigned to allotment A, but that would be rather annoying and could become problematic. Suppose that the owners of both allotments initially intend for the user to have access; the assignment from allotment A succeeds, but the assignment from allotment B fails. The owner of allotment B is informed that their intended user still has access to the product, so it's fine. Now suppose that either allotment A expires or the owner of allotment A takes that license back, for whatever reason. The user experiences service interruption, which the owner of allotment B—who always intended for the user to have a license—must now correct. One might imagine this scenario playing out with allotments owned by teachers in an educational setting. Perhaps the user is a student who needs access to the same software for two different classes, but leaves one of the classes partway through the year. There is no good way to prevent this situation, as the two assignments can never overlap.

It gets worse. With group-based licensing, such enforcement goes from frustrating to unreasonably difficult. Individual Microsoft employees, for example, can easily be direct members of hundreds of groups. Including transitive memberships, this number often exceeds one thousand. Without the fourth guarantee, if any two of these groups are assigned to different allotments for the same product, the customer will experience some sort of licensing error. No matter how good a hypothetical untangling wizard UX might be, this is surely a recipe for frustration.

The fifth proposition—which is not guaranteed by our system—also has obvious value. If a user is receiving duplicate licenses, but they aren't getting any additional benefit for those licenses, why should they consume more than one of them? Unfortunately, there is no way to enable this without breaking one or more of the four existing guarantees.

One approach is to entirely prevent the situation where there are multiple allotments from which a user receives a license, which violates the fourth guarantee by definition. Another solution is to have the system pick one of the allotments based on some deterministic logic, but that creates new problems. Aside from the complexity of simply maintaining that accounting association, it introduces a new question—how do we preserve the capacity limits on the other allotments?

Suppose a user is linked via direct or group assignment to allotments A and B, which both contain the same product-SKU. Suppose that this is the only overlapping user between these two allotments, which are otherwise full. If the fifth proposition is false, they are both full; if the fifth proposition is true, then only one of them is full. For the sake of argument, suppose the fifth proposition is true. Now, suppose our system decides that allotment A is the allotment from which this user should consume a license. All licenses in allotment A are consumed, and one license in allotment B is not consumed. Suppose that final license in allotment B is assigned to a completely new, heretofore unlicensesd user. Now, suppose that the overlapping user loses their connection to allotment A—either due to subscription expiration, group membership removal, or assignment removal. What happens to this user?

If we maintain the capacity restriction on allotment B—thereby preserving the third guarantee—then the user experiences service interruption, breaking the first guarantee. If we prevent service interruption—preserving the first guarantee—by allowing the user to consume an additional license beyond the capacity of allotment B, we break the third guarantee. If we attempt to prevent this situation altogether by not allowing the final license in allotment B to be assigned, we break the second guarantee.

In summary: it is simply not possible for all five propositions to be true; we have chosen to prioritize the first four and make those our guarantees. As a consequence, users or devices may consume multiple licenses of the same SKU (without receiving any additional benefit) under certain circumstances.

#### Associating assignmentErrors with specific allotments

We discussed modeling relationships between assignmentErrors and specific allotments, but we were unable to find an efficient way to support this with our underlying data and we do not believe this support to be sufficiently useful for us to work to accommodate it. With group-based licensing, we don't have a simple way to directly enumerate all of the transitive license recipients, let alone the ones with errors. However, the actual problem which produces an assignmentError is inherently scoped to the SKU, as that is the scope at which multiple assignments are combined on the same user. Fixing an assignmentError is also likely to require a holistic approach, including the context of everything which is assigned to that user.

#### One subscription per allotment

While it is our expectation that this will be the most common case and eventually the only case, in the near future we cannot guarantee that all allotments will be tied only to one subscription. This whole Cloud Licensing effort is part of a longer plan to transition ownership of licensing from Directory Services to Commerce, which will involve a backend platform migration. Prior to that migration—and for an indefinite period after, in certain rare edge cases—some allotments will need to be a pool of multiple subscriptions, as subscribedSkus are today. We initially wanted to optimize for that one-subscription future, but it became increasingly difficult to explain and handle in the intermediate period. So, we put subscription information in an array. That array will often only have one entry, but sometimes it won't. We need to honor that.

#### Services as entities

We briefly considered modeling services as entities, which could be enabled or disabled on assignments by adding or removing references to these services. Given how the assignments are expected to be manipulated—with the complete set of enabled and disabled plans being reconfigured every time, possibly toggling many values at once—it made the call pattern too complex.

#### SubscribedSku relationships instead of skuId and skuPartNumber properties

The subscribedSku resource type belongs to another workload, and this resource does not currently support cross-workload navigation or `$filter` queries. The cross-workload navigation issue appears to be a bug (related to it being a directoryObject whose id is not a GUID), but lack of `$filter` query support is a problem that may take much longer to address. We use SKU-based filtering extensively in our scenarios, so we cannot proceed with the navigation property approach unless both of these issues are resolved.

### Throttling

https://learn.microsoft.com/en-us/graph/throttling

We intend to add throttling on all endpoints.
