# Batches
(*batches*)

## Overview

### Available Operations

* [list](#list) - List batches
* [create](#create) - Create batch
* [remove](#remove) - Delete multiple batches
* [update](#update) - Update batches
* [get](#get) - List batches
* [delete](#delete) - Delete batch

## list

List batches and their details.

### Example Usage

<!-- UsageSnippet language="python" operationID="GetBatches" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/batches" -->
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

    res = ma_client.batches.list(workspace_id=4, project_id=4, dataset_id=121, fields="id,name", id="1,2,3", created_at="(from:'2023-12-19T09:39:18.628Z',to:'2023-12-26T10:42:43.152Z')", status="active,suspended", row_count="10,25,3", limit=10, offset=10, sort="(id:asc),(state:asc)")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `fields`                                                                                       | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Fields to be returned in a comma-separated format may include id, name, status, created_at.    | id,name                                                                                        |
| `id`                                                                                           | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Track multiple batch ids, comma separated                                                      | 1,2,3                                                                                          |
| `created_at`                                                                                   | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Track multiple batches, which falls under created_at date range                                | (from:'2023-12-19T09:39:18.628Z',to:'2023-12-26T10:42:43.152Z')                                |
| `status`                                                                                       | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Track multiple batch state, comma separated                                                    | active,suspended                                                                               |
| `row_count`                                                                                    | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Track multiple batch row counts, comma separated                                               | 10,25,3                                                                                        |
| `limit`                                                                                        | *Optional[int]*                                                                                | :heavy_minus_sign:                                                                             | Max number of result to return                                                                 | 10                                                                                             |
| `offset`                                                                                       | *Optional[int]*                                                                                | :heavy_minus_sign:                                                                             | Distance from the beginning of the list of results                                             | 10                                                                                             |
| `sort`                                                                                         | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Sort the batches based on the fields                                                           | (id:asc),(state:asc)                                                                           |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.BatchesList](../../models/batcheslist.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.GetBatchesBadRequestError    | 400                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Create a new batch through combine another datasets.

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateBatch" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/batches" -->
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

    res = ma_client.batches.create(workspace_id=4, project_id=4, dataset_id=121, source_id=239169, mapping=[
        {
            "destination_c_id": "c_id",
            "source_c_id": "c_id",
            "expected_destination_c_type": models.ColumnIDMappingExpectedDestinationCType.TEXT,
        },
    ], validate_only=False, delete_source_ds=False, new_ds_details={
        "name": "Batch Dataset",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `source_id`                                                                                    | *int*                                                                                          | :heavy_check_mark:                                                                             | Source dataset id                                                                              | {<br/>"value": 239169<br/>}                                                                    |
| `mapping`                                                                                      | [models.Mapping](../../models/mapping.md)                                                      | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `validate_only`                                                                                | *bool*                                                                                         | :heavy_check_mark:                                                                             | Validation required                                                                            | {<br/>"value": true<br/>}                                                                      |
| `delete_source_ds`                                                                             | *bool*                                                                                         | :heavy_check_mark:                                                                             | Delete source dataset                                                                          | {<br/>"value": false<br/>}                                                                     |
| `new_ds_details`                                                                               | [OptionalNullable[models.NewDsDetails]](../../models/newdsdetails.md)                          | :heavy_minus_sign:                                                                             | New dataset details                                                                            | {<br/>"value": {<br/>"name": "new_dataset_name"<br/>}<br/>}                                    |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.CreateBatchResponse](../../models/createbatchresponse.md)**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| errors.CreateBatchResponseBodyError1 | 400                                  | application/json                     |
| errors.CreateBatchResponseBodyError2 | 400                                  | application/json                     |
| errors.MammothAnalyticsDefaultError  | 4XX, 5XX                             | \*/\*                                |

## remove

Deletes multiple batches and its associated data.

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteBatches" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/batches" -->
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

    res = ma_client.batches.remove(workspace_id=4, project_id=4, dataset_id=121, ids="1,2,3")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `ids`                                                                                          | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Track multiple dataset ids, comma separated                                                    | 1,2,3                                                                                          |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ObjectJobSchema](../../models/objectjobschema.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| errors.DeleteBatchesResponseBodyError1 | 400                                    | application/json                       |
| errors.DeleteBatchesResponseBodyError2 | 400                                    | application/json                       |
| errors.MammothAnalyticsDefaultError    | 4XX, 5XX                               | \*/\*                                  |

## update

Update batches state.

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateBatches" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/batches" -->
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

    res = ma_client.batches.update(workspace_id=4, project_id=4, dataset_id=121, patch={
        "op": models.BatchesPatchOperationOp.REPLACE,
        "path": models.BatchesPatchOperationPath.BATCHES,
        "value": {
            "suspend": [
                1,
                2,
                8,
            ],
            "restore": [
                4,
                5,
                7,
            ],
        },
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `patch`                                                                                        | [models.BatchesPatchOperation](../../models/batchespatchoperation.md)                          | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ObjectJobSchema](../../models/objectjobschema.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| errors.UpdateBatchesResponseBodyError1 | 400                                    | application/json                       |
| errors.UpdateBatchesResponseBodyError2 | 400                                    | application/json                       |
| errors.MammothAnalyticsDefaultError    | 4XX, 5XX                               | \*/\*                                  |

## get

List batches and their details.

### Example Usage

<!-- UsageSnippet language="python" operationID="GetBatch" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/batches/{batch_id}" -->
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

    res = ma_client.batches.get(workspace_id=4, project_id=4, dataset_id=121, batch_id=121, fields="id,name")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `batch_id`                                                                                     | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the batch                                                                                | 121                                                                                            |
| `fields`                                                                                       | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Fields to be returned in a comma-separated format may include id, name, status, created_at.    | id,name                                                                                        |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.BatchDetails](../../models/batchdetails.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.GetBatchBadRequestError      | 400                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## delete

Deletes the batch and its associated data.

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteBatch" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/batches/{batch_id}" -->
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

    res = ma_client.batches.delete(workspace_id=4, project_id=4, dataset_id=121, batch_id=121)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `batch_id`                                                                                     | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ObjectJobSchema](../../models/objectjobschema.md)**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| errors.DeleteBatchResponseBodyError1 | 400                                  | application/json                     |
| errors.DeleteBatchResponseBodyError2 | 400                                  | application/json                     |
| errors.MammothAnalyticsDefaultError  | 4XX, 5XX                             | \*/\*                                |