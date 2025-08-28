# UpdateQuerySpec

Value to update query for a dataset


## Fields

| Field                                                   | Type                                                    | Required                                                | Description                                             | Example                                                 |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| `query`                                                 | *str*                                                   | :heavy_check_mark:                                      | Query to update                                         | {<br/>"value": "SELECT * FROM \"base_templates\" limit 1"<br/>} |
| `ds_id`                                                 | *int*                                                   | :heavy_check_mark:                                      | Dataset ID                                              | {<br/>"value": 2605<br/>}                               |
| `validate_`                                             | *Optional[bool]*                                        | :heavy_minus_sign:                                      | Validate flag                                           | {<br/>"value": true<br/>}                               |