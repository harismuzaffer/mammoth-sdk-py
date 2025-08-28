# Preferences
(*preferences*)

## Overview

### Available Operations

* [get](#get) - Fetch user preferences
* [update](#update) - Update user preferences

## get

This endpoint is used to fetch user preferences.

### Example Usage

<!-- UsageSnippet language="python" operationID="GetUserPreferences" method="get" path="/preferences" -->
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

    res = ma_client.preferences.get()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.PreferencesSchema](../../models/preferencesschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## update

This endpoint is used to update user preferences.

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateUserPreferences" method="patch" path="/preferences" -->
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

    res = ma_client.preferences.update(patch=[
        {
            "op": models.PreferencesPatchOpOp.REPLACE,
            "path": models.PreferencesPatchOpPath.GLOBAL_SELF_SERVE,
            "value": {},
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                             | Type                                                                  | Required                                                              | Description                                                           |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `patch`                                                               | List[[models.PreferencesPatchOp](../../models/preferencespatchop.md)] | :heavy_check_mark:                                                    | N/A                                                                   |
| `retries`                                                             | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)      | :heavy_minus_sign:                                                    | Configuration to override the default retry behavior of the client.   |

### Response

**[Any](../../models/.md)**

### Errors

| Error Type                                     | Status Code                                    | Content Type                                   |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| errors.UpdateUserPreferencesResponseBodyError1 | 400                                            | application/json                               |
| errors.UpdateUserPreferencesResponseBodyError2 | 400                                            | application/json                               |
| errors.MammothAnalyticsDefaultError            | 4XX, 5XX                                       | \*/\*                                          |