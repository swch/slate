---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript
  - csharp

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

The CardSavr REST API is a service for managing payment card circulation on merchant websites. It uses REST principles and standard HTTP features, such as HTTP verbs, as well as several layers of security to protect sensitive data.

CardSavr responses and requests support JSON-formatted bodies only.

# Authentication

> To authorize, use this code:

```javascript
const { CardsavrHelper } = require("@strivve/strivve-sdk/lib/cardsavr/CardsavrJSLibrary-2.0");

const session = new CardsavrSession(this.cardsavr_server, 
    this.app_key, this.app_name, username, password);
const login_data = await session.init();
//await session.getCards({}); //session can now be used to make api calls
```

```csharp
using Switch.CardSavr.Http;

CardSavrHttpClient session = new CardSavrHttpClient(_cardsavrServer, 
  _appKey, _appName, userName, password);
CardSavrResponse<LoginResult> login = await session.Init();

//await session.getCardsAsync(); //session can now be used to make api calls
```

```shell
# With a shell, you must first establish a session, followed by 
# a login command.  Note that the cookies from the session call 
# must be passed into the login call. Keep in mind, this ONLY works 
# with a development server that supports unsigned body requests. 
curl "https://api.INSTANCE.cardsavr.io/session/start" 
  -H "trace: {\"key\": \"my_trace\"}" -c ~/_cookies

curl -iv -d "{\"password\": \"PASSWORD\", \"userName\": \"USERNAME\"}" 
  -H "Content-Type: application/json" "https://api.INSTANCE.cardsavr.io/session/login" 
  -H "trace: {\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
  
```

> You can retrieve an integrator name/key and an agent username/password from developers@strivve.com

There is more information in the [session endpoint](#session) docuemtnation. If you decide not to use one of our SDKs, you are responsible for encryption of all bodies passed into the REST API.  

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```javascript
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```csharp
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```javascript
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```csharp
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```javascript
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```csharp
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

