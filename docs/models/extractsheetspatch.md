# ExtractSheetsPatch


## Fields

| Field                                                     | Type                                                      | Required                                                  | Description                                               | Example                                                   |
| --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- |
| `sheets`                                                  | List[*str*]                                               | :heavy_check_mark:                                        | Sheets to extract                                         | {<br/>"value": [<br/>"Sheet1",<br/>"Sheet2"<br/>]<br/>}   |
| `delete_file_after_extract`                               | *Optional[bool]*                                          | :heavy_minus_sign:                                        | Whether to delete main file after sheet extraction or not | {<br/>"value": true<br/>}                                 |
| `combine_after_extract`                                   | *Optional[bool]*                                          | :heavy_minus_sign:                                        | Whether to combine sheets after sheet extraction or not   | {<br/>"value": false<br/>}                                |