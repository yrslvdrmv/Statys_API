# Statys Marketplace website API specification

- [Overview](#1-overview)
- [Methods](#2-methods)
  - [Create new order](#21-create-new-order)
  - [Self-issued access tokens](#22-self-issued-access-tokens)


## Overview

Data | Made by | Changes
------------ | ------------- | -------------
October 1, 2021 | `Yaroslav Dromov` | Blablablablablablablablablablablablabla

## Methods

Below are the API methods for order processing by the Marketplace:

- Create new order
- Retrieve order status

### Create new order

To get access to current weather, minute forecast for 1 hour, hourly forecast for 48 hours, daily forecast for 7 days and government weather alerts, please use this section of the documentation.

If you are interested in historical weather data, please read the "Historical weather data" section

#### API call
```http
https://.../api/v1/websites/products
```
web site authentication: HTTP header request must have a custom parameter: 
[x-API-key=' <key given to client>']

#### Parameters

Parameter | Status | Description
------------ | ------------- | -------------
`buyer` | required | The buyer information
`billing_address` | required | billing address 
`shipping_address` | required | shipping address
`basket` | required | shopping basket
`payment_info` | required | payment information

```
It is assumed that before order submission, the website has identified a buyer and checked the license if the requested product requires such license in the buyer's (shipping address) jurisdiction. 

Statys Marketplace will not accept new non-paid orders, i.e., payment must be made and money received. It is possible to submit an order with payment made but not completed yet. This may happen if the payment processor requires more time. If the payment doesn't go through, the order will be declined.
```



<details><summary><b>INPUT JSON Sample:</b></summary>
<p>
	
```json
{
"products":
  [
    {
      "product_data": 
          {
          "product_id": {"type": "integer"},
          "product_name": {"type": "string", "maxlength": 128},
          "product_short_description": {"type": "string", "maxlength": 512},
          "product_long_description": {"type": "string", "maxlength": 1024},
          "product_sku": {"type": "string", "maxlength": 128},
          "product_weight": {"type": "number"},
          "product_weight_uom": {"type": "string", "maxlength": 32},
          "product_length": {"type": "number"},
          "product_width": {"type": "number"},
          "product_height": {"type": "number"},
          "product_lwh_uom": {"type": "string","maxlength": 32},
          "dosage_value": {"type": "string", "maxlength": 256},
          "dosage_type": {"type": "string", "maxlength": 32},
          "items_in_pack": {"type": "string", "maxlength": 128},
          "pack_type": {"type": "string", "maxlength": 32},
          "brand_name": {"type": "string", "maxlength": 32}
          }
      "product_category": 
 		  {
			"is_cold": {"type": "boolean"},
			"type": {"type": "string", "maxlength": 32} /"pharma"|"med_device"/
		  },
   "msrp_price_and_availability": 

 		  {
			"availability": {"type": "string", "maxlength": 32} /"Backorder"|"Low"|"Medium"|"High"/
			"msrp_price": {"type": "number"},
			"currency": {"type": "string", "maxlength": 3}, /"USD"/
			"is_license_required": {"type": "boolean"}  
		  }
	   }
	]
}
```
	
</p>
</details>

<details><summary><b>OUTPUT JSON Sample:</b></summary>
<p>
	
```json

{
    "products": [
        {
            "product_data": {
                "product_id": 110,
                "product_name": "Some Product",
                "product_short_description": "Short Product Description",
                "product_long_description": "Long Product Description",
                "product_sku": "SAMPLE-SKU",
                "product_weight": 4.5,
                "product_weight_uom": "kg",
                "product_length": 20,
                "product_width": 30,
                "product_height": 15,
                "product_lwh_uom": "cm",
                "dosage_value": "0.5",
                "dosage_type": "ml",
                "items_in_pack": "1",
                "pack_type": "pre-filled syringe(s)",
                "brand_name": "Sample Brand"
            },
            "product_category": {
                "is_cold": true,
                "type": "pharma"
            },
            "msrp_price_and_availability": {
                "availability": "Medium",
                "msrp_price": 140.50,
                "currency": "USD",
                "is_license_required": true
            }
        }
    ]
}
```
</p>
</details>

Property name | Value | Description
------------ | ------------- | -------------
`website_order_id` | integer | Order ID how it was created/registered on the website.
`order_date` | timestamp | Date and time, the order was created on the website.	


