# Files
(*files*)

## Overview

### Available Operations

* [list](#list) - List files
* [create_dataset](#create_dataset) - Upload file or folder
* [remove](#remove) - Delete files
* [get](#get) - Get file details
* [delete](#delete) - Delete file
* [update_configs](#update_configs) - Updates the file configs

## list

Returns list of webhook details. Query parameters can be used to optimize the response.

### Example Usage

<!-- UsageSnippet language="python" operationID="ListFiles" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/files" -->
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

    res = ma_client.files.list(workspace_id=4, project_id=4, fields="id,name", id="1,2,3", name="file_name1,file_name2,file_name3", status="processing,action_needed", created_at="(from:'2023-12-19T09:39:17.628Z',to:'2023-12-26T09:42:43.152Z')", updated_at="(from:'2023-12-19T09:39:17.628Z',to:'2023-12-26T09:42:43.152Z')", limit=10, offset=10, sort="(id:asc),(name:asc)")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      | Example                                                                                          |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `workspace_id`                                                                                   | *int*                                                                                            | :heavy_check_mark:                                                                               | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.   | 4                                                                                                |
| `project_id`                                                                                     | *int*                                                                                            | :heavy_check_mark:                                                                               | Project ID of the workspace                                                                      | 4                                                                                                |
| `fields`                                                                                         | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Fields to be returned in a comma-separated format may include id, name, status_info, created_at. | id,name                                                                                          |
| `id`                                                                                             | *Optional[str]*                                                                                  | :heavy_minus_sign:                                                                               | Track multiple file ids, comma separated                                                         | 1,2,3                                                                                            |
| `name`                                                                                           | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Track multiple file names, comma separated                                                       | file_name1,file_name2,file_name3                                                                 |
| `status`                                                                                         | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Track multiple file statuses, comma separated                                                    | processing,action_needed                                                                         |
| `created_at`                                                                                     | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Track multiple files, which falls under created_at date range                                    | (from:'2023-12-19T09:39:17.628Z',to:'2023-12-26T09:42:43.152Z')                                  |
| `updated_at`                                                                                     | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Track multiple files, which falls under updated_at date range                                    | (from:'2023-12-19T09:39:17.628Z',to:'2023-12-26T09:42:43.152Z')                                  |
| `limit`                                                                                          | *Optional[int]*                                                                                  | :heavy_minus_sign:                                                                               | Max number of result to return                                                                   | 10                                                                                               |
| `offset`                                                                                         | *Optional[int]*                                                                                  | :heavy_minus_sign:                                                                               | Distance from the beginning of the list of results                                               | 10                                                                                               |
| `sort`                                                                                           | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Sort the files based on the fields                                                               | (id:asc),(name:asc)                                                                              |
| `retries`                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                 | :heavy_minus_sign:                                                                               | Configuration to override the default retry behavior of the client.                              |                                                                                                  |

### Response

**[models.FilesList](../../models/fileslist.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create_dataset

Upload file or folder to create a dataset

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateFileDataset" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/files" -->
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

    res = ma_client.files.create_dataset(workspace_id=4, project_id=4, folder_resource_id="label_123", append_to_ds_id=4, override_target_schema=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                      | Type                                                                                                                                           | Required                                                                                                                                       | Description                                                                                                                                    | Example                                                                                                                                        |
| ---------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                                                                 | *int*                                                                                                                                          | :heavy_check_mark:                                                                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.                                                 | 4                                                                                                                                              |
| `project_id`                                                                                                                                   | *int*                                                                                                                                          | :heavy_check_mark:                                                                                                                             | Project ID of the workspace                                                                                                                    | 4                                                                                                                                              |
| `folder_resource_id`                                                                                                                           | *OptionalNullable[str]*                                                                                                                        | :heavy_minus_sign:                                                                                                                             | Resource ID of the folder where the dataset is to be created                                                                                   | label_123                                                                                                                                      |
| `append_to_ds_id`                                                                                                                              | *OptionalNullable[int]*                                                                                                                        | :heavy_minus_sign:                                                                                                                             | Dataset ID to which the file is being appended                                                                                                 | 4                                                                                                                                              |
| `override_target_schema`                                                                                                                       | *OptionalNullable[bool]*                                                                                                                       | :heavy_minus_sign:                                                                                                                             | When appending to an existing dataset and this flag is set, the schema of the target dataset will be overridden by schema of the incoming data | false                                                                                                                                          |
| `files`                                                                                                                                        | List[[models.CreateFileDatasetFile](../../models/createfiledatasetfile.md)]                                                                    | :heavy_minus_sign:                                                                                                                             | N/A                                                                                                                                            |                                                                                                                                                |
| `retries`                                                                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                               | :heavy_minus_sign:                                                                                                                             | Configuration to override the default retry behavior of the client.                                                                            |                                                                                                                                                |

### Response

**[models.CreateFileDatasetResponse](../../models/createfiledatasetresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## remove

Deletes given files.

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteFiles" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/files" -->
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

    ma_client.files.remove(workspace_id=4, project_id=4, ids="1,2,3")

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `ids`                                                                                          | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Track multiple file ids, comma separated                                                       | 1,2,3                                                                                          |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| errors.DeleteFilesResponseBodyError1 | 400                                  | application/json                     |
| errors.DeleteFilesResponseBodyError2 | 400                                  | application/json                     |
| errors.MammothAnalyticsDefaultError  | 4XX, 5XX                             | \*/\*                                |

## get

Returns file details. Query parameters can be used to optimize the response.

### Example Usage

<!-- UsageSnippet language="python" operationID="GetFileDetails" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/files/{file_id}" -->
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

    res = ma_client.files.get(workspace_id=4, project_id=4, file_id=4, fields="id,name")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      | Example                                                                                          |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `workspace_id`                                                                                   | *int*                                                                                            | :heavy_check_mark:                                                                               | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.   | 4                                                                                                |
| `project_id`                                                                                     | *int*                                                                                            | :heavy_check_mark:                                                                               | Project ID of the workspace                                                                      | 4                                                                                                |
| `file_id`                                                                                        | *int*                                                                                            | :heavy_check_mark:                                                                               | ID of the file                                                                                   | 4                                                                                                |
| `fields`                                                                                         | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Fields to be returned in a comma-separated format may include id, name, status_info, created_at. | id,name                                                                                          |
| `retries`                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                 | :heavy_minus_sign:                                                                               | Configuration to override the default retry behavior of the client.                              |                                                                                                  |

### Response

**[models.FileDetails](../../models/filedetails.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## delete

Deletes given file.

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteFile" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/files/{file_id}" -->
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

    ma_client.files.delete(workspace_id=4, project_id=4, file_id=4)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `file_id`                                                                                      | *int*                                                                                          | :heavy_check_mark:                                                                             | ID of the file                                                                                 | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.DeleteFileResponseBodyError1 | 400                                 | application/json                    |
| errors.DeleteFileResponseBodyError2 | 400                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## update_configs

Updates the file details with given information.

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateFileConfigs" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/files/{file_id}" -->
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

    res = ma_client.files.update_configs(workspace_id=4, project_id=4, file_id=4, patch=[
        {
            "op": models.FilePatchDataOperation.REPLACE,
            "path": models.FilePatchDataPath.PASSWORD,
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
| `file_id`                                                                                      | *int*                                                                                          | :heavy_check_mark:                                                                             | ID of the file                                                                                 | 4                                                                                              |
| `patch`                                                                                        | List[[models.FilePatchData](../../models/filepatchdata.md)]                                    | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ObjectJobSchema](../../models/objectjobschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |