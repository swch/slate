
# Accounts
Account objects contain the account information, such as username and password, for a particular cardhoder. They are used to log in to a cardholder's account for placing a payment card.
## Get account

```javascript
const accounts = await session.getAccounts(266084664,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","merchant_site","cardsavr_card"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["cardholder","merchant_site","cardsavr_card"])}
JsonArray response = (JsonArray)session.get(266084664, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 266084664,
  "last_password_update": "2002-03-18T08:08:08.234Z",
  "last_saved_card": "1999-05-26T17:59:13.323Z",
  "created_on": "1982-05-15T23:17:19.320Z",
  "last_updated_on": "2020-04-02T02:59:11.166Z",
  "cardholder": {
    "id": 1256512418,
    "type": "persistent_nocreds",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "wNHNeY",
    "webhook_url": "https://mywebhooks.com/this",
    "custom_data": {
      "CljkumxDCBge": "v1nc",
      "FYNGVlCgSbYg": 4,
      "TNjDyLfUugUU": false
    },
    "created_on": "2008-08-27T17:55:46.845Z",
    "last_updated_on": "1993-02-08T13:59:02.783Z",
    "cuid": "ZQcVzxSJjkIdr"
  },
  "merchant_site": {
    "id": 1059870448,
    "name": "Amazon",
    "note": "riwZKUExvTEZtpiOPJGXGKbhT",
    "host": "amazon.com",
    "tags": [
      "UU6[yYiwfvE-{3x8-p~[BdJsMtb%2GQ",
      13,
      "WS8B-lX~}^,vVDIara[=hujhn2r0lA"
    ],
    "interface_type": "vbs",
    "job_type": "CARD_PLACEMENT",
    "required_form_fields": [
      "email",
      "phone_number",
      "card_data",
      "cvv",
      "billing_address",
      "postal_code"
    ],
    "images": [
      {
        "url": "https://d1t7g1oas7m24a.cloudfront.net/tiles/dollarshaveclub.com?width=128&version=21f917315911eec1b1705bc7784ce861579cff2b",
        "width": 128,
        "grayscale": false
      },
      {
        "url": "https://d1t7g1oas7m24a.cloudfront.net/tiles/dollarshaveclub.com?width=32&version=21f917315911eec1b1705bc7784ce861579cff2b",
        "width": 32,
        "grayscale": false
      }
    ],
    "account_link": [
      {
        "key_name": "username",
        "label": "Username",
        "type": "initial_account_link"
      },
      {
        "key_name": "password",
        "label": "Password",
        "type": "initial_account_link",
        "secret": true
      },
      {
        "key_name": "otp",
        "label": "One Time Passcode",
        "type": ""
      }
    ],
    "messages": {
      "mfa_label": "Additional information required, this code may be sent to your phone or email address.",
      "additional_info_message": "",
      "auth_message": "Linking account."
    },
    "script_directory": "zjQKIBnOZPKidtEIqpUS",
    "record_final_site_artifacts": true,
    "puppeteer_screenshot": true,
    "login_page": "https://www.merchantsite.com/login",
    "forgot_password_page": "https://www.merchantsite.com/forgot_password",
    "credit_card_page": "https://www.merchantsite.com/credit_card",
    "wallet_page": "L",
    "merchant_sso_group": "TyWGYRtyN",
    "tier": 1524940817,
    "cookie_caching_scheme": "pre-authentication",
    "dynamic_viewport": true,
    "use_puppeteer": false
  },
  "cardsavr_card": {
    "id": 459823259,
    "type": "Mastercard",
    "expiration_month": 12,
    "expiration_year": 24,
    "name_on_card": "Jane Smith",
    "nickname": "Jane's VISA",
    "custom_data": {
      "ZccbMTevREtD": "P^nY3OZx0e(*u",
      "fEUOVhnMECfl": 59,
      "dWllTukvaCqM": true
    },
    "created_on": "2014-07-31T06:25:55.099Z",
    "last_updated_on": "2018-01-06T15:13:44.537Z",
    "par": "VMDEyxNytZlYmPCcHQGvpvxodytqN",
    "customer_key": "xAXHoEnnCyGXassGJfiXqY"
  },
  "customer_key": "gCguiOAUaUKbXqX"
}
```

### Path

GET /cardsavr_accounts **(batch)** or GET /cardsavr_accounts/:id **(singular)**

### Description

Returns the account specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable accounts, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- cardholder_ids
- merchant_site_ids
- customer_key
- last_card_placed_ids
- last_password_update_min / last_password_update_max
- last_saved_card_min / last_saved_card_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/cardsavr_accounts?ids=1,2`

#### Singular GET requests

**Singular requests** only return the account matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_accounts/266084664`

