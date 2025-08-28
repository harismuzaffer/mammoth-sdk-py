# AddUsersToProject

Add user to a project. Only project_admin and project_analyst are allowed


## Fields

| Field                                                           | Type                                                            | Required                                                        | Description                                                     | Example                                                         |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| `users`                                                         | List[[models.AddUserSpec](../models/adduserspec.md)]            | :heavy_check_mark:                                              | List of user IDs to add to project                              | {<br/>"value": [<br/>{<br/>"user_id": 1,<br/>"role_name": "project_admin"<br/>}<br/>]<br/>} |