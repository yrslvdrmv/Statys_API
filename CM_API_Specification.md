# Catalog managment website API specification

## Table of contents

* [Changes control](#сhanges-control)
* [Shema](#shema)
* [Summary](#summary)
* [Authentication and Security](#Authentication-and-Security)
* [General considerations](#general-considerations)
* [Error handling](#error-handling)
* [API](#api)
	* [Get product (partial search)](#Get-product-partial-search)
	* [Get product (full search)](#Get-product-full-search)
	* [Get product (partial search status published)](#Get-product-partial-search-status-published)
	* [Get product (full search status published)](#Get-product-full-search-status-published)
	* [Get product info](#Get-product-info)
	* [Add new product](#Add-new-product)
	* [Update product](#Update-product)
	* [Update product status](#Update-product-status)
	* [Get variants](#Get-variants)
	* [Get variant info](#Get-variant-info)
	* [Get variant pricing](#Get-variant-pricing)
	* [Add new variant](#Add-new-variant)
	* [Update variant](#Update-variant)
	* [Update variant status](#Update-variant-status)

* [Appendix 1](#apendix_1)

Changes control
---------------

Data | Made by | Changes
------------ | ------------- | -------------
October 4, 2021 | `Yaroslav Dromov` | First edition

Shema
-----
All API access is over HTTPS, and accessed from https://fs6wjwxd00.execute-api.us-east-1.amazonaws.com. 
All data is sent and received as JSON.

Summary
------

The document describes how Catalog Managment module can integrate with the Statys Business services marketplace. The API provides integration capability for new or existing websites to add Statys Business services products to their catalog, check product statuse

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

Error handling
--------------

	Hypertext Transfer Protocol (HTTP) Status Code Registry

Value | Description | Reference
------------ | ------------- | -------------
`400` | Bad Request | https://www.rfc-editor.org/rfc/rfc7231.html
`400` | Bad Request | https://www.rfc-editor.org/rfc/rfc7231.html
`403` | Forbiden | https://www.rfc-editor.org/rfc/rfc7231.html
`500` | Forbiden | https://www.rfc-editor.org/rfc/rfc7231.html


API
===

Get product (partial search)
----------------
<details><summary><b>details:</b></summary>
<p>

<b>[POST]</b> 
Endpoint:
```
https://.../api/v1/products/search
```

Get list of existing products.

#### Auth

HTTP header request must have a custom parameter: 
```
[x-API-key=' <key given to client>']
```

#### Path param
The API for a partial search requires:
```
Full or partial parent product name
```

It is assumed that before order submission, the website has identified a buyer and checked the license if the requested product requires such license in the buyer's (shipping address) jurisdiction. 

Statys Marketplace will not accept new non-paid orders, i.e., payment must be made and money received. It is possible to submit an order with payment made but not completed yet. This may happen if the payment processor requires more time. If the payment doesn't go through, the order will be declined.

#### Request param

```
order_header section
```
R/O | Property name | Value | Description
------------ | ------------- | ------------- | -------------
R | `productParent.productName` | string | Full or partial name



<details><summary><b>Request JSON example:</b></summary>
<p>
	
```json
{
  "product_name": ""
}
```
	
</p>
</details>

#### Response
```
order_header section
```
R/O | Property name | Value | Description
------------ | ------------- | ------------- | -------------
R | `order_id` | integer | Order ID assigned by Statys Marketplace to submitted order. It will be used in subsequent communications as a reference.
R | `buyer_account_id` | integer | The ID of a Buyer from StatysMarketplace. The buyer account ID is created on Statys side and has to be used in further inquiries. In response to a brand new account order with buyer_account_id= "0", Statys returns the account number created for this buyer. In case it is found to be existing (found by name and address), Statys returns the existing account ID. Even if the buyer account is presented by web site as new, Statys will attempt to match account data (billing address details) with the existing account, and if the credible match is made, the existing buyer account id will be returned.
R | `order_status_cd` | string | Possible returned values: "Created", "Pending", pending issues resolution like license confirmation, etc., "Confirmed" , "Cancelled".

This version of API does not have order adjustment or cancellation endpoints. After submission, all changes must be done through a call to a CSR.


<details><summary><b>Response JSON example (request status 200):</b></summary>
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
	
</p>
</details>

[Table of contents](#table-of-contents)



