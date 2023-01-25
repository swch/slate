
# Accounts
Account objects contain the account information, such as username and password, for a particular cardhoder. They are used to log in to a cardholder's account for placing a payment card.
## Get account

```javascript
const accounts = await session.getAccounts(926973539,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","merchant_site","cardsavr_card"])});
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
JsonArray response = (JsonArray)session.get(926973539, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 926973539,
  "last_password_update": "1985-11-19T06:46:24.535Z",
  "last_saved_card": "1999-08-16T22:00:19.904Z",
  "created_on": "1997-02-11T12:01:09.969Z",
  "last_updated_on": "1983-06-05T12:57:16.844Z",
  "cardholder": {
    "id": 1553486083,
    "type": "ephemeral",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "j",
    "custom_data": {
      "SJqToifjYwAi": "6&[H.6XGMrEt8r1!",
      "iWVHHiEbiTMd": 18,
      "LGJAxSkQGOMf": false
    },
    "created_on": "2007-04-22T12:00:59.796Z",
    "last_updated_on": "2012-11-13T23:15:14.773Z",
    "cuid": "zSU"
  },
  "merchant_site": {
    "id": 1235464671,
    "name": "Amazon",
    "host": "amazon.com",
    "tags": [
      "yV3GRN}1)NP",
      2,
      "(ZYXaS{e!f*(9{Q,l"
    ],
    "interface_type": "dcs",
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
    "credit_card_page": "https://www.merchantsite.com/credit_card",
    "forgot_password_page": "https://www.merchantsite.com/forgot_password",
    "login_page": "https://www.merchantsite.com/login"
  },
  "cardsavr_card": {
    "id": 1897542437,
    "type": "Unknown Type",
    "expiration_month": 12,
    "expiration_year": 24,
    "name_on_card": "Jane Smith",
    "nickname": "Jane's VISA",
    "custom_data": {
      "tdpZmpqFDZmH": "^A,RhN^iz0",
      "tvZSTVzeIyMJ": 50,
      "YXjVCKdeimjc": false
    },
    "created_on": "1984-01-26T22:43:52.931Z",
    "last_updated_on": "1993-05-09T08:36:15.716Z",
    "par": "aWmvlZqRuuLYnKAsXzTXlainxaOWg",
    "customer_key": "mPNhZsKJZTEZwZqDWiqJu"
  },
  "customer_key": "cueNZsKKUOzaHsIWTLfnbHLByxc"
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

**Example GET request path:**<br>`/cardsavr_accounts/926973539`

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
  "cardholder_id": 164543038,
  "merchant_site_id": 1186198109,
  "customer_key": "cueNZsKKUOzaHsIWTLfnbHLByxc",
  "last_card_placed_id": 622962491,
  "account_link": {
    "username": "jsmith123",
    "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 164543038 },
	{ "merchant_site_id", 1186198109 },
	{ "customer_key", "cueNZsKKUOzaHsIWTLfnbHLByxc" },
	{ "last_card_placed_id", 622962491 }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 164543038 )
	.add("merchant_site_id", 1186198109 )
	.add("customer_key", "cueNZsKKUOzaHsIWTLfnbHLByxc" )
	.add("last_card_placed_id", 622962491 )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":164543038,\"merchant_site_id\":1186198109,\"customer_key\":\"cueNZsKKUOzaHsIWTLfnbHLByxc\",\"last_card_placed_id\":622962491,\"account_link\":{\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}}"
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
account_link | object | no | One or more properties with key:value pairs that are required for authenticated a user.  These properties are either included as part of initial account collection, or they are requested as part of a credential_request.  An error will be returned if all properties are not provided for a given credential_request. The set of key:value pairs for a site is specified in the merchant site info returned from GET /merchant_sites as account_link.

See [account response attributes](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the account_link when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Upsert account

```javascript
const account = await session.updateAccount(1,{
  "last_card_placed_id": 476358147,
  "account_link": {
    "username": "jsmith123",
    "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
  }
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 476358147 }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 476358147 )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":476358147,\"account_link\":{\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/926973539
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
account_link | object | One or more properties with key:value pairs that are required for authenticated a user.  These properties are either included as part of initial account collection, or they are requested as part of a credential_request.  An error will be returned if all properties are not provided for a given credential_request. The set of key:value pairs for a site is specified in the merchant site info returned from GET /merchant_sites as account_link.

See [account response parameters](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the account_link when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete account

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/926973539
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
const addresses = await session.getAddresses(261039396,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder"])});
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
JsonArray response = (JsonArray)session.get(261039396, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 261039396,
  "address1": "alSyPLJPMkknIbHtJLJakmIYcpyQpmtDCmzQAzLhGVmmwbtDiAaufivSqmJdMluCJcpAfxdMJTMhNuwiXsbHTYbXLvCHAGQkkLh",
  "address2": "TKvflZNGUQDfvvSgIncTWOvVQWOpTWHIGBcBlokeZMQeJLmsQowsyDwWzFzRcyoVfzEncQwlfMaQzqxNvoAmGsVRyCcIwgTqodO",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "DBOwhnRasyTd@ifAmoh.cnX",
  "phone_number": "2065555555",
  "created_on": "1975-08-06T22:41:52.224Z",
  "last_updated_on": "1972-08-30T12:34:10.890Z",
  "cardholder": {
    "id": 1600004190,
    "type": "persistent_all",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "G",
    "custom_data": {
      "enWcQBbhkncf": "u)W6vwp=ZXDK[DqHdrZO9X*d^6Dzg.y",
      "BPECXeTvNUzZ": 28,
      "ByrgHeWwXNDj": false
    },
    "created_on": "1972-01-27T03:10:52.768Z",
    "last_updated_on": "1972-09-22T02:10:07.390Z",
    "cuid": "qRHikeOeHUZRzfMKsmAfHOlIGRxGRU"
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

**Example GET request path:**<br>`/cardsavr_addresses/261039396`

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
  "cardholder_id": 44595665,
  "address1": "alSyPLJPMkknIbHtJLJakmIYcpyQpmtDCmzQAzLhGVmmwbtDiAaufivSqmJdMluCJcpAfxdMJTMhNuwiXsbHTYbXLvCHAGQkkLh",
  "address2": "TKvflZNGUQDfvvSgIncTWOvVQWOpTWHIGBcBlokeZMQeJLmsQowsyDwWzFzRcyoVfzEncQwlfMaQzqxNvoAmGsVRyCcIwgTqodO",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "DBOwhnRasyTd@ifAmoh.cnX",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 44595665 },
	{ "address1", "alSyPLJPMkknIbHtJLJakmIYcpyQpmtDCmzQAzLhGVmmwbtDiAaufivSqmJdMluCJcpAfxdMJTMhNuwiXsbHTYbXLvCHAGQkkLh" },
	{ "address2", "TKvflZNGUQDfvvSgIncTWOvVQWOpTWHIGBcBlokeZMQeJLmsQowsyDwWzFzRcyoVfzEncQwlfMaQzqxNvoAmGsVRyCcIwgTqodO" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "DBOwhnRasyTd@ifAmoh.cnX" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 44595665 )
	.add("address1", "alSyPLJPMkknIbHtJLJakmIYcpyQpmtDCmzQAzLhGVmmwbtDiAaufivSqmJdMluCJcpAfxdMJTMhNuwiXsbHTYbXLvCHAGQkkLh" )
	.add("address2", "TKvflZNGUQDfvvSgIncTWOvVQWOpTWHIGBcBlokeZMQeJLmsQowsyDwWzFzRcyoVfzEncQwlfMaQzqxNvoAmGsVRyCcIwgTqodO" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "DBOwhnRasyTd@ifAmoh.cnX" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":44595665,\"address1\":\"alSyPLJPMkknIbHtJLJakmIYcpyQpmtDCmzQAzLhGVmmwbtDiAaufivSqmJdMluCJcpAfxdMJTMhNuwiXsbHTYbXLvCHAGQkkLh\",\"address2\":\"TKvflZNGUQDfvvSgIncTWOvVQWOpTWHIGBcBlokeZMQeJLmsQowsyDwWzFzRcyoVfzEncQwlfMaQzqxNvoAmGsVRyCcIwgTqodO\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"DBOwhnRasyTd@ifAmoh.cnX\",\"phone_number\":\"2065555555\"}"
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
  "address1": "LUyXjBqfthkAVuIglsCPQToQoeRecFkjxoKlDqjBqJMgiicxquZIrOIUuqfPOUTxHFXfKKGDzPpOLAPrtMHlrvqEDXqUhHAFPBG",
  "address2": "eWEyedAasqyVDFwDKjQHquXVMmNhikmIkRAVMqBAJQiMdCTDJUhOzbwuTczNrKnUUiSionAPxuvKPnIozefxQiMotNxxsvYxjPa",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "zXZVSJWvevJc@HlQYXT.ezr",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "LUyXjBqfthkAVuIglsCPQToQoeRecFkjxoKlDqjBqJMgiicxquZIrOIUuqfPOUTxHFXfKKGDzPpOLAPrtMHlrvqEDXqUhHAFPBG" },
	{ "address2", "eWEyedAasqyVDFwDKjQHquXVMmNhikmIkRAVMqBAJQiMdCTDJUhOzbwuTczNrKnUUiSionAPxuvKPnIozefxQiMotNxxsvYxjPa" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "zXZVSJWvevJc@HlQYXT.ezr" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "LUyXjBqfthkAVuIglsCPQToQoeRecFkjxoKlDqjBqJMgiicxquZIrOIUuqfPOUTxHFXfKKGDzPpOLAPrtMHlrvqEDXqUhHAFPBG" )
	.add("address2", "eWEyedAasqyVDFwDKjQHquXVMmNhikmIkRAVMqBAJQiMdCTDJUhOzbwuTczNrKnUUiSionAPxuvKPnIozefxQiMotNxxsvYxjPa" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", false )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "zXZVSJWvevJc@HlQYXT.ezr" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"LUyXjBqfthkAVuIglsCPQToQoeRecFkjxoKlDqjBqJMgiicxquZIrOIUuqfPOUTxHFXfKKGDzPpOLAPrtMHlrvqEDXqUhHAFPBG\",\"address2\":\"eWEyedAasqyVDFwDKjQHquXVMmNhikmIkRAVMqBAJQiMdCTDJUhOzbwuTczNrKnUUiSionAPxuvKPnIozefxQiMotNxxsvYxjPa\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"zXZVSJWvevJc@HlQYXT.ezr\",\"phone_number\":\"2065555555\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/261039396
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/261039396
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
const bins = await session.getBins(201638270,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(201638270, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 201638270,
  "custom_data": {
    "bsPIjhMmSDHp": "HVEAdoJ",
    "oWgndYcpWicV": 4,
    "aBlPAfgbeIeU": false
  },
  "created_on": "2010-09-15T21:21:58.477Z",
  "last_updated_on": "2006-08-05T12:59:18.731Z",
  "financial_institution": {
    "id": 1306497883,
    "name": "yfzxcuupqYlthHTEwigksJsdkddKYxadnRaCQddkJLlNDtMhoNiNNGXCPteRTtz",
    "description": "pyVzRrVfkZzC",
    "lookup_key": "TtwmVzHGjPZicFJEEmSGgpqWACztDqhSgkYMpHehzYPIErgMoJMZjbXkDabzbAN",
    "alternate_lookup_key": "QymEEiyCouygiAlGkAhQzBaInrwYnowQnsVbkPvSogewqgNEXhpcKbBBKElksZW",
    "last_activity": "2012-02-26T09:29:01.660Z",
    "created_on": "2015-09-05T17:26:10.549Z",
    "last_updated_on": "2006-11-07T08:57:29.652Z"
  },
  "bank_identification_number": "55698365"
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

**Example GET request path:**<br>`/cardsavr_bins/201638270`

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
  "financial_institution_id": 1976993790,
  "bank_identification_number": "55698365",
  "custom_data": {
    "bsPIjhMmSDHp": "HVEAdoJ",
    "oWgndYcpWicV": 4,
    "aBlPAfgbeIeU": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1976993790 },
	{ "bank_identification_number", "55698365" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1976993790 )
	.add("bank_identification_number", "55698365" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1976993790,\"bank_identification_number\":\"55698365\",\"custom_data\":{\"bsPIjhMmSDHp\":\"HVEAdoJ\",\"oWgndYcpWicV\":4,\"aBlPAfgbeIeU\":false}}"
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
  "financial_institution_id": 1561361880,
  "custom_data": {
    "jaGOiVWnWvnN": "9{o-y$a",
    "qeFbdxUjZekG": 72,
    "CVduDfaRirKe": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1561361880 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1561361880 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1561361880,\"custom_data\":{\"jaGOiVWnWvnN\":\"9{o-y$a\",\"qeFbdxUjZekG\":72,\"CVduDfaRirKe\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/201638270
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/201638270
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
const cardplacementresults = await session.getCardPlacementResults(399110469,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution","merchant_site","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(399110469, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 399110469,
  "merchant_site_hostname": "XfXbncufewIONToOkMZtQRezvsmYBgHEkCLEtLEarcIjdzgEJmNmPeZsJPRGOLTmXGNMqDQMSUSImhEtvHAbRGuwVMjqzoUWVEqSZABDenbarKHMOwfEpxTAFsfBgTMntGmQYmAqYjUVNCndPyACWjuicZIMVeHodZBDUtkcKzdbvttuGjxttzZDFIIwCSKyHZeaOXfmsBqJHecYvNKhrDbqGJqgwyDUQOKwfHQXnmOrgAYUaAkGbQaHDFlYMA",
  "meta_key": "MB9810411",
  "fi_name": "AqKjNoTsvUvsUNDxKSSQUBsmlGLOMsoKjccgKRNZjjfIffEcXjFPxovvfXZfNli",
  "bank_identification_number": "11090977",
  "cuid": "ZtoinTkfdLZEXZJre",
  "par": "LrxNellXFWFPCDvjSOkbhNMmvTJzf",
  "card_customer_key": "yRDQCU",
  "account_customer_key": "ZZ",
  "status": "SUCCESSFUL",
  "status_message": "Successful",
  "termination_type": "BILLABLE",
  "custom_data": {
    "jVTjXUqLhgik": "T2bRRr{E,ca0DHjlQ!6%4e,",
    "wBvVOMOnvnlT": 48,
    "lbkPLDLBUwgR": false
  },
  "time_elapsed": 1933346517,
  "first_6": "rmRuOkyuZhDWYtFSxLXnRUaRnvakqaoZ",
  "first_7": "XnrSHFohAczRxSthyAgApfJyzFygtDrz",
  "first_8": "KyqLzPvczmazUqkLBQFcJgMxJDbtdfnR",
  "trace": "WkK",
  "email_sent": true,
  "completed_on": "1978-04-24T15:17:25.009Z",
  "created_on": "1990-02-17T06:42:14.572Z",
  "last_updated_on": "1984-05-15T11:42:48.910Z",
  "financial_institution": {
    "id": 1737261672,
    "name": "oQTuzdCpnoPGVwfjGOQszszRaPMavuBJKWhHIgvGymAafAxajZJBYpPJgIXhrZv",
    "description": "lEHvgbQAaRxBySWxSWWSikvEPAeT",
    "lookup_key": "kRMzosVfvJvsOrSwxcYbjKZfCbabnWPvnKcjWdalPHAjbUlbenGAffRIQGsOYIa",
    "alternate_lookup_key": "HrmvHsqNWjaoKEROiCYojThMzwMuxECWFeMWGniVulyeynsBlAImgpxNDHTZqyj",
    "last_activity": "2007-03-08T13:45:42.104Z",
    "created_on": "1971-11-11T00:50:55.474Z",
    "last_updated_on": "1995-06-25T08:32:15.991Z"
  },
  "merchant_site": {
    "id": 2021726552,
    "name": "Amazon",
    "host": "amazon.com",
    "tags": [
      "p)Bigjv*3yA][LqC[r",
      63,
      "*G"
    ],
    "interface_type": "dcs",
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
    "credit_card_page": "https://www.merchantsite.com/credit_card",
    "forgot_password_page": "https://www.merchantsite.com/forgot_password",
    "login_page": "https://www.merchantsite.com/login"
  },
  "cardsavr_bin": {
    "id": 1322825346,
    "custom_data": {
      "tVlUQurmjhMR": "qWdpLYx={tkr1OF",
      "ZHUzRAIjkJAu": 37,
      "AeGOxbqkmQco": false
    },
    "created_on": "2013-08-28T08:00:22.870Z",
    "last_updated_on": "2009-11-20T12:53:20.545Z",
    "bank_identification_number": "67003839"
  },
  "place_card_on_single_site_job_id": 1740625745
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

**Example GET request path:**<br>`/card_placement_results/399110469`

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
const cards = await session.getCards(1813456615,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_address","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(1813456615, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1813456615,
  "type": "Mastercard",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "CwNacPCPNmIU": "q-8)JhOTA[OCd/[J_n/De",
    "gvjYqMSJwXgZ": 91,
    "ENLaLbdchwGR": false
  },
  "created_on": "1973-10-14T02:06:57.504Z",
  "last_updated_on": "1989-04-07T23:05:36.824Z",
  "cardholder": {
    "id": 1394198683,
    "type": "persistent_all",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "hVeTWilUppNVOiZtzi",
    "custom_data": {
      "auAgbjcYvTTD": "I@I04t",
      "glcVKNLLHSqK": 15,
      "oeWzcSyussSj": true
    },
    "created_on": "1970-06-14T17:59:09.850Z",
    "last_updated_on": "1975-04-12T11:59:20.675Z",
    "cuid": "jRSUTDkSjcu"
  },
  "cardsavr_address": {
    "id": 526367763,
    "address1": "UUGXHOlGbhqPMBLhkftXrHgnezmOkYhuCWaaqgFbNKIBKxVAsjbBNCqTBBFHtObVQhNxqKcYHozSusezqKDSGhNykRUcoSFPMAL",
    "address2": "PqEAUMrxJdMqiMgAPyNUbHHPcTWEPLTpzqjDaNvtrWBqsrXjsxjighCnHIqAnyRUfcPvOfboXpxpFcPJfWAoPPelZKMqWptVcbz",
    "city": "Seattle",
    "subnational": "WA",
    "postal_code": "98177",
    "postal_other": "98177-0124",
    "country": "USA",
    "is_primary": true,
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "txlQfbwtbspt@sJctMQ.Tzc",
    "phone_number": "2065555555",
    "created_on": "2020-07-10T05:58:48.988Z",
    "last_updated_on": "1978-01-28T22:37:56.112Z"
  },
  "cardsavr_bin": {
    "id": 1513500547,
    "custom_data": {
      "ltVWidfGdYMc": "uqRR^=6^@fl.$bNr.%",
      "qKuesjkKgLxc": 13,
      "hSgvXonxEEHJ": false
    },
    "created_on": "1976-10-04T00:43:53.083Z",
    "last_updated_on": "1976-01-27T16:32:09.409Z",
    "bank_identification_number": "85723429"
  },
  "par": "lAoyjhCJGRGiecPagBCcqHxuzOeti",
  "customer_key": "MqYMATeOluc"
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

**Example GET request path:**<br>`/cardsavr_cards/1813456615`

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
  "cardholder_id": 157157184,
  "address_id": 1543548658,
  "bin_id": 1373778445,
  "par": "lAoyjhCJGRGiecPagBCcqHxuzOeti",
  "customer_key": "MqYMATeOluc",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "CwNacPCPNmIU": "q-8)JhOTA[OCd/[J_n/De",
    "gvjYqMSJwXgZ": 91,
    "ENLaLbdchwGR": false
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 157157184 },
	{ "address_id", 1543548658 },
	{ "bin_id", 1373778445 },
	{ "par", "lAoyjhCJGRGiecPagBCcqHxuzOeti" },
	{ "customer_key", "MqYMATeOluc" },
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
	.add("cardholder_id", 157157184 )
	.add("address_id", 1543548658 )
	.add("bin_id", 1373778445 )
	.add("par", "lAoyjhCJGRGiecPagBCcqHxuzOeti" )
	.add("customer_key", "MqYMATeOluc" )
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
curl -d "{\"cardholder_id\":157157184,\"address_id\":1543548658,\"bin_id\":1373778445,\"par\":\"lAoyjhCJGRGiecPagBCcqHxuzOeti\",\"customer_key\":\"MqYMATeOluc\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"Jane's VISA\",\"custom_data\":{\"CwNacPCPNmIU\":\"q-8)JhOTA[OCd/[J_n/De\",\"gvjYqMSJwXgZ\":91,\"ENLaLbdchwGR\":false}}"
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
cvv | string | yes | 
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
  "bin_id": 433864784,
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "qmYEriQhOIIQ": "RK%lj4l/~*a&",
    "HtFLaXTnHkfB": 4,
    "aIYCDatyeNRS": true
  },
  "pan": "4111111111111111"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "bin_id", 433864784 },
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
	.add("bin_id", 433864784 )
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
curl -d "{\"bin_id\":433864784,\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"Jane's VISA\",\"custom_data\":{\"qmYEriQhOIIQ\":\"RK%lj4l/~*a&\",\"HtFLaXTnHkfB\":4,\"aIYCDatyeNRS\":true},\"pan\":\"4111111111111111\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1813456615
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1813456615
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
const cardholders = await session.getCardholders(1782988779,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["financial_institution"])}
JsonArray response = (JsonArray)session.get(1782988779, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1782988779,
  "type": "ephemeral",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "sNXdczKJsPyWPJ",
  "custom_data": {
    "MqlnxJmrjghY": "EfHXSEpwU*8XDbgXo*9V",
    "ONzAPWfEwNVz": 32,
    "LqVhXmsTrygS": true
  },
  "created_on": "2017-12-09T11:24:46.185Z",
  "last_updated_on": "1972-05-15T09:23:26.437Z",
  "financial_institution": {
    "id": 427671308,
    "name": "bMnFabMJLgJKxOtSjSEZknYovbDoQgxdVzDKDopdIUclYgDTiqeayriiyNjNSBV",
    "description": "huVjwlBcBWkqJkHifajAwafvQPrQORu",
    "lookup_key": "LyEhwmhUrBuPrEKARPrwTEEsDcIGJofnWGQgcHCZHmZeeUvTwPlmsOyUtmkUrth",
    "alternate_lookup_key": "ZMCpngKdjTRXhxjZtxIMyBmtFpCPZeeXaQfWbUCtZUgdEuSVFFtjfkyjnQrtsYD",
    "last_activity": "2020-01-07T07:00:23.432Z",
    "created_on": "2013-12-17T23:01:36.599Z",
    "last_updated_on": "2018-05-07T06:48:34.916Z"
  },
  "cuid": "ezCSzBNK"
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

**Example GET request path:**<br>`/cardholders/1782988779`

### <a name="response-cardholder"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this cardholder.
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | 
type | string | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities.
 If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
first_name | string | 
last_name | string | 
email | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
custom_data | object | Additional data that can be added to the cardholder if needed.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cuid | string | External unique ID for cardholder--can be account_id, email address, phone number, etc.  A random number will be gnenerated if not provided.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create cardholder

```javascript
const cardholder = await session.createCardholder({
  "cuid": "ezCSzBNK",
  "type": "ephemeral",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "sNXdczKJsPyWPJ",
  "custom_data": {
    "MqlnxJmrjghY": "EfHXSEpwU*8XDbgXo*9V",
    "ONzAPWfEwNVz": 32,
    "LqVhXmsTrygS": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cuid", "ezCSzBNK" },
	{ "type", "ephemeral" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "sNXdczKJsPyWPJ" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cuid", "ezCSzBNK" )
	.add("type", "ephemeral" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "sNXdczKJsPyWPJ" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"cuid\":\"ezCSzBNK\",\"type\":\"ephemeral\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"sNXdczKJsPyWPJ\",\"custom_data\":{\"MqlnxJmrjghY\":\"EfHXSEpwU*8XDbgXo*9V\",\"ONzAPWfEwNVz\":32,\"LqVhXmsTrygS\":true}}"
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
type | [string enum](#post-cardholder-1)* | no | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities.
 If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
first_name | string | no | 
last_name | string | no | 
email | string | no | 
meta_key | string | no | Key used for billing record identification; automatically generated during card creation.
custom_data | object | no | Additional data that can be added to the cardholder if needed.

See [cardholder response attributes](#response-cardholder).

#### <a name="post-cardholder-1"></a>string enum*
- ephemeral
- persistent_creds
- persistent_all


## Upsert cardholder

```javascript
const cardholder = await session.updateCardholder(1,{
  "type": "persistent_creds",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "GYDwleaMQBTSfwTKWQjS",
  "custom_data": {
    "fMiZFwaUBoey": "mFuSi@W{ml!TjvzcSsr@c+QP#E*=Cb",
    "lkuHfmPdMRDl": 87,
    "NaNXxXwxfRxb": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "type", "persistent_creds" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "GYDwleaMQBTSfwTKWQjS" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("type", "persistent_creds" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "GYDwleaMQBTSfwTKWQjS" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"type\":\"persistent_creds\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"GYDwleaMQBTSfwTKWQjS\",\"custom_data\":{\"fMiZFwaUBoey\":\"mFuSi@W{ml!TjvzcSsr@c+QP#E*=Cb\",\"lkuHfmPdMRDl\":87,\"NaNXxXwxfRxb\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/1782988779
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
type | [string enum](#post-cardholder-1)* | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities.
 If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
first_name | string | 
last_name | string | 
email | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
custom_data | object | Additional data that can be added to the cardholder if needed.

See [cardholder response parameters](#response-cardholder).


## Delete cardholder

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/1782988779
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
const users = await session.getUsers(2102632703,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(2102632703, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2102632703,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1982-04-20T17:22:16.089Z",
  "is_locked": true,
  "password_lifetime": 118,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_agent",
  "next_rotation_on": "2022-07-09T13:12:41.227Z",
  "created_on": "2001-02-17T01:34:27.466Z",
  "last_updated_on": "2003-07-03T14:15:33.235Z",
  "username": "jsmith123",
  "financial_institution": {
    "id": 61731631,
    "name": "YSZWznkBLHGFluybzjvceNKtJkcbGgqrvkSrHbFZwWYANvGQBpvoCJDYgxUJuND",
    "description": "zYSpMicLNbetnnBIbxoM",
    "lookup_key": "wpYeYRUXYmIbwmPDxXzZogOizFNPqdJAdWsnNNMpqbqzSoawxmBRlDuGFfCDarV",
    "alternate_lookup_key": "iETcdXueMupmkCfcseFAgxrsKfteAqKBTpIoCuLWOgKeQFFjzTatBUyAiZRFVbY",
    "last_activity": "1997-05-07T00:00:13.794Z",
    "created_on": "1981-12-02T11:50:10.947Z",
    "last_updated_on": "1982-06-15T19:21:36.015Z"
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

**Example GET request path:**<br>`/cardsavr_users/2102632703`

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
  "financial_institution_id": 1621675055,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 118,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_agent",
  "next_rotation_on": "2022-07-09T13:12:41.227Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1621675055 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 118 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "cardholder_agent" },
	{ "next_rotation_on", "2022-07-09T13:12:41.227Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1621675055 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 118 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "cardholder_agent" )
	.add("next_rotation_on", "2022-07-09T13:12:41.227Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1621675055,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":118,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"cardholder_agent\",\"next_rotation_on\":\"2022-07-09T13:12:41.227Z\"}"
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
  "financial_institution_id": 1168702799,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 166,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "cardholder_sso_agent",
  "next_rotation_on": "2021-03-07T18:27:47.563Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1168702799 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 166 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "cardholder_sso_agent" },
	{ "next_rotation_on", "2021-03-07T18:27:47.563Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1168702799 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 166 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "cardholder_sso_agent" )
	.add("next_rotation_on", "2021-03-07T18:27:47.563Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1168702799,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":166,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"cardholder_sso_agent\",\"next_rotation_on\":\"2021-03-07T18:27:47.563Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/2102632703
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/2102632703
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
const financialinstitutions = await session.getFinancialInstitutions(1695151068,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(1695151068, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1695151068,
  "name": "wnseWAThaBRWyATTObBmQoBugrbuUOqQnhnPMLGYFyzxmNeXoxwMaigByjxQoWS",
  "description": "tgmHjyIKPPYQlZgrSW",
  "lookup_key": "sijAQXuPHYgRjuRZpUqvzpADczUqDNTzraNOIuqfjBJddpeoPJwzDEqhnbGzdml",
  "alternate_lookup_key": "fehmnelatrPZKwhnJXptRcrHUVPdIQKDWsYlHOKPJdCcTRyOCpqCxcPgTkyuMLZ",
  "last_activity": "1993-11-20T17:28:08.116Z",
  "created_on": "1992-11-21T09:22:43.830Z",
  "last_updated_on": "2012-05-30T14:34:10.640Z"
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

**Example GET request path:**<br>`/financial_institutions/1695151068`

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
  "name": "wnseWAThaBRWyATTObBmQoBugrbuUOqQnhnPMLGYFyzxmNeXoxwMaigByjxQoWS",
  "description": "tgmHjyIKPPYQlZgrSW",
  "lookup_key": "sijAQXuPHYgRjuRZpUqvzpADczUqDNTzraNOIuqfjBJddpeoPJwzDEqhnbGzdml",
  "alternate_lookup_key": "fehmnelatrPZKwhnJXptRcrHUVPdIQKDWsYlHOKPJdCcTRyOCpqCxcPgTkyuMLZ"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "wnseWAThaBRWyATTObBmQoBugrbuUOqQnhnPMLGYFyzxmNeXoxwMaigByjxQoWS" },
	{ "description", "tgmHjyIKPPYQlZgrSW" },
	{ "lookup_key", "sijAQXuPHYgRjuRZpUqvzpADczUqDNTzraNOIuqfjBJddpeoPJwzDEqhnbGzdml" },
	{ "alternate_lookup_key", "fehmnelatrPZKwhnJXptRcrHUVPdIQKDWsYlHOKPJdCcTRyOCpqCxcPgTkyuMLZ" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "wnseWAThaBRWyATTObBmQoBugrbuUOqQnhnPMLGYFyzxmNeXoxwMaigByjxQoWS" )
	.add("description", "tgmHjyIKPPYQlZgrSW" )
	.add("lookup_key", "sijAQXuPHYgRjuRZpUqvzpADczUqDNTzraNOIuqfjBJddpeoPJwzDEqhnbGzdml" )
	.add("alternate_lookup_key", "fehmnelatrPZKwhnJXptRcrHUVPdIQKDWsYlHOKPJdCcTRyOCpqCxcPgTkyuMLZ" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"wnseWAThaBRWyATTObBmQoBugrbuUOqQnhnPMLGYFyzxmNeXoxwMaigByjxQoWS\",\"description\":\"tgmHjyIKPPYQlZgrSW\",\"lookup_key\":\"sijAQXuPHYgRjuRZpUqvzpADczUqDNTzraNOIuqfjBJddpeoPJwzDEqhnbGzdml\",\"alternate_lookup_key\":\"fehmnelatrPZKwhnJXptRcrHUVPdIQKDWsYlHOKPJdCcTRyOCpqCxcPgTkyuMLZ\"}"
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
  "name": "jOdclOCeylfjBrLSuCtxPRkEgMRevQZxcrVqqyQOTgtHewtFHQNXrqrZQfSDhum",
  "description": "CjlwVIGgfptT",
  "lookup_key": "nuRZQygmEGmJAKbawmLydWpCYQYKKGOvUKhMYxVsbrYGHTMmtAOsiyrIOBOuFHf",
  "alternate_lookup_key": "fcdAMPgoqXtHBXssCuSqcewZGrDQXdSEiQEeKJADXAOYaMRCPkcUFBoCTNgOqty"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "jOdclOCeylfjBrLSuCtxPRkEgMRevQZxcrVqqyQOTgtHewtFHQNXrqrZQfSDhum" },
	{ "description", "CjlwVIGgfptT" },
	{ "lookup_key", "nuRZQygmEGmJAKbawmLydWpCYQYKKGOvUKhMYxVsbrYGHTMmtAOsiyrIOBOuFHf" },
	{ "alternate_lookup_key", "fcdAMPgoqXtHBXssCuSqcewZGrDQXdSEiQEeKJADXAOYaMRCPkcUFBoCTNgOqty" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "jOdclOCeylfjBrLSuCtxPRkEgMRevQZxcrVqqyQOTgtHewtFHQNXrqrZQfSDhum" )
	.add("description", "CjlwVIGgfptT" )
	.add("lookup_key", "nuRZQygmEGmJAKbawmLydWpCYQYKKGOvUKhMYxVsbrYGHTMmtAOsiyrIOBOuFHf" )
	.add("alternate_lookup_key", "fcdAMPgoqXtHBXssCuSqcewZGrDQXdSEiQEeKJADXAOYaMRCPkcUFBoCTNgOqty" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"jOdclOCeylfjBrLSuCtxPRkEgMRevQZxcrVqqyQOTgtHewtFHQNXrqrZQfSDhum\",\"description\":\"CjlwVIGgfptT\",\"lookup_key\":\"nuRZQygmEGmJAKbawmLydWpCYQYKKGOvUKhMYxVsbrYGHTMmtAOsiyrIOBOuFHf\",\"alternate_lookup_key\":\"fcdAMPgoqXtHBXssCuSqcewZGrDQXdSEiQEeKJADXAOYaMRCPkcUFBoCTNgOqty\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/1695151068
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
https://api.INSTANCE.cardsavr.io/financial_institutions/1695151068
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
const integrators = await session.getIntegrators(2061261422,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(2061261422, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2061261422,
  "name": "LWteRoFYwcMyKJVciQUURAiDPFGMfdUFhbXqUVcJOhWkMJHQb",
  "description": "BvaYjvxhveEsb",
  "current_key": "e2k9Zl4HMUFVrdEUJCvrAuBga0cm6XgqdEWkElJ4TrM=",
  "key_lifetime": 338,
  "next_rotation_on": "2009-08-21T23:48:14.329Z",
  "created_on": "2018-08-31T05:34:38.068Z",
  "last_updated_on": "1994-08-25T14:30:13.509Z"
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

**Example GET request path:**<br>`/integrators/2061261422`

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
  "name": "LWteRoFYwcMyKJVciQUURAiDPFGMfdUFhbXqUVcJOhWkMJHQb",
  "description": "BvaYjvxhveEsb",
  "current_key": "e2k9Zl4HMUFVrdEUJCvrAuBga0cm6XgqdEWkElJ4TrM=",
  "key_lifetime": 338,
  "next_rotation_on": "2009-08-21T23:48:14.329Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "LWteRoFYwcMyKJVciQUURAiDPFGMfdUFhbXqUVcJOhWkMJHQb" },
	{ "description", "BvaYjvxhveEsb" },
	{ "current_key", "e2k9Zl4HMUFVrdEUJCvrAuBga0cm6XgqdEWkElJ4TrM=" },
	{ "key_lifetime", 338 },
	{ "next_rotation_on", "2009-08-21T23:48:14.329Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "LWteRoFYwcMyKJVciQUURAiDPFGMfdUFhbXqUVcJOhWkMJHQb" )
	.add("description", "BvaYjvxhveEsb" )
	.add("current_key", "e2k9Zl4HMUFVrdEUJCvrAuBga0cm6XgqdEWkElJ4TrM=" )
	.add("key_lifetime", 338 )
	.add("next_rotation_on", "2009-08-21T23:48:14.329Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"LWteRoFYwcMyKJVciQUURAiDPFGMfdUFhbXqUVcJOhWkMJHQb\",\"description\":\"BvaYjvxhveEsb\",\"current_key\":\"e2k9Zl4HMUFVrdEUJCvrAuBga0cm6XgqdEWkElJ4TrM=\",\"key_lifetime\":338,\"next_rotation_on\":\"2009-08-21T23:48:14.329Z\"}"
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
  "name": "QmsSQaAjSuwZmfDuQPJJMwXQHGwbVIStDFwZuxoxwTdDSHafm",
  "description": "SRXvmtTMTbCztkQ",
  "current_key": "mqmsA9p7pvPzWroLSUwYNPkO5kwp/KHVj3D8ErnTXeU=",
  "key_lifetime": 241,
  "next_rotation_on": "1980-01-29T04:34:45.592Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "QmsSQaAjSuwZmfDuQPJJMwXQHGwbVIStDFwZuxoxwTdDSHafm" },
	{ "description", "SRXvmtTMTbCztkQ" },
	{ "current_key", "mqmsA9p7pvPzWroLSUwYNPkO5kwp/KHVj3D8ErnTXeU=" },
	{ "key_lifetime", 241 },
	{ "next_rotation_on", "1980-01-29T04:34:45.592Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "QmsSQaAjSuwZmfDuQPJJMwXQHGwbVIStDFwZuxoxwTdDSHafm" )
	.add("description", "SRXvmtTMTbCztkQ" )
	.add("current_key", "mqmsA9p7pvPzWroLSUwYNPkO5kwp/KHVj3D8ErnTXeU=" )
	.add("key_lifetime", 241 )
	.add("next_rotation_on", "1980-01-29T04:34:45.592Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"QmsSQaAjSuwZmfDuQPJJMwXQHGwbVIStDFwZuxoxwTdDSHafm\",\"description\":\"SRXvmtTMTbCztkQ\",\"current_key\":\"mqmsA9p7pvPzWroLSUwYNPkO5kwp/KHVj3D8ErnTXeU=\",\"key_lifetime\":241,\"next_rotation_on\":\"1980-01-29T04:34:45.592Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/2061261422
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
https://api.INSTANCE.cardsavr.io/integrators/2061261422
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
const merchantsites = await session.getMerchantSites(1262448513,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(1262448513, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1262448513,
  "name": "Amazon",
  "host": "amazon.com",
  "tags": [
    "ud+D^70SMS",
    27,
    "qALx+=w2Dn(5{j+Q[YUwJ{ZWxR"
  ],
  "interface_type": "vbs",
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
  "credit_card_page": "https://www.merchantsite.com/credit_card",
  "forgot_password_page": "https://www.merchantsite.com/forgot_password",
  "login_page": "https://www.merchantsite.com/login"
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

**Example GET request path:**<br>`/merchant_sites/1262448513`

### <a name="response-merchant_site"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this merchant site.
name | string | 
host | string | For interface type 'dcs',  hostname of the DCS broker server for the merchant site; for interface type 'vbs' hostname of the merchant_site. e.g. amazon.com
tags | array | Tags for filtering desired merchant sites.  This could either be site status (e.g. prod, development), countries supported (e.g. usa, canada), or site attributes (e.g. synthetic).  Tags can also be compounded to create combinations: (e.g. ?tags=prod,usa&tags=synthetic means all sites tagged prod and usa as well as sites tagged synthetic)
interface_type | string | Type of interface agent to use with merchant. Set to 'dcs' for a site that has direct connect support; and to 'vbs' for a site using Robotic Process Automation
required_form_fields | array | Indicates the cardholder personal information fields that are required by this site.
images | array | URLs of the images for this merchant site.  Use a filter parameter of 'image_widths', a comma delimited list of widths (e.g. image_widths=64).  Tile images with these widths will be returned.  The default is 128 and 32 width images.
account_link | array | One or more property sets with key names to populated on POST/PUT /cardsavr_accounts requests, and labels to display to the end user for the type of information being requested for this site ( e.g. Username, Password, Account Number, Email, ... ) Each property contains its 'key_name', a 'label' that defines the property, a 'secret' flag (property should be masked on input like a password), and a type.  Only properties with a type of 'initial_account_link' should be presented upon initial credential collection.  For example, an input field for 'tfa' is not displayed on initial collection.  All other non-'initial_account_link' properties will be requested while the transactiion progresses and they are only listed here for informational purposes.
messages | object | Message properties to display to end users.  Supercedes the deprecated loging properties. The message properties are mfa_label: additional informaton required for mfs challenges such as a code sent to users phone or email, additional_info_message: some contextual info sent from CardSavr to aid the user interaction, auth_message: a label to display during during the authentication phase
credit_card_page | string | Merchant's credit card entry page.
forgot_password_page | string | Merchant's forgotten password page.
login_page | string | URL of login page.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

# Notifications
Notification objects define a set of actions to be triggered by certain CardSavr events, such as session completion.
## Get notification

```javascript
const notifications = await session.getNotifications(523781682,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(523781682, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 523781682,
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
  "html_template": "uojrNCFILYElpFntKQaamDWFNsZuWm",
  "text_template": "FzkkiFLJSJZWmrsRuyYvDP",
  "created_on": "1997-09-04T13:40:26.298Z",
  "last_updated_on": "1973-11-08T02:28:56.009Z",
  "financial_institution": {
    "id": 110031612,
    "name": "oEExBusweVaucfbjqIKOsioUwBtNbfIhsGihLOCooywTnysaRuZHoSMbKQVXBOh",
    "description": "mK",
    "lookup_key": "OotKNPgTIhdJWHSnLEqzTsfjpNAHsxpxgsPNuloWiExjtvJRytrjsPmbkDhIVrR",
    "alternate_lookup_key": "KYhlXOhFiBQQVonEweHQklGEzgbscbkuOtOrqAIXabQpFVDttikoiSWVWGBvvsG",
    "last_activity": "2016-07-28T22:08:04.953Z",
    "created_on": "2003-09-11T23:05:10.792Z",
    "last_updated_on": "2007-10-30T02:16:19.896Z"
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

**Example GET request path:**<br>`/notifications/523781682`

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
  "financial_institution_id": 1850832957,
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
  "html_template": "uojrNCFILYElpFntKQaamDWFNsZuWm",
  "text_template": "FzkkiFLJSJZWmrsRuyYvDP"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1850832957 },
	{ "name", "Sample Notification" },
	{ "type", "webhook" },
	{ "event", "webhook_error_summary" },
	{ "html_template", "uojrNCFILYElpFntKQaamDWFNsZuWm" },
	{ "text_template", "FzkkiFLJSJZWmrsRuyYvDP" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1850832957 )
	.add("name", "Sample Notification" )
	.add("type", "webhook" )
	.add("event", "webhook_error_summary" )
	.add("html_template", "uojrNCFILYElpFntKQaamDWFNsZuWm" )
	.add("text_template", "FzkkiFLJSJZWmrsRuyYvDP" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1850832957,\"name\":\"Sample Notification\",\"type\":\"webhook\",\"event\":\"webhook_error_summary\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"uojrNCFILYElpFntKQaamDWFNsZuWm\",\"text_template\":\"FzkkiFLJSJZWmrsRuyYvDP\"}"
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
  "html_template": "KmjiYdWlpxlVMFVhSjfXnqCQvMWFFmVA",
  "text_template": "SUaDAGcVFBAPBeEigOJeE"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Sample Notification" },
	{ "type", "email" },
	{ "event", "merchant_site_updates_all" },
	{ "html_template", "KmjiYdWlpxlVMFVhSjfXnqCQvMWFFmVA" },
	{ "text_template", "SUaDAGcVFBAPBeEigOJeE" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Sample Notification" )
	.add("type", "email" )
	.add("event", "merchant_site_updates_all" )
	.add("html_template", "KmjiYdWlpxlVMFVhSjfXnqCQvMWFFmVA" )
	.add("text_template", "SUaDAGcVFBAPBeEigOJeE" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"Sample Notification\",\"type\":\"email\",\"event\":\"merchant_site_updates_all\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"KmjiYdWlpxlVMFVhSjfXnqCQvMWFFmVA\",\"text_template\":\"SUaDAGcVFBAPBeEigOJeE\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/523781682
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
https://api.INSTANCE.cardsavr.io/notifications/523781682
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
const notificationresults = await session.getNotificationResults(1315398487,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["notification"])});
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
JsonArray response = (JsonArray)session.get(1315398487, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1315398487,
  "last_attempt_date": "2009-10-24T23:52:28.018Z",
  "fi_lookup_key": "EYlRsscQNPBxLyRFgzHWhmBVZrKgGDlhNsHjouoAtvSqfiAjeLOgIhAdfclpfXZ",
  "cuid": "lBOMQZrlBmscgP",
  "status": "success",
  "attempts": 537665824,
  "notification_data": {
    "CmZppkwtpFOx": "za8YC+VT!A&OG}s.3",
    "QsGXiEtWcHHQ": 13,
    "wkjxcizntyFo": true
  },
  "created_on": "1972-04-11T13:39:37.860Z",
  "last_updated_on": "2009-10-10T23:36:48.531Z",
  "notification": {
    "id": 1216746928,
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
    "html_template": "zogIvKOskJyanZRHHPS",
    "text_template": "LcXMwBoz",
    "created_on": "2000-05-22T11:46:31.141Z",
    "last_updated_on": "1989-06-26T03:08:16.953Z"
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

**Example GET request path:**<br>`/notification_results/1315398487`

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
  "notification_id": 195284361,
  "fi_lookup_key": "EYlRsscQNPBxLyRFgzHWhmBVZrKgGDlhNsHjouoAtvSqfiAjeLOgIhAdfclpfXZ",
  "cuid": "lBOMQZrlBmscgP",
  "status": "success",
  "attempts": 537665824,
  "notification_data": {
    "CmZppkwtpFOx": "za8YC+VT!A&OG}s.3",
    "QsGXiEtWcHHQ": 13,
    "wkjxcizntyFo": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 195284361 },
	{ "fi_lookup_key", "EYlRsscQNPBxLyRFgzHWhmBVZrKgGDlhNsHjouoAtvSqfiAjeLOgIhAdfclpfXZ" },
	{ "cuid", "lBOMQZrlBmscgP" },
	{ "status", "success" },
	{ "attempts", 537665824 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 195284361 )
	.add("fi_lookup_key", "EYlRsscQNPBxLyRFgzHWhmBVZrKgGDlhNsHjouoAtvSqfiAjeLOgIhAdfclpfXZ" )
	.add("cuid", "lBOMQZrlBmscgP" )
	.add("status", "success" )
	.add("attempts", 537665824 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":195284361,\"fi_lookup_key\":\"EYlRsscQNPBxLyRFgzHWhmBVZrKgGDlhNsHjouoAtvSqfiAjeLOgIhAdfclpfXZ\",\"cuid\":\"lBOMQZrlBmscgP\",\"status\":\"success\",\"attempts\":537665824,\"notification_data\":{\"CmZppkwtpFOx\":\"za8YC+VT!A&OG}s.3\",\"QsGXiEtWcHHQ\":13,\"wkjxcizntyFo\":true}}"
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
const singlesitejobs = await session.getSingleSiteJobs(995538075,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_card","cardsavr_account","credential_requests"])});
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
JsonArray response = (JsonArray)session.get(995538075, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 995538075,
  "status": "VBS_ERROR",
  "status_message": "ZmiZhllOFj",
  "termination_type": "USER_DATA_FAILURE",
  "custom_data": {
    "uRVsNfIPcNWa": ".vXxtAxfs1t,oX@Qt#rQ=",
    "UtbQtETBlJNJ": 54,
    "UYNnMAmquZqQ": false
  },
  "notification_sent": true,
  "time_elapsed": 1166121565,
  "started_on": "1975-09-09T14:28:03.868Z",
  "completed_on": "2021-09-27T00:30:03.132Z",
  "created_on": "1971-02-15T14:05:17.229Z",
  "last_updated_on": "2001-01-29T01:17:40.973Z",
  "cardholder": {
    "id": 770736677,
    "type": "ephemeral",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "YzzWxBSFlUTchvvW",
    "custom_data": {
      "mRIaRvqEdRnE": ",@(A$N(5!1Vi[D1gNN=2+s#]$HR3ZDa",
      "SNRNUvELBDxQ": 92,
      "JncGtuGSxPRS": false
    },
    "created_on": "2013-06-25T21:38:26.907Z",
    "last_updated_on": "1987-10-21T06:23:54.999Z",
    "cuid": "ElDSKYEHUoCNxFd"
  },
  "cardsavr_card": {
    "id": 1006363961,
    "type": "American Express",
    "expiration_month": 12,
    "expiration_year": 24,
    "name_on_card": "Jane Smith",
    "nickname": "Jane's VISA",
    "custom_data": {
      "zqItFRcNJSDy": "tw",
      "DtzfBDLwjHfS": 69,
      "KYQtuFNtFoxL": false
    },
    "created_on": "1976-06-19T18:42:59.636Z",
    "last_updated_on": "1973-02-26T05:41:31.413Z",
    "par": "AAWGBJoGOsrbBwOQDNSVtKqmiGdtU",
    "customer_key": "qAfLSnsMrjPBBcyGMFduCJz"
  },
  "cardsavr_account": {
    "id": 921588398,
    "last_password_update": "1980-10-23T11:41:40.745Z",
    "last_saved_card": "2013-07-01T20:23:39.740Z",
    "created_on": "2014-06-09T06:41:35.069Z",
    "last_updated_on": "1981-04-16T10:34:37.055Z",
    "customer_key": "C"
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/995538075`

To hydrate all credential requests currently associated with a job, include credential_requests in the hydration header (see example at right).`

### <a name="response-place_card_on_single_site_job"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this job.
card_id | number (fk) [cards](#cards) | ID of card associated with this job.
status | string | Current status of job (e.g. pending_tfa). These names are dynamic and change frequently, so it is best to use status_message to communicate with cardholders.
status_message | string | Human readable representation of the jobs status.
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
  "cardholder_id": 1468402461,
  "card_id": 1311887504,
  "account_id": 402520100,
  "status": "VBS_ERROR",
  "custom_data": {
    "uRVsNfIPcNWa": ".vXxtAxfs1t,oX@Qt#rQ=",
    "UtbQtETBlJNJ": 54,
    "UYNnMAmquZqQ": false
  },
  "notification_sent": true,
  "time_elapsed": 1166121565,
  "started_on": "1975-09-09T14:28:03.868Z",
  "completed_on": "2021-09-27T00:30:03.132Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1468402461 },
	{ "card_id", 1311887504 },
	{ "account_id", 402520100 },
	{ "status", "VBS_ERROR" },
	{ "notification_sent", true },
	{ "time_elapsed", 1166121565 },
	{ "started_on", "1975-09-09T14:28:03.868Z" },
	{ "completed_on", "2021-09-27T00:30:03.132Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1468402461 )
	.add("card_id", 1311887504 )
	.add("account_id", 402520100 )
	.add("status", "VBS_ERROR" )
	.add("notification_sent", true )
	.add("time_elapsed", 1166121565 )
	.add("started_on", "1975-09-09T14:28:03.868Z" )
	.add("completed_on", "2021-09-27T00:30:03.132Z" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1468402461,\"card_id\":1311887504,\"account_id\":402520100,\"status\":\"VBS_ERROR\",\"custom_data\":{\"uRVsNfIPcNWa\":\".vXxtAxfs1t,oX@Qt#rQ=\",\"UtbQtETBlJNJ\":54,\"UYNnMAmquZqQ\":false},\"notification_sent\":true,\"time_elapsed\":1166121565,\"started_on\":\"1975-09-09T14:28:03.868Z\",\"completed_on\":\"2021-09-27T00:30:03.132Z\"}"
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
card_id | number | no | ID of card associated with this job.
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
  "card_id": 1882337403,
  "status": "CANCEL_REQUESTED",
  "custom_data": {
    "qOJPzLkxjNvK": "tsk[-u3.v@W*o{",
    "PblRsGGGmHtK": 0,
    "SEDMBiWobQBi": true
  },
  "notification_sent": false,
  "time_elapsed": 866246299,
  "started_on": "1986-10-20T10:44:29.409Z",
  "completed_on": "2019-05-26T00:28:15.172Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 1882337403 },
	{ "status", "CANCEL_REQUESTED" },
	{ "notification_sent", false },
	{ "time_elapsed", 866246299 },
	{ "started_on", "1986-10-20T10:44:29.409Z" },
	{ "completed_on", "2019-05-26T00:28:15.172Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 1882337403 )
	.add("status", "CANCEL_REQUESTED" )
	.add("notification_sent", false )
	.add("time_elapsed", 866246299 )
	.add("started_on", "1986-10-20T10:44:29.409Z" )
	.add("completed_on", "2019-05-26T00:28:15.172Z" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":1882337403,\"status\":\"CANCEL_REQUESTED\",\"custom_data\":{\"qOJPzLkxjNvK\":\"tsk[-u3.v@W*o{\",\"PblRsGGGmHtK\":0,\"SEDMBiWobQBi\":true},\"notification_sent\":false,\"time_elapsed\":866246299,\"started_on\":\"1986-10-20T10:44:29.409Z\",\"completed_on\":\"2019-05-26T00:28:15.172Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/995538075
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/995538075
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


# Transaction Record
Credit Card Transaction Record
## Get transaction record

