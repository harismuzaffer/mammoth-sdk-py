# BatchesPostRequest

Specs for new batch to be created


## Fields

| Field                                                              | Type                                                               | Required                                                           | Description                                                        | Example                                                            |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `source_id`                                                        | *int*                                                              | :heavy_check_mark:                                                 | Source dataset id                                                  | {<br/>"value": 239169<br/>}                                        |
| `mapping`                                                          | [models.Mapping](../models/mapping.md)                             | :heavy_check_mark:                                                 | N/A                                                                |                                                                    |
| `validate_only`                                                    | *bool*                                                             | :heavy_check_mark:                                                 | Validation required                                                | {<br/>"value": true<br/>}                                          |
| `delete_source_ds`                                                 | *bool*                                                             | :heavy_check_mark:                                                 | Delete source dataset                                              | {<br/>"value": false<br/>}                                         |
| `new_ds_details`                                                   | [OptionalNullable[models.NewDsDetails]](../models/newdsdetails.md) | :heavy_minus_sign:                                                 | New dataset details                                                | {<br/>"value": {<br/>"name": "new_dataset_name"<br/>}<br/>}        |