# ValidateAndSampleDataSpec

Details of the dataset to be created


## Fields

| Field                                                   | Type                                                    | Required                                                | Description                                             | Example                                                 |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| `profile`                                               | *OptionalNullable[str]*                                 | :heavy_minus_sign:                                      | Profile of the selected connection                      | {<br/>"value": "public"<br/>}                           |
| `query`                                                 | *OptionalNullable[str]*                                 | :heavy_minus_sign:                                      | Query to fetch data from cloud                          | {<br/>"value": "SELECT * FROM \"base_templates\" limit 2"<br/>} |
| `table`                                                 | *OptionalNullable[str]*                                 | :heavy_minus_sign:                                      | Name of the Table                                       | {<br/>"value": "base_templates"<br/>}                   |
| `validate_`                                             | *Optional[bool]*                                        | :heavy_minus_sign:                                      | Validate                                                | {<br/>"value": true<br/>}                               |
| `data_sample`                                           | *Optional[bool]*                                        | :heavy_minus_sign:                                      | Sample data flag                                        | {<br/>"value": true<br/>}                               |
| `file_source`                                           | *OptionalNullable[str]*                                 | :heavy_minus_sign:                                      | Source path of the file                                 | {<br/>"value": "./sftp_test/08.12.21-RFIG.csv"<br/>}    |