## Brief API description

```
Products:
```
№ | API method | Role | User input | System output
------------ | ------------- | ------------- | ------------- | -------------
1 |	`Get product (partial search)` | BM, WHM |	Partial or full parent product name | `Product name`
2 |	`Get product (full search)` |	BM, WHM |	Partial or full parent product name + Enter | `Product name`, sum(`Product ID`), `Product status`
3 |	`Get product (partial search status published)` | BM, WHM |	Partial or full parent product name + `Show active only checkbox` = 1 |  `Product name` where published status = 1
4 |	`Get product (full search status published)` |	BM, WHM | Partial or full parent product name + `Show active only checkbox` = 1 + Enter | `Product name`, sum(`Product ID`), `Published status` where `Published status` = 1
5 | `Get product info` |	BM, WHM | `Product name` | `Product name`, `Catalog category`, `Long description`, `Brand name`, `Manufacturer`, `Version`, `HS Code`, `Cooling status`, `Temperature details`
6 |	`Add new product` |	BM | `Product name`, `Catalog category`, `Long description`, `Brand name`, `Manufacturer`, `Version`, `HS Code`, `Cooling status`, `Temperature details` | -
7 | `Update product` |	BM | `Product name`, `Catalog category`, `Long description`, `Brand name`, `Manufacturer`, `Version`, `HS Code`, `Cooling status`, `Temperature details`	| -
8 | `Update product status` | BM |	`Product published status` | -


```
Variants:
```
№ | API method | Role | User input | System output
------------ | ------------- | ------------- | ------------- | -------------
1 | `Get variants` |	BM, WHM |	`Product name` | `Variant name`, `SKU`, `Version`, `MSRP`, `Status`
2 | `Get variant info` |	BM, WHM |	`Variant name` | `Short description`, `SKU`, `Strength`, `Manufacturer product URL`, `Country of origin`, `Long description`, `inch`, `ounce`, `Units in the box`, `Lenght`, `Width`, `Hight`, `Package weight`
3 | `Get variant pricing` |	BM, WHM | `Variant name`	| `Region`, `Licence`, `Currency`, `MSRP Price`, `Minimum sales price`, `Tier 1 quantity`, `Tier 2 quantity`, `Tier 3 quantity`, `Tier 4 quantity`, `Tier 5 quantity`, `Tier 1 price`, `Tier 2 price`, `Tier 3 price`, `Tier 4 price`, `Tier 5 price`
4 |	`Add new variant` |	BM, WHM |	`Short description`, `SKU`, `Strength`, `Manufacturer product URL`, `Country of origin`, `Long description`, `inch`, `ounce`, `Units in the box`, `Lenght`, `Width`, `Hight`, `Package weight` | -
5 | `Update variant` |	BM, WHM |	`Short description`, `SKU`, `Strength`, `Manufacturer product URL`, `Country of origin`, `Long description`, `inch`, `ounce`, `Units in the box`, `Lenght`, `Width`, `Hight`, `Package weight` | -
6 | `Update variant status` | BM |	`Variant published status`| -

