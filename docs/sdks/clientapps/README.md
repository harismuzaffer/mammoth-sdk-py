# ClientApps
(*client_apps*)

## Overview

### Available Operations

* [get_details](#get_details) - Get client app details
* [delete](#delete) - Delete a client app
* [update](#update) - Update client app
* [list](#list) - Get list of client apps
* [create](#create) - Create api tokens to access api

## get_details

Get client app details

### Example Usage

<!-- UsageSnippet language="python" operationID="AppDetails" method="get" path="/workspaces/{workspace_id}/clientapps/{client_key}" -->
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

    res = ma_client.client_apps.get_details(workspace_id=4, client_key="abcdefasdfafdsfaf345asf", fields="id,app_name")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `client_key`                                                                                   | *str*                                                                                          | :heavy_check_mark:                                                                             | Id of the client key to work with                                                              | abcdefasdfafdsfaf345asf                                                                        |
| `fields`                                                                                       | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Fields to return. Can be (id, app_name)                                                        | id,app_name                                                                                    |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ClientAppSchema](../../models/clientappschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## delete

Delete a client app

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteApp" method="delete" path="/workspaces/{workspace_id}/clientapps/{client_key}" -->
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

    ma_client.client_apps.delete(workspace_id=4, client_key="abcdefasdfafdsfaf345asf")

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `client_key`                                                                                   | *str*                                                                                          | :heavy_check_mark:                                                                             | Id of the client key to work with                                                              | abcdefasdfafdsfaf345asf                                                                        |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## update

Update client app details like name, description, secret etc

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateApp" method="patch" path="/workspaces/{workspace_id}/clientapps/{client_key}" -->
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

    res = ma_client.client_apps.update(workspace_id=4, client_key="abcdefasdfafdsfaf345asf", patch=[
        {
            "op": "replace",
            "path": "app_name",
            "value": "test",
        },
        {
            "op": "replace",
            "path": "description",
            "value": "test",
        },
        {
            "op": "replace",
            "path": "api_secret",
            "value": [
                "abcd3234adfaf3w3f4a4",
                "encrypted_abcd3234adfaf3w3f4a4",
            ],
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `client_key`                                                                                   | *str*                                                                                          | :heavy_check_mark:                                                                             | Id of the client key to work with                                                              | abcdefasdfafdsfaf345asf                                                                        |
| `patch`                                                                                        | List[[models.PatchOperation](../../models/patchoperation.md)]                                  | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ClientAppSchema](../../models/clientappschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## list

Get list of client apps specific to given user and workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="ListApps" method="get" path="/workspaces/{workspace_id}/clientapps" -->
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

    res = ma_client.client_apps.list(workspace_id=4, limit=10, offset=0, fields="id,app_name", sort="(last_usage:asc),(id:desc)")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                        | Type                                                                                                                             | Required                                                                                                                         | Description                                                                                                                      | Example                                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                                                   | *int*                                                                                                                            | :heavy_check_mark:                                                                                                               | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.                                   | 4                                                                                                                                |
| `limit`                                                                                                                          | *Optional[int]*                                                                                                                  | :heavy_minus_sign:                                                                                                               | Max number of result to return                                                                                                   | 10                                                                                                                               |
| `offset`                                                                                                                         | *Optional[int]*                                                                                                                  | :heavy_minus_sign:                                                                                                               | Distance from the beginning of the list of results                                                                               | 0                                                                                                                                |
| `fields`                                                                                                                         | *Optional[str]*                                                                                                                  | :heavy_minus_sign:                                                                                                               | Fields to return. Can be (id, app_name)                                                                                          | id,app_name                                                                                                                      |
| `sort`                                                                                                                           | *OptionalNullable[str]*                                                                                                          | :heavy_minus_sign:                                                                                                               | Returned client apps based on this parameter Use the format '(field:asc)' for ascending and '(field:desc)' for descending order. | (last_usage:asc),(id:desc)                                                                                                       |
| `retries`                                                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                 | :heavy_minus_sign:                                                                                                               | Configuration to override the default retry behavior of the client.                                                              |                                                                                                                                  |

### Response

**[models.ClientAppsList](../../models/clientappslist.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Create api tokens to a user for a workspace to access APIs

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateApp" method="post" path="/workspaces/{workspace_id}/clientapps" -->
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

    res = ma_client.client_apps.create(workspace_id=4, app_name="test2", description="test from doc", api_key="G4gSQUNMLw1PJOAb3TLbiCPXpDF5", api_secret="noGXcACTSUBYoC0ZBM42rgYpClxcgjkk5f", encrypted_key="tkerqRZHKkwVL8oyKGZpozno9uelBjK+hyIk82VhEtmsS0aGsrX5Hc1mnKY0pUhdYMygSdYGFTA=", encrypted_secret="BT3fC5CiZsNECQryaSICcdlix87BWFWnBxDxStbOe0aKJJCmGLqgELssp3z4PrR4wNSiWhc2Rlw/beZMaLo=", project_id=[object Object])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `app_name`                                                                                     | *str*                                                                                          | :heavy_check_mark:                                                                             | Name of client app or api tokens                                                               | {<br/>"value": "New Example Client App Name"<br/>}                                             |
| `description`                                                                                  | *str*                                                                                          | :heavy_check_mark:                                                                             | Description of client app or api tokens                                                        | {<br/>"value": "Example Client App Description"<br/>}                                          |
| `api_key`                                                                                      | *str*                                                                                          | :heavy_check_mark:                                                                             | App key of client app or api tokens                                                            | {<br/>"value": "abcDefGhiJklMnoPqrStuVwxYz1234567890"<br/>}                                    |
| `api_secret`                                                                                   | *str*                                                                                          | :heavy_check_mark:                                                                             | App Secret of client app or api tokens                                                         | {<br/>"value": "secret_abcDefGhiJklMnoPqrStuVwxYz1234567890"<br/>}                             |
| `encrypted_key`                                                                                | *str*                                                                                          | :heavy_check_mark:                                                                             | Encrypted keyof client app or api tokens                                                       | {<br/>"value": "encrypted_abcDefGhiJklMnoPqrStuVwxYz1234567890"<br/>}                          |
| `encrypted_secret`                                                                             | *str*                                                                                          | :heavy_check_mark:                                                                             | Encrypted secret of client app or api tokens                                                   | {<br/>"value": "encrypted_secret_abcDefGhiJklMnoPqrStuVwxYz1234567890"<br/>}                   |
| `project_id`                                                                                   | *OptionalNullable[int]*                                                                        | :heavy_minus_sign:                                                                             | Project ID                                                                                     | {<br/>"value": "Sample project ID"<br/>}                                                       |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ClientAppPostResponse](../../models/clientapppostresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |