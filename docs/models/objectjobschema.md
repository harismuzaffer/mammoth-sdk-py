# ObjectJobSchema


## Fields

| Field                                            | Type                                             | Required                                         | Description                                      | Example                                          |
| ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ |
| `status_code`                                    | *OptionalNullable[int]*                          | :heavy_minus_sign:                               | N/A                                              | {<br/>"value": {<br/>"status_code": 200<br/>}<br/>} |
| `job_id`                                         | *OptionalNullable[int]*                          | :heavy_minus_sign:                               | Created job id                                   |                                                  |
| `failure_reason`                                 | *OptionalNullable[str]*                          | :heavy_minus_sign:                               | Failure reason if status is failure              | {<br/>"value": {<br/>"failure_reason": "Some reason"<br/>}<br/>} |