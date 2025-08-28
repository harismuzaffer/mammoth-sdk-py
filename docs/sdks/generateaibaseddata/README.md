# GenerateAiBasedData
(*generate_ai_based_data*)

## Overview

### Available Operations

* [get_validation_info](#get_validation_info) - Get validation information

## get_validation_info


        This endpoint fetches validation information with regards to the external service used to generate the data e.g. limits for the Open AI key
        

### Example Usage

<!-- UsageSnippet language="python" operationID="GetValidationInfo" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/data/generate" -->
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

    res = ma_client.generate_ai_based_data.get_validation_info(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, sequence=2, validate_only=True)

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
| `sequence`                                                                                     | *OptionalNullable[int]*                                                                        | :heavy_minus_sign:                                                                             | Sequence number of the dataview task                                                           | 2                                                                                              |
| `validate_only`                                                                                | *OptionalNullable[bool]*                                                                       | :heavy_minus_sign:                                                                             | Validate AI generation for the view                                                            | true                                                                                           |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.GenAIValidationSpec](../../models/genaivalidationspec.md)**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| errors.GetValidationInfoResponseBodyError1 | 400                                        | application/json                           |
| errors.GetValidationInfoResponseBodyError2 | 400                                        | application/json                           |
| errors.MammothAnalyticsDefaultError        | 4XX, 5XX                                   | \*/\*                                      |