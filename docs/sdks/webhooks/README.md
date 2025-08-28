# Webhooks
(*webhooks*)

## Overview

### Available Operations

* [list](#list) - List webhooks
* [create](#create) - Create a webhook
* [get_details](#get_details) - Get webhook details
* [delete](#delete) - Delete webhook
* [update](#update) - Updates the webhook
* [add_data_using_get](#add_data_using_get) - Add data to the webhook
* [add_data](#add_data) - Add data to webhook

## list

Returns list of webhook details. Query parameters can be used to optimize the response.

### Example Usage

<!-- UsageSnippet language="python" operationID="ListWebhooks" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/webhooks" -->
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

    res = ma_client.webhooks.list(workspace_id=4, project_id=4, fields="id,name", id="1,2,3", name="webhook_name1,webhook_name2,webhook_name3", ds_id="1,2,3", mode="combine,replace", limit=10, offset=10, sort="(id:asc),(name:asc)")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `fields`                                                                                       | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Fields to be returned in a comma-separated format may include id, name, ds_id, url.            | id,name                                                                                        |
| `id`                                                                                           | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Track multiple webhook ids, comma separated                                                    | 1,2,3                                                                                          |
| `name`                                                                                         | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Track multiple webhook names, comma separated                                                  | webhook_name1,webhook_name2,webhook_name3                                                      |
| `ds_id`                                                                                        | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Track multiple webhook ds ids, comma separated                                                 | 1,2,3                                                                                          |
| `mode`                                                                                         | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Track multiple webhook modes, comma separated                                                  | combine,replace                                                                                |
| `limit`                                                                                        | *Optional[int]*                                                                                | :heavy_minus_sign:                                                                             | Max number of result to return                                                                 | 10                                                                                             |
| `offset`                                                                                       | *Optional[int]*                                                                                | :heavy_minus_sign:                                                                             | Distance from the beginning of the list of results                                             | 10                                                                                             |
| `sort`                                                                                         | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Sort the webhooks based on the fields                                                          | (id:asc),(name:asc)                                                                            |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.WebhooksList](../../models/webhookslist.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Create a webhook dataset.

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateAWebhook" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/webhooks" -->
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

    res = ma_client.webhooks.create(workspace_id=4, project_id=4, folder_resource_id="label_1363", name="test", mode=models.WebhookSpecMode.COMBINE, origins="{\"value\":\"*\"}", is_secure=True)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `folder_resource_id`                                                                           | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Folder resource id                                                                             | {<br/>"value": "label_1363"<br/>}                                                              |
| `name`                                                                                         | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Name of the webhook                                                                            | {<br/>"value": "test"<br/>}                                                                    |
| `mode`                                                                                         | [Optional[models.WebhookSpecMode]](../../models/webhookspecmode.md)                            | :heavy_minus_sign:                                                                             | Mode of the webhook                                                                            | {<br/>"value": "combine"<br/>}                                                                 |
| `origins`                                                                                      | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Origins                                                                                        | {<br/>"value": "*"<br/>}                                                                       |
| `is_secure`                                                                                    | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | Is secure                                                                                      | {<br/>"value": true<br/>}                                                                      |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.WebhookDetails](../../models/webhookdetails.md)**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.CreateAWebhookResponseBodyError1 | 400                                     | application/json                        |
| errors.CreateAWebhookResponseBodyError2 | 400                                     | application/json                        |
| errors.MammothAnalyticsDefaultError     | 4XX, 5XX                                | \*/\*                                   |

## get_details

Returns webhook details. Query parameters can be used to optimize the response.

### Example Usage

<!-- UsageSnippet language="python" operationID="GetWebhookDetails" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/webhooks/{webhook_id}" -->
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

    res = ma_client.webhooks.get_details(workspace_id=4, project_id=4, webhook_id=4, fields="id,name")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `webhook_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | ID of the webhook                                                                              | 4                                                                                              |
| `fields`                                                                                       | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Fields to be returned in a comma-separated format may include id, name, ds_id, url.            | id,name                                                                                        |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.WebhookDetails](../../models/webhookdetails.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## delete

Deletes given webhook.

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteWebhook" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/webhooks/{webhook_id}" -->
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

    ma_client.webhooks.delete(workspace_id=4, project_id=4, webhook_id=4)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `webhook_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | ID of the webhook                                                                              | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| errors.DeleteWebhookResponseBodyError1 | 400                                    | application/json                       |
| errors.DeleteWebhookResponseBodyError2 | 400                                    | application/json                       |
| errors.MammothAnalyticsDefaultError    | 4XX, 5XX                               | \*/\*                                  |

## update

Updates the webhook with given information.

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateWebhookConfigurations" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/webhooks/{webhook_id}" -->
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

    res = ma_client.webhooks.update(workspace_id=4, project_id=4, webhook_id=4, patch=[
        {
            "op": models.WebhookPatchDataOperation.REPLACE,
            "path": models.WebhookPatchDataPath.MODE,
            "value": models.WebhookPatchDataValueEnum.REPLACE,
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
| `webhook_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | ID of the webhook                                                                              | 4                                                                                              |
| `patch`                                                                                        | List[[models.WebhookPatchData](../../models/webhookpatchdata.md)]                              | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.WebhookDetails](../../models/webhookdetails.md)**

### Errors

| Error Type                                           | Status Code                                          | Content Type                                         |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| errors.UpdateWebhookConfigurationsResponseBodyError1 | 400                                                  | application/json                                     |
| errors.UpdateWebhookConfigurationsResponseBodyError2 | 400                                                  | application/json                                     |
| errors.MammothAnalyticsDefaultError                  | 4XX, 5XX                                             | \*/\*                                                |

## add_data_using_get

Add data to the webhook.

### Example Usage

<!-- UsageSnippet language="python" operationID="AddDataToWebhookUsingGetMethod" method="get" path="/webhooks/data/{webhook_uri}" -->
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

    ma_client.webhooks.add_data_using_get(webhook_uri="g7rHe3mUqUGPEpnc4XxeDWJa")

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `webhook_uri`                                                       | *str*                                                               | :heavy_check_mark:                                                  | API key of the webhook                                              | g7rHe3mUqUGPEpnc4XxeDWJa                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## add_data

Add data webhook dataset. Query parameters can be used to optimize the response.

### Example Usage

<!-- UsageSnippet language="python" operationID="AddDataToWebhook" method="post" path="/webhooks/data/{webhook_uri}" -->
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

    res = ma_client.webhooks.add_data(webhook_uri="g7rHe3mUqUGPEpnc4XxeDWJa")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `webhook_uri`                                                       | *str*                                                               | :heavy_check_mark:                                                  | API key of the webhook                                              | g7rHe3mUqUGPEpnc4XxeDWJa                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[Any](../../models/.md)**

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| errors.AddDataToWebhookResponseBodyError1 | 400                                       | application/json                          |
| errors.AddDataToWebhookResponseBodyError2 | 400                                       | application/json                          |
| errors.MammothAnalyticsDefaultError       | 4XX, 5XX                                  | \*/\*                                     |