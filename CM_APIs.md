
## Product partial search WHM
1. Create an API method product partial/search to call by the CM UI to get product search results based on the product name entered by a user;
2. The method input parameters are:
* product_name, can be an empty string;
* max_results = number of results;
3. If the method’s input is an empty string, the method returns the list of up to max_results random products;
4. If the method’s input is 1 or 2 character string, the method returns the list of up to max_results random product names that **start** with the string from the method’s input;
5. If method input is 3 or more character string, the method returns the list of up to max_results random product names that **contain** the string from the method’s input;
6. Return only products having Product.productUnavailable flag equal to 0;
7. The method return is the array of the matched product records along with their attributes:
* product_name from Product.productName;
8. Order output alphabetically;


Endpoint (production):

[POST]:
```
https://.../api/v1/products/search
```

JSON Input
```JSON
{
  "product_name": "",
  "max_results": ""
}
```

JSON Output
```JSON
{
    "product_records":
        [
            {
             "product_id": ""
	     "product_name": ""
	    }
	]
}
```
