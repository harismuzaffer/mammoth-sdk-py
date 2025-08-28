# SubscriptionPlans
(*subscription_plans*)

## Overview

### Available Operations

* [archive](#archive) - Archive a subscription plan
* [list](#list) - List all subscription plans
* [create](#create) - Create a new subscription plan
* [get](#get) - Get a specific plan
* [update](#update) - Update a subscription plan
* [delete](#delete) - Delete a subscription plan
* [update_storage_tiers](#update_storage_tiers) - Update storage tiers for a plan

## archive

Archive a subscription plan (soft delete)

### Example Usage

<!-- UsageSnippet language="python" operationID="ArchivePlan" method="post" path="/subscription/plans/{plan_id}/archive" -->
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

    res = ma_client.subscription_plans.archive(plan_id=477584)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `plan_id`                                                           | *int*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.PlanResponseSchema](../../models/planresponseschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.ArchivePlanBadRequestError   | 400                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## list

Retrieve all active subscription plans with enhanced error handling

### Example Usage

<!-- UsageSnippet language="python" operationID="ListSubscriptionPlans" method="get" path="/subscription/plans" -->
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

    res = ma_client.subscription_plans.list()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.PlanListResponseSchema](../../models/planlistresponseschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Create a new subscription plan with comprehensive validation

### Example Usage

<!-- UsageSnippet language="python" operationID="CreatePlan" method="post" path="/subscription/plans" -->
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

    res = ma_client.subscription_plans.create(name="<value>", monthly_price=9111.71, is_self_serve=False, annual_only=False, storage_amount=0, number_of_tiers=1)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                 | Type                                                                                                      | Required                                                                                                  | Description                                                                                               |
| --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| `name`                                                                                                    | *str*                                                                                                     | :heavy_check_mark:                                                                                        | Plan name                                                                                                 |
| `monthly_price`                                                                                           | *float*                                                                                                   | :heavy_check_mark:                                                                                        | Monthly price in USD                                                                                      |
| `is_self_serve`                                                                                           | *bool*                                                                                                    | :heavy_check_mark:                                                                                        | Whether users can self-subscribe                                                                          |
| `description`                                                                                             | *OptionalNullable[str]*                                                                                   | :heavy_minus_sign:                                                                                        | Plan description                                                                                          |
| `annual_price`                                                                                            | *OptionalNullable[float]*                                                                                 | :heavy_minus_sign:                                                                                        | Annual price in USD                                                                                       |
| `annual_only`                                                                                             | *Optional[bool]*                                                                                          | :heavy_minus_sign:                                                                                        | Whether plan is annual only                                                                               |
| `trial_days`                                                                                              | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Trial period in days                                                                                      |
| `storage_amount`                                                                                          | *Optional[int]*                                                                                           | :heavy_minus_sign:                                                                                        | Included storage in GB                                                                                    |
| `max_storage`                                                                                             | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Maximum storage in GB                                                                                     |
| `max_users`                                                                                               | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Maximum number of users                                                                                   |
| `no_of_users`                                                                                             | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Number of included users                                                                                  |
| `seat_price`                                                                                              | *OptionalNullable[float]*                                                                                 | :heavy_minus_sign:                                                                                        | Price per additional user seat                                                                            |
| `number_of_tiers`                                                                                         | *Optional[int]*                                                                                           | :heavy_minus_sign:                                                                                        | Number of storage tiers                                                                                   |
| `storage_block_size`                                                                                      | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Storage block size in GB                                                                                  |
| `tiers`                                                                                                   | List[[models.SubscriptionSchemasStorageTierSchema](../../models/subscriptionschemasstoragetierschema.md)] | :heavy_minus_sign:                                                                                        | Storage pricing tiers                                                                                     |
| `connector_profile_id`                                                                                    | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Connector profile ID                                                                                      |
| `feature_profile_id`                                                                                      | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Feature profile ID                                                                                        |
| `retries`                                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                          | :heavy_minus_sign:                                                                                        | Configuration to override the default retry behavior of the client.                                       |

### Response

**[models.PlanResponseSchema](../../models/planresponseschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.CreatePlanBadRequestError    | 400                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## get

Retrieve details of a specific subscription plan

### Example Usage

<!-- UsageSnippet language="python" operationID="GetPlan" method="get" path="/subscription/plans/{plan_id}" -->
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

    res = ma_client.subscription_plans.get(plan_id=910215)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `plan_id`                                                           | *int*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.PlanResponseSchema](../../models/planresponseschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.GetPlanBadRequestError       | 400                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## update

Update an existing subscription plan with validation

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdatePlan" method="put" path="/subscription/plans/{plan_id}" -->
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

    res = ma_client.subscription_plans.update(plan_id=494542)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                 | Type                                                                                                      | Required                                                                                                  | Description                                                                                               |
| --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| `plan_id`                                                                                                 | *int*                                                                                                     | :heavy_check_mark:                                                                                        | N/A                                                                                                       |
| `name`                                                                                                    | *OptionalNullable[str]*                                                                                   | :heavy_minus_sign:                                                                                        | Plan name                                                                                                 |
| `description`                                                                                             | *OptionalNullable[str]*                                                                                   | :heavy_minus_sign:                                                                                        | Plan description                                                                                          |
| `monthly_price`                                                                                           | *OptionalNullable[float]*                                                                                 | :heavy_minus_sign:                                                                                        | Monthly price in USD                                                                                      |
| `annual_price`                                                                                            | *OptionalNullable[float]*                                                                                 | :heavy_minus_sign:                                                                                        | Annual price in USD                                                                                       |
| `annual_only`                                                                                             | *OptionalNullable[bool]*                                                                                  | :heavy_minus_sign:                                                                                        | Whether plan is annual only                                                                               |
| `is_self_serve`                                                                                           | *OptionalNullable[bool]*                                                                                  | :heavy_minus_sign:                                                                                        | Whether users can self-subscribe                                                                          |
| `trial_days`                                                                                              | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Trial period in days                                                                                      |
| `storage_amount`                                                                                          | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Included storage in GB                                                                                    |
| `max_storage`                                                                                             | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Maximum storage in GB                                                                                     |
| `max_users`                                                                                               | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Maximum number of users                                                                                   |
| `no_of_users`                                                                                             | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Number of included users                                                                                  |
| `seat_price`                                                                                              | *OptionalNullable[float]*                                                                                 | :heavy_minus_sign:                                                                                        | Price per additional user seat                                                                            |
| `number_of_tiers`                                                                                         | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Number of storage tiers                                                                                   |
| `storage_block_size`                                                                                      | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Storage block size in GB                                                                                  |
| `tiers`                                                                                                   | List[[models.SubscriptionSchemasStorageTierSchema](../../models/subscriptionschemasstoragetierschema.md)] | :heavy_minus_sign:                                                                                        | Storage pricing tiers                                                                                     |
| `connector_profile_id`                                                                                    | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Connector profile ID                                                                                      |
| `feature_profile_id`                                                                                      | *OptionalNullable[int]*                                                                                   | :heavy_minus_sign:                                                                                        | Feature profile ID                                                                                        |
| `retries`                                                                                                 | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                          | :heavy_minus_sign:                                                                                        | Configuration to override the default retry behavior of the client.                                       |

### Response

**[models.PlanResponseSchema](../../models/planresponseschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.UpdatePlanBadRequestError    | 400                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## delete

Permanently delete a subscription plan

### Example Usage

<!-- UsageSnippet language="python" operationID="DeletePlan" method="delete" path="/subscription/plans/{plan_id}" -->
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

    res = ma_client.subscription_plans.delete(plan_id=308803)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `plan_id`                                                           | *int*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.MessageResponseSchema](../../models/messageresponseschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.DeletePlanBadRequestError    | 400                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## update_storage_tiers

Update the storage tier pricing for a subscription plan

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateStorageTiers" method="put" path="/subscription/plans/{plan_id}/storage-tiers" -->
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

    res = ma_client.subscription_plans.update_storage_tiers(plan_id=962633, storage_tiers=[])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                       | Type                                                                            | Required                                                                        | Description                                                                     |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| `plan_id`                                                                       | *int*                                                                           | :heavy_check_mark:                                                              | N/A                                                                             |
| `storage_tiers`                                                                 | List[[models.SchemaStorageTierSchema](../../models/schemastoragetierschema.md)] | :heavy_check_mark:                                                              | N/A                                                                             |
| `retries`                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                | :heavy_minus_sign:                                                              | Configuration to override the default retry behavior of the client.             |

### Response

**[models.PlanResponseSchema](../../models/planresponseschema.md)**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| errors.UpdateStorageTiersBadRequestError | 400                                      | application/json                         |
| errors.MammothAnalyticsDefaultError      | 4XX, 5XX                                 | \*/\*                                    |