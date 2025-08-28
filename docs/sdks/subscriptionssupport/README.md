# SubscriptionsSupport
(*subscriptions_support*)

## Overview

### Available Operations

* [get_detail](#get_detail) - Get subscription details
* [register](#register) - Create subscription for workspace
* [update_subscription](#update_subscription) - Update subscription for workspace
* [get_plans](#get_plans) - Get available plans and other chargebee resources

## get_detail

Retrieve associated chargebee subscription details for the workspace

### Example Usage

<!-- UsageSnippet language="python" operationID="GetSubscriptionDetail" method="get" path="/support/workspaces/{workspace_id}/sms" -->
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

    res = ma_client.subscriptions_support.get_detail(workspace_id=4, fields="id,name")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `workspace_id`                                                      | *int*                                                               | :heavy_check_mark:                                                  | Id of the workspace to work with                                    | 4                                                                   |
| `fields`                                                            | *Optional[str]*                                                     | :heavy_minus_sign:                                                  | Fields to return. Can be (id, name)                                 | id,name                                                             |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.SubscriptionSchema](../../models/subscriptionschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## register

Associate the workspace with chargebee subscription

### Example Usage

<!-- UsageSnippet language="python" operationID="RegisterSubscription" method="post" path="/support/workspaces/{workspace_id}/sms" -->
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

    res = ma_client.subscriptions_support.register(workspace_id=4, plan_id="plan_1", first_name="TestUser", last_name="TestUser", email="testuser@test.com", company_name="Test Company", customer_id="{\"summary\":\"Customer ID\",\"value\":\"cus_123456789\"}")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `workspace_id`                                                      | *int*                                                               | :heavy_check_mark:                                                  | Id of the workspace to work with                                    | 4                                                                   |
| `plan_id`                                                           | *str*                                                               | :heavy_check_mark:                                                  | Plan ID of the customer                                             | {<br/>"summary": "Sample Plan ID",<br/>"value": "professional"<br/>} |
| `first_name`                                                        | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | First Name of the customer                                          | {<br/>"summary": "First Name",<br/>"value": "John"<br/>}            |
| `last_name`                                                         | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | Last Name of the customer                                           | {<br/>"summary": "Last Name",<br/>"value": "Adom"<br/>}             |
| `email`                                                             | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | Email of the customer                                               | {<br/>"summary": "Email",<br/>"value": "example@some.com"<br/>}     |
| `company_name`                                                      | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | Company of the customer                                             | {<br/>"summary": "Company",<br/>"value": "Bad"<br/>}                |
| `customer_id`                                                       | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | ID of the customer                                                  | {<br/>"summary": "Customer ID",<br/>"value": "cus_123456789"<br/>}  |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.JobSchema](../../models/jobschema.md)**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| errors.RegisterSubscriptionBadRequestError | 400                                        | application/json                           |
| errors.MammothAnalyticsDefaultError        | 4XX, 5XX                                   | \*/\*                                      |

## update_subscription

Update the workspace's chargebee subscription

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateSubscription" method="patch" path="/support/workspaces/{workspace_id}/sms" -->
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

    ma_client.subscriptions_support.update_subscription(workspace_id=4, patch=[
        {
            "op": "replace",
            "path": "subscription_id",
            "value": "AleMockSubsIda32ax",
        },
    ])

    # Use the SDK ...

```

### Parameters

| Parameter                                                               | Type                                                                    | Required                                                                | Description                                                             | Example                                                                 |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| `workspace_id`                                                          | *int*                                                                   | :heavy_check_mark:                                                      | Id of the workspace to work with                                        | 4                                                                       |
| `patch`                                                                 | List[[models.SubscriptionPatchOp](../../models/subscriptionpatchop.md)] | :heavy_check_mark:                                                      | N/A                                                                     |                                                                         |
| `retries`                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)        | :heavy_minus_sign:                                                      | Configuration to override the default retry behavior of the client.     |                                                                         |

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| errors.UpdateSubscriptionBadRequestError | 400                                      | application/json                         |
| errors.MammothAnalyticsDefaultError      | 4XX, 5XX                                 | \*/\*                                    |

## get_plans

Retrieve the list of available plans and other Chargebee-related resources

### Example Usage

<!-- UsageSnippet language="python" operationID="GetPlans" method="get" path="/support/sms" -->
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

    res = ma_client.subscriptions_support.get_plans(resource="plans")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `resource`                                                          | *str*                                                               | :heavy_check_mark:                                                  | Type of resource to list                                            |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.PlanList](../../models/planlist.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |