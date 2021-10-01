# Statys Marketplace website API specification

## Table of contents

* [Changes control](#сhanges-control)
* [Summary](#summary)
* [Authentication and Security](#Authentication-and-Security)
* [General considerations](#general-considerations)
* [Error handling](#error-hendling)
* [Orders](#orders)

Changes control
---------------

Data | Made by | Changes
------------ | ------------- | -------------
October 1, 2021 | `Yaroslav Dromov` | First version

Summary
------

The document describes how a website can integrate with the Statys Business services marketplace. The API provides integration capability for new or existing websites to add Statys Business services products to their catalog and submit orders to and check order status from the Statys Order Management System (OMS).

The current revision described below provides:  
- The endpoint to obtain the product list along with availability and the current MSRP price for a given website;
- The endpoint for the website order submission;
- Retrieve parcel tracking for buyer's ALL previously submitted orders.
- API to confirm product availability

Authentication and Security
--------

* The website making an API call identifies itself to the Marketplace by a token submitted in the API request HTTP header. The token will be provided by OMS Business Admin to the participating site owner (webmaster) for each website individually during the onboarding process. The token is valid indefinitely unless a website owner has requested a replacement or advised to be replaced by the Marketplace.
* The website authentication: HTTP header request must have a custom parameter:
```http
x-API-key=' <token provided to website>'
```
* Security requirements must be observed in every API call.

General considerations
----------------------

* All products returned in the product list are available for sale.
* Submitted orders must include references to product list items by the product ID and provide the buyer details, including licenses where needed and payment information.
* The order status API provides information on parcels shipped for all the buyer's orders identified by Statys buyer account ID. Until the Marketplace's internal system ships a parcel, the API returns the empty parcel section.
* The current version of API uses English only.
* If the optional information is not available, the sender should skip the particular element in the request. The validation does not support the NULL value in the fields. 

Error hendling
--------------

	Hypertext Transfer Protocol (HTTP) Status Code Registry

Value | Description | Reference
------------ | ------------- | -------------
`400` | Bad Request | https://www.rfc-editor.org/rfc/rfc7231.html
`400` | Bad Request | https://www.rfc-editor.org/rfc/rfc7231.html
`403` | Forbiden | https://www.rfc-editor.org/rfc/rfc7231.html
`500` | Forbiden | https://www.rfc-editor.org/rfc/rfc7231.html


Orders
---

### Create new order
<b>[POST]</b> 
```
https://fs6wjwxd00.execute-api.us-east-1.amazonaws.com/test/api/v1/orders?buyer={buyer information}&billing_address={billing address}&shipping_address={shipping_address}&basket={basket}&payment_info={payment}
```

Publishes an order in system. 

#### Auth

HTTP header request must have a custom parameter: 
```
[x-API-key=' <key given to client>']
```

#### Path param
```
The buyer information, 
Billing address 
Shipping address, 
Shopping basket and 
Payment information. 
```

It is assumed that before order submission, the website has identified a buyer and checked the license if the requested product requires such license in the buyer's (shipping address) jurisdiction. 

Statys Marketplace will not accept new non-paid orders, i.e., payment must be made and money received. It is possible to submit an order with payment made but not completed yet. This may happen if the payment processor requires more time. If the payment doesn't go through, the order will be declined.

#### Request param

```
order_header section
```
R/O | Property name | Value | Description
------------ | ------------- | ------------- | -------------
R |	`website_order_id` | integer |	Order ID how it was created/registered on the website. 
R |	`order_date` |	timestamp |	Date and time, the order was created on the website.
O |	`shipping_total` | number | The total amount a website charged for shipping all items in the order.
O |	`shipping_tax` |	number | Tax amount a website charged on shipping cost.
O |	`cart_tax` |	number | Tax for the whole order
R |	`total` |	number | The total cost of order items and shipping
O |	`total_tax` | number |	Total tax charged for order items and shipping.
O |	`prices_include_tax` |	boolean |	The grand total of the order, including taxes
R |	`currency` |	string |	Currency code for currency an order was processed in.
O |	`customer_note` |	string |	Any note for the order a website wants to be attached. It may have an explanation of the discount provided, special delivery instructions, etc.
R |	`Is_paid` |	boolean |	Default to false reflecting the order payment to be captured by OMS. If the order was prepaid on the website, the value should be true. In this case the payment information object is optional;


	discounts section
R	discount_total	number	The total amount is given as a discount for the whole order.
O	discount_tax	number	Taxes are matching the discount amount.
	buyer section
R	buyer_account_id	integer	Buyer account ID. If the buyer is brand new, set this value to 0. Buyer account ID is created on Statys side and has to be used in further inquiries. In response to the new account "0", Statys returns the account number created for this buyer. In case a "new" account is found to be existing (found by name and address), Statys returns the existing account ID.
R	buyer_ip_address	string	An IP address a buyer contacted web site from.
	The medical license section: optional. 
R	license_name	string	License Name. It may be a license number.
R	license_expiry_date	date	YYYY-MM-DD format, a date doctor's license expires
O	title	string	The medical license owner title 
R	first_name	string	The medical license owner first name
O	middle_name	string	The medical license owner middle name
R	last_name	string	The medical license owner last name
R	state	string	If applicable – state or another administrative region within a country like "province", "canton". *Required for the USA and Canada
R	country	string	ISO 2-char Country code of shipping destination. See https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2

O	profession	string	The license owner occupation i.e. “Medical doctor”.
O	specialty	string	The license owner specialty i.e. “Family doctor”.
	The buyer address section has the same fields and requirements as the shipping address section below. It is required.
	The shipping address section is required.
O	title	text	Title abbreviation a buyer would like to be addressed: "Dr"," Mrs"," Sir".
R	first_name	text	First name of a person indicated as shipment receiver.
O	middle_name	text	The middle name of a person indicated as shipment receiver. It can be NULL.
R	last_name	text	Last name of a person indicated as shipment receiver.
O	company	text	Company name of a person indicated as shipment receiver.
R	address_1	text	The first line of the address. It is typically building number, Street name, and suite number like "123 Some St., suite 1400".
O	address_2	text	The second line of address if the first line is not enough. It can be NULL.
R	city	text	City a shipment to be sent to.
R	state	text	If applicable – state or another administrative region within a country like "province", "canton". *Required for the USA and Canada
R	postcode	text	Postal code of shipping destination.
R	country	char(2)	ISO 2-char Country code of shipping destination. See https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2 

R	phone_number_1	Text	First phone number of shipping destination contact in free form prefixed by country code: 
+1 416-123-4567. It can be NULL.
O	phone_number_2	text	Second phone number of shipping destination contact in free form prefixed by country code: 
+1 416-123-4567. It can be NULL.
R	email	text	E-mail address of a buyer. It can be NULL.
	payment_details section is required if the is_paid flag set to FALSE.
R	payment_transaction_id	string	Payment transaction ID returned by the payment processor.
O	payment_method_description	string	Payment transaction details returned by the payment provider.
R	payment_method_type	string	In the current API version, it is "CC" - credit card only.
O	payment_token	string	Payment token returned by Payment provider masking buyer's credit card information. It may be NULL.
Payment token allows to "pay with the Credit card used last time".
R	Payment_mid	integer	This is the Merchant MID used by the website while processing the order payment;
	line_items section. At least one order line must be provided.
R	product_id	integer	Product ID as per Statys Marketplace Product List.
R	quantity	integer	The number of units of the product.
R	price	money	Price a unit was actually sold by the website. (Do not mix with MSRP product price!)
R	total	money	The total price paid for the item. The total price may include a discount and not be equal quantity * price.
O	total_tax	money	Total tax charged for the item.


<details><summary><b>Example request:</b></summary>
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

<details><summary><b>Example response 200:</b></summary>
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





