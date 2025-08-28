# CreateFeatureRequestSchema


## Fields

| Field                          | Type                           | Required                       | Description                    |
| ------------------------------ | ------------------------------ | ------------------------------ | ------------------------------ |
| `name`                         | *str*                          | :heavy_check_mark:             | Feature name                   |
| `description`                  | *OptionalNullable[str]*        | :heavy_minus_sign:             | Feature description            |
| `price_per_month`              | *Optional[float]*              | :heavy_minus_sign:             | Monthly price in USD           |
| `enabled`                      | *Optional[bool]*               | :heavy_minus_sign:             | Whether feature is enabled     |
| `values`                       | List[*str*]                    | :heavy_minus_sign:             | Allowed values for the feature |