# WorkspacesSDK
(*workspaces*)

## Overview

### Available Operations

* [add_connector_addon](#add_connector_addon) - Add connector addon to workspace
* [add_storage_addon](#add_storage_addon) - Add storage addon to workspace
* [list_users](#list_users) - Get users in workspace
* [add_user](#add_user) - Add user in workspace
* [remove_member](#remove_member) - Remove users or invites from workspace
* [modify_member](#modify_member) - Resend invite, remove invitation, or change role in workspace
* [add_user_seats_addon](#add_user_seats_addon) - Add user seats addon to workspace
* [list](#list) - Get workspaces
* [create](#create) - Create workspace
* [get](#get) - Get workspace details
* [delete](#delete) - Delete a workspace
* [update](#update) - Update workspace
* [remove_user](#remove_user) - Remove user from workspace/Leave workspace
* [update_user](#update_user) - Change user role in workspace

## add_connector_addon

Add a connector addon to the specified workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="AddConnectorAddon" method="post" path="/workspaces/{workspace_id}/addons/connectors" -->
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

    res = ma_client.workspaces.add_connector_addon(workspace_id=4, connector_id=[object Object])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `connector_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | ID of the connector to add as an addon                                                         | {<br/>"value": 1<br/>}                                                                         |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.AddonSuccessResponse](../../models/addonsuccessresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## add_storage_addon

Add storage addon to the specified workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="AddStorageAddon" method="post" path="/workspaces/{workspace_id}/addons/storage" -->
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

    res = ma_client.workspaces.add_storage_addon(workspace_id=4, additional_storage_gb=[object Object])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `additional_storage_gb`                                                                        | *int*                                                                                          | :heavy_check_mark:                                                                             | Amount of additional storage to add in gigabytes                                               | {<br/>"value": 100<br/>}                                                                       |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.WorkspaceAddonResponse](../../models/workspaceaddonresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## list_users

Get all users inside of given workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="GetUsersInWorkspace" method="get" path="/workspaces/{workspace_id}/users" -->
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

    res = ma_client.workspaces.list_users(workspace_id=4, fields="id,email", sort="(email:desc), (id:asc)", first_name="John", last_name="John", email="john.doe@rediffmail.com", ids="1,2,3", offset=1, limit=10, invited=True, project_id=4)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     | Example                                                                                         |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                  | *int*                                                                                           | :heavy_check_mark:                                                                              | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.  | 4                                                                                               |
| `fields`                                                                                        | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | Fields to be returned in a comma-separated format may include id, name, created_at, updated_at. | id,email                                                                                        |
| `sort`                                                                                          | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | Sort users by id, first_name or email                                                           | (email:desc), (id:asc)                                                                          |
| `first_name`                                                                                    | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | Fetch all users which matches given name (case sensitive)                                       | John                                                                                            |
| `last_name`                                                                                     | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | Fetch all users which matches given name (case sensitive)                                       | John                                                                                            |
| `email`                                                                                         | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | Fetch user which matches given email                                                            | john.doe@rediffmail.com                                                                         |
| `ids`                                                                                           | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | Filter users by ids, provided as comma separated integer values                                 | 1,2,3                                                                                           |
| `offset`                                                                                        | *Optional[int]*                                                                                 | :heavy_minus_sign:                                                                              | Offset from the beginning of the users list                                                     | 1                                                                                               |
| `limit`                                                                                         | *Optional[int]*                                                                                 | :heavy_minus_sign:                                                                              | Max number of users to return                                                                   | 10                                                                                              |
| `invited`                                                                                       | *Optional[bool]*                                                                                | :heavy_minus_sign:                                                                              | Include invited users                                                                           | true                                                                                            |
| `project_id`                                                                                    | *OptionalNullable[int]*                                                                         | :heavy_minus_sign:                                                                              | Project ID of the workspace                                                                     | 4                                                                                               |
| `retries`                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                | :heavy_minus_sign:                                                                              | Configuration to override the default retry behavior of the client.                             |                                                                                                 |

### Response

**[models.WorkspaceUserGetResponse](../../models/workspaceusergetresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## add_user

Add users inside of given workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="AddUserInWorkspace" method="post" path="/workspaces/{workspace_id}/users" -->
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

    res = ma_client.workspaces.add_user(workspace_id=4, invite={
        "email_ids": [
            "apitests2@mammoth.io",
        ],
        "projects": [
            {
                "project_id": 1,
            },
        ],
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `invite`                                                                                       | [models.UserInviteSchema](../../models/userinviteschema.md)                                    | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.WorkspaceUserInviteResponse](../../models/workspaceuserinviteresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## remove_member

Remove users or invites from workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="RemoveUserFromWorkspace" method="delete" path="/workspaces/{workspace_id}/users" -->
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

    ma_client.workspaces.remove_member(workspace_id=4, ids="1,4", invite_ids="1,4")

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `ids`                                                                                          | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Comma separated user ids                                                                       | 1,4                                                                                            |
| `invite_ids`                                                                                   | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Comma separated invitation ids                                                                 | 1,4                                                                                            |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                                    | Status Code                                   | Content Type                                  |
| --------------------------------------------- | --------------------------------------------- | --------------------------------------------- |
| errors.RemoveUserFromWorkspaceBadRequestError | 400                                           | application/json                              |
| errors.MammothAnalyticsDefaultError           | 4XX, 5XX                                      | \*/\*                                         |

## modify_member

Resend invite, remove invitation, or change workspace role of a invited user, transfer ownership

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateUserToWorkspace" method="patch" path="/workspaces/{workspace_id}/users" -->
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

    ma_client.workspaces.modify_member(workspace_id=4, patches=[
        {
            "op": models.WorkspaceUsersPatchOpOp.COMMAND,
            "path": models.WorkspaceUsersPatchOpPath.INVITE_RESEND,
            "value": "1",
        },
    ])

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `patches`                                                                                      | List[[models.WorkspaceUsersPatchOp](../../models/workspaceuserspatchop.md)]                    | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| errors.UpdateUserToWorkspaceBadRequestError | 400                                         | application/json                            |
| errors.MammothAnalyticsDefaultError         | 4XX, 5XX                                    | \*/\*                                       |

## add_user_seats_addon

Add user seats addon to the specified workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="AddUserSeatsAddon" method="post" path="/workspaces/{workspace_id}/addons/users" -->
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

    res = ma_client.workspaces.add_user_seats_addon(workspace_id=4, user_count=[object Object])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `user_count`                                                                                   | *Optional[int]*                                                                                | :heavy_minus_sign:                                                                             | Number of additional user seats to add                                                         | {<br/>"value": 5<br/>}                                                                         |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.AddonSuccessResponse](../../models/addonsuccessresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## list

Get all workspaces

### Example Usage

<!-- UsageSnippet language="python" operationID="GetWorkspaces" method="get" path="/workspaces" -->
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

    res = ma_client.workspaces.list(fields="id,name", name="My Workspace", created_at="(from:'2023-12-16T09:39:17.628Z',to:'2023-12-16T09:42:43.152Z')", updated_at="(from:'2023-12-16T09:39:17.628Z',to:'2023-12-16T09:42:43.152Z')", sort="(name:desc), (id:asc)", offset=1, limit=10)

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     | Example                                                                                         |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `fields`                                                                                        | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | Fields to be returned in a comma-separated format may include id, name, created_at, updated_at. | id,name                                                                                         |
| `name`                                                                                          | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | Fetch all workspaces which matches given name (case sensitive)                                  | My Workspace                                                                                    |
| `created_at`                                                                                    | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | Fetch all workspaces which matches given filter criterion                                       | (from:'2023-12-16T09:39:17.628Z',to:'2023-12-16T09:42:43.152Z')                                 |
| `updated_at`                                                                                    | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | Fetch all workspaces which matches given filter criterion                                       | (from:'2023-12-16T09:39:17.628Z',to:'2023-12-16T09:42:43.152Z')                                 |
| `sort`                                                                                          | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | Sort workspace by id or name                                                                    | (name:desc), (id:asc)                                                                           |
| `offset`                                                                                        | *Optional[int]*                                                                                 | :heavy_minus_sign:                                                                              | Offset from the beginning of the workspace list                                                 | 1                                                                                               |
| `limit`                                                                                         | *Optional[int]*                                                                                 | :heavy_minus_sign:                                                                              | Max number of workspaces to return                                                              | 10                                                                                              |
| `retries`                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                | :heavy_minus_sign:                                                                              | Configuration to override the default retry behavior of the client.                             |                                                                                                 |

### Response

**[models.WorkspacesSchema](../../models/workspacesschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Create a new workspace with optional plan assignment

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateWorkspace" method="post" path="/workspaces" -->
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

    res = ma_client.workspaces.create(request={})

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `request`                                                               | [models.CreateWorkspaceRequest](../../models/createworkspacerequest.md) | :heavy_check_mark:                                                      | The request object to use for the request.                              |
| `retries`                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)        | :heavy_minus_sign:                                                      | Configuration to override the default retry behavior of the client.     |

### Response

**[models.CreateWorkspaceResponse](../../models/createworkspaceresponse.md)**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.CreateWorkspaceBadRequestError | 400                                   | application/json                      |
| errors.MammothAnalyticsDefaultError   | 4XX, 5XX                              | \*/\*                                 |

## get

Fetch additional details about workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="GetWorkspace" method="get" path="/workspaces/{workspace_id}" -->
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

    res = ma_client.workspaces.get(workspace_id=4, fields="id,name")

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     | Example                                                                                         |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                  | *int*                                                                                           | :heavy_check_mark:                                                                              | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.  | 4                                                                                               |
| `fields`                                                                                        | *Optional[str]*                                                                                 | :heavy_minus_sign:                                                                              | Fields to be returned in a comma-separated format may include id, name, created_at, updated_at. | id,name                                                                                         |
| `retries`                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                | :heavy_minus_sign:                                                                              | Configuration to override the default retry behavior of the client.                             |                                                                                                 |

### Response

**[models.WorkspacesSchema](../../models/workspacesschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## delete

Delete the specified workspace.

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteUserWorkspace" method="delete" path="/workspaces/{workspace_id}" -->
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

    ma_client.workspaces.delete(workspace_id=4)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| errors.DeleteUserWorkspaceBadRequestError | 400                                       | application/json                          |
| errors.MammothAnalyticsDefaultError       | 4XX, 5XX                                  | \*/\*                                     |

## update

Update workspace details

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateWorkspace" method="patch" path="/workspaces/{workspace_id}" -->
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

    res = ma_client.workspaces.update(workspace_id=4, patches=[
        {
            "op": "replace",
            "path": models.WorkspacePatchOpPath.NAME,
            "value": "My cool workspace",
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `patches`                                                                                      | List[[models.WorkspacePatchOp](../../models/workspacepatchop.md)]                              | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.WorkspacesWorkspaceSchemaWorkspaceUpdate](../../models/workspacesworkspaceschemaworkspaceupdate.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## remove_user

Remove user from given workspace/Leave workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="RemoveUser" method="delete" path="/workspaces/{workspace_id}/users/{user_id}" -->
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

    ma_client.workspaces.remove_user(workspace_id=4, user_id=4)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `user_id`                                                                                      | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the user                                                                                 | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.RemoveUserBadRequestError    | 400                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## update_user

This endpoint can be used to change user role in workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateUserInWorkspace" method="patch" path="/workspaces/{workspace_id}/users/{user_id}" -->
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

    res = ma_client.workspaces.update_user(workspace_id=4, user_id=4, patches=[
        {
            "op": "replace",
            "path": "role",
            "value": models.WorkspaceUserPatchOpValue.WORKSPACE_MEMBER,
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `user_id`                                                                                      | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the user                                                                                 | 4                                                                                              |
| `patches`                                                                                      | List[[models.WorkspaceUserPatchOp](../../models/workspaceuserpatchop.md)]                      | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.WorkspaceUserPatchResponse](../../models/workspaceuserpatchresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |