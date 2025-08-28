# AddUserSupport

Details of the workspace to be created


## Fields

| Field                                                           | Type                                                            | Required                                                        | Description                                                     | Example                                                         |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| `first_name`                                                    | *OptionalNullable[str]*                                         | :heavy_minus_sign:                                              | First name of the user                                          | {<br/>"summary": "Sample First Name",<br/>"value": "Jacob"<br/>} |
| `last_name`                                                     | *OptionalNullable[str]*                                         | :heavy_minus_sign:                                              | Last name of the user                                           | {<br/>"summary": "Sample Last Name",<br/>"value": "van"<br/>}   |
| `email`                                                         | *str*                                                           | :heavy_check_mark:                                              | Email of the customer                                           | {<br/>"value": "kia@example.com"<br/>}                          |
| `role`                                                          | [models.AddUserSupportRole](../models/addusersupportrole.md)    | :heavy_check_mark:                                              | Role of the user                                                | {<br/>"summary": "Sample User Roles",<br/>"value": "workspace_member"<br/>} |