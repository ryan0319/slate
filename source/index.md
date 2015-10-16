---
title: API Reference

includes:
  - errors

search: true
---

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](http://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

## Authenticate

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "message": null,
  "payload": {
    "auth_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1aWQiOiI2MmIwMjRkMi05MWU3LTRkOGItYjljZS05NzA2YzI4YmI5OTQiLCJleHBpcmUiOiJcL0RhdGUoMTQ0NzUzNTM4ODI5NClcLyJ9.aZ5r3dh8lXOJTbVN2eVOxnueLOwSpUDpmwZs_CL5Mck",
    "curUserProfile": {
      "userProfileID": "62b024d2-91e7-4d8b-b9ce-9706c28bb994",
      "firstName": "test",
      "lastName": "test",
      "email": "test5@test.com",
      "birthday": "/Date(1443657600000)/",
      "profileImageUrl": null,
      "devices": [
        {
          "ID": "3eae3ea7-4ba4-4aef-b6d2-51d2ddd0c2eb",
          "deviceType": "device-type-android",
          "deviceToken": "APA91bFfXl8WAfJ0UawCJC87NyB0DkL1qxHnsIxUYjZXzeUCapeNQhtOVELkoEXfdHpxf8zDHSBNG_lRZcqSZWZmrmEewc5Uu1WNGFuZT3auKbeTfZ4CkXaxakUVdslCyDNrxioKvBAQ",
          "shouldSendPN": true
        }
      ]
    }
  }
}
```

This endpoint authenticates a user.

### HTTP Request

`POST /auth/authenticate`

### Query Parameters

Parameter | Description
--------- | ------- | -----------
email | User's email.
password | User's password.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Register User

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "message": null,
  "payload": {
    "auth_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1aWQiOiI0MDJhNjExMS04YjZhLTQ0Y2MtOTg1Ni1mYjlkYTU5OTRlZDciLCJleHBpcmUiOiJcL0RhdGUoMTQ0NzUzODE3NjE4NClcLyJ9.KZsrogw2RUfQZv-uMXoWFjyXYEODKBmddtjy8qbtj_4",
    "curUserProfile": {
      "userProfileID": "402a6111-8b6a-44cc-9856-fb9da5994ed7",
      "firstName": "Joe",
      "lastName": "Blow",
      "email": "test15000@test.com",
      "birthday": "/Date(-625363200000)/",
      "profileImageUrl": null,
      "devices": []
    }
  }
}
```

This endpoint registers a user.

### HTTP Request

`POST /auth/registeruser`

### Query Parameters

Parameter | Description
--------- | ------- | -----------
email | User's email.
password | User's password.
firstname | User's first name.
lastname | User's last name.
birthday | User's birthday.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Password Recovery

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "message": null,
  "payload": {
    "message": "Password recovery email sent to test15000@test.com"
  }
}
```

This endpoint sends an email for password recovery to a user.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`POST /auth/passwordrecovery`

### URL Parameters

Parameter | Description
--------- | -----------
emailAddress | User's email.

## Complete / Confirm Registration

> The above command returns a string like this:

```json
Need output
```

This endpoint is used for a user to complete the registration process after email address confirmation.

<aside class="warning">This endpoint requires the ``auth-token`` header to be set to an authenticated token.</aside>

### HTTP Request

`POST /auth/completeregistration`

### URL Parameters

Parameter | Description
--------- | -----------
email | User's email.
password | The new user password.
passwordConfirmation | The new user password again.




# Menu

## Get Menu Categories

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "message": null,
  "payload": [
    {
      "id": "1dd75339-8407-4b75-bb46-f4c9a1c54347",
      "name": "Espresso Bar",
      "image": "http://www.cocoloco.ee/beta/wp-content/uploads/2014/02/cafe-latte.jpg",
      "ordinal": 1,
      "createDate": "/Date(1439263408000)/",
      "menuItems": [
        {
          "id": "1dd75339-8407-4b75-bb46-f4c9a1c59347",
          "name": "Latte",
          "shortName": "Latte",
          "price": 3.57,
          "description": null,
          "image": "http://cdn.hellogiggles.com/wp-content/uploads/2014/09/29/Latte-Art-Training-Product-Image__18860__17179_zoom.jpg",
          "ordinal": 1,
          "createDate": "/Date(1439263408000)/",
          "modifierGroups": [
            "0361aaac-d740-4498-8dd0-cba5183c038e",
            "49b83f1b-3458-4a60-b50f-64be38c962b6",
            "ec32c117-978b-48cb-abfb-83a18291b16a",
            "3a2ae1a3-a52a-4f10-8501-005c3978f96d",
            "5aaa9c67-1097-47c4-bf07-8edff926d228",
            "26fcbe52-2a86-4dc1-b34b-491733ca3ae5"
          ]
        },
        { ... }
      ]
    }
  ]
}
```

This endpoint gets menu items.

### HTTP Request

`GET /menu/getmenucategories`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | The page of the paginated results.
itemsperpage | 100 | The number of results to show per page.

## Get Modifier Groups

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "message": null,
  "payload": [
    {
      "id": "138a2b20-326a-490c-8087-9578acf3b410",
      "name": "Au Lait",
      "requiredSelections": 1,
      "isActive": false,
      "createDate": "/Date(-62135596800000)/",
      "modifiers": [
        {
          "id": "43d83541-371d-4227-b93d-d5861a2078e4",
          "name": "None",
          "groupName": "Au Lait",
          "ordinal": 1,
          "isDefault": true,
          "price": 0
        },
        {
          "id": "5ec4cb14-c274-43b1-bc73-2d7010d34f9a",
          "name": "3.25%",
          "groupName": "Au Lait",
          "ordinal": 2,
          "isDefault": false,
          "price": 0
        },
        {
          "id": "7f8a7ad8-baf0-4a09-8bcc-d2771a402c7d",
          "name": "1%",
          "groupName": "Au Lait",
          "ordinal": 3,
          "isDefault": false,
          "price": 0
        },
        {
          "id": "6f6f054b-cc35-48a7-b416-6c7086bd92f7",
          "name": "10%",
          "groupName": "Au Lait",
          "ordinal": 4,
          "isDefault": false,
          "price": 0
        },
        {
          "id": "a8672e08-83e7-4693-bf4b-ccf4452304dc",
          "name": "Almond Milk",
          "groupName": "Au Lait",
          "ordinal": 5,
          "isDefault": false,
          "price": 0
        },
        {
          "id": "8ca9e13d-3837-4664-8557-1461cbff9e74",
          "name": "Soy Milk",
          "groupName": "Au Lait",
          "ordinal": 6,
          "isDefault": false,
          "price": 0
        },
        {
          "id": "9f3f01cc-93cb-466b-8bad-873a2329379f",
          "name": "Lactose-Free",
          "groupName": "Au Lait",
          "ordinal": 7,
          "isDefault": false,
          "price": 0
        }
      ]
    },
    { ... }
  ]
}
```

This endpoint gets menu item modifier groups.


### HTTP Request

`GET /menu/getmodifiergroups`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | The page of the paginated results.
itemsperpage | 100 | The number of results to show per page.




# Order

## Place Order

> The above command returns JSON structured like this:

```json
{
  "success": true,
  "message": null,
  "payload": {
    "message": "Password recovery email sent to test15000@test.com"
  }
}
```

This endpoint places an order for a user.

<aside class="warning">This endpoint requires the ``auth-token`` header to be set to an authenticated token.</aside>

### HTTP Request

`POST /auth/placeorder`

### URL Parameters

Parameter | Subparameter | Description
--------- | -----------
items | | Array of items.
| menuitemid | The menu item id.
| quantity | The number of the current item to order.
| ordinal | The position in the order list to display the item.
| modifierids | Array of modifier ids.
note | |  Order notes.
percentgratuity | |  The gratuity percentage.

## Complete / Confirm Registration

> The above command returns a string like this:

```json
{
  "success": true,
  "message": null,
  "payload": {
    "id": "9197fbc5-6059-4334-a94c-97c9e1270cf4",
    "userFirstName": "Joe",
    "userLastName": "Blow",
    "userProfileImageUrl": "http://www.gravatar.com/avatar/5c34d2880234f93301298c65a85cf3a2",
    "status": "PENDING",
    "note": "Hurry please!",
    "price": 0,
    "gst": 0,
    "pst": 0,
    "hst": 0,
    "gratuity": 0,
    "total": 0,
    "createDate": "2015-10-16T15:25:32Z",
    "sendDate": null,
    "processedDate": null,
    "pickupDate": null,
    "orderItems": []
  }
}
```

This endpoint is used for a user to complete the registration process after email address confirmation.

<aside class="warning">This endpoint requires the ``auth-token`` header to be set to an authenticated token.</aside>

### HTTP Request

`POST /auth/completeregistration`

### URL Parameters

Parameter | Description
--------- | -----------
email | User's email.
password | The new user password.
passwordConfirmation | The new user password again.

