
#Admin

<!-- ################################################################################################## -->

## Retrieve Merchants

> Request:

```plaintext
/admin/merchants
```

> Response:

```json
{
  "code": 200,
  "data": [
      {
          "id": "eba3a23c-6b37-4e7e-b8e5-274365f36d02",
          "email":  "jane@merchant.com",
          "mobile": "6512345678",
          "image": "http://s3bucket/jane_merchant.png",
          "role": "merchant"
      },
      {
          "id": "bc6ba085-a2f7-48e8-928c-33d424385527",
          "email":  "john@merchant.com",
          "mobile": "6512345678",
          "image": "http://s3bucket/john_merchant.png",
          "role": "merchant"
      },
      ...
  ]
}
```

This endpoint retrieves the list of merchants

### HTTP Request

`GET /admin/merchants`

<!-- ################################################################################################## -->

## Retrieve a Merchant

> Request:

```plaintext
/admin/merchants/bc6ba085-a2f7-48e8-928c-33d424385527
```

> Response:

```json
{
  "code": 200,
  "data": {
      "id": "bc6ba085-a2f7-48e8-928c-33d424385527",
      "email":  "john@merchant.com",
      "mobile": "6512345678",
      "image": "http://s3bucket/john_merchant.png",
      "role": "merchant"
  }
}  
```

This endpoint retrieves a merchant's data.

### HTTP Request

`GET /admin/merchants/:merchantid`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
merchantid | true | Merchant's ID

<!-- ################################################################################################## -->

## Create a Merchant

> Request:

```plaintext
/admin/mechants
```

> Body:

```json
{
    "email":  "john@merchant.com",
    "mobile": "6512345678",
    "image": "data:image/png;base64,iVBO...Jggg==",
    "password": "6UQbeggYOL8wgvL8CAWqYw=="
}
```
> Response:

```json
{
    "code": 200,
    "data": {
        "id": "bc6ba085-a2f7-48e8-928c-33d424385527",
        "email":  "john@merchant.com",
        "mobile": "6512345678",
        "image": "http://s3bucket/john_merchant.png",
        "role": "merchant",
        "password": "6UQbeggYOL8wgvL8CAWqYw=="
    }
}  
```

This endpoint creates a merchant.

### HTTP Request

`POST /admin/merchants`

### Body Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | true | 
mobile | true | 
image | true | `"base64 data"`
password | true | `"aes256"`

<!-- ################################################################################################## -->

## Update a Merchant

> Request:

```plaintext
/admin/merchants/bc6ba085-a2f7-48e8-928c-33d424385527
```

> Body:

```json
{
    "image": "data:image/png;base64,qRVD...yGhy==",
    "mobile": "6587654321",
    "password": "QAPy3/Uoo4twNJs5vtd5dA=="
}
```
> Response:

```json
{
    "code": 200,
    "data": {
        "id": "bc6ba085-a2f7-48e8-928c-33d424385527",
        "email":  "john@merchant.com",
        "mobile": "6587654321",
        "image": "http://s3bucket/john_merchant.png",
        "role": "merchant",
        "password": "QAPy3/Uoo4twNJs5vtd5dA=="
    }
}  
```

This endpoint updates a merchant's data.

### HTTP Request

`PUT /admin/merchants/:merchantid`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
merchantid | true | Merchant's ID

### Body Parameters

Parameter | Required | Description
--------- | ------- | -----------
mobile | false | 
image | true | `"base64 data"`
password | false | `"aes256"`

<!-- ################################################################################################## -->

## Delete a Merchant

> Request:

```plaintext
/admin/merchants/bc6ba085-a2f7-48e8-928c-33d424385527
```

> Body:

```json
{
    "image": "data:image/png;base64,qRVD...yGhy==",
    "mobile": "6587654321",
    "password": "QAPy3/Uoo4twNJs5vtd5dA=="
}
```
> Response:

```json
{
    "code": 200,
    "data": {}
}  
```

This endpoint deletes a merchant.

### HTTP Request

`DELETE /admin/merchants/:merchantid`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
merchantid | true | Merchant's ID

<!-- ################################################################################################## -->

## Schedule Hot Deals

> Request:

```plaintext
/admin/deals-hot
```

> Body:

```json
{
    "dealId": "298e489b-a721-4eac-a5d4-e16069af3d42",
    "from": "1564617600",
    "to": "1567296000"
}
```
> Response:

```json
{
    "code": 200,
    "data": {
        "id": "298e489b-a721-4eac-a5d4-e16069af3d42",
        "merchantId": "bc6ba085-a2f7-48e8-928c-33d424385527",
        "name": "Free Honey Green Tea",
        "qty": 100,
        "points": : 100,
        "image": "https://s3bucket/free_honey_green_tea.png",
        "from": "1564617600",
        "to": "1567296000"
    }
}  
```

This endpoint 

### HTTP Request

`POST /admin/deals/hot`

### Body Parameters

Parameter | Required | Description
--------- | ------- | -----------
dealId | true | Deal's ID
from | true | `"epoch"` Start date of deal's promotion
to | true | `"epoch"` End date of deal's promotion

