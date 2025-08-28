# AddRemoveBatchColumns


## Fields

| Field                                            | Type                                             | Required                                         | Description                                      | Example                                          |
| ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ |
| `add`                                            | List[*str*]                                      | :heavy_check_mark:                               | List of columns to be added to batch_columns     | {<br/>"value": [<br/>"batch_table_col_id"<br/>]<br/>} |
| `remove`                                         | List[*str*]                                      | :heavy_check_mark:                               | List of columns to be removed from batch_columns | {<br/>"value": [<br/>"batch_table_col_row_count"<br/>]<br/>} |