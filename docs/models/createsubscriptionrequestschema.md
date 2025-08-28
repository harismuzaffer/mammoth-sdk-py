# CreateSubscriptionRequestSchema


## Fields

| Field                   | Type                    | Required                | Description             |
| ----------------------- | ----------------------- | ----------------------- | ----------------------- |
| `plan_id`               | *int*                   | :heavy_check_mark:      | Plan ID to subscribe to |
| `billing_interval`      | *Optional[str]*         | :heavy_minus_sign:      | Billing interval        |
| `trial_days`            | *Optional[int]*         | :heavy_minus_sign:      | Trial period in days    |
| `customer_email`        | *str*                   | :heavy_check_mark:      | Customer email address  |