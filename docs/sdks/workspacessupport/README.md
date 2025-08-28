# WorkspacesSupport
(*workspaces_support*)

## Overview

### Available Operations

* [list](#list) - Get workspaces list
* [create](#create) - Create new workspace
* [get_detail](#get_detail) - Get workspace details
* [delete](#delete) - Delete a workspace
* [update_detail](#update_detail) - Update workspace details

## list

Retrieve a comprehensive list of workspaces along with their details.

### Example Usage

<!-- UsageSnippet language="python" operationID="ListWorkspaces" method="get" path="/support/workspaces" -->
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

    res = ma_client.workspaces_support.list()

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |

### Response

**[models.ListWorkspacesResponse](../../models/listworkspacesresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Create new workspace including relevant details.

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateWorkspaces" method="post" path="/support/workspaces" -->
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

    res = ma_client.workspaces_support.create(name="Docs", user_email="test@test.com", payment_frequency="monthly", plan_id=None, is_verified=True, is_registration=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                | Type                                                                     | Required                                                                 | Description                                                              | Example                                                                  |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| `name`                                                                   | *str*                                                                    | :heavy_check_mark:                                                       | Name of the workspace to be created                                      | {<br/>"summary": "Sample Workspace Name",<br/>"value": "Sample Workspace Name"<br/>} |
| `user_email`                                                             | *str*                                                                    | :heavy_check_mark:                                                       | Email of the customer                                                    | {<br/>"value": "kia@example.com"<br/>}                                   |
| `payment_frequency`                                                      | *str*                                                                    | :heavy_check_mark:                                                       | Payment frequency of the workspace                                       | {<br/>"summary": "Sample Payment Frequency",<br/>"value": "monthly"<br/>} |
| `plan_id`                                                                | *OptionalNullable[int]*                                                  | :heavy_minus_sign:                                                       | Plan ID                                                                  | {<br/>"summary": "Sample Plan ID",<br/>"value": "internal"<br/>}         |
| `is_verified`                                                            | *Optional[bool]*                                                         | :heavy_minus_sign:                                                       | Is verified                                                              | {<br/>"summary": "Sample Is verified",<br/>"value": true<br/>}           |
| `is_registration`                                                        | *Optional[bool]*                                                         | :heavy_minus_sign:                                                       | Is registration                                                          | {<br/>"summary": "Sample Is registration",<br/>"value": false<br/>}      |
| `retries`                                                                | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)         | :heavy_minus_sign:                                                       | Configuration to override the default retry behavior of the client.      |                                                                          |

### Response

**[models.JobSchema](../../models/jobschema.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## get_detail

Retrieve details for the specified workspace.

### Example Usage

<!-- UsageSnippet language="python" operationID="GetWorkspaceDetail" method="get" path="/support/workspaces/{workspace_id}" -->
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

    res = ma_client.workspaces_support.get_detail(workspace_id=4, fields="id,name")

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

**[models.GetWorkspaceDetailResponse](../../models/getworkspacedetailresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## delete

Remove the specified workspace.

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteWorkspace" method="delete" path="/support/workspaces/{workspace_id}" -->
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

    ma_client.workspaces_support.delete(workspace_id=4)

    # Use the SDK ...

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `workspace_id`                                                      | *int*                                                               | :heavy_check_mark:                                                  | Id of the workspace to work with                                    | 4                                                                   |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## update_detail

Update details for the specified workspace.

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateWorkspaceDetail" method="patch" path="/support/workspaces/{workspace_id}" -->
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

    res = ma_client.workspaces_support.update_detail(workspace_id=4, name="Docs", plan_id=[object Object], payment_frequency="monthly")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                | Type                                                                     | Required                                                                 | Description                                                              | Example                                                                  |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| `workspace_id`                                                           | *int*                                                                    | :heavy_check_mark:                                                       | Id of the workspace to work with                                         | 4                                                                        |
| `name`                                                                   | *str*                                                                    | :heavy_check_mark:                                                       | Name of the workspace to be created                                      | {<br/>"summary": "Sample Workspace Name",<br/>"value": "Sample Workspace Name"<br/>} |
| `plan_id`                                                                | *int*                                                                    | :heavy_check_mark:                                                       | Plan ID                                                                  | {<br/>"summary": "Sample Plan ID",<br/>"value": "internal"<br/>}         |
| `payment_frequency`                                                      | *str*                                                                    | :heavy_check_mark:                                                       | Payment frequency of the workspace                                       | {<br/>"summary": "Sample Payment Frequency",<br/>"value": "monthly"<br/>} |
| `retries`                                                                | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)         | :heavy_minus_sign:                                                       | Configuration to override the default retry behavior of the client.      |                                                                          |

### Response

**[models.UserList](../../models/userlist.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |