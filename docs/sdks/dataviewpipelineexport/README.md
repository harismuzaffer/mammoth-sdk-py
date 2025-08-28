# DataviewPipelineExport
(*dataview_pipeline_export*)

## Overview

### Available Operations

* [delete](#delete) - Delete an export

## delete

Deletes a pipeline export 

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteExport" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/pipeline/exports/{export_id}" -->
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

    res = ma_client.dataview_pipeline_export.delete(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, export_id=121, skip_validation=False)

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
| `export_id`                                                                                    | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of a pipeline export                                                                        | 121                                                                                            |
| `skip_validation`                                                                              | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.DeleteExportResponse](../../models/deleteexportresponse.md)**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.DeleteExportResponseBodyError1 | 400                                   | application/json                      |
| errors.DeleteExportResponseBodyError2 | 400                                   | application/json                      |
| errors.DeleteExportNotFoundError      | 404                                   | application/json                      |
| errors.MammothAnalyticsDefaultError   | 4XX, 5XX                              | \*/\*                                 |