### <a name="response-cardsavr_account"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this account.
last_card_placed_id | number (fk) [cards](#cards) | ID of the last card placed on this account by the Virtual Browser System (VBS).
last_password_update | date | 
last_saved_card | date | Date of last card saved on this account.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) [cardholders](#cardholders) | ID of the cardholder associated with this account.
merchant_site_id | number (fk) [merchant sites](#merchant-sites) | ID of the merchant site associated with this account.
customer_key | string | An external reference to a merchant site for a specific cardholder.  A key of merchant host and cuid will be used if none provided. The default can potentially violate a constraint with two accounts of the same merchant site.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create account

```javascript
const account = await session.createAccount({
  "cardholder_id": 908894426,
  "merchant_site_id": 1248830464,
  "customer_key": "gCguiOAUaUKbXqX",
  "last_card_placed_id": 1263765051,
  "account_link": {
    "username": "jsmith123",
    "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 908894426 },
	{ "merchant_site_id", 1248830464 },
	{ "customer_key", "gCguiOAUaUKbXqX" },
	{ "last_card_placed_id", 1263765051 }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 908894426 )
	.add("merchant_site_id", 1248830464 )
	.add("customer_key", "gCguiOAUaUKbXqX" )
	.add("last_card_placed_id", 1263765051 )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":908894426,\"merchant_site_id\":1248830464,\"customer_key\":\"gCguiOAUaUKbXqX\",\"last_card_placed_id\":1263765051,\"account_link\":{\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/
```

### Path

POST /cardsavr_accounts

### Description

Create a account and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.



<aside class="notice"><a href=#request-hydration-on-post>Request hydration</a> can be used on this endpoint. This allows you to create a new account and all referential entities in a single POST request.
</aside>

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cardholder_id | number | yes | ID of the cardholder associated with this account.
merchant_site_id | number | yes | ID of the merchant site associated with this account.
customer_key | string | yes | An external reference to a merchant site for a specific cardholder.  A key of merchant host and cuid will be used if none provided. The default can potentially violate a constraint with two accounts of the same merchant site.
last_card_placed_id | number | no | ID of the last card placed on this account by the Virtual Browser System (VBS).
account_link | object | no | One or more properties with key:value pairs that are required for authenticated a user.  These properties are either included as part of initial account collection, or they are requested as part of a credential_request.  An error will be returned if all properties are not provided for a given credential_request. The set of key:value pairs for a site are specified in the merchant site info returned from GET /merchant_sites as 'account_link'.  If credentials are being saved as part of a credential_response, the corresponding envelope_id must be supplied as a header.

See [account response attributes](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the account_link when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Upsert account

```javascript
const account = await session.updateAccount(1,{
  "last_card_placed_id": 682904579,
  "account_link": {
    "username": "jsmith123",
    "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
  }
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 682904579 }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 682904579 )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":682904579,\"account_link\":{\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/266084664
```

### Path

PUT /cardsavr_accounts OR /cardsavr_accounts/{id}

### Description

Upsert can be used to either update a account, create a new account, or return an existing account.  Either an id or customer_key is required for upsert. The id (in path or body), along with an updated body, can be used to update an existing account; the customer_key (in body) can likewise be used to update a account, and can also be used to create a new account, if the customer_key does not match any existing accounts. If the id or customer_key provided corresponds to a pre-existing account and no updated information has been included in the body, the existing account will be returned.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
last_card_placed_id | number | ID of the last card placed on this account by the Virtual Browser System (VBS).
account_link | object | One or more properties with key:value pairs that are required for authenticated a user.  These properties are either included as part of initial account collection, or they are requested as part of a credential_request.  An error will be returned if all properties are not provided for a given credential_request. The set of key:value pairs for a site are specified in the merchant site info returned from GET /merchant_sites as 'account_link'.  If credentials are being saved as part of a credential_response, the corresponding envelope_id must be supplied as a header.

See [account response parameters](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the account_link when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete account

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/266084664
```

```javascript
await session.deleteAccount(undefined);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(undefined);
```

```java
JsonValue account = session.delete("/cardsavr_accounts", undefined, null);
```

### Path

DELETE /cardsavr_accounts/{id}

### Description

Delete a account and purge its [related items](#cascading-delete).  An id is required on every delete request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [account response parameters](#response-cardsavr_account).


# Addresses
Address objects contain the billing address for a specific cardholder, and are used to populate billing address information on merchant sites. They are linked to cards and cardholders.
## Get address

```javascript
const addresses = await session.getAddresses(1491699994,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["cardholder"])}
JsonArray response = (JsonArray)session.get(1491699994, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1491699994,
  "address1": "ypEQiDFPsxFmRYIbCYSuEtVsLkpcMBotnLlTqlIAPFmJiBlTBXXLxbyKoMxPMYBASMCMVISQZqYyoWAaxXDiECkYXqWgyTDljIb",
  "address2": "rrflIhFdmMaXSaEbFCIUuNkpXPsyUpsErNKizjqFRdTIwNraWaFOQAQXJywqWfRhpkICIVFznvAUBwQmcXVhXvhHAqVNMcFPMdx",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "XjYggQTDsQzb@XhujRV.hIB",
  "phone_number": "2065555555",
  "created_on": "2021-08-24T04:39:22.973Z",
  "last_updated_on": "2010-06-25T07:14:55.880Z",
  "cardholder": {
    "id": 425796635,
    "type": "persistent_creds",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "khModUQpsyT",
    "webhook_url": "https://mywebhooks.com/this",
    "custom_data": {
      "bZtMPDVgJfSz": "bh#VWu!3RBCJlQAE[*0iJ[qI",
      "ttsqzLeqTiFi": 64,
      "NRTsqhRYODOE": false
    },
    "created_on": "2013-06-28T22:27:25.769Z",
    "last_updated_on": "1992-08-04T11:01:03.145Z",
    "cuid": "vyz"
  }
}
```

### Path

GET /cardsavr_addresses **(batch)** or GET /cardsavr_addresses/:id **(singular)**

### Description

Returns the address specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable addresses, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- cardholder_ids
- is_primary
- first_name
- last_name
- email
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/cardsavr_addresses?ids=1,2`

#### Singular GET requests

**Singular requests** only return the address matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_addresses/1491699994`

### <a name="response-cardsavr_address"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this address.
address1 | string | 
address2 | string | Second line of address, if one exists (e.g. apartment number).
city | string | 
subnational | string | Subnational unit (i.e. state or province).
postal_code | string | 
postal_other | string | E.g. last four digits in a zip-plus-four.
country | string | 
is_primary | boolean | Indicates if this is the primary address of this cardholder, as a cardholder can be linked to multiple addresses.
first_name | string | 
last_name | string | 
email | string | 
phone_number | string | 
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) [cardholders](#cardholders) | ID of the cardholder associated with this address.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create address

```javascript
const address = await session.createAddress({
  "cardholder_id": 157855181,
  "address1": "ypEQiDFPsxFmRYIbCYSuEtVsLkpcMBotnLlTqlIAPFmJiBlTBXXLxbyKoMxPMYBASMCMVISQZqYyoWAaxXDiECkYXqWgyTDljIb",
  "address2": "rrflIhFdmMaXSaEbFCIUuNkpXPsyUpsErNKizjqFRdTIwNraWaFOQAQXJywqWfRhpkICIVFznvAUBwQmcXVhXvhHAqVNMcFPMdx",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "XjYggQTDsQzb@XhujRV.hIB",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 157855181 },
	{ "address1", "ypEQiDFPsxFmRYIbCYSuEtVsLkpcMBotnLlTqlIAPFmJiBlTBXXLxbyKoMxPMYBASMCMVISQZqYyoWAaxXDiECkYXqWgyTDljIb" },
	{ "address2", "rrflIhFdmMaXSaEbFCIUuNkpXPsyUpsErNKizjqFRdTIwNraWaFOQAQXJywqWfRhpkICIVFznvAUBwQmcXVhXvhHAqVNMcFPMdx" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "XjYggQTDsQzb@XhujRV.hIB" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 157855181 )
	.add("address1", "ypEQiDFPsxFmRYIbCYSuEtVsLkpcMBotnLlTqlIAPFmJiBlTBXXLxbyKoMxPMYBASMCMVISQZqYyoWAaxXDiECkYXqWgyTDljIb" )
	.add("address2", "rrflIhFdmMaXSaEbFCIUuNkpXPsyUpsErNKizjqFRdTIwNraWaFOQAQXJywqWfRhpkICIVFznvAUBwQmcXVhXvhHAqVNMcFPMdx" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "XjYggQTDsQzb@XhujRV.hIB" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":157855181,\"address1\":\"ypEQiDFPsxFmRYIbCYSuEtVsLkpcMBotnLlTqlIAPFmJiBlTBXXLxbyKoMxPMYBASMCMVISQZqYyoWAaxXDiECkYXqWgyTDljIb\",\"address2\":\"rrflIhFdmMaXSaEbFCIUuNkpXPsyUpsErNKizjqFRdTIwNraWaFOQAQXJywqWfRhpkICIVFznvAUBwQmcXVhXvhHAqVNMcFPMdx\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"XjYggQTDsQzb@XhujRV.hIB\",\"phone_number\":\"2065555555\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/
```

### Path

POST /cardsavr_addresses

### Description

Create a address and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.



<aside class="notice"><a href=#request-hydration-on-post>Request hydration</a> can be used on this endpoint. This allows you to create an new address and all referential entities in a single POST request.
</aside>

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cardholder_id | number | yes | ID of the cardholder associated with this address.
address1 | string | yes | 
address2 | string | no | Second line of address, if one exists (e.g. apartment number).
city | string | yes | 
subnational | string | yes | Subnational unit (i.e. state or province).
postal_code | string | yes | 
postal_other | string | no | E.g. last four digits in a zip-plus-four.
country | [string enum](#post-cardsavr_address-1)* | no | 
is_primary | boolean | yes | Indicates if this is the primary address of this cardholder, as a cardholder can be linked to multiple addresses.
first_name | string | no | 
last_name | string | no | 
email | string | no | 
phone_number | string | no | 

See [address response attributes](#response-cardsavr_address).

#### <a name="post-cardsavr_address-1"></a>string enum*
- usa
- USA
- us
- US
- canada
- Canada
- ca
- CA


## Update address

```javascript
const address = await session.updateAddress(1,{
  "address1": "FpaDaJiKWkUetRBsmtkNqEBkdZyCDbGAwiRYILePbfxqOYwCSUbjimmeMMgbptHhBHEmGvlgQuTdbCcjzexWjWvMPtYjygCzllg",
  "address2": "RYTgyXEULYCxjlHGEbAmPyIdmYVRRKOZjPpzHAlcqKQMhsZXkEuMuWWuXTUBOFXwQsyUspxRGfjxZJFNFNuygwdznZrZjSiFvNn",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "QAqFByEIxBmo@WAxRCi.ipo",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "FpaDaJiKWkUetRBsmtkNqEBkdZyCDbGAwiRYILePbfxqOYwCSUbjimmeMMgbptHhBHEmGvlgQuTdbCcjzexWjWvMPtYjygCzllg" },
	{ "address2", "RYTgyXEULYCxjlHGEbAmPyIdmYVRRKOZjPpzHAlcqKQMhsZXkEuMuWWuXTUBOFXwQsyUspxRGfjxZJFNFNuygwdznZrZjSiFvNn" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "QAqFByEIxBmo@WAxRCi.ipo" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "FpaDaJiKWkUetRBsmtkNqEBkdZyCDbGAwiRYILePbfxqOYwCSUbjimmeMMgbptHhBHEmGvlgQuTdbCcjzexWjWvMPtYjygCzllg" )
	.add("address2", "RYTgyXEULYCxjlHGEbAmPyIdmYVRRKOZjPpzHAlcqKQMhsZXkEuMuWWuXTUBOFXwQsyUspxRGfjxZJFNFNuygwdznZrZjSiFvNn" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "QAqFByEIxBmo@WAxRCi.ipo" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"FpaDaJiKWkUetRBsmtkNqEBkdZyCDbGAwiRYILePbfxqOYwCSUbjimmeMMgbptHhBHEmGvlgQuTdbCcjzexWjWvMPtYjygCzllg\",\"address2\":\"RYTgyXEULYCxjlHGEbAmPyIdmYVRRKOZjPpzHAlcqKQMhsZXkEuMuWWuXTUBOFXwQsyUspxRGfjxZJFNFNuygwdznZrZjSiFvNn\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"QAqFByEIxBmo@WAxRCi.ipo\",\"phone_number\":\"2065555555\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1491699994
```

### Path

PUT /cardsavr_addresses OR /cardsavr_addresses/{id}

### Description

Update a address and return the updated object.  An id is required on every update request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
address1 | string | 
address2 | string | Second line of address, if one exists (e.g. apartment number).
city | string | 
subnational | string | Subnational unit (i.e. state or province).
postal_code | string | 
postal_other | string | E.g. last four digits in a zip-plus-four.
country | [string enum](#post-cardsavr_address-1)* | 
is_primary | boolean | Indicates if this is the primary address of this cardholder, as a cardholder can be linked to multiple addresses.
first_name | string | 
last_name | string | 
email | string | 
phone_number | string | 

See [address response parameters](#response-cardsavr_address).


## Delete address

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1491699994
```

```javascript
await session.deleteAddress(undefined);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(undefined);
```

```java
JsonValue address = session.delete("/cardsavr_addresses", undefined, null);
```

### Path

DELETE /cardsavr_addresses/{id}

### Description

Delete a address and purge its [related items](#cascading-delete).  An id is required on every delete request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [address response parameters](#response-cardsavr_address).


# Bins
A Bank Identification Number (BIN) object represents a BIN used by a financial institution in the CardSavr API. They are linked to cards and FIs and used for reporting purposes.
## Get bin

```javascript
const bins = await session.getBins(1397722725,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Bins> bins = await session.GetBinsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["financial_institution"])}
JsonArray response = (JsonArray)session.get(1397722725, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1397722725,
  "custom_data": {
    "jiOoJeVIzUPF": "n./{8{WB{3EpQUC=nEkXuKg+qGf.Bk.@",
    "weTiLsxiaqwR": 40,
    "IEnMdnuWOBOy": true
  },
  "created_on": "1985-12-01T13:42:58.530Z",
  "last_updated_on": "1978-12-25T15:01:31.455Z",
  "financial_institution": {
    "id": 267334305,
    "name": "zRTRtvEPlyqCbEkVaSeiCbJoVEIdFOuTnDoNUGVoTbswhVftZHWwlYVWfbXTZZE",
    "description": "jMtlhrrNKLJEk",
    "lookup_key": "KIpXoEROxciGDQpzHNZTzZTWwcafAgQFcCVZffwmyyOufFdoZDcXHJoEgcZmyUn",
    "alternate_lookup_key": "chJrGjYybDtLKekaznhNdoeChSYVoyMSKSdTaLXaxDBSVookRxxqujIzEBSxcJZ",
    "last_activity": "2003-02-04T08:23:14.446Z",
    "created_on": "2011-02-13T15:54:28.316Z",
    "last_updated_on": "1971-02-08T22:57:36.459Z"
  },
  "bank_identification_number": "34744400"
}
```

### Path

GET /cardsavr_bins **(batch)** or GET /cardsavr_bins/:id **(singular)**

### Description

Returns the bin specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable bins, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- financial_institution_ids
- bank_identification_numbers
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/cardsavr_bins?ids=1,2`

#### Singular GET requests

**Singular requests** only return the bin matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_bins/1397722725`

### <a name="response-cardsavr_bin"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this BIN.
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | ID of financial institution that this Bank Identification Number belongs to.
custom_data | object | Custom data (e.g. brand, type) that can be added according to FI need.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
bank_identification_number | string | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create bin

```javascript
const bin = await session.createBin({
  "financial_institution_id": 412839044,
  "bank_identification_number": "34744400",
  "custom_data": {
    "jiOoJeVIzUPF": "n./{8{WB{3EpQUC=nEkXuKg+qGf.Bk.@",
    "weTiLsxiaqwR": 40,
    "IEnMdnuWOBOy": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 412839044 },
	{ "bank_identification_number", "34744400" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 412839044 )
	.add("bank_identification_number", "34744400" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":412839044,\"bank_identification_number\":\"34744400\",\"custom_data\":{\"jiOoJeVIzUPF\":\"n./{8{WB{3EpQUC=nEkXuKg+qGf.Bk.@\",\"weTiLsxiaqwR\":40,\"IEnMdnuWOBOy\":true}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/
```

### Path

POST /cardsavr_bins

### Description

Create a bin and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
financial_institution_id | number | yes | ID of financial institution that this Bank Identification Number belongs to.
bank_identification_number | string | yes | 
custom_data | object | no | Custom data (e.g. brand, type) that can be added according to FI need.

See [bin response attributes](#response-cardsavr_bin).


## Update bin

```javascript
const bin = await session.updateBin(1,{
  "financial_institution_id": 735777647,
  "custom_data": {
    "OaIhzKERvolW": "T0U%h7r",
    "gecrJTaJEmMS": 40,
    "qlIjtRJaSgVh": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 735777647 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 735777647 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":735777647,\"custom_data\":{\"OaIhzKERvolW\":\"T0U%h7r\",\"gecrJTaJEmMS\":40,\"qlIjtRJaSgVh\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1397722725
```

### Path

PUT /cardsavr_bins OR /cardsavr_bins/{id}

### Description

Update a bin and return the updated object.  An id is required on every update request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
financial_institution_id | number | ID of financial institution that this Bank Identification Number belongs to.
custom_data | object | Custom data (e.g. brand, type) that can be added according to FI need.

See [bin response parameters](#response-cardsavr_bin).


## Delete bin

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1397722725
```

```javascript
await session.deleteBin(undefined);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(undefined);
```

```java
JsonValue bin = session.delete("/cardsavr_bins", undefined, null);
```

### Path

DELETE /cardsavr_bins/{id}

### Description

Delete a bin and purge its [related items](#cascading-delete).  An id is required on every delete request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [bin response parameters](#response-cardsavr_bin).


# Card Placement Results
Card Placement results are a flatted version of the jobs and its publily available meta data. Although sensitive data like the PAN and account creds are not available, all the details of the job are captured here for future reference after the corresponding entities may have been deleted.
## Get card placement result

```javascript
const cardplacementresults = await session.getCardPlacementResults(1947970693,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution","merchant_site","cardsavr_bin"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<CardPlacementResults> cardplacementresults = await session.GetCardPlacementResultsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["financial_institution","merchant_site","cardsavr_bin"])}
JsonArray response = (JsonArray)session.get(1947970693, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1947970693,
  "merchant_site_hostname": "EIYsjGNMvWqHRmHoaZvXBKAGlVVngOkkYkgywkSZoxIRRMZimHLKVGyBepOfIPeCoLozvBpVAViXovprOKAHaCkXibbGYDUYnCQFphAAJtypVOBENIbCIJunfFysJbNmJDaRsJrroMlCPDVQkpbnIfeCkieHZoarNBeupspBCKWOxMzxTbYPYlsVyJqWGDHxJxDSkjarjKRvpAxOlLCxTBhqoscpxHQEzCKEootHvzHwOkXviwKhqHQzzSQHeQ",
  "meta_key": "MB9810411",
  "fi_name": "rMrXTUfOugMwYLQtVBzFSMVOlpUTXAEkVTYmqbJOXgTwyqpUuaLmDvFLhUCCtje",
  "bank_identification_number": "67042473",
  "cuid": "ilFRgdcmGXBnLY",
  "par": "eEMMMkxkMkwkPwIUDqYICjjkNPKPZ",
  "card_customer_key": "XMqklDgKdYYzuEifXhMbvpYe",
  "account_customer_key": "REqVZuJ",
  "status": "SUCCESSFUL",
  "status_message": "Successful",
  "termination_type": "BILLABLE",
  "custom_data": {
    "gSZCOzAPDTWs": ")88jQ,BPUOA",
    "fZthtENujrvN": 35,
    "bTiDzFzVdYcF": true
  },
  "time_elapsed": 339906507,
  "first_6": "yhqaxkJpwIzZIsKcheUIkRwYhXLgJrwf",
  "first_7": "McUqaGqHkUWUiIHafxNdsVhKCJCChGvZ",
  "first_8": "ArtwLqVcyNolueETTCqhfBYsgWbpkhIt",
  "trace": "YHrXjmzkfhq",
  "agent_session_id": "eqsrXpnqAEdDmzFvkZQIe",
  "email_sent": false,
  "account_linked_on": "1997-01-20T17:55:47.347Z",
  "job_ready_on": "1975-02-23T01:36:52.653Z",
  "job_created_on": "1998-10-05T17:32:49.446Z",
  "completed_on": "1979-03-15T22:00:29.287Z",
  "created_on": "1998-07-24T00:01:59.908Z",
  "last_updated_on": "1972-05-08T19:02:02.293Z",
  "financial_institution": {
    "id": 668173149,
    "name": "yYCEVMSEkYjFBnmphKTHsUlFsAEAHOqkxfaeqpfTDTKLrMYnCxftSczjlGAQAHg",
    "description": "UPHSdDWVKDcgdnNujME",
    "lookup_key": "fCIhCkHikYVxWvUZYnolhZYRFVNMileUWeOvefCVHPeNMckETrjlXXaKTcTqoVV",
    "alternate_lookup_key": "WWafuPezYixxiRNhsjvlUMgYbEendbZeoORCJKvJbxHXRbUkoVhlKBgiEfGJwYQ",
    "last_activity": "1978-07-09T20:03:52.696Z",
    "created_on": "1994-11-19T23:28:07.738Z",
    "last_updated_on": "1970-02-07T04:57:24.989Z"
  },
  "merchant_site": {
    "id": 812578964,
    "name": "Amazon",
    "note": "mlCwZPBYOjr",
    "host": "amazon.com",
    "tags": [
      "&vK4{",
      2,
      "j.v3^wh$9NoI,)WJYe#_8tA"
    ],
    "interface_type": "vbs",
    "job_type": "BILL_PAY",
    "required_form_fields": [
      "email",
      "phone_number",
      "card_data",
      "cvv",
      "billing_address",
      "postal_code"
    ],
    "images": [
      {
        "url": "https://d1t7g1oas7m24a.cloudfront.net/tiles/dollarshaveclub.com?width=128&version=21f917315911eec1b1705bc7784ce861579cff2b",
        "width": 128,
        "grayscale": false
      },
      {
        "url": "https://d1t7g1oas7m24a.cloudfront.net/tiles/dollarshaveclub.com?width=32&version=21f917315911eec1b1705bc7784ce861579cff2b",
        "width": 32,
        "grayscale": false
      }
    ],
    "account_link": [
      {
        "key_name": "username",
        "label": "Username",
        "type": "initial_account_link"
      },
      {
        "key_name": "password",
        "label": "Password",
        "type": "initial_account_link",
        "secret": true
      },
      {
        "key_name": "otp",
        "label": "One Time Passcode",
        "type": ""
      }
    ],
    "messages": {
      "mfa_label": "Additional information required, this code may be sent to your phone or email address.",
      "additional_info_message": "",
      "auth_message": "Linking account."
    },
    "script_directory": "iCFstlHvsTMtmQHgzbCKXjPDQrZ",
    "record_final_site_artifacts": false,
    "puppeteer_screenshot": true,
    "login_page": "https://www.merchantsite.com/login",
    "forgot_password_page": "https://www.merchantsite.com/forgot_password",
    "credit_card_page": "https://www.merchantsite.com/credit_card",
    "wallet_page": "WJpZBvjmSyRucdMvRIdzzMEFJo",
    "merchant_sso_group": "WszkadC",
    "tier": 845790445,
    "cookie_caching_scheme": "none",
    "dynamic_viewport": true,
    "use_puppeteer": false
  },
  "cardsavr_bin": {
    "id": 613109741,
    "custom_data": {
      "KkHQspkKgmNV": ".DUtTW1U5Cm}_NO(hT5",
      "IBDixEdtEUyc": 80,
      "CjXKbmZLeHdp": false
    },
    "created_on": "2023-12-19T17:36:44.229Z",
    "last_updated_on": "2001-02-23T00:27:46.535Z",
    "bank_identification_number": "6821244"
  },
  "place_card_on_single_site_job_id": 18768762
}
```

### Path

GET /card_placement_results **(batch)** or GET /card_placement_results/:id **(singular)**

### Description

Returns the card placement result specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable card placement results, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- merchant_site_hostnames
- merchant_site_hostname
- meta_key
- fi_name
- bank_identification_numbers
- cuids
- pars
- card_customer_keys
- account_customer_keys
- statuses
- status
- termination_type
- termination_types_include / termination_types_exclude
- first_6
- first_7
- first_8
- place_card_on_single_site_job_ids
- financial_institution_ids
- merchant_site_ids
- agent_session_id
- email_sent
- account_linked_on_min / account_linked_on_max
- job_ready_on_min / job_ready_on_max
- job_created_on_min / job_created_on_max
- completed_on_min / completed_on_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/card_placement_results?ids=1,2`

#### Singular GET requests

**Singular requests** only return the card placement result matching the id provided in the path.

**Example GET request path:**<br>`/card_placement_results/1947970693`

### <a name="response-card_placement_result"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this card placement result.
merchant_site_hostname | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
fi_name | string | 
bank_identification_number | string | 
cuid | string | External unique ID for cardholder--can be account_id, email address, phone number, etc.  A random number will be gnenerated if not provided.
par | string | 
card_customer_key | string | Unique customer reference for this card. A random number will be generated and returned if not provided
account_customer_key | string | An external reference to a merchant site for a specific cardholder.  A key of merchant host and cuid will be used if none provided. The default can potentially violate a constraint with two accounts of the same merchant site.
status | string | Status of job (when it terminated).
status_message | string | Human readable representation of the job's status.
termination_type | string | Final termination status of a job. (BILLABLE, SITE_INTERACTION_FAILURE, USER_DATA_FAILURE, PROCESS FAILURE)
custom_data | object | 
time_elapsed | number | 
first_6 | string | First six digits of card number.
first_7 | string | First seven digits of card number.
first_8 | string | First eight digits of card number.
trace | string | The trace key follows jobs as they are processed from beginning to end.  This helps with debugging the logs.
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | 
merchant_site_id | number (fk) [merchant sites](#merchant-sites) | 
agent_session_id | string | 
email_sent | boolean | 
account_linked_on | date | Timestamp from when the account for this job is linked -- this could use persistent or user provided credentials
job_ready_on | date | Timestamp from when initial credentials have been set on the account for the job.
job_created_on | date | Timestamp from when the job was created.
completed_on | date | 
created_on | date | Date this job result was created on
last_updated_on | date | Date this job result was last updated on
place_card_on_single_site_job_id | number | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

# Cardholder sessions
A record of information associated with the session of a carholder -- it terminates after explicit completion or 15 minutes of inactivity.
## Get cardholder session

```javascript
const cardholdersessions = await session.getCardholderSessions(243495999,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","financial_institution"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<CardholderSessions> cardholdersessions = await session.GetCardholderSessionsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["cardholder","financial_institution"])}
JsonArray response = (JsonArray)session.get(243495999, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 243495999,
  "successful_jobs": 880155574,
  "failed_jobs": 461747565,
  "clickstream": [
    {
      "uyEDhCKJocJU": "+WpkFKFn1Z",
      "MZLNOpLNkMxV": 85,
      "QeDOBdYNldsp": true
    },
    {
      "hYhodOfRBYxg": "tDRpPHG}WEUm.p{1ZxQ{,_",
      "rCFpGFwSqCcY": 1,
      "zoVHcDtLfbCP": false
    },
    {
      "NNDqmWcBgxSF": "z!!(~7_(=qgr^ZQ",
      "LJCkMwdPOuBG": 32,
      "lYkyOvDDTjqK": true
    }
  ],
  "closed_on": "1983-10-07T23:13:26.298Z",
  "custom_data": {
    "gAWaHBAzheEj": "v$Xjm_M[Ix_/^=A4.9Q",
    "lzBnSDnpJdYu": 56,
    "WbEmamPZgJrp": false
  },
  "created_on": "2017-07-04T15:53:21.457Z",
  "last_updated_on": "2023-03-08T01:06:37.050Z",
  "cardholder": {
    "id": 677820644,
    "type": "persistent_nocreds",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "WKsQVbgVN",
    "webhook_url": "https://mywebhooks.com/this",
    "custom_data": {
      "kjrfJrTmYZzK": "I)y-t/b1J[pTUM#,",
      "rqkenJrCnGJH": 66,
      "ZqkzFQeXhzIo": false
    },
    "created_on": "1970-03-31T02:21:57.690Z",
    "last_updated_on": "1994-12-24T15:01:39.315Z",
    "cuid": "pPBGTpqyjzJcHsKSsZI"
  },
  "financial_institution": {
    "id": 489234121,
    "name": "DrxksIiDOZsWXsuPrcDZjAlhWsZHCzMcsyMcYKQnrCEqUdvTgiTmWlmYNtgxDUt",
    "description": "gHjxZUMLRLdGPPMil",
    "lookup_key": "kzhPImWPZCrMnTyuUODYGUlpPKeDlUdbGbQLYsAQgFfWJOzqVBQoHTBBzdFenuW",
    "alternate_lookup_key": "AuRddWluqSBSraTCakbNmLoeaAnryDZwNQwxmESMIjJJipmWLTsGwQoPNAdmSRW",
    "last_activity": "1973-08-04T03:16:58.206Z",
    "created_on": "1986-07-16T05:29:06.944Z",
    "last_updated_on": "1991-09-05T14:18:16.416Z"
  },
  "cuid": "IHwdTsuL"
}
```

### Path

GET /cardholder_sessions **(batch)** or GET /cardholder_sessions/:id **(singular)**

### Description

Returns the cardholder session specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable cardholder sessions, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- cuid
- cardholder_id
- financial_institution_id
- closed_on_min / closed_on_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/cardholder_sessions?ids=1,2`

#### Singular GET requests

**Singular requests** only return the cardholder session matching the id provided in the path.

**Example GET request path:**<br>`/cardholder_sessions/243495999`

### <a name="response-cardholder_session"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this card placement result.
successful_jobs | number | 
failed_jobs | number | 
cardholder_id | number (fk) [cardholders](#cardholders) | 
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | 
clickstream | array | Click stream events and their corresponding timestamps
closed_on | date | Timestamp at which this cardholder session was closed
custom_data | object | Additional data that can be added to the cardholder if needed.
created_on | date | Date this job result was created on
last_updated_on | date | Date this job result was last updated on
cuid | string | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).


## Upsert cardholder session

```javascript
const cardholdersession = await session.updateCardholderSession(1,{
  "successful_jobs": 1170130296,
  "failed_jobs": 189466969,
  "clickstream": [
    {
      "chYEgWePeVzn": "]]9u4BjyBM",
      "qJmOiNcXKKdL": 11,
      "CwUJloUviJge": true
    },
    {
      "mdPXWmvdEyUL": "CN78vA$T_}A37@qV2wuo9uCLSV",
      "UcknuLAadkNc": 73,
      "SAdyVDHDQlUy": false
    },
    {
      "FtIkrvedOYji": "n1Et#Jv$HZT_",
      "dWXnlkODZNnK": 30,
      "XpeLCGFIJDgM": true
    }
  ]
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "successful_jobs", 1170130296 },
	{ "failed_jobs", 189466969 }
};

CardSavrResponse<CardholderSession> cardholdersession = await http.UpdateCardholderSessionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("successful_jobs", 1170130296 )
	.add("failed_jobs", 189466969 )
	.build();
JsonValue cardholdersession = session.put("/cardholder_sessions", body, null, null);
```

```shell
curl -d "{\"successful_jobs\":1170130296,\"failed_jobs\":189466969,\"clickstream\":[{\"chYEgWePeVzn\":\"]]9u4BjyBM\",\"qJmOiNcXKKdL\":11,\"CwUJloUviJge\":true},{\"mdPXWmvdEyUL\":\"CN78vA$T_}A37@qV2wuo9uCLSV\",\"UcknuLAadkNc\":73,\"SAdyVDHDQlUy\":false},{\"FtIkrvedOYji\":\"n1Et#Jv$HZT_\",\"dWXnlkODZNnK\":30,\"XpeLCGFIJDgM\":true}]}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholder_sessions/243495999
```

### Path

PUT /cardholder_sessions OR /cardholder_sessions/{id}

### Description

Upsert can be used to either update a cardholder session, create a new cardholder session, or return an existing cardholder session.  Either an id or customer_key is required for upsert. The id (in path or body), along with an updated body, can be used to update an existing cardholder session; the customer_key (in body) can likewise be used to update a cardholder session, and can also be used to create a new cardholder session, if the customer_key does not match any existing cardholder sessions. If the id or customer_key provided corresponds to a pre-existing cardholder session and no updated information has been included in the body, the existing cardholder session will be returned.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
successful_jobs | number | 
failed_jobs | number | 
clickstream | array | Click stream events and their corresponding timestamps

See [cardholder session response parameters](#response-cardholder_session).

# Cards
A card object contains information about a payment card for a specific cardholder. Card objects are used to populate payment information on merchant sites.
## Get card

```javascript
const cards = await session.getCards(367162066,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_address","cardsavr_bin"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Cards> cards = await session.GetCardsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_address","cardsavr_bin"])}
JsonArray response = (JsonArray)session.get(367162066, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 367162066,
  "type": "Mastercard",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "RuhBBJrWafpz": "rX#rW!GB8",
    "pyErFMiIpgKn": 96,
    "YcJFUHCHxyHT": false
  },
  "created_on": "1985-12-19T18:55:30.820Z",
  "last_updated_on": "2024-04-25T23:15:50.467Z",
  "cardholder": {
    "id": 279093433,
    "type": "persistent_nocreds",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "UKMAPrwGxqAWoKaZYDRJuYWM",
    "webhook_url": "https://mywebhooks.com/this",
    "custom_data": {
      "dIykSyMWlHDk": "V)P+3Y6r)[",
      "fMKURMdQgasK": 65,
      "elJlxczNmpxv": false
    },
    "created_on": "2005-01-23T09:32:59.321Z",
    "last_updated_on": "2004-12-26T14:40:21.292Z",
    "cuid": "TOGONYZkpsnMLlTFgUVbsYcXOZDsD"
  },
  "cardsavr_address": {
    "id": 1051375920,
    "address1": "BgDQfXDkSvZJsDEPeZuVHUFJcTmrACAmSeumkflNUZuHpvxcczHIJoKgKhRNQzJuiwybjeanzXIKzoFCPAGFZPuFFhZUWuDgTpm",
    "address2": "QaGOTgysRoDeHjDxUzAcFxDWTEvjybiwulHyxowTrDwQNVDEPjGJRUHrNPkUIlowHGvZmAuHUChBzqYyfkRveJJaNnItHFEixug",
    "city": "Seattle",
    "subnational": "WA",
    "postal_code": "98177",
    "postal_other": "98177-0124",
    "country": "USA",
    "is_primary": true,
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "kRKIYqxCtVpp@bLSAOD.sfN",
    "phone_number": "2065555555",
    "created_on": "1984-04-19T09:01:10.810Z",
    "last_updated_on": "2021-06-01T15:32:38.787Z"
  },
  "cardsavr_bin": {
    "id": 402685629,
    "custom_data": {
      "aqZGilDssVkx": "n%Q*_0-G3MgRyksqe1CY%XTyO{W",
      "sMViEdNVbhST": 78,
      "sYMclrTlPYcq": false
    },
    "created_on": "2008-10-12T16:05:29.869Z",
    "last_updated_on": "1987-12-18T11:25:32.284Z",
    "bank_identification_number": "66211757"
  },
  "par": "wcjrormelZptYiACKQVweWTXNysCJ",
  "customer_key": "zWAHD"
}
```

### Path

GET /cardsavr_cards **(batch)** or GET /cardsavr_cards/:id **(singular)**

### Description

Returns the card specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable cards, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- cardholder_ids
- address_ids
- bin_ids
- pars
- customer_keys
- types
- type
- nickname
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/cardsavr_cards?ids=1,2`

#### Singular GET requests

**Singular requests** only return the card matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_cards/367162066`

### <a name="response-cardsavr_card"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this card.
address_id | number (fk) [addresses](#addresses) | ID of address associated with this card.
bin_id | number (fk) [bins](#bins) | ID of BIN associated with this card.
type | string | Type of card (e.g. Visa), automatically filled in by CardSavr.
expiration_month | string | 
expiration_year | string | 
name_on_card | string | 
nickname | string | 
custom_data | object | Meta-data that can be added to the card if needed.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) [cardholders](#cardholders) | ID of cardholder associated with this card.
par | string | Unique Personal Account Reference number for this card, to be used for card lookup. Generated automatically from PAN, expiration date, and username if using the SDK.
customer_key | string | Unique customer reference for this card. A random number will be generated and returned if not provided

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create card

```javascript
const card = await session.createCard({
  "cardholder_id": 893707349,
  "address_id": 421801386,
  "bin_id": 279961730,
  "par": "wcjrormelZptYiACKQVweWTXNysCJ",
  "customer_key": "zWAHD",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "RuhBBJrWafpz": "rX#rW!GB8",
    "pyErFMiIpgKn": 96,
    "YcJFUHCHxyHT": false
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 893707349 },
	{ "address_id", 421801386 },
	{ "bin_id", 279961730 },
	{ "par", "wcjrormelZptYiACKQVweWTXNysCJ" },
	{ "customer_key", "zWAHD" },
	{ "pan", "4111111111111111" },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Jane Smith" },
	{ "nickname", "Jane's VISA" }
};

CardSavrResponse<Card> card = await http.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 893707349 )
	.add("address_id", 421801386 )
	.add("bin_id", 279961730 )
	.add("par", "wcjrormelZptYiACKQVweWTXNysCJ" )
	.add("customer_key", "zWAHD" )
	.add("pan", "4111111111111111" )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Jane Smith" )
	.add("nickname", "Jane's VISA" )
	.build();
JsonValue card = session.post("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":893707349,\"address_id\":421801386,\"bin_id\":279961730,\"par\":\"wcjrormelZptYiACKQVweWTXNysCJ\",\"customer_key\":\"zWAHD\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"Jane's VISA\",\"custom_data\":{\"RuhBBJrWafpz\":\"rX#rW!GB8\",\"pyErFMiIpgKn\":96,\"YcJFUHCHxyHT\":false}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/
```

### Path

POST /cardsavr_cards

### Description

Create a card and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.



<aside class="notice"><a href=#request-hydration-on-post>Request hydration</a> can be used on this endpoint. This allows you to create a new card and all referential entities in a single POST request.
</aside>

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cardholder_id | number | yes | ID of cardholder associated with this card.
address_id | number | no | ID of address associated with this card.
bin_id | number | no | ID of BIN associated with this card.
par | string | no | Unique Personal Account Reference number for this card, to be used for card lookup. Generated automatically from PAN, expiration date, and username if using the SDK.
customer_key | string | yes | Unique customer reference for this card. A random number will be generated and returned if not provided
pan | string | yes | Personal Account Number (PAN) of this card.
cvv | string | no | 
expiration_month | [string enum](#post-cardsavr_card-2)** | yes | 
expiration_year | string | yes | 
name_on_card | string | yes | 
nickname | string | yes | 
custom_data | object | no | Meta-data that can be added to the card if needed.

See [card response attributes](#response-cardsavr_card).

#### <a name="post-cardsavr_card-1"></a>string enum*
- Visa
- Mastercard
- American Express
- Unknown Type

#### <a name="post-cardsavr_card-2"></a>string enum**
- 01
- 02
- 03
- 04
- 05
- 06
- 07
- 08
- 09
- 10
- 11
- 12

<aside class="notice">Update calls to /cardsavr_cards require the cardholder's personal cardholder_safe_key header to encrypt and save the pan and cvv when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Upsert card

```javascript
const card = await session.updateCard(1,{
  "address_id": 2011076689,
  "bin_id": 1224955123,
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "CNaKjYTYmOXo": "=fLp!uv81R%Yhi",
    "EYqYtpTKIcmF": 91,
    "GrBUhfIqNjUt": true
  },
  "pan": "4111111111111111"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address_id", 2011076689 },
	{ "bin_id", 1224955123 },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Jane Smith" },
	{ "nickname", "Jane's VISA" },
	{ "pan", "4111111111111111" }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address_id", 2011076689 )
	.add("bin_id", 1224955123 )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Jane Smith" )
	.add("nickname", "Jane's VISA" )
	.add("pan", "4111111111111111" )
	.build();
JsonValue card = session.put("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"address_id\":2011076689,\"bin_id\":1224955123,\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"Jane's VISA\",\"custom_data\":{\"CNaKjYTYmOXo\":\"=fLp!uv81R%Yhi\",\"EYqYtpTKIcmF\":91,\"GrBUhfIqNjUt\":true},\"pan\":\"4111111111111111\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/367162066
```

### Path

PUT /cardsavr_cards OR /cardsavr_cards/{id}

### Description

Upsert can be used to either update a card, create a new card, or return an existing card.  Either an id or customer_key is required for upsert. The id (in path or body), along with an updated body, can be used to update an existing card; the customer_key (in body) can likewise be used to update a card, and can also be used to create a new card, if the customer_key does not match any existing cards. If the id or customer_key provided corresponds to a pre-existing card and no updated information has been included in the body, the existing card will be returned.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
address_id | number | ID of address associated with this card.
bin_id | number | ID of BIN associated with this card.
cvv | string | 
expiration_month | [string enum](#post-cardsavr_card-2)** | 
expiration_year | string | 
name_on_card | string | 
nickname | string | 
custom_data | object | Meta-data that can be added to the card if needed.

See [card response parameters](#response-cardsavr_card).


## Delete card

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/367162066
```

```javascript
await session.deleteCard(undefined);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(undefined);
```

```java
JsonValue card = session.delete("/cardsavr_cards", undefined, null);
```

### Path

DELETE /cardsavr_cards/{id}

### Description

Delete a card and purge its [related items](#cascading-delete).  An id is required on every delete request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [card response parameters](#response-cardsavr_card).


# Cardholders
Cardholders are the end-users of the CardSavr API, who can have their their payment information updated on merchant site(s). Cardholders can be linked to cards, accounts, and addresses.
## Get cardholder

```javascript
const cardholders = await session.getCardholders(1872752000,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution","integrator"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Cardholders> cardholders = await session.GetCardholdersAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["financial_institution","integrator"])}
JsonArray response = (JsonArray)session.get(1872752000, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1872752000,
  "type": "ephemeral",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "Itrf",
  "webhook_url": "https://mywebhooks.com/this",
  "custom_data": {
    "mfShmWbzeUFu": "wKkj/Qu3oU&[aA,Q4Y@$i0",
    "zwqjNMyPRuyY": 24,
    "TxmhNRYLHNxl": false
  },
  "created_on": "2013-08-28T20:50:02.288Z",
  "last_updated_on": "2001-04-06T23:47:37.275Z",
  "financial_institution": {
    "id": 1269399462,
    "name": "yHAoswbvRQXvqTDxeIPfilwLWsukmTMwfZRWqbTbWfQfOaPfwirtFjWPWJHguLG",
    "description": "YUGLHWiOC",
    "lookup_key": "IkgCLZhCpwTTFkIoIWUiIWyAUoTMBwneDwVGKTqCECByDKoisxvssXxcVopuPmx",
    "alternate_lookup_key": "AlIFZjVJXlzOAxkxTMmfNBpKLcLIATOOPIlwIqPpdSsdwsPbHayccyuvQNLBYbR",
    "last_activity": "1990-07-12T01:45:43.878Z",
    "created_on": "2011-06-10T08:56:52.021Z",
    "last_updated_on": "2004-12-17T01:38:02.167Z"
  },
  "integrator": {
    "id": 698724959,
    "name": "oBMSFhvGaMeGbPafZHuoaqbyqvjAemvQIazIsxarbOEcMAVYF",
    "description": "CZdWXMjVuJKNgyjGPvvQvWdJoDZTEr",
    "current_key": "uYB/5R6WtPcOisWYP76CQQi4PFN32M98byphyIV8Y8w=",
    "key_lifetime": 288,
    "next_rotation_on": "2011-03-05T22:27:19.969Z",
    "created_on": "1999-01-21T05:29:49.909Z",
    "last_updated_on": "1978-08-24T06:12:25.753Z"
  },
  "cuid": "PZkDarkwBWMwmafUtgWQNVr"
}
```

### Path

GET /cardholders **(batch)** or GET /cardholders/:id **(singular)**

### Description

Returns the cardholder specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable cardholders, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- financial_institution_ids
- financial_institution_id
- cuid
- type
- first_name
- last_name
- email
- meta_key
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/cardholders?ids=1,2`

#### Singular GET requests

**Singular requests** only return the cardholder matching the id provided in the path.

**Example GET request path:**<br>`/cardholders/1872752000`

### <a name="response-cardholder"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this cardholder.
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | 
type | string | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities. If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
first_name | string | 
last_name | string | 
email | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
webhook_url | string | A cardholder specific url for posting job reults following the end of a session.  This overrides the FI global settiings in the portal.
custom_data | object | Additional data that can be added to the cardholder if needed.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cuid | string | External unique ID for cardholder--can be account_id, email address, phone number, etc.  A random number will be gnenerated if not provided.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create cardholder

```javascript
const cardholder = await session.createCardholder({
  "cuid": "PZkDarkwBWMwmafUtgWQNVr",
  "type": "ephemeral",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "Itrf",
  "webhook_url": "https://mywebhooks.com/this",
  "custom_data": {
    "mfShmWbzeUFu": "wKkj/Qu3oU&[aA,Q4Y@$i0",
    "zwqjNMyPRuyY": 24,
    "TxmhNRYLHNxl": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cuid", "PZkDarkwBWMwmafUtgWQNVr" },
	{ "type", "ephemeral" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "Itrf" },
	{ "webhook_url", "https://mywebhooks.com/this" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cuid", "PZkDarkwBWMwmafUtgWQNVr" )
	.add("type", "ephemeral" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "Itrf" )
	.add("webhook_url", "https://mywebhooks.com/this" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"cuid\":\"PZkDarkwBWMwmafUtgWQNVr\",\"type\":\"ephemeral\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"Itrf\",\"webhook_url\":\"https://mywebhooks.com/this\",\"custom_data\":{\"mfShmWbzeUFu\":\"wKkj/Qu3oU&[aA,Q4Y@$i0\",\"zwqjNMyPRuyY\":24,\"TxmhNRYLHNxl\":false}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/
```

### Path

POST /cardholders

### Description

Create a cardholder and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cuid | string | yes | External unique ID for cardholder--can be account_id, email address, phone number, etc.  A random number will be gnenerated if not provided.
type | [string enum](#post-cardholder-1)* | no | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities. If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
first_name | string | no | 
last_name | string | no | 
email | string | no | 
meta_key | string | no | Key used for billing record identification; automatically generated during card creation.
webhook_url | string | no | A cardholder specific url for posting job reults following the end of a session.  This overrides the FI global settiings in the portal.
custom_data | object | no | Additional data that can be added to the cardholder if needed.

See [cardholder response attributes](#response-cardholder).

#### <a name="post-cardholder-1"></a>string enum*
- ephemeral
- persistent_nocreds
- persistent_creds
- persistent_all


## Upsert cardholder

```javascript
const cardholder = await session.updateCardholder(1,{
  "type": "persistent_nocreds",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "D",
  "webhook_url": "https://mywebhooks.com/this",
  "custom_data": {
    "bTBqVwpYDQLN": "{o)8F",
    "MQYgxruuwZfC": 77,
    "uQWcryTLWLDF": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "type", "persistent_nocreds" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "D" },
	{ "webhook_url", "https://mywebhooks.com/this" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("type", "persistent_nocreds" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "D" )
	.add("webhook_url", "https://mywebhooks.com/this" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"type\":\"persistent_nocreds\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"D\",\"webhook_url\":\"https://mywebhooks.com/this\",\"custom_data\":{\"bTBqVwpYDQLN\":\"{o)8F\",\"MQYgxruuwZfC\":77,\"uQWcryTLWLDF\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/1872752000
```

### Path

PUT /cardholders OR /cardholders/{id}

### Description

Upsert can be used to either update a cardholder, create a new cardholder, or return an existing cardholder.  Either an id or cuid is required for upsert. The id (in path or body), along with an updated body, can be used to update an existing cardholder; the cuid (in body) can likewise be used to update a cardholder, and can also be used to create a new cardholder, if the cuid does not match any existing cardholders. If the id or cuid provided corresponds to a pre-existing cardholder and no updated information has been included in the body, the existing cardholder will be returned.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
type | [string enum](#post-cardholder-1)* | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities. If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
first_name | string | 
last_name | string | 
email | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
webhook_url | string | A cardholder specific url for posting job reults following the end of a session.  This overrides the FI global settiings in the portal.
custom_data | object | Additional data that can be added to the cardholder if needed.

See [cardholder response parameters](#response-cardholder).


## Delete cardholder

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/1872752000
```

```javascript
await session.deleteCardholder(undefined);
```

```csharp
CardSavrResponse<Cardholder> cardholder = await http.DeleteCardholderAsync(undefined);
```

```java
JsonValue cardholder = session.delete("/cardholders", undefined, null);
```

### Path

DELETE /cardholders/{id}

### Description

Delete a cardholder and purge its [related items](#cascading-delete).  An id is required on every delete request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [cardholder response parameters](#response-cardholder).


# Users
Users are internal entities, such as agents or admins, that can perform such functions as creating and deleting cardholders, fetching merchant sites, creating jobs, etc.
## Get user

```javascript
const users = await session.getUsers(665640954,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Users> users = await session.GetUsersAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["financial_institution"])}
JsonArray response = (JsonArray)session.get(665640954, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 665640954,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "2002-06-25T22:30:43.795Z",
  "is_locked": true,
  "password_lifetime": 196,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "admin",
  "next_rotation_on": "2009-05-30T23:55:01.284Z",
  "created_on": "1979-11-01T03:28:46.649Z",
  "last_updated_on": "1991-09-25T07:30:18.554Z",
  "username": "jsmith123",
  "financial_institution": {
    "id": 1694870516,
    "name": "mzWLTBGKbUnprdnvkFgHGyfneUDfSmhHOzMMCPsnZjKksqRyNYBFhLcUVOLaSsz",
    "description": "dpfMaJlKKsgqYbwaGfFFXnUkqJtV",
    "lookup_key": "ANlsdhICAvgYWcYbONiVNBDyNJPLyHWlTNvleJLgkHRIxhGOgkMEpXmsDvxjxnQ",
    "alternate_lookup_key": "kXDSZbHlLPkDGrLEcfbxwpRTrykjVaSfAuivdcuoLJwSyJpHNyFvRZqiOCIveJD",
    "last_activity": "1995-02-28T15:00:01.038Z",
    "created_on": "2017-01-13T14:22:43.903Z",
    "last_updated_on": "1990-08-05T21:33:45.346Z"
  }
}
```

### Path

GET /cardsavr_users **(batch)** or GET /cardsavr_users/:id **(singular)**

### Description

Returns the user specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable users, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- financial_institution_ids
- usernames
- username
- first_name
- last_name
- last_login_time_min / last_login_time_max
- is_locked
- email
- is_password_update_required
- role
- roles_include / roles_exclude
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/cardsavr_users?ids=1,2`

#### Singular GET requests

**Singular requests** only return the user matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_users/665640954`

### <a name="response-cardsavr_user"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this user.
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | 
first_name | string | 
last_name | string | 
last_login_time | date | 
is_locked | boolean | 
password_lifetime | number | Length of time that password will remain valid.
email | string | 
is_password_update_required | boolean | 
role | string | <p>User role (cardholder_agent, cardholder_sso_agent or customer_agent) determines the user's ability to access certain endpoints and perform certain operations within the CardSavr API.</p><p>cardholder_agents can create cardholders, create card's addresses for those cardholders, create accounts for those cardholders, and post jobs for those cardholders. cardholder_sso_agents are like cardholder_agent, but cannot create cardholder or cards.</p>customer_agents can peform all actions on cardholders/accounts/, but are limited to acting on cardholders/jobs/accounts/cards within their FI (unless they are assigned to the admin FI)
next_rotation_on | date | Date of next password rotation for this user.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
username | string | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create user

```javascript
const user = await session.createUser({
  "financial_institution_id": 1384278015,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 196,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "admin",
  "next_rotation_on": "2009-05-30T23:55:01.284Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1384278015 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 196 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "admin" },
	{ "next_rotation_on", "2009-05-30T23:55:01.284Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1384278015 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 196 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "admin" )
	.add("next_rotation_on", "2009-05-30T23:55:01.284Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1384278015,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":196,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"admin\",\"next_rotation_on\":\"2009-05-30T23:55:01.284Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/
```

### Path

POST /cardsavr_users

### Description

Create a user and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
financial_institution_id | number | yes | 
username | string | yes | 
password | string | yes | 
first_name | string | no | 
last_name | string | no | 
password_lifetime | number | no | Length of time that password will remain valid.
email | string | no | 
is_password_update_required | boolean | no | 
role | [string enum](#post-cardsavr_user-1)* | yes | <p>User role (cardholder_agent, cardholder_sso_agent or customer_agent) determines the user's ability to access certain endpoints and perform certain operations within the CardSavr API.</p><p>cardholder_agents can create cardholders, create card's addresses for those cardholders, create accounts for those cardholders, and post jobs for those cardholders. cardholder_sso_agents are like cardholder_agent, but cannot create cardholder or cards.</p>customer_agents can peform all actions on cardholders/accounts/, but are limited to acting on cardholders/jobs/accounts/cards within their FI (unless they are assigned to the admin FI)
next_rotation_on | date | no | Date of next password rotation for this user.

See [user response attributes](#response-cardsavr_user).

#### <a name="post-cardsavr_user-1"></a>string enum*
- admin
- cardholder_sso_agent
- cardholder_agent
- customer_agent
- swch_agent


## Update user

```javascript
const user = await session.updateUser(1,{
  "financial_institution_id": 1942030194,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 181,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_agent",
  "next_rotation_on": "2011-10-28T09:04:20.612Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1942030194 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 181 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "swch_agent" },
	{ "next_rotation_on", "2011-10-28T09:04:20.612Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1942030194 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 181 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "swch_agent" )
	.add("next_rotation_on", "2011-10-28T09:04:20.612Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1942030194,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":181,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"swch_agent\",\"next_rotation_on\":\"2011-10-28T09:04:20.612Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/665640954
```

### Path

PUT /cardsavr_users OR /cardsavr_users/{id}

### Description

Update a user and return the updated object.  An id is required on every update request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
financial_institution_id | number | 
first_name | string | 
last_name | string | 
password_lifetime | number | Length of time that password will remain valid.
email | string | 
is_password_update_required | boolean | 
role | [string enum](#post-cardsavr_user-1)* | <p>User role (cardholder_agent, cardholder_sso_agent or customer_agent) determines the user's ability to access certain endpoints and perform certain operations within the CardSavr API.</p><p>cardholder_agents can create cardholders, create card's addresses for those cardholders, create accounts for those cardholders, and post jobs for those cardholders. cardholder_sso_agents are like cardholder_agent, but cannot create cardholder or cards.</p>customer_agents can peform all actions on cardholders/accounts/, but are limited to acting on cardholders/jobs/accounts/cards within their FI (unless they are assigned to the admin FI)
next_rotation_on | date | Date of next password rotation for this user.

See [user response parameters](#response-cardsavr_user).


## Delete user

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/665640954
```

```javascript
await session.deleteUser(undefined);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(undefined);
```

```java
JsonValue user = session.delete("/cardsavr_users", undefined, null);
```

### Path

DELETE /cardsavr_users/{id}

### Description

Delete a user and purge its [related items](#cascading-delete).  An id is required on every delete request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [user response parameters](#response-cardsavr_user).


# Financial Institutions
Financial Institution (FI) objects represent individual FIs and can be linked to users and cardholders. They also contain the configuration information that can be used to customize an FI's CardUpdatr instance, if one exists.
## Get financial institution

```javascript
const financialinstitutions = await session.getFinancialInstitutions(478801859,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = 
JsonArray response = (JsonArray)session.get(478801859, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 478801859,
  "name": "CIjVcPmwGvIETVCPiWPjaImGToeFaVSIkcJTBxpYkTNnbbuFwJtjMVFcZGJdkXz",
  "description": "Qt",
  "lookup_key": "mgHatDLVPcTWbBGCKdPqGXGKSpEKVNgswubIPsKxAwSavgpvJXAwWyaESKJUkJL",
  "alternate_lookup_key": "YwlBoskcrzOlZbKzvlerIbDnrltbFWMxzPoDXCELsfFnlqSfIBsCcQlcNUcuBXF",
  "last_activity": "2017-09-08T00:42:39.675Z",
  "created_on": "2010-08-16T23:22:55.352Z",
  "last_updated_on": "1971-11-11T01:22:58.886Z"
}
```

### Path

GET /financial_institutions **(batch)** or GET /financial_institutions/:id **(singular)**

### Description

Returns the financial institution specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable financial institutions, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- id
- names
- lookup_key
- exclude_lookup_keys
- alternate_lookup_key
- last_activity_min / last_activity_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/financial_institutions?ids=1,2`

#### Singular GET requests

**Singular requests** only return the financial institution matching the id provided in the path.

**Example GET request path:**<br>`/financial_institutions/478801859`

### <a name="response-financial_institution"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this financial institution.
name | string | 
description | string | 
lookup_key | string | Unique key used to identify financial institution.
alternate_lookup_key | string | Alternate lookup key; can be used in case of FI name change that does not match original lookup_key, in order to maintain backwards compatibility.
last_activity | date | Date of last cardholder creation for this financial institution
created_on | date | Date this financial institution was created on
last_updated_on | date | Date this financial institution was last updated on

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create financial institution

```javascript
const financialinstitution = await session.createFinancialInstitution({
  "name": "CIjVcPmwGvIETVCPiWPjaImGToeFaVSIkcJTBxpYkTNnbbuFwJtjMVFcZGJdkXz",
  "description": "Qt",
  "lookup_key": "mgHatDLVPcTWbBGCKdPqGXGKSpEKVNgswubIPsKxAwSavgpvJXAwWyaESKJUkJL",
  "alternate_lookup_key": "YwlBoskcrzOlZbKzvlerIbDnrltbFWMxzPoDXCELsfFnlqSfIBsCcQlcNUcuBXF"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "CIjVcPmwGvIETVCPiWPjaImGToeFaVSIkcJTBxpYkTNnbbuFwJtjMVFcZGJdkXz" },
	{ "description", "Qt" },
	{ "lookup_key", "mgHatDLVPcTWbBGCKdPqGXGKSpEKVNgswubIPsKxAwSavgpvJXAwWyaESKJUkJL" },
	{ "alternate_lookup_key", "YwlBoskcrzOlZbKzvlerIbDnrltbFWMxzPoDXCELsfFnlqSfIBsCcQlcNUcuBXF" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "CIjVcPmwGvIETVCPiWPjaImGToeFaVSIkcJTBxpYkTNnbbuFwJtjMVFcZGJdkXz" )
	.add("description", "Qt" )
	.add("lookup_key", "mgHatDLVPcTWbBGCKdPqGXGKSpEKVNgswubIPsKxAwSavgpvJXAwWyaESKJUkJL" )
	.add("alternate_lookup_key", "YwlBoskcrzOlZbKzvlerIbDnrltbFWMxzPoDXCELsfFnlqSfIBsCcQlcNUcuBXF" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"CIjVcPmwGvIETVCPiWPjaImGToeFaVSIkcJTBxpYkTNnbbuFwJtjMVFcZGJdkXz\",\"description\":\"Qt\",\"lookup_key\":\"mgHatDLVPcTWbBGCKdPqGXGKSpEKVNgswubIPsKxAwSavgpvJXAwWyaESKJUkJL\",\"alternate_lookup_key\":\"YwlBoskcrzOlZbKzvlerIbDnrltbFWMxzPoDXCELsfFnlqSfIBsCcQlcNUcuBXF\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/
```

### Path

POST /financial_institutions

### Description

Create a financial institution and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
name | string | yes | 
description | string | no | 
lookup_key | string | yes | Unique key used to identify financial institution.
alternate_lookup_key | string | no | Alternate lookup key; can be used in case of FI name change that does not match original lookup_key, in order to maintain backwards compatibility.

See [financial institution response attributes](#response-financial_institution).


## Update financial institution

```javascript
const financialinstitution = await session.updateFinancialInstitution(1,{
  "name": "UTjymsymJJhLjrRdiONwGYpxpbvPQSOzqArZqdAFbymQFdUnQhBFJCNXxTpKfHS",
  "description": "CYgeLoWQURGfZNMXuEKrNhWAc",
  "lookup_key": "OjcTjTqcVqKMyKtcUcSxvgsKNLBqxXsLVlTvVaYBgqYWVrgmbeZZNaPGhqUuSoZ",
  "alternate_lookup_key": "uJyxtvVSaUyLAULDemdfRqQvbIUHHUdstygCFiZIQvnDLmKLazgXHbQUFoRTNSD"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "UTjymsymJJhLjrRdiONwGYpxpbvPQSOzqArZqdAFbymQFdUnQhBFJCNXxTpKfHS" },
	{ "description", "CYgeLoWQURGfZNMXuEKrNhWAc" },
	{ "lookup_key", "OjcTjTqcVqKMyKtcUcSxvgsKNLBqxXsLVlTvVaYBgqYWVrgmbeZZNaPGhqUuSoZ" },
	{ "alternate_lookup_key", "uJyxtvVSaUyLAULDemdfRqQvbIUHHUdstygCFiZIQvnDLmKLazgXHbQUFoRTNSD" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "UTjymsymJJhLjrRdiONwGYpxpbvPQSOzqArZqdAFbymQFdUnQhBFJCNXxTpKfHS" )
	.add("description", "CYgeLoWQURGfZNMXuEKrNhWAc" )
	.add("lookup_key", "OjcTjTqcVqKMyKtcUcSxvgsKNLBqxXsLVlTvVaYBgqYWVrgmbeZZNaPGhqUuSoZ" )
	.add("alternate_lookup_key", "uJyxtvVSaUyLAULDemdfRqQvbIUHHUdstygCFiZIQvnDLmKLazgXHbQUFoRTNSD" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"UTjymsymJJhLjrRdiONwGYpxpbvPQSOzqArZqdAFbymQFdUnQhBFJCNXxTpKfHS\",\"description\":\"CYgeLoWQURGfZNMXuEKrNhWAc\",\"lookup_key\":\"OjcTjTqcVqKMyKtcUcSxvgsKNLBqxXsLVlTvVaYBgqYWVrgmbeZZNaPGhqUuSoZ\",\"alternate_lookup_key\":\"uJyxtvVSaUyLAULDemdfRqQvbIUHHUdstygCFiZIQvnDLmKLazgXHbQUFoRTNSD\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/478801859
```

### Path

PUT /financial_institutions OR /financial_institutions/{id}

### Description

Update a financial institution and return the updated object.  An id is required on every update request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
name | string | 
description | string | 
lookup_key | string | Unique key used to identify financial institution.
alternate_lookup_key | string | Alternate lookup key; can be used in case of FI name change that does not match original lookup_key, in order to maintain backwards compatibility.

See [financial institution response parameters](#response-financial_institution).


## Delete financial institution

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/478801859
```

```javascript
await session.deleteFinancialInstitution(undefined);
```

```csharp
CardSavrResponse<FinancialInstitution> financialinstitution = await http.DeleteFinancialInstitutionAsync(undefined);
```

```java
JsonValue financialinstitution = session.delete("/financial_institutions", undefined, null);
```

### Path

DELETE /financial_institutions/{id}

### Description

Delete a financial institution and purge its [related items](#cascading-delete).  An id is required on every delete request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [financial institution response parameters](#response-financial_institution).


# Integrators
Integrators are applications that integrate the CardSavr API, using their own unique integrator key. An integrator name and key are required for all calls to the CardSavr API. An integrator can be associated with multiple users.
## Get integrator

```javascript
const integrators = await session.getIntegrators(1444857493,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = 
JsonArray response = (JsonArray)session.get(1444857493, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1444857493,
  "name": "RfJovShRQCFbAtutAwpCFakaOmAyZGSdVZbsEQMCQosvzrIYM",
  "description": "BEcHAOzb",
  "current_key": "LStjUequR3lMTR/ua4eBhTXpjZvpRx04NeAOBn5hVGc=",
  "key_lifetime": 328,
  "next_rotation_on": "2015-03-18T21:54:25.369Z",
  "created_on": "1980-11-04T17:02:49.911Z",
  "last_updated_on": "2001-06-14T22:33:55.568Z"
}
```

### Path

GET /integrators **(batch)** or GET /integrators/:id **(singular)**

### Description

Returns the integrator specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable integrators, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- names
- name
- next_rotation_on_min / next_rotation_on_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/integrators?ids=1,2`

#### Singular GET requests

**Singular requests** only return the integrator matching the id provided in the path.

**Example GET request path:**<br>`/integrators/1444857493`

### <a name="response-integrator"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this integrator.
name | string | Name of integrator.
description | string | 
current_key | string | Current key for this integrator.
key_lifetime | number | Sets the duration of validity for integrator key.
next_rotation_on | date | Date of next key rotation for this integrator.
created_on | date | Date this integrator was created on
last_updated_on | date | Date this integrator was last updated on

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create integrator

```javascript
const integrator = await session.createIntegrator({
  "name": "RfJovShRQCFbAtutAwpCFakaOmAyZGSdVZbsEQMCQosvzrIYM",
  "description": "BEcHAOzb",
  "current_key": "LStjUequR3lMTR/ua4eBhTXpjZvpRx04NeAOBn5hVGc=",
  "key_lifetime": 328,
  "next_rotation_on": "2015-03-18T21:54:25.369Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "RfJovShRQCFbAtutAwpCFakaOmAyZGSdVZbsEQMCQosvzrIYM" },
	{ "description", "BEcHAOzb" },
	{ "current_key", "LStjUequR3lMTR/ua4eBhTXpjZvpRx04NeAOBn5hVGc=" },
	{ "key_lifetime", 328 },
	{ "next_rotation_on", "2015-03-18T21:54:25.369Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "RfJovShRQCFbAtutAwpCFakaOmAyZGSdVZbsEQMCQosvzrIYM" )
	.add("description", "BEcHAOzb" )
	.add("current_key", "LStjUequR3lMTR/ua4eBhTXpjZvpRx04NeAOBn5hVGc=" )
	.add("key_lifetime", 328 )
	.add("next_rotation_on", "2015-03-18T21:54:25.369Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"RfJovShRQCFbAtutAwpCFakaOmAyZGSdVZbsEQMCQosvzrIYM\",\"description\":\"BEcHAOzb\",\"current_key\":\"LStjUequR3lMTR/ua4eBhTXpjZvpRx04NeAOBn5hVGc=\",\"key_lifetime\":328,\"next_rotation_on\":\"2015-03-18T21:54:25.369Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/
```

### Path

POST /integrators

### Description

Create a integrator and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
name | string | yes | Name of integrator.
description | string | no | 
current_key | string | yes | Current key for this integrator.
key_lifetime | number | no | Sets the duration of validity for integrator key.
next_rotation_on | date | no | Date of next key rotation for this integrator.

See [integrator response attributes](#response-integrator).


## Update integrator

```javascript
const integrator = await session.updateIntegrator(1,{
  "name": "xnakbfIwBwnwuZrkXylxzNyqDSbMsVbHOepJicHSWHdcSCoLY",
  "description": "JhjViCCORA",
  "current_key": "+M6WEu0Zrsb0fuNADYjfX9ZlKMIGfPmBAWgiEUrVBVQ=",
  "key_lifetime": 15,
  "next_rotation_on": "1981-03-10T18:10:54.691Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "xnakbfIwBwnwuZrkXylxzNyqDSbMsVbHOepJicHSWHdcSCoLY" },
	{ "description", "JhjViCCORA" },
	{ "current_key", "+M6WEu0Zrsb0fuNADYjfX9ZlKMIGfPmBAWgiEUrVBVQ=" },
	{ "key_lifetime", 15 },
	{ "next_rotation_on", "1981-03-10T18:10:54.691Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "xnakbfIwBwnwuZrkXylxzNyqDSbMsVbHOepJicHSWHdcSCoLY" )
	.add("description", "JhjViCCORA" )
	.add("current_key", "+M6WEu0Zrsb0fuNADYjfX9ZlKMIGfPmBAWgiEUrVBVQ=" )
	.add("key_lifetime", 15 )
	.add("next_rotation_on", "1981-03-10T18:10:54.691Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"xnakbfIwBwnwuZrkXylxzNyqDSbMsVbHOepJicHSWHdcSCoLY\",\"description\":\"JhjViCCORA\",\"current_key\":\"+M6WEu0Zrsb0fuNADYjfX9ZlKMIGfPmBAWgiEUrVBVQ=\",\"key_lifetime\":15,\"next_rotation_on\":\"1981-03-10T18:10:54.691Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/1444857493
```

### Path

PUT /integrators OR /integrators/{id}

### Description

Update a integrator and return the updated object.  An id is required on every update request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
name | string | Name of integrator.
description | string | 
current_key | string | Current key for this integrator.
key_lifetime | number | Sets the duration of validity for integrator key.
next_rotation_on | date | Date of next key rotation for this integrator.

See [integrator response parameters](#response-integrator).


## Delete integrator

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/1444857493
```

```javascript
await session.deleteIntegrator(undefined);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(undefined);
```

```java
JsonValue integrator = session.delete("/integrators", undefined, null);
```

### Path

DELETE /integrators/{id}

### Description

Delete a integrator and purge its [related items](#cascading-delete).  An id is required on every delete request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [integrator response parameters](#response-integrator).


# Merchant sites
A merchant site object contains information, such as images URLs and hostname, for a CardSavr-supported merchant site.
## Get merchant site

```javascript
const merchantsites = await session.getMerchantSites(421751717,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = 
JsonArray response = (JsonArray)session.get(421751717, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 421751717,
  "name": "Amazon",
  "note": "YtsnMAIpPzsPXwrbEAMMUww",
  "host": "amazon.com",
  "tags": [
    "Lc5e%/]x",
    37,
    "!"
  ],
  "interface_type": "rpa",
  "job_type": "CARD_PLACEMENT",
  "required_form_fields": [
    "email",
    "phone_number",
    "card_data",
    "cvv",
    "billing_address",
    "postal_code"
  ],
  "images": [
    {
      "url": "https://d1t7g1oas7m24a.cloudfront.net/tiles/dollarshaveclub.com?width=128&version=21f917315911eec1b1705bc7784ce861579cff2b",
      "width": 128,
      "grayscale": false
    },
    {
      "url": "https://d1t7g1oas7m24a.cloudfront.net/tiles/dollarshaveclub.com?width=32&version=21f917315911eec1b1705bc7784ce861579cff2b",
      "width": 32,
      "grayscale": false
    }
  ],
  "account_link": [
    {
      "key_name": "username",
      "label": "Username",
      "type": "initial_account_link"
    },
    {
      "key_name": "password",
      "label": "Password",
      "type": "initial_account_link",
      "secret": true
    },
    {
      "key_name": "otp",
      "label": "One Time Passcode",
      "type": ""
    }
  ],
  "messages": {
    "mfa_label": "Additional information required, this code may be sent to your phone or email address.",
    "additional_info_message": "",
    "auth_message": "Linking account."
  },
  "script_directory": "cjvj",
  "record_final_site_artifacts": true,
  "puppeteer_screenshot": false,
  "login_page": "https://www.merchantsite.com/login",
  "forgot_password_page": "https://www.merchantsite.com/forgot_password",
  "credit_card_page": "https://www.merchantsite.com/credit_card",
  "wallet_page": "UhElrZNIWZayhSvx",
  "merchant_sso_group": "IIKQwXNUklUgcxMzyk",
  "tier": 1145990086,
  "cookie_caching_scheme": "none",
  "dynamic_viewport": true,
  "use_puppeteer": true
}
```

### Path

GET /merchant_sites **(batch)** or GET /merchant_sites/:id **(singular)**

### Description

Returns the merchant site specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable merchant sites, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- id
- exclude_ids
- top_ids
- name_starts_with
- hosts
- host
- exclude_hosts
- top_hosts
- host_starts_with
- tags
- image_widths

**Example batch GET request path:**<br>`/merchant_sites?ids=1,2`

#### Singular GET requests

**Singular requests** only return the merchant site matching the id provided in the path.

**Example GET request path:**<br>`/merchant_sites/421751717`

### <a name="response-merchant_site"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this merchant site.
name | string | 
note | string | Human-readable note about the site for developers
host | string | For interface type 'dcs',  hostname of the DCS broker server for the merchant site; for interface type 'vbs' hostname of the merchant_site. e.g. amazon.com
tags | array | Tags for filtering desired merchant sites.  This could either be site status (e.g. prod, down), countries supported (e.g. usa, canada), or site attributes (e.g. synthetic).  Tags can also be compounded to create combinations: (e.g. ?tags=prod,synthetic&tags=usa,synthetic means all sites tagged prod and usa and also sites tagged synthetic)
interface_type | string | Type of interface agent to use with merchant. Set to 'dcs' for a site that has direct connect support; and to 'vbs' for a site using Robotic Process Automation
job_type | string | Type of job this site supports. Card placement or bill payment
required_form_fields | array | Indicates the cardholder personal information fields that are required by this site.
images | array | URLs of the images for this merchant site.  Use a filter parameter of 'image_widths', a comma delimited list of widths (e.g. image_widths=64).  Tile images with these widths will be returned.  The default is 128 and 32 width images.
account_link | array | One or more property sets with key names to populated on POST/PUT /cardsavr_accounts requests, and labels to display to the end user for the type of information being requested for this site ( e.g. Username, Password, Account Number, Email, ... ) Each property contains its 'key_name', a 'label' that defines the property, a 'secret' flag (property should be masked on input like a password), and a type.  Only properties with a type of 'initial_account_link' should be presented upon initial credential collection.  For example, an input field for 'tfa' is not displayed on initial collection.  All other non-'initial_account_link' properties will be requested while the transactiion progresses and they are only listed here for informational purposes.
messages | object | Message properties to display to end users.  Supercedes the deprecated loging properties. The message properties are mfa_label: additional informaton required for mfs challenges such as a code sent to users phone or email, additional_info_message: some contextual info sent from CardSavr to aid the user interaction, auth_message: a label to display during during the authentication phase
script_directory | string | Optional override for the name of the directory to lookup scripts in (default is host)
record_final_site_artifacts | boolean | Take a snapshot of html and a screenshot of the final merchant site. Disabling this can speed up task cleanup.
puppeteer_screenshot | boolean | Use puppeteer to take a screenshot of site for debugging.
login_page | string | URL of login page.
forgot_password_page | string | Merchant's forgotten password page.
credit_card_page | string | Merchant's credit card entry page.
wallet_page | string | URL of the site's wallet page, where the is a list of last 4 card numbers.
merchant_sso_group | string | Default group a site rolls up to. Jobs for the same user account should not run simultaneously.
tier | number | Site's tier based on perceived card usage on that site.
cookie_caching_scheme | string | Caching scheme for saving site cookies to allow for auto-resumption of previous cardholder sessions
dynamic_viewport | boolean | whether or not the VBS puppeteer viewport size is dynamic.
use_puppeteer | boolean | whether or not the VBS will use puppeteer instead of playwright.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

# Notifications
Notification objects define a set of actions to be triggered by certain CardSavr events, such as session completion.
## Get notification

```javascript
const notifications = await session.getNotifications(1811795793,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["financial_institution"])}
JsonArray response = (JsonArray)session.get(1811795793, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1811795793,
  "name": "Sample Notification",
  "type": "webhook",
  "event": "webhook_error_summary",
  "config": {
    "recipient": "cardholder",
    "url": null,
    "from_email": "CardUpdatr <no-reply@cardupdatr.app>",
    "return_path": "no-reply@cardupdatr.app",
    "send_email_time": null,
    "interval_length": null,
    "interval_type": null
  },
  "html_template": "CddiNoOBELIQdyv",
  "text_template": "EInPepGTzvNTzajdUKePbNwdurIXM",
  "created_on": "2023-05-22T14:53:36.214Z",
  "last_updated_on": "2002-08-25T00:53:09.939Z",
  "financial_institution": {
    "id": 61599913,
    "name": "FDmwvHzEyhNFHkNrxtTWXHyegakvMTTgCcPZtCPCBwbtPCLAOnAkbTabzNIXUCt",
    "description": "sobY",
    "lookup_key": "RgdbpdRHjrXZwfItzDDCsYBQjtnBJtcXNqxLbQxbqDBvbeqfvXZvcejPzEitByf",
    "alternate_lookup_key": "CfpKYKAyYQhprCjggVvPMXDdofJSLehPxbgCryfNVCTUeTZbcRsQaQpyBdSqblW",
    "last_activity": "1980-11-13T02:28:33.564Z",
    "created_on": "2017-12-04T12:42:42.099Z",
    "last_updated_on": "1995-11-10T13:13:29.402Z"
  }
}
```

### Path

GET /notifications **(batch)** or GET /notifications/:id **(singular)**

### Description

Returns the notification specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable notifications, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- financial_institution_ids
- names
- type
- events
- event
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/notifications?ids=1,2`

#### Singular GET requests

**Singular requests** only return the notification matching the id provided in the path.

**Example GET request path:**<br>`/notifications/1811795793`

### <a name="response-notification"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this notification.
name | string | Name of this notification.
type | string | Notification type (e.g. webhook or email).
event | string | Event that will triger the notification (e.g. session complete).
config | object | 
html_template | string | Overrides the default CardUpdatr html email template (for email notifications).
text_template | string | Overrides the default CardUpdatr text email template (for email notifications).
created_on | date | Date this notification was created on
last_updated_on | date | Date this notification was last updated on
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | ID of the financial institution associated with this notification.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create notification

```javascript
const notification = await session.createNotification({
  "financial_institution_id": 780479503,
  "name": "Sample Notification",
  "type": "webhook",
  "event": "webhook_error_summary",
  "config": {
    "recipient": "cardholder",
    "url": null,
    "from_email": "CardUpdatr <no-reply@cardupdatr.app>",
    "return_path": "no-reply@cardupdatr.app",
    "send_email_time": null,
    "interval_length": null,
    "interval_type": null
  },
  "html_template": "CddiNoOBELIQdyv",
  "text_template": "EInPepGTzvNTzajdUKePbNwdurIXM"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 780479503 },
	{ "name", "Sample Notification" },
	{ "type", "webhook" },
	{ "event", "webhook_error_summary" },
	{ "html_template", "CddiNoOBELIQdyv" },
	{ "text_template", "EInPepGTzvNTzajdUKePbNwdurIXM" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 780479503 )
	.add("name", "Sample Notification" )
	.add("type", "webhook" )
	.add("event", "webhook_error_summary" )
	.add("html_template", "CddiNoOBELIQdyv" )
	.add("text_template", "EInPepGTzvNTzajdUKePbNwdurIXM" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":780479503,\"name\":\"Sample Notification\",\"type\":\"webhook\",\"event\":\"webhook_error_summary\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"CddiNoOBELIQdyv\",\"text_template\":\"EInPepGTzvNTzajdUKePbNwdurIXM\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/
```

### Path

POST /notifications

### Description

Create a notification and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
financial_institution_id | number | yes | ID of the financial institution associated with this notification.
name | string | yes | Name of this notification.
type | [string enum](#post-notification-1)* | yes | Notification type (e.g. webhook or email).
event | [string enum](#post-notification-2)** | yes | Event that will triger the notification (e.g. session complete).
config | object | no | 
html_template | string | no | Overrides the default CardUpdatr html email template (for email notifications).
text_template | string | no | Overrides the default CardUpdatr text email template (for email notifications).

See [notification response attributes](#response-notification).

#### <a name="post-notification-1"></a>string enum*
- email
- webhook

#### <a name="post-notification-2"></a>string enum**
- session_complete
- webhook_error_summary
- merchant_site_updates_top
- merchant_site_updates_all


## Update notification

```javascript
const notification = await session.updateNotification(1,{
  "name": "Sample Notification",
  "type": "email",
  "event": "merchant_site_updates_top",
  "config": {
    "recipient": "cardholder",
    "url": null,
    "from_email": "CardUpdatr <no-reply@cardupdatr.app>",
    "return_path": "no-reply@cardupdatr.app",
    "send_email_time": null,
    "interval_length": null,
    "interval_type": null
  },
  "html_template": "cyrChzIdjwscFdsVi",
  "text_template": "yyeUQOgFFgLmWffjuYCPbjvCdciEvOK"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Sample Notification" },
	{ "type", "email" },
	{ "event", "merchant_site_updates_top" },
	{ "html_template", "cyrChzIdjwscFdsVi" },
	{ "text_template", "yyeUQOgFFgLmWffjuYCPbjvCdciEvOK" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Sample Notification" )
	.add("type", "email" )
	.add("event", "merchant_site_updates_top" )
	.add("html_template", "cyrChzIdjwscFdsVi" )
	.add("text_template", "yyeUQOgFFgLmWffjuYCPbjvCdciEvOK" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"Sample Notification\",\"type\":\"email\",\"event\":\"merchant_site_updates_top\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"cyrChzIdjwscFdsVi\",\"text_template\":\"yyeUQOgFFgLmWffjuYCPbjvCdciEvOK\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/1811795793
```

### Path

PUT /notifications OR /notifications/{id}

### Description

Update a notification and return the updated object.  An id is required on every update request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
name | string | Name of this notification.
type | [string enum](#post-notification-1)* | Notification type (e.g. webhook or email).
event | [string enum](#post-notification-2)** | Event that will triger the notification (e.g. session complete).
config | object | 
html_template | string | Overrides the default CardUpdatr html email template (for email notifications).
text_template | string | Overrides the default CardUpdatr text email template (for email notifications).

See [notification response parameters](#response-notification).


## Delete notification

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/1811795793
```

```javascript
await session.deleteNotification(undefined);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(undefined);
```

```java
JsonValue notification = session.delete("/notifications", undefined, null);
```

### Path

DELETE /notifications/{id}

### Description

Delete a notification and purge its [related items](#cascading-delete).  An id is required on every delete request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [notification response parameters](#response-notification).


# Notification results
Notification result objects are records of an attempt/attempts to send a notification, indicating success/failure and additional relevant information.
## Get notification result

```javascript
const notificationresults = await session.getNotificationResults(1338807535,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["notification"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<NotificationResults> notificationresults = await session.GetNotificationResultsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["notification"])}
JsonArray response = (JsonArray)session.get(1338807535, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1338807535,
  "last_attempt_date": "2008-04-14T15:12:22.777Z",
  "fi_lookup_key": "DplOklhSgzCqxfiWBhFMSfTlJnlbnOOFqgjnQzTNnbFHtrhRUBWNtlmxfrWPRcV",
  "cuid": "HgDugQBfGzTgtZqnIHbDaVewMSzlm",
  "status": "success",
  "attempts": 1980200462,
  "notification_data": {
    "TXMJccGzYUtf": "H[okVi7u%q4fy.H(_VZ0.KTwVV",
    "xlRGLoLMIrBT": 43,
    "gGVivAPljZtF": false
  },
  "created_on": "1987-11-20T09:26:44.920Z",
  "last_updated_on": "2014-10-02T23:13:17.440Z",
  "notification": {
    "id": 1069490097,
    "name": "Sample Notification",
    "type": "webhook",
    "event": "session_complete",
    "config": {
      "recipient": "cardholder",
      "url": null,
      "from_email": "CardUpdatr <no-reply@cardupdatr.app>",
      "return_path": "no-reply@cardupdatr.app",
      "send_email_time": null,
      "interval_length": null,
      "interval_type": null
    },
    "html_template": "y",
    "text_template": "q",
    "created_on": "1977-02-05T04:06:11.422Z",
    "last_updated_on": "1987-08-01T14:35:13.802Z"
  }
}
```

### Path

GET /notification_results **(batch)** or GET /notification_results/:id **(singular)**

### Description

Returns the notification result specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable notification results, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- notification_ids
- last_attempt_date_min / last_attempt_date_max
- fi_lookup_keys
- cuid
- status
- attempts
- attempts_min / attempts_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/notification_results?ids=1,2`

#### Singular GET requests

**Singular requests** only return the notification result matching the id provided in the path.

**Example GET request path:**<br>`/notification_results/1338807535`

### <a name="response-notification_result"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this notification.
last_attempt_date | date | Date of last attempt to post this notification.
fi_lookup_key | string | FI lookup key associated with the attempted notification.
cuid | string | External unique ID for cardholder--can be account_id, email address, phone number, etc.  A random number will be gnenerated if not provided.
status | string | Status of the notification attempt.
attempts | number | Number of attempts made to send or post notification.
notification_data | object | Data sent with the notification.
created_on | date | Date this notification result was created on
last_updated_on | date | Date this notification result was last updated on
notification_id | number (fk) [notifications](#notifications) | ID of the attempted notification.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create notification result

```javascript
const notificationresult = await session.createNotificationResult({
  "notification_id": 800158275,
  "fi_lookup_key": "DplOklhSgzCqxfiWBhFMSfTlJnlbnOOFqgjnQzTNnbFHtrhRUBWNtlmxfrWPRcV",
  "cuid": "HgDugQBfGzTgtZqnIHbDaVewMSzlm",
  "status": "success",
  "attempts": 1980200462,
  "notification_data": {
    "TXMJccGzYUtf": "H[okVi7u%q4fy.H(_VZ0.KTwVV",
    "xlRGLoLMIrBT": 43,
    "gGVivAPljZtF": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 800158275 },
	{ "fi_lookup_key", "DplOklhSgzCqxfiWBhFMSfTlJnlbnOOFqgjnQzTNnbFHtrhRUBWNtlmxfrWPRcV" },
	{ "cuid", "HgDugQBfGzTgtZqnIHbDaVewMSzlm" },
	{ "status", "success" },
	{ "attempts", 1980200462 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 800158275 )
	.add("fi_lookup_key", "DplOklhSgzCqxfiWBhFMSfTlJnlbnOOFqgjnQzTNnbFHtrhRUBWNtlmxfrWPRcV" )
	.add("cuid", "HgDugQBfGzTgtZqnIHbDaVewMSzlm" )
	.add("status", "success" )
	.add("attempts", 1980200462 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":800158275,\"fi_lookup_key\":\"DplOklhSgzCqxfiWBhFMSfTlJnlbnOOFqgjnQzTNnbFHtrhRUBWNtlmxfrWPRcV\",\"cuid\":\"HgDugQBfGzTgtZqnIHbDaVewMSzlm\",\"status\":\"success\",\"attempts\":1980200462,\"notification_data\":{\"TXMJccGzYUtf\":\"H[okVi7u%q4fy.H(_VZ0.KTwVV\",\"xlRGLoLMIrBT\":43,\"gGVivAPljZtF\":false}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notification_results/
```

### Path

POST /notification_results

### Description

Create a notification result and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
notification_id | number | yes | ID of the attempted notification.
fi_lookup_key | string | yes | FI lookup key associated with the attempted notification.
cuid | string | yes | External unique ID for cardholder--can be account_id, email address, phone number, etc.  A random number will be gnenerated if not provided.
status | [string enum](#post-notification_result-1)* | yes | Status of the notification attempt.
attempts | number | yes | Number of attempts made to send or post notification.
notification_data | object | no | Data sent with the notification.

See [notification result response attributes](#response-notification_result).

#### <a name="post-notification_result-1"></a>string enum*
- success
- failure

# Single-site jobs
Single-site job objects contain the information necessary to place a payment card on a merchant site, as well as status information about the card placement attempt. They are linked to a single cardholder, account, card, and merchant site.
## Get single-site job

```javascript
const singlesitejobs = await session.getSingleSiteJobs(750836597,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_card","cardsavr_account","credential_requests"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_card","cardsavr_account","credential_requests"])}
JsonArray response = (JsonArray)session.get(750836597, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 750836597,
  "status": "CANCELLED",
  "status_message": "LosqYmvFSUiAPXv",
  "termination_type": "USER_DATA_FAILURE",
  "custom_data": {
    "JMlLIhHrMqOl": "Grc7r(TKWRuTX0qgm7Vc",
    "XmyODUFRqdVz": 80,
    "ecPtHWTuRFXn": false
  },
  "notification_sent": false,
  "time_elapsed": 488741644,
  "auth_percent_complete": 56642461,
  "percent_complete": 818184615,
  "started_on": "1981-12-19T21:43:37.659Z",
  "completed_on": "1992-08-02T10:50:19.487Z",
  "created_on": "1986-01-03T06:05:45.953Z",
  "last_updated_on": "1977-12-06T12:40:38.326Z",
  "use_puppeteer": true,
  "cardholder": {
    "id": 1848500081,
    "type": "ephemeral",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "l",
    "webhook_url": "https://mywebhooks.com/this",
    "custom_data": {
      "dyfdQaScWHMT": "bpF5decCah@%d94#(EOT6~Rv+IqG",
      "moTebbPWfWDU": 18,
      "PHHVtBwSmFDR": true
    },
    "created_on": "1981-11-22T07:19:32.232Z",
    "last_updated_on": "1986-11-26T19:45:38.740Z",
    "cuid": "omOrvilk"
  },
  "cardsavr_card": {
    "id": 1176505801,
    "type": "American Express",
    "expiration_month": 12,
    "expiration_year": 24,
    "name_on_card": "Jane Smith",
    "nickname": "Jane's VISA",
    "custom_data": {
      "PsNoXknreypo": "4rOeMclf8[jKw_(KTFAi90/{",
      "gkKvCqhyguAV": 48,
      "IRyCNJUefYQG": false
    },
    "created_on": "1981-10-05T11:42:15.699Z",
    "last_updated_on": "2004-09-25T18:53:06.257Z",
    "par": "UPToHiruBRRqFENFhtNlooJBkQQRh",
    "customer_key": "CWSWHENzRgmIVbefL"
  },
  "cardsavr_account": {
    "id": 380331212,
    "last_password_update": "1985-10-06T17:15:33.484Z",
    "last_saved_card": "1990-12-06T13:00:27.897Z",
    "created_on": "2011-11-25T13:13:55.892Z",
    "last_updated_on": "2021-05-16T11:19:39.770Z",
    "customer_key": "AtFnWeUKKMxmOVsOIdlJleoWU"
  },
  "credential_timeout": 272570080
}
```

### Path

GET /place_card_on_single_site_jobs **(batch)** or GET /place_card_on_single_site_jobs/:id **(singular)**

### Description

Returns the single-site job specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable single-site jobs, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- cardholder_ids
- card_ids
- account_ids
- status
- status_include / status_exclude
- termination_type
- termination_types_include / termination_types_exclude
- notification_sent
- time_elapsed_min / time_elapsed_max
- started_on_min / started_on_max
- completed_on_min / completed_on_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/place_card_on_single_site_jobs?ids=1,2`

#### Singular GET requests

**Singular requests** only return the single-site job matching the id provided in the path.

**Example GET request path:**<br>`/place_card_on_single_site_jobs/750836597`

To hydrate all credential requests currently associated with a job, include credential_requests in the hydration header (see example at right).`

### <a name="response-place_card_on_single_site_job"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this job.
card_id | number (fk) [cards](#cards) | ID of card associated with this job.
status | string | Current status of job (e.g. pending_tfa). These names are dynamic and change frequently, so it is best to use status_message to communicate with cardholders.
status_message | string | Human readable representation of the job's status.
termination_type | string | Final termination status of a job. (BILLABLE, SITE_INTERACTION_FAILURE, USER_DATA_FAILURE, PROCESS FAILURE)
custom_data | object | 
notification_sent | boolean | Indicates if a notification has been sent or posted for this job.
time_elapsed | number | Amount of time elapsed since the creation of the job.
auth_percent_complete | number | 
percent_complete | number | 
started_on | date | Time when job started.
completed_on | date | Timestamp of job completion.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
use_puppeteer | boolean | whether or not the VBS will use puppeteer instead of playwright.
cardholder_id | number (fk) [cardholders](#cardholders) | ID of cardholder associated with this job.
account_id | number (fk) [accounts](#accounts) | ID of account associated with this job.
credential_timeout | number | Credential timeout value in seconds.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create single-site job

```javascript
const singlesitejob = await session.createSingleSiteJob({
  "cardholder_id": 1303525921,
  "card_id": 503984253,
  "account_id": 480054694,
  "status": "CANCELLED",
  "custom_data": {
    "JMlLIhHrMqOl": "Grc7r(TKWRuTX0qgm7Vc",
    "XmyODUFRqdVz": 80,
    "ecPtHWTuRFXn": false
  },
  "notification_sent": false,
  "time_elapsed": 488741644,
  "credential_timeout": 272570080,
  "auth_percent_complete": 56642461,
  "percent_complete": 818184615,
  "started_on": "1981-12-19T21:43:37.659Z",
  "completed_on": "1992-08-02T10:50:19.487Z",
  "use_puppeteer": true
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1303525921 },
	{ "card_id", 503984253 },
	{ "account_id", 480054694 },
	{ "status", "CANCELLED" },
	{ "notification_sent", false },
	{ "time_elapsed", 488741644 },
	{ "credential_timeout", 272570080 },
	{ "auth_percent_complete", 56642461 },
	{ "percent_complete", 818184615 },
	{ "started_on", "1981-12-19T21:43:37.659Z" },
	{ "completed_on", "1992-08-02T10:50:19.487Z" },
	{ "use_puppeteer", true }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1303525921 )
	.add("card_id", 503984253 )
	.add("account_id", 480054694 )
	.add("status", "CANCELLED" )
	.add("notification_sent", false )
	.add("time_elapsed", 488741644 )
	.add("credential_timeout", 272570080 )
	.add("auth_percent_complete", 56642461 )
	.add("percent_complete", 818184615 )
	.add("started_on", "1981-12-19T21:43:37.659Z" )
	.add("completed_on", "1992-08-02T10:50:19.487Z" )
	.add("use_puppeteer", true )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1303525921,\"card_id\":503984253,\"account_id\":480054694,\"status\":\"CANCELLED\",\"custom_data\":{\"JMlLIhHrMqOl\":\"Grc7r(TKWRuTX0qgm7Vc\",\"XmyODUFRqdVz\":80,\"ecPtHWTuRFXn\":false},\"notification_sent\":false,\"time_elapsed\":488741644,\"credential_timeout\":272570080,\"auth_percent_complete\":56642461,\"percent_complete\":818184615,\"started_on\":\"1981-12-19T21:43:37.659Z\",\"completed_on\":\"1992-08-02T10:50:19.487Z\",\"use_puppeteer\":true}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/
```

### Path

POST /place_card_on_single_site_jobs

### Description

Create a single-site job and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.



<aside class="notice"><a href=#request-hydration-on-post>Request hydration</a> can be used on this endpoint. This allows you to create a new single-site job and all referential entities in a single POST request.
</aside>

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cardholder_id | number | yes | ID of cardholder associated with this job.
card_id | number | yes | ID of card associated with this job.
account_id | number | yes | ID of account associated with this job.
status | [string enum](#post-place_card_on_single_site_job-1)* | no | Current status of job (e.g. pending_tfa). These names are dynamic and change frequently, so it is best to use status_message to communicate with cardholders.
custom_data | object | no | 
notification_sent | boolean | no | Indicates if a notification has been sent or posted for this job.
time_elapsed | number | no | Amount of time elapsed since the creation of the job.
credential_timeout | number | no | Credential timeout value in seconds.
auth_percent_complete | number | no | 
percent_complete | number | no | 
started_on | date | no | Time when job started.
completed_on | date | no | Timestamp of job completion.
use_puppeteer | boolean | no | whether or not the VBS will use puppeteer instead of playwright.

See [single-site job response attributes](#response-place_card_on_single_site_job).

#### <a name="post-place_card_on_single_site_job-1"></a>string enum*
- INITIATED
- REQUESTED
- IN_PROGRESS
- AUTH
- LOGIN_SUBMITTED
- CREDS_RECEIVED
- TFA_CODE_RECEIVED
- TFA_SUBMITTED
- SUBMITTED
- PENDING_NEWCREDS
- PENDING_TFA
- PENDING
- UPDATING
- QUEUED
- SITE_BLOCKED
- CANCEL_REQUESTED
- CANCELLED
- CANCELLED_QUICKSTART
- JOB_RECORD_DELETED
- ABANDONED
- ABANDONED_QUICKSTART
- KILLED
- ACCOUNT_SETUP_INCOMPLETE
- ACCOUNT_NOT_SUPPORTED
- TFA_NOT_SUPPORTED
- PREPAID_ACCOUNT
- INACTIVE_ACCOUNT
- MISSING_CARD_DATA
- CARD_FORM_FAILED
- UNEXPECTED_ERROR
- INVALID_CARD_DETAILS
- INVALID_CARD_TYPE
- MULTI_ACCOUNT_CARD_NOT_ALLOWED
- INVALID_ADDRESS
- PASSWORD_RESET_REQUIRED
- BUNDLED_SUBSCRIPTION
- FREE_ACCOUNT
- ACCOUNT_LOCKED
- INVALID_EXPIRATION_DATE
- EXPIRED_CARD
- INVALID_CVV
- INVALID_NETWORK
- MAX_LIMIT_OF_STORED_CARDS
- PAYMENT_PROCESSOR_DOWN
- DUPLICATE_CARD
- TEST_COMPLETE_SUCCESS
- SUCCESSFUL
- UNSUPPORTED_CAPTCHA
- TIMEOUT_CAPTCHA
- TIMEOUT_CREDENTIALS
- MISSING_CREDENTIALS
- TIMEOUT_TFA
- TOO_MANY_LOGIN_FAILURES
- TOO_MANY_TFA_FAILURES
- TOO_MANY_OTP_FAILURES
- INVALID_SECURITY_ANSWERS
- INVALID_CREDENTIAL_REQUEST_TYPE
- UNSUCCESSFUL
- PROXY_PROBE_FAILED
- VBS_TIMEOUT
- VBS_ERROR
- UNKNOWN_INTERFACE_TYPE
- UNIMPLEMENTED_JOB_TYPE
- UNKNOWN_JOB_TYPE
- INTERNAL_ERROR
- ACCOUNT_NOT_FOUND
- MERCHANT_SECURITY_NOT_IMPLEMENTED
- MERCHANT_PROCESSOR_NOT_IMPLEMENTED
- WALLET_PROCESSOR_NOT_IMPLEMENTED

#### <a name="post-place_card_on_single_site_job-2"></a>string enum**
- USER_DATA_FAILURE
- PROCESS_FAILURE
- SITE_INTERACTION_FAILURE
- BILLABLE
- NEVER_STARTED

<aside class="notice">Update calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Update single-site job

```javascript
const singlesitejob = await session.updateSingleSiteJob(1,{
  "card_id": 401740834,
  "status": "INVALID_SECURITY_ANSWERS",
  "custom_data": {
    "LcRGycCzblbO": "+Sp4Fab7)(hM=IrX=Vb^YL",
    "pWbfpuayjBXp": 71,
    "fYlfJCCskVCH": false
  },
  "notification_sent": true,
  "time_elapsed": 1792363815,
  "auth_percent_complete": 1190904038,
  "percent_complete": 1842028782,
  "started_on": "2019-04-03T02:53:22.522Z",
  "completed_on": "1978-09-26T09:06:54.052Z",
  "use_puppeteer": false
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 401740834 },
	{ "status", "INVALID_SECURITY_ANSWERS" },
	{ "notification_sent", true },
	{ "time_elapsed", 1792363815 },
	{ "auth_percent_complete", 1190904038 },
	{ "percent_complete", 1842028782 },
	{ "started_on", "2019-04-03T02:53:22.522Z" },
	{ "completed_on", "1978-09-26T09:06:54.052Z" },
	{ "use_puppeteer", false }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 401740834 )
	.add("status", "INVALID_SECURITY_ANSWERS" )
	.add("notification_sent", true )
	.add("time_elapsed", 1792363815 )
	.add("auth_percent_complete", 1190904038 )
	.add("percent_complete", 1842028782 )
	.add("started_on", "2019-04-03T02:53:22.522Z" )
	.add("completed_on", "1978-09-26T09:06:54.052Z" )
	.add("use_puppeteer", false )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":401740834,\"status\":\"INVALID_SECURITY_ANSWERS\",\"custom_data\":{\"LcRGycCzblbO\":\"+Sp4Fab7)(hM=IrX=Vb^YL\",\"pWbfpuayjBXp\":71,\"fYlfJCCskVCH\":false},\"notification_sent\":true,\"time_elapsed\":1792363815,\"auth_percent_complete\":1190904038,\"percent_complete\":1842028782,\"started_on\":\"2019-04-03T02:53:22.522Z\",\"completed_on\":\"1978-09-26T09:06:54.052Z\",\"use_puppeteer\":false}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/750836597
```

### Path

PUT /place_card_on_single_site_jobs OR /place_card_on_single_site_jobs/{id}

### Description

Update a single-site job and return the updated object.  An id is required on every update request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
card_id | number | ID of card associated with this job.
status | [string enum](#post-place_card_on_single_site_job-1)* | Current status of job (e.g. pending_tfa). These names are dynamic and change frequently, so it is best to use status_message to communicate with cardholders.
custom_data | object | 
notification_sent | boolean | Indicates if a notification has been sent or posted for this job.
time_elapsed | number | Amount of time elapsed since the creation of the job.
auth_percent_complete | number | 
percent_complete | number | 
started_on | date | Time when job started.
completed_on | date | Timestamp of job completion.
use_puppeteer | boolean | whether or not the VBS will use puppeteer instead of playwright.

See [single-site job response parameters](#response-place_card_on_single_site_job).

<aside class="notice">Update calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete single-site job

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/750836597
```

```javascript
await session.deleteSingleSiteJob(undefined);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(undefined);
```

```java
JsonValue singlesitejob = session.delete("/place_card_on_single_site_jobs", undefined, null);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [single-site job response parameters](#response-place_card_on_single_site_job).

