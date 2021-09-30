# first_repo

- [Article1](#1-art)

# Article1

First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column

## B

##### C



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

## 1. Overview



<details><summary>INPUT JSON Sample:</summary>
<p>

#### yes, even hidden code blocks!
'''
  {
"order_header": {
        		"website_order_id": "web_001",
       		 "order_date": "2021-03-12",
       		 "shipping_total": 35.56,
        		"shipping_tax": null,
        		"cart_tax": null,
        		"total": 540.12,
        		"total_tax": null,
        		"prices_include_tax": true,
        		"currency": "USD",
        		"customer_note": null,
		"is_paid": false,
    		},
    "discounts": {
        		"discount_total": 200.0,
        		"discount_tax": null
    		},
    "buyer": {
        "buyer_account_id": 100110,
        "buyer_ip_address": "192.168.1.1",
        "buyer_license" : {
    		"license_name": "567-09977"
    		"license_expiry_date": "",
		"title": "Dr.",
    		"first_name": "Joe",
    		"middle_name": "",
    		"last_name": "Doe",
		"state": "Nevada",
 		"country": "US",
		"profession": "General practitioner",
		"specialty": "Family doctor"
	           },
    "buyer_address": {
    		"title": null,
        		"first_name": "John",
        		"middle_name": null,
        		"last_name": "Smith",
        		"company": "John Smith",
        		"address_1": "1 some street",
        		"address_2": null,
        		"city": "New York",
        		"state": "New York",
        		"postcode": "10033",
        		"country": "US",
        		"phone_number_1": "555-555-55-55",
        		"phone_number_2": null,
        		"email": "something@gmail.com"
		}
    },
    "shipping": {
        		"title": null,
        		"first_name": "John",
        		"middle_name": null,
        		"last_name": "Smith",
        		"company": "John Smith",
        		"address_1": "1 some street",
        		"address_2": null,
        		"city": "New York",
        		"state": "New York",
        		"postcode": "10033",
        		"country": "US",
        		"phone_number_1": "555-555-55-55",
        		"phone_number_2": null,
        		"email": "something@gmail.com"
   		},
    "payment_details": {
        		"payment_transaction_id": "payment001",
       		"payment_token": "card001",
        		"payment_method_type": "CC",
        		"payment_method_description": "4156 78XX XXXX 0019",
		"payment_mid": 10928
    		},
    "line_items": [
            		{
                	"product_id": 123,
                	"quantity": 10,
                	"price": 12.20,
                	"total": 122.00,
                	"total_tax": null
            		}
        	]
}
'''
```python
print("hello world!")
```

</p>
</details>
