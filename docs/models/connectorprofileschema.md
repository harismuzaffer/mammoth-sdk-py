# ConnectorProfileSchema


## Fields

| Field                                                        | Type                                                         | Required                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `id`                                                         | *int*                                                        | :heavy_check_mark:                                           | N/A                                                          |
| `name`                                                       | *str*                                                        | :heavy_check_mark:                                           | N/A                                                          |
| `description`                                                | *OptionalNullable[str]*                                      | :heavy_minus_sign:                                           | N/A                                                          |
| `created_at`                                                 | *OptionalNullable[str]*                                      | :heavy_minus_sign:                                           | N/A                                                          |
| `updated_at`                                                 | *OptionalNullable[str]*                                      | :heavy_minus_sign:                                           | N/A                                                          |
| `connectors`                                                 | List[[models.ConnectorSchema](../models/connectorschema.md)] | :heavy_check_mark:                                           | N/A                                                          |
| `connectors_count`                                           | *int*                                                        | :heavy_check_mark:                                           | N/A                                                          |
| `used_in_plans`                                              | List[*str*]                                                  | :heavy_check_mark:                                           | N/A                                                          |
| `plan_count`                                                 | *int*                                                        | :heavy_check_mark:                                           | N/A                                                          |