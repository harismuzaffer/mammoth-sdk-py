# Folders
(*folders*)

## Overview

### Available Operations

* [list](#list) - List folders
* [create](#create) - Create Folder
* [remove](#remove) - Delete folders
* [update_resources](#update_resources) - Move resources from/to folder
* [get](#get) - Get Folder Details
* [delete](#delete) - Delete Folder
* [update](#update) - Updates the folder details

## list

List folders.

### Example Usage

<!-- UsageSnippet language="python" operationID="ListFolders" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/folders" -->
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

    res = ma_client.folders.list(workspace_id=4, project_id=4, fields="id,name", id="1,2,3", name="folder_name1,folder_name2,folder_name3", status="ready,deleting", created_at="(from:'2023-12-19T09:39:17.728Z',to:'2023-12-26T19:42:43.152Z')", updated_at="(from:'2024-12-19T09:39:17.628Z',to:'2024-12-26T09:42:43.152Z')", created_by="riya,geeta", limit=10, offset=10, sort="(id:asc),(name:asc)")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      | Example                                                                                          |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `workspace_id`                                                                                   | *int*                                                                                            | :heavy_check_mark:                                                                               | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.   | 4                                                                                                |
| `project_id`                                                                                     | *int*                                                                                            | :heavy_check_mark:                                                                               | Project ID of the workspace                                                                      | 4                                                                                                |
| `fields`                                                                                         | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Fields to be returned in a comma-separated format may include id, name, status_info, created_at. | id,name                                                                                          |
| `id`                                                                                             | *Optional[str]*                                                                                  | :heavy_minus_sign:                                                                               | Filter by multiple folder ids, comma separated                                                   | 1,2,3                                                                                            |
| `name`                                                                                           | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Filter by multiple folder names, comma separated                                                 | folder_name1,folder_name2,folder_name3                                                           |
| `status`                                                                                         | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Filter by multiple folder statuses, comma separated                                              | ready,deleting                                                                                   |
| `created_at`                                                                                     | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Filter by multiple folders, which falls under created_at date range                              | (from:'2023-12-19T09:39:17.728Z',to:'2023-12-26T19:42:43.152Z')                                  |
| `updated_at`                                                                                     | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Filter by multiple folders, which falls under updated_at date range                              | (from:'2024-12-19T09:39:17.628Z',to:'2024-12-26T09:42:43.152Z')                                  |
| `created_by`                                                                                     | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Filter by multiple folder created by user names, comma separated                                 | riya,geeta                                                                                       |
| `limit`                                                                                          | *Optional[int]*                                                                                  | :heavy_minus_sign:                                                                               | Max number of result to return                                                                   | 10                                                                                               |
| `offset`                                                                                         | *Optional[int]*                                                                                  | :heavy_minus_sign:                                                                               | Distance from the beginning of the list of results                                               | 10                                                                                               |
| `sort`                                                                                           | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Sort the folders based on the fields                                                             | (id:asc),(name:asc)                                                                              |
| `retries`                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                 | :heavy_minus_sign:                                                                               | Configuration to override the default retry behavior of the client.                              |                                                                                                  |

### Response

**[models.FoldersList](../../models/folderslist.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Creates a new folder.

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateFolder" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/folders" -->
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

    res = ma_client.folders.create(workspace_id=4, project_id=4, name="Folder1", parent_folder_id=8043)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `name`                                                                                         | *str*                                                                                          | :heavy_check_mark:                                                                             | Folder Name                                                                                    | {<br/>"value": "Folder1"<br/>}                                                                 |
| `parent_folder_id`                                                                             | *OptionalNullable[int]*                                                                        | :heavy_minus_sign:                                                                             | Parent folder id                                                                               | {<br/>"value": 8024<br/>}                                                                      |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.FolderDetails](../../models/folderdetails.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## remove

Deletes given folders.

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteFolders" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/folders" -->
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

    ma_client.folders.remove(workspace_id=4, project_id=4, ids="1,2,3", check_dependency=True, remove_contents=True)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `ids`                                                                                          | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Filter by multiple folder ids, comma separated                                                 | 1,2,3                                                                                          |
| `check_dependency`                                                                             | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | Check for dependency before deleting the folder                                                | true                                                                                           |
| `remove_contents`                                                                              | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | Remove folder contents before deleting the folder                                              | true                                                                                           |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| errors.DeleteFoldersResponseBodyError1 | 400                                    | application/json                       |
| errors.DeleteFoldersResponseBodyError2 | 400                                    | application/json                       |
| errors.MammothAnalyticsDefaultError    | 4XX, 5XX                               | \*/\*                                  |

## update_resources

Move resources from/to folder.

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateFolderResources" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/folders" -->
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

    res = ma_client.folders.update_resources(workspace_id=4, project_id=4, patch=[
        {
            "op": models.FoldersPatchDataOperation.MOVE,
            "from_": [
                555,
            ],
            "path": 344,
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `patch`                                                                                        | List[[models.FoldersPatchData](../../models/folderspatchdata.md)]                              | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ObjectJobSchema](../../models/objectjobschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## get

Get details of a folder.

### Example Usage

<!-- UsageSnippet language="python" operationID="GetFolder" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/folders/{folder_id}" -->
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

    res = ma_client.folders.get(workspace_id=4, project_id=4, folder_id=4, fields="id,name")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      | Example                                                                                          |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `workspace_id`                                                                                   | *int*                                                                                            | :heavy_check_mark:                                                                               | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.   | 4                                                                                                |
| `project_id`                                                                                     | *int*                                                                                            | :heavy_check_mark:                                                                               | Project ID of the workspace                                                                      | 4                                                                                                |
| `folder_id`                                                                                      | *int*                                                                                            | :heavy_check_mark:                                                                               | ID of the folder                                                                                 | 4                                                                                                |
| `fields`                                                                                         | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Fields to be returned in a comma-separated format may include id, name, status_info, created_at. | id,name                                                                                          |
| `retries`                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                 | :heavy_minus_sign:                                                                               | Configuration to override the default retry behavior of the client.                              |                                                                                                  |

### Response

**[models.FolderDetails](../../models/folderdetails.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## delete

Deletes given folder along with all the files inside the folder.

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteFolder" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/folders/{folder_id}" -->
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

    ma_client.folders.delete(workspace_id=4, project_id=4, folder_id=4, check_dependency=True, remove_contents=True)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `folder_id`                                                                                    | *int*                                                                                          | :heavy_check_mark:                                                                             | ID of the folder                                                                               | 4                                                                                              |
| `check_dependency`                                                                             | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | Check for dependency before deleting the folder                                                | true                                                                                           |
| `remove_contents`                                                                              | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | Remove folder contents before deleting the folder                                              | true                                                                                           |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.DeleteFolderResponseBodyError1 | 400                                   | application/json                      |
| errors.DeleteFolderResponseBodyError2 | 400                                   | application/json                      |
| errors.MammothAnalyticsDefaultError   | 4XX, 5XX                              | \*/\*                                 |

## update

Updates the folder details with given information.

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateFolderDetails" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/folders/{folder_id}" -->
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

    res = ma_client.folders.update(workspace_id=4, project_id=4, folder_id=4, patch=[
        {
            "op": models.FolderPatchDataOperation.REPLACE,
            "path": models.FolderPatchDataPath.NAME,
            "value": "test",
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `folder_id`                                                                                    | *int*                                                                                          | :heavy_check_mark:                                                                             | ID of the folder                                                                               | 4                                                                                              |
| `patch`                                                                                        | List[[models.FolderPatchData](../../models/folderpatchdata.md)]                                | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.FolderDetails](../../models/folderdetails.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |