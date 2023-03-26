
# Accounts
Account objects contain the account information, such as username and password, for a particular cardhoder. They are used to log in to a cardholder's account for placing a payment card.
## Get account

```javascript
const accounts = await session.getAccounts(1637505986,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","merchant_site","cardsavr_card"])});
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
JsonArray response = (JsonArray)session.get(1637505986, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1637505986,
  "last_password_update": "1994-03-30T19:38:43.444Z",
  "last_saved_card": "2006-07-21T20:33:20.790Z",
  "created_on": "1971-02-11T21:11:21.005Z",
  "last_updated_on": "2014-11-04T04:21:40.253Z",
  "cardholder": {
    "id": 161683346,
    "type": "ephemeral",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "CcZtpBywxzkYravtgWLbhBw",
    "webhook_url": "nBlqNhaeUsKweSUSdG",
    "custom_data": {
      "pnMSevMnYeEX": "(-U{^M-9hEyanbGO0/mn5cpxTl&hzF6",
      "WWvagndwZjev": 15,
      "lVLwVWbcpwUP": true
    },
    "created_on": "1972-06-15T05:00:25.034Z",
    "last_updated_on": "1982-03-01T07:46:02.642Z",
    "cuid": "jNekwDTHGqLpPAkaw"
  },
  "merchant_site": {
    "id": 1197479981,
    "name": "Amazon",
    "note": "UREUYIptJIYKTegaAOJq",
    "host": "amazon.com",
    "tags": [
      "iV./wfwn{.)#",
      61,
      ",G"
    ],
    "interface_type": "rpa",
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
    "script_directory": "rXhZHiOqKjajbAcnpsCaEbg",
    "record_final_site_artifacts": true,
    "puppeteer_screenshot": false,
    "login_page": "https://www.merchantsite.com/login",
    "forgot_password_page": "https://www.merchantsite.com/forgot_password",
    "credit_card_page": "https://www.merchantsite.com/credit_card",
    "wallet_page": "IVYMdqSPNQPIixKD",
    "merchant_sso_group": "KOWsvddEzHJZVSKQD",
    "tier": 1540514554
  },
  "cardsavr_card": {
    "id": 1569845803,
    "type": "Unknown Type",
    "expiration_month": 12,
    "expiration_year": 24,
    "name_on_card": "Jane Smith",
    "nickname": "Jane's VISA",
    "custom_data": {
      "iLYDdBuICXjm": "xn1qJ.O+wXytcg)KHzFuHcPJ%",
      "rTEACzbUrWjC": 85,
      "sezitamsGVTX": true
    },
    "created_on": "1991-03-20T12:05:02.539Z",
    "last_updated_on": "1991-01-31T18:26:09.769Z",
    "par": "aMbJABgHzSaaZiEYBMSdarkaYGtYV",
    "customer_key": "oIBmL"
  },
  "customer_key": "tITkPukfxnHyKADhTvMTYs"
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

**Example GET request path:**<br>`/cardsavr_accounts/1637505986`

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
  "cardholder_id": 381579780,
  "merchant_site_id": 196912375,
  "customer_key": "tITkPukfxnHyKADhTvMTYs",
  "last_card_placed_id": 1073831464,
  "account_link": {
    "username": "jsmith123",
    "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 381579780 },
	{ "merchant_site_id", 196912375 },
	{ "customer_key", "tITkPukfxnHyKADhTvMTYs" },
	{ "last_card_placed_id", 1073831464 }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 381579780 )
	.add("merchant_site_id", 196912375 )
	.add("customer_key", "tITkPukfxnHyKADhTvMTYs" )
	.add("last_card_placed_id", 1073831464 )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":381579780,\"merchant_site_id\":196912375,\"customer_key\":\"tITkPukfxnHyKADhTvMTYs\",\"last_card_placed_id\":1073831464,\"account_link\":{\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}}"
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
  "last_card_placed_id": 1610151412,
  "account_link": {
    "username": "jsmith123",
    "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
  }
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 1610151412 }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 1610151412 )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":1610151412,\"account_link\":{\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1637505986
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
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1637505986
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
const addresses = await session.getAddresses(1711081592,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder"])});
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
JsonArray response = (JsonArray)session.get(1711081592, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1711081592,
  "address1": "jtsVFhLVBcnhXzJAmswEFdIoZrgTfIFjXWcGiZjAhogpkNqWiFkfuWXCsDNPySKBPOrjxzawxUTTlFUiXJbRNYdVjEuVARIyhBl",
  "address2": "YYFJQzONeRrwepAzeSKRhQBNYbriUjbPWaofyYhFjkCqBdloVFYoikUXHSzlRoSrsnJYIHVmAmtqmDjyhDOKNzdcfjTsQfZlxdo",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "KxOBMNxXdsUs@pcNfQt.DJw",
  "phone_number": "2065555555",
  "created_on": "2021-09-17T15:22:10.462Z",
  "last_updated_on": "2004-09-16T08:16:17.218Z",
  "cardholder": {
    "id": 441832953,
    "type": "persistent_all",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "oUpHYMqSTHS",
    "webhook_url": "sSpHeUIkStFEKniOvoAZJqsHldJz",
    "custom_data": {
      "miugMCjDyKsH": "SCs]vC9z@mA]q8ltQHs",
      "joTmuOLwiCep": 64,
      "vmVJqyyuCnzz": false
    },
    "created_on": "1984-08-06T23:01:39.640Z",
    "last_updated_on": "2022-03-11T23:37:17.326Z",
    "cuid": "aJwsysWXPm"
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

**Example GET request path:**<br>`/cardsavr_addresses/1711081592`

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
  "cardholder_id": 1504938596,
  "address1": "jtsVFhLVBcnhXzJAmswEFdIoZrgTfIFjXWcGiZjAhogpkNqWiFkfuWXCsDNPySKBPOrjxzawxUTTlFUiXJbRNYdVjEuVARIyhBl",
  "address2": "YYFJQzONeRrwepAzeSKRhQBNYbriUjbPWaofyYhFjkCqBdloVFYoikUXHSzlRoSrsnJYIHVmAmtqmDjyhDOKNzdcfjTsQfZlxdo",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "KxOBMNxXdsUs@pcNfQt.DJw",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1504938596 },
	{ "address1", "jtsVFhLVBcnhXzJAmswEFdIoZrgTfIFjXWcGiZjAhogpkNqWiFkfuWXCsDNPySKBPOrjxzawxUTTlFUiXJbRNYdVjEuVARIyhBl" },
	{ "address2", "YYFJQzONeRrwepAzeSKRhQBNYbriUjbPWaofyYhFjkCqBdloVFYoikUXHSzlRoSrsnJYIHVmAmtqmDjyhDOKNzdcfjTsQfZlxdo" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "KxOBMNxXdsUs@pcNfQt.DJw" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1504938596 )
	.add("address1", "jtsVFhLVBcnhXzJAmswEFdIoZrgTfIFjXWcGiZjAhogpkNqWiFkfuWXCsDNPySKBPOrjxzawxUTTlFUiXJbRNYdVjEuVARIyhBl" )
	.add("address2", "YYFJQzONeRrwepAzeSKRhQBNYbriUjbPWaofyYhFjkCqBdloVFYoikUXHSzlRoSrsnJYIHVmAmtqmDjyhDOKNzdcfjTsQfZlxdo" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "KxOBMNxXdsUs@pcNfQt.DJw" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1504938596,\"address1\":\"jtsVFhLVBcnhXzJAmswEFdIoZrgTfIFjXWcGiZjAhogpkNqWiFkfuWXCsDNPySKBPOrjxzawxUTTlFUiXJbRNYdVjEuVARIyhBl\",\"address2\":\"YYFJQzONeRrwepAzeSKRhQBNYbriUjbPWaofyYhFjkCqBdloVFYoikUXHSzlRoSrsnJYIHVmAmtqmDjyhDOKNzdcfjTsQfZlxdo\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"KxOBMNxXdsUs@pcNfQt.DJw\",\"phone_number\":\"2065555555\"}"
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
  "address1": "KbXUepLpBCIpOHiKbAfaPRnYLuXnQJFIHpFnVnAImTUHFLtzQFWQndJgxrpftKxrdUygwBecfCcbZoQeeOIqjhqaFTypuwxXHoB",
  "address2": "AvcuQzpXRnQNepeyfmAfnKVpucxzmtmnpFsrRmaXMLoGHPCDxZrfEmnPIVTaDpNPWOnoYPuonJQBNsrXhHBTbGBuMclKOFMfAOH",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "JlDVziEVfVlu@fTsBmr.ttO",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "KbXUepLpBCIpOHiKbAfaPRnYLuXnQJFIHpFnVnAImTUHFLtzQFWQndJgxrpftKxrdUygwBecfCcbZoQeeOIqjhqaFTypuwxXHoB" },
	{ "address2", "AvcuQzpXRnQNepeyfmAfnKVpucxzmtmnpFsrRmaXMLoGHPCDxZrfEmnPIVTaDpNPWOnoYPuonJQBNsrXhHBTbGBuMclKOFMfAOH" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "JlDVziEVfVlu@fTsBmr.ttO" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "KbXUepLpBCIpOHiKbAfaPRnYLuXnQJFIHpFnVnAImTUHFLtzQFWQndJgxrpftKxrdUygwBecfCcbZoQeeOIqjhqaFTypuwxXHoB" )
	.add("address2", "AvcuQzpXRnQNepeyfmAfnKVpucxzmtmnpFsrRmaXMLoGHPCDxZrfEmnPIVTaDpNPWOnoYPuonJQBNsrXhHBTbGBuMclKOFMfAOH" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", false )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "JlDVziEVfVlu@fTsBmr.ttO" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"KbXUepLpBCIpOHiKbAfaPRnYLuXnQJFIHpFnVnAImTUHFLtzQFWQndJgxrpftKxrdUygwBecfCcbZoQeeOIqjhqaFTypuwxXHoB\",\"address2\":\"AvcuQzpXRnQNepeyfmAfnKVpucxzmtmnpFsrRmaXMLoGHPCDxZrfEmnPIVTaDpNPWOnoYPuonJQBNsrXhHBTbGBuMclKOFMfAOH\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"JlDVziEVfVlu@fTsBmr.ttO\",\"phone_number\":\"2065555555\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1711081592
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1711081592
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
const bins = await session.getBins(1077033969,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(1077033969, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1077033969,
  "custom_data": {
    "IaHrVDaUBCUY": "X@W{-b#bZvUHOZ/YX",
    "yBTpMzGXnoUX": 92,
    "CcNMIASQzRRX": false
  },
  "created_on": "1979-07-07T17:34:31.290Z",
  "last_updated_on": "1979-03-12T18:52:44.073Z",
  "financial_institution": {
    "id": 1391864704,
    "name": "hBBDOYkEZALIjLIHskhuagFHlRqtsiZlQwmOrmVVGDBkHfqCizMAdXycqIpHDbF",
    "description": "HlqSyywjCxjvkRwvB",
    "lookup_key": "YtGNiIvwWRKxZZUfRoBatGFSiinulNdbqKdTSWWSCgjnOUYYfFyqjUmIZDMLRfj",
    "alternate_lookup_key": "mUidqcrDANYoNjSKUiwLPIhQLjTOeTGFUMZONSUwYWQqGEFBLBadMOBSFgjeKFs",
    "last_activity": "1994-06-02T22:34:32.445Z",
    "created_on": "2020-11-27T05:01:45.981Z",
    "last_updated_on": "2001-10-20T17:24:56.013Z"
  },
  "bank_identification_number": "47342080"
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

**Example GET request path:**<br>`/cardsavr_bins/1077033969`

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
  "financial_institution_id": 1608159204,
  "bank_identification_number": "47342080",
  "custom_data": {
    "IaHrVDaUBCUY": "X@W{-b#bZvUHOZ/YX",
    "yBTpMzGXnoUX": 92,
    "CcNMIASQzRRX": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1608159204 },
	{ "bank_identification_number", "47342080" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1608159204 )
	.add("bank_identification_number", "47342080" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1608159204,\"bank_identification_number\":\"47342080\",\"custom_data\":{\"IaHrVDaUBCUY\":\"X@W{-b#bZvUHOZ/YX\",\"yBTpMzGXnoUX\":92,\"CcNMIASQzRRX\":false}}"
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
  "financial_institution_id": 2069503954,
  "custom_data": {
    "NbiRmKEEnaGF": "e)*L8+-/s!2D",
    "ZHHqtPmrQCRq": 9,
    "HzCGkCTdXwBQ": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 2069503954 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 2069503954 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":2069503954,\"custom_data\":{\"NbiRmKEEnaGF\":\"e)*L8+-/s!2D\",\"ZHHqtPmrQCRq\":9,\"HzCGkCTdXwBQ\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1077033969
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1077033969
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
const cardplacementresults = await session.getCardPlacementResults(1460347968,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution","merchant_site","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(1460347968, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1460347968,
  "merchant_site_hostname": "tqkOkneBUyRJgpcWnUkULZoKVKBoLQcTEfHgjuxVRNDfGjgFaQkfiouWHFuDxFlHcJKiwwEXKpinPkuklqjsXZDJhaifgbUHoEiXeQjwcNTgPyTEEpfJtPYxIOEgPJxGCtJMjbsCYSRJXdylPVKeuffzTGoSSnhtAeikeuUqhdcGanLJqmKeGOxhJNRGMLjLxbNfyPfIxObUPaqtdReRrcOVxccAzNTOGHCbBfPfAMgJqxRSzJOXlAkCnIuPiz",
  "meta_key": "MB9810411",
  "fi_name": "USyDyjGrfogtpXfKovfknmBXJMJjQVxhTdtfmSAXGcXbdJiOOxixGiQZFflsaEu",
  "bank_identification_number": "22411964",
  "cuid": "WDBDctiMXMphgDTYFxlAnJZljpkrqFj",
  "par": "aHHfdNNMtGEWCTOHLWNnrwTaprtNE",
  "card_customer_key": "VImITx",
  "account_customer_key": "LDtCmTyFlhrXg",
  "status": "SUCCESSFUL",
  "status_message": "Successful",
  "termination_type": "BILLABLE",
  "custom_data": {
    "qQjPMIyAUZDa": "Jc.",
    "KfmoFXqBYsWb": 66,
    "NhYBlrkUIPxo": true
  },
  "time_elapsed": 315698992,
  "first_6": "kOEyyoWSgwJLnzYkwwGSbkrdLhWQIYJO",
  "first_7": "AgZuDTCToNObYeAMpNdWFTklthwYXtvi",
  "first_8": "jSEtbIPZjceCtoBTkHRxofFtjMoZATNO",
  "trace": "cblezgJaWYUbgeIQ",
  "email_sent": true,
  "completed_on": "1972-06-13T05:56:05.322Z",
  "created_on": "1975-09-19T04:38:20.989Z",
  "last_updated_on": "2023-03-24T20:49:54.656Z",
  "financial_institution": {
    "id": 1064576996,
    "name": "GUweuAoITCzBRbVefCorVNVThgdZJKILcnwCTmdEEmLYUCSdIUQvDlUCutVgsBP",
    "description": "sNjYmapIsnEJR",
    "lookup_key": "WHSfKGYkrylEhVggQVXvPjMfOHMroWahKaDVSIheiQsrdOJvKrPdXxsaGOMjHCO",
    "alternate_lookup_key": "VTxlPglLnBFZmQHZUCVnRGBVuWhTAoNKFEZSDeiyPocaoirUYEiiGezexVWaezG",
    "last_activity": "2011-12-27T09:49:11.028Z",
    "created_on": "1971-09-22T18:54:46.723Z",
    "last_updated_on": "1980-08-21T02:17:17.887Z"
  },
  "merchant_site": {
    "id": 1209359753,
    "name": "Amazon",
    "note": "qgOtdHInSToAFkLQ",
    "host": "amazon.com",
    "tags": [
      "krjFvawIme/+YC",
      78,
      "MkKsG8&D{AA2"
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
    "script_directory": "AJONxbHFpRHWYadLVjkhXEp",
    "record_final_site_artifacts": true,
    "puppeteer_screenshot": false,
    "login_page": "https://www.merchantsite.com/login",
    "forgot_password_page": "https://www.merchantsite.com/forgot_password",
    "credit_card_page": "https://www.merchantsite.com/credit_card",
    "wallet_page": "NXYkNQUTUupYjtCkSoaK",
    "merchant_sso_group": "nwOjxAJBWlJge",
    "tier": 1088329359
  },
  "cardsavr_bin": {
    "id": 1510023611,
    "custom_data": {
      "nCkRSoiXhQyj": "e8vbKB,%01R~CnJLMFBKE9&,jA)",
      "kjTWIDAxNiKH": 0,
      "vpAUdNDqYtIo": true
    },
    "created_on": "2022-11-15T05:57:26.064Z",
    "last_updated_on": "1992-09-05T16:26:38.728Z",
    "bank_identification_number": "68271220"
  },
  "place_card_on_single_site_job_id": 1326781438
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

**Example GET request path:**<br>`/card_placement_results/1460347968`

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
const cards = await session.getCards(162799606,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_address","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(162799606, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 162799606,
  "type": "American Express",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "KkxjoDSELtSn": "[7(Qd8sw%huw),rYYu",
    "vjYRYOsTbfHi": 78,
    "edZhLqpDscVn": true
  },
  "created_on": "1972-12-10T15:22:38.593Z",
  "last_updated_on": "2002-03-22T02:53:48.817Z",
  "cardholder": {
    "id": 544786090,
    "type": "persistent_creds",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "jBqZovDqfDNBQgeZms",
    "webhook_url": "ZX",
    "custom_data": {
      "CiVEBWFAWTKh": ".6nMmkL~y}01X#dsY1Zi",
      "pesFxdIYwmeV": 95,
      "ZPWbknczScZW": true
    },
    "created_on": "1976-09-15T17:07:26.459Z",
    "last_updated_on": "1983-03-06T18:24:40.299Z",
    "cuid": "cMhVsTwcyiinoIgsRZvCEiiNfasNG"
  },
  "cardsavr_address": {
    "id": 625257271,
    "address1": "GgnhMJiFicLJYVDtnZLVlpzafNdRKRUyyGBhIDJiZhHiTeHmbRnrjSCQDNFuljhIqdrwlsJhljtIdiVPSvpQUJWeyULvueHJIin",
    "address2": "PmPTjxIpmTCWHbPAaKgphTtOmNCFPevLTBWBgBnYbtPmyafzctuMXGyWMzmoGyJotnyuiMMfgAFwApdjJxcnvECtqwPmGQFckIX",
    "city": "Seattle",
    "subnational": "WA",
    "postal_code": "98177",
    "postal_other": "98177-0124",
    "country": "USA",
    "is_primary": false,
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "syFcKWMFKDpT@kCAEfl.nQu",
    "phone_number": "2065555555",
    "created_on": "1975-04-25T04:31:40.083Z",
    "last_updated_on": "1997-05-13T06:26:47.588Z"
  },
  "cardsavr_bin": {
    "id": 906041456,
    "custom_data": {
      "FHArmfTeTyUg": "rw@L=X-ia/l%s1@(}vrm",
      "iCvTvUzbDget": 42,
      "MIbJNtuLrZWA": false
    },
    "created_on": "1973-07-01T00:49:30.401Z",
    "last_updated_on": "2019-10-03T09:56:38.466Z",
    "bank_identification_number": "74659844"
  },
  "par": "cLCVhWzdVZZHznCxvreEoSJPLVhrk",
  "customer_key": "LpUvPwpkINang"
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

**Example GET request path:**<br>`/cardsavr_cards/162799606`

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
  "cardholder_id": 2114883864,
  "address_id": 1892478435,
  "bin_id": 1479724720,
  "par": "cLCVhWzdVZZHznCxvreEoSJPLVhrk",
  "customer_key": "LpUvPwpkINang",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "KkxjoDSELtSn": "[7(Qd8sw%huw),rYYu",
    "vjYRYOsTbfHi": 78,
    "edZhLqpDscVn": true
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 2114883864 },
	{ "address_id", 1892478435 },
	{ "bin_id", 1479724720 },
	{ "par", "cLCVhWzdVZZHznCxvreEoSJPLVhrk" },
	{ "customer_key", "LpUvPwpkINang" },
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
	.add("cardholder_id", 2114883864 )
	.add("address_id", 1892478435 )
	.add("bin_id", 1479724720 )
	.add("par", "cLCVhWzdVZZHznCxvreEoSJPLVhrk" )
	.add("customer_key", "LpUvPwpkINang" )
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
curl -d "{\"cardholder_id\":2114883864,\"address_id\":1892478435,\"bin_id\":1479724720,\"par\":\"cLCVhWzdVZZHznCxvreEoSJPLVhrk\",\"customer_key\":\"LpUvPwpkINang\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"Jane's VISA\",\"custom_data\":{\"KkxjoDSELtSn\":\"[7(Qd8sw%huw),rYYu\",\"vjYRYOsTbfHi\":78,\"edZhLqpDscVn\":true}}"
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
  "bin_id": 1312023764,
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "nzieohBvFeIa": "QOhG=W4@@irmgV^RKbAEeW1Q[",
    "tYrvhlqVrMPA": 6,
    "QudWRgWAGRmY": true
  },
  "pan": "4111111111111111"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "bin_id", 1312023764 },
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
	.add("bin_id", 1312023764 )
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
curl -d "{\"bin_id\":1312023764,\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"Jane's VISA\",\"custom_data\":{\"nzieohBvFeIa\":\"QOhG=W4@@irmgV^RKbAEeW1Q[\",\"tYrvhlqVrMPA\":6,\"QudWRgWAGRmY\":true},\"pan\":\"4111111111111111\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/162799606
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/162799606
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
const cardholders = await session.getCardholders(1895565014,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution","integrator"])});
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
JsonArray response = (JsonArray)session.get(1895565014, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1895565014,
  "type": "persistent_creds",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "kDmosagmvpglpaXXMrELuiPciXpHPPf",
  "webhook_url": "dQgvkqHFaMBZrKfP",
  "custom_data": {
    "QGOtTcKyiKRJ": "hY!Q{@E]{yNFo-_sks+8m",
    "foTKTPEcEWzU": 18,
    "PFagiHHmSKwZ": true
  },
  "created_on": "1984-07-29T16:03:36.973Z",
  "last_updated_on": "1988-04-15T22:58:59.265Z",
  "financial_institution": {
    "id": 2146815518,
    "name": "FwQlnusTJfmreMdlFTzfaCTFfCwhWttlRRaZNUsfteFoSDQiyVIGVTuXEjHlwgw",
    "description": "HwbHbhYnnBkiMlQJOtMyiQiLWPMI",
    "lookup_key": "hSIEESkzrxTFafRPCYAkjBaBJElGwvEHXynmDDWEOnhlWGInItgrLSKwdTsoYlM",
    "alternate_lookup_key": "ATdoLwTgTPPJAWNQLOlNSyFngrncVDKNhUyVZxvuHjDQRFlvGoIHcvsdQAxmscc",
    "last_activity": "2015-08-24T01:28:46.116Z",
    "created_on": "2002-03-22T10:32:23.573Z",
    "last_updated_on": "1997-01-27T14:34:11.971Z"
  },
  "integrator": {
    "id": 1771317070,
    "name": "szJgRpfLzyIalZoMYbBXHdLvjSkEOVDsFjRPrsuBuKGHTGULE",
    "description": "TquzdHzLiDFRAFNYDPEiGrHtwTJjj",
    "current_key": "t20m2yYED/aNMxycE6xt8HDpe2orVm5DQHkLfdD+5H8=",
    "key_lifetime": 314,
    "next_rotation_on": "1983-10-30T10:47:20.523Z",
    "created_on": "2020-04-23T17:57:31.535Z",
    "last_updated_on": "2011-02-12T17:22:21.669Z"
  },
  "cuid": "cBBFMoQzTwu"
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

**Example GET request path:**<br>`/cardholders/1895565014`

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
webhook_url | string | A cardholder specific url for posting job reults following the end of a session.  This overrides the FI global settiings in the portal.
custom_data | object | Additional data that can be added to the cardholder if needed.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cuid | string | External unique ID for cardholder--can be account_id, email address, phone number, etc.  A random number will be gnenerated if not provided.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create cardholder

```javascript
const cardholder = await session.createCardholder({
  "cuid": "cBBFMoQzTwu",
  "type": "persistent_creds",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "kDmosagmvpglpaXXMrELuiPciXpHPPf",
  "webhook_url": "dQgvkqHFaMBZrKfP",
  "custom_data": {
    "QGOtTcKyiKRJ": "hY!Q{@E]{yNFo-_sks+8m",
    "foTKTPEcEWzU": 18,
    "PFagiHHmSKwZ": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cuid", "cBBFMoQzTwu" },
	{ "type", "persistent_creds" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "kDmosagmvpglpaXXMrELuiPciXpHPPf" },
	{ "webhook_url", "dQgvkqHFaMBZrKfP" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cuid", "cBBFMoQzTwu" )
	.add("type", "persistent_creds" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "kDmosagmvpglpaXXMrELuiPciXpHPPf" )
	.add("webhook_url", "dQgvkqHFaMBZrKfP" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"cuid\":\"cBBFMoQzTwu\",\"type\":\"persistent_creds\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"kDmosagmvpglpaXXMrELuiPciXpHPPf\",\"webhook_url\":\"dQgvkqHFaMBZrKfP\",\"custom_data\":{\"QGOtTcKyiKRJ\":\"hY!Q{@E]{yNFo-_sks+8m\",\"foTKTPEcEWzU\":18,\"PFagiHHmSKwZ\":true}}"
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
  "type": "persistent_creds",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "VWgtwiMalINyBCCxeatvOavkoQNdx",
  "webhook_url": "ZTbDbodQziyKlfBa",
  "custom_data": {
    "NtCKkWUYFatY": "WuJ~Eg~tco8aMXLkPFc}XZ1dBd#0S+",
    "fJTLBJJHzxEJ": 88,
    "lFWqjNgmcgwN": false
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
	{ "meta_key", "VWgtwiMalINyBCCxeatvOavkoQNdx" },
	{ "webhook_url", "ZTbDbodQziyKlfBa" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("type", "persistent_creds" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "VWgtwiMalINyBCCxeatvOavkoQNdx" )
	.add("webhook_url", "ZTbDbodQziyKlfBa" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"type\":\"persistent_creds\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"VWgtwiMalINyBCCxeatvOavkoQNdx\",\"webhook_url\":\"ZTbDbodQziyKlfBa\",\"custom_data\":{\"NtCKkWUYFatY\":\"WuJ~Eg~tco8aMXLkPFc}XZ1dBd#0S+\",\"fJTLBJJHzxEJ\":88,\"lFWqjNgmcgwN\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/1895565014
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
webhook_url | string | A cardholder specific url for posting job reults following the end of a session.  This overrides the FI global settiings in the portal.
custom_data | object | Additional data that can be added to the cardholder if needed.

See [cardholder response parameters](#response-cardholder).


## Delete cardholder

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/1895565014
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
const users = await session.getUsers(1632111398,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(1632111398, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1632111398,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1998-02-06T22:05:10.628Z",
  "is_locked": false,
  "password_lifetime": 87,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "swch_agent",
  "next_rotation_on": "2011-01-15T04:34:42.475Z",
  "created_on": "1987-04-26T23:29:36.221Z",
  "last_updated_on": "1980-07-20T12:56:45.072Z",
  "username": "jsmith123",
  "financial_institution": {
    "id": 813707152,
    "name": "PQAMCxISkPUygOnNdlJKJZhinRNEOBHYaueHSDHMkjSzrpWJZslLAGawKhJuXSY",
    "description": "RcRULLCrdEd",
    "lookup_key": "UzGLAXCAbkOPsbaSAERBbGQhyQmItizDtamdXMyXnweKimmCBxkOVPOfDaQvwso",
    "alternate_lookup_key": "zQCOwfmxKkQRNOkNbvWXmwaXYSZWtasxxAaajNUihPjrXjRWgCUegyEbclEDxBy",
    "last_activity": "1977-04-05T17:06:40.786Z",
    "created_on": "2000-07-21T08:15:04.604Z",
    "last_updated_on": "1994-01-08T20:12:35.642Z"
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

**Example GET request path:**<br>`/cardsavr_users/1632111398`

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
  "financial_institution_id": 1672390360,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 87,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "swch_agent",
  "next_rotation_on": "2011-01-15T04:34:42.475Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1672390360 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 87 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "swch_agent" },
	{ "next_rotation_on", "2011-01-15T04:34:42.475Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1672390360 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 87 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "swch_agent" )
	.add("next_rotation_on", "2011-01-15T04:34:42.475Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1672390360,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":87,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"swch_agent\",\"next_rotation_on\":\"2011-01-15T04:34:42.475Z\"}"
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
  "financial_institution_id": 1755515440,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 267,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_agent",
  "next_rotation_on": "2015-10-31T06:03:13.910Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1755515440 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 267 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "cardholder_agent" },
	{ "next_rotation_on", "2015-10-31T06:03:13.910Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1755515440 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 267 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "cardholder_agent" )
	.add("next_rotation_on", "2015-10-31T06:03:13.910Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1755515440,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":267,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"cardholder_agent\",\"next_rotation_on\":\"2015-10-31T06:03:13.910Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/1632111398
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/1632111398
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
const financialinstitutions = await session.getFinancialInstitutions(2132792919,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(2132792919, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2132792919,
  "name": "EIVBPcnxvDqYcKcPZmemcYPPEPxDEUkHceBmGMnTiWQKveIboetJPqcBVBfBMCs",
  "description": "QLyGaKAR",
  "lookup_key": "URkXCeIVDZeeFVdNHbUeYoIBYFrcbcfqWXPIInaUSNTBWClTUYrYjvYHrXNBktU",
  "alternate_lookup_key": "ysRLYpewhsbbgnXgAGEvjdmMARzjwGmHRvgtZWlacFLjCMyNNXmgTncQUDdtsQk",
  "last_activity": "1989-06-03T07:30:09.280Z",
  "created_on": "2021-03-28T03:06:11.643Z",
  "last_updated_on": "2006-03-13T03:26:56.222Z"
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

**Example GET request path:**<br>`/financial_institutions/2132792919`

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
  "name": "EIVBPcnxvDqYcKcPZmemcYPPEPxDEUkHceBmGMnTiWQKveIboetJPqcBVBfBMCs",
  "description": "QLyGaKAR",
  "lookup_key": "URkXCeIVDZeeFVdNHbUeYoIBYFrcbcfqWXPIInaUSNTBWClTUYrYjvYHrXNBktU",
  "alternate_lookup_key": "ysRLYpewhsbbgnXgAGEvjdmMARzjwGmHRvgtZWlacFLjCMyNNXmgTncQUDdtsQk"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "EIVBPcnxvDqYcKcPZmemcYPPEPxDEUkHceBmGMnTiWQKveIboetJPqcBVBfBMCs" },
	{ "description", "QLyGaKAR" },
	{ "lookup_key", "URkXCeIVDZeeFVdNHbUeYoIBYFrcbcfqWXPIInaUSNTBWClTUYrYjvYHrXNBktU" },
	{ "alternate_lookup_key", "ysRLYpewhsbbgnXgAGEvjdmMARzjwGmHRvgtZWlacFLjCMyNNXmgTncQUDdtsQk" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "EIVBPcnxvDqYcKcPZmemcYPPEPxDEUkHceBmGMnTiWQKveIboetJPqcBVBfBMCs" )
	.add("description", "QLyGaKAR" )
	.add("lookup_key", "URkXCeIVDZeeFVdNHbUeYoIBYFrcbcfqWXPIInaUSNTBWClTUYrYjvYHrXNBktU" )
	.add("alternate_lookup_key", "ysRLYpewhsbbgnXgAGEvjdmMARzjwGmHRvgtZWlacFLjCMyNNXmgTncQUDdtsQk" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"EIVBPcnxvDqYcKcPZmemcYPPEPxDEUkHceBmGMnTiWQKveIboetJPqcBVBfBMCs\",\"description\":\"QLyGaKAR\",\"lookup_key\":\"URkXCeIVDZeeFVdNHbUeYoIBYFrcbcfqWXPIInaUSNTBWClTUYrYjvYHrXNBktU\",\"alternate_lookup_key\":\"ysRLYpewhsbbgnXgAGEvjdmMARzjwGmHRvgtZWlacFLjCMyNNXmgTncQUDdtsQk\"}"
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
  "name": "oTOqwzChYFJtkssyJwofetcXPhWpuaPdYUhbvFnMqQHjMOaNsYJLhwBqRzpGDrY",
  "description": "EjdnFkLNMsLSlgKuia",
  "lookup_key": "XoXdzAMHpcSwEdidGfvtzITZNDzhKohTMBXgyvrkVrwCGhVIWobNaICOnHaKfdu",
  "alternate_lookup_key": "NcsBWGYaRkqwQdArXiSkHGJgUSfjsJJohQVrPyyByEiGhFqVodowwRROnLhAPRU"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "oTOqwzChYFJtkssyJwofetcXPhWpuaPdYUhbvFnMqQHjMOaNsYJLhwBqRzpGDrY" },
	{ "description", "EjdnFkLNMsLSlgKuia" },
	{ "lookup_key", "XoXdzAMHpcSwEdidGfvtzITZNDzhKohTMBXgyvrkVrwCGhVIWobNaICOnHaKfdu" },
	{ "alternate_lookup_key", "NcsBWGYaRkqwQdArXiSkHGJgUSfjsJJohQVrPyyByEiGhFqVodowwRROnLhAPRU" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "oTOqwzChYFJtkssyJwofetcXPhWpuaPdYUhbvFnMqQHjMOaNsYJLhwBqRzpGDrY" )
	.add("description", "EjdnFkLNMsLSlgKuia" )
	.add("lookup_key", "XoXdzAMHpcSwEdidGfvtzITZNDzhKohTMBXgyvrkVrwCGhVIWobNaICOnHaKfdu" )
	.add("alternate_lookup_key", "NcsBWGYaRkqwQdArXiSkHGJgUSfjsJJohQVrPyyByEiGhFqVodowwRROnLhAPRU" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"oTOqwzChYFJtkssyJwofetcXPhWpuaPdYUhbvFnMqQHjMOaNsYJLhwBqRzpGDrY\",\"description\":\"EjdnFkLNMsLSlgKuia\",\"lookup_key\":\"XoXdzAMHpcSwEdidGfvtzITZNDzhKohTMBXgyvrkVrwCGhVIWobNaICOnHaKfdu\",\"alternate_lookup_key\":\"NcsBWGYaRkqwQdArXiSkHGJgUSfjsJJohQVrPyyByEiGhFqVodowwRROnLhAPRU\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/2132792919
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
https://api.INSTANCE.cardsavr.io/financial_institutions/2132792919
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
const integrators = await session.getIntegrators(483018809,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(483018809, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 483018809,
  "name": "OTdJqBOjuzdkhUZymUKugMDNepxjTBEOFJfGoUKncJZQqjxZp",
  "description": "EXDsisAuyTKwWZiUEwvHEqWErJl",
  "current_key": "qT4K8CMS0plncQH7agSEohTiNcHza7LQzgwKHZViMVI=",
  "key_lifetime": 184,
  "next_rotation_on": "2004-08-09T00:00:13.624Z",
  "created_on": "1987-10-06T09:52:11.956Z",
  "last_updated_on": "2007-09-08T11:36:23.134Z"
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

**Example GET request path:**<br>`/integrators/483018809`

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
  "name": "OTdJqBOjuzdkhUZymUKugMDNepxjTBEOFJfGoUKncJZQqjxZp",
  "description": "EXDsisAuyTKwWZiUEwvHEqWErJl",
  "current_key": "qT4K8CMS0plncQH7agSEohTiNcHza7LQzgwKHZViMVI=",
  "key_lifetime": 184,
  "next_rotation_on": "2004-08-09T00:00:13.624Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "OTdJqBOjuzdkhUZymUKugMDNepxjTBEOFJfGoUKncJZQqjxZp" },
	{ "description", "EXDsisAuyTKwWZiUEwvHEqWErJl" },
	{ "current_key", "qT4K8CMS0plncQH7agSEohTiNcHza7LQzgwKHZViMVI=" },
	{ "key_lifetime", 184 },
	{ "next_rotation_on", "2004-08-09T00:00:13.624Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "OTdJqBOjuzdkhUZymUKugMDNepxjTBEOFJfGoUKncJZQqjxZp" )
	.add("description", "EXDsisAuyTKwWZiUEwvHEqWErJl" )
	.add("current_key", "qT4K8CMS0plncQH7agSEohTiNcHza7LQzgwKHZViMVI=" )
	.add("key_lifetime", 184 )
	.add("next_rotation_on", "2004-08-09T00:00:13.624Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"OTdJqBOjuzdkhUZymUKugMDNepxjTBEOFJfGoUKncJZQqjxZp\",\"description\":\"EXDsisAuyTKwWZiUEwvHEqWErJl\",\"current_key\":\"qT4K8CMS0plncQH7agSEohTiNcHza7LQzgwKHZViMVI=\",\"key_lifetime\":184,\"next_rotation_on\":\"2004-08-09T00:00:13.624Z\"}"
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
  "name": "IdlxVQuOUbLiXlWQklLliHoUGRZQRVZjThIWfGEKfBswWtcrc",
  "description": "KLeFzJiTFDZ",
  "current_key": "yJs75jMKpwfRSlhL0KOYYKqXWaii3wz14PQAlRqD8I0=",
  "key_lifetime": 189,
  "next_rotation_on": "1999-11-01T11:12:32.711Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "IdlxVQuOUbLiXlWQklLliHoUGRZQRVZjThIWfGEKfBswWtcrc" },
	{ "description", "KLeFzJiTFDZ" },
	{ "current_key", "yJs75jMKpwfRSlhL0KOYYKqXWaii3wz14PQAlRqD8I0=" },
	{ "key_lifetime", 189 },
	{ "next_rotation_on", "1999-11-01T11:12:32.711Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "IdlxVQuOUbLiXlWQklLliHoUGRZQRVZjThIWfGEKfBswWtcrc" )
	.add("description", "KLeFzJiTFDZ" )
	.add("current_key", "yJs75jMKpwfRSlhL0KOYYKqXWaii3wz14PQAlRqD8I0=" )
	.add("key_lifetime", 189 )
	.add("next_rotation_on", "1999-11-01T11:12:32.711Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"IdlxVQuOUbLiXlWQklLliHoUGRZQRVZjThIWfGEKfBswWtcrc\",\"description\":\"KLeFzJiTFDZ\",\"current_key\":\"yJs75jMKpwfRSlhL0KOYYKqXWaii3wz14PQAlRqD8I0=\",\"key_lifetime\":189,\"next_rotation_on\":\"1999-11-01T11:12:32.711Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/483018809
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
https://api.INSTANCE.cardsavr.io/integrators/483018809
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
const merchantsites = await session.getMerchantSites(1719710308,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(1719710308, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1719710308,
  "name": "Amazon",
  "note": "a",
  "host": "amazon.com",
  "tags": [
    "D~CB{}JP{qhU#Md%$7M1*1L",
    74,
    "8bhW2jO^[GU~~+@p)ln"
  ],
  "interface_type": "rpa",
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
  "script_directory": "BgwaIAPdnVZa",
  "record_final_site_artifacts": true,
  "puppeteer_screenshot": true,
  "login_page": "https://www.merchantsite.com/login",
  "forgot_password_page": "https://www.merchantsite.com/forgot_password",
  "credit_card_page": "https://www.merchantsite.com/credit_card",
  "wallet_page": "gYnLDNiOLQqiuobIHynemaQKQLX",
  "merchant_sso_group": "cfVuaLeAxDLDKWtJbUhrVgsoTMvWlf",
  "tier": 1689679084
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

**Example GET request path:**<br>`/merchant_sites/1719710308`

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
const notifications = await session.getNotifications(2013149238,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(2013149238, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2013149238,
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
  "html_template": "FinMEjuIdYOplkHBLbfVeBUyeYPiau",
  "text_template": "aLoBxfJ",
  "created_on": "1988-05-17T09:19:57.840Z",
  "last_updated_on": "1993-07-06T09:31:45.570Z",
  "financial_institution": {
    "id": 1544934126,
    "name": "grgbtGoGCIIGrfvCGLVaJTGyoLGuNMaPBjjQlipzEPOZkgnsOUfSqelPHopkLfG",
    "description": "DtkH",
    "lookup_key": "xmXRvUbkHjKxXMhrntEfqZAqwGlrJvmUoFjQTBLeaUNEfBWTFprZrpfOjkiCJYV",
    "alternate_lookup_key": "eqrZmtLVMYiilHPrUFMbUFyNHJtmwMGlkioGefNWwWGcPqqkRnbaqqMDZnvAetc",
    "last_activity": "1978-09-06T08:00:45.094Z",
    "created_on": "1979-05-15T23:42:41.917Z",
    "last_updated_on": "2020-11-26T07:32:01.778Z"
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

**Example GET request path:**<br>`/notifications/2013149238`

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
  "financial_institution_id": 2061727893,
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
  "html_template": "FinMEjuIdYOplkHBLbfVeBUyeYPiau",
  "text_template": "aLoBxfJ"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 2061727893 },
	{ "name", "Sample Notification" },
	{ "type", "email" },
	{ "event", "merchant_site_updates_all" },
	{ "html_template", "FinMEjuIdYOplkHBLbfVeBUyeYPiau" },
	{ "text_template", "aLoBxfJ" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 2061727893 )
	.add("name", "Sample Notification" )
	.add("type", "email" )
	.add("event", "merchant_site_updates_all" )
	.add("html_template", "FinMEjuIdYOplkHBLbfVeBUyeYPiau" )
	.add("text_template", "aLoBxfJ" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":2061727893,\"name\":\"Sample Notification\",\"type\":\"email\",\"event\":\"merchant_site_updates_all\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"FinMEjuIdYOplkHBLbfVeBUyeYPiau\",\"text_template\":\"aLoBxfJ\"}"
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
  "html_template": "HXniRRPXCfBhMJdxoOhAGsEMdcaKXaX",
  "text_template": "InNyFDLQKHYwDyunzzrGvQPVWRgSYV"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Sample Notification" },
	{ "type", "email" },
	{ "event", "merchant_site_updates_top" },
	{ "html_template", "HXniRRPXCfBhMJdxoOhAGsEMdcaKXaX" },
	{ "text_template", "InNyFDLQKHYwDyunzzrGvQPVWRgSYV" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Sample Notification" )
	.add("type", "email" )
	.add("event", "merchant_site_updates_top" )
	.add("html_template", "HXniRRPXCfBhMJdxoOhAGsEMdcaKXaX" )
	.add("text_template", "InNyFDLQKHYwDyunzzrGvQPVWRgSYV" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"Sample Notification\",\"type\":\"email\",\"event\":\"merchant_site_updates_top\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"HXniRRPXCfBhMJdxoOhAGsEMdcaKXaX\",\"text_template\":\"InNyFDLQKHYwDyunzzrGvQPVWRgSYV\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/2013149238
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
https://api.INSTANCE.cardsavr.io/notifications/2013149238
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
const notificationresults = await session.getNotificationResults(285064026,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["notification"])});
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
JsonArray response = (JsonArray)session.get(285064026, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 285064026,
  "last_attempt_date": "2013-05-19T16:36:38.953Z",
  "fi_lookup_key": "vEkrsuQyfhBxXEskGFQbHlxiTDESIRQfEyIhGkUKVwyuGsGhgDvPfrmbxpfazxX",
  "cuid": "flfOojTaVy",
  "status": "success",
  "attempts": 801426589,
  "notification_data": {
    "RMiDtNklaMYq": "AK)^6knq&/C%x&Tjq=wHXH8ZO4Lc].",
    "ZsSvLzzKYMqn": 9,
    "iYNtmlYHCCDn": true
  },
  "created_on": "2019-10-13T15:13:03.005Z",
  "last_updated_on": "1971-11-15T06:28:48.084Z",
  "notification": {
    "id": 1620334805,
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
    "html_template": "IXUcyjeWTndMBVqypXq",
    "text_template": "UpKYKQGPugOGjTLQZBEIeofRkjm",
    "created_on": "1987-09-04T04:32:53.529Z",
    "last_updated_on": "1977-07-21T03:57:12.442Z"
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

**Example GET request path:**<br>`/notification_results/285064026`

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
  "notification_id": 1898261452,
  "fi_lookup_key": "vEkrsuQyfhBxXEskGFQbHlxiTDESIRQfEyIhGkUKVwyuGsGhgDvPfrmbxpfazxX",
  "cuid": "flfOojTaVy",
  "status": "success",
  "attempts": 801426589,
  "notification_data": {
    "RMiDtNklaMYq": "AK)^6knq&/C%x&Tjq=wHXH8ZO4Lc].",
    "ZsSvLzzKYMqn": 9,
    "iYNtmlYHCCDn": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 1898261452 },
	{ "fi_lookup_key", "vEkrsuQyfhBxXEskGFQbHlxiTDESIRQfEyIhGkUKVwyuGsGhgDvPfrmbxpfazxX" },
	{ "cuid", "flfOojTaVy" },
	{ "status", "success" },
	{ "attempts", 801426589 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 1898261452 )
	.add("fi_lookup_key", "vEkrsuQyfhBxXEskGFQbHlxiTDESIRQfEyIhGkUKVwyuGsGhgDvPfrmbxpfazxX" )
	.add("cuid", "flfOojTaVy" )
	.add("status", "success" )
	.add("attempts", 801426589 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":1898261452,\"fi_lookup_key\":\"vEkrsuQyfhBxXEskGFQbHlxiTDESIRQfEyIhGkUKVwyuGsGhgDvPfrmbxpfazxX\",\"cuid\":\"flfOojTaVy\",\"status\":\"success\",\"attempts\":801426589,\"notification_data\":{\"RMiDtNklaMYq\":\"AK)^6knq&/C%x&Tjq=wHXH8ZO4Lc].\",\"ZsSvLzzKYMqn\":9,\"iYNtmlYHCCDn\":true}}"
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
const singlesitejobs = await session.getSingleSiteJobs(701772066,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_card","cardsavr_account","credential_requests"])});
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
JsonArray response = (JsonArray)session.get(701772066, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 701772066,
  "status": "VBS_ERROR",
  "status_message": "ZbCNOmoAqxBewzzkhxahtNHNdrXP",
  "termination_type": "USER_DATA_FAILURE",
  "custom_data": {
    "gibcxhFrejCy": "8oUVqxb^Od^WZZ.e[e9O-/",
    "sNftPAHEPAcf": 51,
    "iwVInbWzBjWz": true
  },
  "notification_sent": true,
  "time_elapsed": 1431530878,
  "started_on": "1997-03-04T16:07:39.080Z",
  "completed_on": "2005-07-30T06:09:21.613Z",
  "created_on": "1999-11-20T18:17:18.726Z",
  "last_updated_on": "2019-01-13T18:28:04.690Z",
  "cardholder": {
    "id": 1041435818,
    "type": "persistent_all",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "UABNNMXN",
    "webhook_url": "QElWVAYALPVDmOF",
    "custom_data": {
      "pirpMVewqZYJ": "Oe#a9].(*9o~Ok}h#%Y7c~4todtiT0",
      "qNSPuyyFMfTo": 57,
      "WfnYQBGxNhOc": false
    },
    "created_on": "1975-05-13T13:09:42.467Z",
    "last_updated_on": "1984-08-26T00:35:56.294Z",
    "cuid": "cxeSKfcdtBJTapJr"
  },
  "cardsavr_card": {
    "id": 769964032,
    "type": "Mastercard",
    "expiration_month": 12,
    "expiration_year": 24,
    "name_on_card": "Jane Smith",
    "nickname": "Jane's VISA",
    "custom_data": {
      "yrxuyaCaTTKu": "S+aWLCvMMA.*",
      "brfzvxjQCLkJ": 48,
      "juzgxUEtVuLx": false
    },
    "created_on": "2019-07-30T09:52:34.441Z",
    "last_updated_on": "2004-01-07T16:26:03.631Z",
    "par": "RiTsybBMFwajzJgNlWFSJpBipUXYY",
    "customer_key": "qcycFXvTnMurrWNedZCXfdHpiyohU"
  },
  "cardsavr_account": {
    "id": 1850887615,
    "last_password_update": "2016-11-02T10:55:16.236Z",
    "last_saved_card": "1971-12-09T12:33:21.050Z",
    "created_on": "1998-09-20T21:47:43.649Z",
    "last_updated_on": "2010-05-10T20:24:17.882Z",
    "customer_key": "dz"
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/701772066`

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
  "cardholder_id": 734792374,
  "card_id": 1268945868,
  "account_id": 445255421,
  "status": "VBS_ERROR",
  "custom_data": {
    "gibcxhFrejCy": "8oUVqxb^Od^WZZ.e[e9O-/",
    "sNftPAHEPAcf": 51,
    "iwVInbWzBjWz": true
  },
  "notification_sent": true,
  "time_elapsed": 1431530878,
  "started_on": "1997-03-04T16:07:39.080Z",
  "completed_on": "2005-07-30T06:09:21.613Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 734792374 },
	{ "card_id", 1268945868 },
	{ "account_id", 445255421 },
	{ "status", "VBS_ERROR" },
	{ "notification_sent", true },
	{ "time_elapsed", 1431530878 },
	{ "started_on", "1997-03-04T16:07:39.080Z" },
	{ "completed_on", "2005-07-30T06:09:21.613Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 734792374 )
	.add("card_id", 1268945868 )
	.add("account_id", 445255421 )
	.add("status", "VBS_ERROR" )
	.add("notification_sent", true )
	.add("time_elapsed", 1431530878 )
	.add("started_on", "1997-03-04T16:07:39.080Z" )
	.add("completed_on", "2005-07-30T06:09:21.613Z" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":734792374,\"card_id\":1268945868,\"account_id\":445255421,\"status\":\"VBS_ERROR\",\"custom_data\":{\"gibcxhFrejCy\":\"8oUVqxb^Od^WZZ.e[e9O-/\",\"sNftPAHEPAcf\":51,\"iwVInbWzBjWz\":true},\"notification_sent\":true,\"time_elapsed\":1431530878,\"started_on\":\"1997-03-04T16:07:39.080Z\",\"completed_on\":\"2005-07-30T06:09:21.613Z\"}"
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
  "card_id": 2013353588,
  "status": "SUCCESSFUL",
  "custom_data": {
    "MDkOMxvLUmsP": "5",
    "EbFwYjROztXS": 95,
    "rmstawwVjfNT": false
  },
  "notification_sent": false,
  "time_elapsed": 623495881,
  "started_on": "2009-10-18T02:46:48.083Z",
  "completed_on": "1993-08-19T05:13:39.452Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 2013353588 },
	{ "status", "SUCCESSFUL" },
	{ "notification_sent", false },
	{ "time_elapsed", 623495881 },
	{ "started_on", "2009-10-18T02:46:48.083Z" },
	{ "completed_on", "1993-08-19T05:13:39.452Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 2013353588 )
	.add("status", "SUCCESSFUL" )
	.add("notification_sent", false )
	.add("time_elapsed", 623495881 )
	.add("started_on", "2009-10-18T02:46:48.083Z" )
	.add("completed_on", "1993-08-19T05:13:39.452Z" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":2013353588,\"status\":\"SUCCESSFUL\",\"custom_data\":{\"MDkOMxvLUmsP\":\"5\",\"EbFwYjROztXS\":95,\"rmstawwVjfNT\":false},\"notification_sent\":false,\"time_elapsed\":623495881,\"started_on\":\"2009-10-18T02:46:48.083Z\",\"completed_on\":\"1993-08-19T05:13:39.452Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/701772066
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/701772066
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

