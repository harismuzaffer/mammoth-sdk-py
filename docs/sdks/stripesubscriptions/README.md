# StripeSubscriptions
(*stripe_subscriptions*)

## Overview

### Available Operations

* [cancel_workspace](#cancel_workspace) - Cancel workspace subscription in Stripe
* [create_checkout_url](#create_checkout_url) - Create Stripe checkout URL for workspace subscription
* [create_portal_url](#create_portal_url) - Create Stripe customer portal URL
* [get](#get) - Get workspace subscription from Stripe
* [create_workspace](#create_workspace) - Create Stripe subscription for workspace
* [get_payment_methods](#get_payment_methods) - Get workspace payment methods from Stripe
* [get_upcoming_invoice](#get_upcoming_invoice) - Get upcoming invoice from Stripe
* [get_billing_history](#get_billing_history) - Get workspace billing history from Stripe
* [get_workspace_status](#get_workspace_status) - Get workspace subscription status
* [get_usage](#get_usage) - Get workspace usage from Stripe

## cancel_workspace

Cancel workspace subscription in Stripe

### Example Usage

<!-- UsageSnippet language="python" operationID="CancelWorkspaceSubscription" method="post" path="/workspaces/{workspace_id}/subscription/cancel" -->
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

    res = ma_client.stripe_subscriptions.cancel_workspace(workspace_id=4, request_body={
        "key": "<value>",
        "key1": "<value>",
        "key2": "<value>",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `request_body`                                                                                 | Dict[str, *Any*]                                                                               | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.MessageResponseSchema](../../models/messageresponseschema.md)**

### Errors

| Error Type                                        | Status Code                                       | Content Type                                      |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| errors.CancelWorkspaceSubscriptionBadRequestError | 400                                               | application/json                                  |
| errors.MammothAnalyticsDefaultError               | 4XX, 5XX                                          | \*/\*                                             |

## create_checkout_url

Create Stripe checkout URL for workspace subscription

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateCheckoutUrl" method="post" path="/workspaces/{workspace_id}/subscription/create-checkout" -->
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

    res = ma_client.stripe_subscriptions.create_checkout_url(workspace_id=4, success_url="https://mysterious-help.com", cancel_url="https://ironclad-bowler.biz")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `success_url`                                                                                  | *str*                                                                                          | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `cancel_url`                                                                                   | *str*                                                                                          | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.CreateCheckoutURLResponseSchema](../../models/createcheckouturlresponseschema.md)**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.CreateCheckoutURLBadRequestError | 400                                     | application/json                        |
| errors.MammothAnalyticsDefaultError     | 4XX, 5XX                                | \*/\*                                   |

## create_portal_url

Create Stripe customer portal URL

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateCustomerPortalUrl" method="post" path="/workspaces/{workspace_id}/subscription/customer-portal" -->
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

    res = ma_client.stripe_subscriptions.create_portal_url(workspace_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `return_url`                                                                                   | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.CreateCustomerPortalURLResponseSchema](../../models/createcustomerportalurlresponseschema.md)**

### Errors

| Error Type                                    | Status Code                                   | Content Type                                  |
| --------------------------------------------- | --------------------------------------------- | --------------------------------------------- |
| errors.CreateCustomerPortalURLBadRequestError | 400                                           | application/json                              |
| errors.MammothAnalyticsDefaultError           | 4XX, 5XX                                      | \*/\*                                         |

## get

Get workspace subscription from Stripe

### Example Usage

<!-- UsageSnippet language="python" operationID="GetWorkspaceSubscription" method="get" path="/workspaces/{workspace_id}/subscription" -->
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

    res = ma_client.stripe_subscriptions.get(workspace_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.SubscriptionResponseSchema](../../models/subscriptionresponseschema.md)**

### Errors

| Error Type                                     | Status Code                                    | Content Type                                   |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| errors.GetWorkspaceSubscriptionBadRequestError | 400                                            | application/json                               |
| errors.MammothAnalyticsDefaultError            | 4XX, 5XX                                       | \*/\*                                          |

## create_workspace

Create Stripe subscription for workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateWorkspaceSubscription" method="post" path="/workspaces/{workspace_id}/subscription" -->
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

    res = ma_client.stripe_subscriptions.create_workspace(workspace_id=4, plan_id=699898, customer_email="<value>", billing_interval="monthly", trial_days=0)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `plan_id`                                                                                      | *int*                                                                                          | :heavy_check_mark:                                                                             | Plan ID to subscribe to                                                                        |                                                                                                |
| `customer_email`                                                                               | *str*                                                                                          | :heavy_check_mark:                                                                             | Customer email address                                                                         |                                                                                                |
| `billing_interval`                                                                             | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Billing interval                                                                               |                                                                                                |
| `trial_days`                                                                                   | *Optional[int]*                                                                                | :heavy_minus_sign:                                                                             | Trial period in days                                                                           |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.CreateSubscriptionResponseSchema](../../models/createsubscriptionresponseschema.md)**

### Errors

| Error Type                                        | Status Code                                       | Content Type                                      |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| errors.CreateWorkspaceSubscriptionBadRequestError | 400                                               | application/json                                  |
| errors.MammothAnalyticsDefaultError               | 4XX, 5XX                                          | \*/\*                                             |

## get_payment_methods

Get workspace payment methods from Stripe

### Example Usage

<!-- UsageSnippet language="python" operationID="GetPaymentMethods" method="get" path="/workspaces/{workspace_id}/subscription/payment-methods" -->
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

    res = ma_client.stripe_subscriptions.get_payment_methods(workspace_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.PaymentMethodsResponseSchema](../../models/paymentmethodsresponseschema.md)**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.GetPaymentMethodsBadRequestError | 400                                     | application/json                        |
| errors.MammothAnalyticsDefaultError     | 4XX, 5XX                                | \*/\*                                   |

## get_upcoming_invoice

Get upcoming invoice from Stripe

### Example Usage

<!-- UsageSnippet language="python" operationID="GetUpcomingInvoice" method="get" path="/workspaces/{workspace_id}/subscription/upcoming-invoice" -->
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

    res = ma_client.stripe_subscriptions.get_upcoming_invoice(workspace_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.UpcomingInvoiceResponseSchema](../../models/upcominginvoiceresponseschema.md)**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| errors.GetUpcomingInvoiceBadRequestError | 400                                      | application/json                         |
| errors.MammothAnalyticsDefaultError      | 4XX, 5XX                                 | \*/\*                                    |

## get_billing_history

Get workspace billing history from Stripe

### Example Usage

<!-- UsageSnippet language="python" operationID="GetWorkspaceBillingHistory" method="get" path="/workspaces/{workspace_id}/subscription/billing-history" -->
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

    res = ma_client.stripe_subscriptions.get_billing_history(workspace_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.BillingHistoryResponseSchema](../../models/billinghistoryresponseschema.md)**

### Errors

| Error Type                                       | Status Code                                      | Content Type                                     |
| ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ |
| errors.GetWorkspaceBillingHistoryBadRequestError | 400                                              | application/json                                 |
| errors.MammothAnalyticsDefaultError              | 4XX, 5XX                                         | \*/\*                                            |

## get_workspace_status

Get workspace subscription status

### Example Usage

<!-- UsageSnippet language="python" operationID="GetWorkspaceSubscriptionStatus" method="get" path="/workspaces/{workspace_id}/subscription/status" -->
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

    res = ma_client.stripe_subscriptions.get_workspace_status(workspace_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.WorkspaceSubscriptionStatusDataSchema](../../models/workspacesubscriptionstatusdataschema.md)**

### Errors

| Error Type                                           | Status Code                                          | Content Type                                         |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| errors.GetWorkspaceSubscriptionStatusBadRequestError | 400                                                  | application/json                                     |
| errors.MammothAnalyticsDefaultError                  | 4XX, 5XX                                             | \*/\*                                                |

## get_usage

Get workspace usage from Stripe

### Example Usage

<!-- UsageSnippet language="python" operationID="GetWorkspaceUsage" method="get" path="/workspaces/{workspace_id}/subscription/usage" -->
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

    res = ma_client.stripe_subscriptions.get_usage(workspace_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.UsageResponseSchema](../../models/usageresponseschema.md)**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.GetWorkspaceUsageBadRequestError | 400                                     | application/json                        |
| errors.MammothAnalyticsDefaultError     | 4XX, 5XX                                | \*/\*                                   |