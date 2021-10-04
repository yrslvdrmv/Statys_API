
## Product partial search
1. Create an API method product/search to call by the IRS UI to get product search results based on the product name entered by a user;
2. The method input parameters are:
2.1 product_name; Can be an empty string;
2.2 an array of product IDs to exclude from search;
3. If the method’s input is an empty string, the method returns the list of up to max_results random products excluding ones passed in the arrays of products passed as an input


Endpoint (production):

[POST]:
```
https://.../api/v1/products/search
```

JSON Input
```JSON
{
  "product_name": ""
}
```

JSON Output

