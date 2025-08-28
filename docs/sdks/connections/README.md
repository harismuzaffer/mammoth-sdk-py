# Connections
(*connections*)

## Overview

### Available Operations

* [get](#get) - Get Connection
* [delete](#delete) - Delete Connection
* [update](#update) - Update Connection
* [list](#list) - List Connections
* [create](#create) - Create Connection

## get

Get connection for given connector using the connection key

### Example Usage

<!-- UsageSnippet language="python" operationID="GetConnection" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/connectors/{connector_key}/connections/{connection_key}" -->
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

    res = ma_client.connections.get(workspace_id=4, project_id=4, connector_key="cG9zdGdyZXM=", connection_key="kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8", concern=models.ConcernType.PROFILES, profile="api", is_export=False)

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
| `concern`                                                                                      | [OptionalNullable[models.ConcernType]](../../models/concerntype.md)                            | :heavy_minus_sign:                                                                             | Concern type                                                                                   | data                                                                                           |
| `profile`                                                                                      | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Profile type                                                                                   | api                                                                                            |
| `is_export`                                                                                    | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | Is export type                                                                                 | false                                                                                          |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[Any](../../models/.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| errors.GetConnectionResponseBodyError1 | 400                                    | application/json                       |
| errors.GetConnectionResponseBodyError2 | 400                                    | application/json                       |
| errors.GetConnectionUnauthorizedError  | 401                                    | application/json                       |
| errors.MammothAnalyticsDefaultError    | 4XX, 5XX                               | \*/\*                                  |

## delete

Delete connection for given connector using the connection key

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteConnection" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/connectors/{connector_key}/connections/{connection_key}" -->
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

    ma_client.connections.delete(workspace_id=4, project_id=4, connector_key="cG9zdGdyZXM=", connection_key="kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8", is_export=False)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `connector_key`                                                                                | *str*                                                                                          | :heavy_check_mark:                                                                             | Encoded key of the Connector to work with                                                      | cG9zdGdyZXM=                                                                                   |
| `connection_key`                                                                               | *str*                                                                                          | :heavy_check_mark:                                                                             | Encoded key of the connection                                                                  | kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8                                                       |
| `is_export`                                                                                    | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | Is export type                                                                                 | false                                                                                          |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| errors.DeleteConnectionResponseBodyError1 | 400                                       | application/json                          |
| errors.DeleteConnectionResponseBodyError2 | 400                                       | application/json                          |
| errors.DeleteConnectionUnauthorizedError  | 401                                       | application/json                          |
| errors.MammothAnalyticsDefaultError       | 4XX, 5XX                                  | \*/\*                                     |

## update

update connection for given connector using the connection key with the provided data

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateConnection" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/connectors/{connector_key}/connections/{connection_key}" -->
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

    res = ma_client.connections.update(workspace_id=4, project_id=4, connector_key="cG9zdGdyZXM=", connection_key="kvx3b8lhfe3ilk0wv4xu4fl539njerj0lmcr6wf8", patch=[
        {
            "op": "replace",
            "path": "connection",
            "value": {},
        },
    ], is_export=False)

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
| `patch`                                                                                        | List[[models.ConnectionPatchOp](../../models/connectionpatchop.md)]                            | :heavy_check_mark:                                                                             | List of patch operations                                                                       | {<br/>"value": [<br/>{<br/>"op": "replace",<br/>"path": "connection",<br/>"value": {<br/>"database": "db"<br/>}<br/>}<br/>]<br/>} |
| `is_export`                                                                                    | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | Is export type                                                                                 | false                                                                                          |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[Any](../../models/.md)**

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| errors.UpdateConnectionResponseBodyError1 | 400                                       | application/json                          |
| errors.UpdateConnectionResponseBodyError2 | 400                                       | application/json                          |
| errors.UpdateConnectionUnauthorizedError  | 401                                       | application/json                          |
| errors.MammothAnalyticsDefaultError       | 4XX, 5XX                                  | \*/\*                                     |

## list

Get the list of connections for the given connector

### Example Usage

<!-- UsageSnippet language="python" operationID="ListConnections" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/connectors/{connector_key}/connections" -->
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

    res = ma_client.connections.list(workspace_id=4, project_id=4, connector_key="cG9zdGdyZXM=", is_export=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `connector_key`                                                                                | *str*                                                                                          | :heavy_check_mark:                                                                             | Encoded key of the Connector to work with                                                      | cG9zdGdyZXM=                                                                                   |
| `is_export`                                                                                    | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | Is export type                                                                                 | false                                                                                          |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ListConnectionsSchema](../../models/listconnectionsschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Create connection for given connector using the provided data

### Example Usage

<!-- UsageSnippet language="python" operationID="SaveConnection" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/connectors/{connector_key}/connections" -->
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

    res = ma_client.connections.create(workspace_id=4, project_id=4, connector_key="cG9zdGdyZXM=", request_body={}, is_export=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                | Type                                                                                                                                     | Required                                                                                                                                 | Description                                                                                                                              | Example                                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                                                           | *int*                                                                                                                                    | :heavy_check_mark:                                                                                                                       | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.                                           | 4                                                                                                                                        |
| `project_id`                                                                                                                             | *int*                                                                                                                                    | :heavy_check_mark:                                                                                                                       | Project ID of the workspace                                                                                                              | 4                                                                                                                                        |
| `connector_key`                                                                                                                          | *str*                                                                                                                                    | :heavy_check_mark:                                                                                                                       | Encoded key of the Connector to work with                                                                                                | cG9zdGdyZXM=                                                                                                                             |
| `request_body`                                                                                                                           | [models.SaveConnectionRequestBody](../../models/saveconnectionrequestbody.md)                                                            | :heavy_check_mark:                                                                                                                       | N/A                                                                                                                                      | {<br/>"database": "hubli_journal",<br/>"hostname": "localhost",<br/>"port": 5432,<br/>"username": "appuser",<br/>"\u003cpassword\u003e": "\u003cpwd\u003e"<br/>} |
| `is_export`                                                                                                                              | *Optional[bool]*                                                                                                                         | :heavy_minus_sign:                                                                                                                       | Is export type                                                                                                                           | false                                                                                                                                    |
| `retries`                                                                                                                                | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                         | :heavy_minus_sign:                                                                                                                       | Configuration to override the default retry behavior of the client.                                                                      |                                                                                                                                          |

### Response

**[Any](../../models/.md)**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.SaveConnectionResponseBodyError1 | 400                                     | application/json                        |
| errors.SaveConnectionResponseBodyError2 | 400                                     | application/json                        |
| errors.SaveConnectionUnauthorizedError  | 401                                     | application/json                        |
| errors.MammothAnalyticsDefaultError     | 4XX, 5XX                                | \*/\*                                   |