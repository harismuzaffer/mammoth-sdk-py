# RegisterUserPostSchema

Details of the user to be registered


## Fields

| Field                              | Type                               | Required                           | Description                        | Example                            |
| ---------------------------------- | ---------------------------------- | ---------------------------------- | ---------------------------------- | ---------------------------------- |
| `email`                            | *str*                              | :heavy_check_mark:                 | Email of the customer              | {<br/>"value": "kia@example.com"<br/>} |
| `first_name`                       | *str*                              | :heavy_check_mark:                 | First Name of the user to register | Sample First Name                  |
| `last_name`                        | *str*                              | :heavy_check_mark:                 | Last Name of the user to register  | Sample Last Name                   |
| `verified`                         | *bool*                             | :heavy_check_mark:                 | Verified status of the user        | false                              |
| `is_registration`                  | *OptionalNullable[bool]*           | :heavy_minus_sign:                 | Is post request from registration  | {<br/>"value": false<br/>}         |