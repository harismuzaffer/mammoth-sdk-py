# Subscriptions
(*subscriptions*)

## Overview

### Available Operations

* [get_detail](#get_detail) - Get subscription details
* [list_invoices](#list_invoices) - List all invoices

## get_detail

Retrieve associated chargebee subscription details for the workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="GetWkspSubscriptionDetail" method="get" path="/workspaces/{workspace_id}/subscription_v1" -->
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

    res = ma_client.subscriptions.get_detail(workspace_id=4, fields="id,name")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `fields`                                                                                       | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Fields to return. Can be (id, name)                                                            | id,name                                                                                        |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.SubscriptionsFieldSchema](../../models/subscriptionsfieldschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## list_invoices

List all invoices for the workspace subscription

### Example Usage

<!-- UsageSnippet language="python" operationID="ListInvoices" method="get" path="/workspaces/{workspace_id}/subscription_v1/invoices" -->
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

    res = ma_client.subscriptions.list_invoices(workspace_id=4, limit=10, sort="(date:desc)")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                         | Type                                                                                                                                                              | Required                                                                                                                                                          | Description                                                                                                                                                       | Example                                                                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                                                                                    | *int*                                                                                                                                                             | :heavy_check_mark:                                                                                                                                                | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.                                                                    | 4                                                                                                                                                                 |
| `limit`                                                                                                                                                           | *Optional[int]*                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                | Max number of result to return                                                                                                                                    | 10                                                                                                                                                                |
| `sort`                                                                                                                                                            | *Optional[str]*                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                | Returns resource based on this parameter. Use the format '(field:asc)' for ascending and '(field:desc)' for descending order. Allowed values: date and updated_at | (date:desc)                                                                                                                                                       |
| `retries`                                                                                                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                  | :heavy_minus_sign:                                                                                                                                                | Configuration to override the default retry behavior of the client.                                                                                               |                                                                                                                                                                   |

### Response

**[models.InvoicesSchema](../../models/invoicesschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |