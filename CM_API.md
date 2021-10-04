```
UI
```


№ | API | User | Description
------------ | ------------- | ------------- | -------------
1 |	`Get product (partial search)` | BM, WHM |	User type one or several letters into search bar. System returns: `Parant product names` in drop down list.
2 |	`Get product (full search)` |	BM, WHM |	User type several letters into search bar and press Enter or select product from search drop down list. System returns: Parent product name, number of variants, status in search result frame.
3 |	`Get variants` |	BM, WHM |	User press on product name. System returns: Product variant name, SKU, Version, MSRP, Status in extended bar
4 |	`Get product details` |	BM, WHM |	User press on edit button in header. System returns: ...
5 |	`Get variant details` |	BM, WHM |	User press on edit button in variant row. System returns: Product name, catalog category, Brand name, Manufacturer, HS code, Cooling, Temperature details.
6 |	`Add product` |	BM |	
7 |	`Add variants` |	BM, WHM |	
8 |	`Update product` |	BM |	
9 |	`Update variant` |	BM |	
10 |	`Update product status` |	BM |	
11 |	`Update variant status` |	BM |	


## 1,2. As a BM user, I want to search parant products (UI)
Follow the [Figma](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A11333) board for the page design
### Acceptance criteria:
1. **User** on the [page](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A11333)
2. **User** type one or several letters into search bar [example](https://user-images.githubusercontent.com/73137432/135811153-9693454b-27b5-422a-8b17-1ca08e0ebc87.png) 
4. **System** call `partial search API method` and returns list of `parent product names` in drop down list
5. **System** call `full search API method` and returns list of `parent product names` with `number of variants`, `status` in search result frame, in case of user press `enter` button [example](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A10768)
6. **System** filter 
