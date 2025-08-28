# FeatureProfiles
(*feature_profiles*)

## Overview

### Available Operations

* [add_feature](#add_feature) - Add feature to profile
* [list](#list) - List all feature profiles
* [create](#create) - Create a new feature profile
* [update](#update) - Update a feature profile
* [delete](#delete) - Delete a feature profile

## add_feature

Add feature to profile

### Example Usage

<!-- UsageSnippet language="python" operationID="AddFeatureToProfile" method="post" path="/subscription/feature-profiles/{profile_id}/features" -->
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

    res = ma_client.feature_profiles.add_feature(profile_id=152994, feature_id=351625, price_per_month=0, enabled=True)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `profile_id`                                                        | *int*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `feature_id`                                                        | *int*                                                               | :heavy_check_mark:                                                  | N/A                                                                 |
| `price_per_month`                                                   | *OptionalNullable[float]*                                           | :heavy_minus_sign:                                                  | N/A                                                                 |
| `enabled`                                                           | *OptionalNullable[bool]*                                            | :heavy_minus_sign:                                                  | N/A                                                                 |
| `value`                                                             | *OptionalNullable[str]*                                             | :heavy_minus_sign:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.AddFeatureToProfileResponseSchema](../../models/addfeaturetoprofileresponseschema.md)**

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| errors.AddFeatureToProfileBadRequestError | 400                                       | application/json                          |
| errors.MammothAnalyticsDefaultError       | 4XX, 5XX                                  | \*/\*                                     |

## list

List all feature profiles

### Example Usage

<!-- UsageSnippet language="python" operationID="ListFeatureProfiles" method="get" path="/subscription/feature-profiles" -->
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

    res = ma_client.feature_profiles.list()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.FeatureProfileListResponseSchema](../../models/featureprofilelistresponseschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Create a new feature profile

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateFeatureProfile" method="post" path="/subscription/feature-profiles" -->
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

    res = ma_client.feature_profiles.create(name="<value>")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                               | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `name`                                                                                  | *str*                                                                                   | :heavy_check_mark:                                                                      | N/A                                                                                     |
| `description`                                                                           | *OptionalNullable[str]*                                                                 | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `features`                                                                              | List[[models.FeatureProfileFeatureSchema](../../models/featureprofilefeatureschema.md)] | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `retries`                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                        | :heavy_minus_sign:                                                                      | Configuration to override the default retry behavior of the client.                     |

### Response

**[models.FeatureProfileResponseSchema](../../models/featureprofileresponseschema.md)**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| errors.CreateFeatureProfileBadRequestError | 400                                        | application/json                           |
| errors.MammothAnalyticsDefaultError        | 4XX, 5XX                                   | \*/\*                                      |

## update

Update a feature profile

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateFeatureProfile" method="put" path="/subscription/feature-profiles/{profile_id}" -->
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

    res = ma_client.feature_profiles.update(profile_id=932060)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                               | Type                                                                                    | Required                                                                                | Description                                                                             |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `profile_id`                                                                            | *int*                                                                                   | :heavy_check_mark:                                                                      | N/A                                                                                     |
| `name`                                                                                  | *OptionalNullable[str]*                                                                 | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `description`                                                                           | *OptionalNullable[str]*                                                                 | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `features`                                                                              | List[[models.FeatureProfileFeatureSchema](../../models/featureprofilefeatureschema.md)] | :heavy_minus_sign:                                                                      | N/A                                                                                     |
| `retries`                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                        | :heavy_minus_sign:                                                                      | Configuration to override the default retry behavior of the client.                     |

### Response

**[models.FeatureProfileResponseSchema](../../models/featureprofileresponseschema.md)**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| errors.UpdateFeatureProfileBadRequestError | 400                                        | application/json                           |
| errors.MammothAnalyticsDefaultError        | 4XX, 5XX                                   | \*/\*                                      |

## delete

Delete a feature profile

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteFeatureProfile" method="delete" path="/subscription/feature-profiles/{profile_id}" -->
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

    res = ma_client.feature_profiles.delete(profile_id=779387)

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

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| errors.DeleteFeatureProfileBadRequestError | 400                                        | application/json                           |
| errors.MammothAnalyticsDefaultError        | 4XX, 5XX                                   | \*/\*                                      |