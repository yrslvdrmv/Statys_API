```json
{  
    "$schema": "http://json-schema.org/draft-04/schema#",
    "title": "put variant model",
    "type": "object",
    "properties": {
        "order_header": {
            "type": "object",
            "properties": {
                "variant_name": {"type": "string"},
                "sku": {"type": "string"},
                "strength": {"type": "string"},
                "manufacturer_product_url": {"type": "string"},
                "country_of_origin": {"type": "string"},
                "description": {"type": "string"},
                "uom_dimension": {"type": "boolean"},
                "uom_weight": {"type": "boolean"},
                "units_in_the_box": {"type": "integer"},
                "lenght": {"type": "number"},
                "width": {"type": "number"},
                "height": {"type": "number"},
                "package_weight": {"type": "number"},
                "region": {
                    "type": "array",
                    "items": {
                        "type": "object",
                        "properties": {
                            "region_id": {"type": "integer"},
                            "currency": {"type": "decimal"},
                            "msrp_prict": {},
                            "minimum_sale_price": {},
                            "tier": {
                                "type": "array",
                                "maxItems": 5,
                                "items": {
                                    "type": "object",
                                    "properties": {
                                        "tier_number": {"type": "integer"},
                                        "tier_from": {"type": "integer"},
                                        "tier_to": {"type": "integer"},
                                        "tier_price": {"type": "number"}
                                    },  
                                    "additionalProperties": false,
                                    "required": ["tier_number", "tier_from", "tier_to", "tier_price"]
                                }
                            }
                        },
                        "required": ["region_id", "currency", "msrp_price", "minimus_sale_price"],
                        "additionalProperties": false
                    }
                }
            },
        "required": ["variant_name"]
        }
    }
}
```
