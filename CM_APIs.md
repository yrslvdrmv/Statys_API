1. Create an API method product/search to call by the CM UI to get product search results based on the product name entered by a user;
2. The method input parameter is the product_name;
3. For this userID verify the role of the user in the table field User.role. If BM, return all related products. If WHM return products related to Warehouses this WHM user belongs to. Get the UserID from the Cognito token in the header request. 
4. The method returns to the UI the list of the products matching the partial search condition to the method’s input.


Endpoint (production):

POST:
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

