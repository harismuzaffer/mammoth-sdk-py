# DataviewPipeline
(*dataview_pipeline*)

## Overview

### Available Operations

* [get](#get) - Get dataview pipeline information
* [edit](#edit) - Edit and perform bulk operations on a dataview pipeline

## get


        This endpoint fetches useful information of a dataview pipeline including some stats. This endpoint, representing a singular resource doesn't allow any filters.
        

### Example Usage

<!-- UsageSnippet language="python" operationID="GetPipeline" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/pipeline" -->
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

    res = ma_client.dataview_pipeline.get(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, fields="state, draft_mode")

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
| `fields`                                                                                       | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Fields to be returned in a comma-separated format. Check full mode for all fields.             | state, draft_mode                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.PipelineInfo](../../models/pipelineinfo.md)**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| errors.GetPipelineResponseBodyError1 | 400                                  | application/json                     |
| errors.GetPipelineResponseBodyError2 | 400                                  | application/json                     |
| errors.GetPipelineNotFoundError      | 404                                  | application/json                     |
| errors.MammothAnalyticsDefaultError  | 4XX, 5XX                             | \*/\*                                |

## edit


        This endpoint allows
        - Editing a pipeline. Supported operations are
          - Reorder
          - Reset
          - Run
          - Discard-changes
          - Set auto-run
        - Bulk operations on(items of) the pipeline
          - suspend
          - restore
          - discard
        

### Example Usage

<!-- UsageSnippet language="python" operationID="EditPipeline" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/pipeline" -->
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

    res = ma_client.dataview_pipeline.edit(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, patches=[
        {
            "op": models.PipelinePatchOp.COMMAND,
            "path": models.PipelinePatchPath.DISCARD_CHANGES,
            "value": None,
        },
    ], skip_validation=False, force_run=False)

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
| `patches`                                                                                      | List[[models.PipelinePatch](../../models/pipelinepatch.md)]                                    | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `skip_validation`                                                                              | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `force_run`                                                                                    | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.EditPipelineResponse](../../models/editpipelineresponse.md)**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.EditPipelineResponseBodyError1 | 400                                   | application/json                      |
| errors.EditPipelineResponseBodyError2 | 400                                   | application/json                      |
| errors.EditPipelineNotFoundError      | 404                                   | application/json                      |
| errors.MammothAnalyticsDefaultError   | 4XX, 5XX                              | \*/\*                                 |