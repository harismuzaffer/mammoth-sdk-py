# ExternalKeys
(*external_keys*)

## Overview

### Available Operations

* [get_by_workspace_id](#get_by_workspace_id) - Get external keys of the given Workspace ID
* [add](#add) - Add external keys to access the intended services
* [delete](#delete) - Delete an external key

## get_by_workspace_id


        This endpoint fetches all external keys added as part of the given Workspace ID
        

### Example Usage

<!-- UsageSnippet language="python" operationID="GetKeysByWorkspaceId" method="get" path="/workspaces/{workspace_id}/external_keys" -->
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

    res = ma_client.external_keys.get_by_workspace_id(workspace_id=4, fields="key_type,key_name,created_by_user_id", limit=10, offset=10, sort="(id:asc)", key_type=models.FilterByKeyType.OPEN_AI)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `fields`                                                                                       | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Fields to be returned in a comma-separated format. Check full mode for all fields.             | key_type,key_name,created_by_user_id                                                           |
| `limit`                                                                                        | *Optional[int]*                                                                                | :heavy_minus_sign:                                                                             | Max number of result to return                                                                 | 10                                                                                             |
| `offset`                                                                                       | *Optional[int]*                                                                                | :heavy_minus_sign:                                                                             | Distance from the beginning of the list of results                                             | 10                                                                                             |
| `sort`                                                                                         | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Returned results are sorted by the combination of the given fields.                            | (id:asc)                                                                                       |
| `key_type`                                                                                     | [OptionalNullable[models.FilterByKeyType]](../../models/filterbykeytype.md)                    | :heavy_minus_sign:                                                                             | Returns all tasks where key type matches the given type                                        | open_ai                                                                                        |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ExternalKeysPaginated](../../models/externalkeyspaginated.md)**

### Errors

| Error Type                                    | Status Code                                   | Content Type                                  |
| --------------------------------------------- | --------------------------------------------- | --------------------------------------------- |
| errors.GetKeysByWorkspaceIDResponseBodyError1 | 400                                           | application/json                              |
| errors.GetKeysByWorkspaceIDResponseBodyError2 | 400                                           | application/json                              |
| errors.MammothAnalyticsDefaultError           | 4XX, 5XX                                      | \*/\*                                         |

## add

External keys that lets Mammoth to user certain services. User brings their own key to access the service e.g AI based rules need an Open AI key

### Example Usage

<!-- UsageSnippet language="python" operationID="AddExternalKey" method="post" path="/workspaces/{workspace_id}/external_keys" -->
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

    res = ma_client.external_keys.add(workspace_id=4, key_type=models.AddExternalKeySpecKeyType.OPEN_AI, key_name="My Open AI key", secure_key="abcDefGhiJklMnoPqrStuVwxYz1234567890", description=None)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `key_type`                                                                                     | [models.AddExternalKeySpecKeyType](../../models/addexternalkeyspeckeytype.md)                  | :heavy_check_mark:                                                                             | Type of the external key e.g. open_ai                                                          | {<br/>"value": "open_ai"<br/>}                                                                 |
| `key_name`                                                                                     | *str*                                                                                          | :heavy_check_mark:                                                                             | A name to be associated with the key                                                           | {<br/>"value": "Mammmoth Open AI"<br/>}                                                        |
| `secure_key`                                                                                   | *str*                                                                                          | :heavy_check_mark:                                                                             | The key value which will be used in the intended service                                       | {<br/>"value": "abcDefGhiJklMnoPqrStuVwxYz1234567890"<br/>}                                    |
| `description`                                                                                  | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Describe the purpose of the key and any added information related to it                        |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ExternalKey](../../models/externalkey.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## delete

Delete an external key from the DB. Doesnt not delete the corresponding key from the service

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteExternalKey" method="delete" path="/workspaces/{workspace_id}/external_keys/{key_id}" -->
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

    ma_client.external_keys.delete(workspace_id=4, key_id=121)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `key_id`                                                                                       | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of an external key                                                                          | 121                                                                                            |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |