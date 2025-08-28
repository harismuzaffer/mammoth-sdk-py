# UpdateFeatureRequestSchema


## Fields

| Field                          | Type                           | Required                       | Description                    |
| ------------------------------ | ------------------------------ | ------------------------------ | ------------------------------ |
| `name`                         | *OptionalNullable[str]*        | :heavy_minus_sign:             | Feature name                   |
| `description`                  | *OptionalNullable[str]*        | :heavy_minus_sign:             | Feature description            |
| `price_per_month`              | *OptionalNullable[float]*      | :heavy_minus_sign:             | Monthly price in USD           |
| `enabled`                      | *OptionalNullable[bool]*       | :heavy_minus_sign:             | Whether feature is enabled     |
| `values`                       | List[*str*]                    | :heavy_minus_sign:             | Allowed values for the feature |