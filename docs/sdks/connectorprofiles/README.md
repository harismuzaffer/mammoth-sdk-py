# ConnectorProfiles
(*connector_profiles*)

## Overview

### Available Operations

* [add_connector](#add_connector) - Add connector to profile
* [list](#list) - List all connector profiles
* [create](#create) - Create a new connector profile
* [update](#update) - Update a connector profile
* [delete](#delete) - Delete a connector profile

## add_connector

Add a connector to an existing profile

### Example Usage

<!-- UsageSnippet language="python" operationID="AddConnectorToProfile" method="post" path="/subscription/connector-profiles/{profile_id}/connectors" -->
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

    res = ma_client.connector_profiles.add_connector(profile_id=443370, connector_id=500013, price_per_month=0, enabled=True)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `profile_id`                                                        | *int*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `connector_id`                                                      | *int*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `price_per_month`                                                   | *OptionalNullable[float]*                                           | :heavy_minus_sign:                                                  | N/A                                                                 |
| `enabled`                                                           | *OptionalNullable[bool]*                                            | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.AddConnectorToProfileResponseSchema](../../models/addconnectortoprofileresponseschema.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| errors.AddConnectorToProfileBadRequestError | 400                                         | application/json                            |
| errors.MammothAnalyticsDefaultError         | 4XX, 5XX                                    | \*/\*                                       |

## list

Retrieve all connector profiles

### Example Usage

<!-- UsageSnippet language="python" operationID="ListConnectorProfiles" method="get" path="/subscription/connector-profiles" -->
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

    res = ma_client.connector_profiles.list()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ConnectorProfileListResponseSchema](../../models/connectorprofilelistresponseschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Create a new connector profile with comprehensive validation

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateConnectorProfile" method="post" path="/subscription/connector-profiles" -->
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

    res = ma_client.connector_profiles.create(name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `name`                                                                                          | *str*                                                                                           | :heavy_check_mark:                                                                              | N/A                                                                                             |
| `description`                                                                                   | *OptionalNullable[str]*                                                                         | :heavy_minus_sign:                                                                              | N/A                                                                                             |
| `connectors`                                                                                    | List[[models.ConnectorProfileConnectorSchema](../../models/connectorprofileconnectorschema.md)] | :heavy_minus_sign:                                                                              | N/A                                                                                             |
| `retries`                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                | :heavy_minus_sign:                                                                              | Configuration to override the default retry behavior of the client.                             |

### Response

**[models.ConnectorProfileResponseSchema](../../models/connectorprofileresponseschema.md)**

### Errors

| Error Type                                   | Status Code                                  | Content Type                                 |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| errors.CreateConnectorProfileBadRequestError | 400                                          | application/json                             |
| errors.MammothAnalyticsDefaultError          | 4XX, 5XX                                     | \*/\*                                        |

## update

Update an existing connector profile

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateConnectorProfile" method="put" path="/subscription/connector-profiles/{profile_id}" -->
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

    res = ma_client.connector_profiles.update(profile_id=508522)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                       | Type                                                                                            | Required                                                                                        | Description                                                                                     |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `profile_id`                                                                                    | *int*                                                                                           | :heavy_check_mark:                                                                              | N/A                                                                                             |
| `name`                                                                                          | *OptionalNullable[str]*                                                                         | :heavy_minus_sign:                                                                              | N/A                                                                                             |
| `description`                                                                                   | *OptionalNullable[str]*                                                                         | :heavy_minus_sign:                                                                              | N/A                                                                                             |
| `connectors`                                                                                    | List[[models.ConnectorProfileConnectorSchema](../../models/connectorprofileconnectorschema.md)] | :heavy_minus_sign:                                                                              | N/A                                                                                             |
| `retries`                                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                | :heavy_minus_sign:                                                                              | Configuration to override the default retry behavior of the client.                             |

### Response

**[models.ConnectorProfileResponseSchema](../../models/connectorprofileresponseschema.md)**

### Errors

| Error Type                                   | Status Code                                  | Content Type                                 |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| errors.UpdateConnectorProfileBadRequestError | 400                                          | application/json                             |
| errors.MammothAnalyticsDefaultError          | 4XX, 5XX                                     | \*/\*                                        |

## delete

Delete a connector profile

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteConnectorProfile" method="delete" path="/subscription/connector-profiles/{profile_id}" -->
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

    res = ma_client.connector_profiles.delete(profile_id=799908)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `profile_id`                                                        | *int*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.MessageResponseSchema](../../models/messageresponseschema.md)**

### Errors

| Error Type                                   | Status Code                                  | Content Type                                 |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| errors.DeleteConnectorProfileBadRequestError | 400                                          | application/json                             |
| errors.MammothAnalyticsDefaultError          | 4XX, 5XX                                     | \*/\*                                        |