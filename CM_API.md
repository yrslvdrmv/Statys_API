```
UI
```


№ | API method | Role | User input | System output
------------ | ------------- | ------------- | ------------- | -------------
1 |	`Get product (partial search)` | BM, WHM |	Partial or full parent product name | List of related `Parent product names`
2 |	`Get product (full search)` |	BM, WHM |	Partial or full parent product name + Enter | Parent product name, number of variants, status in search result frame.
3 |	`Get product (partial search filter status)` | BM, WHM |	Partial or full parent product name | List of related `Parent product names`
4 |	`Get product (full search filter status)` |	BM, WHM |	Partial or full parent product name + Enter | Parent product name, number of variants, status in search result frame.
5 |	`Get variants` |	BM, WHM | |	User press on product name. System returns: Product variant name, SKU, Version, MSRP, Status in extended bar
6 |	`Get product details` |	BM, WHM | |	User press on edit button in header. System returns: ...
7 |	`Get variant details` |	BM, WHM | |	User press on edit button in variant row. System returns: Product name, catalog category, Brand name, Manufacturer, HS code, Cooling, Temperature details.
8 |	`Add product` |	BM |	|
9 |	`Add variants` |	BM, WHM |	|
10 | `Update product` |	BM |	|
11 | `Update variant` |	BM, WHM |	|
12 | `Update product status` |	BM |	|
13 | `Update variant status` |	BM |	|


## Ticket 1. As a BM user, I want to search parant products (UI)
Follow the [UI](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A11333) board for the page design
### Acceptance criteria:
1. **User** on the [page](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A11333)
2. **User** type one or several letters into search bar [UI](https://user-images.githubusercontent.com/73137432/135811153-9693454b-27b5-422a-8b17-1ca08e0ebc87.png). 
3. **System** call `Get product (partial search)` API method
4. In case of **User** activated: Show active only checkbox, **System** calls `Get product (partial search filter status)`
5. In case of **User** press `enter` button, **System** calls `full search API method` [UI](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A10768)
6. 




## Ticker 2. As a WHM user, I want to search parant products (UI)
