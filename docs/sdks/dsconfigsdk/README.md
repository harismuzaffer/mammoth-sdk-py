# DsConfigSDK
(*ds_config*)

## Overview

### Available Operations

* [get](#get) - Get ds config details
* [delete](#delete) - Delete ds configs

## get

Returns ds config details. Query parameters can be used to optimize the response.

### Example Usage

<!-- UsageSnippet language="python" operationID="GetDsConfig" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/connectors/{connector_key}/connections/{connection_key}/ds_configs/{ds_config_key}" -->
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

    res = ma_client.ds_config.get(workspace_id=4, project_id=4, connector_key="YmlncXVlcnk=", connection_key="kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8", ds_config_key="ytvudfx0e2w2wr2e1artrz1wtrn2wmgdyu7bgj4v")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `connector_key`                                                                                | *str*                                                                                          | :heavy_check_mark:                                                                             | Encoded key of the connector                                                                   | YmlncXVlcnk=                                                                                   |
| `connection_key`                                                                               | *str*                                                                                          | :heavy_check_mark:                                                                             | Encoded key of the connection                                                                  | kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8                                                       |
| `ds_config_key`                                                                                | *str*                                                                                          | :heavy_check_mark:                                                                             | Key for the ds_config                                                                          | ytvudfx0e2w2wr2e1artrz1wtrn2wmgdyu7bgj4v                                                       |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.DsConfigDetails](../../models/dsconfigdetails.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## delete

Deletes list of ds configs. Query parameters can be used to optimize the response.

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteDsConfigs" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/connectors/{connector_key}/connections/{connection_key}/ds_configs" -->
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

    ma_client.ds_config.delete(workspace_id=4, project_id=4, connector_key="YmlncXVlcnk=", connection_key="kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8", config_ids="<value>")

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `connector_key`                                                                                | *str*                                                                                          | :heavy_check_mark:                                                                             | Encoded key of the connector                                                                   | YmlncXVlcnk=                                                                                   |
| `connection_key`                                                                               | *str*                                                                                          | :heavy_check_mark:                                                                             | Encoded key of the connection                                                                  | kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8                                                       |
| `config_ids`                                                                                   | *str*                                                                                          | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| errors.DeleteDsConfigsResponseBodyError1 | 400                                      | application/json                         |
| errors.DeleteDsConfigsResponseBodyError2 | 400                                      | application/json                         |
| errors.MammothAnalyticsDefaultError      | 4XX, 5XX                                 | \*/\*                                    |