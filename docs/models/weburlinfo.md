# WebURLInfo


## Fields

| Field                                                          | Type                                                           | Required                                                       | Description                                                    | Example                                                        |
| -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- |
| `type`                                                         | [Optional[models.WebURLInfoType]](../models/weburlinfotype.md) | :heavy_minus_sign:                                             | Type of the source                                             | sketch                                                         |
| `details`                                                      | [models.WebURLSource](../models/weburlsource.md)               | :heavy_check_mark:                                             | Details of the web url ds source                               | {<br/>"id": "https://aws.com/efg.csv"<br/>}                    |