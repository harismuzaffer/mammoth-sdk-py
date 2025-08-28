# UsersSupport
(*users_support*)

## Overview

### Available Operations

* [list](#list) - Get users list
* [add_to_workspace](#add_to_workspace) - Add a user to the workspace
* [transfer_roles](#transfer_roles) - Transfer workspace ownership
* [remove](#remove) - Remove a user in a workspace

## list

Retrieve a list of users within a workspace.

### Example Usage

<!-- UsageSnippet language="python" operationID="GetUserList" method="get" path="/support/workspaces/{workspace_id}/users" -->
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

    res = ma_client.users_support.list(workspace_id=4, limit=10, offset=0, fields="id,email", sort="(email:asc),(id:desc)")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                   | Type                                                                                                                                        | Required                                                                                                                                    | Description                                                                                                                                 | Example                                                                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                                                              | *int*                                                                                                                                       | :heavy_check_mark:                                                                                                                          | Id of the workspace to work with                                                                                                            | 4                                                                                                                                           |
| `limit`                                                                                                                                     | *Optional[int]*                                                                                                                             | :heavy_minus_sign:                                                                                                                          | Max number of result to return                                                                                                              | 10                                                                                                                                          |
| `offset`                                                                                                                                    | *Optional[int]*                                                                                                                             | :heavy_minus_sign:                                                                                                                          | Distance from the beginning of the list of results                                                                                          | 0                                                                                                                                           |
| `fields`                                                                                                                                    | *Optional[str]*                                                                                                                             | :heavy_minus_sign:                                                                                                                          | Fields to return. Can be (id, email)                                                                                                        | id,email                                                                                                                                    |
| `sort`                                                                                                                                      | *OptionalNullable[str]*                                                                                                                     | :heavy_minus_sign:                                                                                                                          | Returned users from a workspaces based on this parameter, User format '(field:asc)' for ascending and  '(field:desc)' for descending order. | (email:asc),(id:desc)                                                                                                                       |
| `retries`                                                                                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                            | :heavy_minus_sign:                                                                                                                          | Configuration to override the default retry behavior of the client.                                                                         |                                                                                                                                             |

### Response

**[models.UserList](../../models/userlist.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## add_to_workspace

Add a user into the specified workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="AddUserToWorkspace" method="post" path="/support/workspaces/{workspace_id}/users" -->
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

    res = ma_client.users_support.add_to_workspace(workspace_id=4, email="johnsmith@gmail.com", role=models.AddUserSupportRole.WORKSPACE_ADMIN, first_name="John", last_name="Smith")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `workspace_id`                                                      | *int*                                                               | :heavy_check_mark:                                                  | Id of the workspace to work with                                    | 4                                                                   |
| `email`                                                             | *str*                                                               | :heavy_check_mark:                                                  | Email of the customer                                               | {<br/>"value": "kia@example.com"<br/>}                              |
| `role`                                                              | [models.AddUserSupportRole](../../models/addusersupportrole.md)     | :heavy_check_mark:                                                  | Role of the user                                                    | {<br/>"summary": "Sample User Roles",<br/>"value": "workspace_member"<br/>} |
| `first_name`                                                        | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | First name of the user                                              | {<br/>"summary": "Sample First Name",<br/>"value": "Jacob"<br/>}    |
| `last_name`                                                         | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | Last name of the user                                               | {<br/>"summary": "Sample Last Name",<br/>"value": "van"<br/>}       |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.UserPostSchema](../../models/userpostschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## transfer_roles

Transfer workspace ownership to another user

### Example Usage

<!-- UsageSnippet language="python" operationID="TransferUserRoles" method="patch" path="/support/workspaces/{workspace_id}/users" -->
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

    res = ma_client.users_support.transfer_roles(workspace_id=4, patch=[
        {
            "op": "replace",
            "path": "role",
            "value": {},
        },
        {
            "op": "replace",
            "path": "role",
            "value": {},
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                           | Type                                                                                | Required                                                                            | Description                                                                         | Example                                                                             |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `workspace_id`                                                                      | *int*                                                                               | :heavy_check_mark:                                                                  | Id of the workspace to work with                                                    | 4                                                                                   |
| `patch`                                                                             | List[[models.AdminWorkspaceUserPatchOp](../../models/adminworkspaceuserpatchop.md)] | :heavy_check_mark:                                                                  | N/A                                                                                 |                                                                                     |
| `retries`                                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                    | :heavy_minus_sign:                                                                  | Configuration to override the default retry behavior of the client.                 |                                                                                     |

### Response

**[models.UserList](../../models/userlist.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## remove

Remove a user from the specified workspace.

### Example Usage

<!-- UsageSnippet language="python" operationID="RemoveWorkspaceUser" method="delete" path="/support/workspaces/{workspace_id}/users/{user_id}" -->
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

    ma_client.users_support.remove(workspace_id=4, user_id=4)

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `workspace_id`                                                      | *int*                                                               | :heavy_check_mark:                                                  | Id of the workspace to work with                                    | 4                                                                   |
| `user_id`                                                           | *int*                                                               | :heavy_check_mark:                                                  | Id of the user to work with                                         | 4                                                                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |