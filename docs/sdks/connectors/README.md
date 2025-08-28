# Connectors
(*connectors*)

## Overview

### Available Operations

* [fetch](#fetch) - List all connectors
* [create](#create) - Create a new connector
* [update](#update) - Update a connector
* [delete](#delete) - Delete a connector
* [get](#get) - Get connector details
* [list](#list) - List connectors

## fetch

Retrieve all available connectors with enhanced error handling

### Example Usage

<!-- UsageSnippet language="python" operationID="ListSubscriptionConnectors" method="get" path="/subscription/connectors" -->
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

    res = ma_client.connectors.fetch()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ConnectorListResponseSchema](../../models/connectorlistresponseschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Create a new connector with comprehensive validation

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateConnector" method="post" path="/subscription/connectors" -->
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

    res = ma_client.connectors.create(name="<value>", price_per_month=0, enabled=True)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `name`                                                              | *str*                                                               | :heavy_check_mark:                                                  | Connector name                                                      |
| `description`                                                       | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | Connector description                                               |
| `price_per_month`                                                   | *Optional[float]*                                                   | :heavy_minus_sign:                                                  | Monthly price in USD                                                |
| `enabled`                                                           | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | Whether connector is enabled                                        |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ConnectorResponseSchema](../../models/connectorresponseschema.md)**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.CreateConnectorBadRequestError | 400                                   | application/json                      |
| errors.MammothAnalyticsDefaultError   | 4XX, 5XX                              | \*/\*                                 |

## update

Update an existing connector with validation

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateConnector" method="put" path="/subscription/connectors/{connector_id}" -->
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

    res = ma_client.connectors.update(connector_id=241775)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `connector_id`                                                      | *int*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `name`                                                              | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | Connector name                                                      |
| `description`                                                       | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | Connector description                                               |
| `price_per_month`                                                   | *OptionalNullable[float]*                                           | :heavy_minus_sign:                                                  | Monthly price in USD                                                |
| `enabled`                                                           | *OptionalNullable[bool]*                                            | :heavy_minus_sign:                                                  | Whether connector is enabled                                        |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ConnectorResponseSchema](../../models/connectorresponseschema.md)**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.UpdateConnectorBadRequestError | 400                                   | application/json                      |
| errors.MammothAnalyticsDefaultError   | 4XX, 5XX                              | \*/\*                                 |

## delete

Delete a connector with enhanced validation

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteConnector" method="delete" path="/subscription/connectors/{connector_id}" -->
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

    res = ma_client.connectors.delete(connector_id=585335)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `connector_id`                                                      | *int*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.MessageResponseSchema](../../models/messageresponseschema.md)**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| errors.DeleteConnectorBadRequestError | 400                                   | application/json                      |
| errors.MammothAnalyticsDefaultError   | 4XX, 5XX                              | \*/\*                                 |

## get

Get the details of an connector

### Example Usage

<!-- UsageSnippet language="python" operationID="GetConnector" method="get" path="/workspaces/{workspace_id}/connectors/{connector_key}" -->
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

    res = ma_client.connectors.get(workspace_id=4, connector_key="cG9zdGdyZXM=", fields="name_key,api_type", is_export=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `connector_key`                                                                                | *str*                                                                                          | :heavy_check_mark:                                                                             | Encoded key of the Connector to work with                                                      | cG9zdGdyZXM=                                                                                   |
| `fields`                                                                                       | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Fields to be returned in a comma-separated format                                              | name_key,api_type                                                                              |
| `is_export`                                                                                    | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ConnectorsSchema](../../models/connectorsschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## list

List the connectors that are provided by the system

### Example Usage

<!-- UsageSnippet language="python" operationID="ListWorkspaceConnectors" method="get" path="/workspaces/{workspace_id}/connectors" -->
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

    res = ma_client.connectors.list(workspace_id=4, limit=10, offset=10, fields="name_key,api_type", sort="(name_key:asc),(disp_name:desc)", name_key="My Connector", is_premium=True, is_added=True)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                        | Type                                                                                                                             | Required                                                                                                                         | Description                                                                                                                      | Example                                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                                                   | *int*                                                                                                                            | :heavy_check_mark:                                                                                                               | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.                                   | 4                                                                                                                                |
| `limit`                                                                                                                          | *Optional[int]*                                                                                                                  | :heavy_minus_sign:                                                                                                               | Max number of result to return                                                                                                   | 10                                                                                                                               |
| `offset`                                                                                                                         | *Optional[int]*                                                                                                                  | :heavy_minus_sign:                                                                                                               | Distance from the beginning of the list of results                                                                               | 10                                                                                                                               |
| `fields`                                                                                                                         | *Optional[str]*                                                                                                                  | :heavy_minus_sign:                                                                                                               | Fields to be returned in a comma-separated format                                                                                | name_key,api_type                                                                                                                |
| `sort`                                                                                                                           | *Optional[str]*                                                                                                                  | :heavy_minus_sign:                                                                                                               | Returned connectors based on this parameter Use the format '(field:asc)' for ascending and  '(field:desc)' for descending order. | (name_key:asc),(disp_name:desc)                                                                                                  |
| `name_key`                                                                                                                       | *Optional[str]*                                                                                                                  | :heavy_minus_sign:                                                                                                               | Fetch Connector which matches given name (case sensitive)                                                                        | My Connector                                                                                                                     |
| `is_premium`                                                                                                                     | *OptionalNullable[bool]*                                                                                                         | :heavy_minus_sign:                                                                                                               | Fetch all Connectors based on premium status                                                                                     | true                                                                                                                             |
| `is_added`                                                                                                                       | *OptionalNullable[bool]*                                                                                                         | :heavy_minus_sign:                                                                                                               | Fetch all Connectors based on added status                                                                                       | true                                                                                                                             |
| `retries`                                                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                 | :heavy_minus_sign:                                                                                                               | Configuration to override the default retry behavior of the client.                                                              |                                                                                                                                  |

### Response

**[models.ConnectorList](../../models/connectorlist.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |