# InternalDsInfo


## Fields

| Field                                                                  | Type                                                                   | Required                                                               | Description                                                            | Example                                                                |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `type`                                                                 | [Optional[models.InternalDsInfoType]](../models/internaldsinfotype.md) | :heavy_minus_sign:                                                     | Type of the source                                                     | sketch                                                                 |
| `details`                                                              | [models.InternalDsSource](../models/internaldssource.md)               | :heavy_check_mark:                                                     | Details of the internal ds source                                      | {<br/>"id": 1,<br/>"trigger_id": 1<br/>}                               |