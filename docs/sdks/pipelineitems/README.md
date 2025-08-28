# PipelineItems
(*pipeline_items*)

## Overview

### Available Operations

* [get](#get) - Get dataview pipeline items

## get


        This endpoint gives information about items in the pipeline. Currently items in the pipeline can be
        either a Task or an Export. See `datviews/{<id>}/tasks` and `dataviews/{<id>}/exports` APIs for more information.
        

### Example Usage

<!-- UsageSnippet language="python" operationID="GetPipelineItems" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/pipeline/items" -->
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

    res = ma_client.pipeline_items.get(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, fields="sequence, status", limit=10, offset=10, sort="(id:asc)", sequence=2, status=models.GetPipelineItemsFilterByStatus.ADDED)

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
| `fields`                                                                                                  | *Optional[str]*                                                                                           | :heavy_minus_sign:                                                                                        | Fields to be returned in a comma-separated format. Check full mode for all fields.                        | sequence, status                                                                                          |
| `limit`                                                                                                   | *Optional[int]*                                                                                           | :heavy_minus_sign:                                                                                        | Max number of result to return                                                                            | 10                                                                                                        |
| `offset`                                                                                                  | *Optional[int]*                                                                                           | :heavy_minus_sign:                                                                                        | Distance from the beginning of the list of results                                                        | 10                                                                                                        |
| `sort`                                                                                                    | *Optional[str]*                                                                                           | :heavy_minus_sign:                                                                                        | Returned results are sorted by the combination of the given fields.                                       | (id:asc)                                                                                                  |
| `sequence`                                                                                                | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Returns all items where sequence matches the given value                                                  | 2                                                                                                         |
| `status`                                                                                                  | [OptionalNullable[models.GetPipelineItemsFilterByStatus]](../../models/getpipelineitemsfilterbystatus.md) | :heavy_minus_sign:                                                                                        | Returns all items where status matches the given value                                                    | added                                                                                                     |
| `retries`                                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                          | :heavy_minus_sign:                                                                                        | Configuration to override the default retry behavior of the client.                                       |                                                                                                           |

### Response

**[models.PipelineItemsPaginated](../../models/pipelineitemspaginated.md)**

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| errors.GetPipelineItemsResponseBodyError1 | 400                                       | application/json                          |
| errors.GetPipelineItemsResponseBodyError2 | 400                                       | application/json                          |
| errors.GetPipelineItemsUnauthorizedError  | 401                                       | application/json                          |
| errors.GetPipelineItemsNotFoundError      | 404                                       | application/json                          |
| errors.MammothAnalyticsDefaultError       | 4XX, 5XX                                  | \*/\*                                     |