# DatasetsPatchOperation


## Fields

| Field                                               | Type                                                | Required                                            | Description                                         | Example                                             |
| --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- |
| `op`                                                | *Literal["replace"]*                                | :heavy_check_mark:                                  | Operation                                           | {<br/>"value": "replace"<br/>}                      |
| `path`                                              | *Literal["name"]*                                   | :heavy_check_mark:                                  | Path                                                | {<br/>"value": "name"<br/>}                         |
| `value`                                             | Dict[str, *str*]                                    | :heavy_check_mark:                                  | Rename datasets                                     | {<br/>"value": {<br/>"34": "new_name",<br/>"35": "new_name"<br/>}<br/>} |