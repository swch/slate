
# Accounts
Account objects contain the account information, such as username and password, for a particular cardhoder. They are used to log in to a cardholder's account for placing a payment card.
## Get account

```javascript
const accounts = await session.getAccounts(2099246402,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","merchant_site","cardsavr_card"])});
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
JsonArray response = (JsonArray)session.get(2099246402, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2099246402,
  "last_password_update": "1982-08-10T18:26:33.747Z",
  "last_saved_card": "1992-07-13T04:17:16.429Z",
  "created_on": "2010-10-09T14:45:36.564Z",
  "last_updated_on": "2002-03-21T00:39:05.830Z",
  "cardholder": {
    "id": 794983310,
    "type": "persistent_all",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "mMQlpBcvfbaamltijvMWzvKjkC",
    "webhook_url": "bGWUVirOAMcQypVHGbyMVlhGRr",
    "custom_data": {
      "cFkrRXaZiwHN": "&A3f/o",
      "zozhqmnXzVPb": 95,
      "MLTkEMhdGrFK": true
    },
    "created_on": "1998-01-18T22:22:37.274Z",
    "last_updated_on": "1982-07-29T06:41:26.125Z",
    "cuid": "IdteUWdnBboMWZxMmvWpgyiEOA"
  },
  "merchant_site": {
    "id": 587182395,
    "name": "Amazon",
    "note": "bXWhFRYPNWjHfisRfNAFuXRlmTECA",
    "host": "amazon.com",
    "tags": [
      "VZjy^tMX12l7a$3)1dUop[Sh",
      9,
      "S,UR_PD[p%AOb=[5ld/.i3Z-"
    ],
    "interface_type": "dcs",
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
    "script_directory": "GLDOsTQiO",
    "record_final_site_artifacts": true,
    "puppeteer_screenshot": true,
    "login_page": "https://www.merchantsite.com/login",
    "forgot_password_page": "https://www.merchantsite.com/forgot_password",
    "credit_card_page": "https://www.merchantsite.com/credit_card",
    "wallet_page": "iwHZAGFN",
    "merchant_sso_group": "vsYOqQ",
    "tier": 285440939
  },
  "cardsavr_card": {
    "id": 1271838559,
    "type": "Visa",
    "expiration_month": 12,
    "expiration_year": 24,
    "name_on_card": "Jane Smith",
    "nickname": "Jane's VISA",
    "custom_data": {
      "WQCNFRAyWKxZ": "B)kwcLDiu[@U(5U8[",
      "beXixQvJfSIs": 20,
      "udIRZvQbfoVg": false
    },
    "created_on": "1999-02-18T14:10:20.898Z",
    "last_updated_on": "1980-11-16T20:18:24.487Z",
    "par": "cbOORgsSGzjchdLevuetSBcLtdyaA",
    "customer_key": "abEiLBUVMYelsqthiWbehWz"
  },
  "customer_key": "euuCtwssVeMQpQOPNMagZynLBGJsRpW"
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

**Example GET request path:**<br>`/cardsavr_accounts/2099246402`

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
  "cardholder_id": 109220318,
  "merchant_site_id": 213606053,
  "customer_key": "euuCtwssVeMQpQOPNMagZynLBGJsRpW",
  "last_card_placed_id": 1307115325,
  "account_link": {
    "username": "jsmith123",
    "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 109220318 },
	{ "merchant_site_id", 213606053 },
	{ "customer_key", "euuCtwssVeMQpQOPNMagZynLBGJsRpW" },
	{ "last_card_placed_id", 1307115325 }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 109220318 )
	.add("merchant_site_id", 213606053 )
	.add("customer_key", "euuCtwssVeMQpQOPNMagZynLBGJsRpW" )
	.add("last_card_placed_id", 1307115325 )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":109220318,\"merchant_site_id\":213606053,\"customer_key\":\"euuCtwssVeMQpQOPNMagZynLBGJsRpW\",\"last_card_placed_id\":1307115325,\"account_link\":{\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}}"
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
  "last_card_placed_id": 87528087,
  "account_link": {
    "username": "jsmith123",
    "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
  }
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 87528087 }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 87528087 )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":87528087,\"account_link\":{\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/2099246402
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
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/2099246402
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
const addresses = await session.getAddresses(1070482522,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder"])});
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
JsonArray response = (JsonArray)session.get(1070482522, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1070482522,
  "address1": "mtdWHceZUnHrayxokeGsMcCDZtDGvMFLvNyCEYUPRJbRFIyOGlwQNGmbVevDbaWNnYmhnMkQsXjSufIeUoYnSBZvUUNMdBRIFsy",
  "address2": "JdLOLrWMcRmvTuRiDFhUhjBVYaySwhPUDFZNvNnfrMOWQXeyGUOybiyYazzXHldhmtgIpCHQVBJGbEyOlggvkeVJUJvbjdQkxQn",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "nLwUVEKmSsmd@cfYmUo.BSr",
  "phone_number": "2065555555",
  "created_on": "1991-12-27T07:03:58.074Z",
  "last_updated_on": "1996-11-28T03:37:00.646Z",
  "cardholder": {
    "id": 400555945,
    "type": "persistent_creds",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "dCeMKWO",
    "webhook_url": "oeuIhQa",
    "custom_data": {
      "xDvevsFRkcVz": "-+y1{Zc",
      "XzLFaxNUzeuW": 71,
      "nrNimMqrYLtR": true
    },
    "created_on": "2010-09-28T00:10:38.423Z",
    "last_updated_on": "2018-07-16T04:03:45.720Z",
    "cuid": "tnipGuJbQySUjGYEHgcqHFOdR"
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

**Example GET request path:**<br>`/cardsavr_addresses/1070482522`

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
  "cardholder_id": 1536462572,
  "address1": "mtdWHceZUnHrayxokeGsMcCDZtDGvMFLvNyCEYUPRJbRFIyOGlwQNGmbVevDbaWNnYmhnMkQsXjSufIeUoYnSBZvUUNMdBRIFsy",
  "address2": "JdLOLrWMcRmvTuRiDFhUhjBVYaySwhPUDFZNvNnfrMOWQXeyGUOybiyYazzXHldhmtgIpCHQVBJGbEyOlggvkeVJUJvbjdQkxQn",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "nLwUVEKmSsmd@cfYmUo.BSr",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1536462572 },
	{ "address1", "mtdWHceZUnHrayxokeGsMcCDZtDGvMFLvNyCEYUPRJbRFIyOGlwQNGmbVevDbaWNnYmhnMkQsXjSufIeUoYnSBZvUUNMdBRIFsy" },
	{ "address2", "JdLOLrWMcRmvTuRiDFhUhjBVYaySwhPUDFZNvNnfrMOWQXeyGUOybiyYazzXHldhmtgIpCHQVBJGbEyOlggvkeVJUJvbjdQkxQn" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "nLwUVEKmSsmd@cfYmUo.BSr" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1536462572 )
	.add("address1", "mtdWHceZUnHrayxokeGsMcCDZtDGvMFLvNyCEYUPRJbRFIyOGlwQNGmbVevDbaWNnYmhnMkQsXjSufIeUoYnSBZvUUNMdBRIFsy" )
	.add("address2", "JdLOLrWMcRmvTuRiDFhUhjBVYaySwhPUDFZNvNnfrMOWQXeyGUOybiyYazzXHldhmtgIpCHQVBJGbEyOlggvkeVJUJvbjdQkxQn" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "nLwUVEKmSsmd@cfYmUo.BSr" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1536462572,\"address1\":\"mtdWHceZUnHrayxokeGsMcCDZtDGvMFLvNyCEYUPRJbRFIyOGlwQNGmbVevDbaWNnYmhnMkQsXjSufIeUoYnSBZvUUNMdBRIFsy\",\"address2\":\"JdLOLrWMcRmvTuRiDFhUhjBVYaySwhPUDFZNvNnfrMOWQXeyGUOybiyYazzXHldhmtgIpCHQVBJGbEyOlggvkeVJUJvbjdQkxQn\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"nLwUVEKmSsmd@cfYmUo.BSr\",\"phone_number\":\"2065555555\"}"
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
- canada
- Canada
- USA


## Update address

```javascript
const address = await session.updateAddress(1,{
  "address1": "dXjJhtykEEZNDAXCbgBAMTsXuWtRfrsNtMdRsplcCLFfvlzxrRuUfZwmbArVSOofqSIQaKbxoMftuPmVCBeKiosqwKMRzQjSuNX",
  "address2": "QaUyqBPONsmBDfiWpnIycgAURiNNTOzOVqXXEgqmqqgKFrVGtxOCDFYlPtcLrLKTQYlKZAWuIwMjuDkaEPHsgjMuMMagFBGtniG",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "ievvftldACZl@RZvVDI.aYh",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "dXjJhtykEEZNDAXCbgBAMTsXuWtRfrsNtMdRsplcCLFfvlzxrRuUfZwmbArVSOofqSIQaKbxoMftuPmVCBeKiosqwKMRzQjSuNX" },
	{ "address2", "QaUyqBPONsmBDfiWpnIycgAURiNNTOzOVqXXEgqmqqgKFrVGtxOCDFYlPtcLrLKTQYlKZAWuIwMjuDkaEPHsgjMuMMagFBGtniG" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "ievvftldACZl@RZvVDI.aYh" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "dXjJhtykEEZNDAXCbgBAMTsXuWtRfrsNtMdRsplcCLFfvlzxrRuUfZwmbArVSOofqSIQaKbxoMftuPmVCBeKiosqwKMRzQjSuNX" )
	.add("address2", "QaUyqBPONsmBDfiWpnIycgAURiNNTOzOVqXXEgqmqqgKFrVGtxOCDFYlPtcLrLKTQYlKZAWuIwMjuDkaEPHsgjMuMMagFBGtniG" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", false )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "ievvftldACZl@RZvVDI.aYh" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"dXjJhtykEEZNDAXCbgBAMTsXuWtRfrsNtMdRsplcCLFfvlzxrRuUfZwmbArVSOofqSIQaKbxoMftuPmVCBeKiosqwKMRzQjSuNX\",\"address2\":\"QaUyqBPONsmBDfiWpnIycgAURiNNTOzOVqXXEgqmqqgKFrVGtxOCDFYlPtcLrLKTQYlKZAWuIwMjuDkaEPHsgjMuMMagFBGtniG\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"ievvftldACZl@RZvVDI.aYh\",\"phone_number\":\"2065555555\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1070482522
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1070482522
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
const bins = await session.getBins(464372615,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(464372615, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 464372615,
  "custom_data": {
    "nxjRbqPmEpCK": "(m(^]Z~718_PcR",
    "HPKJSNegZQdo": 47,
    "EoTOeJCouBue": false
  },
  "created_on": "2014-05-18T17:41:50.254Z",
  "last_updated_on": "1975-04-26T12:56:23.783Z",
  "financial_institution": {
    "id": 1889423262,
    "name": "JhnPBTjPIKKZaZPRRsmPExyAytLzialIwWGehdUBQMxCdfTRRnXqRpELZhvtTQM",
    "description": "oNkXtxouwwITsxjFJxIAiWyBMuZG",
    "lookup_key": "iKWcWQqYBOOOamIAOmudawELockfMRvnSCNYKdTKfbcRsOyasmDKXBbCmGEYHtB",
    "alternate_lookup_key": "IFTxnCTiIQgOCrBftpNaRMUNNiwRjfdEUlDuMmnIqBjMVpJblzGVRTPOpCqkKVW",
    "last_activity": "1971-08-30T18:30:35.177Z",
    "created_on": "2003-10-14T04:27:03.658Z",
    "last_updated_on": "2018-10-06T19:10:21.629Z"
  },
  "bank_identification_number": "46368723"
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

**Example GET request path:**<br>`/cardsavr_bins/464372615`

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
  "financial_institution_id": 1140241523,
  "bank_identification_number": "46368723",
  "custom_data": {
    "nxjRbqPmEpCK": "(m(^]Z~718_PcR",
    "HPKJSNegZQdo": 47,
    "EoTOeJCouBue": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1140241523 },
	{ "bank_identification_number", "46368723" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1140241523 )
	.add("bank_identification_number", "46368723" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1140241523,\"bank_identification_number\":\"46368723\",\"custom_data\":{\"nxjRbqPmEpCK\":\"(m(^]Z~718_PcR\",\"HPKJSNegZQdo\":47,\"EoTOeJCouBue\":false}}"
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
  "financial_institution_id": 1421396091,
  "custom_data": {
    "bdIWJatdXGbr": "t&{8Ql+M,K^W[F%^",
    "CdbVaeRmEcYB": 89,
    "ikRYAiYPjcqa": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1421396091 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1421396091 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1421396091,\"custom_data\":{\"bdIWJatdXGbr\":\"t&{8Ql+M,K^W[F%^\",\"CdbVaeRmEcYB\":89,\"ikRYAiYPjcqa\":true}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/464372615
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/464372615
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
const cardplacementresults = await session.getCardPlacementResults(706136488,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution","merchant_site","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(706136488, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 706136488,
  "merchant_site_hostname": "bqrdxjthYXBcDYmnQqLlCLoiVxHwqmZlVbrgUlAGuCAPdQeyouOtzxyZPPHOCSWMAvUFlKPIWzximEZTYRnmfjbFucFPuVQGdSTVDszxlVIYjbuxiFxPYCiTckIEeFRqhMzpvxQQGQQmsIYBLNhPQdGXaWbyNRUkCHaCjIPvSrzrCQrMIDUDWuoxzbVkqzhZfJUSIvayYXKHVkTqQebuDxlJPZMIwVqoNLTeqkgkcaIdGvyZdxmojcIUgvcKCl",
  "meta_key": "MB9810411",
  "fi_name": "IHxLHlraLNQOxQhkCduwlLtaTRfSUXygfTBlrSzDdGKzpepgfkaLLxfQACrOISw",
  "bank_identification_number": "27944068",
  "cuid": "vReOTmSSdjwpYjiH",
  "par": "PnLzytaRWWNZrYVopAEViznAYrMNw",
  "card_customer_key": "WUSzTWDnBcif",
  "account_customer_key": "jjElqxxFsQnKbQkAqgXxAlQRlsY",
  "status": "SUCCESSFUL",
  "status_message": "Successful",
  "termination_type": "BILLABLE",
  "custom_data": {
    "MYvQDQBLRQiF": "IOGat8#X6f]~bVfDS$./",
    "BOTaptIwELMd": 80,
    "jYbUgPCqIOcP": false
  },
  "time_elapsed": 1868968112,
  "first_6": "eMpJrjHugEMUlnTtMAYoklhhwUesMMiP",
  "first_7": "rTKJebNgtqEuLxlDiGxqXeusrFSwcRpr",
  "first_8": "VNwzXMsPjSnwvrqJhBRthaZdJvcQhHIx",
  "trace": "zCFtW",
  "email_sent": true,
  "completed_on": "1970-07-17T00:23:48.628Z",
  "created_on": "2003-05-28T15:40:19.755Z",
  "last_updated_on": "1985-06-27T05:42:25.063Z",
  "financial_institution": {
    "id": 102432428,
    "name": "ztJZcNOhWPVYlkaatiCnUgQMmcwvkXuVjFIwBHThkamkwdGVmiTELwXaZIkHUKS",
    "description": "DawsbFgQEemm",
    "lookup_key": "ZnjbcbEiYpCZvYjgbNVbiJpNssWkZGBzlmoksDufAJXYLepqQxgyIRlRfhiaqKX",
    "alternate_lookup_key": "NtwKEQZmytYhiTOLtQuQyOKMQttwYZPfsYgfIjXoRtQMBGPugCmACebNQnFEQvd",
    "last_activity": "1982-12-06T02:08:51.946Z",
    "created_on": "1973-07-23T07:14:31.353Z",
    "last_updated_on": "1986-02-11T16:24:24.147Z"
  },
  "merchant_site": {
    "id": 1607972791,
    "name": "Amazon",
    "note": "fqKUczEfzMTxb",
    "host": "amazon.com",
    "tags": [
      "2[~1%b,bk^p5t~/SZWLoIi_E=~4",
      46,
      "iQT,"
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
    "script_directory": "csnHpAUlKfmNaHqGCvjeFC",
    "record_final_site_artifacts": false,
    "puppeteer_screenshot": false,
    "login_page": "https://www.merchantsite.com/login",
    "forgot_password_page": "https://www.merchantsite.com/forgot_password",
    "credit_card_page": "https://www.merchantsite.com/credit_card",
    "wallet_page": "csPLkdZsQEOllMklgmmYdW",
    "merchant_sso_group": "dZNcYiIgdiBtPasJMmrULKkLmBJYp",
    "tier": 1666387060
  },
  "cardsavr_bin": {
    "id": 503152339,
    "custom_data": {
      "tchZgbVKCgyM": "Tu$n/LB$MeoG#+$@$!rYLd",
      "gpaopksWjAvL": 77,
      "KidlimseQrCK": true
    },
    "created_on": "1972-09-07T02:45:39.598Z",
    "last_updated_on": "2022-03-02T21:21:09.281Z",
    "bank_identification_number": "59702270"
  },
  "place_card_on_single_site_job_id": 40066451
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
- email_sent
- completed_on_min / completed_on_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/card_placement_results?ids=1,2`

#### Singular GET requests

**Singular requests** only return the card placement result matching the id provided in the path.

**Example GET request path:**<br>`/card_placement_results/706136488`

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
email_sent | boolean | 
completed_on | date | 
created_on | date | Date this job result was created on
last_updated_on | date | Date this job result was last updated on
place_card_on_single_site_job_id | number | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

# Cards
A card object contains information about a payment card for a specific cardholder. Card objects are used to populate payment information on merchant sites.
## Get card

```javascript
const cards = await session.getCards(847069282,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_address","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(847069282, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 847069282,
  "type": "American Express",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "OPipkjdCdCWk": "M5sFC+SJ.L3ODF2YQT,}W*j8bHX",
    "HPMMGhIZhXwd": 50,
    "yBGrqMksnPVQ": false
  },
  "created_on": "2019-01-03T20:25:07.325Z",
  "last_updated_on": "2000-11-21T11:02:40.460Z",
  "cardholder": {
    "id": 1004134286,
    "type": "ephemeral",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "PwyWTSCPPi",
    "webhook_url": "jAvTUDByvzkPAaoGsFzVIosdPQNkCy",
    "custom_data": {
      "viDfjDyknuaC": "tc[59O,K)RTnS&aCqd.u3",
      "ITWYScRBbPDc": 37,
      "KJSarBhZEbgE": true
    },
    "created_on": "2009-06-04T00:28:16.604Z",
    "last_updated_on": "2017-04-03T20:48:06.354Z",
    "cuid": "zkBThJlQGSAK"
  },
  "cardsavr_address": {
    "id": 691432632,
    "address1": "CKPDmvGfQVSXtJuKQxHlTliLrDTpjYiHeVRkGAfodLFYlVhnlLusZUdRbVQlEgPCDgrZWRfYSIQurlWXBzCyxMrUQDQuYumUpDU",
    "address2": "NeFUpbcJKDcjgAuPRcMDHiybnVAEcLWNDyfFJSZiXCQqqGFaeVgQTZpfBJJvuHigRIFXsrDKmvDgnBiSKrpPgLHnZMfRHSiJYDj",
    "city": "Seattle",
    "subnational": "WA",
    "postal_code": "98177",
    "postal_other": "98177-0124",
    "country": "USA",
    "is_primary": false,
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "KBolCrTOzkXj@HUZmzZ.dAk",
    "phone_number": "2065555555",
    "created_on": "1995-11-11T16:28:51.714Z",
    "last_updated_on": "1998-03-04T11:08:57.807Z"
  },
  "cardsavr_bin": {
    "id": 1448955557,
    "custom_data": {
      "CxhpUJwnGUuz": "Ab.~J#Tq83+_v4",
      "yagnrNulLPOE": 95,
      "xJlwGpYLfIIF": false
    },
    "created_on": "1982-04-11T19:48:29.128Z",
    "last_updated_on": "1970-11-05T01:37:36.470Z",
    "bank_identification_number": "83509260"
  },
  "par": "ocKmsBGwPlfbypMdlBndBFsxXzxQS",
  "customer_key": "jhTzBPKEZQcTIHF"
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

**Example GET request path:**<br>`/cardsavr_cards/847069282`

### <a name="response-cardsavr_card"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this card.
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
address_id | number (fk) [addresses](#addresses) | ID of address associated with this card.
par | string | Unique Personal Account Reference number for this card, to be used for card lookup. Generated automatically from PAN, expiration date, and username if using the SDK.
customer_key | string | Unique customer reference for this card. A random number will be generated and returned if not provided

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create card

```javascript
const card = await session.createCard({
  "cardholder_id": 1947808003,
  "address_id": 777568517,
  "bin_id": 1966080863,
  "par": "ocKmsBGwPlfbypMdlBndBFsxXzxQS",
  "customer_key": "jhTzBPKEZQcTIHF",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "OPipkjdCdCWk": "M5sFC+SJ.L3ODF2YQT,}W*j8bHX",
    "HPMMGhIZhXwd": 50,
    "yBGrqMksnPVQ": false
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1947808003 },
	{ "address_id", 777568517 },
	{ "bin_id", 1966080863 },
	{ "par", "ocKmsBGwPlfbypMdlBndBFsxXzxQS" },
	{ "customer_key", "jhTzBPKEZQcTIHF" },
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
	.add("cardholder_id", 1947808003 )
	.add("address_id", 777568517 )
	.add("bin_id", 1966080863 )
	.add("par", "ocKmsBGwPlfbypMdlBndBFsxXzxQS" )
	.add("customer_key", "jhTzBPKEZQcTIHF" )
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
curl -d "{\"cardholder_id\":1947808003,\"address_id\":777568517,\"bin_id\":1966080863,\"par\":\"ocKmsBGwPlfbypMdlBndBFsxXzxQS\",\"customer_key\":\"jhTzBPKEZQcTIHF\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"Jane's VISA\",\"custom_data\":{\"OPipkjdCdCWk\":\"M5sFC+SJ.L3ODF2YQT,}W*j8bHX\",\"HPMMGhIZhXwd\":50,\"yBGrqMksnPVQ\":false}}"
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
expiration_month | string | yes | 
expiration_year | string | yes | 
name_on_card | string | yes | 
nickname | string | no | 
custom_data | object | no | Meta-data that can be added to the card if needed.

See [card response attributes](#response-cardsavr_card).

#### <a name="post-cardsavr_card-1"></a>string enum*
- Visa
- Mastercard
- American Express
- Unknown Type

<aside class="notice">Update calls to /cardsavr_cards require the cardholder's personal cardholder_safe_key header to encrypt and save the pan and cvv when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Upsert card

```javascript
const card = await session.updateCard(1,{
  "bin_id": 1350279616,
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "BFxhTXMQDGjS": "Rhb8DAU0@{x#p#O)o=fNxCCE",
    "sYaempfOYUVe": 32,
    "mABSOeQKQBCS": true
  },
  "pan": "4111111111111111"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "bin_id", 1350279616 },
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
	.add("bin_id", 1350279616 )
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
curl -d "{\"bin_id\":1350279616,\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"Jane's VISA\",\"custom_data\":{\"BFxhTXMQDGjS\":\"Rhb8DAU0@{x#p#O)o=fNxCCE\",\"sYaempfOYUVe\":32,\"mABSOeQKQBCS\":true},\"pan\":\"4111111111111111\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/847069282
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
bin_id | number | ID of BIN associated with this card.
cvv | string | 
expiration_month | string | 
expiration_year | string | 
name_on_card | string | 
nickname | string | 
custom_data | object | Meta-data that can be added to the card if needed.

See [card response parameters](#response-cardsavr_card).


## Delete card

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/847069282
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
const cardholders = await session.getCardholders(408803874,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution","integrator"])});
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
JsonArray response = (JsonArray)session.get(408803874, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 408803874,
  "type": "persistent_all",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "Bjv",
  "webhook_url": "TgvYSUUbYWmIko",
  "custom_data": {
    "XfcptZxPUBLV": "OW#F=xNpGbOnln8$f~1BXW",
    "TDbnCCdNVKMs": 7,
    "GtHpgftWNrUa": true
  },
  "created_on": "2010-05-07T03:07:07.491Z",
  "last_updated_on": "1989-02-25T07:06:43.510Z",
  "financial_institution": {
    "id": 1656483750,
    "name": "rKjkLmScJHYaFInXAgFwBImfgWxTXobjPFpxzWhdTRrSnzDIvizSTRqvLlhsfbf",
    "description": "mhKnZcWlQkhjNojkfKnrhuGVQAneTah",
    "lookup_key": "mbUheAOYMPiVwETPUwCfxzDDJgRmbuLtrKcSbnFvnZfEBktInRPVxpDsUUYUsYL",
    "alternate_lookup_key": "OEQakDfIwrGGGavLbOWUdlbCBebhtXNjhbSnYvFGYFasaDBPLIQgWJzwyHVvgpP",
    "last_activity": "2018-11-28T21:17:20.068Z",
    "created_on": "2019-11-12T01:22:24.317Z",
    "last_updated_on": "2007-10-30T20:55:34.971Z"
  },
  "integrator": {
    "id": 170898908,
    "name": "iHgrkuzKpQMsjFsLzOPGENroTOGUWhkKGTQkjodgDjPrULKxM",
    "description": "QGtJSjWyemGhzcoYsSucofXyiIK",
    "current_key": "DcjzeiFzDJqLNabxl5hE9MaLq/PrQIq9bf6wX9Iig14=",
    "key_lifetime": 10,
    "next_rotation_on": "2010-04-23T04:05:18.340Z",
    "created_on": "2018-10-16T04:49:15.079Z",
    "last_updated_on": "2009-12-07T00:04:56.804Z"
  },
  "cuid": "ygAl"
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

**Example GET request path:**<br>`/cardholders/408803874`

### <a name="response-cardholder"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this cardholder.
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | 
type | string | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities.  If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
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
  "cuid": "ygAl",
  "type": "persistent_all",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "Bjv",
  "webhook_url": "TgvYSUUbYWmIko",
  "custom_data": {
    "XfcptZxPUBLV": "OW#F=xNpGbOnln8$f~1BXW",
    "TDbnCCdNVKMs": 7,
    "GtHpgftWNrUa": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cuid", "ygAl" },
	{ "type", "persistent_all" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "Bjv" },
	{ "webhook_url", "TgvYSUUbYWmIko" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cuid", "ygAl" )
	.add("type", "persistent_all" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "Bjv" )
	.add("webhook_url", "TgvYSUUbYWmIko" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"cuid\":\"ygAl\",\"type\":\"persistent_all\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"Bjv\",\"webhook_url\":\"TgvYSUUbYWmIko\",\"custom_data\":{\"XfcptZxPUBLV\":\"OW#F=xNpGbOnln8$f~1BXW\",\"TDbnCCdNVKMs\":7,\"GtHpgftWNrUa\":true}}"
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
type | [string enum](#post-cardholder-1)* | no | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities.  If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
first_name | string | no | 
last_name | string | no | 
email | string | no | 
meta_key | string | no | Key used for billing record identification; automatically generated during card creation.
webhook_url | string | no | A cardholder specific url for posting job reults following the end of a session.  This overrides the FI global settiings in the portal.
custom_data | object | no | Additional data that can be added to the cardholder if needed.

See [cardholder response attributes](#response-cardholder).

#### <a name="post-cardholder-1"></a>string enum*
- ephemeral
- persistent_creds
- persistent_all


## Upsert cardholder

```javascript
const cardholder = await session.updateCardholder(1,{
  "type": "ephemeral",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "ei",
  "webhook_url": "uzbBfpWZVnrEJsXBLZrPMVnUwivC",
  "custom_data": {
    "DQQCRDZACvLK": "9VK^Af,%o-=IO1%tH!$vQ~!t+s",
    "NilKbBXWfDeh": 89,
    "yDUSkmzublHO": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "type", "ephemeral" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "ei" },
	{ "webhook_url", "uzbBfpWZVnrEJsXBLZrPMVnUwivC" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("type", "ephemeral" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "ei" )
	.add("webhook_url", "uzbBfpWZVnrEJsXBLZrPMVnUwivC" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"type\":\"ephemeral\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"ei\",\"webhook_url\":\"uzbBfpWZVnrEJsXBLZrPMVnUwivC\",\"custom_data\":{\"DQQCRDZACvLK\":\"9VK^Af,%o-=IO1%tH!$vQ~!t+s\",\"NilKbBXWfDeh\":89,\"yDUSkmzublHO\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/408803874
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
type | [string enum](#post-cardholder-1)* | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities.  If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
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
https://api.INSTANCE.cardsavr.io/cardholders/408803874
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
const users = await session.getUsers(920039694,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(920039694, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 920039694,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1972-05-15T00:16:59.314Z",
  "is_locked": false,
  "password_lifetime": 18,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "admin",
  "next_rotation_on": "1996-06-05T19:06:23.393Z",
  "created_on": "1977-04-22T12:27:47.821Z",
  "last_updated_on": "1977-10-04T07:29:19.255Z",
  "username": "jsmith123",
  "financial_institution": {
    "id": 71919296,
    "name": "CzqJSiieLnFJmtpRaJVjJpwRUZKLUFaRTZQZcXCGzzqCQHdBqiyWdChMeMqrJqJ",
    "description": "GXxBXuxQXyZr",
    "lookup_key": "vjPyTXgckHsOAdtTvTnVZAAFbVllXicuzKudpXGPnYFPxsFqUkgkgopiqTAvQpM",
    "alternate_lookup_key": "WwbkOIvihBewcAZrzhRsjhAvHqjgDiUNCjPgJqUGLIYSVNXlrWWYomJxkvcuZvu",
    "last_activity": "1997-11-08T23:07:36.077Z",
    "created_on": "1986-02-07T20:33:22.959Z",
    "last_updated_on": "1978-06-03T07:32:50.494Z"
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

**Example GET request path:**<br>`/cardsavr_users/920039694`

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
  "financial_institution_id": 659241943,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 18,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "admin",
  "next_rotation_on": "1996-06-05T19:06:23.393Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 659241943 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 18 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "admin" },
	{ "next_rotation_on", "1996-06-05T19:06:23.393Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 659241943 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 18 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "admin" )
	.add("next_rotation_on", "1996-06-05T19:06:23.393Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":659241943,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":18,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"admin\",\"next_rotation_on\":\"1996-06-05T19:06:23.393Z\"}"
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
financial_institution_id | number | no | 
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
  "financial_institution_id": 1176149886,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 300,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "admin",
  "next_rotation_on": "2013-05-16T01:22:01.353Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1176149886 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 300 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "admin" },
	{ "next_rotation_on", "2013-05-16T01:22:01.353Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1176149886 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 300 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "admin" )
	.add("next_rotation_on", "2013-05-16T01:22:01.353Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1176149886,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":300,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"admin\",\"next_rotation_on\":\"2013-05-16T01:22:01.353Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/920039694
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/920039694
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
const financialinstitutions = await session.getFinancialInstitutions(1156861128,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(1156861128, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1156861128,
  "name": "pSsalAqVjthqJDlZiTYjGuRezwtVAtImzqHkdWGwxcKrmKHZsTpPWRKwmyeFhSV",
  "description": "ZJbpovuZdQuimrbSbwkLOFbpqFF",
  "lookup_key": "dlLcXtmKUXpBeYUKHFggsQFhYOdTfdnfMzKJGAuxylLdRMRzpaEscBPbunjdLHd",
  "alternate_lookup_key": "sOcbMOoHpiiXvtHdjJaBHFTWpUUWnhKxviuVtDIGFhBruOYqDpfpKfsYAxZQmfa",
  "last_activity": "2023-02-07T06:43:16.814Z",
  "created_on": "1986-10-12T11:13:22.065Z",
  "last_updated_on": "2020-01-26T15:31:52.237Z"
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

**Example GET request path:**<br>`/financial_institutions/1156861128`

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
  "name": "pSsalAqVjthqJDlZiTYjGuRezwtVAtImzqHkdWGwxcKrmKHZsTpPWRKwmyeFhSV",
  "description": "ZJbpovuZdQuimrbSbwkLOFbpqFF",
  "lookup_key": "dlLcXtmKUXpBeYUKHFggsQFhYOdTfdnfMzKJGAuxylLdRMRzpaEscBPbunjdLHd",
  "alternate_lookup_key": "sOcbMOoHpiiXvtHdjJaBHFTWpUUWnhKxviuVtDIGFhBruOYqDpfpKfsYAxZQmfa"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "pSsalAqVjthqJDlZiTYjGuRezwtVAtImzqHkdWGwxcKrmKHZsTpPWRKwmyeFhSV" },
	{ "description", "ZJbpovuZdQuimrbSbwkLOFbpqFF" },
	{ "lookup_key", "dlLcXtmKUXpBeYUKHFggsQFhYOdTfdnfMzKJGAuxylLdRMRzpaEscBPbunjdLHd" },
	{ "alternate_lookup_key", "sOcbMOoHpiiXvtHdjJaBHFTWpUUWnhKxviuVtDIGFhBruOYqDpfpKfsYAxZQmfa" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "pSsalAqVjthqJDlZiTYjGuRezwtVAtImzqHkdWGwxcKrmKHZsTpPWRKwmyeFhSV" )
	.add("description", "ZJbpovuZdQuimrbSbwkLOFbpqFF" )
	.add("lookup_key", "dlLcXtmKUXpBeYUKHFggsQFhYOdTfdnfMzKJGAuxylLdRMRzpaEscBPbunjdLHd" )
	.add("alternate_lookup_key", "sOcbMOoHpiiXvtHdjJaBHFTWpUUWnhKxviuVtDIGFhBruOYqDpfpKfsYAxZQmfa" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"pSsalAqVjthqJDlZiTYjGuRezwtVAtImzqHkdWGwxcKrmKHZsTpPWRKwmyeFhSV\",\"description\":\"ZJbpovuZdQuimrbSbwkLOFbpqFF\",\"lookup_key\":\"dlLcXtmKUXpBeYUKHFggsQFhYOdTfdnfMzKJGAuxylLdRMRzpaEscBPbunjdLHd\",\"alternate_lookup_key\":\"sOcbMOoHpiiXvtHdjJaBHFTWpUUWnhKxviuVtDIGFhBruOYqDpfpKfsYAxZQmfa\"}"
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
  "name": "oUAHIYHGakCMpGnjkNxVEEuQApDvYpTYOCBOTHNSIqAvyNLNdXirGzZwjTNGLnK",
  "description": "xhgyVzApF",
  "lookup_key": "xQfIATpSWdDlbThFHdGOlEirgCacePcKpXJLpWbgOylHyJCaYCxYtWswfsPAeiP",
  "alternate_lookup_key": "vDpGNzDxsGRRLywaARvXoPefWcUpnxQYjnZbMGPZocTzWawphhhFNhRsBuGDnnX"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "oUAHIYHGakCMpGnjkNxVEEuQApDvYpTYOCBOTHNSIqAvyNLNdXirGzZwjTNGLnK" },
	{ "description", "xhgyVzApF" },
	{ "lookup_key", "xQfIATpSWdDlbThFHdGOlEirgCacePcKpXJLpWbgOylHyJCaYCxYtWswfsPAeiP" },
	{ "alternate_lookup_key", "vDpGNzDxsGRRLywaARvXoPefWcUpnxQYjnZbMGPZocTzWawphhhFNhRsBuGDnnX" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "oUAHIYHGakCMpGnjkNxVEEuQApDvYpTYOCBOTHNSIqAvyNLNdXirGzZwjTNGLnK" )
	.add("description", "xhgyVzApF" )
	.add("lookup_key", "xQfIATpSWdDlbThFHdGOlEirgCacePcKpXJLpWbgOylHyJCaYCxYtWswfsPAeiP" )
	.add("alternate_lookup_key", "vDpGNzDxsGRRLywaARvXoPefWcUpnxQYjnZbMGPZocTzWawphhhFNhRsBuGDnnX" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"oUAHIYHGakCMpGnjkNxVEEuQApDvYpTYOCBOTHNSIqAvyNLNdXirGzZwjTNGLnK\",\"description\":\"xhgyVzApF\",\"lookup_key\":\"xQfIATpSWdDlbThFHdGOlEirgCacePcKpXJLpWbgOylHyJCaYCxYtWswfsPAeiP\",\"alternate_lookup_key\":\"vDpGNzDxsGRRLywaARvXoPefWcUpnxQYjnZbMGPZocTzWawphhhFNhRsBuGDnnX\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/1156861128
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
https://api.INSTANCE.cardsavr.io/financial_institutions/1156861128
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
const integrators = await session.getIntegrators(1340638252,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(1340638252, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1340638252,
  "name": "aKgzuesUajyMWrayxbzuBRERwkdMeGznkhPXwYLDHoYpqaDep",
  "description": "WpBrfLT",
  "current_key": "IWw9xunfmbKizR7LOPumvJU4tUW1BsRR2m72E7W3ECs=",
  "key_lifetime": 290,
  "next_rotation_on": "2011-05-30T23:14:57.782Z",
  "created_on": "1989-11-17T23:59:26.340Z",
  "last_updated_on": "1984-12-02T22:47:39.056Z"
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

**Example GET request path:**<br>`/integrators/1340638252`

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
  "name": "aKgzuesUajyMWrayxbzuBRERwkdMeGznkhPXwYLDHoYpqaDep",
  "description": "WpBrfLT",
  "current_key": "IWw9xunfmbKizR7LOPumvJU4tUW1BsRR2m72E7W3ECs=",
  "key_lifetime": 290,
  "next_rotation_on": "2011-05-30T23:14:57.782Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "aKgzuesUajyMWrayxbzuBRERwkdMeGznkhPXwYLDHoYpqaDep" },
	{ "description", "WpBrfLT" },
	{ "current_key", "IWw9xunfmbKizR7LOPumvJU4tUW1BsRR2m72E7W3ECs=" },
	{ "key_lifetime", 290 },
	{ "next_rotation_on", "2011-05-30T23:14:57.782Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "aKgzuesUajyMWrayxbzuBRERwkdMeGznkhPXwYLDHoYpqaDep" )
	.add("description", "WpBrfLT" )
	.add("current_key", "IWw9xunfmbKizR7LOPumvJU4tUW1BsRR2m72E7W3ECs=" )
	.add("key_lifetime", 290 )
	.add("next_rotation_on", "2011-05-30T23:14:57.782Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"aKgzuesUajyMWrayxbzuBRERwkdMeGznkhPXwYLDHoYpqaDep\",\"description\":\"WpBrfLT\",\"current_key\":\"IWw9xunfmbKizR7LOPumvJU4tUW1BsRR2m72E7W3ECs=\",\"key_lifetime\":290,\"next_rotation_on\":\"2011-05-30T23:14:57.782Z\"}"
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
current_key | string | no | Current key for this integrator.
key_lifetime | number | no | Sets the duration of validity for integrator key.
next_rotation_on | date | no | Date of next key rotation for this integrator.

See [integrator response attributes](#response-integrator).


## Update integrator

```javascript
const integrator = await session.updateIntegrator(1,{
  "name": "HxQJpNAgMyXXRXTBrQaBdqjqwYoaAdklHsZAdfmVDDiCIASgk",
  "description": "sztkKsXDlsjjhGaPOIiycMCNAkXLJc",
  "current_key": "6oT/rU5eoyRZdHWOhfg+gSOqxfvBQ9TlDkLnYU4Trps=",
  "key_lifetime": 265,
  "next_rotation_on": "1972-12-15T02:49:01.873Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "HxQJpNAgMyXXRXTBrQaBdqjqwYoaAdklHsZAdfmVDDiCIASgk" },
	{ "description", "sztkKsXDlsjjhGaPOIiycMCNAkXLJc" },
	{ "current_key", "6oT/rU5eoyRZdHWOhfg+gSOqxfvBQ9TlDkLnYU4Trps=" },
	{ "key_lifetime", 265 },
	{ "next_rotation_on", "1972-12-15T02:49:01.873Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "HxQJpNAgMyXXRXTBrQaBdqjqwYoaAdklHsZAdfmVDDiCIASgk" )
	.add("description", "sztkKsXDlsjjhGaPOIiycMCNAkXLJc" )
	.add("current_key", "6oT/rU5eoyRZdHWOhfg+gSOqxfvBQ9TlDkLnYU4Trps=" )
	.add("key_lifetime", 265 )
	.add("next_rotation_on", "1972-12-15T02:49:01.873Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"HxQJpNAgMyXXRXTBrQaBdqjqwYoaAdklHsZAdfmVDDiCIASgk\",\"description\":\"sztkKsXDlsjjhGaPOIiycMCNAkXLJc\",\"current_key\":\"6oT/rU5eoyRZdHWOhfg+gSOqxfvBQ9TlDkLnYU4Trps=\",\"key_lifetime\":265,\"next_rotation_on\":\"1972-12-15T02:49:01.873Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/1340638252
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
https://api.INSTANCE.cardsavr.io/integrators/1340638252
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
const merchantsites = await session.getMerchantSites(1549102737,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(1549102737, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1549102737,
  "name": "Amazon",
  "note": "SQBBlsuQIlWKOYCQQXNRHQV",
  "host": "amazon.com",
  "tags": [
    ".earZ0jFG8iw$D=tjgb(MmZ+S,OlLRY.",
    20,
    ",/VjNc)-0YjYU1&AfwDuKgD"
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
  "script_directory": "tkXXlyNafScTkBfmalGQzKBZee",
  "record_final_site_artifacts": true,
  "puppeteer_screenshot": false,
  "login_page": "https://www.merchantsite.com/login",
  "forgot_password_page": "https://www.merchantsite.com/forgot_password",
  "credit_card_page": "https://www.merchantsite.com/credit_card",
  "wallet_page": "ZXXpINwSvfxVCeknOOu",
  "merchant_sso_group": "GJhDSpBJQXges",
  "tier": 568096015
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

**Example GET request path:**<br>`/merchant_sites/1549102737`

### <a name="response-merchant_site"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this merchant site.
name | string | 
note | string | Human-readable note about the site for developers
host | string | For interface type 'dcs',  hostname of the DCS broker server for the merchant site; for interface type 'vbs' hostname of the merchant_site. e.g. amazon.com
tags | array | Tags for filtering desired merchant sites.  This could either be site status (e.g. prod, development), countries supported (e.g. usa, canada), or site attributes (e.g. synthetic).  Tags can also be compounded to create combinations: (e.g. ?tags=prod,usa&tags=synthetic means all sites tagged prod and usa as well as sites tagged synthetic)
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

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

# Notifications
Notification objects define a set of actions to be triggered by certain CardSavr events, such as session completion.
## Get notification

```javascript
const notifications = await session.getNotifications(780353289,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(780353289, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 780353289,
  "name": "Sample Notification",
  "type": "webhook",
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
  "html_template": "gMJynUPAazkeIJmmIbRyCUspYz",
  "text_template": "vtyQPSsP",
  "created_on": "1973-11-19T18:24:54.210Z",
  "last_updated_on": "2023-03-22T02:02:00.279Z",
  "financial_institution": {
    "id": 305272525,
    "name": "JcEFuwzuTNeFORMkgnGRiFpzGvqIWOrIcuDRGfBCvxgchRvvQcxzRNZxXzFYHzJ",
    "description": "NMZIiNpYY",
    "lookup_key": "lXMfKqceAnXPGemJawURYJVmuKNSFFYAMZHQkQcNdpoPDScQxbkcoyCXkXiCzVt",
    "alternate_lookup_key": "qhlJHSsdAteEUskhPBcSIsGBACNvxGyjRiDdJkLBQlyZhXvDGAAGDsjZqvIfmQI",
    "last_activity": "1995-11-21T16:31:05.000Z",
    "created_on": "1981-07-01T15:44:07.819Z",
    "last_updated_on": "1991-11-20T09:25:51.851Z"
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

**Example GET request path:**<br>`/notifications/780353289`

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
  "financial_institution_id": 980747263,
  "name": "Sample Notification",
  "type": "webhook",
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
  "html_template": "gMJynUPAazkeIJmmIbRyCUspYz",
  "text_template": "vtyQPSsP"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 980747263 },
	{ "name", "Sample Notification" },
	{ "type", "webhook" },
	{ "event", "merchant_site_updates_top" },
	{ "html_template", "gMJynUPAazkeIJmmIbRyCUspYz" },
	{ "text_template", "vtyQPSsP" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 980747263 )
	.add("name", "Sample Notification" )
	.add("type", "webhook" )
	.add("event", "merchant_site_updates_top" )
	.add("html_template", "gMJynUPAazkeIJmmIbRyCUspYz" )
	.add("text_template", "vtyQPSsP" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":980747263,\"name\":\"Sample Notification\",\"type\":\"webhook\",\"event\":\"merchant_site_updates_top\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"gMJynUPAazkeIJmmIbRyCUspYz\",\"text_template\":\"vtyQPSsP\"}"
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
  "type": "webhook",
  "event": "merchant_site_updates_all",
  "config": {
    "recipient": "cardholder",
    "url": null,
    "from_email": "CardUpdatr <no-reply@cardupdatr.app>",
    "return_path": "no-reply@cardupdatr.app",
    "send_email_time": null,
    "interval_length": null,
    "interval_type": null
  },
  "html_template": "JdYvXgOFFQAFbtbYYVrwk",
  "text_template": "j"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Sample Notification" },
	{ "type", "webhook" },
	{ "event", "merchant_site_updates_all" },
	{ "html_template", "JdYvXgOFFQAFbtbYYVrwk" },
	{ "text_template", "j" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Sample Notification" )
	.add("type", "webhook" )
	.add("event", "merchant_site_updates_all" )
	.add("html_template", "JdYvXgOFFQAFbtbYYVrwk" )
	.add("text_template", "j" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"Sample Notification\",\"type\":\"webhook\",\"event\":\"merchant_site_updates_all\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"JdYvXgOFFQAFbtbYYVrwk\",\"text_template\":\"j\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/780353289
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
https://api.INSTANCE.cardsavr.io/notifications/780353289
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
const notificationresults = await session.getNotificationResults(1554838724,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["notification"])});
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
JsonArray response = (JsonArray)session.get(1554838724, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1554838724,
  "last_attempt_date": "2014-08-30T20:04:36.767Z",
  "fi_lookup_key": "rfRowUSsndqXjjLRoaTlxerzxIXyrsnwAJUitfhHKrHFCTCAjeMlcXloSmtGyRZ",
  "cuid": "IpDqKqnFjQkTuxkXPKyHbfooLUrZDM",
  "status": "failure",
  "attempts": 302625232,
  "notification_data": {
    "OFEzcmDwjSzg": "%7=df2oKPQ-pQn",
    "lzRjcBXZqGvp": 58,
    "QLxPWJYkEomM": false
  },
  "created_on": "1995-03-09T14:38:12.063Z",
  "last_updated_on": "2020-08-09T02:57:32.346Z",
  "notification": {
    "id": 941313341,
    "name": "Sample Notification",
    "type": "email",
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
    "html_template": "AyYRrMzFwCoyKZYUfmElxsNoXRctJz",
    "text_template": "kEMdXrUjKCuNCwl",
    "created_on": "1980-06-21T22:56:14.691Z",
    "last_updated_on": "1985-06-29T08:09:28.986Z"
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

**Example GET request path:**<br>`/notification_results/1554838724`

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
  "notification_id": 1900582160,
  "fi_lookup_key": "rfRowUSsndqXjjLRoaTlxerzxIXyrsnwAJUitfhHKrHFCTCAjeMlcXloSmtGyRZ",
  "cuid": "IpDqKqnFjQkTuxkXPKyHbfooLUrZDM",
  "status": "failure",
  "attempts": 302625232,
  "notification_data": {
    "OFEzcmDwjSzg": "%7=df2oKPQ-pQn",
    "lzRjcBXZqGvp": 58,
    "QLxPWJYkEomM": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 1900582160 },
	{ "fi_lookup_key", "rfRowUSsndqXjjLRoaTlxerzxIXyrsnwAJUitfhHKrHFCTCAjeMlcXloSmtGyRZ" },
	{ "cuid", "IpDqKqnFjQkTuxkXPKyHbfooLUrZDM" },
	{ "status", "failure" },
	{ "attempts", 302625232 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 1900582160 )
	.add("fi_lookup_key", "rfRowUSsndqXjjLRoaTlxerzxIXyrsnwAJUitfhHKrHFCTCAjeMlcXloSmtGyRZ" )
	.add("cuid", "IpDqKqnFjQkTuxkXPKyHbfooLUrZDM" )
	.add("status", "failure" )
	.add("attempts", 302625232 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":1900582160,\"fi_lookup_key\":\"rfRowUSsndqXjjLRoaTlxerzxIXyrsnwAJUitfhHKrHFCTCAjeMlcXloSmtGyRZ\",\"cuid\":\"IpDqKqnFjQkTuxkXPKyHbfooLUrZDM\",\"status\":\"failure\",\"attempts\":302625232,\"notification_data\":{\"OFEzcmDwjSzg\":\"%7=df2oKPQ-pQn\",\"lzRjcBXZqGvp\":58,\"QLxPWJYkEomM\":false}}"
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
const singlesitejobs = await session.getSingleSiteJobs(1776843278,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_card","cardsavr_account","credential_requests"])});
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
JsonArray response = (JsonArray)session.get(1776843278, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1776843278,
  "status": "PAYMENT_PROCESSOR_DOWN",
  "status_message": "PdAc",
  "termination_type": "BILLABLE",
  "custom_data": {
    "gdaSMuKNaenv": "Yrm^DL5tz/$J",
    "qlkCmFfubgKW": 81,
    "EFydoCIYcinl": false
  },
  "notification_sent": true,
  "time_elapsed": 759709407,
  "started_on": "1990-02-13T01:49:14.260Z",
  "completed_on": "2012-01-17T07:09:55.558Z",
  "created_on": "2021-11-11T23:29:09.276Z",
  "last_updated_on": "2000-01-23T02:00:07.830Z",
  "cardholder": {
    "id": 1010430175,
    "type": "persistent_all",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "ZmvYzoTiLwbCWwrWCjybc",
    "webhook_url": "JgljUqwFEwAkBomfaG",
    "custom_data": {
      "NStiwpwDmoap": "8Ot$U^H",
      "bmIYaaJuWdZV": 21,
      "zpesGWaOfvlg": false
    },
    "created_on": "2021-04-11T11:57:28.325Z",
    "last_updated_on": "2005-05-15T08:49:58.086Z",
    "cuid": "fnR"
  },
  "cardsavr_card": {
    "id": 339837036,
    "type": "Unknown Type",
    "expiration_month": 12,
    "expiration_year": 24,
    "name_on_card": "Jane Smith",
    "nickname": "Jane's VISA",
    "custom_data": {
      "pLGDtWgFfdwE": "8JJ17aW[+5^+#g_q/)t&p(RWC",
      "ijWZpypzeEAd": 12,
      "EspOMbpOHDkB": false
    },
    "created_on": "1979-09-05T19:08:50.551Z",
    "last_updated_on": "2000-11-01T19:19:24.772Z",
    "par": "jFkASXJXhvPMKGDfPMOAPuqkySdcf",
    "customer_key": "NFOwqvMlsMrIEnAFAECTiuhyoGNzYoWM"
  },
  "cardsavr_account": {
    "id": 434785253,
    "last_password_update": "1980-05-16T00:28:37.846Z",
    "last_saved_card": "1989-12-18T04:09:34.697Z",
    "created_on": "2001-04-23T16:08:10.700Z",
    "last_updated_on": "1985-03-24T20:32:58.400Z",
    "customer_key": "SQhIKJgyGaWrRRvEdLsuIOZs"
  }
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/1776843278`

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
started_on | date | Time when job started.
completed_on | date | Timestamp of job completion.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) [cardholders](#cardholders) | ID of cardholder associated with this job.
account_id | number (fk) [accounts](#accounts) | ID of account associated with this job.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create single-site job

```javascript
const singlesitejob = await session.createSingleSiteJob({
  "cardholder_id": 757454038,
  "card_id": 93982891,
  "account_id": 887391038,
  "status": "PAYMENT_PROCESSOR_DOWN",
  "custom_data": {
    "gdaSMuKNaenv": "Yrm^DL5tz/$J",
    "qlkCmFfubgKW": 81,
    "EFydoCIYcinl": false
  },
  "notification_sent": true,
  "time_elapsed": 759709407,
  "started_on": "1990-02-13T01:49:14.260Z",
  "completed_on": "2012-01-17T07:09:55.558Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 757454038 },
	{ "card_id", 93982891 },
	{ "account_id", 887391038 },
	{ "status", "PAYMENT_PROCESSOR_DOWN" },
	{ "notification_sent", true },
	{ "time_elapsed", 759709407 },
	{ "started_on", "1990-02-13T01:49:14.260Z" },
	{ "completed_on", "2012-01-17T07:09:55.558Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 757454038 )
	.add("card_id", 93982891 )
	.add("account_id", 887391038 )
	.add("status", "PAYMENT_PROCESSOR_DOWN" )
	.add("notification_sent", true )
	.add("time_elapsed", 759709407 )
	.add("started_on", "1990-02-13T01:49:14.260Z" )
	.add("completed_on", "2012-01-17T07:09:55.558Z" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":757454038,\"card_id\":93982891,\"account_id\":887391038,\"status\":\"PAYMENT_PROCESSOR_DOWN\",\"custom_data\":{\"gdaSMuKNaenv\":\"Yrm^DL5tz/$J\",\"qlkCmFfubgKW\":81,\"EFydoCIYcinl\":false},\"notification_sent\":true,\"time_elapsed\":759709407,\"started_on\":\"1990-02-13T01:49:14.260Z\",\"completed_on\":\"2012-01-17T07:09:55.558Z\"}"
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
started_on | date | no | Time when job started.
completed_on | date | no | Timestamp of job completion.

See [single-site job response attributes](#response-place_card_on_single_site_job).

#### <a name="post-place_card_on_single_site_job-1"></a>string enum*
- INITIATED
- REQUESTED
- IN_PROGRESS
- AUTH
- CREDS_RECEIVED
- TFA_CODE_RECEIVED
- TFA_SUBMITTED
- LOGIN_SUBMITTED
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
- ABANDONED
- ABANDONED_QUICKSTART
- KILLED
- ACCOUNT_SETUP_INCOMPLETE
- ACCOUNT_NOT_SUPPORTED
- TFA_NOT_SUPPORTED
- PREPAID_ACCOUNT
- INACTIVE_ACCOUNT
- MISSING_CARD_DATA
- card_form_failed
- INVALID_CARD
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
- SUCCESSFUL
- UNSUPPORTED_CAPTCHA
- TIMEOUT_CAPTCHA
- TIMEOUT_CREDENTIALS
- TIMEOUT_TFA
- TOO_MANY_LOGIN_FAILURES
- TOO_MANY_TFA_FAILURES
- INVALID_SECURITY_ANSWERS
- INVALID_CREDENTIAL_REQUEST_TYPE
- UNSUCCESSFUL
- PROXY_PROBE_FAILED
- VBS_TIMEOUT
- VBS_ERROR
- UNKNOWN_INTERFACE_TYPE
- UNIMPLEMENTED_JOB_TYPE
- UNKNOWN_JOB_TYPE
- INCOMPLETE_JOB_DATA

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
  "card_id": 1598128587,
  "status": "PREPAID_ACCOUNT",
  "custom_data": {
    "XxcDiBAnElTJ": "utX_",
    "nZgnFsuWgvjl": 74,
    "zvGrgcrZvizl": true
  },
  "notification_sent": true,
  "time_elapsed": 2134861535,
  "started_on": "2003-08-19T16:35:28.602Z",
  "completed_on": "2010-12-24T13:26:41.265Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 1598128587 },
	{ "status", "PREPAID_ACCOUNT" },
	{ "notification_sent", true },
	{ "time_elapsed", 2134861535 },
	{ "started_on", "2003-08-19T16:35:28.602Z" },
	{ "completed_on", "2010-12-24T13:26:41.265Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 1598128587 )
	.add("status", "PREPAID_ACCOUNT" )
	.add("notification_sent", true )
	.add("time_elapsed", 2134861535 )
	.add("started_on", "2003-08-19T16:35:28.602Z" )
	.add("completed_on", "2010-12-24T13:26:41.265Z" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":1598128587,\"status\":\"PREPAID_ACCOUNT\",\"custom_data\":{\"XxcDiBAnElTJ\":\"utX_\",\"nZgnFsuWgvjl\":74,\"zvGrgcrZvizl\":true},\"notification_sent\":true,\"time_elapsed\":2134861535,\"started_on\":\"2003-08-19T16:35:28.602Z\",\"completed_on\":\"2010-12-24T13:26:41.265Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1776843278
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
started_on | date | Time when job started.
completed_on | date | Timestamp of job completion.

See [single-site job response parameters](#response-place_card_on_single_site_job).

<aside class="notice">Update calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete single-site job

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1776843278
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

