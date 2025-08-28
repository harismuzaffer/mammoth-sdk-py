# FileInfo


## Fields

| Field                                                      | Type                                                       | Required                                                   | Description                                                | Example                                                    |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| `type`                                                     | [Optional[models.FileInfoType]](../models/fileinfotype.md) | :heavy_minus_sign:                                         | Type of the source                                         | sketch                                                     |
| `details`                                                  | [models.FileSource](../models/filesource.md)               | :heavy_check_mark:                                         | Details of the file ds source                              | {<br/>"id": 1,<br/>"file_name": "abcd.csv",<br/>"size": "20 Bytes"<br/>} |