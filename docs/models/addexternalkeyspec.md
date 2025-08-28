# AddExternalKeySpec

External key specification


## Fields

| Field                                                                      | Type                                                                       | Required                                                                   | Description                                                                | Example                                                                    |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `key_type`                                                                 | [models.AddExternalKeySpecKeyType](../models/addexternalkeyspeckeytype.md) | :heavy_check_mark:                                                         | Type of the external key e.g. open_ai                                      | {<br/>"value": "open_ai"<br/>}                                             |
| `key_name`                                                                 | *str*                                                                      | :heavy_check_mark:                                                         | A name to be associated with the key                                       | {<br/>"value": "Mammmoth Open AI"<br/>}                                    |
| `description`                                                              | *OptionalNullable[str]*                                                    | :heavy_minus_sign:                                                         | Describe the purpose of the key and any added information related to it    |                                                                            |
| `secure_key`                                                               | *str*                                                                      | :heavy_check_mark:                                                         | The key value which will be used in the intended service                   | {<br/>"value": "abcDefGhiJklMnoPqrStuVwxYz1234567890"<br/>}                |