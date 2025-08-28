# GenerateAiData
(*generate_ai_data*)

## Overview

### Available Operations

* [preview](#preview) - Generate AI preview data for a dataview for the given sequence

## preview

Given the prompt, generate AI data againt a sequence number in the pipeline

### Example Usage

<!-- UsageSnippet language="python" operationID="Preview" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/data/generate" -->
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

    res = ma_client.generate_ai_data.preview(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, no_of_rows=10, prompt="Describe the nature of the data of each cell in the given columns", sequence=2, columns=[
        "column_1",
    ])

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
| `no_of_rows`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `prompt`                                                                                       | *str*                                                                                          | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `sequence`                                                                                     | *OptionalNullable[int]*                                                                        | :heavy_minus_sign:                                                                             | Sequence number of the dataview task                                                           | 2                                                                                              |
| `model_type`                                                                                   | [OptionalNullable[models.ModelType]](../../models/modeltype.md)                                | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `columns`                                                                                      | List[*str*]                                                                                    | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.PreviewResponse](../../models/previewresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.PreviewResponseBodyError1    | 400                                 | application/json                    |
| errors.PreviewResponseBodyError2    | 400                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |