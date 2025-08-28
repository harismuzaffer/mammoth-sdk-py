# GenerateDataBasedOnAI
(*generate_data_based_on_ai*)

## Overview

### Available Operations

* [ai_suggestions](#ai_suggestions) - Generate AI-based Suggestions for Dataview

## ai_suggestions

Given the prompt, generate AI data againt a sequence number in the pipeline

### Example Usage

<!-- UsageSnippet language="python" operationID="AiSuggestions" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/suggestions" -->
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

    res = ma_client.generate_data_based_on_ai.ai_suggestions(workspace_id=4, project_id=4, dataset_id=121, suggestion_type=models.SuggestionType.EXTRACT_TEXT, params={
        "column_name": "comments",
        "sequence_number": 1,
        "prompt": "Extract all mentions of product issues",
        "edit_regex": None,
    }, dataview_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `suggestion_type`                                                                              | [models.SuggestionType](../../models/suggestiontype.md)                                        | :heavy_check_mark:                                                                             | Type of operation (extraction or conditional filtering)                                        |                                                                                                |
| `params`                                                                                       | [models.Params](../../models/params.md)                                                        | :heavy_check_mark:                                                                             | Encapsulated parameters for the operation                                                      |                                                                                                |
| `dataview_id`                                                                                  | *Optional[int]*                                                                                | :heavy_minus_sign:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.AiSuggestionsResponse](../../models/aisuggestionsresponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| errors.AiSuggestionsResponseBodyError1 | 400                                    | application/json                       |
| errors.AiSuggestionsResponseBodyError2 | 400                                    | application/json                       |
| errors.MammothAnalyticsDefaultError    | 4XX, 5XX                               | \*/\*                                  |