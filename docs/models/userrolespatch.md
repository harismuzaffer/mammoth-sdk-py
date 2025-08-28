# UserRolesPatch


## Fields

| Field                                                                  | Type                                                                   | Required                                                               | Description                                                            | Example                                                                |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `user_id`                                                              | *OptionalNullable[int]*                                                | :heavy_minus_sign:                                                     | User ID                                                                | {<br/>"value": 1<br/>}                                                 |
| `role`                                                                 | [Optional[models.UserRolesPatchRole]](../models/userrolespatchrole.md) | :heavy_minus_sign:                                                     | Role                                                                   | {<br/>"value": "project_admin"<br/>}                                   |