# ShopifyPrivacyWebhooks
(*shopify_privacy_webhooks*)

## Overview

### Available Operations

* [redact_customer](#redact_customer) - Delete requested shopify customer orders data from the system
* [data_request](#data_request) - Get requested data of shopify user
* [shop_redact](#shop_redact) - Delete requested shopify shop's data from the system

## redact_customer

Delete requested shopify customer orders data from the system

### Example Usage

<!-- UsageSnippet language="python" operationID="ShopifyCustomerRedact" method="post" path="/gdpr_hooks/shopify/customers/redact" -->
```python
from mammoth_analytics import MammothAnalytics, models
import os


with MammothAnalytics(
    server_url="https://api.example.com",
    security=models.Security(
        api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
        api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
    ),
) as ma_client:

    res = ma_client.shopify_privacy_webhooks.redact_customer(shop_id=954589, shop_domain="shop.myshopify.com", customer={
        "id": 191167,
        "email": "keven@example.com",
        "phone": "555-625-1199",
    }, orders_to_redact=[
        299938,
        225458,
    ])

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `shop_id`                                                           | *int*                                                               | :heavy_check_mark:                                                  | Shop Id                                                             | {<br/>"value": 113<br/>}                                            |
| `shop_domain`                                                       | *str*                                                               | :heavy_check_mark:                                                  | Shop Domain                                                         | {<br/>"value": "shop3.myshopify.com"<br/>}                          |
| `customer`                                                          | [models.ShopifyCustomer](../../models/shopifycustomer.md)           | :heavy_check_mark:                                                  | N/A                                                                 |                                                                     |
| `orders_to_redact`                                                  | List[*int*]                                                         | :heavy_check_mark:                                                  | List of orders to redact                                            | {<br/>"value": [<br/>299938,<br/>280263<br/>]<br/>}                 |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.ShopifyCustomerRedactResponse](../../models/shopifycustomerredactresponse.md)**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| errors.ShopifyCustomerRedactBadRequestError | 400                                         | application/json                            |
| errors.MammothAnalyticsDefaultError         | 4XX, 5XX                                    | \*/\*                                       |

## data_request

Get requested data of shopify user

### Example Usage

<!-- UsageSnippet language="python" operationID="ShopifyDataRequest" method="post" path="/gdpr_hooks/shopify/customers/data_request" -->
```python
from mammoth_analytics import MammothAnalytics, models
import os


with MammothAnalytics(
    server_url="https://api.example.com",
    security=models.Security(
        api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
        api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
    ),
) as ma_client:

    res = ma_client.shopify_privacy_webhooks.data_request(shop_id=954888, shop_domain="testshop.myshopify.com", orders_requested=[
        280263,
        220458,
    ], customer={
        "id": 191167,
        "email": "john@example.com",
        "phone": "555-625-1199",
    }, data_request={
        "id": 9999,
    })

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                                   | Type                                                                        | Required                                                                    | Description                                                                 | Example                                                                     |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| `shop_id`                                                                   | *int*                                                                       | :heavy_check_mark:                                                          | Shop Id                                                                     | {<br/>"value": 113<br/>}                                                    |
| `shop_domain`                                                               | *str*                                                                       | :heavy_check_mark:                                                          | Shop Domain                                                                 | {<br/>"value": "shop3.myshopify.com"<br/>}                                  |
| `orders_requested`                                                          | List[*int*]                                                                 | :heavy_check_mark:                                                          | List of orders requested                                                    | {<br/>"value": [<br/>311<br/>]<br/>}                                        |
| `customer`                                                                  | [models.ShopifyCustomer](../../models/shopifycustomer.md)                   | :heavy_check_mark:                                                          | N/A                                                                         |                                                                             |
| `data_request`                                                              | [models.ShopifyDataRequestSchema](../../models/shopifydatarequestschema.md) | :heavy_check_mark:                                                          | N/A                                                                         |                                                                             |
| `retries`                                                                   | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)            | :heavy_minus_sign:                                                          | Configuration to override the default retry behavior of the client.         |                                                                             |

### Response

**[models.ShopifyDataRequestResponse](../../models/shopifydatarequestresponse.md)**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| errors.ShopifyDataRequestBadRequestError | 400                                      | application/json                         |
| errors.MammothAnalyticsDefaultError      | 4XX, 5XX                                 | \*/\*                                    |

## shop_redact

Delete requested shopify shop's data from the system

### Example Usage

<!-- UsageSnippet language="python" operationID="ShopifyShopRedact" method="post" path="/gdpr_hooks/shopify/shop/redact" -->
```python
from mammoth_analytics import MammothAnalytics, models
import os


with MammothAnalytics(
    server_url="https://api.example.com",
    security=models.Security(
        api_key=os.getenv("MAMMOTHANALYTICS_API_KEY", ""),
        api_secret=os.getenv("MAMMOTHANALYTICS_API_SECRET", ""),
    ),
) as ma_client:

    res = ma_client.shopify_privacy_webhooks.shop_redact(shop_id=959889, shop_domain="test.myshopify.com")

    # Handle response
    print(res)

```

### Parameters

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `shop_id`                                                           | *int*                                                               | :heavy_check_mark:                                                  | Shop Id                                                             | {<br/>"value": 113<br/>}                                            |
| `shop_domain`                                                       | *str*                                                               | :heavy_check_mark:                                                  | Shop Domain                                                         | {<br/>"value": "shop3.myshopify.com"<br/>}                          |
| `retries`                                                           | [Optional[utils.RetryConfig]](../../models/utils/retryconfig.md)    | :heavy_minus_sign:                                                  | Configuration to override the default retry behavior of the client. |                                                                     |

### Response

**[models.ShopifyShopRedactResponse](../../models/shopifyshopredactresponse.md)**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| errors.ShopifyShopRedactBadRequestError | 400                                     | application/json                        |
| errors.MammothAnalyticsDefaultError     | 4XX, 5XX                                | \*/\*                                   |