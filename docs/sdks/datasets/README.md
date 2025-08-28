# Datasets
(*datasets*)

## Overview

### Available Operations

* [list](#list) - Get list of datasets
* [create](#create) - Create dataset
* [remove](#remove) - Delete multiple datasets
* [rename](#rename) - Update datasets name
* [get](#get) - Get dataset details
* [delete](#delete) - Delete dataset
* [update](#update) - Update dataset
* [get_data](#get_data) - Get dataset data

## list

Returns list of datasets in given project. Query parameters can be used to optimize the response.

### Example Usage

<!-- UsageSnippet language="python" operationID="GetDatasets" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets" -->
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

    res = ma_client.datasets.list(project_id=4, workspace_id=4, fields="id,name", id="1,2,3", name="ds_name1,ds_name2,ds_name3", created_at="(from:'2023-12-19T09:39:17.628Z',to:'2023-12-26T09:42:43.152Z')", updated_at="(from:'2023-12-18T09:39:17.628Z',to:'2023-12-17T09:42:43.152Z')", created_by="riya,shriya", source_type="file,cloud,sketch", status="ready,error,processing", limit=10, offset=10, sort="(id:asc),(name:asc)")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             | Example                                                                                                 |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `project_id`                                                                                            | *int*                                                                                                   | :heavy_check_mark:                                                                                      | Project ID of the workspace                                                                             | 4                                                                                                       |
| `workspace_id`                                                                                          | *int*                                                                                                   | :heavy_check_mark:                                                                                      | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.          | 4                                                                                                       |
| `fields`                                                                                                | *OptionalNullable[str]*                                                                                 | :heavy_minus_sign:                                                                                      | Fields to be returned in a comma-separated format may include id, name, owner_workspace_id, updated_at. | id,name                                                                                                 |
| `id`                                                                                                    | *Optional[str]*                                                                                         | :heavy_minus_sign:                                                                                      | Track multiple dataset ids, comma separated                                                             | 1,2,3                                                                                                   |
| `name`                                                                                                  | *OptionalNullable[str]*                                                                                 | :heavy_minus_sign:                                                                                      | Track multiple dataset names, comma separated                                                           | ds_name1,ds_name2,ds_name3                                                                              |
| `created_at`                                                                                            | *OptionalNullable[str]*                                                                                 | :heavy_minus_sign:                                                                                      | Track multiple dataset, which falls under created_at date range                                         | (from:'2023-12-19T09:39:17.628Z',to:'2023-12-26T09:42:43.152Z')                                         |
| `updated_at`                                                                                            | *OptionalNullable[str]*                                                                                 | :heavy_minus_sign:                                                                                      | Track multiple dataset, which falls under updated_at date range                                         | (from:'2023-12-18T09:39:17.628Z',to:'2023-12-17T09:42:43.152Z')                                         |
| `created_by`                                                                                            | *OptionalNullable[str]*                                                                                 | :heavy_minus_sign:                                                                                      | Track multiple dataset created by, comma separated                                                      | riya,shriya                                                                                             |
| `source_type`                                                                                           | *OptionalNullable[str]*                                                                                 | :heavy_minus_sign:                                                                                      | Track multiple dataset source type, comma separated                                                     | file,cloud,sketch                                                                                       |
| `status`                                                                                                | *OptionalNullable[str]*                                                                                 | :heavy_minus_sign:                                                                                      | Track multiple dataset status, comma separated                                                          | ready,error,processing                                                                                  |
| `limit`                                                                                                 | *Optional[int]*                                                                                         | :heavy_minus_sign:                                                                                      | Max number of result to return                                                                          | 10                                                                                                      |
| `offset`                                                                                                | *Optional[int]*                                                                                         | :heavy_minus_sign:                                                                                      | Distance from the beginning of the list of results                                                      | 10                                                                                                      |
| `sort`                                                                                                  | *OptionalNullable[str]*                                                                                 | :heavy_minus_sign:                                                                                      | Sort the datasets based on the fields                                                                   | (id:asc),(name:asc)                                                                                     |
| `retries`                                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                        | :heavy_minus_sign:                                                                                      | Configuration to override the default retry behavior of the client.                                     |                                                                                                         |

### Response

**[models.DatasetsList](../../models/datasetslist.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Create datasets

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateDatasets" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/datasets" -->
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

    res = ma_client.datasets.create(workspace_id=4, project_id=4, ds_creation_type=models.DsCreationType.WEBURL, dataset_spec={
        "url": "https://www.google.com",
    }, folder_resource_id=None)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `ds_creation_type`                                                                             | [models.DsCreationType](../../models/dscreationtype.md)                                        | :heavy_check_mark:                                                                             | Dataset Creation Type                                                                          | {<br/>"summary": "Sample Dataset Creation Type",<br/>"value": "sketch"<br/>}                   |
| `dataset_spec`                                                                                 | [models.DatasetSpec](../../models/datasetspec.md)                                              | :heavy_check_mark:                                                                             | Dataset Specification                                                                          |                                                                                                |
| `folder_resource_id`                                                                           | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Folder Resource ID                                                                             | {<br/>"summary": "Folder resource id",<br/>"value": "folder_1"<br/>}                           |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[Any](../../models/.md)**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| errors.CreateDatasetsBadRequestError | 400                                  | application/json                     |
| errors.MammothAnalyticsDefaultError  | 4XX, 5XX                             | \*/\*                                |

## remove

Deletes multiple datasets and its associated data.

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteDatasets" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/datasets" -->
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

    ma_client.datasets.remove(workspace_id=4, project_id=4, ids="1,2,3")

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `ids`                                                                                          | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Track multiple dataset ids, comma separated                                                    | 1,2,3                                                                                          |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| errors.DeleteDatasetsBadRequestError | 400                                  | application/json                     |
| errors.MammothAnalyticsDefaultError  | 4XX, 5XX                             | \*/\*                                |

## rename

Update the name of multiple datasets

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateDatasets" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/datasets" -->
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

    res = ma_client.datasets.rename(workspace_id=4, project_id=4, patch={
        "op": "replace",
        "path": "name",
        "value": {
            "23": "test",
            "24": "test2",
        },
    }, validation_only=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `patch`                                                                                        | [models.DatasetsPatchOperation](../../models/datasetspatchoperation.md)                        | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `validation_only`                                                                              | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[Any](../../models/.md)**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| errors.UpdateDatasetsBadRequestError | 400                                  | application/json                     |
| errors.MammothAnalyticsDefaultError  | 4XX, 5XX                             | \*/\*                                |

## get

Returns dataset details. Query parameters can be used to optimize the response.

### Example Usage

<!-- UsageSnippet language="python" operationID="GetDataset" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}" -->
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

    res = ma_client.datasets.get(workspace_id=4, project_id=4, dataset_id=121, fields="id,name")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             | Example                                                                                                 |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                          | *int*                                                                                                   | :heavy_check_mark:                                                                                      | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.          | 4                                                                                                       |
| `project_id`                                                                                            | *int*                                                                                                   | :heavy_check_mark:                                                                                      | Project ID of the workspace                                                                             | 4                                                                                                       |
| `dataset_id`                                                                                            | *int*                                                                                                   | :heavy_check_mark:                                                                                      | Id of the dataset                                                                                       | 121                                                                                                     |
| `fields`                                                                                                | *OptionalNullable[str]*                                                                                 | :heavy_minus_sign:                                                                                      | Fields to be returned in a comma-separated format may include id, name, owner_workspace_id, updated_at. | id,name                                                                                                 |
| `retries`                                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                        | :heavy_minus_sign:                                                                                      | Configuration to override the default retry behavior of the client.                                     |                                                                                                         |

### Response

**[models.DatasetDetails](../../models/datasetdetails.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## delete

Deletes the dataset and its associated data.

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteDataset" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}" -->
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

    ma_client.datasets.delete(workspace_id=4, project_id=4, dataset_id=121)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.DeleteDatasetBadRequestError | 400                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## update

Update the dataset

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateDataset" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}" -->
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

    res = ma_client.datasets.update(workspace_id=4, project_id=4, dataset_id=121, patch={
        "op": models.DatasetPatchOperationOp.REPLACE,
        "path": models.DatasetPatchOperationPath.NAME,
        "value": "test",
    }, validation_only=False, skip_dependency_validation=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `patch`                                                                                        | [models.DatasetPatchOperation](../../models/datasetpatchoperation.md)                          | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `validation_only`                                                                              | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `skip_dependency_validation`                                                                   | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[Any](../../models/.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.UpdateDatasetBadRequestError | 400                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## get_data

Get the given dataset data

### Example Usage

<!-- UsageSnippet language="python" operationID="GetDatasetData" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/data" -->
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

    res = ma_client.datasets.get_data(workspace_id=839020, project_id=218920, dataset_id=892144, limit=100, offset=0)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `workspace_id`                                                      | *int*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `project_id`                                                        | *int*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `dataset_id`                                                        | *int*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `columns`                                                           | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | N/A                                                                 |
| `limit`                                                             | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `offset`                                                            | *Optional[int]*                                                     | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[Any](../../models/.md)**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| errors.GetDatasetDataBadRequestError | 400                                  | application/json                     |
| errors.MammothAnalyticsDefaultError  | 4XX, 5XX                             | \*/\*                                |