# QueryGen
(*query_gen*)

## Overview

### Available Operations

* [get_chat_status](#get_chat_status) - Get status
* [get_suggestion](#get_suggestion) - Generate query

## get_chat_status

Get status on chat generation

### Example Usage

<!-- UsageSnippet language="python" operationID="GetChatStatus" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/connectors/{connector_key}/connections/{connection_key}/chat" -->
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

    res = ma_client.query_gen.get_chat_status(workspace_id=4, project_id=4, connector_key="cG9zdGdyZXM=", connection_key="kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `connector_key`                                                                                | *str*                                                                                          | :heavy_check_mark:                                                                             | Encoded key of the Connector to work with                                                      | cG9zdGdyZXM=                                                                                   |
| `connection_key`                                                                               | *str*                                                                                          | :heavy_check_mark:                                                                             | Encoded key of the connection                                                                  | kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8                                                       |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.QueryGenerationStatus](../../models/querygenerationstatus.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| errors.GetChatStatusResponseBodyError1 | 400                                    | application/json                       |
| errors.GetChatStatusResponseBodyError2 | 400                                    | application/json                       |
| errors.GetChatStatusUnauthorizedError  | 401                                    | application/json                       |
| errors.MammothAnalyticsDefaultError    | 4XX, 5XX                               | \*/\*                                  |

## get_suggestion

Get query suggestion for the given data

### Example Usage

<!-- UsageSnippet language="python" operationID="GetQuerySuggestion" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/connectors/{connector_key}/connections/{connection_key}/chat" -->
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

    res = ma_client.query_gen.get_suggestion(workspace_id=4, project_id=4, connector_key="cG9zdGdyZXM=", connection_key="kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8", query="What is the total sales for the month of January?", reset_cache=True)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `connector_key`                                                                                | *str*                                                                                          | :heavy_check_mark:                                                                             | Encoded key of the Connector to work with                                                      | cG9zdGdyZXM=                                                                                   |
| `connection_key`                                                                               | *str*                                                                                          | :heavy_check_mark:                                                                             | Encoded key of the connection                                                                  | kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8                                                       |
| `query`                                                                                        | *str*                                                                                          | :heavy_check_mark:                                                                             | Intent                                                                                         |                                                                                                |
| `reset_cache`                                                                                  | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | Force Reset/regenerate cache. This will ignore any query request                               | true                                                                                           |
| `profile`                                                                                      | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | profile                                                                                        |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[Any](../../models/.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| errors.GetQuerySuggestionResponseBodyError1 | 400                                         | application/json                            |
| errors.GetQuerySuggestionResponseBodyError2 | 400                                         | application/json                            |
| errors.GetQuerySuggestionUnauthorizedError  | 401                                         | application/json                            |
| errors.MammothAnalyticsDefaultError         | 4XX, 5XX                                    | \*/\*                                       |