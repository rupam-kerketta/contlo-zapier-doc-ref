# Contlo <> Zapier Doc

## Authentication
For authentication the user needs to have the store's private api key. It can be found in the [settings section](https://marketing.contlo.com/home#/settings).

This endpoint allows you to authenticate using the stores private API key.

> [POST] https://marketing.contlo.com/api/integrations/zapier

### Headers

| Name | Required | Type | Description |
|------|----------|------|-------------|
|X-API-KEY      |  required        |   string   |   This should be the store's private API key          |

### Response
```js
    // On valid private API key response
    {
        success: true
    }

    // On invalid private API key response
    {
        success: false
    }
```

## Triggers
There are two triggers available in the Contlo Zapier App.
| Trigger Name    | Description |
|-----------------|-------------|
| New Subscribers | Triggers when new subscribers are created in the Contlo Platform. (polling) |
| New Customers   | Triggers when new customers are create in the Contlo Platform. (polling)         |

**New Subscribers Endpoint**
> [GET] https://marketing.contlo.com/api/integrations/zapier/subscribers

Response
```js
[
    {
    "country": "India",
    "email": "contlosri+30293@gmail.com",
    "first_name": "Srikanth",
    "geo_country": "india",
    "last_name": "C G",
    "name": "Srikanth C G",
    "phone_number": "+917019690733",
    "province": "Karnataka",
    "id": 23897
  }
]
```


**New Customers Endpoint**
> [GET] https://marketing.contlo.com/api/integrations/zapier/customers

Response
```js
[
    {
        "country": "India",
        "customer_id": 8534,
        "email": "cg.srikanth1+24839@gmail.com",
        "first_name": "Srikanth",
        "geo_country": null,
        "last_name": "C G",
        "name": "Srikanth C G",
        "phone_number": "+917019690733",
        "province": "Karnataka",
        "id": 24192
    }
]
```

## Actions
| Action Name         | Description                               |
|---------------------|-------------------------------------------|
| Create Event        | Create a new event in the Contlo Platform. |
| Create Subscriber   | Creates a new subscriber for the shop in the Contlo Platform.         |

**Create Event Endpoint**
> [POST] https://marketing.contlo.com/v1/track

Example request body
```js
{
    "event": "submitted_review",
    "email": "john@example.com",
    "phone_number": "+12092122222",
    "profile_properties": {
        "property1": "value1"
    },
    "properties": {
        "email": "john@example.com",
        "rating": 4
    }
}
```

Response
```js
{
    success: true
}
```

**Create Subscriber Endpoint**
> [POST] https://marketing.contlo.com/v1/identify

Example request body
```js
{
    "custom_properties": {
        "property1": "value1"
    },
    "email": "jack@example.com",
    "first_name": "Jack",
    "last_name": "Sparrow",
    "phone_number": "+12322222212",
    "country": "India",
    "zip": "560037",
    "city": "Bangalore",
}
```

Response
```js
{
    success: true
}
```