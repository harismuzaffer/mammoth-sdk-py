# RegisterPatchValueSchema


## Fields

| Field                                                        | Type                                                         | Required                                                     | Description                                                  | Example                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `email`                                                      | *str*                                                        | :heavy_check_mark:                                           | Email of the customer                                        | {<br/>"value": "kia@example.com"<br/>}                       |
| `verified`                                                   | *bool*                                                       | :heavy_check_mark:                                           | Verified status of the user to be updated                    | {<br/>"summary": "Is registered user verified",<br/>"value": false<br/>} |
| `is_registration`                                            | *OptionalNullable[bool]*                                     | :heavy_minus_sign:                                           | Is patch request from registration                           | {<br/>"value": false<br/>}                                   |