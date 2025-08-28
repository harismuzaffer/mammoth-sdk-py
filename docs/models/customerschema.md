# CustomerSchema

Subscription creation details


## Fields

| Field                                                    | Type                                                     | Required                                                 | Description                                              | Example                                                  |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `first_name`                                             | *OptionalNullable[str]*                                  | :heavy_minus_sign:                                       | First Name of the customer                               | {<br/>"summary": "First Name",<br/>"value": "John"<br/>} |
| `last_name`                                              | *OptionalNullable[str]*                                  | :heavy_minus_sign:                                       | Last Name of the customer                                | {<br/>"summary": "Last Name",<br/>"value": "Adom"<br/>}  |
| `email`                                                  | *OptionalNullable[str]*                                  | :heavy_minus_sign:                                       | Email of the customer                                    | {<br/>"summary": "Email",<br/>"value": "example@some.com"<br/>} |
| `company_name`                                           | *OptionalNullable[str]*                                  | :heavy_minus_sign:                                       | Company of the customer                                  | {<br/>"summary": "Company",<br/>"value": "Bad"<br/>}     |
| `plan_id`                                                | *str*                                                    | :heavy_check_mark:                                       | Plan ID of the customer                                  | {<br/>"summary": "Sample Plan ID",<br/>"value": "professional"<br/>} |
| `customer_id`                                            | *OptionalNullable[str]*                                  | :heavy_minus_sign:                                       | ID of the customer                                       | {<br/>"summary": "Customer ID",<br/>"value": "cus_123456789"<br/>} |