##Ecommerce With Golang Project By Akhil Sharma
```bash
docker-compose up -d
go run .\cmd\ecommerce\main.go
```
- **SIGNUP FUNCTION API CALL (POST REQUEST)**

http://localhost:8000/users/signup

```json
{
  "first_name": "Artem",
  "last_name": "Popov",
  "email": "artempopovv@gmail.com",
  "password": "12345678",
  "phone": "87056570364"
}
```
Response: "successfully signed in!"
- **LOGIN FUNCTION API CALL (POST REQUEST)**

  http://localhost:8000/users/login

```json
{
  "email": "artempopovv@gmail.com",
  "password": "12345678"
}
```

Response:

```json
{
    "_id": "65d5f24ee7dd3620df0254b8",
    "first_name": "Artem",
    "last_name": "Popov",
    "password": "$2a$14$OxPsSCYBpuFyJE357jx.2eq3dCiGODbBP4i33HBSbBWDzDbuzEOIG",
    "email": "artempopovv@gmail.com",
    "phone": "87056570364",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJFbWFpbCI6ImFydGVtcG9wb3Z2QGdtYWlsLmNvbSIsIkZpcnN0X05hbWUiOiJBcnRlbSIsIkxhc3RfTmFtZSI6IlBvcG92IiwiVWlkIjoiNjVkNWYyNGVlN2RkMzYyMGRmMDI1NGI4IiwiZXhwIjoxNzA4NjA2NDE0fQ.mIAPS5bjpDSMSC8bEywFPVcYYER51mpabxdUD7yZt20",
    "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJFbWFpbCI6IiIsIkZpcnN0X05hbWUiOiIiLCJMYXN0X05hbWUiOiIiLCJVaWQiOiIiLCJleHAiOjE3MDkxMjQ4MTR9.S7mR17JcZfDQ-VIT53tOnJqMZ7VdJ7UJeFeffW8IPY8",
    "created_at": "2024-02-21T12:53:34Z",
    "updated_at": "2024-02-21T12:53:34Z",
    "user_id": "65d5f24ee7dd3620df0254b8",
    "usercart": [],
    "address": [],
    "orders": []
}
```

- **add Product Function (POST REQUEST)**

  http://localhost:8000/admin/addproduct

```json
{
  "product_name": "Iphone 15",
  "price": 1000,
  "rating": 9,
  "image": "iphone15.jpg"
}
```

Response: "succesfully added"

- **View all the Products in db GET REQUEST**

  http://localhost:8000/users/productview

Response:

```json
[
    {
        "Product_ID": "6538b06cccc7dcf403e817d5",
        "product_name": "Alienware x15",
        "price": 2500,
        "rating": 10,
        "image": "alienware.jpg"
    },
    {
        "Product_ID": "6538b0baccc7dcf403e817d7",
        "product_name": "Lenovo Ideapad 3 15ALC6",
        "price": 300000,
        "rating": 7,
        "image": "ideapad315alc6.jpg"
    },
    {
        "Product_ID": "6538b0d5ccc7dcf403e817d9",
        "product_name": "Panteon PS100",
        "price": 8000,
        "rating": 9,
        "image": "panteonps100.jpg"
    },
    {
        "Product_ID": "6538b0ecccc7dcf403e817db",
        "product_name": "Vivo Y21",
        "price": 100000,
        "rating": 8,
        "image": "vivoy21.jpg"
    },
    {
        "Product_ID": "65d5f327e7dd3620df0254ba",
        "product_name": "Iphone 15",
        "price": 1000,
        "rating": 9,
        "image": "iphone15.jpg"
    }
]
```

- **Search Product by regex function (GET REQUEST)**

defines the word search sorting
http://localhost:8000/users/search?name=15

Response:

```json
[
    {
        "Product_ID": "6538b06cccc7dcf403e817d5",
        "product_name": "Alienware x15",
        "price": 2500,
        "rating": 10,
        "image": "alienware.jpg"
    },
    {
        "Product_ID": "6538b0baccc7dcf403e817d7",
        "product_name": "Lenovo Ideapad 3 15ALC6",
        "price": 300000,
        "rating": 7,
        "image": "ideapad315alc6.jpg"
    },
    {
        "Product_ID": "65d5f327e7dd3620df0254ba",
        "product_name": "Iphone 15",
        "price": 1000,
        "rating": 9,
        "image": "iphone15.jpg"
    }
]
```

- **Adding the Products to the Cart (GET REQUEST)**
http://localhost:8000/addtocart?id=65d5f327e7dd3620df0254ba&userID=65d5f24ee7dd3620df0254b8
Response: "Successfully Added to the cart"

- **Removing Item From the Cart (GET REQUEST)**

http://localhost:8000/removeitem?id=65d5f327e7dd3620df0254ba&userID=65d5f24ee7dd3620df0254b8
Response: "Successfully removed from cart"

- **Listing the item in the users cart (GET REQUEST) and total price**

http://localhost:8000/listcart?id=65d5f24ee7dd3620df0254b8
Response:

```json
302000[
    {
        "Product_ID": "65d5f327e7dd3620df0254ba",
        "product_name": "Iphone 15",
        "price": 1000,
        "rating": 9,
        "image": "iphone15.jpg"
    },
    {
        "Product_ID": "65d5f327e7dd3620df0254ba",
        "product_name": "Iphone 15",
        "price": 1000,
        "rating": 9,
        "image": "iphone15.jpg"
    },
    {
        "Product_ID": "6538b0baccc7dcf403e817d7",
        "product_name": "Lenovo Ideapad 3 15ALC6",
        "price": 300000,
        "rating": 7,
        "image": "ideapad315alc6.jpg"
    }
]
```

