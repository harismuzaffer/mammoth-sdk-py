# DsConfigs
(*ds_configs*)

## Overview

### Available Operations

* [remove](#remove) - Delete ds config
* [update](#update) - Validate and get sample data
* [list](#list) - List ds configs
* [validate_and_fetch_data](#validate_and_fetch_data) - Validate and get sample data

## remove

Deletes ds config. Query parameters can be used to optimize the response.

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteDsConfig" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/connectors/{connector_key}/connections/{connection_key}/ds_configs/{ds_config_key}" -->
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

    ma_client.ds_configs.remove(workspace_id=4, project_id=4, connector_key="YmlncXVlcnk=", connection_key="kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8", ds_config_key="ytvudfx0e2w2wr2e1artrz1wtrn2wmgdyu7bgj4v")

    # Use the SDK ...

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

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.DeleteDsConfigResponseBodyError1 | 400                                     | application/json                        |
| errors.DeleteDsConfigResponseBodyError2 | 400                                     | application/json                        |
| errors.MammothAnalyticsDefaultError     | 4XX, 5XX                                | \*/\*                                   |

## update

Validates and gets the sample data for given details. Query parameters can be used to optimize the response.

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateDsConfigs" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/connectors/{connector_key}/connections/{connection_key}/ds_configs/{ds_config_key}" -->
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

    res = ma_client.ds_configs.update(workspace_id=4, project_id=4, connector_key="YmlncXVlcnk=", connection_key="kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8", ds_config_key="ytvudfx0e2w2wr2e1artrz1wtrn2wmgdyu7bgj4v", patch=[
        {
            "op": models.DsConfigPatchDataOperation.REPLACE,
            "path": models.DsConfigPatchDataPath.QUERY,
            "value": {
                "query": "SELECT * FROM \"ValidateCredentials\"",
                "ds_id": 67,
            },
        },
    ])

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
| `patch`                                                                                        | List[[models.DsConfigPatchData](../../models/dsconfigpatchdata.md)]                            | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[Any](../../models/.md)**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| errors.UpdateDsConfigsResponseBodyError1 | 400                                      | application/json                         |
| errors.UpdateDsConfigsResponseBodyError2 | 400                                      | application/json                         |
| errors.MammothAnalyticsDefaultError      | 4XX, 5XX                                 | \*/\*                                    |

## list

Returns list of ds configs. Query parameters can be used to optimize the response.

### Example Usage

<!-- UsageSnippet language="python" operationID="ListDsConfigs" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/connectors/{connector_key}/connections/{connection_key}/ds_configs" -->
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

    ma_client.ds_configs.list(workspace_id=4, project_id=4, connector_key="YmlncXVlcnk=", connection_key="kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8", fields="<value>")

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `connector_key`                                                                                | *str*                                                                                          | :heavy_check_mark:                                                                             | Encoded key of the connector                                                                   | YmlncXVlcnk=                                                                                   |
| `connection_key`                                                                               | *str*                                                                                          | :heavy_check_mark:                                                                             | Encoded key of the connection                                                                  | kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8                                                       |
| `fields`                                                                                       | *str*                                                                                          | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| errors.ListDsConfigsResponseBodyError1 | 400                                    | application/json                       |
| errors.ListDsConfigsResponseBodyError2 | 400                                    | application/json                       |
| errors.MammothAnalyticsDefaultError    | 4XX, 5XX                               | \*/\*                                  |

## validate_and_fetch_data

Validates and gets the sample data for given details. Query parameters can be used to optimize the response.

### Example Usage

<!-- UsageSnippet language="python" operationID="ValidateAndGetDsConfig" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/connectors/{connector_key}/connections/{connection_key}/ds_configs" -->
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

    res = ma_client.ds_configs.validate_and_fetch_data(workspace_id=4, project_id=4, connector_key="YmlncXVlcnk=", connection_key="kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8", profile="public", query="SELECT * FROM \"append_transforms\"", table="append_transforms", validate=True, data_sample=True, file_source="{\"value\":\"./sftp_test/08.12.21-RFIG.csv\"}")

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
| `profile`                                                                                      | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Profile of the selected connection                                                             | {<br/>"value": "public"<br/>}                                                                  |
| `query`                                                                                        | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Query to fetch data from cloud                                                                 | {<br/>"value": "SELECT * FROM \"base_templates\" limit 2"<br/>}                                |
| `table`                                                                                        | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Name of the Table                                                                              | {<br/>"value": "base_templates"<br/>}                                                          |
| `validate_`                                                                                    | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | Validate                                                                                       | {<br/>"value": true<br/>}                                                                      |
| `data_sample`                                                                                  | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | Sample data flag                                                                               | {<br/>"value": true<br/>}                                                                      |
| `file_source`                                                                                  | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Source path of the file                                                                        | {<br/>"value": "./sftp_test/08.12.21-RFIG.csv"<br/>}                                           |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[Any](../../models/.md)**

### Errors

| Error Type                                      | Status Code                                     | Content Type                                    |
| ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- |
| errors.ValidateAndGetDsConfigResponseBodyError1 | 400                                             | application/json                                |
| errors.ValidateAndGetDsConfigResponseBodyError2 | 400                                             | application/json                                |
| errors.MammothAnalyticsDefaultError             | 4XX, 5XX                                        | \*/\*                                           |