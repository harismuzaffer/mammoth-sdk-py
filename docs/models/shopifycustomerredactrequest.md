# ShopifyCustomerRedactRequest

Shopify customer redact details


## Fields

| Field                                                  | Type                                                   | Required                                               | Description                                            | Example                                                |
| ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
| `shop_id`                                              | *int*                                                  | :heavy_check_mark:                                     | Shop Id                                                | {<br/>"value": 113<br/>}                               |
| `shop_domain`                                          | *str*                                                  | :heavy_check_mark:                                     | Shop Domain                                            | {<br/>"value": "shop3.myshopify.com"<br/>}             |
| `customer`                                             | [models.ShopifyCustomer](../models/shopifycustomer.md) | :heavy_check_mark:                                     | N/A                                                    |                                                        |
| `orders_to_redact`                                     | List[*int*]                                            | :heavy_check_mark:                                     | List of orders to redact                               | {<br/>"value": [<br/>299938,<br/>280263<br/>]<br/>}    |