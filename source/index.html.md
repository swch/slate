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
  - session
  - rest
  - messages
  - errors

search: true
---

# Introduction

The CardSavr REST API is a service for managing payment card circulation on merchant websites. It uses REST principles and standard HTTP features, such as HTTP verbs, as well as several layers of security to protect sensitive data.

CardSavr responses and requests support JSON-formatted bodies only.

# API Level Encryption

The CardSavr service requires all API requests and responses to be signed and encrypted independent of TLS for all production environments. Development environments relax this to also allow plain text calls over TLS for learning and troubleshooting purposes. See See [Additional REST API Protection](https://developers.strivve.com/resources/cryptography/) for information on this requirement. The CardSavr SDK takes care of all API encryption and signing.  Applications directly implementing the REST API are responsible for implementing this security.

# Authentication

> To authorize, a session initialization followed by a login call is required:

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

REST calls support and/or require the following headers once the session is established.  

Header | Default | Type | Description
------ | ------- | ---- | -----------
trace | required | stringified JSON object | [See trace](#trace)
client-application | integrator name | string | unique per application, integrator name provided as default when using an SDK
authorization | preferred | string | contains the [integrator name and a prefix](https://developers.strivve.com/resources/encryption), populated by SDK libraries. This header is not required for use with Postman and Curl on development environments.
nonce | preferred | string (milliseconds) | contains the current UTC time in milliseconds, and therefore provides protection against [replay attacks](https://developers.strivve.com/resources/encryption). This header is not required for use with Postman and Curl on development environments.
signature | preferred | string | The [string-to-sign format](https://developers.strivve.com/resources/encryption) requires the URL-Path (decoded), the authorization header, and the nonce header.  Also part of the [SDK Libraries](https://developers.strivve.com/api-sdk/). This header is not required for use with Postman and Curl on development environments.
hydration | (none) | stringified JSON object | [See hydration](#hydration) 
paging | {"page": 1, "page_length": 25} | stringified JSON object | Only supported with GET calls. [See paging](#paging)
x-cardsavr-session-jwt | preferred | string | [See session tokens] (#session-tokens)
cookie | alternative | cookie format | [See cookie note] (#cookie-note)

## session-tokens

CardSavr needs to maintain an API session for state management including authentication, session key, replay prevention, etc.  Standard RFC-7519 JWT tokens are preferred for session persistence and cookies are used as a backup mechanism. The x-cardsavr-session-jwt header is used with token based session. The x-cardsavr-session-jwt header is managed transparently within the Strivve SDK.  It is the responsibility of applications directly using the direct REST protocol to set this header or provide cookies for each request.

With GET /session/start to begin a new session

  `"x-cardsavr-session-token": "null"` 

With all subsequent requests on a session

  `"x-cardsavr-session-token": value-returned-from-session-start`

### cookie-note

When the x-cardsavr-session-jwt header is not present in a /session/start request, CardSavr will fall back to setting and using a cookie named "CardSavrSession" for session persistence. This support is intended for use with cURL and Postman for testing and debugging. 

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

> Paging headers give you the flexibility to modify the number of results returned, and how they should be sorted.

```javascript
//javascript SDK supports a json object as a paging header
await session.getCards(123, { page: 1 });
```

```csharp
Paging paging = new Paging() { PageLength = 100 };
CardSavrResponse<List<Card>> list = await http.getCardsAsync(null, paging);
```

```shell
curl "https://api.INSTANCE.cardsavr.io/cardsavr_cards/123" 
  -H "trace: {\"key\": \"NlOFNNlKabi7Fn26CLw==\"}" 
  -H "paging: \"{\"page\": \"1\"}\"" 
  -b ~/_cookies
```

`{'paging': 'JSON-stringified paging object'}`

CardSavr uses paging headers in both requests to and responses from batch GET endpoints. When sent with a batch GET request, a paging header specifies the length, sorting criterion, page number, and order of the data returned. Since each batch GET request can only return one page of data at a time, paging headers give users more control over the data they receive back.

If no paging header is submitted with the request, default values are applied (see table).

**Note**: CardSavr sends a paging header with each batch GET response to provide details about the page returned.

In the example header at right sent to '/cardsavr_cards', the second page of 25 results would be returned, sorted in descending order by PAR.

### Parameters
The paging header takes a JSON stringified object with the following properties. If a paging header is not included, the page of results will use the default values. Results are returned as an array.

Property name | Type | Description | Default value
------------- | -----| ----------- | -------------
page | integer | The page to be returned | 1
page_length | integer | Length of each page | 25
sort* | string | Property to sort results by | "id"
descending | boolean | If true, sorts results in descending order; if false, sorts in ascending order | false

*Check GET endpoint documentation to see which properties are sort-able

const updated_body = { id: 1, cardholder_safe_key : new_cardholder_safe_key };
const res = await my_session.updateUser(1, updated_body, new_cardholder_safe_key, cardholder_safe_key);


## Safe key

> safe keys are included to save data to the users' safe - if Strivve is storing the safe key, safe keys do not be inlcuded as a request header. If a customer uses a remote safe key store, it must be included with all safe managed properties (accounts, jobs, and cards), and it is the customer's responsibility to rotate them.  If a user is going to persist for a significant length of time (longer than a one and done job), then it is advised to use a thrid party safe key store.

```javascript
const updated_body = { id: 1, cardholder_safe_key : new_cardholder_safe_key };
const res = await my_session.updateUser(1, updated_body, new_cardholder_safe_key, cardholder_safe_key);
```

```csharp
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
AddNewSafeKeyHeader(headers, newSafeKey);
AddSafeKeyHeader(headers, safeKey);

PropertyBag bag = new PropertyBag();
bag["id"] = 1;
bag["cardholder_safe_key"] = newSafeKey;
await http.UpdateUserAsync(bag.GetString("id"), bag, null, headers); //no paging
```

```shell
curl "https://api.INSTANCE.cardsavr.io/cardsavr_users/1" 
  -X PUT
  -H "trace: {\"key\": \"NlOFNNlKabi7Fn26CLw==\"}" 
  -H "new-cardholder-safe-key: +h+W0c9EsgvFLufWnu87iV6ErDF7dpyT5YUEbb/oOIw=}" 
  -H "cardholder-safe-key: rttYqkGPHLk2KeK6OD8612gSurKXu0X8W6BTWF3hhGM=}" 
  -B "{ \"id\": 1 }" 
  -b ~/_cookies
```

`{'cardholder-safe-key': 'rttYqkGPHLk2KeK6OD8612gSurKXu0X8W6BTWF3hhGM='}`
`{'new-cardholder-safe-key': '+h+W0c9EsgvFLufWnu87iV6ErDF7dpyT5YUEbb/oOIw='}`

You must send an encrypted cardholder safe key header for each request that involves safe-protected information. Saving users (/cardsavr_users), accounts (/cardsavr_accounts) and cards (/cardsavr_cards) require the key to write encrypted data for PANs, CVVs, merchant usernames and merchant site passwords to the server side safe.  Safe keys can be stored by the third party by including the 'cardholder-safe-key' header when creating a user, or they can optionally be stored by Strivve within Cardsavr by not including a 'cardholder-safe-key]' header when creating a user. Individual endpoint documentation will indicate if a safe key header is required.

For third party managed safe keys, when rotating a safe key, you must provide both an encrypted 'cardholder-safe-key' header and an encrypted 'new-cardholder-safe-key' header on a user update.

See the [link] cardholder safe key section for more information on generating and using safe keys.

# API Usage 

Query parameter filters can be used with GET requests that do not have an ID path parameter (i.e. '/cardsavr_cards' but not '/cardsavr_cards/123'). When using a query filter, you must place a '?' after the endpoint (preceding the first query filter). Mutiple query filters must be separated by an '&'. There are six filter types in CardSavr:

## GET Filters

> Filters can be aggregated together to apply multiple filters

```javascript
const merchants = await session.getMerchants({ top_hosts : "amazon.com,apple.com", exclude_hosts : "walmart.com" });
```

```csharp
CardSavrResponse<List<MerchantSite>> merchants = await http.GetMerchantSitesAsync(
    new NameValueCollection() {
        { "top_hosts", "amazon.com,apple.com"}, {"exclude_hosts", "walmart.com" }
    }
);
```

```shell
curl "https://api.INSTANCE.cardsavr.io/cardsavr_users?top_hosts=amazon.com,apple.com&exclude_hosts=walmart.com" 
  -H "trace: {\"key\": \"NlOFNNlKabi7Fn26CLw==\"}" 
  -b ~/_cookies
```

### Singular filters

**Singular filters** select for results with one specific value. If the property has a unique constraint (e.g. "username" for '/cardsavr_users'), the singular filter can only select one object.

For string properties, singular filters always use **partial** matching, meaning they will match any string that contains the filter value as a substring.

### Multiple filters

**Multiple filters** select for any object containing one of the specified values for a property. Multiple values must be separated by commas and no spaces. A single value can be submitted for multiple filter, as well.

Multiple filters for string properties always use **partial** matching, meaning they will match any string that contains the filter value as a substring.

<aside class="notice">
"/cardsavr_accounts?cardholder_ids=1,2,3" would return accounts associated with the cardholders that have the IDs 1, 2, and 3.
</aside>

### Starts-with filters

**Starts-with** filters select all objects where the property value begins with the provided query value.

<aside class="notice">
"/merchant_sites?name_starts_with=a" returns all sites with names beginning with A (e.g. names of "Apple", "Amazon", "Atlantis").
</aside>

### Top filters

**Top filters** select for objects with specified properties to be returned first, in the order specified.

<aside class="notice">
"/merchant_sites?top_ids=2,4,6" would return an array with sites with IDs 2,4,6 in the 1st, 2nd, and 3rd index positions, respectively, with any additional matching objects returned after.
</aside>

### Include/exclude filters

**Include filters** select for any objects that have the specified property value. Unlike multiple filters, include filters use exact matching.

<aside class="notice">
"/cardsavr_users?roles_include=developer,analysts" returns users with roles of developer and analyst.
"/cardsavr_users?roles_include=dev,ana" would return no users, as "dev" and "ana" are not roles defined in CardSavr.
</aside>

**Exclude filters** select for any objects that do NOT have the specified property value.  Exclude filters use exact matching.

<aside class="notice">
"/cardsavr_users?roles_exclude=cardholder,admin" filters out users with the roles cardholder and admin.
</aside>

### Min/Max filters

**Max filters** select for objects that have a value equal to or less than the specified value.

<aside class="notice">
"/cardsavr_accounts?created_on_max=2018-04-20T23:10:36.657Z" returns accounts that were created on or before the date string 2018-04-20T23:10:36.657Z.
</aside>

**Min filters** select for any objects that have a value equal to or greater than the specified value.

<aside class="notice">
'/cardsavr_accounts?created_on_min=2018-04-20T23:10:36.657Z' returns accounts that were created on or after the date string 2018-04-20T23:10:36.657Z.
</aside>

## Cascading DELETE

> Deleting user 123 will delete their corresponding jobs, cards, and addresses.  Their job results will remain.

```javascript
await session.deleteUser(123); 
```

```csharp
await http.DeleteUserAsync(123);
```

```shell
curl "https://api.INSTANCE.cardsavr.io/cardsavr_users" 
  -X DELETE
  -H "trace: {\"key\": \"NlOFNNlKabi7Fn26CLw==\"}" 
  -B "{ \"id\": 123 }" 
  -b ~/_cookies
```

A successful DELETE request will also delete any object that references the deleted object. The additional object types that will be deleted for a particular DELETE endpoint are listed in the individual endpoint documentation.

For example, a successful DELETE request to '/cardsavr_accounts/123' would also delete any single-site jobs that reference the account with ID 123, as single-site jobs contain a foreign key reference to an account.

