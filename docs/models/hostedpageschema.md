# HostedPageSchema

Details of the hosted page


## Fields

| Field                                                        | Type                                                         | Required                                                     | Description                                                  | Example                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `object_type`                                                | *str*                                                        | :heavy_check_mark:                                           | Type of the hosted page                                      | {<br/>"summary": "Sample Page Type",<br/>"value": "portal_session"<br/>} |
| `plan_id`                                                    | *OptionalNullable[str]*                                      | :heavy_minus_sign:                                           | ID of the plan                                               | {<br/>"summary": "Sample Plan ID",<br/>"value": "internal"<br/>} |