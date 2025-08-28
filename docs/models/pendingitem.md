# PendingItem


## Fields

| Field                   | Type                    | Required                | Description             |
| ----------------------- | ----------------------- | ----------------------- | ----------------------- |
| `op_id`                 | *int*                   | :heavy_check_mark:      | N/A                     |
| `op_type`               | *str*                   | :heavy_check_mark:      | N/A                     |
| `op_name`               | *str*                   | :heavy_check_mark:      | N/A                     |
| `source_dataview_id`    | *OptionalNullable[int]* | :heavy_minus_sign:      | N/A                     |
| `additional_info`       | Dict[str, *Any*]        | :heavy_check_mark:      | N/A                     |
| `data_pass_through`     | *bool*                  | :heavy_check_mark:      | N/A                     |
| `data_update_pending`   | *bool*                  | :heavy_check_mark:      | N/A                     |
| `resource`              | Dict[str, *Any*]        | :heavy_check_mark:      | N/A                     |