## Ticket 1. As a BM user, I want to search parant products (UI)
Follow the [UI](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A11333) board for the page design
Follow the [API specification](https://github.com/yrslvdrmv/Statys_API/blob/d25a1b63dc01693621d1d30f28f1771a775c8497/CM_API_Specification.md)

### Acceptance criteria:
1. **User** on the [Home search page](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A11333)
2. **User** type one or several letters into [search bar](https://user-images.githubusercontent.com/73137432/135811153-9693454b-27b5-422a-8b17-1ca08e0ebc87.png) 
3. **System** call `Get product (partial search)` API method. In case of [Show active only checkbox](https://user-images.githubusercontent.com/73137432/135830700-fb21f7cc-2b08-4f7f-936b-a6720db2b3bd.png) is activated, **System** call `Get product (partial search status published)` API method
4. **User** type one or several letters into search bar and press `Enter` button on keyboard 
5. **System** call `Get product (full search)` [UI](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A10768). In case of [Show active only checkbox](https://user-images.githubusercontent.com/73137432/135830700-fb21f7cc-2b08-4f7f-936b-a6720db2b3bd.png) is activated, **System** call `Get product (full search status published)` API method
6. **User** switch [Product status toggle](https://user-images.githubusercontent.com/73137432/135833166-f4de8c8e-3a8a-40d0-8b7b-2622693a7f24.png)
7. **System** call `Update product status` API method
8. **User** press [Edit product button](https://user-images.githubusercontent.com/73137432/135833794-12e656ec-3513-4a1e-ba42-a618089ce5ca.png)
9. **System** call `Get product info` API method and move to [Edit product page](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=743%3A21512)
10. **User** press [Add variant button](https://user-images.githubusercontent.com/73137432/135834938-f94ca0fd-b4be-46a2-97f0-ad00fa73e00c.png) **'IN BUTTON NAME CREATE' SHOULD BE CHANGED ON 'ADD'**
11. **System** call `Add new variant` API method and move to [Add product varian page](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A12074)
12. **User** press [Get variants button](https://user-images.githubusercontent.com/73137432/135835514-d2cff86e-eb2c-405c-9f36-b156eb3fd515.png)
13. **System** call `Get variants` API method [UI](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A10862)
14. **User** press [Add product button](https://user-images.githubusercontent.com/73137432/135837018-72427440-d43f-4685-9051-d93774551e2d.png)
15. **System** call `Add new product` API method and move to [Add new product page](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A11865)
16. **User** switch [Variant status toggle](https://user-images.githubusercontent.com/73137432/135833166-f4de8c8e-3a8a-40d0-8b7b-2622693a7f24.png)
17. **System** call `Update variant status` API method
18. **User** press [Edit variant button](https://user-images.githubusercontent.com/73137432/135839534-cbac8be1-52d8-4cfa-8041-18787a3ec31f.png)
19. **System** call `Get variant info` API method and move to [Edit variant page](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=699%3A21720)





## Ticker 2. As a WHM user, I want to search parant products (UI)
Follow the [UI](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A11333) board for the page design
Follow the [API specification](https://github.com/yrslvdrmv/Statys_API/blob/d25a1b63dc01693621d1d30f28f1771a775c8497/CM_API_Specification.md)

### Acceptance criteria:
1. **User** on the [Home search page](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A11333)
2. **User** type one or several letters into [search bar](https://user-images.githubusercontent.com/73137432/135811153-9693454b-27b5-422a-8b17-1ca08e0ebc87.png) 
3. **System** call `Get product (partial search)` API method. In case of [Show active only checkbox](https://user-images.githubusercontent.com/73137432/135830700-fb21f7cc-2b08-4f7f-936b-a6720db2b3bd.png) is activated, **System** call `Get product (partial search status published)` API method
4. **User** type one or several letters into search bar and press `Enter` button on keyboard 
5. **System** call `Get product (full search)` [UI](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A10768). In case of [Show active only checkbox](https://user-images.githubusercontent.com/73137432/135830700-fb21f7cc-2b08-4f7f-936b-a6720db2b3bd.png) is activated, **System** call `Get product (full search status published)` API method
6. **User** press [Add variant button](https://user-images.githubusercontent.com/73137432/135834938-f94ca0fd-b4be-46a2-97f0-ad00fa73e00c.png) **'IN BUTTON NAME CREATE' SHOULD BE CHANGED ON 'ADD'**
7. **System** call `Add new variant` API method and move to [Add product varian page](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A12074)
8. **User** press [Get variants button](https://user-images.githubusercontent.com/73137432/135835514-d2cff86e-eb2c-405c-9f36-b156eb3fd515.png)
9. **System** call `Get variants` API method [UI](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=389%3A10862)
10. **User** press [Edit variant button](https://user-images.githubusercontent.com/73137432/135839534-cbac8be1-52d8-4cfa-8041-18787a3ec31f.png)
11. **System** call `Get variant info` API method and move to [Edit variant page](https://www.figma.com/file/8esK6SC43J6ioZCIuj2hJr/Catalog-Management?node-id=699%3A21720)
