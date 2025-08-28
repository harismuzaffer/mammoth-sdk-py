# SQLGeneration
(*sql_generation*)

## Overview

### Available Operations

* [generate_sql](#generate_sql) - Generate SQL query based on intent

## generate_sql

Given the intent, generate SQL query for a sequence number in the pipeline

### Example Usage

<!-- UsageSnippet language="python" operationID="GenerateSql" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/sql_generation" -->
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

    res = ma_client.sql_generation.generate_sql(workspace_id=4, project_id=4, dataset_id=121, params={
        "sequence_number": 1,
        "intent": "Get all customers who made purchases in the last month",
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
| `params`                                                                                       | [models.SQLGenerationParams](../../models/sqlgenerationparams.md)                              | :heavy_check_mark:                                                                             | Encapsulated SQL generation parameters                                                         |                                                                                                |
| `dataview_id`                                                                                  | *Optional[int]*                                                                                | :heavy_minus_sign:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.GenerateSQLResponse](../../models/generatesqlresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.GenerateSQLUnauthorizedError | 401                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |