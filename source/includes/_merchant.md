
# Merchant

<!-- ################################################################################################## -->

## Reward Points

> Request:

```plaintext
/merchants/bc6ba085-a2f7-48e8-928c-33d424385527/points-reward
```


> Body:

```json
{
  "transactionId": "eba3a23c-6b37-4e7e-b8e5-274365f36d02",
  "status": "approved"
}
```

> Response:

```json
{
  "code": 200,
  "data": {
      "id": "eba3a23c-6b37-4e7e-b8e5-274365f36d02",
      "pin": "123456",
      "consumerId": "cc7290a4-3bf3-48d0-a093-13a0899514f5",
      "merchantId": "bc6ba085-a2f7-48e8-928c-33d424385527",
      "type": "merchant-consumer",
      "points": 88,
      "status": "approved",
      "createdAt": 1565751039,
      "updatedAt": 1565753517
  }
}
```

This endpoint approves or rejects the consumer's transaction for earning points.

### HTTP Request

`POST /merchants/:merchantid/points-reward`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
merchantid | true | Merchant's ID

### Body Parameters

Parameter | Required | Description
--------- | ------- | -----------
transactionId | true | `uuid`
status | true | `"approved"` `"rejected"` 

<!-- ################################################################################################## -->

## Process Redemption

> Request:

```plaintext
/merchants/bc6ba085-a2f7-48e8-928c-33d424385527/points-redemption
```

> Body:

```json
{
  "transactionId": "d7407721-c29c-4e6e-b092-e3eb3b4eb60d",
  "status": "approved"
}
```

> Response:

```json
{
  "code": 200,
  "data": {
      "id": "d7407721-c29c-4e6e-b092-e3eb3b4eb60d",
      "pin": "123456",
      "consumerId": "cc7290a4-3bf3-48d0-a093-13a0899514f5",
      "merchantId": "bc6ba085-a2f7-48e8-928c-33d424385527",
      "type": "consumer-merchant",
      "points": 99,
      "dealId": "298e489b-a721-4eac-a5d4-e16069af3d42",
      "status": "approved",
      "createdAt": 1565751039,
      "updatedAt": 1565753517
  }
}
```

This endpoint approves or rejects the consumer's transaction for redeeming a deal.

### HTTP Request

`POST /merchants/:merchantid/points-redemption/`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
merchantid | true | Merchant's ID

### Body Parameters

Parameter | Required | Description
--------- | ------- | -----------
transactionId | true | `uuid`
status | true | `"approved"` `"rejected"` 

<!-- ################################################################################################## -->

## Retrieve Transactions

> Request:

```plaintext
/merchants/bc6ba085-a2f7-48e8-928c-33d424385527/transactions
```

> Response:

```json
{
  "code": 200,
  "data": [
      {
          "id": "eba3a23c-6b37-4e7e-b8e5-274365f36d02",
          "pin": "12345678",
          "consumerId": "cc7290a4-3bf3-48d0-a093-13a0899514f5",
          "merchantId": "bc6ba085-a2f7-48e8-928c-33d424385527",
          "type": "consumer-merchant",
          "points": 88,
          "dealId": "4ebe3e43-3e28-4e25-87b9-f6f1ca1ecb57",
          "status": "approved",
          "validated": true,
          "createdAt": 1565751039,
          "updatedAt": 1565753517
      },
      {
          "id": "dec4840f-10dd-446a-9219-2fe4eef1a96a",
          "pin": "12345678",
          "consumerId": "cc7290a4-3bf3-48d0-a093-13a0899514f5",
          "merchantId": "bc6ba085-a2f7-48e8-928c-33d424385527",
          "type": "merchant-consumer",
          "points": 88,
          "status": "approved",
          "validated": false,
          "createdAt": 1565751039,
          "updatedAt": 1565753517
      },
      ...
  ]
}
    
```

This endpoint retrieves a list of the merchant's transactions

### HTTP Request

`POST /merchants/:merchantid/points-redemption/`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
merchantid | true | Merchant's ID

<!-- ################################################################################################## -->

## Retrieve a Transaction

> Request:

```plaintext
/merchants/bc6ba085-a2f7-48e8-928c-33d424385527/transactions/eba3a23c-6b37-4e7e-b8e5-274365f36d02
```

> Response:

```json
{
  "code": 200,
  "data": {
      "id": "eba3a23c-6b37-4e7e-b8e5-274365f36d02",
      "pin": "12345678",
      "consumerId": "cc7290a4-3bf3-48d0-a093-13a0899514f5",
      "merchantId": "bc6ba085-a2f7-48e8-928c-33d424385527",
      "type": "consumer-merchant",
      "points": 88,
      "dealId": "4ebe3e43-3e28-4e25-87b9-f6f1ca1ecb57",
      "status": "approved",
      "validated": true,
      "createdAt": 1565751039,
      "updatedAt": 1565753517
  }
}
    
```

