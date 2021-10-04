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


## As a BM user, I want to search parant products (UI)
### Acceptance criteria:
1. User on the (link on UI example) page
2. User type one or several letters into search bar (link on UI example)
3. System returns list of `parent product names` in drop down list, according to users input, once user typed at least one letter. (link on UI example)
4. System hide drop down list and return list of `parent product names`, `number of variants`, `status`, in search result frame in case of user press enter button.
