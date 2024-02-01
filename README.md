
# - product-service

GET http://localhost:8080/api/product

POST http://localhost:8080/api/product

    {
        "name":"iphone 15",
        "description":"iphone 15",
        "price":1200
    }




# - order-service (depends_on: inventory-service)

POST http://localhost:8081/api/order

    {
        "orderLineItemsDtoList": [
            {
                "skuCode":"iphone_15",
                "price": 1200,
                "quantity": 1
            }
        ]
    }

    or

    {
        "orderLineItemsDtoList": [
            {
                "skuCode":"iphone_15",
                "price": 1200,
                "quantity": 1
            },
                {
                "skuCode":"iphone_15_black",
                "price": 1200,
                "quantity": 1
            }
        ]
    }



# - inventory-service

GET http://localhost:8082/api/inventory

	http://localhost:8082/api/inventory?skucode=iphone_15
	http://localhost:8082/api/inventory?skucode=iphone_15&skucode=iphone_15_black