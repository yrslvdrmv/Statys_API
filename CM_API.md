

№ | API method | Role | User input | System output
------------ | ------------- | ------------- | ------------- | -------------
1 |	`Get product (partial search)` | BM, WHM |	Partial or full parent product name | ```productName```
2 |	`Get product (full search)` |	BM, WHM |	Partial or full parent product name + Enter | `productName`, sum(`productID`), `isPublished`
3 |	`Get product (partial search status published)` | BM, WHM |	Partial or full parent product name + `Show active only checkbox` = 1 |  `productName` where `isPublished`=1
4 |	`Get product (full search status published)` |	BM, WHM | Partial or full parent product name + `Show active only checkbox` = 1 + Enter | `productName`, sum(`productID`), `isPublished` where `isPublished`=1
5 | `Get variants` |	BM, WHM |	|
6 | `Get product info` |	BM |	|
7 | `Update product` |	BM |	|
8 | `Get variants info` |	BM, WHM |	|
9 | `Get variants pricing` |	BM, WHM |	|
10 | `Update variants` |	BM, WHM |	|
11 | `Update product status` | BM |	|
12 | `Update variant status` | BM |	|
13 |	`Add new product` |	BM |	|
14 |	`Add new variant` |	BM, WHM |	|



## Ticket 1. As a BM user, I want to search parant products (UI)
Follow the [UI](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A11333) board for the page design
### Acceptance criteria:
1. **User** on the [page](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A11333)
2. **User** type one or several letters into search bar [UI](https://user-images.githubusercontent.com/73137432/135811153-9693454b-27b5-422a-8b17-1ca08e0ebc87.png) 
3. **System** call `Get product (partial search)` API method. In case of `Show active only checkbox`([UI](https://user-images.githubusercontent.com/73137432/135830700-fb21f7cc-2b08-4f7f-936b-a6720db2b3bd.png)) is activated, **System** call `Get product (partial search status published)` API method
4. **User** type one or several letters into search bar and press `Enter` button on keyboard 
5. **System** call `Get product (full search)` [UI](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A10768). In case of `Show active only checkbox`([UI](https://user-images.githubusercontent.com/73137432/135830700-fb21f7cc-2b08-4f7f-936b-a6720db2b3bd.png)) is activated, **System** call `Get product (full search status published)` API method
6. **User** select product status toggle [UI](https://user-images.githubusercontent.com/73137432/135833166-f4de8c8e-3a8a-40d0-8b7b-2622693a7f24.png)
7. **System** call `Update product status`




## Ticker 2. As a WHM user, I want to search parant products (UI)
