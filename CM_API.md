

№ | API method | Role | User input | System output
------------ | ------------- | ------------- | ------------- | -------------
1 |	`Get product (partial search)` | BM, WHM |	Partial or full parent product name | `productName`
2 |	`Get product (full search)` |	BM, WHM |	Partial or full parent product name + Enter | `productName`, sum(`productID`), `isPublished`
3 |	`Get product (partial search status published)` | BM, WHM |	Partial or full parent product name + `Show active only checkbox` = 1 |  `productName` where `isPublished`=1
4 |	`Get product (full search status published)` |	BM, WHM | Partial or full parent product name + `Show active only checkbox` = 1 + Enter | `productName`, sum(`productID`), `isPublished` where `isPublished`=1
5 | `Get variants` |	BM, WHM |	- |
6 | `Get product info` |	BM | - | ...
7 | `Update product` |	BM |	|
8 | `Get variants info` |	BM, WHM |	|
9 | `Get variants pricing` |	BM, WHM |	|
10 | `Update variants` |	BM, WHM |	|
11 | `Update product status` | BM |	`isPublished` | -
12 | `Update variant status` | BM |	|
13 |	`Add new product` |	BM |	|
14 |	`Add new variant` |	BM, WHM |	|



## Ticket 1. As a BM user, I want to search parant products (UI)
Follow the [UI](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A11333) board for the page design
### Acceptance criteria:
1. **User** on the [Home search page](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A11333)
2. **User** type one or several letters into [search bar](https://user-images.githubusercontent.com/73137432/135811153-9693454b-27b5-422a-8b17-1ca08e0ebc87.png) 
3. **System** call `Get product (partial search)` API method. In case of [Show active only checkbox](https://user-images.githubusercontent.com/73137432/135830700-fb21f7cc-2b08-4f7f-936b-a6720db2b3bd.png) is activated, **System** call `Get product (partial search status published)` API method
4. **User** type one or several letters into search bar and press `Enter` button on keyboard 
5. **System** call `Get product (full search)` [UI](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A10768). In case of [Show active only checkbox](https://user-images.githubusercontent.com/73137432/135830700-fb21f7cc-2b08-4f7f-936b-a6720db2b3bd.png) is activated, **System** call `Get product (full search status published)` API method
6. **User** switch [product status toggle](https://user-images.githubusercontent.com/73137432/135833166-f4de8c8e-3a8a-40d0-8b7b-2622693a7f24.png)
7. **System** call `Update product status` API method
8. **User** press [Edit button](https://user-images.githubusercontent.com/73137432/135833794-12e656ec-3513-4a1e-ba42-a618089ce5ca.png)
9. **System** call `Get product info` API method and move to [Edit product page](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=743%3A21512)
10. **User** press [Creat variant button](https://user-images.githubusercontent.com/73137432/135834938-f94ca0fd-b4be-46a2-97f0-ad00fa73e00c.png)
11. **System** call `Add new variant` API method and move to [Add product varian page](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A12074)
12. **User** press [List of variants button](https://user-images.githubusercontent.com/73137432/135835514-d2cff86e-eb2c-405c-9f36-b156eb3fd515.png)
13. **System** call `Add new variant` API method [UI](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A10862)




Add product






## Ticker 2. As a WHM user, I want to search parant products (UI)
