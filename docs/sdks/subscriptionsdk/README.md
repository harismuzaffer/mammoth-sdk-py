# SubscriptionSDK
(*subscription*)

## Overview

### Available Operations

* [fetch_hosted_page](#fetch_hosted_page) - Get hosted pages
* [get_invoice](#get_invoice) - Get associated plan details
* [update_detail](#update_detail) - Update subscription details

## fetch_hosted_page

Get hosted pages of the subscription for the requested properties

### Example Usage

<!-- UsageSnippet language="python" operationID="FetchHostedPage" method="post" path="/workspaces/{workspace_id}/subscription_v1/hosted-page" -->
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

    res = ma_client.subscription.fetch_hosted_page(workspace_id=4, object_type="change_plan", plan_id="test_plan_11")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `object_type`                                                                                  | *str*                                                                                          | :heavy_check_mark:                                                                             | Type of the hosted page                                                                        | {<br/>"summary": "Sample Page Type",<br/>"value": "portal_session"<br/>}                       |
| `plan_id`                                                                                      | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | ID of the plan                                                                                 | {<br/>"summary": "Sample Plan ID",<br/>"value": "internal"<br/>}                               |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.FetchHostedPageResponse](../../models/fetchhostedpageresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## get_invoice

Retrieve the current plan details for the workspace subscription

### Example Usage

<!-- UsageSnippet language="python" operationID="GetInvoice" method="get" path="/workspaces/{workspace_id}/subscription_v1/invoices/{invoice_id}" -->
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

    res = ma_client.subscription.get_invoice(workspace_id=4, invoice_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `invoice_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | ID of the invoice                                                                              | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.InvoiceSchema](../../models/invoiceschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## update_detail

Update associated chargebee subscription objects for the workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateSubscriptionDetail" method="patch" path="/workspaces/{workspace_id}/subscription_v1" -->
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

    res = ma_client.subscription.update_detail(workspace_id=4, patch=[
        {
            "op": models.SubscriptionPatchItemOp.ADD,
            "path": "addons",
            "value": {
                "type": models.SubscriptionPatchValueType.STORAGE,
                "count": 1,
            },
        },
        {
            "op": models.SubscriptionPatchItemOp.REPLACE,
            "path": "addons",
            "value": {
                "type": models.SubscriptionPatchValueType.CONNECTOR,
                "add": [
                    "ga_lib",
                ],
                "remove": [
                    "facebook_ads",
                ],
            },
        },
        {
            "op": models.SubscriptionPatchItemOp.ADD,
            "path": "addons",
            "value": {
                "type": models.SubscriptionPatchValueType.USER,
                "count": 1,
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
| `patch`                                                                                        | List[[models.SubscriptionPatchItem](../../models/subscriptionpatchitem.md)]                    | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.SubscriptionsFieldSchema](../../models/subscriptionsfieldschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |