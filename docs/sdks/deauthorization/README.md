# Deauthorization
(*deauthorization*)

## Overview

### Available Operations

* [delete_user_data](#delete_user_data) - Delete user's data from the system

## delete_user_data

This endpoint is used to delete user's data from the system

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteUserData" method="post" path="/gdpr_hooks/{integration_name}/deauthorization" -->
```python
from mammoth_analytics import MammothAnalytics, models
from mammoth_analytics.utils import parse_datetime
import os


with MammothAnalytics(
    server_url="https://api.example.com",
    security=models.Security(
        api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
        api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
    ),
) as ma_client:

    res = ma_client.deauthorization.delete_user_data(integration_name=models.IntegrationName.ZOOM, event="app_deauthorized", payload={
        "account_id": "EabCDEFlhiLHMA",
        "client_id": "ADZ9kgbTWmGUoUbECUKU_a",
        "deauthorization_time": parse_datetime("2019-06-17T13:52:28.632Z"),
        "signature": "827ed83452044f0bc86bdd5684afb7d1e6becfa1a767f24df1b287853cf73000",
        "user_id": "z9jkdsfsdfjhdkfjQ",
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `integration_name`                                                  | [models.IntegrationName](../../models/integrationname.md)           | :heavy_check_mark:                                                  | Integration for which the data should be deleted                    | zoom                                                                |
| `event`                                                             | *str*                                                               | :heavy_check_mark:                                                  | Name of the event                                                   | {<br/>"value": "app_deauthorized"<br/>}                             |
| `payload`                                                           | [models.ZoomPayload](../../models/zoompayload.md)                   | :heavy_check_mark:                                                  | N/A                                                                 |                                                                     |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.DeAuthorizationPostResponse](../../models/deauthorizationpostresponse.md)**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| errors.DeleteUserDataBadRequestError | 400                                  | application/json                     |
| errors.MammothAnalyticsDefaultError  | 4XX, 5XX                             | \*/\*                                |