# DataviewPipelineExports
(*dataview_pipeline_exports*)

## Overview

### Available Operations

* [list](#list) - Get dataview pipeline exports information
* [add](#add) - Add a export in the pipeline
* [get](#get) - Get dataview pipeline export information
* [edit](#edit) - Edit a dataview pipeline export

## list


        This endpoint fetches exports information of exports in a dataview pipeline.
        

### Example Usage

<!-- UsageSnippet language="python" operationID="GetPipelineExports" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/pipeline/exports" -->
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

    res = ma_client.dataview_pipeline_exports.list(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, fields="sequence,status", limit=10, offset=10, sort="(id:asc)", sequence=2, status=models.GetPipelineExportsFilterByStatus.EXECUTED, reorderd=False, handler_type=models.FilterByTheGivenValueOfHandlerType.BIGQUERY, end_of_pipeline=False, runnable=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                                         | Type                                                                                                              | Required                                                                                                          | Description                                                                                                       | Example                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                                    | *int*                                                                                                             | :heavy_check_mark:                                                                                                | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.                    | 4                                                                                                                 |
| `project_id`                                                                                                      | *int*                                                                                                             | :heavy_check_mark:                                                                                                | Project ID of the workspace                                                                                       | 4                                                                                                                 |
| `dataset_id`                                                                                                      | *int*                                                                                                             | :heavy_check_mark:                                                                                                | Id of the dataset                                                                                                 | 121                                                                                                               |
| `dataview_id`                                                                                                     | *int*                                                                                                             | :heavy_check_mark:                                                                                                | Dataview ID of the dataset                                                                                        | 4                                                                                                                 |
| `fields`                                                                                                          | *Optional[str]*                                                                                                   | :heavy_minus_sign:                                                                                                | Fields to be returned in a comma-separated format. Check full mode for all fields.                                | sequence,status                                                                                                   |
| `limit`                                                                                                           | *Optional[int]*                                                                                                   | :heavy_minus_sign:                                                                                                | Max number of result to return                                                                                    | 10                                                                                                                |
| `offset`                                                                                                          | *Optional[int]*                                                                                                   | :heavy_minus_sign:                                                                                                | Distance from the beginning of the list of results                                                                | 10                                                                                                                |
| `sort`                                                                                                            | *Optional[str]*                                                                                                   | :heavy_minus_sign:                                                                                                | Returned results are sorted by the combination of the given fields.                                               | (id:asc)                                                                                                          |
| `sequence`                                                                                                        | *OptionalNullable[int]*                                                                                           | :heavy_minus_sign:                                                                                                | Returns all exports where sequence matches the given value                                                        | 2                                                                                                                 |
| `status`                                                                                                          | [OptionalNullable[models.GetPipelineExportsFilterByStatus]](../../models/getpipelineexportsfilterbystatus.md)     | :heavy_minus_sign:                                                                                                | Returns all exports where status matches the given value                                                          | executed                                                                                                          |
| `reorderd`                                                                                                        | *OptionalNullable[bool]*                                                                                          | :heavy_minus_sign:                                                                                                | Returns all exports where reordered status matches the given value                                                | false                                                                                                             |
| `handler_type`                                                                                                    | [OptionalNullable[models.FilterByTheGivenValueOfHandlerType]](../../models/filterbythegivenvalueofhandlertype.md) | :heavy_minus_sign:                                                                                                | Returns all exports where handler type matches the given value                                                    | bigquery                                                                                                          |
| `end_of_pipeline`                                                                                                 | *OptionalNullable[bool]*                                                                                          | :heavy_minus_sign:                                                                                                | Returns all exports where end of pipeline boolean matches the given value                                         | false                                                                                                             |
| `runnable`                                                                                                        | *OptionalNullable[bool]*                                                                                          | :heavy_minus_sign:                                                                                                | Returns all exports where runnable status matches the given value                                                 | false                                                                                                             |
| `retries`                                                                                                         | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                                  | :heavy_minus_sign:                                                                                                | Configuration to override the default retry behavior of the client.                                               |                                                                                                                   |

### Response

**[models.PipelineExportsPaginated](../../models/pipelineexportspaginated.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| errors.GetPipelineExportsResponseBodyError1 | 400                                         | application/json                            |
| errors.GetPipelineExportsResponseBodyError2 | 400                                         | application/json                            |
| errors.MammothAnalyticsDefaultError         | 4XX, 5XX                                    | \*/\*                                       |

## add

add a new transformation to the dataview. This transformation gets added as a export in the dataview pipeline

### Example Usage

<!-- UsageSnippet language="python" operationID="AddExport" method="post" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/pipeline/exports" -->
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

    res = ma_client.dataview_pipeline_exports.add(workspace_id=4, project_id=4, dataset_id=121, dataview_id_param=4, dataview_id=2311, handler_type=models.AddExportSpecHandlerType.INTERNAL_DATASET, trigger_type=models.AddExportSpecTriggerType.PIPELINE, run_immediately=True, sequence=3, trigger_id=None, end_of_pipeline=True, target_properties={}, additional_properties={}, condition={}, validate_only=False)

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                                               | Type                                                                                                    | Required                                                                                                | Description                                                                                             | Example                                                                                                 |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `workspace_id`                                                                                          | *int*                                                                                                   | :heavy_check_mark:                                                                                      | Workspace refers to a collection of projects. Workspace ID is unique identifier for workspace.          | 4                                                                                                       |
| `project_id`                                                                                            | *int*                                                                                                   | :heavy_check_mark:                                                                                      | Project ID of the workspace                                                                             | 4                                                                                                       |
| `dataset_id`                                                                                            | *int*                                                                                                   | :heavy_check_mark:                                                                                      | Id of the dataset                                                                                       | 121                                                                                                     |
| `dataview_id_param`                                                                                     | *int*                                                                                                   | :heavy_check_mark:                                                                                      | Dataview ID of the dataset                                                                              | 4                                                                                                       |
| `dataview_id`                                                                                           | *int*                                                                                                   | :heavy_check_mark:                                                                                      | N/A                                                                                                     |                                                                                                         |
| `handler_type`                                                                                          | [models.AddExportSpecHandlerType](../../models/addexportspechandlertype.md)                             | :heavy_check_mark:                                                                                      | N/A                                                                                                     |                                                                                                         |
| `trigger_type`                                                                                          | [models.AddExportSpecTriggerType](../../models/addexportspectriggertype.md)                             | :heavy_check_mark:                                                                                      | N/A                                                                                                     |                                                                                                         |
| `run_immediately`                                                                                       | *bool*                                                                                                  | :heavy_check_mark:                                                                                      | N/A                                                                                                     |                                                                                                         |
| `sequence`                                                                                              | *OptionalNullable[int]*                                                                                 | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |                                                                                                         |
| `trigger_id`                                                                                            | *OptionalNullable[int]*                                                                                 | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |                                                                                                         |
| `end_of_pipeline`                                                                                       | *Optional[bool]*                                                                                        | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |                                                                                                         |
| `target_properties`                                                                                     | [Optional[models.AddExportSpecTargetProperties]](../../models/addexportspectargetproperties.md)         | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |                                                                                                         |
| `additional_properties`                                                                                 | [Optional[models.AddExportSpecAdditionalProperties]](../../models/addexportspecadditionalproperties.md) | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |                                                                                                         |
| `condition`                                                                                             | [Optional[models.AddExportSpecCondition]](../../models/addexportspeccondition.md)                       | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |                                                                                                         |
| `validate_only`                                                                                         | *Optional[bool]*                                                                                        | :heavy_minus_sign:                                                                                      | N/A                                                                                                     |                                                                                                         |
| `retries`                                                                                               | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                                        | :heavy_minus_sign:                                                                                      | Configuration to override the default retry behavior of the client.                                     |                                                                                                         |

### Response

**[models.AddExportResponse](../../models/addexportresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.AddExportResponseBodyError1  | 400                                 | application/json                    |
| errors.AddExportResponseBodyError2  | 400                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |

## get


        This endpoint fetches information of a export in a dataview pipeline.
        

### Example Usage

<!-- UsageSnippet language="python" operationID="GetPipelineExport" method="get" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/pipeline/exports/{export_id}" -->
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

    res = ma_client.dataview_pipeline_exports.get(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, export_id=121, fields="sequence,status")

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
| `export_id`                                                                                    | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of a pipeline export                                                                        | 121                                                                                            |
| `fields`                                                                                       | *Optional[str]*                                                                                | :heavy_minus_sign:                                                                             | Fields to be returned in a comma-separated format. Check full mode for all fields.             | sequence,status                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.ItemExportInfo](../../models/itemexportinfo.md)**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| errors.GetPipelineExportResponseBodyError1 | 400                                        | application/json                           |
| errors.GetPipelineExportResponseBodyError2 | 400                                        | application/json                           |
| errors.GetPipelineExportNotFoundError      | 404                                        | application/json                           |
| errors.MammothAnalyticsDefaultError        | 4XX, 5XX                                   | \*/\*                                      |

## edit

Modify a export, e.g. the params, the display_info(e.g. note), status(e.g. suspend a export)

### Example Usage

<!-- UsageSnippet language="python" operationID="EditExport" method="patch" path="/workspaces/{workspace_id}/projects/{project_id}/datasets/{dataset_id}/dataviews/{dataview_id}/pipeline/exports/{export_id}" -->
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

    res = ma_client.dataview_pipeline_exports.edit(workspace_id=4, project_id=4, dataset_id=121, dataview_id=4, export_id=121, patches=[
        {
            "op": models.ItemExportPatchOp.COMMAND,
            "path": models.ItemExportPatchPath.SUSPEND,
            "value": None,
        },
    ], skip_validation=False)

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
| `export_id`                                                                                    | *int*                                                                                          | :heavy_check_mark:                                                                             | Id of a pipeline export                                                                        | 121                                                                                            |
| `patches`                                                                                      | List[[models.ItemExportPatch](../../models/itemexportpatch.md)]                                | :heavy_check_mark:                                                                             | N/A                                                                                            |                                                                                                |
| `skip_validation`                                                                              | *Optional[bool]*                                                                               | :heavy_minus_sign:                                                                             | N/A                                                                                            |                                                                                                |
| `retries`                                                                                      | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)                               | :heavy_minus_sign:                                                                             | Configuration to override the default retry behavior of the client.                            |                                                                                                |

### Response

**[models.EditExportResponse](../../models/editexportresponse.md)**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| errors.EditExportResponseBodyError1 | 400                                 | application/json                    |
| errors.EditExportResponseBodyError2 | 400                                 | application/json                    |
| errors.EditExportNotFoundError      | 404                                 | application/json                    |
| errors.MammothAnalyticsDefaultError | 4XX, 5XX                            | \*/\*                               |