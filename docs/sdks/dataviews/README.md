# Dataviews
(*dataviews*)

## Overview

### Available Operations

* [list](#list) - Get list of dataviews present in a dataset
* [add](#add) - Create or duplicate dataview
* [delete_multiple](#delete_multiple) - Delete multiple dataviews
* [get_information](#get_information) - Get dataview information
* [delete](#delete) - Delete dataview safely
* [patch](#patch) - Patch dataview
* [get_active_users](#get_active_users) - Get list of active users on this dataview
* [mark_active_user](#mark_active_user) - Mark active user on this dataview
* [get_data](#get_data) - Get dataview data
* [retrievedata](#retrievedata) - Get dataview data
* [ai_suggestions](#ai_suggestions) - Generate AI-based Suggestions for Dataview
* [generate_sql](#generate_sql) - Generate SQL query based on intent
* [generate_profile](#generate_profile) - Generate or Update Dataset Profile

## list

Get list of dataviews present in a dataset

### Example Usage

<!-- UsageSnippet language="python" operationID="ListDataviews" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews" -->
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

    res = ma_client.dataviews.list(workspace_id=4, project_id=4, dataset_id=121, fields="id,name", limit=2, offset=2, sort="(id:desc)")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                                                              | Type                                                                                                                                                                                                                   | Required                                                                                                                                                                                                               | Description                                                                                                                                                                                                            | Example                                                                                                                                                                                                                |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                                                                                                                                         | *int*                                                                                                                                                                                                                  | :heavy_check_mark:                                                                                                                                                                                                     | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.                                                                                                                         | 4                                                                                                                                                                                                                      |
| `project_id`                                                                                                                                                                                                           | *int*                                                                                                                                                                                                                  | :heavy_check_mark:                                                                                                                                                                                                     | Project ID of the workspace                                                                                                                                                                                            | 4                                                                                                                                                                                                                      |
| `dataset_id`                                                                                                                                                                                                           | *int*                                                                                                                                                                                                                  | :heavy_check_mark:                                                                                                                                                                                                     | Id of the dataset                                                                                                                                                                                                      | 121                                                                                                                                                                                                                    |
| `fields`                                                                                                                                                                                                               | *Optional[str]*                                                                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                                                     | Fields to be returned in a comma-separated format. Check full mode for all fields.                                                                                                                                     | id,name                                                                                                                                                                                                                |
| `limit`                                                                                                                                                                                                                | *Optional[int]*                                                                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                                                     | Limit for how many dataviews to list                                                                                                                                                                                   | 2                                                                                                                                                                                                                      |
| `offset`                                                                                                                                                                                                               | *Optional[int]*                                                                                                                                                                                                        | :heavy_minus_sign:                                                                                                                                                                                                     | Offset for the dataviews list                                                                                                                                                                                          | 2                                                                                                                                                                                                                      |
| `sort`                                                                                                                                                                                                                 | *OptionalNullable[str]*                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                     | Sort is a list of tuples in string format. Tuples are of the form (field, sort_order), separated by comma, where sort_order can be 'asc' or 'desc'. Allowed fields are ['id', 'name', 'ds_id', 'status', 'created_at'] | (id:desc)                                                                                                                                                                                                              |
| `retries`                                                                                                                                                                                                              | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                     | Configuration to override the default retry behavior of the client.                                                                                                                                                    |                                                                                                                                                                                                                        |

### Response

**[models.ListDataviewsResponse](../../models/listdataviewsresponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| errors.ListDataviewsResponseBodyError1 | 400                                    | application/json                       |
| errors.ListDataviewsResponseBodyError2 | 400                                    | application/json                       |
| errors.ListDataviewsUnauthorizedError  | 401                                    | application/json                       |
| errors.ListDataviewsNotFoundError      | 404                                    | application/json                       |
| errors.MammothAnalyticsDefaultError    | 4XX, 5XX                               | \*/\*                                  |

## add

Create or duplicate dataview

### Example Usage

<!-- UsageSnippet language="python" operationID="AddDataview" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews" -->
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

    res = ma_client.dataviews.add(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, name="{\"value\":\"New Dataview\"}", clone_config_from=[object Object])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `dataview_id`                                                                                  | *Optional[int]*                                                                                | :heavy_minus_sign:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `name`                                                                                         | *OptionalNullable[str]*                                                                        | :heavy_minus_sign:                                                                             | Dataview Name                                                                                  | {<br/>"value": "New Dataview"<br/>}                                                            |
| `clone_config_from`                                                                            | *OptionalNullable[int]*                                                                        | :heavy_minus_sign:                                                                             | Clone config from                                                                              | {<br/>"value": {<br/>"clone_config_from": {<br/>"dataview_id": 1<br/>}<br/>}<br/>}             |
| `dataview_config`                                                                              | [OptionalNullable[models.DataviewConfig]](../../models/dataviewconfig.md)                      | :heavy_minus_sign:                                                                             | Dataview Config                                                                                |                                                                                                |
| `extra_condition`                                                                              | [OptionalNullable[models.ExtraCondition]](../../models/extracondition.md)                      | :heavy_minus_sign:                                                                             | Extra Condition                                                                                |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.AddDataviewResponse](../../models/adddataviewresponse.md)**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| errors.AddDataviewResponseBodyError1 | 400                                  | application/json                     |
| errors.AddDataviewResponseBodyError2 | 400                                  | application/json                     |
| errors.AddDataviewUnauthorizedError  | 401                                  | application/json                     |
| errors.AddDataviewNotFoundError      | 404                                  | application/json                     |
| errors.MammothAnalyticsDefaultError  | 4XX, 5XX                             | \*/\*                                |

## delete_multiple

Delete multiple dataviews

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteMultipleDataviews" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews" -->
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

    res = ma_client.dataviews.delete_multiple(workspace_id=4, project_id=4, dataset_id=121, ids="4,5")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `ids`                                                                                          | *str*                                                                                          | :heavy_check_mark:                                                                             | Comma separated integers for the dataviews ids within the dataset                              | 4,5                                                                                            |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.DataviewBulkDelete](../../models/dataviewbulkdelete.md)**

### Errors

| Error Type                                       | Status Code                                      | Content Type                                     |
| ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ |
| errors.DeleteMultipleDataviewsResponseBodyError1 | 400                                              | application/json                                 |
| errors.DeleteMultipleDataviewsResponseBodyError2 | 400                                              | application/json                                 |
| errors.DeleteMultipleDataviewsUnauthorizedError  | 401                                              | application/json                                 |
| errors.DeleteMultipleDataviewsNotFoundError      | 404                                              | application/json                                 |
| errors.MammothAnalyticsDefaultError              | 4XX, 5XX                                         | \*/\*                                            |

## get_information

Get dataview information like id, row_count, column_count, metadata, taskwise info, status, etc

### Example Usage

<!-- UsageSnippet language="python" operationID="GetDataviewInformationIndividual" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}" -->
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

    res = ma_client.dataviews.get_information(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, fields="id,name", sequence=2)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `dataview_id`                                                                                  | *int*                                                                                          | :heavy_check_mark:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `fields`                                                                                       | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Fields to be returned in a comma-separated format. Check full mode for all fields.             | id,name                                                                                        |
| `sequence`                                                                                     | *Optional[int]*                                                                                | :heavy_minus_sign:                                                                             | Sequence number of the dataview task                                                           | 2                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.GetDataviewInformationIndividualResponse](../../models/getdataviewinformationindividualresponse.md)**

### Errors

| Error Type                                                | Status Code                                               | Content Type                                              |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| errors.GetDataviewInformationIndividualResponseBodyError1 | 400                                                       | application/json                                          |
| errors.GetDataviewInformationIndividualResponseBodyError2 | 400                                                       | application/json                                          |
| errors.GetDataviewInformationIndividualUnauthorizedError  | 401                                                       | application/json                                          |
| errors.GetDataviewInformationIndividualNotFoundError      | 404                                                       | application/json                                          |
| errors.MammothAnalyticsDefaultError                       | 4XX, 5XX                                                  | \*/\*                                                     |

## delete

Delete dataview safely

### Example Usage

<!-- UsageSnippet language="python" operationID="DeleteDataview" method="delete" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}" -->
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

    res = ma_client.dataviews.delete(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `dataview_id`                                                                                  | *int*                                                                                          | :heavy_check_mark:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.DataviewBulkDelete](../../models/dataviewbulkdelete.md)**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.DeleteDataviewResponseBodyError1 | 400                                     | application/json                        |
| errors.DeleteDataviewResponseBodyError2 | 400                                     | application/json                        |
| errors.DeleteDataviewUnauthorizedError  | 401                                     | application/json                        |
| errors.DeleteDataviewNotFoundError      | 404                                     | application/json                        |
| errors.MammothAnalyticsDefaultError     | 4XX, 5XX                                | \*/\*                                   |

## patch

Update dataview properties like rename a dataview, reset a dataview, or apply display properties

### Example Usage

<!-- UsageSnippet language="python" operationID="Patch" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}" -->
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

    ma_client.dataviews.patch(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, patch=[
        {
            "op": "replace",
            "path": "name",
            "value": "Renamed Dataview",
        },
    ])

    # Use the SDK ...

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `dataview_id`                                                                                  | *int*                                                                                          | :heavy_check_mark:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `patch`                                                                                        | List[[models.DataviewPatchOp](../../models/dataviewpatchop.md)]                                | :heavy_check_mark:                                                                             | List of patch operations                                                                       | {<br/>"value": [<br/>{<br/>"value": {<br/>"op": "replace",<br/>"path": "name",<br/>"value": "Renamed Dataview"<br/>}<br/>}<br/>]<br/>} |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.PatchResponseBodyError1      | 400                                 | application/json                    |
| errors.PatchResponseBodyError2      | 400                                 | application/json                    |
| errors.PatchUnauthorizedError       | 401                                 | application/json                    |
| errors.PatchNotFoundError           | 404                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## get_active_users

Get list of active users on this dataview

### Example Usage

<!-- UsageSnippet language="python" operationID="GetActiveUsers" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/activities" -->
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

    res = ma_client.dataviews.get_active_users(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `dataview_id`                                                                                  | *int*                                                                                          | :heavy_check_mark:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.GetActiveUsersResponse](../../models/getactiveusersresponse.md)**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.GetActiveUsersResponseBodyError1 | 400                                     | application/json                        |
| errors.GetActiveUsersResponseBodyError2 | 400                                     | application/json                        |
| errors.GetActiveUsersUnauthorizedError  | 401                                     | application/json                        |
| errors.GetActiveUsersNotFoundError      | 404                                     | application/json                        |
| errors.MammothAnalyticsDefaultError     | 4XX, 5XX                                | \*/\*                                   |

## mark_active_user

Mark active user on this dataview

### Example Usage

<!-- UsageSnippet language="python" operationID="MarkActiveUser" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/activities" -->
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

    res = ma_client.dataviews.mark_active_user(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `dataview_id`                                                                                  | *int*                                                                                          | :heavy_check_mark:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.MarkActiveUserResponse](../../models/markactiveuserresponse.md)**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.MarkActiveUserResponseBodyError1 | 400                                     | application/json                        |
| errors.MarkActiveUserResponseBodyError2 | 400                                     | application/json                        |
| errors.MarkActiveUserUnauthorizedError  | 401                                     | application/json                        |
| errors.MarkActiveUserNotFoundError      | 404                                     | application/json                        |
| errors.MammothAnalyticsDefaultError     | 4XX, 5XX                                | \*/\*                                   |

## get_data

Get dataview data

### Example Usage

<!-- UsageSnippet language="python" operationID="GetDataviewData" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/data" -->
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

    res = ma_client.dataviews.get_data(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, sequence=2, offset=1, limit=1, columns=[
        "column_1",
        "column_2",
    ], sort="(column_1:asc)")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                                                  | Type                                                                                                                                                                       | Required                                                                                                                                                                   | Description                                                                                                                                                                | Example                                                                                                                                                                    |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                                                                                             | *int*                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                         | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.                                                                             | 4                                                                                                                                                                          |
| `project_id`                                                                                                                                                               | *int*                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                         | Project ID of the workspace                                                                                                                                                | 4                                                                                                                                                                          |
| `dataset_id`                                                                                                                                                               | *int*                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                         | Id of the dataset                                                                                                                                                          | 121                                                                                                                                                                        |
| `dataview_id`                                                                                                                                                              | *int*                                                                                                                                                                      | :heavy_check_mark:                                                                                                                                                         | Dataview ID of the dataset                                                                                                                                                 | 4                                                                                                                                                                          |
| `sequence`                                                                                                                                                                 | *Optional[int]*                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                         | Sequence number of the dataview task                                                                                                                                       | 2                                                                                                                                                                          |
| `offset`                                                                                                                                                                   | *Optional[int]*                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                         | Offset is the starting position of rows at which we want to fetch data                                                                                                     | 1                                                                                                                                                                          |
| `limit`                                                                                                                                                                    | *Optional[int]*                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                         | Limit is the number of rows we want to fetch                                                                                                                               | 1                                                                                                                                                                          |
| `columns`                                                                                                                                                                  | List[*str*]                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                         | Columns are a list of comma separated column names (within quotes) we want to fetch, enclosed in square brackets. If we don't pass anything, then all columns are fetched. | [<br/>"column_1",<br/>"column_2"<br/>]                                                                                                                                     |
| `sort`                                                                                                                                                                     | *OptionalNullable[str]*                                                                                                                                                    | :heavy_minus_sign:                                                                                                                                                         | Sort is a list of tuples in string format. Tuples are of the form (column_name, sort_order), separated by comma, where sort_order can be 'asc' or 'desc', limited to three | (column_1:asc)                                                                                                                                                             |
| `retries`                                                                                                                                                                  | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                                           | :heavy_minus_sign:                                                                                                                                                         | Configuration to override the default retry behavior of the client.                                                                                                        |                                                                                                                                                                            |

### Response

**[models.JobResponse](../../models/jobresponse.md)**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| errors.GetDataviewDataResponseBodyError1 | 400                                      | application/json                         |
| errors.GetDataviewDataResponseBodyError2 | 400                                      | application/json                         |
| errors.GetDataviewDataUnauthorizedError  | 401                                      | application/json                         |
| errors.GetDataviewDataNotFoundError      | 404                                      | application/json                         |
| errors.MammothAnalyticsDefaultError      | 4XX, 5XX                                 | \*/\*                                    |

## retrievedata

Get dataview data

### Example Usage

<!-- UsageSnippet language="python" operationID="GetDataviewDataPost" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/data" -->
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

    res = ma_client.dataviews.retrievedata(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, sequence=[object Object], offset=[object Object], limit=[object Object], columns=[
        "{\"summary\":\"Sample columns\",\"value\":[\"column_1\",\"column_2\"]}",
    ], condition={}, sort="{\"summary\":\"Sample sort in string format\",\"value\":[\"(column_1:asc),(column_2:desc)\"]}")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                                                          | Type                                                                                                                                               | Required                                                                                                                                           | Description                                                                                                                                        | Example                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                                                                     | *int*                                                                                                                                              | :heavy_check_mark:                                                                                                                                 | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.                                                     | 4                                                                                                                                                  |
| `project_id`                                                                                                                                       | *int*                                                                                                                                              | :heavy_check_mark:                                                                                                                                 | Project ID of the workspace                                                                                                                        | 4                                                                                                                                                  |
| `dataset_id`                                                                                                                                       | *int*                                                                                                                                              | :heavy_check_mark:                                                                                                                                 | Id of the dataset                                                                                                                                  | 121                                                                                                                                                |
| `dataview_id`                                                                                                                                      | *int*                                                                                                                                              | :heavy_check_mark:                                                                                                                                 | Dataview ID of the dataset                                                                                                                         | 4                                                                                                                                                  |
| `sequence`                                                                                                                                         | *Optional[int]*                                                                                                                                    | :heavy_minus_sign:                                                                                                                                 | Sequence Number is the step in pipeline at which we want to fetch data                                                                             | {<br/>"summary": "Sample sequence number",<br/>"value": 1<br/>}                                                                                    |
| `offset`                                                                                                                                           | *Optional[int]*                                                                                                                                    | :heavy_minus_sign:                                                                                                                                 | Offset is the one-indexed starting position of rows to fetch data                                                                                  | {<br/>"summary": "Sample offset",<br/>"value": 1<br/>}                                                                                             |
| `limit`                                                                                                                                            | *Optional[int]*                                                                                                                                    | :heavy_minus_sign:                                                                                                                                 | Limit is the number of rows we want to fetch                                                                                                       | {<br/>"summary": "Sample limit",<br/>"value": 1<br/>}                                                                                              |
| `columns`                                                                                                                                          | List[*str*]                                                                                                                                        | :heavy_minus_sign:                                                                                                                                 | Columns are a list of comma separated column names (within quotes) we want to fetch, enclosed in square brackets                                   | {<br/>"summary": "Sample columns",<br/>"value": [<br/>"column_1",<br/>"column_2"<br/>]<br/>}                                                       |
| `condition`                                                                                                                                        | [OptionalNullable[models.DataviewDataCondition]](../../models/dataviewdatacondition.md)                                                            | :heavy_minus_sign:                                                                                                                                 | Condition is a JSON representation of the condition we want to use while fetching the rows                                                         | {<br/>"summary": "Sample condition",<br/>"value": {<br/>"column_1": {<br/>"operator": "eq",<br/>"value": "value_1"<br/>}<br/>}<br/>}               |
| `sort`                                                                                                                                             | *OptionalNullable[str]*                                                                                                                            | :heavy_minus_sign:                                                                                                                                 | Sort is a list tuples in string format. Tuples are of the form (column_name, sort_order) where sort_order can be 'asc' or 'desc', limited to three | {<br/>"summary": "Sample sort in string format",<br/>"value": [<br/>"(column_1:asc),(column_2:desc)"<br/>]<br/>}                                   |
| `retries`                                                                                                                                          | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                                                   | :heavy_minus_sign:                                                                                                                                 | Configuration to override the default retry behavior of the client.                                                                                |                                                                                                                                                    |

### Response

**[models.JobResponse](../../models/jobresponse.md)**

### Errors

| Error Type                                   | Status Code                                  | Content Type                                 |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| errors.GetDataviewDataPostResponseBodyError1 | 400                                          | application/json                             |
| errors.GetDataviewDataPostResponseBodyError2 | 400                                          | application/json                             |
| errors.GetDataviewDataPostUnauthorizedError  | 401                                          | application/json                             |
| errors.GetDataviewDataPostNotFoundError      | 404                                          | application/json                             |
| errors.MammothAnalyticsDefaultError          | 4XX, 5XX                                     | \*/\*                                        |

## ai_suggestions

Given the prompt, generate AI data againt a sequence number in the pipeline

### Example Usage

<!-- UsageSnippet language="python" operationID="AiSuggestions" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/suggestions" -->
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

    res = ma_client.dataviews.ai_suggestions(workspace_id=4, project_id=4, dataset_id=121, suggestion_type=models.SuggestionType.EXTRACT_TEXT, params={
        "column_name": "comments",
        "sequence_number": 1,
        "prompt": "Extract all mentions of product issues",
        "edit_regex": None,
    }, dataview_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `suggestion_type`                                                                              | [models.SuggestionType](../../models/suggestiontype.md)                                        | :heavy_check_mark:                                                                             | Type of operation (extraction or conditional filtering)                                        |                                                                                                |
| `params`                                                                                       | [models.Params](../../models/params.md)                                                        | :heavy_check_mark:                                                                             | Encapsulated parameters for the operation                                                      |                                                                                                |
| `dataview_id`                                                                                  | *Optional[int]*                                                                                | :heavy_minus_sign:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.AiSuggestionsResponse](../../models/aisuggestionsresponse.md)**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| errors.AiSuggestionsResponseBodyError1 | 400                                    | application/json                       |
| errors.AiSuggestionsResponseBodyError2 | 400                                    | application/json                       |
| errors.MammothAnalyticsDefaultError    | 4XX, 5XX                               | \*/\*                                  |

## generate_sql

Given the intent, generate SQL query for a sequence number in the pipeline

### Example Usage

<!-- UsageSnippet language="python" operationID="GenerateSql" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/sql_generation" -->
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

    res = ma_client.dataviews.generate_sql(workspace_id=4, project_id=4, dataset_id=121, params={
        "sequence_number": 1,
        "intent": "Get all customers who made purchases in the last month",
    }, dataview_id=4)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `params`                                                                                       | [models.SQLGenerationParams](../../models/sqlgenerationparams.md)                              | :heavy_check_mark:                                                                             | Encapsulated SQL generation parameters                                                         |                                                                                                |
| `dataview_id`                                                                                  | *Optional[int]*                                                                                | :heavy_minus_sign:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.GenerateSQLResponse](../../models/generatesqlresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.GenerateSQLUnauthorizedError | 401                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## generate_profile

Triggers AI-based profiling for a given dataview.

### Example Usage

<!-- UsageSnippet language="python" operationID="GenerateProfile" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/profile_generation" -->
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

    res = ma_client.dataviews.generate_profile(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, params={
        "action": models.Action.GET_PROFILE,
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    | Example                                                                                        |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                 | *int*                                                                                          | :heavy_check_mark:                                                                             | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace. | 4                                                                                              |
| `project_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Project ID of the workspace                                                                    | 4                                                                                              |
| `dataset_id`                                                                                   | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of the dataset                                                                              | 121                                                                                            |
| `dataview_id`                                                                                  | *int*                                                                                          | :heavy_check_mark:                                                                             | Dataview ID of the dataset                                                                     | 4                                                                                              |
| `params`                                                                                       | [models.ProfileGenerationParams](../../models/profilegenerationparams.md)                      | :heavy_check_mark:                                                                             | Encapsulated profile generation parameters                                                     |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.JobResponse](../../models/jobresponse.md)**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| errors.GenerateProfileResponseBodyError1 | 400                                      | application/json                         |
| errors.GenerateProfileResponseBodyError2 | 400                                      | application/json                         |
| errors.GenerateProfileUnauthorizedError  | 401                                      | application/json                         |
| errors.MammothAnalyticsDefaultError      | 4XX, 5XX                                 | \*/\*                                    |