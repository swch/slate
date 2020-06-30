---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript
  - csharp

toc_footers:
  - <a href='#'>Email us for a Developer Key</a>
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

const session = new CardsavrSession(cardsavr_server, 
    app_key, app_name, username, password);
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

> The SDK calls save the sessionSalt for future use, so all that is returned is the structure JSON of the login.  See [link to encryption stuff] on how to use the sessionSalt.

```json
{
  "sessionSalt": "kz2R3qexAkZqhoCalnNX9+6CLAMZ+"
}
```

```json
{
  "serverPublicKey": "sample_public_key",
  "status": "valid_password",
  "success": true,
  "user_id": 321,
  "user": 
  {
    "id": 123,
    "username": "john_smith_123",
    "first_name": "John",
    "last_name": "Smith",
    "email": "jsmith@email.com",
    "is_locked": true,
    "role": "dev",
    "created_on": "2018-04-19T23:10:36.657Z",
    "last_updated_on": null
  }
}
```

There is more information in the [session endpoint](#session) documentation. If you decide not to use one of the Strivve SDKs, you are responsible for encryption of all bodies passed into the REST API.  

<aside class="notice">
The cardsavr server, app key, app name, and the application username/password must be attained from developers@strivve.com.  See the definitions of these settings [link to app key definitions] here.
</aside>

# Headers

There is a set of required and optional headers.  The SDKs abstract most of these settings, but it's important to understand how they are used when making REST calls.

## Trace 

> Setting a sample Trace Header

```javascript
//initialize as part of the session -- defaults to 
//the unique username of the session
const session = new CardsavrSession(cardsavr_server, 
    app_key, app_name, username, password, null, null, 
    JSON.stringify({key: "NlOFNNlKabi7Fn26CLw="}));

//or change the trace mid-session 
session.setHeaders({"trace": JSON.stringify({key: "NlOFNNlKabi7Fn26CLw="}));

//or per request
await session.getUsers({}, {}, {trace: JSON.stringify({key: "NlOFNNlKabi7Fn26CLw="})}); 
```

```csharp
//Add a trace at the start of the session
CardSavrHttpClient session = new CardSavrHttpClient(_cardsavrServer, 
  _appKey, _appName, userName, password, null, "{\"key\": \"my_trace\"}");

//or per request
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
headers.Add("trace", "{\"key\": \"my_trace\"}");

CardSavrResponse<List<User>> result = await http.GetUsersAsync(null, null, headers);
```

```shell
curl "https://api.INSTANCE.cardsavr.io/cardsavr_users" 
  -H "trace: {\"key\": \"NlOFNNlKabi7Fn26CLw==\", \"bid\": \"hEOF26sbi7FCNNlLw==\"}" -c ~/_cookies
```

`"trace": JSON-stringified trace object`

CardSavr uses trace headers to trace all request-related activity within the CardSavr infrastructure. When a request is made to CardSavr, any ID included in the trace header will appear in all logging associated with that request. This allows for quick troubleshooting and monitoring. .  

The trace header takes a JSON-stringified object, which can be as simple or as complex as necessary for the given application.  The trace is a **required header**, and must contain at least a trace "key".  Within the SDKs, the trace key defaults to the username of the session.

Type | Description | Example
--------- | ---------- | -----------
key | unique key that identifies a request or set of requests | `trace: '{ "key": "hEOFNKapn26sbi7FCNNlLw==" }'

A trace header can contain multiple trace IDs. It is up to the developer to mint trace IDs in a way that best categorizes their app's requests. If a backend server is used, adding the trace IDs into the backend server logs can yield additional tracing efficacy.

## Hydration

> Setting a sample Hydration Header

```javascript
//or per request
await session.getCards(123, {}, { "hydration": JSON.stringify(["address"]) });
```

```csharp
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
headers.Add("hydration", "[\"address\"]");

CardSavrResponse<List<Card>> result = await 
  http.GetCardsAsync(123);
```

```shell
curl "https://api.INSTANCE.cardsavr.io/cardsavr_cards/123" 
  -H "trace: {\"key\": \"NlOFNNlKabi7Fn26CLw==\"}" 
  -H "hydration: [\"address\"]" 
  -c ~/_cookies
```

```json
{
  "id": 123,
  "cardholder_id": 3,
  "bin_id": 5,
  "address_id": 7,
  "par": "Q1J4AwSWD4Dx6q1DTo0MB21XDAV76",
  "expiration_month": "03",
  "expiration_year": "20",
  "name_on_card": "Joe Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "created_on": "2019-02-06T20:33:23.094Z",
  "last_updated_on": "2019-03-13T22:32:30.897Z",
  "address": 
    { "user_id": 3,
      "is_primary": false,
      "address1": "12345 Harris Ave",
      "address2": "STE. 601",
      "city": "Seattle",
      "subnational": "WA",
      "country": "USA",
      "postal_code": "98133",
      "postal_other": 98133-1234,
      "created_on": "2019-02-02T10:12:51.081Z",
      "last_updated_on": "2019-02-06T20:33:23.094Z"
  }
}
```

`{"hydration": {JSON-stringified array of resources to be hydrated}}`

For requests against a resource type that contains foreign key references (e.g. 'address_id' for 'cardsavr_cards'), a hydration header will "hydrate" (i.e. fill out) any of the resources indicated. Therefore, any objects returned in the response body will contain additional key-value pairs for each of the resources listed, where the key is the resource name (e.g. "address" in the previous example) and the value is the full object.

For example, including the header {hydration: '["address"]'} in a successful PUT request to '/cardsavr_cards/123' would return the updated card with an additional 'address' property containing the full address object associated with that card.

**Nested hydration** can also be used. For example, the following header:

`{"hydration": '["card.cardholder"]'}`

for the endpoint '/place_card_on_multiple_sites_jobs' would hydrate the associated card AND cardholder (i.e. user) associated with the card. Hydration headers can be used with any endpoint for any resource that contains foreign key references.

## Client Application

> Setting a custom application header (defaults to app name)

```javascript
session.setSessionHeaders( {'client-application': 'my-client-app' });
```

```csharp
http.SetIdentificationHeader('my-client-app');
```

```shell
curl "https://api.INSTANCE.cardsavr.io/cardsavr_cards/123" 
  -H "trace: {\"key\": \"NlOFNNlKabi7Fn26CLw==\"}" 
  -H "client-application: \"my-client-app\"" 
  -c ~/_cookies
```

`{'client-application': {client application name}}`

Your client application name will appear in the CardSavr logs alongside each request and response for your app, making troubleshooting and any other information retrieval much easier. Choose a name that clearly identifies your specific app for improved log searching (e.g. "acmebank-web-app").  When using the SDKs, the client-application defaults to the integrator name, and this is generally acceptable for most use cases.  This is an optional header, but recommended when not using the SDK.

## Paging

> Setting a custom application header (defaults to app name)

```javascript
//javascript SDK supports a json object as a paging header
await session.getCards(123, { page: 1 });
```

```csharp
```

```shell
curl "https://api.INSTANCE.cardsavr.io/cardsavr_cards/123" 
  -H "trace: {\"key\": \"NlOFNNlKabi7Fn26CLw==\"}" 
  -H "paging: \"{\"page\": \"1\"}\"" 
  -c ~/_cookies
```

`{'paging': 'JSON-stringified paging object'}`

CardSavr uses paging headers in both requests to and responses from batch GET endpoints. When sent with a batch GET request, a paging header specifies the length, sorting criterion, page number, and order of the data returned. Since each batch GET request can only return one page of data at a time, paging headers give users more control over the data they receive back.

If no paging header is submitted with the request, default values are applied (see table).

**Note**: CardSavr sends a paging header with each batch GET response to provide details about the page returned.

In the example header at right sent to '/cardsavr_cards', the second page of 25 results would be returned, sorted in descending order by PAR.

### Parameters
The paging header takes a JSON stringified object with the following properties. If a paging header is not included, the page of results will use the default values.

Property name | Type | Description | Default value
------------- | -----| ----------- | -------------
page | integer | The page to be returned | 1
page_length | integer | Length of each page | 25
sort* | string | Property to sort results by | "id"
descending | boolean | If true, sorts results in descending order; if false, sorts in ascending order | false

*Check GET endpoint documentation to see which properties are sort-able

## Safe key

`{'cardholder-safe-key': '+h+W0c9EsgvFLufWnu87iV6ErDF7dpyT5YUEbb/oOIw='}`
`{'new-cardholder-safe-key': '+h+W0c9EsgvFLufWnu87iV6ErDF7dpyT5YUEbb/oOIw='}`

You must send an encrypted cardholder safe key header for each request that involves safe-protected information. Saving users (/cardsavr_users), accounts (/cardsavr_accounts) and cards (/cardsavr_cards) require the key to write encrypted data like PANs and merchant site passwords to the server side safe.  Safe keys can be stored by the third party, or they can optionally be stored by Strivve within Cardsavr. Individual endpoint documentation will indicate if a safe key header is required.

When creating a user, or rotating a safe key, you must provide a 'new-cardholder-safe-key' header.  In the case of rotating the safe key, both headers are required.

See the [link] cardholder safe key section for more information on generating and using safe keys.

# Kittens

## Get All Kittens

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

