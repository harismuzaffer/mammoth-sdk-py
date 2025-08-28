# NumericFormat


## Fields

| Field                                                            | Type                                                             | Required                                                         | Description                                                      |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `comma_separated`                                                | *Optional[bool]*                                                 | :heavy_minus_sign:                                               | Whether to format numbers with commas as thousand separators.    |
| `currency_symbol`                                                | *Optional[str]*                                                  | :heavy_minus_sign:                                               | Symbol to use for currency formatting (empty if not applicable). |
| `decimal_spec`                                                   | *Optional[int]*                                                  | :heavy_minus_sign:                                               | Number of decimal places to display.                             |
| `enabled`                                                        | *Optional[bool]*                                                 | :heavy_minus_sign:                                               | Whether numeric formatting is applied.                           |
| `is_percentage`                                                  | *Optional[bool]*                                                 | :heavy_minus_sign:                                               | Whether the number should be displayed as a percentage.          |
| `numtype`                                                        | [Optional[models.NumberType]](../models/numbertype.md)           | :heavy_minus_sign:                                               | The data type of the number (e.g., int, float).                  |