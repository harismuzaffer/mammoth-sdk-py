# DatasetCreationSpec

A task specification


## Fields

| Field                                                            | Type                                                             | Required                                                         | Description                                                      | Example                                                          |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `ds_creation_type`                                               | [models.DsCreationType](../models/dscreationtype.md)             | :heavy_check_mark:                                               | Dataset Creation Type                                            | {<br/>"summary": "Sample Dataset Creation Type",<br/>"value": "sketch"<br/>} |
| `folder_resource_id`                                             | *OptionalNullable[str]*                                          | :heavy_minus_sign:                                               | Folder Resource ID                                               | {<br/>"summary": "Folder resource id",<br/>"value": "folder_1"<br/>} |
| `dataset_spec`                                                   | [models.DatasetSpec](../models/datasetspec.md)                   | :heavy_check_mark:                                               | Dataset Specification                                            |                                                                  |