# PendingPipelineChange


## Fields

| Field                  | Type                   | Required               | Description            |
| ---------------------- | ---------------------- | ---------------------- | ---------------------- |
| `dataview_id`          | *int*                  | :heavy_check_mark:     | N/A                    |
| `dataview_name`        | *str*                  | :heavy_check_mark:     | N/A                    |
| `is_pipeline_in_error` | *bool*                 | :heavy_check_mark:     | N/A                    |
| `datasource_name`      | *str*                  | :heavy_check_mark:     | N/A                    |
| `pending_steps_count`  | *int*                  | :heavy_check_mark:     | N/A                    |
| `tasks_in_error`       | Dict[str, *Any*]       | :heavy_check_mark:     | N/A                    |
| `actions_in_error`     | Dict[str, *Any*]       | :heavy_check_mark:     | N/A                    |