- **Addding the Address (POST REQUEST)**
http://localhost:8000/addaddress?id=65d5f24ee7dd3620df0254b8
The Address array is limited to two values home and work address more than two address is not acceptable
```json
{
  "house_name": "8",
  "street_name": "23-proezd",
  "city_name": "Astana",
  "pin_code": "666777"
}
```
- **Editing the Home Address(PUT REQUEST)**
http://localhost:8000/edithomeaddress?id=65d5f24ee7dd3620df0254b8
```json
{
  "house_name": "3",
  "street_name": "23-proezd",
  "city_name": "Nur-Sultan",
  "pin_code": "000000"
}
```
Response: "succsdfully updated the home address"
- **Editing the Work Address(PUT REQUEST)**
http://localhost:8000/editworkaddress?id=65d5f24ee7dd3620df0254b8
```json
{
  "house_name": "71a",
  "street_name": "40 years of Victory",
  "city_name": "Shakhtinsk",
  "pin_code": "6667"
}
```
- **Delete Addresses(GET REQUEST)**

http://localhost:8000/deleteaddresses?id=xxxxxxxxxuser_idxxxxxxxxxxxxx
delete both addresses
Response: "succesfully deleted"

- **Cart Checkout Function and placing the order(GET REQUEST)**
After placing the order the items have to be deleted from cart functonality added
http://localhost:8000/cartcheckout?id=65d5f24ee7dd3620df0254b8
Response: "Successfully Placed the order"

- **Instantly Buying the Products(GET REQUEST)**
http://localhost:8000/instantbuy?userid=65d5f24ee7dd3620df0254b8&pid=6538b06cccc7dcf403e817d5
Response: "Successully placed the order"

```json
{
    "_id": "65d5f24ee7dd3620df0254b8",
    "first_name": "Artem",
    "last_name": "Popov",
    "password": "$2a$14$OxPsSCYBpuFyJE357jx.2eq3dCiGODbBP4i33HBSbBWDzDbuzEOIG",
    "email": "artempopovv@gmail.com",
    "phone": "87056570364",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJFbWFpbCI6ImFydGVtcG9wb3Z2QGdtYWlsLmNvbSIsIkZpcnN0X05hbWUiOiJBcnRlbSIsIkxhc3RfTmFtZSI6IlBvcG92IiwiVWlkIjoiNjVkNWYyNGVlN2RkMzYyMGRmMDI1NGI4IiwiZXhwIjoxNzA4NjA2NTA5fQ.Ud0wpUZyKuWUPg6O9IjHPot6xliN_bZ1R999aCNMJY4",
    "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJFbWFpbCI6IiIsIkZpcnN0X05hbWUiOiIiLCJMYXN0X05hbWUiOiIiLCJVaWQiOiIiLCJleHAiOjE3MDkxMjQ5MDl9.8cMbKYkTZYTZi2-1eiPIM3tRvfXq9EQqCZuoM0GyW2Q",
    "created_at": "2024-02-21T12:53:34Z",
    "updated_at": "2024-02-21T12:55:09Z",
    "user_id": "65d5f24ee7dd3620df0254b8",
    "usercart": [
        {
            "Product_ID": "6538b0baccc7dcf403e817d7",
            "product_name": "Lenovo Ideapad 3 15ALC6",
            "price": 300000,
            "rating": 7,
            "image": "ideapad315alc6.jpg"
        },
        {
            "Product_ID": "6538b0baccc7dcf403e817d7",
            "product_name": "Lenovo Ideapad 3 15ALC6",
            "price": 300000,
            "rating": 7,
            "image": "ideapad315alc6.jpg"
        }
    ],
    "address": [],
    "orders": [
        {
            "Order_ID": "65d5f80de7dd3620df0254bf",
            "order_list": [
                {
                    "Product_ID": "65d5f327e7dd3620df0254ba",
                    "product_name": "Iphone 15",
                    "price": 1000,
                    "rating": 9,
                    "image": "iphone15.jpg"
                },
                {
                    "Product_ID": "65d5f327e7dd3620df0254ba",
                    "product_name": "Iphone 15",
                    "price": 1000,
                    "rating": 9,
                    "image": "iphone15.jpg"
                },
                {
                    "Product_ID": "6538b0baccc7dcf403e817d7",
                    "product_name": "Lenovo Ideapad 3 15ALC6",
                    "price": 300000,
                    "rating": 7,
                    "image": "ideapad315alc6.jpg"
                },
                {
                    "Product_ID": "6538b06cccc7dcf403e817d5",
                    "product_name": "Alienware x15",
                    "price": 2500,
                    "rating": 10,
                    "image": "alienware.jpg"
                }
            ],
            "ordered_at": "2024-02-21T13:18:05.143Z",
            "total_price": 302000,
            "discount": null,
            "payment_method": {
                "Digital": false,
                "COD": true
            }
        },
        {
            "Order_ID": "65d5f86be7dd3620df0254c0",
            "order_list": [
                {
                    "Product_ID": "6538b06cccc7dcf403e817d5",
                    "product_name": "Alienware x15",
                    "price": 2500,
                    "rating": 10,
                    "image": "alienware.jpg"
                }
            ],
            "ordered_at": "2024-02-21T13:19:39.478Z",
            "total_price": 2500,
            "discount": null,
            "payment_method": {
                "Digital": false,
                "COD": true
            }
        }
    ]
}
```
