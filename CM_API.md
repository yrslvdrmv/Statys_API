```
UI
```


№ | API method | Role | User input | System output
------------ | ------------- | ------------- | ------------- | -------------
1 |	`Get product (partial search)` | BM, WHM |	Partial or full parent product name | `productName`
2 |	`Get product (full search)` |	BM, WHM |	Partial or full parent product name + Enter | `productName`, sum(`productID`), `isPublished`
3 |	`Get product (partial search filter status)` | BM, WHM |	Partial or full parent product name + `Show active only checkbox` activated |  `productName`, `isPublished`=1
4 |	`Get product (full search filter status)` |	BM, WHM |	Partial or full parent product name + Enter | Parent product name, number of variants, status in search result frame.
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
3. **System** call `Get product (partial search)` API method
4. In case of **User** activate `Show active only checkbox`, **System** call `Get product (partial search filter status)`
5. **User** press `Enter` button
6. **System** call `Get product (full search)` [UI](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A10768)
7. In case of **User** activate `Show active only checkbox`, **System** call `Get product (full search filter status)`
8. **User** select status toggle
9. **System** call `Update product status`




## Ticker 2. As a WHM user, I want to search parant products (UI)
