# Schedules
(*schedules*)

## Overview

### Available Operations

* [list](#list) - Get list of schedules
* [create](#create) - Create schedule
* [get](#get) - Get schedule data
* [delete](#delete) - Delete schedule data
* [patch](#patch) - Patch schedule related data

## list

Get list of schedules

### Example Usage

<!-- UsageSnippet language="python" operationID="ListSchedules" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/schedules" -->
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

    res = ma_client.schedules.list(workspace_id=4, project_id=4, fields="id,email")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `fields`                                                                                       | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Fields to return. Can be (id, email)                                                           | id,email                                                                                       |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[List[models.ScheduleSchemaFields]](../../models/.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## create

Create schedule

### Example Usage

<!-- UsageSnippet language="python" operationID="CreateSchedule" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/schedules" -->
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

    res = ma_client.schedules.create(workspace_id=4, project_id=4, rrule={
        "interval": 5,
        "frequency": models.RruleSchemaFrequency.MINUTELY,
        "start": parse_datetime("2025-08-28T23:32:40.194132"),
        "by_week_day": [],
        "by_month_day": [],
    }, work_items=[
        {
            "name": "pull_cloud_data",
            "execution_params": {},
            "args": [
                2586,
            ],
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
| `rrule`                                                                                        | [models.RruleSchema](../../models/rruleschema.md)                                              | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `work_items`                                                                                   | List[[models.WorkItemSchema](../../models/workitemschema.md)]                                  | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.CreateScheduleResponse](../../models/createscheduleresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## get

Get requested schedule data

### Example Usage

<!-- UsageSnippet language="python" operationID="GetSchedule" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/schedules/{schedule_id}" -->
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

    res = ma_client.schedules.get(workspace_id=4, project_id=4, schedule_id=4, fields="id,email")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `schedule_id`                                                                                  | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the schedule                                                                             | 4                                                                                              |
| `fields`                                                                                       | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Fields to return. Can be (id, email)                                                           | id,email                                                                                       |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ScheduleSchemaFields](../../models/scheduleschemafields.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## delete

Delete schedule data

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteSchedule" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/schedules/{schedule_id}" -->
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

    ma_client.schedules.delete(workspace_id=4, project_id=4, schedule_id=4, force=False)

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `schedule_id`                                                                                  | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the schedule                                                                             | 4                                                                                              |
| `force`                                                                                        | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | Is force delete                                                                                | false                                                                                          |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.DeleteScheduleResponseBodyError1 | 400                                     | application/json                        |
| errors.DeleteScheduleResponseBodyError2 | 400                                     | application/json                        |
| errors.DeleteScheduleUnauthorizedError  | 401                                     | application/json                        |
| errors.MammothAnalyticsDefaultError     | 4XX, 5XX                                | \*/\*                                   |

## patch

Patch schedule related data

### Example Usage

<!-- UsageSnippet language="python" operationID="PatchSchedule" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/schedules/{schedule_id}" -->
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

    res = ma_client.schedules.patch(workspace_id=4, project_id=4, schedule_id=4, patch=[
        {
            "op": models.SchedulePatchDataOp.REPLACE,
            "path": models.SchedulePatchDataPath.RRULE,
            "value": models.SchedulePatchDataValueEnum.RESUME,
        },
        {
            "op": models.SchedulePatchDataOp.ADD,
            "path": models.SchedulePatchDataPath.TASK,
            "value": models.SchedulePatchDataValueEnum.RESUME,
        },
        {
            "op": models.SchedulePatchDataOp.REPLACE,
            "path": models.SchedulePatchDataPath.STATUS,
            "value": models.SchedulePatchDataValueEnum.RESUME,
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
| `schedule_id`                                                                                  | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the schedule                                                                             | 4                                                                                              |
| `patch`                                                                                        | List[[models.SchedulePatchData](../../models/schedulepatchdata.md)]                            | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ScheduleSchemaFields](../../models/scheduleschemafields.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |