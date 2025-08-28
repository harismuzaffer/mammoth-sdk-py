# DataviewPipelineTasks
(*dataview_pipeline_tasks*)

## Overview

### Available Operations

* [get_pipeline_tasks](#get_pipeline_tasks) - Get dataview pipeline tasks information
* [add](#add) - Add a task in the pipeline
* [get](#get) - Get dataview pipeline task information
* [delete](#delete) - Delete a task
* [edit](#edit) - Edit a dataview pipeline task

## get_pipeline_tasks


        This endpoint fetches tasks information of tasks in a dataview pipeline.
        

### Example Usage

<!-- UsageSnippet language="python" operationID="GetPipelineTasks" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/pipeline/tasks" -->
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

    res = ma_client.dataview_pipeline_tasks.get_pipeline_tasks(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, fields="sequence,status", limit=10, offset=10, sort="(id:asc)", sequence=2, status=models.GetPipelineTasksFilterByStatus.EXECUTED)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                 | Type                                                                                                      | Required                                                                                                  | Description                                                                                               | Example                                                                                                   |
| --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                            | *int*                                                                                                     | :heavy_check_mark:                                                                                        | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.            | 4                                                                                                         |
| `project_id`                                                                                              | *int*                                                                                                     | :heavy_check_mark:                                                                                        | Project ID of the workspace                                                                               | 4                                                                                                         |
| `dataset_id`                                                                                              | *int*                                                                                                     | :heavy_check_mark:                                                                                        | Id of the dataset                                                                                         | 121                                                                                                       |
| `dataview_id`                                                                                             | *int*                                                                                                     | :heavy_check_mark:                                                                                        | Dataview ID of the dataset                                                                                | 4                                                                                                         |
| `fields`                                                                                                  | *Optional[str]*                                                                                           | :heavy_minus_sign:                                                                                        | Fields to be returned in a comma-separated format. Check full mode for all fields.                        | sequence,status                                                                                           |
| `limit`                                                                                                   | *Optional[int]*                                                                                           | :heavy_minus_sign:                                                                                        | Max number of result to return                                                                            | 10                                                                                                        |
| `offset`                                                                                                  | *Optional[int]*                                                                                           | :heavy_minus_sign:                                                                                        | Distance from the beginning of the list of results                                                        | 10                                                                                                        |
| `sort`                                                                                                    | *Optional[str]*                                                                                           | :heavy_minus_sign:                                                                                        | Returned results are sorted by the combination of the given fields.                                       | (id:asc)                                                                                                  |
| `sequence`                                                                                                | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Returns all tasks where sequence matches the given value                                                  | 2                                                                                                         |
| `status`                                                                                                  | [OptionalNullable[models.GetPipelineTasksFilterByStatus]](../../models/getpipelinetasksfilterbystatus.md) | :heavy_minus_sign:                                                                                        | Returns all tasks where status matches the given value                                                    | executed                                                                                                  |
| `retries`                                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                          | :heavy_minus_sign:                                                                                        | Configuration to override the default retry behavior of the client.                                       |                                                                                                           |

### Response

**[models.PipelineTasksPaginated](../../models/pipelinetaskspaginated.md)**

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| errors.GetPipelineTasksResponseBodyError1 | 400                                       | application/json                          |
| errors.GetPipelineTasksResponseBodyError2 | 400                                       | application/json                          |
| errors.MammothAnalyticsDefaultError       | 4XX, 5XX                                  | \*/\*                                     |

## add

add a new transformation to the dataview. This transformation gets added as a task in the dataview pipeline

### Example Usage

<!-- UsageSnippet language="python" operationID="AddTask" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/pipeline/tasks" -->
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

    res = ma_client.dataview_pipeline_tasks.add(workspace_id=4, project_id=4, dataset_id=121, dataview_id_param=4, dataview_id=2311, sequence_number=13, condition=None)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `dataview_id_param`                                                                            | *int*                                                                                          | :heavy_check_mark:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `dataview_id`                                                                                  | *int*                                                                                          | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `sequence_number`                                                                              | *OptionalNullable[int]*                                                                        | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `condition`                                                                                    | [OptionalNullable[models.AddTaskSpecCONDITION]](../../models/addtaskspeccondition.md)          | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.AddTaskResponse](../../models/addtaskresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.AddTaskResponseBodyError1    | 400                                 | application/json                    |
| errors.AddTaskResponseBodyError2    | 400                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## get


        This endpoint fetches information of a task in a dataview pipeline.
        

### Example Usage

<!-- UsageSnippet language="python" operationID="GetPipelineTask" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/pipeline/tasks/{task_id}" -->
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

    res = ma_client.dataview_pipeline_tasks.get(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, task_id=121, fields="sequence,status")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `dataview_id`                                                                                  | *int*                                                                                          | :heavy_check_mark:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `task_id`                                                                                      | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of a pipeline task                                                                          | 121                                                                                            |
| `fields`                                                                                       | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Fields to be returned in a comma-separated format. Check full mode for all fields.             | sequence,status                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ItemTaskInfo](../../models/itemtaskinfo.md)**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| errors.GetPipelineTaskResponseBodyError1 | 400                                      | application/json                         |
| errors.GetPipelineTaskResponseBodyError2 | 400                                      | application/json                         |
| errors.GetPipelineTaskNotFoundError      | 404                                      | application/json                         |
| errors.MammothAnalyticsDefaultError      | 4XX, 5XX                                 | \*/\*                                    |

## delete

Deletes a pipeline task 

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteTask" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/pipeline/tasks/{task_id}" -->
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

    res = ma_client.dataview_pipeline_tasks.delete(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, task_id=121, skip_validation=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `dataview_id`                                                                                  | *int*                                                                                          | :heavy_check_mark:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `task_id`                                                                                      | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of a pipeline task                                                                          | 121                                                                                            |
| `skip_validation`                                                                              | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.DeleteTaskResponse](../../models/deletetaskresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.DeleteTaskResponseBodyError1 | 400                                 | application/json                    |
| errors.DeleteTaskResponseBodyError2 | 400                                 | application/json                    |
| errors.DeleteTaskNotFoundError      | 404                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## edit

Modify a task, e.g. the params, the display_info(e.g. note), status(e.g. suspend a task)

### Example Usage

<!-- UsageSnippet language="python" operationID="EditTask" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/pipeline/tasks/{task_id}" -->
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

    res = ma_client.dataview_pipeline_tasks.edit(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, task_id=121, patches=[
        {
            "op": models.ItemTaskPatchOp.COMMAND,
            "path": models.ItemTaskPatchPath.SUSPEND,
            "value": None,
        },
    ], skip_validation=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `dataview_id`                                                                                  | *int*                                                                                          | :heavy_check_mark:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `task_id`                                                                                      | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of a pipeline task                                                                          | 121                                                                                            |
| `patches`                                                                                      | List[[models.ItemTaskPatch](../../models/itemtaskpatch.md)]                                    | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `skip_validation`                                                                              | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.EditTaskResponse](../../models/edittaskresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.EditTaskResponseBodyError1   | 400                                 | application/json                    |
| errors.EditTaskResponseBodyError2   | 400                                 | application/json                    |
| errors.EditTaskNotFoundError        | 404                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |