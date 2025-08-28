# Self
(*self_*)

## Overview

### Available Operations

* [upload_profile_pic](#upload_profile_pic) - Add profile picture
* [delete_avatar](#delete_avatar) - Delete profile picture
* [delete](#delete) - Delete self
* [update_user](#update_user) - Update user details

## upload_profile_pic

Add a profile picture (avatar) to the user

### Example Usage

<!-- UsageSnippet language="python" operationID="UploadProfilePic" method="post" path="/self/avatar" -->
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

    ma_client.self_.upload_profile_pic()

    # Use the SDK ...

```

### Parameters

| Parameter                                                                     | Type                                                                          | Required                                                                      | Description                                                                   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `file`                                                                        | [Optional[models.UploadProfilePicFile]](../../models/uploadprofilepicfile.md) | :heavy_minus_sign:                                                            | N/A                                                                           |
| `retries`                                                                     | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)              | :heavy_minus_sign:                                                            | Configuration to override the default retry behavior of the client.           |

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| errors.UploadProfilePicResponseBodyError1 | 400                                       | application/json                          |
| errors.UploadProfilePicResponseBodyError2 | 400                                       | application/json                          |
| errors.UploadProfilePicUnauthorizedError  | 401                                       | application/json                          |
| errors.MammothAnalyticsDefaultError       | 4XX, 5XX                                  | \*/\*                                     |

## delete_avatar

Delete the profile picture (avatar) of the user

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteAvatar" method="delete" path="/self/avatar" -->
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

    ma_client.self_.delete_avatar()

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| errors.DeleteAvatarBadRequestError   | 400                                  | application/json                     |
| errors.DeleteAvatarUnauthorizedError | 401                                  | application/json                     |
| errors.MammothAnalyticsDefaultError  | 4XX, 5XX                             | \*/\*                                |

## delete

Delete self

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteSelf" method="delete" path="/self" -->
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

    ma_client.self_.delete(validate_only=True)

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `validate_only`                                                     | *Optional[bool]*                                                    | :heavy_minus_sign:                                                  | Validate only for deleting self user                                | true                                                                |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.DeleteSelfResponseBodyError1 | 400                                 | application/json                    |
| errors.DeleteSelfResponseBodyError2 | 400                                 | application/json                    |
| errors.DeleteSelfUnauthorizedError  | 401                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## update_user

Update the details of the user

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateUser" method="patch" path="/self" -->
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

    ma_client.self_.update_user(patch=[
        {
            "op": models.SelfPatchDataOperation.REPLACE,
            "path": models.SelfPatchDataPath.FIRST_NAME,
            "value": "John",
        },
        {
            "op": models.SelfPatchDataOperation.REPLACE,
            "path": models.SelfPatchDataPath.LAST_NAME,
            "value": "Cena",
        },
        {
            "op": models.SelfPatchDataOperation.REPLACE,
            "path": models.SelfPatchDataPath.PASSWORD,
            "value": "{\"summary\":\"Sample str value\",\"value\":\"Adom\"}",
        },
        {
            "op": models.SelfPatchDataOperation.ADD,
            "path": models.SelfPatchDataPath.MFA,
            "value": "",
        },
        {
            "op": models.SelfPatchDataOperation.REMOVE,
            "path": models.SelfPatchDataPath.MFA,
            "value": "",
        },
    ])

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `patch`                                                             | List[[models.SelfPatchData](../../models/selfpatchdata.md)]         | :heavy_check_mark:                                                  | N/A                                                                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.UpdateUserResponseBodyError1 | 400                                 | application/json                    |
| errors.UpdateUserResponseBodyError2 | 400                                 | application/json                    |
| errors.UpdateUserUnauthorizedError  | 401                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |