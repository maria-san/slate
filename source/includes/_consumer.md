
# Consumer

<!-- ################################################################################################## -->

## Earn Points

> Request:

```plaintext
/consumers/42b7b87a-9c9e-47d1-bf67-b2d7ae191220/points-earn
```


> Body:

```json
{
  "merchantId": "bc6ba085-a2f7-48e8-928c-33d424385527",
  "amount": 9000
}
```

> Response:

```json
{
  "code": 200,
  "data": {
      "id": "eba3a23c-6b37-4e7e-b8e5-274365f36d02",
      "pin": "123456",
      "consumerId": "42b7b87a-9c9e-47d1-bf67-b2d7ae191220",
      "merchantId": "bc6ba085-a2f7-48e8-928c-33d424385527",
      "type": "merchant-consumer",
      "points": 88,
      "status": "pending",
      "createdAt": 1565751039,
      "updatedAt": 1565751039
  }
}
```

This endpoint initiates a transaction between the consumer and the merchant for earning points.

### HTTP Request

`POST /consumers/:consumerid/points-earn`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
consumerid | true | Consumer's ID

### Body Parameters

Parameter | Required | Description
--------- | ------- | -----------
merchantId | true | Merchant's ID
amount | true | total spending = x dollars

<!-- ################################################################################################## -->

## Redeem a Deal

> Request:

```plaintext
/consumers/42b7b87a-9c9e-47d1-bf67-b2d7ae191220/points-redeem
```


> Body:

```json
{
  "dealId": "298e489b-a721-4eac-a5d4-e16069af3d42"
}
```

> Response:

```json
{
  "code": 200,
  "data": {
      "id": "eba3a23c-6b37-4e7e-b8e5-274365f36d02",
      "consumerId": "42b7b87a-9c9e-47d1-bf67-b2d7ae191220",
      "merchantId": "4ebe3e43-3e28-4e25-87b9-f6f1ca1ecb57",
      "type": "consumer-merchant",
      "points": 100,
      "dealId": "cc7290a4-3bf3-48d0-a093-13a0899514f5",
      "status": "pending",
      "createdAt": 1565751039,
      "updatedAt": 1565751039
  }
}
```

This endpoint initiates a transaction between the consumer and the merchant for deal redemption.

### HTTP Request

`POST /consumers/:consumerid/points-redeem`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
consumerid | true | Consumer's ID

### Body Parameters

Parameter | Required | Description
--------- | ------- | -----------
dealid | true | Deal's ID

<!-- ################################################################################################## -->

## Retrieve Deals

> Request:

```plaintext
/consumers/deals
```

> Response:

```json
{
  "code": 200,
  "data": [
      {
          "id": "eba3a23c-6b37-4e7e-b8e5-274365f36d02",
          "merchantId": "bc6ba085-a2f7-48e8-928c-33d424385527",
          "name": "Free Honey Green Tea",
          "qty": 100,
          "points": 100,
          "image": "https://s3bucket/free_honey_green_tea.png"
      },
      {
          "id": "cc7290a4-3bf3-48d0-a093-13a0899514f5",
          "merchantId": "4ebe3e43-3e28-4e25-87b9-f6f1ca1ecb57",
          "name": "Free Green Milk Tea",
          "qty": 100,
          "points": 100,
          "image": "https://s3bucket/free_green_milk_tea.png"
      },
      ...
  ]
}
```

This endpoint retrieves a list of all available deals.

### HTTP Request

`GET /consumers/deals`

<!-- ################################################################################################## -->

## Retrieve Hot Deals

> Request:

```plaintext
/consumers/deals-hot
```

> Response:

```json
{
  "code": 200,
  "data": [
      {
          "id": "eba3a23c-6b37-4e7e-b8e5-274365f36d02",
          "merchantId": "bc6ba085-a2f7-48e8-928c-33d424385527",
          "name": "Free Honey Green Tea",
          "qty": 100,
          "points": 100,
          "image": "https://s3bucket/free_honey_green_tea.png"
      },
      {
          "id": "cc7290a4-3bf3-48d0-a093-13a0899514f5",
          "merchantId": "4ebe3e43-3e28-4e25-87b9-f6f1ca1ecb57",
          "name": "Free Green Milk Tea",
          "qty": 100,
          "points": 100,
          "image": "https://s3bucket/free_green_milk_tea.png"
      },
      ...
  ]
}
```

This endpoint retrieves a list of all available deals.

### HTTP Request

`GET /consumers/deals-hot`

<!-- ################################################################################################## -->

## Retrieve Transactions

> Request:

```plaintext
/consumers/42b7b87a-9c9e-47d1-bf67-b2d7ae191220/transactions
```


> Body:

```json
{
  "dealId": "298e489b-a721-4eac-a5d4-e16069af3d42"
}
```

> Response:

```json
{
  "code": 200,
  "data": [
      {
          "id": "eba3a23c-6b37-4e7e-b8e5-274365f36d02",
          "pin": "12345678",
          "consumerId": "42b7b87a-9c9e-47d1-bf67-b2d7ae191220",
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
          "consumerId": "42b7b87a-9c9e-47d1-bf67-b2d7ae191220",
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

This endpoint retrieves a list of the consumer's transactions

### HTTP Request

`GET /consumers/:consumerid/transactions`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
consumerid | true | Consumer's ID

<!-- ################################################################################################## -->