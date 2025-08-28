# StatusInfo

Status Info of the file


## Fields

| Field                            | Type                             | Required                         | Description                      | Example                          |
| -------------------------------- | -------------------------------- | -------------------------------- | -------------------------------- | -------------------------------- |
| `extracting`                     | *OptionalNullable[str]*          | :heavy_minus_sign:               | Status extracting info           | {<br/>"value": "requires_password"<br/>} |
| `extracted`                      | *OptionalNullable[str]*          | :heavy_minus_sign:               | Status extracted info            | {<br/>"value": "requires_password"<br/>} |
| `action_needed`                  | *OptionalNullable[str]*          | :heavy_minus_sign:               | Status action needed info        | {<br/>"value": "requires_password"<br/>} |
| `processing`                     | *OptionalNullable[str]*          | :heavy_minus_sign:               | Status processing info           | {<br/>"value": "requires_password"<br/>} |
| `processed`                      | *OptionalNullable[str]*          | :heavy_minus_sign:               | Status processed info            | {<br/>"value": "requires_password"<br/>} |
| `error`                          | *OptionalNullable[str]*          | :heavy_minus_sign:               | Status error info                | {<br/>"value": "requires_password"<br/>} |
| `is_hidden`                      | *Optional[bool]*                 | :heavy_minus_sign:               | Is Hidden                        | {<br/>"value": false<br/>}       |
| `is_empty`                       | *Optional[bool]*                 | :heavy_minus_sign:               | Is Empty                         | {<br/>"value": false<br/>}       |