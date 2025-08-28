# CreateConnectorRequestSchema


## Fields

| Field                        | Type                         | Required                     | Description                  |
| ---------------------------- | ---------------------------- | ---------------------------- | ---------------------------- |
| `name`                       | *str*                        | :heavy_check_mark:           | Connector name               |
| `description`                | *OptionalNullable[str]*      | :heavy_minus_sign:           | Connector description        |
| `price_per_month`            | *Optional[float]*            | :heavy_minus_sign:           | Monthly price in USD         |
| `enabled`                    | *Optional[bool]*             | :heavy_minus_sign:           | Whether connector is enabled |