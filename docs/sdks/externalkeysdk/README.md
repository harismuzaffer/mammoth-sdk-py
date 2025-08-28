# ExternalKeySDK
(*external_key*)

## Overview

### Available Operations

* [get](#get) - Get the given external key

## get


        Fetches information about an external_key, optionally returns validation info
        

### Example Usage

<!-- UsageSnippet language="python" operationID="GetExternalKey" method="get" path="/workspaces/{workspace_id}/external_keys/{key_id}" -->
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

    res = ma_client.external_key.get(workspace_id=4, key_id=121, fields="key_type,key_name,created_by_user_id", validate=True)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `key_id`                                                                                       | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of an external key                                                                          | 121                                                                                            |
| `fields`                                                                                       | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Fields to be returned in a comma-separated format. Check full mode for all fields.             | key_type,key_name,created_by_user_id                                                           |
| `validate_`                                                                                    | *OptionalNullable[bool]*                                                                       | :heavy_minus_sign:                                                                             | When True, Validates the key                                                                   | true                                                                                           |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ExternalKeyResp](../../models/externalkeyresp.md)**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.GetExternalKeyResponseBodyError1 | 400                                     | application/json                        |
| errors.GetExternalKeyResponseBodyError2 | 400                                     | application/json                        |
| errors.GetExternalKeyNotFoundError      | 404                                     | application/json                        |
| errors.MammothAnalyticsDefaultError     | 4XX, 5XX                                | \*/\*                                   |