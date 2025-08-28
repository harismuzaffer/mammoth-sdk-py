# Projects
(*projects*)

## Overview

### Available Operations

* [add_user](#add_user) - Add user to a project
* [remove_user](#remove_user) - Remove user from a project
* [update_user](#update_user) - Update user role on a project
* [list](#list) - Get list of projects
* [create](#create) - Create a new project in given workspace
* [remove_all](#remove_all) - Delete multiple projects
* [update](#update) - Update multiple projects by adding/removing users or changing roles of the users
* [delete](#delete) - Delete a project
* [rename](#rename) - Update a project
* [get_pending_changes](#get_pending_changes) - Get pending changes for a project
* [get_resource_status](#get_resource_status) - Get resource status

## add_user

This endpoint allows addition of a user to a project.

### Example Usage

<!-- UsageSnippet language="python" operationID="AddUserProject" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/users" -->
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

    ma_client.projects.add_user(workspace_id=4, project_id=4, users=[
        {
            "user_id": 4,
            "role_name": models.RoleName.PROJECT_ADMIN,
        },
    ])

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project to delete                                                                              | 4                                                                                              |
| `users`                                                                                        | List[[models.AddUserSpec](../../models/adduserspec.md)]                                        | :heavy_check_mark:                                                                             | List of user IDs to add to project                                                             | {<br/>"value": [<br/>{<br/>"user_id": 1,<br/>"role_name": "project_admin"<br/>}<br/>]<br/>}    |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## remove_user

This endpoint allows removal of a user from a project.

### Example Usage

<!-- UsageSnippet language="python" operationID="RemoveUserProject" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/users" -->
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

    ma_client.projects.remove_user(workspace_id=4, project_id=4, user_id=4)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project to delete                                                                              | 4                                                                                              |
| `user_id`                                                                                      | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the user                                                                                 | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## update_user

This endpoint allows updation of a user to a project.             User role can be changed from editor to admin or vice versa.

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateUserProject" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/users" -->
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

    ma_client.projects.update_user(workspace_id=4, project_id=4, patch=[
        {
            "op": "replace",
            "path": "permissions",
            "value": models.ProjectUserPatchOpValue.PROJECT_ADMIN,
        },
    ], user_id=4, invite_id=4)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project to delete                                                                              | 4                                                                                              |
| `patch`                                                                                        | List[[models.ProjectUserPatchOp](../../models/projectuserpatchop.md)]                          | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `user_id`                                                                                      | *OptionalNullable[int]*                                                                        | :heavy_minus_sign:                                                                             | Id of the user                                                                                 | 4                                                                                              |
| `invite_id`                                                                                    | *OptionalNullable[int]*                                                                        | :heavy_minus_sign:                                                                             | Id of the invited user                                                                         | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## list

Returns list of projects in given workspace. Query parameters can be used to optimize the response.

### Example Usage

<!-- UsageSnippet language="python" operationID="GetProject" method="get" path="/workspaces/{workspace_id}/projects" -->
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

    res = ma_client.projects.list(workspace_id=4, limit=10, offset=0, fields="id,name", sort="(id:asc)", subscribed="true")

    assert res is not None

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             | Example                                                                                                 |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                          | *int*                                                                                                   | :heavy_check_mark:                                                                                      | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.          | 4                                                                                                       |
| `limit`                                                                                                 | *Optional[int]*                                                                                         | :heavy_minus_sign:                                                                                      | Max number of projects to return                                                                        | 10                                                                                                      |
| `offset`                                                                                                | *Optional[int]*                                                                                         | :heavy_minus_sign:                                                                                      | Offset from the beginning of the project list                                                           | 0                                                                                                       |
| `fields`                                                                                                | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | Fields to be returned in a comma-separated format may include id, name, owner_workspace_id, updated_at. | id,name                                                                                                 |
| `sort`                                                                                                  | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | Returned projects are Sort by this parameter. Can be (id, name, owner_workspace_id, updated_at)         | (id:asc)                                                                                                |
| `subscribed`                                                                                            | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | If true, list only subscribed projects otherwise list all projects                                      | true                                                                                                    |
| `retries`                                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                        | :heavy_minus_sign:                                                                                      | Configuration to override the default retry behavior of the client.                                     |                                                                                                         |

### Response

**[models.ProjectList](../../models/projectlist.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Creates new projects and add user as owner of the project.

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateProject" method="post" path="/workspaces/{workspace_id}/projects" -->
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

    res = ma_client.projects.create(workspace_id=4, name="My Project", properties={
        "color": "#E3E5E8",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `name`                                                                                         | *str*                                                                                          | :heavy_check_mark:                                                                             | Name of project to be created                                                                  | {<br/>"value": {<br/>"name": "My Project"<br/>}<br/>}                                          |
| `properties`                                                                                   | [models.ProjectProperties](../../models/projectproperties.md)                                  | :heavy_check_mark:                                                                             | Properties of project                                                                          | {<br/>"value": {<br/>"color": "#E3E5E8"<br/>}<br/>}                                            |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ProjectSchema](../../models/projectschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## remove_all

Delete multiple projects

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteProjects" method="delete" path="/workspaces/{workspace_id}/projects" -->
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

    ma_client.projects.remove_all(workspace_id=4, ids="1,2,3")

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `ids`                                                                                          | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Multiple project ids, comma separated                                                          | 1,2,3                                                                                          |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.DeleteProjectsResponseBodyError1 | 400                                     | application/json                        |
| errors.DeleteProjectsResponseBodyError2 | 400                                     | application/json                        |
| errors.DeleteProjectsUnauthorizedError  | 401                                     | application/json                        |
| errors.MammothAnalyticsDefaultError     | 4XX, 5XX                                | \*/\*                                   |

## update

Update multiple projects by adding/removing users or changing roles of the users

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateProjects" method="patch" path="/workspaces/{workspace_id}/projects" -->
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

    ma_client.projects.update(workspace_id=4, patches=[
        {
            "op": models.ProjectsPatchOpOp.ADD,
            "path": models.ProjectsPatchOpPath.ROLE,
            "value": [
                {
                    "project_id": 4,
                    "user_roles": [
                        {
                            "user_id": 3,
                            "role": models.UserRolesPatchRole.PROJECT_ADMIN,
                        },
                        {
                            "user_id": 4,
                            "role": models.UserRolesPatchRole.PROJECT_ADMIN,
                        },
                    ],
                    "invite_roles": [
                        {
                            "invite_id": 3,
                            "role": models.InviteProjectRolePatchRole.PROJECT_ADMIN,
                        },
                    ],
                },
            ],
        },
    ])

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `patches`                                                                                      | List[[models.ProjectsPatchOp](../../models/projectspatchop.md)]                                | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.UpdateProjectsResponseBodyError1 | 400                                     | application/json                        |
| errors.UpdateProjectsResponseBodyError2 | 400                                     | application/json                        |
| errors.UpdateProjectsUnauthorizedError  | 401                                     | application/json                        |
| errors.MammothAnalyticsDefaultError     | 4XX, 5XX                                | \*/\*                                   |

## delete

This action removes a project along with its associated data.            It operates asynchronously, so the deletion process may take some time to complete fully.            Currently, there's no tracking available; to check the status, attempt listing the projects again.            Please proceed cautiously as deleted data cannot be recovered.

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteProject" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}" -->
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

    ma_client.projects.delete(workspace_id=4, project_id=4)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project to delete                                                                              | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## rename

Currently on project rename is allowed

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateProject" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}" -->
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

    res = ma_client.projects.rename(workspace_id=4, project_id=4, patches=[
        {
            "op": "replace",
            "path": models.ProjectPatchOpPath.NAME,
            "value": {
                "color": "{\"value\":{\"color\":\"#E3E5E8\"}}",
            },
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project to delete                                                                              | 4                                                                                              |
| `patches`                                                                                      | List[[models.ProjectPatchOp](../../models/projectpatchop.md)]                                  | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ProjectSchema](../../models/projectschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## get_pending_changes


        This endpoint fetches pending changes for a project including:
        - Non-sync items
        - Pending data update items
        - Pending pipeline changes
        

### Example Usage

<!-- UsageSnippet language="python" operationID="GetPendingChanges" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/pending-changes" -->
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

    res = ma_client.projects.get_pending_changes(workspace_id=4, project_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project to delete                                                                              | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.GetPendingItemsResponse](../../models/getpendingitemsresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## get_resource_status

Returns the current status for all resources in the project

### Example Usage

<!-- UsageSnippet language="python" operationID="GetResourceStatus" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/resource-status" -->
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

    res = ma_client.projects.get_resource_status(workspace_id=4, project_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project to delete                                                                              | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ResourceStatusResponse](../../models/resourcestatusresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |