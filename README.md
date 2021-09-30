# Statys Marketplace website API specification

- [Overview](#1-overview)
- [Authentication](#2-authentication)
  - [Browser-based authentication](#21-browser-based-authentication)
  - [Self-issued access tokens](#22-self-issued-access-tokens)
- [Resources](#3-resources)
  - [Users](#31-users)
  - [Publications](#32-publications)
  - [Posts](#33-posts)
  - [Images](#34-images)
- [Testing](#4-testing)

## Overview

Data | Made by | Changes
------------ | ------------- | -------------
October 1, 2021 | Yaroslav Dromov | Blablablablablablablablablablablablabla


ENDPOINT: 
GET: https://.../api/v1/websites/products

web site authentication: HTTP header request must have a custom parameter: 
x-API-key=' <key given to client>'

### INPUT JSON Sample:
<details><summary>Hide</summary>
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

OUTPUT JSON Sample:
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
