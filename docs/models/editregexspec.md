# EditRegexSpec


## Fields

| Field                                   | Type                                    | Required                                | Description                             |
| --------------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- |
| `expression`                            | *str*                                   | :heavy_check_mark:                      | Regex pattern for extraction            |
| `delimiter`                             | *str*                                   | :heavy_check_mark:                      | Delimiter used in regex pattern         |
| `global_flag`                           | *bool*                                  | :heavy_check_mark:                      | Whether the regex should match globally |
| `capturing_groups`                      | List[*int*]                             | :heavy_check_mark:                      | List of capturing group indices         |