# Automations
(*automations*)

## Overview

### Available Operations

* [list](#list) - Get list of automations
* [create](#create) - Create automation
* [get](#get) - Get automation data
* [delete](#delete) - Delete automation and its tasks
* [update](#update) - Update automation related data

## list

Get list of automations

### Example Usage

<!-- UsageSnippet language="python" operationID="GetList" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/automations" -->
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

    res = ma_client.automations.list(workspace_id=4, project_id=4, fields="id,name", id="1,2,3", name="automation_name1,automation_name2,automation_name3", status="processing,action_needed", created_at="(from:'2023-12-19T09:39:17.628Z',to:'2023-12-26T09:42:43.152Z')", updated_at="(from:'2023-12-19T09:39:17.628Z',to:'2023-12-26T09:42:43.152Z')", limit=10, offset=10, sort="(id:asc),(name:asc)")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      | Example                                                                                          |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `workspace_id`                                                                                   | *int*                                                                                            | :heavy_check_mark:                                                                               | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.   | 4                                                                                                |
| `project_id`                                                                                     | *int*                                                                                            | :heavy_check_mark:                                                                               | Project ID of the workspace                                                                      | 4                                                                                                |
| `fields`                                                                                         | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Fields to be returned in a comma-separated format may include id, name, status_info, created_at. | id,name                                                                                          |
| `id`                                                                                             | *Optional[str]*                                                                                  | :heavy_minus_sign:                                                                               | Track multiple automation ids, comma separated                                                   | 1,2,3                                                                                            |
| `name`                                                                                           | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Track multiple automation names, comma separated                                                 | automation_name1,automation_name2,automation_name3                                               |
| `status`                                                                                         | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Track multiple automation statuses, comma separated                                              | processing,action_needed                                                                         |
| `created_at`                                                                                     | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Track multiple automations, which falls under created_at date range                              | (from:'2023-12-19T09:39:17.628Z',to:'2023-12-26T09:42:43.152Z')                                  |
| `updated_at`                                                                                     | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Track multiple automations, which falls under updated_at date range                              | (from:'2023-12-19T09:39:17.628Z',to:'2023-12-26T09:42:43.152Z')                                  |
| `limit`                                                                                          | *Optional[int]*                                                                                  | :heavy_minus_sign:                                                                               | Max number of result to return                                                                   | 10                                                                                               |
| `offset`                                                                                         | *Optional[int]*                                                                                  | :heavy_minus_sign:                                                                               | Distance from the beginning of the list of results                                               | 10                                                                                               |
| `sort`                                                                                           | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Sort the automations based on the fields                                                         | (id:asc),(name:asc)                                                                              |
| `retries`                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                 | :heavy_minus_sign:                                                                               | Configuration to override the default retry behavior of the client.                              |                                                                                                  |

### Response

**[models.AutomationsList](../../models/automationslist.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Create automation

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateAutomation" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/automations" -->
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

    res = ma_client.automations.create(workspace_id=4, project_id=4, name="automation test", description="automation test description", tasks=[
        {
            "task_type": models.AutomationTaskSchemaTaskType.APPEND_DATA,
            "details": {
                "destination_dataset_ids": [
                    6,
                ],
                "source_folder_resource_id": 1,
            },
            "conditions": [
                {},
            ],
        },
    ], conditions=[
        {
            "condition_type": models.AutomationConditionSchemaConditionType.NEW_DATA_ADDITION_IN_FOLDER,
            "details": {
                "start_now": False,
                "file_contains": "{\"summary\":\"Sample Name Pattern\",\"value\":\"abc\"}",
            },
        },
    ], condition_mode=models.ConditionMode.OR)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                  | Type                                                                                                                                                                                                                                                                                       | Required                                                                                                                                                                                                                                                                                   | Description                                                                                                                                                                                                                                                                                | Example                                                                                                                                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `workspace_id`                                                                                                                                                                                                                                                                             | *int*                                                                                                                                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                                                                                                                                         | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.                                                                                                                                                                                             | 4                                                                                                                                                                                                                                                                                          |
| `project_id`                                                                                                                                                                                                                                                                               | *int*                                                                                                                                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                                                                                                                                         | Project ID of the workspace                                                                                                                                                                                                                                                                | 4                                                                                                                                                                                                                                                                                          |
| `name`                                                                                                                                                                                                                                                                                     | *str*                                                                                                                                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                                                                                                                                         | Name                                                                                                                                                                                                                                                                                       | {<br/>"summary": "Sample name",<br/>"value": "automation abc"<br/>}                                                                                                                                                                                                                        |
| `description`                                                                                                                                                                                                                                                                              | *str*                                                                                                                                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                                                                                                                                         | Description                                                                                                                                                                                                                                                                                | {<br/>"summary": "Sample description",<br/>"value": "automation description"<br/>}                                                                                                                                                                                                         |
| `tasks`                                                                                                                                                                                                                                                                                    | List[[models.AutomationTaskSchema](../../models/automationtaskschema.md)]                                                                                                                                                                                                                  | :heavy_check_mark:                                                                                                                                                                                                                                                                         | Tasks                                                                                                                                                                                                                                                                                      | {<br/>"summary": "Sample tasks",<br/>"value": [<br/>{<br/>"task_type": "run_data_retrieval",<br/>"details": [<br/>{<br/>"ds_id": 456<br/>},<br/>{<br/>"ds_id": 555<br/>}<br/>]<br/>}<br/>]<br/>}                                                                                           |
| `conditions`                                                                                                                                                                                                                                                                               | List[[models.AutomationConditionSchema](../../models/automationconditionschema.md)]                                                                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                                                                                                                         | Conditions                                                                                                                                                                                                                                                                                 | {<br/>"summary": "Sample conditions",<br/>"value": [<br/>{<br/>"condition_type": "at_specific_time",<br/>"details": {<br/>"frequency": "monthly",<br/>"interval": 1,<br/>"start_at": "2025-08-06 10:56:20Z",<br/>"until": "2025-09-12 10:56:20Z",<br/>"by_week_day": [<br/>"mo"<br/>],<br/>"by_month_day": [<br/>1,<br/>2<br/>],<br/>"start_now": true<br/>}<br/>}<br/>]<br/>} |
| `condition_mode`                                                                                                                                                                                                                                                                           | [Optional[models.ConditionMode]](../../models/conditionmode.md)                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                         | Condition Mode                                                                                                                                                                                                                                                                             | {<br/>"summary": "Sample condition type",<br/>"value": "and"<br/>}                                                                                                                                                                                                                         |
| `retries`                                                                                                                                                                                                                                                                                  | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                                                                                           | :heavy_minus_sign:                                                                                                                                                                                                                                                                         | Configuration to override the default retry behavior of the client.                                                                                                                                                                                                                        |                                                                                                                                                                                                                                                                                            |

### Response

**[models.CreateAutomationResponse](../../models/createautomationresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## get

Get requested automation data

### Example Usage

<!-- UsageSnippet language="python" operationID="GetAutomation" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/automations/{automation_id}" -->
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

    res = ma_client.automations.get(workspace_id=4, project_id=4, automation_id=4, fields="id,name")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                        | Type                                                                                             | Required                                                                                         | Description                                                                                      | Example                                                                                          |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `workspace_id`                                                                                   | *int*                                                                                            | :heavy_check_mark:                                                                               | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.   | 4                                                                                                |
| `project_id`                                                                                     | *int*                                                                                            | :heavy_check_mark:                                                                               | Project ID of the workspace                                                                      | 4                                                                                                |
| `automation_id`                                                                                  | *int*                                                                                            | :heavy_check_mark:                                                                               | ID of the automation                                                                             | 4                                                                                                |
| `fields`                                                                                         | *OptionalNullable[str]*                                                                          | :heavy_minus_sign:                                                                               | Fields to be returned in a comma-separated format may include id, name, status_info, created_at. | id,name                                                                                          |
| `retries`                                                                                        | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                 | :heavy_minus_sign:                                                                               | Configuration to override the default retry behavior of the client.                              |                                                                                                  |

### Response

**[models.AutomationDetails](../../models/automationdetails.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## delete

Delete automation data

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteAutomation" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/automations/{automation_id}" -->
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

    ma_client.automations.delete(workspace_id=4, project_id=4, automation_id=4)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `automation_id`                                                                                | *int*                                                                                          | :heavy_check_mark:                                                                             | ID of the automation                                                                           | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| errors.DeleteAutomationResponseBodyError1 | 400                                       | application/json                          |
| errors.DeleteAutomationResponseBodyError2 | 400                                       | application/json                          |
| errors.DeleteAutomationUnauthorizedError  | 401                                       | application/json                          |
| errors.MammothAnalyticsDefaultError       | 4XX, 5XX                                  | \*/\*                                     |

## update

Update automation related data

### Example Usage

<!-- UsageSnippet language="python" operationID="UpdateAutomation" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/automations/{automation_id}" -->
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

    res = ma_client.automations.update(workspace_id=4, project_id=4, automation_id=4, patch=[
        {
            "op": models.AutomationPatchDataOperation.REPLACE,
            "path": models.AutomationPatchDataPath.DETAILS,
            "value": {},
        },
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `automation_id`                                                                                | *int*                                                                                          | :heavy_check_mark:                                                                             | ID of the automation                                                                           | 4                                                                                              |
| `patch`                                                                                        | List[[models.AutomationPatchData](../../models/automationpatchdata.md)]                        | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.UpdateAutomationResponse](../../models/updateautomationresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |