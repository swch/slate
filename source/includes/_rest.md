
# Accounts
Account objects contain the account information, such as username and password, for a particular cardhoder. They are used to log in to a cardholder's account for placing a payment card.
## Get account

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1438783798
```

```javascript
const accounts = await session.getAccounts(1438783798);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(undefined);
```

```java
JsonValue accounts = session.get("/cardsavr_accounts", 1438783798, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1438783798,
  "last_password_update": "1992-11-02T03:10:35.572Z",
  "last_saved_card": "2018-02-07T12:13:13.541Z",
  "created_on": "2015-10-17T14:35:25.430Z",
  "last_updated_on": "2013-10-22T01:25:22.538Z",
  "cardholder": {
    "id": 883143441,
    "financial_institution_id": 234104313,
    "agent_session_id": "MKECQixiUiCmokSVDdArgoeitZhbcL",
    "type": "persistent",
    "first_name": "ry",
    "last_name": "PRXExEQQzz",
    "email": "WAIoMmQxbgKX@nQxJwG.mNj",
    "meta_key": "atWZmTOQxPiQwV",
    "cardholder_safe_key": "uq03L3ZySwNNlvzvuFHr4hmISDytcLpyrydHsDSroxo=",
    "custom_data": {
      "guYckdFBkQdZ": "Oso(D*4##)9o^=y3[AK=<+meIsU)Q_Vs",
      "sSfKqHUBGBfb": 74,
      "nYISXggDYCHr": false
    },
    "created_on": "2021-04-30T19:14:07.341Z",
    "last_updated_on": "1992-05-02T20:41:31.718Z"
  },
  "merchant_site": {
    "id": 306626240,
    "name": "yBnxpaOCDEGQWOFLIhBeKimwI",
    "host": "UlnSGWZyWuCQsaCXJweyD",
    "tags": [
      "Fs*@PlD",
      43,
      "m<MO$5U>swhV79!VF!XDZ9*PJ"
    ],
    "required_form_fields": [
      "3t{K=@kX8f965i&@Lit-$$>+^dRs^d",
      48,
      "ieqtfb"
    ],
    "images": [
      {
        "AOSdSlaINAac": "ga_RIw#79z2v3xG",
        "iqEKSCUKNNYZ": 64,
        "WPBskpnGHWAe": true
      },
      {
        "FdlZgtEPdbFe": "O]k^YDbpSxdQ-eo)^t",
        "wIarYsVOEcWZ": 89,
        "iBmgZhtHMGDA": false
      },
      {
        "IzLsEGJvXrXS": "YH]Ay)]R",
        "nUgGvoFZGBKo": 10,
        "kUjTfPMCJYcd": false
      }
    ],
    "account_identification": {
      "tJtWvkffyYAu": "*Ef3sAL-z0(E3z",
      "AoPuXXpEzRJv": 6,
      "DiWwnfJwMvIJ": false
    },
    "messages": {
      "qkjWzKBVMvOo": "JE",
      "cUlwqJTfRiAt": 94,
      "KVvxuRtrbXKY": false
    },
    "mfa": false,
    "move_mouse_to_element": true,
    "proxy_order": [
      "gimb%rOv-h9+@rRI1G7Puns",
      32,
      "U}/lL8$f"
    ],
    "credit_card_page": "XGtMkqgSREHaszrxFQIeMFkOccM",
    "forgot_password_page": "EphltFyMcTNobidokMTMo",
    "quick_start": false,
    "login_page": "MmYTKF",
    "login": {
      "RcIFNvmxLMgv": "^N3BNNQ)hO/8>PEQP",
      "hhmyokPtlFKv": 6,
      "LZIQVQUoWrkW": false
    }
  },
  "cardsavr_card": {
    "id": 2007943879,
    "bin_id": 1338511416,
    "cvv": "gaz",
    "expiration_month": "g",
    "expiration_year": "T",
    "name_on_card": "fxOdPjnMSaNZDMscgukZmFEAwGpGavPlWHrJKRoTjouNUjNxLwMlrQPStSKacTbOpuXjXgBcBNSbtAkJOTBYoSGIBpSpNitsZKfpEAdOYhiOiXbqPkZlMspdWwrAlaBnRZkXkgouYZwCayPisqckBBFuDSJwCAaweXVhYpPGqpewbAGJQLWaeQFSlHincjOjvdRZbiyvRbLdTMbHgQmaPUgANYCuLizyESLfoVmwiqOAvgrbjAEhZZhtyaObnm",
    "first_6": "ahXySZnZfFJMghqsNDaRXZdwNrCnlYQz",
    "first_7": "xvZYvIpuwIUHImdZGNSaGreHoZAjsTdn",
    "first_8": "oapaasZLcvFZxaKgzFOvCNAgRJyRgXLr",
    "created_on": "1994-10-25T07:36:19.587Z",
    "last_updated_on": "2015-12-12T15:12:45.089Z"
  },
  "customer_key": "ImTCDzplwTVfnlqqOhxHfFppcd"
}
```

### Path

GET /cardsavr_accounts **(batch)** or GET /cardsavr_accounts/:id **(singular)**

### Description

Returns the account specified by the provided ID

#### Batch GET requests

**Batch requests** return the first page of all viewable accounts, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/cardsavr_accounts?ids=1,2`

#### Singular GET requests

**Singular requests** only return the account matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_accounts/1438783798`

### <a name="response-cardsavr_account"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
last_card_placed_id | number (fk) | ID of the last card placed on this account by the Virtual Browser System (VBS).
last_password_update | date | 
last_saved_card | date | Date of last card saved on this account.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) | ID of the cardholder associated with this account.
merchant_site_id | number (fk) | ID of the merchant site associated with this account.
customer_key | string | A key of merchant host and cuid. This can potentially violate a constraint with two accounts of the same merchant site.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

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

## Create account

```javascript
const account = await session.createAccount({
  "cardholder_id": 1239167830,
  "merchant_site_id": 216990195,
  "customer_key": "ImTCDzplwTVfnlqqOhxHfFppcd",
  "last_card_placed_id": 604007255,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1239167830 },
	{ "merchant_site_id", 216990195 },
	{ "customer_key", "ImTCDzplwTVfnlqqOhxHfFppcd" },
	{ "last_card_placed_id", 604007255 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1239167830 )
	.add("merchant_site_id", 216990195 )
	.add("customer_key", "ImTCDzplwTVfnlqqOhxHfFppcd" )
	.add("last_card_placed_id", 604007255 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1239167830,\"merchant_site_id\":216990195,\"customer_key\":\"ImTCDzplwTVfnlqqOhxHfFppcd\",\"last_card_placed_id\":604007255,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/
```

### Path

POST /cardsavr_accounts

### Description

Create a account and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cardholder_id | number | yes
merchant_site_id | number | yes
customer_key | string | no
last_card_placed_id | number | no
username | string | no
password | string | no

See [account response attributes](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username and password when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Upsert account

```javascript
const account = await session.updateAccount(1,{
  "last_card_placed_id": 1091864865,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 1091864865 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 1091864865 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":1091864865,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1438783798
```

### Path

PUT /cardsavr_accounts OR /cardsavr_accounts/{id}

### Description

Upsert can be used to either update a account, create a new account, or return an existing account.  Either an id or customer_key is required for upsert. The id (in path or body), along with an updated body, can be used to update an existing account; the customer_key (in body) can likewise be used to update a account, and can also be used to create a new account, if the customer_key does not match any existing accounts. If the id or customer_key provided corresponds to a pre-existing account and no updated information has been included in the body, the existing account will be returned.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
last_card_placed_id | number |
username | string |
password | string |

See [account response parameters](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username and password when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete account

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1438783798
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

See [account response parameters](#response-cardsavr_account).


# Addresses
Address objects contain the billing address for a specific cardholder, and are used to populate billing address information on merchant sites. They are linked to cards and cardholders.
## Get address

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1977833182
```

```javascript
const addresses = await session.getAddresses(1977833182);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(undefined);
```

```java
JsonValue addresses = session.get("/cardsavr_addresses", 1977833182, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1977833182,
  "address1": "123 Main St.",
  "address2": "Unit A",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "2065555555",
  "created_on": "1977-05-13T14:11:05.554Z",
  "last_updated_on": "1973-02-07T14:03:25.043Z",
  "cardholder": {
    "id": 1688318784,
    "financial_institution_id": 385230318,
    "agent_session_id": "nxKBbCg",
    "type": "persistent",
    "first_name": "zNS",
    "last_name": "jHhqRjxtsSTucAGjakccENVckQBqWl",
    "email": "RptcbxDPyMxv@OYBuWo.sPL",
    "meta_key": "DGQDepFHwqyNwbqSeUDcgOIC",
    "cardholder_safe_key": "wfnHOaiXDILH7zks2ZwV7BL4n+HuunpNbqvXg8gzR8w=",
    "custom_data": {
      "PWNQIpKgrbCr": "Ej0rjI+{,)l*Aq^y]s~BTs@+)tD}mog",
      "EFoLCNLJYcsm": 61,
      "eyycJfWiejBh": true
    },
    "created_on": "1972-06-07T03:45:04.322Z",
    "last_updated_on": "1982-06-22T02:19:57.822Z"
  }
}
```

### Path

GET /cardsavr_addresses **(batch)** or GET /cardsavr_addresses/:id **(singular)**

### Description

Returns the address specified by the provided ID

#### Batch GET requests

**Batch requests** return the first page of all viewable addresses, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/cardsavr_addresses?ids=1,2`

#### Singular GET requests

**Singular requests** only return the address matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_addresses/1977833182`

### <a name="response-cardsavr_address"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
address1 | string | 
address2 | string | 
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
cardholder_id | number (fk) | ID of the cardholder associated with this address.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- cardholder_ids
- is_primary
- first_name
- last_name
- email
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create address

```javascript
const address = await session.createAddress({
  "cardholder_id": 606094200,
  "address1": "123 Main St.",
  "address2": "Unit A",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 606094200 },
	{ "address1", "123 Main St." },
	{ "address2", "Unit A" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 606094200 )
	.add("address1", "123 Main St." )
	.add("address2", "Unit A" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":606094200,\"address1\":\"123 Main St.\",\"address2\":\"Unit A\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"phone_number\":\"2065555555\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/
```

### Path

POST /cardsavr_addresses

### Description

Create a address and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cardholder_id | number | yes
address1 | string | yes
address2 | string | no
city | string | yes
subnational | string | yes
postal_code | string | yes
postal_other | string | no
country | string | no
is_primary | boolean | yes
first_name | string | no
last_name | string | no
email | string | no
phone_number | string | no

See [address response attributes](#response-cardsavr_address).


## Update address

```javascript
const address = await session.updateAddress(1,{
  "address1": "123 Main St.",
  "address2": "Unit A",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "123 Main St." },
	{ "address2", "Unit A" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "123 Main St." )
	.add("address2", "Unit A" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", false )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"123 Main St.\",\"address2\":\"Unit A\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"phone_number\":\"2065555555\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1977833182
```

### Path

PUT /cardsavr_addresses OR /cardsavr_addresses/{id}

### Description

Update a address and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
address1 | string |
address2 | string |
city | string |
subnational | string |
postal_code | string |
postal_other | string |
country | string |
is_primary | boolean |
first_name | string |
last_name | string |
email | string |
phone_number | string |

See [address response parameters](#response-cardsavr_address).


## Delete address

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1977833182
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

See [address response parameters](#response-cardsavr_address).


# Bins
A Bank Identification Number (BIN) object represents a BIN used by a financial institution in the CardSavr API. They are linked to cards and FIs and used for reporting purposes.
## Get bin

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1979097240
```

```javascript
const bins = await session.getBins(1979097240);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(undefined);
```

```java
JsonValue bins = session.get("/cardsavr_bins", 1979097240, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1979097240,
  "custom_data": {
    "ZHBswYpdGugE": "N)Xfww-{U",
    "PSaRQAeXwKnl": 1,
    "lvoMPJZYQLtN": true
  },
  "created_on": "1983-09-20T07:08:48.712Z",
  "last_updated_on": "1985-11-16T03:46:38.068Z",
  "financial_institution": {
    "id": 1642590424,
    "name": "IesRNZfAFkJjjyYgUpDQCswGWKNgcgxybWguEElFZlfyQMbBMVeVZVpqfadfmkh",
    "description": "FhpgXFAYBdOIJZbTtquniKLQ",
    "lookup_key": "SDwtwfrlMAhusDiTCuxcdJjsVCgKwDJbWNLRHhjBRVViFczPCiKohyXFNDHgvyS",
    "alternate_lookup_key": "hGtwEBiBiLHdRHsmerBIKYAMPqLmyBBOlegeepjentcJpqWggRoZsxSZPWlWqey",
    "config": {
      "KnqoDKmRpcVp": "9S.Yt",
      "fSxxfLZPJcsU": 38,
      "ffugGOSVxPwx": false
    },
    "created_on": "1992-07-05T19:23:55.941Z",
    "last_updated_on": "1973-12-18T13:41:03.115Z"
  },
  "bank_identification_number": "45087778"
}
```

### Path

GET /cardsavr_bins **(batch)** or GET /cardsavr_bins/:id **(singular)**

### Description

Returns the bin specified by the provided ID

#### Batch GET requests

**Batch requests** return the first page of all viewable bins, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/cardsavr_bins?ids=1,2`

#### Singular GET requests

**Singular requests** only return the bin matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_bins/1979097240`

### <a name="response-cardsavr_bin"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
financial_institution_id | number (fk) | ID of financial institution that this Bank Identification Number belongs to.
custom_data | object | Custom data (e.g. brand, type) that can be added according to FI need.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
bank_identification_number | string | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- financial_institution_ids
- bank_identification_numbers
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create bin

```javascript
const bin = await session.createBin({
  "financial_institution_id": 1191397545,
  "bank_identification_number": "45087778",
  "custom_data": {
    "ZHBswYpdGugE": "N)Xfww-{U",
    "PSaRQAeXwKnl": 1,
    "lvoMPJZYQLtN": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1191397545 },
	{ "bank_identification_number", "45087778" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1191397545 )
	.add("bank_identification_number", "45087778" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1191397545,\"bank_identification_number\":\"45087778\",\"custom_data\":{\"ZHBswYpdGugE\":\"N)Xfww-{U\",\"PSaRQAeXwKnl\":1,\"lvoMPJZYQLtN\":true}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/
```

### Path

POST /cardsavr_bins

### Description

Create a bin and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
financial_institution_id | number | yes
bank_identification_number | string | yes
custom_data | object | no

See [bin response attributes](#response-cardsavr_bin).


## Update bin

```javascript
const bin = await session.updateBin(1,{
  "financial_institution_id": 1693667079,
  "custom_data": {
    "WsOAGDWJGppT": "ZJU-Fh2&OIlI/[amw",
    "yjxrlqBVlVKz": 27,
    "xhsNCPcCLoWA": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1693667079 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1693667079 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1693667079,\"custom_data\":{\"WsOAGDWJGppT\":\"ZJU-Fh2&OIlI/[amw\",\"yjxrlqBVlVKz\":27,\"xhsNCPcCLoWA\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1979097240
```

### Path

PUT /cardsavr_bins OR /cardsavr_bins/{id}

### Description

Update a bin and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
financial_institution_id | number |
custom_data | object |

See [bin response parameters](#response-cardsavr_bin).


## Delete bin

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1979097240
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

See [bin response parameters](#response-cardsavr_bin).


# Cards
A card object contains information about a payment card for a specific cardholder. Card objects are used to populate payment information on merchant sites.
## Get card

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/cardsavr_cards/188766777
```

```javascript
const cards = await session.getCards(188766777);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(undefined);
```

```java
JsonValue cards = session.get("/cardsavr_cards", 188766777, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 188766777,
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Joe C Smith",
  "created_on": "2021-02-18T01:00:32.572Z",
  "last_updated_on": "1981-09-12T08:13:15.943Z",
  "cardholder": {
    "id": 739060063,
    "financial_institution_id": 455554640,
    "agent_session_id": "gCKymBqCfalA",
    "type": "persistent",
    "first_name": "SkugaoRvlVOocPzsdy",
    "last_name": "rVeGfxJYUOXNKCWdzFHpvodGVivl",
    "email": "DsbeeMkHdXgp@IeTWYm.xeJ",
    "meta_key": "OBqjpRErIDzebeeI",
    "cardholder_safe_key": "eQieBslO2o5Cd262soalqxr76GqhYJXfnnSodyQnAA0=",
    "custom_data": {
      "ugqdgqgEqahe": "Vz.JwZBbB=Tv",
      "mzTZbXmGmXMy": 46,
      "mLKTahGPfroi": true
    },
    "created_on": "1991-02-05T02:33:08.313Z",
    "last_updated_on": "2011-07-11T02:28:29.508Z"
  },
  "cardsavr_bin": {
    "id": 833801421,
    "financial_institution_id": 1887267408,
    "custom_data": {
      "pPAerhOIwLCl": "J}d{Zv+5N2U4Ztme}",
      "kemXqhxatJSq": 13,
      "JoBVlYQUGYrq": true
    },
    "created_on": "2013-09-29T00:49:12.955Z",
    "last_updated_on": "2018-11-29T11:16:23.544Z"
  },
  "address_id": 1242933982,
  "par": "JcYAFxiETDHsStpfYRCiAcnnmgFvn"
}
```

### Path

GET /cardsavr_cards **(batch)** or GET /cardsavr_cards/:id **(singular)**

### Description

Returns the card specified by the provided ID

#### Batch GET requests

**Batch requests** return the first page of all viewable cards, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/cardsavr_cards?ids=1,2`

#### Singular GET requests

**Singular requests** only return the card matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_cards/188766777`

### <a name="response-cardsavr_card"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
bin_id | number (fk) | ID of BIN associated with this card.
expiration_month | string | 
expiration_year | string | 
name_on_card | string | 
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) | ID of cardholder associated with this card.
address_id | number | ID of address associated with this card.
par | string | Unique Personal Account Reference number for this card, to be used for card lookup. Generated automatically from PAN, expiration date, and username if using the SDK.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- cardholder_ids
- address_ids
- bin_ids
- pars
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create card

```javascript
const card = await session.createCard({
  "cardholder_id": 3102743,
  "address_id": 1242933982,
  "bin_id": 942236393,
  "par": "JcYAFxiETDHsStpfYRCiAcnnmgFvn",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Joe C Smith"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 3102743 },
	{ "address_id", 1242933982 },
	{ "bin_id", 942236393 },
	{ "par", "JcYAFxiETDHsStpfYRCiAcnnmgFvn" },
	{ "pan", "4111111111111111" },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Joe C Smith" }
};

CardSavrResponse<Card> card = await http.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 3102743 )
	.add("address_id", 1242933982 )
	.add("bin_id", 942236393 )
	.add("par", "JcYAFxiETDHsStpfYRCiAcnnmgFvn" )
	.add("pan", "4111111111111111" )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Joe C Smith" )
	.build();
JsonValue card = session.post("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":3102743,\"address_id\":1242933982,\"bin_id\":942236393,\"par\":\"JcYAFxiETDHsStpfYRCiAcnnmgFvn\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/
```

### Path

POST /cardsavr_cards

### Description

Create a card and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cardholder_id | number | yes
address_id | number | no
bin_id | number | no
par | string | yes
pan | string | yes
cvv | string | yes
expiration_month | string | yes
expiration_year | string | yes
name_on_card | string | yes

See [card response attributes](#response-cardsavr_card).

<aside class="notice">Update calls to /cardsavr_cards require the cardholder's personal cardholder_safe_key header to encrypt and save the pan and cvv when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Upsert card

```javascript
const card = await session.updateCard(1,{
  "bin_id": 495265911,
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Joe C Smith",
  "pan": "4111111111111111"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "bin_id", 495265911 },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Joe C Smith" },
	{ "pan", "4111111111111111" }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("bin_id", 495265911 )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Joe C Smith" )
	.add("pan", "4111111111111111" )
	.build();
JsonValue card = session.put("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"bin_id\":495265911,\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\",\"pan\":\"4111111111111111\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/188766777
```

### Path

PUT /cardsavr_cards OR /cardsavr_cards/{id}

### Description

Upsert can be used to either update a card, create a new card, or return an existing card.  Either an id or PAR is required for upsert. The id (in path or body), along with an updated body, can be used to update an existing card; the PAR (in body) can likewise be used to update a card, and can also be used to create a new card, if the PAR does not match any existing cards. If the id or PAR provided corresponds to a pre-existing card and no updated information has been included in the body, the existing card will be returned.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
bin_id | number |
cvv | string |
expiration_month | string |
expiration_year | string |
name_on_card | string |

See [card response parameters](#response-cardsavr_card).


## Delete card

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/188766777
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

See [card response parameters](#response-cardsavr_card).


# Cardholders
Cardholders are the end-users of the CardSavr API, who can have their their payment information updated on merchant site(s). Cardholders can be linked to cards, accounts, and addresses.
## Get cardholder

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/cardholders/1926948393
```

```javascript
const cardholders = await session.getCardholders(1926948393);
```

```csharp
CardSavrResponse<Cardholders> cardholders = await session.GetCardholdersAsync(undefined);
```

```java
JsonValue cardholders = session.get("/cardholders", 1926948393, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1926948393,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "MB9810411",
  "custom_data": {
    "xFoKKsKJLosp": "k+",
    "VDKrQSkuTemb": 91,
    "ctrdZgcOGHWt": false
  },
  "created_on": "1974-05-30T03:58:20.292Z",
  "last_updated_on": "2008-10-09T20:42:30.219Z",
  "cuid": "abcd1234",
  "financial_institution": {
    "id": 1965615681,
    "name": "AIViJvixOKSZQDjAJwmMDOwPEdruFsKnlezGOJmaMbetSvPzbLgpBZcesgyndZT",
    "description": "QqZSeDvpTaTmYLzD",
    "lookup_key": "gMlufFLgkdCGpUcgJSvRvvpSISWvCMsBnnDOlvQszmexmWhKQhihMdruDitXoLO",
    "alternate_lookup_key": "PaekwTuWuQsuEFazwoPKfnMJMcxzBvYWMmcFJCNQXbqLcTwiAVSGOdmDvhkxcQm",
    "config": {
      "vupKohWwufpo": "z^9OY",
      "OJJRAtAyYEpk": 31,
      "XVpDKHMaaGhE": true
    },
    "created_on": "1979-01-17T09:34:40.191Z",
    "last_updated_on": "2015-10-04T22:05:00.827Z"
  }
}
```

### Path

GET /cardholders **(batch)** or GET /cardholders/:id **(singular)**

### Description

Returns the cardholder specified by the provided ID

#### Batch GET requests

**Batch requests** return the first page of all viewable cardholders, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/cardholders?ids=1,2`

#### Singular GET requests

**Singular requests** only return the cardholder matching the id provided in the path.

**Example GET request path:**<br>`/cardholders/1926948393`

### <a name="response-cardholder"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
financial_institution_id | number (fk) | 
first_name | string | 
last_name | string | 
email | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
custom_data | object | Additional data that can be added to the cardholder if needed.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cuid | string | Unique ID for cardholder--can be email address, phone number, etc.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- financial_institution_ids
- cuid
- first_name
- last_name
- email
- meta_key
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create cardholder

```javascript
const cardholder = await session.createCardholder({
  "cuid": "abcd1234",
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "MB9810411",
  "custom_data": {
    "xFoKKsKJLosp": "k+",
    "VDKrQSkuTemb": 91,
    "ctrdZgcOGHWt": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cuid", "abcd1234" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "MB9810411" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cuid", "abcd1234" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "MB9810411" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"cuid\":\"abcd1234\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"MB9810411\",\"custom_data\":{\"xFoKKsKJLosp\":\"k+\",\"VDKrQSkuTemb\":91,\"ctrdZgcOGHWt\":false}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/
```

### Path

POST /cardholders

### Description

Create a cardholder and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cuid | string | yes
first_name | string | no
last_name | string | no
email | string | no
meta_key | string | no
custom_data | object | no

See [cardholder response attributes](#response-cardholder).


## Upsert cardholder

```javascript
const cardholder = await session.updateCardholder(1,{
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "MB9810411",
  "custom_data": {
    "TYfGheekkFmv": "TG-!@O7jjU12g/@WE1{}",
    "oYwTtTmoVWel": 88,
    "kvPEYxtfjpYA": true
  },
  "cuid": "abcd1234"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "MB9810411" },
	{ "cuid", "abcd1234" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "MB9810411" )
	.add("cuid", "abcd1234" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"MB9810411\",\"custom_data\":{\"TYfGheekkFmv\":\"TG-!@O7jjU12g/@WE1{}\",\"oYwTtTmoVWel\":88,\"kvPEYxtfjpYA\":true},\"cuid\":\"abcd1234\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/1926948393
```

### Path

PUT /cardholders OR /cardholders/{id}

### Description

Upsert can be used to either update a cardholder, create a new cardholder, or return an existing cardholder.  Either an id or cuid is required for upsert. The id (in path or body), along with an updated body, can be used to update an existing cardholder; the cuid (in body) can likewise be used to update a cardholder, and can also be used to create a new cardholder, if the cuid does not match any existing cardholders. If the id or cuid provided corresponds to a pre-existing cardholder and no updated information has been included in the body, the existing cardholder will be returned.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
first_name | string |
last_name | string |
email | string |
meta_key | string |
custom_data | object |

See [cardholder response parameters](#response-cardholder).


## Delete cardholder

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/1926948393
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

See [cardholder response parameters](#response-cardholder).


# Users
Users are internal entities, such as agents or admins, that can perform such functions as creating and deleting cardholders, fetching merchant sites, creating jobs, etc.
## Get user

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/cardsavr_users/850375884
```

```javascript
const users = await session.getUsers(850375884);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(undefined);
```

```java
JsonValue users = session.get("/cardsavr_users", 850375884, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 850375884,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1979-06-06T23:19:15.312Z",
  "is_locked": true,
  "password_lifetime": 338,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "cardholder_agent",
  "next_rotation_on": "1988-09-01T20:52:20.556Z",
  "created_on": "1994-11-12T21:27:22.972Z",
  "last_updated_on": "1971-07-02T03:55:26.218Z",
  "username": "jsmith123",
  "financial_institution": {
    "id": 96135351,
    "name": "OQzlrgwkEOcYHYNVNpXWOBNemTWPGcQDPWbgqsOhfTcMIUQHyqfyKQPZLvRHKjd",
    "description": "XbfdyJkoMEVBnQnmlGmvZAd",
    "lookup_key": "lCTUWMkfyudIuzLexjlaTOLlDpYjtRTVEwHDRQRHIucHBSFvskrGcDNgrjLIXUz",
    "alternate_lookup_key": "OhVxJTtDohUatYJvNSGmERuWfRiQAicoNVhbHGDtzMEGwJrBPTdgcgkHxXOCeyu",
    "config": {
      "JKBSFZfFMxHX": "G4FnPm7{b&>",
      "VRRkAXJMGXbJ": 58,
      "HMpDBKqkYOTc": true
    },
    "created_on": "2000-02-22T10:22:16.037Z",
    "last_updated_on": "1981-03-31T19:19:10.552Z"
  }
}
```

### Path

GET /cardsavr_users **(batch)** or GET /cardsavr_users/:id **(singular)**

### Description

Returns the user specified by the provided ID

#### Batch GET requests

**Batch requests** return the first page of all viewable users, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/cardsavr_users?ids=1,2`

#### Singular GET requests

**Singular requests** only return the user matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_users/850375884`

### <a name="response-cardsavr_user"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
financial_institution_id | number (fk) | 
first_name | string | 
last_name | string | 
last_login_time | date | 
is_locked | boolean | 
password_lifetime | number | Length of time that password will remain valid.
email | string | 
is_password_update_required | boolean | 
role | string | User role (cardholder_agent or customer_agent) determines the user's ability to access certain endpoints and perform certain operations within the CardSavr API. 
cardholder_agents can create cardholders, create cards addresses for those cardholders, create accounts for those cardholders, and post jobs for those cardholders.
customer_agents can peform all actions on cardholders/accounts/, but are limited to acting on cardholders/jobs/accounts/cards within their FI (unless they are assigned to the admin FI)
next_rotation_on | date | Date of next password rotation for this user.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
username | string | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

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

## Create user

```javascript
const user = await session.createUser({
  "financial_institution_id": 1266576960,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 338,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "cardholder_agent",
  "next_rotation_on": "1988-09-01T20:52:20.556Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1266576960 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 338 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "cardholder_agent" },
	{ "next_rotation_on", "1988-09-01T20:52:20.556Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1266576960 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 338 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "cardholder_agent" )
	.add("next_rotation_on", "1988-09-01T20:52:20.556Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1266576960,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":338,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"cardholder_agent\",\"next_rotation_on\":\"1988-09-01T20:52:20.556Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/
```

### Path

POST /cardsavr_users

### Description

Create a user and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
financial_institution_id | number | no
username | string | yes
password | string | yes
first_name | string | no
last_name | string | no
password_lifetime | number | no
email | string | no
is_password_update_required | boolean | no
role | [string enum](#post-cardsavr_user-1)* | yes
next_rotation_on | date | no

See [user response attributes](#response-cardsavr_user).

#### <a name="post-cardsavr_user-1"></a>string enum*
- admin
- cardholder_agent
- customer_agent
- swch_agent


## Update user

```javascript
const user = await session.updateUser(1,{
  "financial_institution_id": 1303570096,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 307,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "cardholder_agent",
  "next_rotation_on": "2002-09-23T22:11:55.463Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1303570096 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 307 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "cardholder_agent" },
	{ "next_rotation_on", "2002-09-23T22:11:55.463Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1303570096 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 307 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "cardholder_agent" )
	.add("next_rotation_on", "2002-09-23T22:11:55.463Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1303570096,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":307,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"cardholder_agent\",\"next_rotation_on\":\"2002-09-23T22:11:55.463Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/850375884
```

### Path

PUT /cardsavr_users OR /cardsavr_users/{id}

### Description

Update a user and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
financial_institution_id | number |
first_name | string |
last_name | string |
password_lifetime | number |
email | string |
is_password_update_required | boolean |
role | [string enum](#post-cardsavr_user-1)* |
next_rotation_on | date |

See [user response parameters](#response-cardsavr_user).


## Delete user

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/850375884
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

See [user response parameters](#response-cardsavr_user).


# Financial Institutions
Financial Institution (FI) objects represent individual FIs and can be linked to users and cardholders. They also contain the configuration information that can be used to customize an FI's CardUpdatr instance, if one exists.
## Get financial institution

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/financial_institutions/1800183836
```

```javascript
const financialinstitutions = await session.getFinancialInstitutions(1800183836);
```

```csharp
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(undefined);
```

```java
JsonValue financialinstitutions = session.get("/financial_institutions", 1800183836, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1800183836,
  "name": "cULmMswcOyNCaAbggfQsSbSOGAdXchZpLZhvgCZQPHBzJFZUEBYBbhkTiOzTUuL",
  "description": "XnVGcVdBe",
  "lookup_key": "NyUDDHHWeNjQuAnCuJEOUcucHImLOEnjhuCeWrhRBMmKVkrzcTsjpgVnMrjyzhM",
  "alternate_lookup_key": "YJLvCkDhhJXRHryFeBRxQyCkyDiRMhWlwwqPdUUsXWDzoGmrGHbEEqpAZfYqnuv",
  "created_on": "1992-04-09T04:12:40.614Z",
  "last_updated_on": "1991-04-11T21:58:31.255Z"
}
```

### Path

GET /financial_institutions **(batch)** or GET /financial_institutions/:id **(singular)**

### Description

Returns the financial institution specified by the provided ID

#### Batch GET requests

**Batch requests** return the first page of all viewable financial institutions, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/financial_institutions?ids=1,2`

#### Singular GET requests

**Singular requests** only return the financial institution matching the id provided in the path.

**Example GET request path:**<br>`/financial_institutions/1800183836`

### <a name="response-financial_institution"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
name | string | 
description | string | 
lookup_key | string | Unique key used to identify financial institution.
alternate_lookup_key | string | Alternate lookup key; can be used in case of FI name change that does not match original lookup_key, in order to maintain backwards compatibility.
created_on | date | Date this integrator was created on
last_updated_on | date | Date this integrator was last updated on

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- names
- lookup_key
- alternate_lookup_key
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create financial institution

```javascript
const financialinstitution = await session.createFinancialInstitution({
  "name": "cULmMswcOyNCaAbggfQsSbSOGAdXchZpLZhvgCZQPHBzJFZUEBYBbhkTiOzTUuL",
  "description": "XnVGcVdBe",
  "lookup_key": "NyUDDHHWeNjQuAnCuJEOUcucHImLOEnjhuCeWrhRBMmKVkrzcTsjpgVnMrjyzhM",
  "alternate_lookup_key": "YJLvCkDhhJXRHryFeBRxQyCkyDiRMhWlwwqPdUUsXWDzoGmrGHbEEqpAZfYqnuv"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "cULmMswcOyNCaAbggfQsSbSOGAdXchZpLZhvgCZQPHBzJFZUEBYBbhkTiOzTUuL" },
	{ "description", "XnVGcVdBe" },
	{ "lookup_key", "NyUDDHHWeNjQuAnCuJEOUcucHImLOEnjhuCeWrhRBMmKVkrzcTsjpgVnMrjyzhM" },
	{ "alternate_lookup_key", "YJLvCkDhhJXRHryFeBRxQyCkyDiRMhWlwwqPdUUsXWDzoGmrGHbEEqpAZfYqnuv" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "cULmMswcOyNCaAbggfQsSbSOGAdXchZpLZhvgCZQPHBzJFZUEBYBbhkTiOzTUuL" )
	.add("description", "XnVGcVdBe" )
	.add("lookup_key", "NyUDDHHWeNjQuAnCuJEOUcucHImLOEnjhuCeWrhRBMmKVkrzcTsjpgVnMrjyzhM" )
	.add("alternate_lookup_key", "YJLvCkDhhJXRHryFeBRxQyCkyDiRMhWlwwqPdUUsXWDzoGmrGHbEEqpAZfYqnuv" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"cULmMswcOyNCaAbggfQsSbSOGAdXchZpLZhvgCZQPHBzJFZUEBYBbhkTiOzTUuL\",\"description\":\"XnVGcVdBe\",\"lookup_key\":\"NyUDDHHWeNjQuAnCuJEOUcucHImLOEnjhuCeWrhRBMmKVkrzcTsjpgVnMrjyzhM\",\"alternate_lookup_key\":\"YJLvCkDhhJXRHryFeBRxQyCkyDiRMhWlwwqPdUUsXWDzoGmrGHbEEqpAZfYqnuv\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/
```

### Path

POST /financial_institutions

### Description

Create a financial institution and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
name | string | yes
description | string | no
lookup_key | string | yes
alternate_lookup_key | string | no

See [financial institution response attributes](#response-financial_institution).


## Update financial institution

```javascript
const financialinstitution = await session.updateFinancialInstitution(1,{
  "name": "IysqhGGhzSbZpdWXjWYJLpFfHWLypeqHhfLRgAiuvrKpfVoTBWzYZSvEivZvWhe",
  "description": "rdxgrpSpXMiAqVUhJ",
  "lookup_key": "hqboyZshtltaKCsVwtuMSTygpezEcCeLsnOPLFzMmrUBWDmnbSZcSYZTmGEpxFp",
  "alternate_lookup_key": "MWfBgZQCTXTJuGGhIONLAWSowYreuImurCSyxcAFDKjcHzmadTVLUPdxZwvwkBC"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "IysqhGGhzSbZpdWXjWYJLpFfHWLypeqHhfLRgAiuvrKpfVoTBWzYZSvEivZvWhe" },
	{ "description", "rdxgrpSpXMiAqVUhJ" },
	{ "lookup_key", "hqboyZshtltaKCsVwtuMSTygpezEcCeLsnOPLFzMmrUBWDmnbSZcSYZTmGEpxFp" },
	{ "alternate_lookup_key", "MWfBgZQCTXTJuGGhIONLAWSowYreuImurCSyxcAFDKjcHzmadTVLUPdxZwvwkBC" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "IysqhGGhzSbZpdWXjWYJLpFfHWLypeqHhfLRgAiuvrKpfVoTBWzYZSvEivZvWhe" )
	.add("description", "rdxgrpSpXMiAqVUhJ" )
	.add("lookup_key", "hqboyZshtltaKCsVwtuMSTygpezEcCeLsnOPLFzMmrUBWDmnbSZcSYZTmGEpxFp" )
	.add("alternate_lookup_key", "MWfBgZQCTXTJuGGhIONLAWSowYreuImurCSyxcAFDKjcHzmadTVLUPdxZwvwkBC" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"IysqhGGhzSbZpdWXjWYJLpFfHWLypeqHhfLRgAiuvrKpfVoTBWzYZSvEivZvWhe\",\"description\":\"rdxgrpSpXMiAqVUhJ\",\"lookup_key\":\"hqboyZshtltaKCsVwtuMSTygpezEcCeLsnOPLFzMmrUBWDmnbSZcSYZTmGEpxFp\",\"alternate_lookup_key\":\"MWfBgZQCTXTJuGGhIONLAWSowYreuImurCSyxcAFDKjcHzmadTVLUPdxZwvwkBC\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/1800183836
```

### Path

PUT /financial_institutions OR /financial_institutions/{id}

### Description

Update a financial institution and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
name | string |
description | string |
lookup_key | string |
alternate_lookup_key | string |

See [financial institution response parameters](#response-financial_institution).


## Delete financial institution

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/1800183836
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

See [financial institution response parameters](#response-financial_institution).


# Integrators
Integrators are applications that integrate the CardSavr API, using their own unique integrator key. An integrator name and key are required for all calls to the CardSavr API. An integrator can be associated with multiple users.
## Get integrator

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/integrators/982006164
```

```javascript
const integrators = await session.getIntegrators(982006164);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(undefined);
```

```java
JsonValue integrators = session.get("/integrators", 982006164, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 982006164,
  "name": "lVfVcLXtzYToatgMaixzAFUiHpJqGzCmszvwjlynGoItyJDpR",
  "description": "BGlYxvU",
  "current_key": "888BoG4CwJ8udXEd8bo9H95Tq+qiM6Y8nsDkiU88uDc=",
  "key_lifetime": 17,
  "next_rotation_on": "2006-06-24T10:37:09.357Z",
  "created_on": "1989-04-23T10:44:16.432Z",
  "last_updated_on": "2016-04-25T15:49:18.311Z"
}
```

### Path

GET /integrators **(batch)** or GET /integrators/:id **(singular)**

### Description

Returns the integrator specified by the provided ID

#### Batch GET requests

**Batch requests** return the first page of all viewable integrators, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/integrators?ids=1,2`

#### Singular GET requests

**Singular requests** only return the integrator matching the id provided in the path.

**Example GET request path:**<br>`/integrators/982006164`

### <a name="response-integrator"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | An integrator's unique identifier
name | string | Name of integrator.
description | string | 
current_key | string | Current key for this integrator.
key_lifetime | number | Sets the duration of validity for integrator key.
next_rotation_on | date | Date of next key rotation for this integrator.
created_on | date | Date this integrator was created on
last_updated_on | date | Date this integrator was last updated on

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- names
- name
- next_rotation_on_min / next_rotation_on_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create integrator

```javascript
const integrator = await session.createIntegrator({
  "name": "lVfVcLXtzYToatgMaixzAFUiHpJqGzCmszvwjlynGoItyJDpR",
  "description": "BGlYxvU",
  "current_key": "888BoG4CwJ8udXEd8bo9H95Tq+qiM6Y8nsDkiU88uDc=",
  "key_lifetime": 17,
  "next_rotation_on": "2006-06-24T10:37:09.357Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "lVfVcLXtzYToatgMaixzAFUiHpJqGzCmszvwjlynGoItyJDpR" },
	{ "description", "BGlYxvU" },
	{ "current_key", "888BoG4CwJ8udXEd8bo9H95Tq+qiM6Y8nsDkiU88uDc=" },
	{ "key_lifetime", 17 },
	{ "next_rotation_on", "2006-06-24T10:37:09.357Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "lVfVcLXtzYToatgMaixzAFUiHpJqGzCmszvwjlynGoItyJDpR" )
	.add("description", "BGlYxvU" )
	.add("current_key", "888BoG4CwJ8udXEd8bo9H95Tq+qiM6Y8nsDkiU88uDc=" )
	.add("key_lifetime", 17 )
	.add("next_rotation_on", "2006-06-24T10:37:09.357Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"lVfVcLXtzYToatgMaixzAFUiHpJqGzCmszvwjlynGoItyJDpR\",\"description\":\"BGlYxvU\",\"current_key\":\"888BoG4CwJ8udXEd8bo9H95Tq+qiM6Y8nsDkiU88uDc=\",\"key_lifetime\":17,\"next_rotation_on\":\"2006-06-24T10:37:09.357Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/
```

### Path

POST /integrators

### Description

Create a integrator and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
name | string | yes
description | string | no
current_key | string | no
key_lifetime | number | no
next_rotation_on | date | no

See [integrator response attributes](#response-integrator).


## Update integrator

```javascript
const integrator = await session.updateIntegrator(1,{
  "name": "GxHozSuRGWYuNLVnBAlaCcenVQQlOMTUuetKJKltBRSSBlGGf",
  "description": "W",
  "current_key": "qI+mrV9F3YTDzxUMOi/uK2m6CECmT/qdA5w4rfPBUbw=",
  "key_lifetime": 0,
  "next_rotation_on": "2020-09-18T15:29:25.780Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "GxHozSuRGWYuNLVnBAlaCcenVQQlOMTUuetKJKltBRSSBlGGf" },
	{ "description", "W" },
	{ "current_key", "qI+mrV9F3YTDzxUMOi/uK2m6CECmT/qdA5w4rfPBUbw=" },
	{ "key_lifetime", 0 },
	{ "next_rotation_on", "2020-09-18T15:29:25.780Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "GxHozSuRGWYuNLVnBAlaCcenVQQlOMTUuetKJKltBRSSBlGGf" )
	.add("description", "W" )
	.add("current_key", "qI+mrV9F3YTDzxUMOi/uK2m6CECmT/qdA5w4rfPBUbw=" )
	.add("key_lifetime", 0 )
	.add("next_rotation_on", "2020-09-18T15:29:25.780Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"GxHozSuRGWYuNLVnBAlaCcenVQQlOMTUuetKJKltBRSSBlGGf\",\"description\":\"W\",\"current_key\":\"qI+mrV9F3YTDzxUMOi/uK2m6CECmT/qdA5w4rfPBUbw=\",\"key_lifetime\":0,\"next_rotation_on\":\"2020-09-18T15:29:25.780Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/982006164
```

### Path

PUT /integrators OR /integrators/{id}

### Description

Update a integrator and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
name | string |
description | string |
current_key | string |
key_lifetime | number |
next_rotation_on | date |

See [integrator response parameters](#response-integrator).


## Delete integrator

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/982006164
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

See [integrator response parameters](#response-integrator).


# Merchant sites
A merchant site object contains information, such as images URLs and hostname, for a CardSavr-supported merchant site.
## Get merchant site

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/merchant_sites/53257558
```

```javascript
const merchantsites = await session.getMerchantSites(53257558);
```

```csharp
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(undefined);
```

```java
JsonValue merchantsites = session.get("/merchant_sites", 53257558, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 53257558,
  "name": "zeKqfKLCBCmDHYPMqAYGoRuWl",
  "host": "XAzBJpor",
  "tags": [
    "9}*h#<6!<M(a1/0",
    73,
    "h5/2kV9"
  ],
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
  "account_identification": {
    "nCpxxPFpsRMD": "KN-zM&/Z1vlp~u%TfeL,mxD01%J.y",
    "NVqJryiZHDpP": 0,
    "hhEMLxyQLouQ": true
  },
  "mfa": false,
  "credit_card_page": "https://www.merchantsite.com/credit_card",
  "forgot_password_page": "https://www.merchantsite.com/forgot_password",
  "login_page": "https://www.merchantsite.com/login",
  "login": {
    "username_label": "Username/Email",
    "password_label": "Password",
    "mfa_label": "Additional information required, this code may be sent to your phone or email address.",
    "additional_info_message": "",
    "auth_message": "Linking account."
  }
}
```

### Path

GET /merchant_sites **(batch)** or GET /merchant_sites/:id **(singular)**

### Description

Returns the merchant site specified by the provided ID

#### Batch GET requests

**Batch requests** return the first page of all viewable merchant sites, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/merchant_sites?ids=1,2`

#### Singular GET requests

**Singular requests** only return the merchant site matching the id provided in the path.

**Example GET request path:**<br>`/merchant_sites/53257558`

### <a name="response-merchant_site"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
name | string | 
host | string | e.g. amazon.com
tags | array | Tags for use by front-end, such as development.
required_form_fields | array | Indicates the cardholder personal information fields that are required by this site.
images | array | URLs of the images for this merchant site.
account_identification | object | The identification credentials required to authenticate with merchant site (i.e. username/password or phone number/password)
mfa | boolean | Indicates if this site is MFA-enabled.
credit_card_page | string | Merchant's credit card entry page.
forgot_password_page | string | Merchant's forgotten password page.
login_page | string | URL of login page.
login | object | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- exclude_ids
- top_ids
- name_starts_with
- hosts
- host
- exclude_hosts
- top_hosts
- host_starts_with
- tags

# Notifications
Notification objects define a set of actions to be triggered by certain CardSavr events, such as session completion.
## Get notification

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/notifications/1831169050
```

```javascript
const notifications = await session.getNotifications(1831169050);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(undefined);
```

```java
JsonValue notifications = session.get("/notifications", 1831169050, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1831169050,
  "name": "xhPQwvWkIONDkEaNEyorLIWbuoFhLpaIvdcDocKXXkksDsdQgQtobQHGgFtZhQB",
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
  "html_template": "cDVfmNqZjaVgZUKuqZbRFOOCFOPkt",
  "text_template": "i",
  "created_on": "2013-04-30T20:22:24.003Z",
  "last_updated_on": "1975-06-10T00:42:57.807Z",
  "financial_institution": {
    "id": 1483258606,
    "name": "arGYGDnfXJHqzaORHdpjhAVVZEsCGCTNWpSuHptYFuPcJjQWZYSaFYtFBCeckiL",
    "description": "X",
    "lookup_key": "KJrfEIscUTcnEjmTtWMnSvucsVVfflmpHgiJhHgzbOvCNhYdQfmURAMYutYzwPq",
    "alternate_lookup_key": "xqgsOGTymfWGpTKEExoeoGkMNXdPJWMMZgANzOzDCJaYuSfRVBoCDKiGdUfBjDI",
    "config": {
      "CiwamSWNbdoC": "ihal.)BiO/JX/XB",
      "BazCBvNuZWPr": 30,
      "UwEsRKzWxfFf": true
    },
    "created_on": "2012-11-17T12:25:09.488Z",
    "last_updated_on": "1973-07-03T16:10:55.894Z"
  }
}
```

### Path

GET /notifications **(batch)** or GET /notifications/:id **(singular)**

### Description

Returns the notification specified by the provided ID

#### Batch GET requests

**Batch requests** return the first page of all viewable notifications, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/notifications?ids=1,2`

#### Singular GET requests

**Singular requests** only return the notification matching the id provided in the path.

**Example GET request path:**<br>`/notifications/1831169050`

### <a name="response-notification"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
name | string | Name of this notification.
type | string | Notification type (e.g. webhook or email).
event | string | Event that will triger the notification (e.g. session complete).
config | object | 
html_template | string | Overrides the default CardUpdatr html email template (for email notifications).
text_template | string | Overrides the default CardUpdatr text email template (for email notifications).
created_on | date | Date this notification was created on
last_updated_on | date | Date this notification was last updated on
financial_institution_id | number (fk) | ID of the financial institution associated with this notification.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- financial_institution_ids
- names
- type
- events
- event
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create notification

```javascript
const notification = await session.createNotification({
  "financial_institution_id": 1239694216,
  "name": "xhPQwvWkIONDkEaNEyorLIWbuoFhLpaIvdcDocKXXkksDsdQgQtobQHGgFtZhQB",
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
  "html_template": "cDVfmNqZjaVgZUKuqZbRFOOCFOPkt",
  "text_template": "i"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1239694216 },
	{ "name", "xhPQwvWkIONDkEaNEyorLIWbuoFhLpaIvdcDocKXXkksDsdQgQtobQHGgFtZhQB" },
	{ "type", "webhook" },
	{ "event", "merchant_site_updates_top" },
	{ "html_template", "cDVfmNqZjaVgZUKuqZbRFOOCFOPkt" },
	{ "text_template", "i" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1239694216 )
	.add("name", "xhPQwvWkIONDkEaNEyorLIWbuoFhLpaIvdcDocKXXkksDsdQgQtobQHGgFtZhQB" )
	.add("type", "webhook" )
	.add("event", "merchant_site_updates_top" )
	.add("html_template", "cDVfmNqZjaVgZUKuqZbRFOOCFOPkt" )
	.add("text_template", "i" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1239694216,\"name\":\"xhPQwvWkIONDkEaNEyorLIWbuoFhLpaIvdcDocKXXkksDsdQgQtobQHGgFtZhQB\",\"type\":\"webhook\",\"event\":\"merchant_site_updates_top\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"cDVfmNqZjaVgZUKuqZbRFOOCFOPkt\",\"text_template\":\"i\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/
```

### Path

POST /notifications

### Description

Create a notification and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
financial_institution_id | number | yes
name | string | yes
type | [string enum](#post-notification-1)* | yes
event | [string enum](#post-notification-2)** | yes
config | object | no
html_template | string | no
text_template | string | no

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
  "name": "BRjfZcIJHrtPtbRWcBOPyAUaIFrXdvFBUDyfFPSkZrDnRoAngAKyvUZcfjFupXG",
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
  "html_template": "iFpYqQLmf",
  "text_template": "hAoucEwQlu"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "BRjfZcIJHrtPtbRWcBOPyAUaIFrXdvFBUDyfFPSkZrDnRoAngAKyvUZcfjFupXG" },
	{ "type", "webhook" },
	{ "event", "webhook_error_summary" },
	{ "html_template", "iFpYqQLmf" },
	{ "text_template", "hAoucEwQlu" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "BRjfZcIJHrtPtbRWcBOPyAUaIFrXdvFBUDyfFPSkZrDnRoAngAKyvUZcfjFupXG" )
	.add("type", "webhook" )
	.add("event", "webhook_error_summary" )
	.add("html_template", "iFpYqQLmf" )
	.add("text_template", "hAoucEwQlu" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"BRjfZcIJHrtPtbRWcBOPyAUaIFrXdvFBUDyfFPSkZrDnRoAngAKyvUZcfjFupXG\",\"type\":\"webhook\",\"event\":\"webhook_error_summary\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"iFpYqQLmf\",\"text_template\":\"hAoucEwQlu\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/1831169050
```

### Path

PUT /notifications OR /notifications/{id}

### Description

Update a notification and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
name | string |
type | [string enum](#post-notification-1)* |
event | [string enum](#post-notification-2)** |
config | object |
html_template | string |
text_template | string |

See [notification response parameters](#response-notification).


## Delete notification

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/1831169050
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

See [notification response parameters](#response-notification).


# Notification results
Notification result objects are records of an attempt/attempts to send a notification, indicating success/failure and additional relevant information.
## Get notification result

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/notification_results/531981618
```

```javascript
const notificationresults = await session.getNotificationResults(531981618);
```

```csharp
CardSavrResponse<NotificationResults> notificationresults = await session.GetNotificationResultsAsync(undefined);
```

```java
JsonValue notificationresults = session.get("/notification_results", 531981618, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 531981618,
  "last_attempt_date": "1973-03-03T22:12:09.427Z",
  "fi_lookup_key": "kDMvuyDVMbxPeXMLvaKxTWCivtndcaDpfDuGSdPAWCzeytRhBAtcImfbUeykKmT",
  "cuid": "abcd1234",
  "status": "SUCCESSFUL",
  "attempts": 3,
  "notification_data": {
    "status_code": 200,
    "webhook_request": {
      "request_data": 123
    },
    "webhook_response": "OK"
  },
  "created_on": "1976-08-15T16:24:53.689Z",
  "last_updated_on": "2007-04-05T22:09:32.453Z",
  "notification": {
    "id": 1080316299,
    "name": "sPVzmiezbbWHBxtvFNYphSywmuBkGmygEAejFnyBPkViSapNdbiHuJmurTksEPD",
    "type": "webhook",
    "event": "merchant_site_updates_top",
    "config": {
      "kTFUqnxNjhTn": "w(&%*m",
      "YsXFQiAkcmxw": 16,
      "ZfmHoGKxRDhf": false
    },
    "html_template": "ZcQySpHCwIlitIuRQPSbiqV",
    "text_template": "eOUcgXzTzPEM",
    "created_on": "1980-07-09T07:10:49.503Z",
    "last_updated_on": "1977-10-01T12:28:17.289Z"
  }
}
```

### Path

GET /notification_results **(batch)** or GET /notification_results/:id **(singular)**

### Description

Returns the notification result specified by the provided ID

#### Batch GET requests

**Batch requests** return the first page of all viewable notification results, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/notification_results?ids=1,2`

#### Singular GET requests

**Singular requests** only return the notification result matching the id provided in the path.

**Example GET request path:**<br>`/notification_results/531981618`

### <a name="response-notification_result"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
last_attempt_date | date | Date of last attempt to post this notification.
fi_lookup_key | string | FI lookup key associated with the attempted notification.
cuid | string | Unique ID for cardholder--can be email address, phone number, etc.
status | string | Status of the notification attempt.
attempts | number | Number of attempts made to send or post notification.
notification_data | object | Data sent with the notification.
created_on | date | Date this notification result was created on
last_updated_on | date | Date this notification result was last updated on
notification_id | number (fk) | ID of the attempted notification.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

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

## Create notification result

```javascript
const notificationresult = await session.createNotificationResult({
  "notification_id": 1315847255,
  "fi_lookup_key": "kDMvuyDVMbxPeXMLvaKxTWCivtndcaDpfDuGSdPAWCzeytRhBAtcImfbUeykKmT",
  "cuid": "abcd1234",
  "status": "SUCCESSFUL",
  "attempts": 3,
  "notification_data": {
    "status_code": 200,
    "webhook_request": {
      "request_data": 123
    },
    "webhook_response": "OK"
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 1315847255 },
	{ "fi_lookup_key", "kDMvuyDVMbxPeXMLvaKxTWCivtndcaDpfDuGSdPAWCzeytRhBAtcImfbUeykKmT" },
	{ "cuid", "abcd1234" },
	{ "status", "SUCCESSFUL" },
	{ "attempts", 3 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 1315847255 )
	.add("fi_lookup_key", "kDMvuyDVMbxPeXMLvaKxTWCivtndcaDpfDuGSdPAWCzeytRhBAtcImfbUeykKmT" )
	.add("cuid", "abcd1234" )
	.add("status", "SUCCESSFUL" )
	.add("attempts", 3 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":1315847255,\"fi_lookup_key\":\"kDMvuyDVMbxPeXMLvaKxTWCivtndcaDpfDuGSdPAWCzeytRhBAtcImfbUeykKmT\",\"cuid\":\"abcd1234\",\"status\":\"SUCCESSFUL\",\"attempts\":3,\"notification_data\":{\"status_code\":200,\"webhook_request\":{\"request_data\":123},\"webhook_response\":\"OK\"}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notification_results/
```

### Path

POST /notification_results

### Description

Create a notification result and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
notification_id | number | yes
fi_lookup_key | string | yes
cuid | string | yes
status | [string enum](#post-notification_result-1)* | yes
attempts | number | yes
notification_data | object | no

See [notification result response attributes](#response-notification_result).

#### <a name="post-notification_result-1"></a>string enum*
- success
- failure

# Single-site jobs
Single-site job objects contain the information necessary to place a payment card on a merchant site, as well as status information about the card placement attempt. They are linked to a single cardholder, account, card, and merchant site.
## Get single-site job

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1062112537
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(1062112537);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(undefined);
```

```java
JsonValue singlesitejobs = session.get("/place_card_on_single_site_jobs", 1062112537, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1062112537,
  "status": "SUCCESSFUL",
  "status_message": "xpZhfqKiqVUBYFbMijJrSJQ",
  "termination_type": "BIILLABLE",
  "custom_data": {
    "qZURAOVfbOWO": "#BRy",
    "hUXzoxKCiVuM": 88,
    "dIYchBssVtXh": true
  },
  "notification_sent": true,
  "time_elapsed": 755998015,
  "started_on": "1974-07-25T21:32:26.175Z",
  "completed_on": "2008-08-05T00:33:59.395Z",
  "created_on": "1984-04-06T18:49:54.352Z",
  "last_updated_on": "1988-11-18T15:28:57.796Z",
  "cardholder": {
    "id": 692625618,
    "financial_institution_id": 1438581355,
    "agent_session_id": "jWDJG",
    "type": "ephemeral",
    "first_name": "KBxqNVpRsSLXdskHvwIYTmLq",
    "last_name": "WHQAYuFqewDJFbqhlganjL",
    "email": "hCBLujtZQdMj@zkeXcN.fuO",
    "meta_key": "RciDgHNcsRAEslpHhtYPEkhv",
    "cardholder_safe_key": "t4P0M42gn9SeIshshoSg1Wx6xOzmux1yMw+FUWr2TTo=",
    "custom_data": {
      "BwnzrJFPRGAX": "a8R[",
      "WrYkczqTubgo": 36,
      "tTrrqXRILfpV": false
    },
    "created_on": "2012-01-08T04:08:56.315Z",
    "last_updated_on": "2001-05-23T02:47:33.146Z"
  },
  "cardsavr_card": {
    "id": 486172788,
    "bin_id": 703901687,
    "cvv": "JWK",
    "expiration_month": "q",
    "expiration_year": "H",
    "name_on_card": "MliUwFTklFwxBWbzkUZgIoVNqLNTAtVucAUAulrdwETVrLCYtMSqqVCNRfoiupfSveNFRyrJNOsUXdIJgjpKxpjGLNmwOGHWqJtGPjBNXzRWOZzVBPETOHSUvWRYGcEAOshNYymRumdVmitsBCavnGRWLPeYLbMQfgvitBZVOhZlVfxNGsOuKcnIFfBcUAYkNDxivDmfhZUEYdcIndvUEnVyMuBHuWiFUiuKqkVACIKQBSaqGOutRaRHBszxRZ",
    "first_6": "ASeNxVnZtpBtMnHUVkHDILlVIPKFFflB",
    "first_7": "DehchKfiljfcXmsNKqQcEVUxtaoFflKh",
    "first_8": "hTWofzXEOXMWatnUkfhEeeHeLaIlTclX",
    "created_on": "2019-02-09T23:41:26.193Z",
    "last_updated_on": "1986-11-12T17:31:19.058Z"
  },
  "cardsavr_account": {
    "id": 899623632,
    "last_card_placed_id": 638453371,
    "username": "SAglUauPpcyfbbOVswettuLQfiTbZFiFMKniLqpVTDKUxAAbRpCkGTFtVqm",
    "username_hash": "icVVuuKOogywqcSyoBNbWWQwbhYTphaQcINnvntjOqWXEEodPxgWeepyxdF",
    "password": "XDxkGxHYEVamUhmXrEHZrMYZJxYUfzrRMpbBVXqGJHPepvxNifLQQvtLUtE",
    "last_login": "1995-01-28T19:31:54.347Z",
    "last_password_update": "2003-04-12T16:10:04.991Z",
    "last_saved_card": "1983-06-06T09:30:46.939Z",
    "created_on": "2013-03-11T16:50:29.819Z",
    "last_updated_on": "2008-10-04T18:28:55.973Z"
  }
}
```

### Path

GET /place_card_on_single_site_jobs **(batch)** or GET /place_card_on_single_site_jobs/:id **(singular)**

### Description

Returns the single-site job specified by the provided ID

#### Batch GET requests

**Batch requests** return the first page of all viewable single-site jobs, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/place_card_on_single_site_jobs?ids=1,2`

#### Singular GET requests

**Singular requests** only return the single-site job matching the id provided in the path.

**Example GET request path:**<br>`/place_card_on_single_site_jobs/1062112537`

### <a name="response-place_card_on_single_site_job"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
card_id | number (fk) | ID of card associated with this job.
status | string | Current status of job (e.g. pending_tfa).
status_message | string | Human readable representation of the jobs status.
termination_type | string | Final termination status of a job. (BILLABLE, SITE_INTERACTION_FAILURE, USER_DATA_FAILURE, PROCESS FAILURE)
custom_data | object | 
notification_sent | boolean | Indicates if a notification has been sent or posted for this job.
time_elapsed | number | Amount of time elapsed since the creation of the job.
started_on | date | Time when job started.
completed_on | date | Timestamp of job completion.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) | ID of cardholder associated with this job.
account_id | number (fk) | ID of account associated with this job.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- cardholder_ids
- card_ids
- account_ids
- status
- status_include / status_exclude
- termination_type
- termination_types_include / termaxation_types_exclude
- notification_sent
- time_elapsed_min / time_elapsed_max
- started_on_min / started_on_max
- completed_on_min / completed_on_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create single-site job

```javascript
const singlesitejob = await session.createSingleSiteJob({
  "cardholder_id": 1612637273,
  "card_id": 1854913196,
  "account_id": 1147480986,
  "status": "SUCCESSFUL",
  "custom_data": {
    "qZURAOVfbOWO": "#BRy",
    "hUXzoxKCiVuM": 88,
    "dIYchBssVtXh": true
  },
  "notification_sent": true,
  "time_elapsed": 755998015,
  "started_on": "1974-07-25T21:32:26.175Z",
  "completed_on": "2008-08-05T00:33:59.395Z",
  "termination_type": "BIILLABLE"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1612637273 },
	{ "card_id", 1854913196 },
	{ "account_id", 1147480986 },
	{ "status", "SUCCESSFUL" },
	{ "notification_sent", true },
	{ "time_elapsed", 755998015 },
	{ "started_on", "1974-07-25T21:32:26.175Z" },
	{ "completed_on", "2008-08-05T00:33:59.395Z" },
	{ "termination_type", "BIILLABLE" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1612637273 )
	.add("card_id", 1854913196 )
	.add("account_id", 1147480986 )
	.add("status", "SUCCESSFUL" )
	.add("notification_sent", true )
	.add("time_elapsed", 755998015 )
	.add("started_on", "1974-07-25T21:32:26.175Z" )
	.add("completed_on", "2008-08-05T00:33:59.395Z" )
	.add("termination_type", "BIILLABLE" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1612637273,\"card_id\":1854913196,\"account_id\":1147480986,\"status\":\"SUCCESSFUL\",\"custom_data\":{\"qZURAOVfbOWO\":\"#BRy\",\"hUXzoxKCiVuM\":88,\"dIYchBssVtXh\":true},\"notification_sent\":true,\"time_elapsed\":755998015,\"started_on\":\"1974-07-25T21:32:26.175Z\",\"completed_on\":\"2008-08-05T00:33:59.395Z\",\"termination_type\":\"BIILLABLE\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/
```

### Path

POST /place_card_on_single_site_jobs

### Description

Create a single-site job and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cardholder_id | number | yes
card_id | number | no
account_id | number | yes
status | [string enum](#post-place_card_on_single_site_job-1)* | no
custom_data | object | no
notification_sent | boolean | no
time_elapsed | number | no
started_on | date | no
completed_on | date | no

See [single-site job response attributes](#response-place_card_on_single_site_job).

#### <a name="post-place_card_on_single_site_job-1"></a>string enum*
- INITIATED
- REQUESTED
- IN_PROGRESS
- AUTH
- LOGIN_SUBMITTED
- PENDING_CREDS
- CREDS_RECEIVED
- PENDING_NEWCREDS
- NEWCREDS_RECEIVED
- PENDING_CARD
- LOGIN_RESUBMITTED
- PENDING_TFA
- TFA_CODE_RECEIVED
- TFA_SUBMITTED
- UPDATING
- QUEUED
- NETWORK_ISSUE
- CANCEL_REQUESTED
- CANCELLED
- CANCELLED_QUICKSTART
- ABANDONED
- ABANDONED_QUICKSTART
- KILLED
- ACCOUNT_SETUP_INCOMPLETE
- ACCOUNT_NOT_SUPPORTED
- COUNTRY_NOT_SUPPORTED
- PREPAID_ACCOUNT
- INACTIVE_ACCOUNT
- INVALID_CARD
- INVALID_ADDRESS
- PASSWORD_RESET_REQUIRED
- BUNDLED_SUBSCRIPTION
- FREE_ACCOUNT
- ACCOUNT_LOCKED
- DUPLICATE_CARD
- INVALID_EXPIRATION_DATE
- EXPIRED_CARD
- INVALID_CVV
- INVALID_NETWORK
- MAX_LIMIT_OF_STORED_CARDS
- SUCCESSFUL
- UNSUPPORTED_CAPTCHA
- TIMEOUT_CAPTCHA
- TIMEOUT_CREDENTIALS
- TIMEOUT_TFA
- TOO_MANY_LOGIN_FAILURES
- TOO_MANY_TFA_FAILURES
- UNSUCCESSFUL
- PROXY_PROBE_FAILED
- VBS_TIMEOUT
- VBS_ERROR

<aside class="notice">Update calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Update single-site job

```javascript
const singlesitejob = await session.updateSingleSiteJob(1,{
  "card_id": 1930681205,
  "status": "SUCCESSFUL",
  "custom_data": {
    "hmKlgwwVyEJH": ",U@ZOg</hMW*^3F%oIL(gY*7*",
    "RQXgCAzlbXjb": 50,
    "FiIWAkwPkDQy": false
  },
  "notification_sent": true,
  "time_elapsed": 492323209,
  "started_on": "1975-02-16T18:29:11.199Z",
  "completed_on": "1971-10-02T02:04:34.720Z",
  "termination_type": "BIILLABLE"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 1930681205 },
	{ "status", "SUCCESSFUL" },
	{ "notification_sent", true },
	{ "time_elapsed", 492323209 },
	{ "started_on", "1975-02-16T18:29:11.199Z" },
	{ "completed_on", "1971-10-02T02:04:34.720Z" },
	{ "termination_type", "BIILLABLE" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 1930681205 )
	.add("status", "SUCCESSFUL" )
	.add("notification_sent", true )
	.add("time_elapsed", 492323209 )
	.add("started_on", "1975-02-16T18:29:11.199Z" )
	.add("completed_on", "1971-10-02T02:04:34.720Z" )
	.add("termination_type", "BIILLABLE" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":1930681205,\"status\":\"SUCCESSFUL\",\"custom_data\":{\"hmKlgwwVyEJH\":\",U@ZOg</hMW*^3F%oIL(gY*7*\",\"RQXgCAzlbXjb\":50,\"FiIWAkwPkDQy\":false},\"notification_sent\":true,\"time_elapsed\":492323209,\"started_on\":\"1975-02-16T18:29:11.199Z\",\"completed_on\":\"1971-10-02T02:04:34.720Z\",\"termination_type\":\"BIILLABLE\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1062112537
```

### Path

PUT /place_card_on_single_site_jobs OR /place_card_on_single_site_jobs/{id}

### Description

Update a single-site job and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
card_id | number |
status | [string enum](#post-place_card_on_single_site_job-1)* |
custom_data | object |
notification_sent | boolean |
time_elapsed | number |
started_on | date |
completed_on | date |

See [single-site job response parameters](#response-place_card_on_single_site_job).

<aside class="notice">Update calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete single-site job

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1062112537
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

See [single-site job response parameters](#response-place_card_on_single_site_job).


# Card Placement Results
Card Placement results are a flatted version of the jobs and its publily available meta data. Although sensitive data like the PAN and account creds are not available, all the details of the job are captured here for future reference after the corresponding entities may have been deleted.
## Get card placement result

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/card_placement_results/547263910
```

```javascript
const cardplacementresults = await session.getCardPlacementResults(547263910);
```

```csharp
CardSavrResponse<CardPlacementResults> cardplacementresults = await session.GetCardPlacementResultsAsync(undefined);
```

```java
JsonValue cardplacementresults = session.get("/card_placement_results", 547263910, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 547263910,
  "merchant_site_hostname": "amazon.com",
  "meta_key": "MB9810411",
  "fi_name": "ACME Bank",
  "bank_identification_number": "57763101",
  "cuid": "abcd1234",
  "par": "NVNGnuaAFHRghpzoGGrXDUHgrkFRX",
  "card_customer_key": "NA",
  "account_customer_key": "1$abcd1234",
  "status": "SUCCESSFUL",
  "status_message": "myxbYIEnDwddGPOOztiVRvfvqAWYuW",
  "termination_type": "BIILLABLE",
  "custom_data": {
    "kNBLqLJcMxXD": ",F",
    "xGUkqvXpBFXC": 54,
    "dXjDXpAdvubE": false
  },
  "time_elapsed": 1154137285,
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "trace": "tlemzgskXCIPAkQImxmvbklUTTnALhBEecysfYklurCPILcdqLKuhpwVWwjghBtzBnGoHwojDZTEzWASEeBaXAgEsMqmRSdPWeIVzwTRmtDbgRdSxVKDedTLeGpnNGaRerrIgMHQcJbUQKfynbeezoidslnNWdscaOzkSHnRZQYAcosMCRdyAFYbrhKNZmlHrYHmCZnuUtdKsPXwmpqKcXGnOClfMStdqruZQBsZRiSybcMpzNmhASdwMpjsxD",
  "email_sent": false,
  "completed_on": "1988-11-06T20:44:55.231Z",
  "created_on": "2011-12-10T16:47:32.331Z",
  "last_updated_on": "2006-08-15T23:09:16.241Z",
  "financial_institution": {
    "id": 350876797,
    "name": "pZwBrrXNofgwKbKVekzQtrGTNnkMXvHIFnPMWSNtfVlgHXIUtsilljHnvdaQYJs",
    "description": "wIE",
    "lookup_key": "nxXOiipKeVGmpqWidlSpvXQwpsVxEOOHooKdOWnDzYyRJDJFUPhzVEtpZrxVKNt",
    "alternate_lookup_key": "FioCqkLdegJurrlVwLItUnTKLNpACMmhkUlFGTatDHgWLCaYsOxrKJTxYtJnoLd",
    "config": {
      "sRmIRrEcqCwg": "8a*_CZ>A)!Ib[77+iAsHo>",
      "gHtbrtWeTAie": 30,
      "RdrOBmSfnHqf": true
    },
    "created_on": "1974-07-15T07:36:09.735Z",
    "last_updated_on": "1970-03-08T18:31:53.841Z"
  },
  "merchant_site": {
    "id": 79415849,
    "name": "QZbiEiOtJe",
    "host": "OLFjrghGhDosYlbkMVEKRlMSBK",
    "tags": [
      "-4ScS",
      100,
      "aif*uD"
    ],
    "queue_name": "vbs_queue",
    "required_form_fields": [
      ",IA.k*fG69a",
      11,
      "@_qB="
    ],
    "images": [
      {
        "plGVLVmleGTL": "nK]QMnx8<R^P+",
        "IgTUYxWGaVom": 52,
        "hVuEpmgCsGHy": false
      },
      {
        "yAmCSAyXfKCR": "hw-3Ek/SqA<qH))7!Q2xQq%Eo,",
        "bgKBJRUoyfvV": 90,
        "bJXitmnOsxNT": true
      },
      {
        "XWrdxbjEzVYO": "dO*X~WBM>M9P5teNPx0Vf&D",
        "rDkMeYqBDtyf": 89,
        "uXUXQndfxMjf": true
      }
    ],
    "account_identification": {
      "QkzxgtbMGtyX": ",5JuYUky*4O#zc5.6gxdP7t#&_]h_",
      "vLlUteuiFasK": 65,
      "eUSjLnPDTKth": true
    },
    "messages": {
      "WeTCIHsbEDFk": "2@gn5zX9FuLY/2Xfg_a)TFBe8%",
      "rnvnqVjnvoHn": 19,
      "cpQTMOIcUiYE": false
    },
    "mfa": true,
    "move_mouse_to_element": true,
    "proxy_order": [
      "/{46#PnOH^Dl.)TQm",
      18,
      "[AGv"
    ],
    "credit_card_page": "OhVlluapdOxzbLuATmeSKhVKZbzCrWt",
    "forgot_password_page": "r",
    "quick_start": true,
    "login_page": "IUxifTybyVRgLPzTJcBjlDdvTXr",
    "login": {
      "cqqfXzQFJJJG": "/M~U3v6@NZqXpq%6VIqw+0",
      "QkWurrfZUpFv": 26,
      "VkqlFcpIbRnN": false
    }
  },
  "cardsavr_bin": {
    "id": 189189966,
    "financial_institution_id": 1063624831,
    "custom_data": {
      "TWuCYVMtRawm": "6H]t8~lxRFkMu3FdlvFI}b[dy)rSu",
      "SkmXTgQYZpBJ": 10,
      "LrqQPWJvRAuf": false
    },
    "created_on": "1972-05-11T09:28:06.393Z",
    "last_updated_on": "2013-05-08T09:44:55.327Z"
  },
  "place_card_on_single_site_job_id": 499911904
}
```

### Path

GET /card_placement_results **(batch)** or GET /card_placement_results/:id **(singular)**

### Description

Returns the card placement result specified by the provided ID

#### Batch GET requests

**Batch requests** return the first page of all viewable card placement results, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/card_placement_results?ids=1,2`

#### Singular GET requests

**Singular requests** only return the card placement result matching the id provided in the path.

**Example GET request path:**<br>`/card_placement_results/547263910`

### <a name="response-card_placement_result"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
merchant_site_hostname | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
fi_name | string | 
bank_identification_number | string | 
cuid | string | 
par | string | 
card_customer_key | string | 
account_customer_key | string | 
status | string | 
status_message | string | Human readable representation of the jobs status.
termination_type | string | Final termination status of a job. (BILLABLE, SITE_INTERACTION_FAILURE, USER_DATA_FAILURE, PROCESS FAILURE)
custom_data | object | 
time_elapsed | number | 
first_6 | string | First six digits of card number.
first_7 | string | First seven digits of card number.
first_8 | string | First eight digits of card number.
trace | string | 
financial_institution_id | number (fk) | 
merchant_site_id | number (fk) | 
email_sent | boolean | 
completed_on | date | 
created_on | date | Date this job result was created on
last_updated_on | date | Date this job result was last updated on
place_card_on_single_site_job_id | number | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

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
- status
- termination_type
- termination_types_include / termaxation_types_exclude
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

## Create card placement result

```javascript
const cardplacementresult = await session.createCardPlacementResult({
  "merchant_site_hostname": "amazon.com",
  "meta_key": "MB9810411",
  "fi_name": "ACME Bank",
  "bank_identification_number": "57763101",
  "cuid": "abcd1234",
  "par": "NVNGnuaAFHRghpzoGGrXDUHgrkFRX",
  "card_customer_key": "NA",
  "account_customer_key": "1$abcd1234",
  "status": "SUCCESSFUL",
  "status_message": "myxbYIEnDwddGPOOztiVRvfvqAWYuW",
  "termination_type": "BIILLABLE",
  "custom_data": {
    "kNBLqLJcMxXD": ",F",
    "xGUkqvXpBFXC": 54,
    "dXjDXpAdvubE": false
  },
  "time_elapsed": 1154137285,
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "trace": "tlemzgskXCIPAkQImxmvbklUTTnALhBEecysfYklurCPILcdqLKuhpwVWwjghBtzBnGoHwojDZTEzWASEeBaXAgEsMqmRSdPWeIVzwTRmtDbgRdSxVKDedTLeGpnNGaRerrIgMHQcJbUQKfynbeezoidslnNWdscaOzkSHnRZQYAcosMCRdyAFYbrhKNZmlHrYHmCZnuUtdKsPXwmpqKcXGnOClfMStdqruZQBsZRiSybcMpzNmhASdwMpjsxD",
  "place_card_on_single_site_job_id": 499911904,
  "financial_institution_id": 1214740671,
  "merchant_site_id": 1073264345,
  "email_sent": false,
  "completed_on": "1988-11-06T20:44:55.231Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "merchant_site_hostname", "amazon.com" },
	{ "meta_key", "MB9810411" },
	{ "fi_name", "ACME Bank" },
	{ "bank_identification_number", "57763101" },
	{ "cuid", "abcd1234" },
	{ "par", "NVNGnuaAFHRghpzoGGrXDUHgrkFRX" },
	{ "card_customer_key", "NA" },
	{ "account_customer_key", "1$abcd1234" },
	{ "status", "SUCCESSFUL" },
	{ "status_message", "myxbYIEnDwddGPOOztiVRvfvqAWYuW" },
	{ "termination_type", "BIILLABLE" },
	{ "time_elapsed", 1154137285 },
	{ "first_6", "000000" },
	{ "first_7", "0000000" },
	{ "first_8", "00000000" },
	{ "trace", "tlemzgskXCIPAkQImxmvbklUTTnALhBEecysfYklurCPILcdqLKuhpwVWwjghBtzBnGoHwojDZTEzWASEeBaXAgEsMqmRSdPWeIVzwTRmtDbgRdSxVKDedTLeGpnNGaRerrIgMHQcJbUQKfynbeezoidslnNWdscaOzkSHnRZQYAcosMCRdyAFYbrhKNZmlHrYHmCZnuUtdKsPXwmpqKcXGnOClfMStdqruZQBsZRiSybcMpzNmhASdwMpjsxD" },
	{ "place_card_on_single_site_job_id", 499911904 },
	{ "financial_institution_id", 1214740671 },
	{ "merchant_site_id", 1073264345 },
	{ "email_sent", false },
	{ "completed_on", "1988-11-06T20:44:55.231Z" }
};

CardSavrResponse<CardPlacementResult> cardplacementresult = await http.CreateCardPlacementResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("merchant_site_hostname", "amazon.com" )
	.add("meta_key", "MB9810411" )
	.add("fi_name", "ACME Bank" )
	.add("bank_identification_number", "57763101" )
	.add("cuid", "abcd1234" )
	.add("par", "NVNGnuaAFHRghpzoGGrXDUHgrkFRX" )
	.add("card_customer_key", "NA" )
	.add("account_customer_key", "1$abcd1234" )
	.add("status", "SUCCESSFUL" )
	.add("status_message", "myxbYIEnDwddGPOOztiVRvfvqAWYuW" )
	.add("termination_type", "BIILLABLE" )
	.add("time_elapsed", 1154137285 )
	.add("first_6", "000000" )
	.add("first_7", "0000000" )
	.add("first_8", "00000000" )
	.add("trace", "tlemzgskXCIPAkQImxmvbklUTTnALhBEecysfYklurCPILcdqLKuhpwVWwjghBtzBnGoHwojDZTEzWASEeBaXAgEsMqmRSdPWeIVzwTRmtDbgRdSxVKDedTLeGpnNGaRerrIgMHQcJbUQKfynbeezoidslnNWdscaOzkSHnRZQYAcosMCRdyAFYbrhKNZmlHrYHmCZnuUtdKsPXwmpqKcXGnOClfMStdqruZQBsZRiSybcMpzNmhASdwMpjsxD" )
	.add("place_card_on_single_site_job_id", 499911904 )
	.add("financial_institution_id", 1214740671 )
	.add("merchant_site_id", 1073264345 )
	.add("email_sent", false )
	.add("completed_on", "1988-11-06T20:44:55.231Z" )
	.build();
JsonValue cardplacementresult = session.post("/card_placement_results", body, null, null);
```

```shell
curl -d "{\"merchant_site_hostname\":\"amazon.com\",\"meta_key\":\"MB9810411\",\"fi_name\":\"ACME Bank\",\"bank_identification_number\":\"57763101\",\"cuid\":\"abcd1234\",\"par\":\"NVNGnuaAFHRghpzoGGrXDUHgrkFRX\",\"card_customer_key\":\"NA\",\"account_customer_key\":\"1$abcd1234\",\"status\":\"SUCCESSFUL\",\"status_message\":\"myxbYIEnDwddGPOOztiVRvfvqAWYuW\",\"termination_type\":\"BIILLABLE\",\"custom_data\":{\"kNBLqLJcMxXD\":\",F\",\"xGUkqvXpBFXC\":54,\"dXjDXpAdvubE\":false},\"time_elapsed\":1154137285,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\",\"trace\":\"tlemzgskXCIPAkQImxmvbklUTTnALhBEecysfYklurCPILcdqLKuhpwVWwjghBtzBnGoHwojDZTEzWASEeBaXAgEsMqmRSdPWeIVzwTRmtDbgRdSxVKDedTLeGpnNGaRerrIgMHQcJbUQKfynbeezoidslnNWdscaOzkSHnRZQYAcosMCRdyAFYbrhKNZmlHrYHmCZnuUtdKsPXwmpqKcXGnOClfMStdqruZQBsZRiSybcMpzNmhASdwMpjsxD\",\"place_card_on_single_site_job_id\":499911904,\"financial_institution_id\":1214740671,\"merchant_site_id\":1073264345,\"email_sent\":false,\"completed_on\":\"1988-11-06T20:44:55.231Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/card_placement_results/
```

### Path

POST /card_placement_results

### Description

Create a card placement result and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
merchant_site_hostname | string | no
meta_key | string | no
fi_name | string | yes
bank_identification_number | string | no
cuid | string | yes
par | string | no
card_customer_key | string | no
account_customer_key | string | no
status | string | no
status_message | string | no
termination_type | string | no
custom_data | object | no
time_elapsed | number | no
first_6 | string | no
first_7 | string | no
first_8 | string | no
trace | string | no
place_card_on_single_site_job_id | number | no
financial_institution_id | number | yes
merchant_site_id | number | yes
email_sent | boolean | no
completed_on | date | yes

See [card placement result response attributes](#response-card_placement_result).


## Update card placement result

```javascript
const cardplacementresult = await session.updateCardPlacementResult(1,{
  "merchant_site_hostname": "amazon.com",
  "meta_key": "MB9810411",
  "fi_name": "ACME Bank",
  "bank_identification_number": "80847680",
  "cuid": "abcd1234",
  "par": "TjUaPvoIniQNQrdaQWPFVmsOevUBu",
  "card_customer_key": "NA",
  "account_customer_key": "1$abcd1234",
  "status": "SUCCESSFUL",
  "status_message": "wDQtKlkRymmZSojOTcoEyMPAMmyoMpJQ",
  "termination_type": "BIILLABLE",
  "custom_data": {
    "UbBXhWpfPqcy": "}vL=GByf1xWnxMo",
    "qsuXTNzEDWmS": 26,
    "amORcTVeHPbG": false
  },
  "time_elapsed": 2067869614,
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "trace": "wlMblduiLLdnreVqyLekxceCfcCXVMqDtPQHlGHUcEUhCodnlAYpUuFyDibpBzuuAqFvXpgXoRbYXlyZUXKxfAvvPSGtOswrlzSiDDlReaGFaNvZBSxlwJkrTJRHRpIBGPcNzagKHCHqrqxtuaWBPnscRIztSVtLOUUGKfpnNgYfXXQWXYiOcExlaGwjSEIRiLrfbxefQqaonwxWVfeyjRioBTSAxWqmddqoRJJiroaRmytVrpRPXPAVdMvqvF",
  "financial_institution_id": 1395539547,
  "merchant_site_id": 1940041051,
  "email_sent": false,
  "completed_on": "1985-02-09T05:56:02.589Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "merchant_site_hostname", "amazon.com" },
	{ "meta_key", "MB9810411" },
	{ "fi_name", "ACME Bank" },
	{ "bank_identification_number", "80847680" },
	{ "cuid", "abcd1234" },
	{ "par", "TjUaPvoIniQNQrdaQWPFVmsOevUBu" },
	{ "card_customer_key", "NA" },
	{ "account_customer_key", "1$abcd1234" },
	{ "status", "SUCCESSFUL" },
	{ "status_message", "wDQtKlkRymmZSojOTcoEyMPAMmyoMpJQ" },
	{ "termination_type", "BIILLABLE" },
	{ "time_elapsed", 2067869614 },
	{ "first_6", "000000" },
	{ "first_7", "0000000" },
	{ "first_8", "00000000" },
	{ "trace", "wlMblduiLLdnreVqyLekxceCfcCXVMqDtPQHlGHUcEUhCodnlAYpUuFyDibpBzuuAqFvXpgXoRbYXlyZUXKxfAvvPSGtOswrlzSiDDlReaGFaNvZBSxlwJkrTJRHRpIBGPcNzagKHCHqrqxtuaWBPnscRIztSVtLOUUGKfpnNgYfXXQWXYiOcExlaGwjSEIRiLrfbxefQqaonwxWVfeyjRioBTSAxWqmddqoRJJiroaRmytVrpRPXPAVdMvqvF" },
	{ "financial_institution_id", 1395539547 },
	{ "merchant_site_id", 1940041051 },
	{ "email_sent", false },
	{ "completed_on", "1985-02-09T05:56:02.589Z" }
};

CardSavrResponse<CardPlacementResult> cardplacementresult = await http.UpdateCardPlacementResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("merchant_site_hostname", "amazon.com" )
	.add("meta_key", "MB9810411" )
	.add("fi_name", "ACME Bank" )
	.add("bank_identification_number", "80847680" )
	.add("cuid", "abcd1234" )
	.add("par", "TjUaPvoIniQNQrdaQWPFVmsOevUBu" )
	.add("card_customer_key", "NA" )
	.add("account_customer_key", "1$abcd1234" )
	.add("status", "SUCCESSFUL" )
	.add("status_message", "wDQtKlkRymmZSojOTcoEyMPAMmyoMpJQ" )
	.add("termination_type", "BIILLABLE" )
	.add("time_elapsed", 2067869614 )
	.add("first_6", "000000" )
	.add("first_7", "0000000" )
	.add("first_8", "00000000" )
	.add("trace", "wlMblduiLLdnreVqyLekxceCfcCXVMqDtPQHlGHUcEUhCodnlAYpUuFyDibpBzuuAqFvXpgXoRbYXlyZUXKxfAvvPSGtOswrlzSiDDlReaGFaNvZBSxlwJkrTJRHRpIBGPcNzagKHCHqrqxtuaWBPnscRIztSVtLOUUGKfpnNgYfXXQWXYiOcExlaGwjSEIRiLrfbxefQqaonwxWVfeyjRioBTSAxWqmddqoRJJiroaRmytVrpRPXPAVdMvqvF" )
	.add("financial_institution_id", 1395539547 )
	.add("merchant_site_id", 1940041051 )
	.add("email_sent", false )
	.add("completed_on", "1985-02-09T05:56:02.589Z" )
	.build();
JsonValue cardplacementresult = session.put("/card_placement_results", body, null, null);
```

```shell
curl -d "{\"merchant_site_hostname\":\"amazon.com\",\"meta_key\":\"MB9810411\",\"fi_name\":\"ACME Bank\",\"bank_identification_number\":\"80847680\",\"cuid\":\"abcd1234\",\"par\":\"TjUaPvoIniQNQrdaQWPFVmsOevUBu\",\"card_customer_key\":\"NA\",\"account_customer_key\":\"1$abcd1234\",\"status\":\"SUCCESSFUL\",\"status_message\":\"wDQtKlkRymmZSojOTcoEyMPAMmyoMpJQ\",\"termination_type\":\"BIILLABLE\",\"custom_data\":{\"UbBXhWpfPqcy\":\"}vL=GByf1xWnxMo\",\"qsuXTNzEDWmS\":26,\"amORcTVeHPbG\":false},\"time_elapsed\":2067869614,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\",\"trace\":\"wlMblduiLLdnreVqyLekxceCfcCXVMqDtPQHlGHUcEUhCodnlAYpUuFyDibpBzuuAqFvXpgXoRbYXlyZUXKxfAvvPSGtOswrlzSiDDlReaGFaNvZBSxlwJkrTJRHRpIBGPcNzagKHCHqrqxtuaWBPnscRIztSVtLOUUGKfpnNgYfXXQWXYiOcExlaGwjSEIRiLrfbxefQqaonwxWVfeyjRioBTSAxWqmddqoRJJiroaRmytVrpRPXPAVdMvqvF\",\"financial_institution_id\":1395539547,\"merchant_site_id\":1940041051,\"email_sent\":false,\"completed_on\":\"1985-02-09T05:56:02.589Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/card_placement_results/547263910
```

### Path

PUT /card_placement_results OR /card_placement_results/{id}

### Description

Update a card placement result and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
merchant_site_hostname | string |
meta_key | string |
fi_name | string |
bank_identification_number | string |
cuid | string |
par | string |
card_customer_key | string |
account_customer_key | string |
status | string |
status_message | string |
termination_type | string |
custom_data | object |
time_elapsed | number |
first_6 | string |
first_7 | string |
first_8 | string |
trace | string |
financial_institution_id | number |
merchant_site_id | number |
email_sent | boolean |
completed_on | date |

See [card placement result response parameters](#response-card_placement_result).


## Delete card placement result

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/card_placement_results/547263910
```

```javascript
await session.deleteCardPlacementResult(undefined);
```

```csharp
CardSavrResponse<CardPlacementResult> cardplacementresult = await http.DeleteCardPlacementResultAsync(undefined);
```

```java
JsonValue cardplacementresult = session.delete("/card_placement_results", undefined, null);
```

### Path

DELETE /card_placement_results/{id}

### Description

Delete a card placement result and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [card placement result response parameters](#response-card_placement_result).

