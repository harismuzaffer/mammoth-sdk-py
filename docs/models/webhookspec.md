# WebhookSpec

create webhook


## Fields

| Field                                                            | Type                                                             | Required                                                         | Description                                                      | Example                                                          |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `folder_resource_id`                                             | *OptionalNullable[str]*                                          | :heavy_minus_sign:                                               | Folder resource id                                               | {<br/>"value": "label_1363"<br/>}                                |
| `name`                                                           | *Optional[str]*                                                  | :heavy_minus_sign:                                               | Name of the webhook                                              | {<br/>"value": "test"<br/>}                                      |
| `mode`                                                           | [Optional[models.WebhookSpecMode]](../models/webhookspecmode.md) | :heavy_minus_sign:                                               | Mode of the webhook                                              | {<br/>"value": "combine"<br/>}                                   |
| `origins`                                                        | *Optional[str]*                                                  | :heavy_minus_sign:                                               | Origins                                                          | {<br/>"value": "*"<br/>}                                         |
| `is_secure`                                                      | *Optional[bool]*                                                 | :heavy_minus_sign:                                               | Is secure                                                        | {<br/>"value": true<br/>}                                        |