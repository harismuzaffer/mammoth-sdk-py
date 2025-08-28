# AppUsage
(*app_usage*)

## Overview

### Available Operations

* [get](#get) - Get app usage details

## get

Retrieve app usage and storage details for the workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="GetAppUsage" method="get" path="/workspaces/{workspace_id}/app-usage" -->
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

    res = ma_client.app_usage.get(workspace_id=4, fields="current_storage,max_storage_allowed")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `fields`                                                                                       | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Fields to return. Can be (current_storage,max_storage_allowed)                                 | current_storage,max_storage_allowed                                                            |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.AppUsageSchema](../../models/appusageschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |