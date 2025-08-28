# PatchOperation


## Fields

| Field                                                          | Type                                                           | Required                                                       | Description                                                    | Example                                                        |
| -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- |
| `op`                                                           | *Literal["replace"]*                                           | :heavy_check_mark:                                             | Operation                                                      | {<br/>"value": "replace"<br/>}                                 |
| `path`                                                         | *str*                                                          | :heavy_check_mark:                                             | Path                                                           | {<br/>"value": "name"<br/>}                                    |
| `value`                                                        | [models.PatchOperationValue](../models/patchoperationvalue.md) | :heavy_check_mark:                                             | Value to replace the attribute with                            | {<br/>"value": "New name"<br/>}                                |