This endpoint retrieves a single transaction of the merchant.

### HTTP Request

`POST /merchants/:merchantid/transactions/:transactionid`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
merchantid | true | Merchant's ID
transactionid | true | Transaction's ID

<!-- ################################################################################################## -->

## Retrieve Deals

> Request:

```plaintext
/merchants/bc6ba085-a2f7-48e8-928c-33d424385527/deals
```

> Response:

```json
{
  "code": 200,
  "data": [
      {
          "id": "eba3a23c-6b37-4e7e-b8e5-274365f36d02",
          "name": "Free Honey Green Tea",
          "qty": 100,
          "image": "https://s3bucket/free_honey_green_tea.png"
      },
      {
          "id": "cc7290a4-3bf3-48d0-a093-13a0899514f5",
          "name": "Free Green Milk Tea",
          "qty": 100,
          "image": "https://s3bucket/free_green_milk_tea.png"
      },
      ...
  ]
}   
```

This endpoint retrieves a list of merchant's deals.

### HTTP Request

`GET /merchants/:merchantid/deals`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
merchantid | true | Merchant's ID

<!-- ################################################################################################## -->

## Retrieve a Deal

> Request:

```plaintext
/merchants/bc6ba085-a2f7-48e8-928c-33d424385527/deals/eba3a23c-6b37-4e7e-b8e5-274365f36d02
```

> Response:

```json
{
  "code": 200,
  "data" : {
      "id": "eba3a23c-6b37-4e7e-b8e5-274365f36d02",
      "name": "Free Honey Green Tea",
      "qty": 100,
      "points": 100,
      "image": "https://s3bucket/free_honey_green_tea.png"
  }
}
```

This endpoint retrieves a single deal of the merchant.

### HTTP Request

`GET /merchants/:merchantid/deals/:dealid`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
merchantid | true | Merchant's ID
dealid | true | Deal's ID

<!-- ################################################################################################## -->

## Create a Deal

> Request:

```plaintext
/merchants/bc6ba085-a2f7-48e8-928c-33d424385527/deals/eba3a23c-6b37-4e7e-b8e5-274365f36d02
```

> Body:

```json
{
  "name": "Free Honey Green Tea",
  "qty": 100,
  "points": 80,
  "image": "data:image/png;base64,iVBO...Jggg=="
}
```

> Response:

```json
{
  "code": 200,
  "data": {
      "id": "eba3a23c-6b37-4e7e-b8e5-274365f36d02",
      "name": "Free Honey Green Tea",
      "qty": 100,
      "points": 80,
      "image": "https://s3bucket/free_honey_green_tea.png"
  }
}
```

This endpoint creates a deal.

### HTTP Request

`POST /merchants/:merchantid/deals`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
merchantid | true | Merchant's ID

### Body Parameters

Parameter | Required | Description
--------- | ------- | -----------
name | true | 
qty | true | 
points | true | 
image | true | `"base64 data"`

<!-- ################################################################################################## -->

## Update a Deal

> Request:

```plaintext
/merchants/bc6ba085-a2f7-48e8-928c-33d424385527/deals/eba3a23c-6b37-4e7e-b8e5-274365f36d02
```

> Body:

```json
{
  "name": "Free Black Milk Tea",
  "qty": 50,
  "points": 100,
  "image": "data:image/png;base64,iFTa...ecgs=="
}
```

> Response:

```json
{
  "code": 200,
  "data": {
      "id": "eba3a23c-6b37-4e7e-b8e5-274365f36d02",
      "name": "Free Black Milk Tea",
      "qty": 50,
      "points": 100,
      "image": "https://s3bucket/free_black_milk_tea.png"
  }
}
```

This endpoint updates a deal.

### HTTP Request

`PUT /merchants/:merchantid/deals/:dealid`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
merchantid | true | Merchant's ID
dealid | true | Deals's ID

### Body Parameters

Parameter | Required | Description
--------- | ------- | -----------
name | false | 
qty | false | 
points | false | 
image | false | `"base64 data"`

<!-- ################################################################################################## -->

## Delete a Deal

> Request:

```plaintext
/merchants/bc6ba085-a2f7-48e8-928c-33d424385527/deals/eba3a23c-6b37-4e7e-b8e5-274365f36d02
```

> Response:

```json
{
  "code": 200,
  "data": {}
}
```

This endpoint deletes a deal.

### HTTP Request

`DELETE  /merchants/:merchantid/deals/:dealid`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
merchantid | true | Merchant's ID
dealid | true | Deals's ID

<!-- ################################################################################################## -->