# OwnerUserControlSettings
(*owner_user_control_settings*)

## Overview

### Available Operations

* [list_users](#list_users) - List users of all workspaces
* [transfer_ownerships](#transfer_ownerships) - Transfer ownerships of the workspaces

## list_users

List users of all workspaces where the user is an owner

### Example Usage

<!-- UsageSnippet language="python" operationID="ListUsersOfWorkspaces" method="get" path="/settings/users" -->
```python
from mammoth_analytics import MammothAnalytics, models
import os


with MammothAnalytics(
    server_url="https://api.example.com",
    security=models.Security(
        api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
        api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
    ),
) as ma_client:

    res = ma_client.owner_user_control_settings.list_users(fields="id,email", sort="(email:desc), (id:asc)", offset=1, limit=10)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     | Example                                                                                         |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `fields`                                                                                        | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | Fields to be returned in a comma-separated format may include id, name, created_at, updated_at. | id,email                                                                                        |
| `sort`                                                                                          | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | Sort users by id, first_name or email                                                           | (email:desc), (id:asc)                                                                          |
| `offset`                                                                                        | *Optional[int]*                                                                                 | :heavy_minus_sign:                                                                              | Offset from the beginning of the users list                                                     | 1                                                                                               |
| `limit`                                                                                         | *Optional[int]*                                                                                 | :heavy_minus_sign:                                                                              | Max number of users to return                                                                   | 10                                                                                              |
| `retries`                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                | :heavy_minus_sign:                                                                              | Configuration to override the default retry behavior of the client.                             |                                                                                                 |

### Response

**[models.ListUsersOfWorkspacesResponse](../../models/listusersofworkspacesresponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| errors.ListUsersOfWorkspacesBadRequestError | 400                                         | application/json                            |
| errors.MammothAnalyticsDefaultError         | 4XX, 5XX                                    | \*/\*                                       |

## transfer_ownerships

Transfer ownerships of the workspaces

### Example Usage

<!-- UsageSnippet language="python" operationID="TransferOwnerships" method="patch" path="/settings/users" -->
```python
from mammoth_analytics import MammothAnalytics, models
import os


with MammothAnalytics(
    server_url="https://api.example.com",
    security=models.Security(
        api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
        api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
    ),
) as ma_client:

    res = ma_client.owner_user_control_settings.transfer_ownerships(patches=[
        {
            "op": models.WorkspaceUsersSettingsPatchOpOp.REPLACE,
            "path": models.WorkspaceUsersSettingsPatchOpPath.ROLE,
            "value": {
                "workspace_id": 1,
                "user_id": 29,
                "remove_role": models.TransferOwnershipRemoveRole.WORKSPACE_MEMBER,
            },
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                   | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `patches`                                                                                   | List[[models.WorkspaceUsersSettingsPatchOp](../../models/workspaceuserssettingspatchop.md)] | :heavy_check_mark:                                                                          | N/A                                                                                         |
| `retries`                                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                            | :heavy_minus_sign:                                                                          | Configuration to override the default retry behavior of the client.                         |

### Response

**[models.TransferOwnershipsResponse](../../models/transferownershipsresponse.md)**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| errors.TransferOwnershipsBadRequestError | 400                                      | application/json                         |
| errors.MammothAnalyticsDefaultError      | 4XX, 5XX                                 | \*/\*                                    |