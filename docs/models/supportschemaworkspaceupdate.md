# SupportSchemaWorkspaceUpdate

Update workspace schema details


## Fields

| Field                                                                    | Type                                                                     | Required                                                                 | Description                                                              | Example                                                                  |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| `name`                                                                   | *str*                                                                    | :heavy_check_mark:                                                       | Name of the workspace to be created                                      | {<br/>"summary": "Sample Workspace Name",<br/>"value": "Sample Workspace Name"<br/>} |
| `plan_id`                                                                | *int*                                                                    | :heavy_check_mark:                                                       | Plan ID                                                                  | {<br/>"summary": "Sample Plan ID",<br/>"value": "internal"<br/>}         |
| `payment_frequency`                                                      | *str*                                                                    | :heavy_check_mark:                                                       | Payment frequency of the workspace                                       | {<br/>"summary": "Sample Payment Frequency",<br/>"value": "monthly"<br/>} |