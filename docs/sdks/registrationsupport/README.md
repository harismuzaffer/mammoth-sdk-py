# RegistrationSupport
(*registration_support*)

## Overview

### Available Operations

* [register](#register) - Register a user
* [update_user_verification](#update_user_verification) - Update user details

## register

Register a user with the given details

### Example Usage

<!-- UsageSnippet language="python" operationID="RegisterUser" method="post" path="/support/users" -->
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

    res = ma_client.registration_support.register(email="johnsmith@exmaple.io", first_name="John", last_name="Smith", verified=False, is_registration=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `email`                                                             | *str*                                                               | :heavy_check_mark:                                                  | Email of the customer                                               | {<br/>"value": "kia@example.com"<br/>}                              |
| `first_name`                                                        | *str*                                                               | :heavy_check_mark:                                                  | First Name of the user to register                                  | Sample First Name                                                   |
| `last_name`                                                         | *str*                                                               | :heavy_check_mark:                                                  | Last Name of the user to register                                   | Sample Last Name                                                    |
| `verified`                                                          | *bool*                                                              | :heavy_check_mark:                                                  | Verified status of the user                                         | false                                                               |
| `is_registration`                                                   | *OptionalNullable[bool]*                                            | :heavy_minus_sign:                                                  | Is post request from registration                                   | {<br/>"value": false<br/>}                                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.RegisterResponseSchema](../../models/registerresponseschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## update_user_verification

Update user details

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateUserVerification" method="patch" path="/support/users" -->
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

    res = ma_client.registration_support.update_user_verification(patch=[
        {
            "op": "replace",
            "path": "verified",
            "value": {
                "email": "johnsmith@exmaple.io",
                "verified": True,
            },
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                       | Type                                                                            | Required                                                                        | Description                                                                     |
| ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| `patch`                                                                         | List[[models.RegisterUserPatchSchema](../../models/registeruserpatchschema.md)] | :heavy_check_mark:                                                              | N/A                                                                             |
| `retries`                                                                       | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                | :heavy_minus_sign:                                                              | Configuration to override the default retry behavior of the client.             |

### Response

**[models.RegisterResponseSchema](../../models/registerresponseschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |