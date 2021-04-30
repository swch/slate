
# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1487472190
```

```javascript
const account = await session.getAccounts(1487472190);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(1487472190);
```

```java
JsonValue accounts = session.get("/cardsavr_accounts", 1487472190, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1487472190,
  "last_card_placed_id": 1881289061,
  "last_login": "1992-07-01T11:37:19.822Z",
  "last_password_update": "1981-09-12T23:19:00.638Z",
  "last_saved_card": "2016-04-06T20:52:39.191Z",
  "created_on": "2010-03-06T23:03:01.161Z",
  "last_updated_on": "1970-09-26T05:32:52.835Z",
  "cardholder_id": 1708662020,
  "merchant_site_id": 665351667
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

**Example GET request path:**<br>`/cardsavr_accounts/1487472190`

### <a name="response-cardsavr_account"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
last_card_placed_id | number (fk) | 
last_login | date | 
last_password_update | date | 
last_saved_card | date | 
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) | 
merchant_site_id | number (fk) | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- cardholder_ids
- merchant_site_ids
- last_card_placed_ids
- last_login_min / last_login_max
- last_password_update_min / last_password_update_max
- last_saved_card_min / last_saved_card_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create account

```javascript
const account = await session.createAccount({
  "cardholder_id": 1708662020,
  "merchant_site_id": 665351667,
  "last_card_placed_id": 1881289061,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1708662020 },
	{ "merchant_site_id", 665351667 },
	{ "last_card_placed_id", 1881289061 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1708662020 )
	.add("merchant_site_id", 665351667 )
	.add("last_card_placed_id", 1881289061 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1708662020,\"merchant_site_id\":665351667,\"last_card_placed_id\":1881289061,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/
```

### Path

POST /cardsavr_accounts

### Description

Create an account and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cardholder_id | number | yes
merchant_site_id | number | yes
last_card_placed_id | number | no
username | string | no
password | string | no

See [account response attributes](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username and password when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Update account

```javascript
const account = await session.updateAccount({
  "last_card_placed_id": 1743364227,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "id": "1"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 1743364227 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "id", "1" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 1743364227 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("id", "1" )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":1743364227,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1487472190
```

### Path

PUT /cardsavr_accounts OR /cardsavr_accounts/{id}

### Description

Update a account and return the updated object.  An id is required on every update request.

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
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1487472190
```

```javascript
await session.deleteAccount(1487472190);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(1487472190);
```

```java
JsonValue account = session.delete("/cardsavr_accounts", 1487472190, null);
```

### Path

DELETE /cardsavr_accounts/{id}

### Description

Delete a account and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [account response parameters](#response-cardsavr_account).


# Addresses
Address objects contain billing address information for a particular cardholder.
## Get address

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/130973664
```

```javascript
const addresses = await session.getAddresses(130973664);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(130973664);
```

```java
JsonValue addresses = session.get("/cardsavr_addresses", 130973664, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 130973664,
  "address1": "KYqTHLVtyuNBGEBhgetEzozpisoTrurFcwtHrfRpEaIoehVlOknruHQCSMePPafdTbxvBnwFxUWzPTjIeGkUvHQfFbqMczoyMlk",
  "address2": "bmWAewIfLgcGiqKJijPieCzjaERVlXuClDSyHpQyaMTAUDmWzsDiMCgjWwcHhpWOjDRgivOrurEfuufAWGivsZfwcIGgdKfQcSw",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "FtSpwqqNNLDBpQryOBJiy",
  "created_on": "2014-03-08T06:17:21.269Z",
  "last_updated_on": "1982-03-09T10:19:01.517Z",
  "cardholder_id": 1017066167
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

**Example GET request path:**<br>`/cardsavr_addresses/130973664`

### <a name="response-cardsavr_address"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
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
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) | 

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
  "cardholder_id": 1017066167,
  "address1": "KYqTHLVtyuNBGEBhgetEzozpisoTrurFcwtHrfRpEaIoehVlOknruHQCSMePPafdTbxvBnwFxUWzPTjIeGkUvHQfFbqMczoyMlk",
  "address2": "bmWAewIfLgcGiqKJijPieCzjaERVlXuClDSyHpQyaMTAUDmWzsDiMCgjWwcHhpWOjDRgivOrurEfuufAWGivsZfwcIGgdKfQcSw",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "FtSpwqqNNLDBpQryOBJiy"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1017066167 },
	{ "address1", "KYqTHLVtyuNBGEBhgetEzozpisoTrurFcwtHrfRpEaIoehVlOknruHQCSMePPafdTbxvBnwFxUWzPTjIeGkUvHQfFbqMczoyMlk" },
	{ "address2", "bmWAewIfLgcGiqKJijPieCzjaERVlXuClDSyHpQyaMTAUDmWzsDiMCgjWwcHhpWOjDRgivOrurEfuufAWGivsZfwcIGgdKfQcSw" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "phone_number", "FtSpwqqNNLDBpQryOBJiy" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1017066167 )
	.add("address1", "KYqTHLVtyuNBGEBhgetEzozpisoTrurFcwtHrfRpEaIoehVlOknruHQCSMePPafdTbxvBnwFxUWzPTjIeGkUvHQfFbqMczoyMlk" )
	.add("address2", "bmWAewIfLgcGiqKJijPieCzjaERVlXuClDSyHpQyaMTAUDmWzsDiMCgjWwcHhpWOjDRgivOrurEfuufAWGivsZfwcIGgdKfQcSw" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("phone_number", "FtSpwqqNNLDBpQryOBJiy" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1017066167,\"address1\":\"KYqTHLVtyuNBGEBhgetEzozpisoTrurFcwtHrfRpEaIoehVlOknruHQCSMePPafdTbxvBnwFxUWzPTjIeGkUvHQfFbqMczoyMlk\",\"address2\":\"bmWAewIfLgcGiqKJijPieCzjaERVlXuClDSyHpQyaMTAUDmWzsDiMCgjWwcHhpWOjDRgivOrurEfuufAWGivsZfwcIGgdKfQcSw\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"phone_number\":\"FtSpwqqNNLDBpQryOBJiy\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/
```

### Path

POST /cardsavr_addresses

### Description

Create an address and return the created object.

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
const address = await session.updateAddress({
  "address1": "jGixicoHkXvyzxKbnVuhFblIWRaLmlOQmULbkXtHyxJdpBnfvCqxtkjvxKxFwePbsxMWNtJapMrstojxQClPpaeTwmafXHeErCg",
  "address2": "tfosSQJJYXilGmFYeyXqxrSQcvsRUrDnoUsDwDCLYyejWrYepYGQEoiGKVFSXxZzCFuFaGBvdtvMKhiNQoSlxRZJcVEDAjDNgrU",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "BKstRagrwqWBynJKSa",
  "id": "1"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "jGixicoHkXvyzxKbnVuhFblIWRaLmlOQmULbkXtHyxJdpBnfvCqxtkjvxKxFwePbsxMWNtJapMrstojxQClPpaeTwmafXHeErCg" },
	{ "address2", "tfosSQJJYXilGmFYeyXqxrSQcvsRUrDnoUsDwDCLYyejWrYepYGQEoiGKVFSXxZzCFuFaGBvdtvMKhiNQoSlxRZJcVEDAjDNgrU" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "phone_number", "BKstRagrwqWBynJKSa" },
	{ "id", "1" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "jGixicoHkXvyzxKbnVuhFblIWRaLmlOQmULbkXtHyxJdpBnfvCqxtkjvxKxFwePbsxMWNtJapMrstojxQClPpaeTwmafXHeErCg" )
	.add("address2", "tfosSQJJYXilGmFYeyXqxrSQcvsRUrDnoUsDwDCLYyejWrYepYGQEoiGKVFSXxZzCFuFaGBvdtvMKhiNQoSlxRZJcVEDAjDNgrU" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", false )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("phone_number", "BKstRagrwqWBynJKSa" )
	.add("id", "1" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"jGixicoHkXvyzxKbnVuhFblIWRaLmlOQmULbkXtHyxJdpBnfvCqxtkjvxKxFwePbsxMWNtJapMrstojxQClPpaeTwmafXHeErCg\",\"address2\":\"tfosSQJJYXilGmFYeyXqxrSQcvsRUrDnoUsDwDCLYyejWrYepYGQEoiGKVFSXxZzCFuFaGBvdtvMKhiNQoSlxRZJcVEDAjDNgrU\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"phone_number\":\"BKstRagrwqWBynJKSa\",\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/130973664
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
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/130973664
```

```javascript
await session.deleteAddress(130973664);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(130973664);
```

```java
JsonValue address = session.delete("/cardsavr_addresses", 130973664, null);
```

### Path

DELETE /cardsavr_addresses/{id}

### Description

Delete a address and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [address response parameters](#response-cardsavr_address).


# Bins
A cardsavr_bin object
## Get bin

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/376593441
```

```javascript
const bins = await session.getBins(376593441);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(376593441);
```

```java
JsonValue bins = session.get("/cardsavr_bins", 376593441, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 376593441,
  "financial_institution_id": 996398491,
  "custom_data": {
    "ZItHKCFrAjeO": "+wh",
    "BfjBnZkLWlwO": 21,
    "UKnIpCnLgOkM": false
  },
  "created_on": "2013-07-27T22:10:25.475Z",
  "last_updated_on": "1985-10-24T21:18:02.350Z",
  "bank_identification_number": "63080440"
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

**Example GET request path:**<br>`/cardsavr_bins/376593441`

### <a name="response-cardsavr_bin"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
financial_institution_id | number (fk) | 
custom_data | object | 
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
  "financial_institution_id": 996398491,
  "bank_identification_number": "63080440",
  "custom_data": {
    "ZItHKCFrAjeO": "+wh",
    "BfjBnZkLWlwO": 21,
    "UKnIpCnLgOkM": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 996398491 },
	{ "bank_identification_number", "63080440" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 996398491 )
	.add("bank_identification_number", "63080440" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":996398491,\"bank_identification_number\":\"63080440\",\"custom_data\":{\"ZItHKCFrAjeO\":\"+wh\",\"BfjBnZkLWlwO\":21,\"UKnIpCnLgOkM\":false}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
const bin = await session.updateBin({
  "financial_institution_id": 1212737788,
  "custom_data": {
    "unnWMfHWZEFC": "9^I[86D",
    "XRjwxOlPJzYI": 71,
    "BMEIVrFyULiT": false
  },
  "id": "1"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1212737788 },
	{ "id", "1" }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1212737788 )
	.add("id", "1" )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1212737788,\"custom_data\":{\"unnWMfHWZEFC\":\"9^I[86D\",\"XRjwxOlPJzYI\":71,\"BMEIVrFyULiT\":false},\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/376593441
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
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/376593441
```

```javascript
await session.deleteBin(376593441);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(376593441);
```

```java
JsonValue bin = session.delete("/cardsavr_bins", 376593441, null);
```

### Path

DELETE /cardsavr_bins/{id}

### Description

Delete a bin and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [bin response parameters](#response-cardsavr_bin).


# Cards
Card objects contain information about a payment card belonging to a single cardholder. Card objects are used to populate users' payment information on merchant sites.
## Get card

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1471132855
```

```javascript
const cards = await session.getCards(1471132855);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(1471132855);
```

```java
JsonValue cards = session.get("/cardsavr_cards", 1471132855, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1471132855,
  "address_id": 701323532,
  "bin_id": 1514673407,
  "name_on_card": "Joe C Smith",
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "created_on": "1979-11-14T09:52:07.481Z",
  "last_updated_on": "1989-11-29T11:04:04.571Z",
  "expiration_month": 12,
  "expiration_year": 24,
  "cardholder_id": 228812437,
  "par": "AULZxHCkeeEHEoJWiwKnzkJGBhFJf"
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

**Example GET request path:**<br>`/cardsavr_cards/1471132855`

### <a name="response-cardsavr_card"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
address_id | number | 
bin_id | number (fk) | 
name_on_card | string | 
first_6 | string | 
first_7 | string | 
first_8 | string | 
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
expiration_month | string | 
expiration_year | string | 
cardholder_id | number (fk) | 
par | string | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- cardholder_ids
- address_ids
- bin_ids
- pars
- first_6
- first_7
- first_8
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create card

```javascript
const card = await session.createCard({
  "cardholder_id": 228812437,
  "address_id": 701323532,
  "bin_id": 1514673407,
  "par": "AULZxHCkeeEHEoJWiwKnzkJGBhFJf",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Joe C Smith",
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 228812437 },
	{ "address_id", 701323532 },
	{ "bin_id", 1514673407 },
	{ "par", "AULZxHCkeeEHEoJWiwKnzkJGBhFJf" },
	{ "pan", "4111111111111111" },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Joe C Smith" },
	{ "first_6", "000000" },
	{ "first_7", "0000000" },
	{ "first_8", "00000000" }
};

CardSavrResponse<Card> card = await http.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 228812437 )
	.add("address_id", 701323532 )
	.add("bin_id", 1514673407 )
	.add("par", "AULZxHCkeeEHEoJWiwKnzkJGBhFJf" )
	.add("pan", "4111111111111111" )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Joe C Smith" )
	.add("first_6", "000000" )
	.add("first_7", "0000000" )
	.add("first_8", "00000000" )
	.build();
JsonValue card = session.post("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":228812437,\"address_id\":701323532,\"bin_id\":1514673407,\"par\":\"AULZxHCkeeEHEoJWiwKnzkJGBhFJf\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\",\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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

## Update card

```javascript
const card = await session.updateCard(1, {
  "address_id": 576026016,
  "bin_id": 1204478035,
  "name_on_card": "Joe C Smith",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address_id", 576026016 },
	{ "bin_id", 1204478035 },
	{ "name_on_card", "Joe C Smith" },
	{ "pan", "4111111111111111" },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "first_6", "000000" },
	{ "first_7", "0000000" },
	{ "first_8", "00000000" },
	{ "id", "1" }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address_id", 576026016 )
	.add("bin_id", 1204478035 )
	.add("name_on_card", "Joe C Smith" )
	.add("pan", "4111111111111111" )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("first_6", "000000" )
	.add("first_7", "0000000" )
	.add("first_8", "00000000" )
	.add("id", "1" )
	.build();
JsonValue card = session.put("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"address_id\":576026016,\"bin_id\":1204478035,\"name_on_card\":\"Joe C Smith\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\",\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1471132855
```

### Path

PUT /cardsavr_cards OR /cardsavr_cards/{id}

### Description

Update a card and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
address_id | number |
bin_id | number |
name_on_card | string |

See [card response parameters](#response-cardsavr_card).


## Delete card

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1471132855
```

```javascript
await session.deleteCard(1471132855);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(1471132855);
```

```java
JsonValue card = session.delete("/cardsavr_cards", 1471132855, null);
```

### Path

DELETE /cardsavr_cards/{id}

### Description

Delete a card and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [card response parameters](#response-cardsavr_card).


# Cardholders
Entities which represent end-users/cardholders.
## Get cardholder

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardholders/1831079394
```

```javascript
const cardholders = await session.getCardholders(1831079394);
```

```csharp
CardSavrResponse<Cardholders> cardholders = await session.GetCardholdersAsync(1831079394);
```

```java
JsonValue cardholders = session.get("/cardholders", 1831079394, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1831079394,
  "financial_institution_id": 729701131,
  "agent_session_id": "WwYjWktIMiIGzAZeEayNrtyCUdYXxKv",
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "GhQRwEUV",
  "custom_data": {
    "ffinttuCrcWr": "+E*qsF>iz+Yo551y6TclW#G+{^=%",
    "KiYiChOQmKjr": 56,
    "rJWsASSMczTA": true
  },
  "created_on": "2003-09-16T14:29:05.429Z",
  "last_updated_on": "1987-02-24T13:29:23.610Z",
  "cuid": "agqTBqLmdRrIJNG"
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

**Example GET request path:**<br>`/cardholders/1831079394`

### <a name="response-cardholder"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
financial_institution_id | number (fk) | 
agent_session_id | string | 
type | string | 
first_name | string | 
last_name | string | 
email | string | 
meta_key | string | 
custom_data | object | 
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cuid | string | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- financial_institution_ids
- agent_session_id
- cuid
- type
- first_name
- last_name
- email
- meta_key
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create cardholder

```javascript
const cardholder = await session.createCardholder({
  "financial_institution_id": 729701131,
  "cuid": "agqTBqLmdRrIJNG",
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "GhQRwEUV",
  "custom_data": {
    "ffinttuCrcWr": "+E*qsF>iz+Yo551y6TclW#G+{^=%",
    "KiYiChOQmKjr": 56,
    "rJWsASSMczTA": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 729701131 },
	{ "cuid", "agqTBqLmdRrIJNG" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "GhQRwEUV" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 729701131 )
	.add("cuid", "agqTBqLmdRrIJNG" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "GhQRwEUV" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":729701131,\"cuid\":\"agqTBqLmdRrIJNG\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"GhQRwEUV\",\"custom_data\":{\"ffinttuCrcWr\":\"+E*qsF>iz+Yo551y6TclW#G+{^=%\",\"KiYiChOQmKjr\":56,\"rJWsASSMczTA\":true}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardholders/
```

### Path

POST /cardholders

### Description

Create a cardholder and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
financial_institution_id | number | no
cuid | string | yes
type | [string enum](#post-cardholder-1)* | no
first_name | string | no
last_name | string | no
email | string | no
meta_key | string | no
custom_data | object | no

See [cardholder response attributes](#response-cardholder).

#### <a name="post-cardholder-1"></a>string enum*
- ephemeral


## Update cardholder

```javascript
const cardholder = await session.updateCardholder({
  "financial_institution_id": 1055849678,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "QOqdFEDjwEsSPiCYOldWvGCEYRuD",
  "custom_data": {
    "vLqOsNKvEHCb": "F&4%t}YO.&6/P-__SGrLp)1@G@Q27_",
    "cMSOOoOhjeCA": 45,
    "oRPSvClMQHba": true
  },
  "id": "1"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1055849678 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "QOqdFEDjwEsSPiCYOldWvGCEYRuD" },
	{ "id", "1" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1055849678 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "QOqdFEDjwEsSPiCYOldWvGCEYRuD" )
	.add("id", "1" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1055849678,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"QOqdFEDjwEsSPiCYOldWvGCEYRuD\",\"custom_data\":{\"vLqOsNKvEHCb\":\"F&4%t}YO.&6/P-__SGrLp)1@G@Q27_\",\"cMSOOoOhjeCA\":45,\"oRPSvClMQHba\":true},\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardholders/1831079394
```

### Path

PUT /cardholders OR /cardholders/{id}

### Description

Update a cardholder and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
financial_institution_id | number |
type | [string enum](#post-cardholder-1)* |
first_name | string |
last_name | string |
email | string |
meta_key | string |
custom_data | object |

See [cardholder response parameters](#response-cardholder).


## Delete cardholder

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardholders/1831079394
```

```javascript
await session.deleteCardholder(1831079394);
```

```csharp
CardSavrResponse<Cardholder> cardholder = await http.DeleteCardholderAsync(1831079394);
```

```java
JsonValue cardholder = session.delete("/cardholders", 1831079394, null);
```

### Path

DELETE /cardholders/{id}

### Description

Delete a cardholder and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [cardholder response parameters](#response-cardholder).


# Users
User objects correspond to a single CardSavr user.
## Get user

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/1517012402
```

```javascript
const users = await session.getUsers(1517012402);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(1517012402);
```

```java
JsonValue users = session.get("/cardsavr_users", 1517012402, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1517012402,
  "financial_institution_id": 1514292556,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1976-05-18T01:10:54.652Z",
  "is_locked": false,
  "password_lifetime": 319,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "cardholder_agent",
  "custom_data": {
    "iSYehEpnhxdO": "{$#30SXP5<",
    "GkDvNxYSlREK": 83,
    "MxNugwHsObja": true
  },
  "next_rotation_on": "2017-06-21T17:17:14.045Z",
  "created_on": "1986-10-27T22:12:35.672Z",
  "last_updated_on": "1994-04-21T00:27:51.485Z",
  "username": "jsmith123"
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

**Example GET request path:**<br>`/cardsavr_users/1517012402`

### <a name="response-cardsavr_user"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
financial_institution_id | number (fk) | 
first_name | string | 
last_name | string | 
last_login_time | date | 
is_locked | boolean | 
password_lifetime | number | 
email | string | 
is_password_update_required | boolean | 
role | string | 
custom_data | object | 
next_rotation_on | date | 
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
  "financial_institution_id": 1514292556,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 319,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "cardholder_agent",
  "custom_data": {
    "iSYehEpnhxdO": "{$#30SXP5<",
    "GkDvNxYSlREK": 83,
    "MxNugwHsObja": true
  },
  "next_rotation_on": "2017-06-21T17:17:14.045Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1514292556 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 319 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "cardholder_agent" },
	{ "next_rotation_on", "2017-06-21T17:17:14.045Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1514292556 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 319 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "cardholder_agent" )
	.add("next_rotation_on", "2017-06-21T17:17:14.045Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1514292556,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":319,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"cardholder_agent\",\"custom_data\":{\"iSYehEpnhxdO\":\"{$#30SXP5<\",\"GkDvNxYSlREK\":83,\"MxNugwHsObja\":true},\"next_rotation_on\":\"2017-06-21T17:17:14.045Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
custom_data | object | no
next_rotation_on | date | no

See [user response attributes](#response-cardsavr_user).

#### <a name="post-cardsavr_user-1"></a>string enum*
- admin
- cardholder_agent
- customer_agent
- swch_agent


## Update user

```javascript
const user = await session.updateUser({
  "financial_institution_id": 1267776682,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 69,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "customer_agent",
  "custom_data": {
    "fenvwPAeYxXA": "atW3@%xp8fc<+9",
    "YsKfPSVgvJbO": 8,
    "RnGwLcGnKzac": true
  },
  "next_rotation_on": "2002-03-07T20:59:54.063Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "id": "1"
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1267776682 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 69 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "customer_agent" },
	{ "next_rotation_on", "2002-03-07T20:59:54.063Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "id", "1" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1267776682 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 69 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "customer_agent" )
	.add("next_rotation_on", "2002-03-07T20:59:54.063Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("id", "1" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1267776682,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":69,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"customer_agent\",\"custom_data\":{\"fenvwPAeYxXA\":\"atW3@%xp8fc<+9\",\"YsKfPSVgvJbO\":8,\"RnGwLcGnKzac\":true},\"next_rotation_on\":\"2002-03-07T20:59:54.063Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/1517012402
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
custom_data | object |
next_rotation_on | date |

See [user response parameters](#response-cardsavr_user).


## Delete user

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/1517012402
```

```javascript
await session.deleteUser(1517012402);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(1517012402);
```

```java
JsonValue user = session.delete("/cardsavr_users", 1517012402, null);
```

### Path

DELETE /cardsavr_users/{id}

### Description

Delete a user and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [user response parameters](#response-cardsavr_user).


# Financial Institutions
A CardSavr Financial Institution that can be associated with jobs and users.
## Get financial institution

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/1979168013
```

```javascript
const financialinstitutions = await session.getFinancialInstitutions(1979168013);
```

```csharp
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(1979168013);
```

```java
JsonValue financialinstitutions = session.get("/financial_institutions", 1979168013, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1979168013,
  "name": "IZCkvTVCikdlaxmYjJMAUcDPFzuFnSYHGsxJLdnuxObLalQxmPJQUYrLyATgiwB",
  "description": "HoOUJTlhZrcdjakxOExzppybIagyjWyd",
  "lookup_key": "orLYOcGXacWvwFilJLCitpntHOSRGWFxwosgUtoasJsRkpaPEQesaMZMUmQzivl",
  "alternate_lookup_key": "vubvvioWARKZONSSDAydDvpZFfGZWjkHjyxesMSbYdzcdJjFgQKtVyPWokTUTzp",
  "config": {
    "MxDBBBFEWMIL": "8Wz=Z4/xP",
    "dTwFYguJiUfB": 46,
    "sPAErycWpluG": true
  },
  "email_config": {
    "npkTZTQCQQIx": "M*vo203GP)dKJo$<C,Kq",
    "LOrpBCvwvMTh": 24,
    "ghAUCnxkZbgG": true
  },
  "created_on": "1973-10-02T07:00:38.099Z",
  "last_updated_on": "2001-06-01T04:29:02.366Z"
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

**Example GET request path:**<br>`/financial_institutions/1979168013`

### <a name="response-financial_institution"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
name | string | 
description | string | 
lookup_key | string | 
alternate_lookup_key | string | 
config | object | 
email_config | object | 
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
  "name": "IZCkvTVCikdlaxmYjJMAUcDPFzuFnSYHGsxJLdnuxObLalQxmPJQUYrLyATgiwB",
  "description": "HoOUJTlhZrcdjakxOExzppybIagyjWyd",
  "lookup_key": "orLYOcGXacWvwFilJLCitpntHOSRGWFxwosgUtoasJsRkpaPEQesaMZMUmQzivl",
  "alternate_lookup_key": "vubvvioWARKZONSSDAydDvpZFfGZWjkHjyxesMSbYdzcdJjFgQKtVyPWokTUTzp",
  "config": {
    "MxDBBBFEWMIL": "8Wz=Z4/xP",
    "dTwFYguJiUfB": 46,
    "sPAErycWpluG": true
  },
  "email_config": {
    "npkTZTQCQQIx": "M*vo203GP)dKJo$<C,Kq",
    "LOrpBCvwvMTh": 24,
    "ghAUCnxkZbgG": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "IZCkvTVCikdlaxmYjJMAUcDPFzuFnSYHGsxJLdnuxObLalQxmPJQUYrLyATgiwB" },
	{ "description", "HoOUJTlhZrcdjakxOExzppybIagyjWyd" },
	{ "lookup_key", "orLYOcGXacWvwFilJLCitpntHOSRGWFxwosgUtoasJsRkpaPEQesaMZMUmQzivl" },
	{ "alternate_lookup_key", "vubvvioWARKZONSSDAydDvpZFfGZWjkHjyxesMSbYdzcdJjFgQKtVyPWokTUTzp" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "IZCkvTVCikdlaxmYjJMAUcDPFzuFnSYHGsxJLdnuxObLalQxmPJQUYrLyATgiwB" )
	.add("description", "HoOUJTlhZrcdjakxOExzppybIagyjWyd" )
	.add("lookup_key", "orLYOcGXacWvwFilJLCitpntHOSRGWFxwosgUtoasJsRkpaPEQesaMZMUmQzivl" )
	.add("alternate_lookup_key", "vubvvioWARKZONSSDAydDvpZFfGZWjkHjyxesMSbYdzcdJjFgQKtVyPWokTUTzp" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"IZCkvTVCikdlaxmYjJMAUcDPFzuFnSYHGsxJLdnuxObLalQxmPJQUYrLyATgiwB\",\"description\":\"HoOUJTlhZrcdjakxOExzppybIagyjWyd\",\"lookup_key\":\"orLYOcGXacWvwFilJLCitpntHOSRGWFxwosgUtoasJsRkpaPEQesaMZMUmQzivl\",\"alternate_lookup_key\":\"vubvvioWARKZONSSDAydDvpZFfGZWjkHjyxesMSbYdzcdJjFgQKtVyPWokTUTzp\",\"config\":{\"MxDBBBFEWMIL\":\"8Wz=Z4/xP\",\"dTwFYguJiUfB\":46,\"sPAErycWpluG\":true},\"email_config\":{\"npkTZTQCQQIx\":\"M*vo203GP)dKJo$<C,Kq\",\"LOrpBCvwvMTh\":24,\"ghAUCnxkZbgG\":true}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
config | object | no
email_config | object | no

See [financial institution response attributes](#response-financial_institution).


## Update financial institution

```javascript
const financialinstitution = await session.updateFinancialInstitution({
  "name": "FQPJAeXIKsYIeSqIMQAwFTydokcZjwwHRArWgDSWGYfxQiAcyIocoQCyEclPAbb",
  "description": "OSYHpEDxO",
  "lookup_key": "aJoKBSqVnCZOpLbRWOtKGAbNYnodLHWgCfDUsFMQnilSGGRBEnbCMYvPeBIsEWm",
  "alternate_lookup_key": "RbUGupgXxhTDJlMuWSGTjHUWjkoloOESQLCYuoNycfjVymVlUzmRIdpvwSOWSbT",
  "config": {
    "BHcJwGTxoHvP": "2Em=@%7BYB*~4nV)Aw^~Ch{h0/gGS5",
    "dwBPJKVxmUBV": 50,
    "QdqsrbIuSXwl": false
  },
  "email_config": {
    "MDINEuyXkwyi": "q(",
    "FtkjaSgDmyhl": 57,
    "XoozxhfLUxhw": false
  },
  "id": "1"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "FQPJAeXIKsYIeSqIMQAwFTydokcZjwwHRArWgDSWGYfxQiAcyIocoQCyEclPAbb" },
	{ "description", "OSYHpEDxO" },
	{ "lookup_key", "aJoKBSqVnCZOpLbRWOtKGAbNYnodLHWgCfDUsFMQnilSGGRBEnbCMYvPeBIsEWm" },
	{ "alternate_lookup_key", "RbUGupgXxhTDJlMuWSGTjHUWjkoloOESQLCYuoNycfjVymVlUzmRIdpvwSOWSbT" },
	{ "id", "1" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "FQPJAeXIKsYIeSqIMQAwFTydokcZjwwHRArWgDSWGYfxQiAcyIocoQCyEclPAbb" )
	.add("description", "OSYHpEDxO" )
	.add("lookup_key", "aJoKBSqVnCZOpLbRWOtKGAbNYnodLHWgCfDUsFMQnilSGGRBEnbCMYvPeBIsEWm" )
	.add("alternate_lookup_key", "RbUGupgXxhTDJlMuWSGTjHUWjkoloOESQLCYuoNycfjVymVlUzmRIdpvwSOWSbT" )
	.add("id", "1" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"FQPJAeXIKsYIeSqIMQAwFTydokcZjwwHRArWgDSWGYfxQiAcyIocoQCyEclPAbb\",\"description\":\"OSYHpEDxO\",\"lookup_key\":\"aJoKBSqVnCZOpLbRWOtKGAbNYnodLHWgCfDUsFMQnilSGGRBEnbCMYvPeBIsEWm\",\"alternate_lookup_key\":\"RbUGupgXxhTDJlMuWSGTjHUWjkoloOESQLCYuoNycfjVymVlUzmRIdpvwSOWSbT\",\"config\":{\"BHcJwGTxoHvP\":\"2Em=@%7BYB*~4nV)Aw^~Ch{h0/gGS5\",\"dwBPJKVxmUBV\":50,\"QdqsrbIuSXwl\":false},\"email_config\":{\"MDINEuyXkwyi\":\"q(\",\"FtkjaSgDmyhl\":57,\"XoozxhfLUxhw\":false},\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/1979168013
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
config | object |
email_config | object |

See [financial institution response parameters](#response-financial_institution).


## Delete financial institution

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/1979168013
```

```javascript
await session.deleteFinancialInstitution(1979168013);
```

```csharp
CardSavrResponse<FinancialInstitution> financialinstitution = await http.DeleteFinancialInstitutionAsync(1979168013);
```

```java
JsonValue financialinstitution = session.delete("/financial_institutions", 1979168013, null);
```

### Path

DELETE /financial_institutions/{id}

### Description

Delete a financial institution and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [financial institution response parameters](#response-financial_institution).


# Integrators
An integrator object represents an integrator that implements CardSavr.
## Get integrator

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/1936654662
```

```javascript
const integrators = await session.getIntegrators(1936654662);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(1936654662);
```

```java
JsonValue integrators = session.get("/integrators", 1936654662, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1936654662,
  "name": "qhXQIxmheorJXBxjGcNaXQwVVUYyrpIUHNlyNxxURMntmOPMI",
  "integrator_type": "swch_internal",
  "description": "ZYYtbGhvfrvDLNjXjvks",
  "last_key": "8jrWU5W8GUoaFMVFrryeucj/mfSpn5GuZFxtM7zfsCk=",
  "current_key": "fRBNtlcqdfLbxhywB8V1fLyeBdWnUiaYL5B74mkXXrw=",
  "next_key": "Pv/eEko7o5pDJiehZnKlkljSzOQHQfHzoIN/4H1F55U=",
  "key_lifetime": 167,
  "next_rotation_on": "2003-03-30T23:21:05.239Z",
  "created_on": "1995-05-16T22:48:40.206Z",
  "last_updated_on": "1991-07-17T05:16:45.803Z"
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

**Example GET request path:**<br>`/integrators/1936654662`

### <a name="response-integrator"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | An integrator's unique identifier
name | string | An integrator's name
integrator_type | string | What type of integrator is this?
description | string | An integrator's description
last_key | string | 
current_key | string | 
next_key | string | 
key_lifetime | number | 
next_rotation_on | date | 
created_on | date | Date this integrator was created on
last_updated_on | date | Date this integrator was last updated on

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- names
- name
- integrator_type
- integrator_types_include / integrator_types_exclude
- next_rotation_on_min / next_rotation_on_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create integrator

```javascript
const integrator = await session.createIntegrator({
  "name": "qhXQIxmheorJXBxjGcNaXQwVVUYyrpIUHNlyNxxURMntmOPMI",
  "integrator_type": "swch_internal",
  "description": "ZYYtbGhvfrvDLNjXjvks",
  "last_key": "8jrWU5W8GUoaFMVFrryeucj/mfSpn5GuZFxtM7zfsCk=",
  "current_key": "fRBNtlcqdfLbxhywB8V1fLyeBdWnUiaYL5B74mkXXrw=",
  "next_key": "Pv/eEko7o5pDJiehZnKlkljSzOQHQfHzoIN/4H1F55U=",
  "key_lifetime": 167,
  "next_rotation_on": "2003-03-30T23:21:05.239Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "qhXQIxmheorJXBxjGcNaXQwVVUYyrpIUHNlyNxxURMntmOPMI" },
	{ "integrator_type", "swch_internal" },
	{ "description", "ZYYtbGhvfrvDLNjXjvks" },
	{ "last_key", "8jrWU5W8GUoaFMVFrryeucj/mfSpn5GuZFxtM7zfsCk=" },
	{ "current_key", "fRBNtlcqdfLbxhywB8V1fLyeBdWnUiaYL5B74mkXXrw=" },
	{ "next_key", "Pv/eEko7o5pDJiehZnKlkljSzOQHQfHzoIN/4H1F55U=" },
	{ "key_lifetime", 167 },
	{ "next_rotation_on", "2003-03-30T23:21:05.239Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "qhXQIxmheorJXBxjGcNaXQwVVUYyrpIUHNlyNxxURMntmOPMI" )
	.add("integrator_type", "swch_internal" )
	.add("description", "ZYYtbGhvfrvDLNjXjvks" )
	.add("last_key", "8jrWU5W8GUoaFMVFrryeucj/mfSpn5GuZFxtM7zfsCk=" )
	.add("current_key", "fRBNtlcqdfLbxhywB8V1fLyeBdWnUiaYL5B74mkXXrw=" )
	.add("next_key", "Pv/eEko7o5pDJiehZnKlkljSzOQHQfHzoIN/4H1F55U=" )
	.add("key_lifetime", 167 )
	.add("next_rotation_on", "2003-03-30T23:21:05.239Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"qhXQIxmheorJXBxjGcNaXQwVVUYyrpIUHNlyNxxURMntmOPMI\",\"integrator_type\":\"swch_internal\",\"description\":\"ZYYtbGhvfrvDLNjXjvks\",\"last_key\":\"8jrWU5W8GUoaFMVFrryeucj/mfSpn5GuZFxtM7zfsCk=\",\"current_key\":\"fRBNtlcqdfLbxhywB8V1fLyeBdWnUiaYL5B74mkXXrw=\",\"next_key\":\"Pv/eEko7o5pDJiehZnKlkljSzOQHQfHzoIN/4H1F55U=\",\"key_lifetime\":167,\"next_rotation_on\":\"2003-03-30T23:21:05.239Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
integrator_type | [string enum](#post-integrator-1)* | yes
description | string | no
last_key | string | no
current_key | string | no
next_key | string | no
key_lifetime | number | no
next_rotation_on | date | no

See [integrator response attributes](#response-integrator).

#### <a name="post-integrator-1"></a>string enum*
- application
- swch_internal
- cust_internal


## Update integrator

```javascript
const integrator = await session.updateIntegrator(1, {
  "name": "IvybnTgVORkguWDXDrEWeBMJRSJZLzlTQnbPesbvDhXXNDHzR",
  "integrator_type": "application",
  "description": "ixuYFzESKhSXmKFuKaWEyTIUjC",
  "last_key": "CeCWfe5ebglneLo9RHIQNCv6V5dlKoN7sg+A0ww3/sg=",
  "current_key": "ebWdgK9J4J4GeikNnT9v6RaK847BbmdYzl9YaQiRPNM=",
  "next_key": "T8S8ZsrQnIzdG5C9UbEyXyOT9fo+PeBfDMctj2Y5wAk=",
  "key_lifetime": 301,
  "next_rotation_on": "1992-08-13T16:54:50.455Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "IvybnTgVORkguWDXDrEWeBMJRSJZLzlTQnbPesbvDhXXNDHzR" },
	{ "integrator_type", "application" },
	{ "description", "ixuYFzESKhSXmKFuKaWEyTIUjC" },
	{ "last_key", "CeCWfe5ebglneLo9RHIQNCv6V5dlKoN7sg+A0ww3/sg=" },
	{ "current_key", "ebWdgK9J4J4GeikNnT9v6RaK847BbmdYzl9YaQiRPNM=" },
	{ "next_key", "T8S8ZsrQnIzdG5C9UbEyXyOT9fo+PeBfDMctj2Y5wAk=" },
	{ "key_lifetime", 301 },
	{ "next_rotation_on", "1992-08-13T16:54:50.455Z" },
	{ "id", "1" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "IvybnTgVORkguWDXDrEWeBMJRSJZLzlTQnbPesbvDhXXNDHzR" )
	.add("integrator_type", "application" )
	.add("description", "ixuYFzESKhSXmKFuKaWEyTIUjC" )
	.add("last_key", "CeCWfe5ebglneLo9RHIQNCv6V5dlKoN7sg+A0ww3/sg=" )
	.add("current_key", "ebWdgK9J4J4GeikNnT9v6RaK847BbmdYzl9YaQiRPNM=" )
	.add("next_key", "T8S8ZsrQnIzdG5C9UbEyXyOT9fo+PeBfDMctj2Y5wAk=" )
	.add("key_lifetime", 301 )
	.add("next_rotation_on", "1992-08-13T16:54:50.455Z" )
	.add("id", "1" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"IvybnTgVORkguWDXDrEWeBMJRSJZLzlTQnbPesbvDhXXNDHzR\",\"integrator_type\":\"application\",\"description\":\"ixuYFzESKhSXmKFuKaWEyTIUjC\",\"last_key\":\"CeCWfe5ebglneLo9RHIQNCv6V5dlKoN7sg+A0ww3/sg=\",\"current_key\":\"ebWdgK9J4J4GeikNnT9v6RaK847BbmdYzl9YaQiRPNM=\",\"next_key\":\"T8S8ZsrQnIzdG5C9UbEyXyOT9fo+PeBfDMctj2Y5wAk=\",\"key_lifetime\":301,\"next_rotation_on\":\"1992-08-13T16:54:50.455Z\",\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/1936654662
```

### Path

PUT /integrators OR /integrators/{id}

### Description

Update a integrator and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
name | string |
integrator_type | [string enum](#post-integrator-1)* |
description | string |
last_key | string |
current_key | string |
next_key | string |
key_lifetime | number |
next_rotation_on | date |

See [integrator response parameters](#response-integrator).


## Delete integrator

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/1936654662
```

```javascript
await session.deleteIntegrator(1936654662);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(1936654662);
```

```java
JsonValue integrator = session.delete("/integrators", 1936654662, null);
```

### Path

DELETE /integrators/{id}

### Description

Delete a integrator and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [integrator response parameters](#response-integrator).


# Merchant sites
Merchant site objects contain information and images related to CardSavr-supported merchant sites.
## Get merchant site

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/merchant_sites/1414679202
```

```javascript
const merchantsites = await session.getMerchantSites(1414679202);
```

```csharp
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(1414679202);
```

```java
JsonValue merchantsites = session.get("/merchant_sites", 1414679202, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1414679202,
  "name": "vwGY",
  "host": "mINxMjhycUkFoF",
  "images": [
    {
      "ddCdMBknUevY": "KoG@HTQs)oGpaio7M*^/7Ac)Zz5MnW>",
      "JvAwQDwJUMiZ": 90,
      "NXtMASAYPrOF": false
    },
    {
      "MoXJlvPuhfKa": "Q*vtzPFIktp#2/",
      "dUeWyaqTjbWF": 62,
      "ygfybxtJtKMv": true
    },
    {
      "ZKGOzCIekNLg": ")-kUNJwHCs=Tm2j8",
      "gvfJBypqOJzf": 74,
      "nFDcKIUHkWGd": false
    }
  ],
  "mfa": false,
  "tags": "EEJ",
  "proxy_order": [
    "QI!fES]w_~K/M$b7TnoI(7,<pE4)!!61",
    78,
    "Ao0qD%C^N"
  ],
  "quick_start": false,
  "login": {
    "gvChrJAPrxkm": "zfeYQ<A*c8OWfIe5R^HEYy,G/N2tpk",
    "BtxoQkyOdrrI": 63,
    "VhdbwgfsSlkb": true
  },
  "required_form_fields": [
    "f<J#TA<dUc]7",
    57,
    "(BAY~j@G[rrK]_sMaRQb"
  ],
  "login_page": "CjiIuDyjmbuBhFwVtbcQYjiYm",
  "credit_card_page": "PugAILj"
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

**Example GET request path:**<br>`/merchant_sites/1414679202`

### <a name="response-merchant_site"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
name | string | 
host | string | 
images | array | 
mfa | boolean | 
tags | string | 
proxy_order | array | 
quick_start | boolean | 
login | object | 
required_form_fields | array | 
login_page | string | 
credit_card_page | string | 

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
A notification record that defines how to take action on CardSavr events like jobs completing or sessions ending.
## Get notification

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/618389227
```

```javascript
const notifications = await session.getNotifications(618389227);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(618389227);
```

```java
JsonValue notifications = session.get("/notifications", 618389227, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 618389227,
  "name": "DAIVcNGLxnUTaaeFHYNTVClDLJdNUGzWVrbxDZmJMDXGsmgFVoNIdGTZjCMKXgK",
  "type": "webhook",
  "event": "merchant_site_updates_top",
  "config": {
    "YGamKhvUmrYT": ")#NwKlT9(SexQh/j,ax{IT",
    "sqkRBkMJgsNK": 5,
    "XBdNthNIIlhV": false
  },
  "html_template": "KlgQiGZJgI",
  "text_template": "wNKWGodivsgfXyteaqBxrNcn",
  "created_on": "1981-07-05T12:22:38.721Z",
  "last_updated_on": "2010-12-14T18:18:28.613Z",
  "financial_institution_id": 691099386
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

**Example GET request path:**<br>`/notifications/618389227`

### <a name="response-notification"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
name | string | 
type | string | 
event | string | 
config | object | 
html_template | string | 
text_template | string | 
created_on | date | Date this notification was created on
last_updated_on | date | Date this notification was last updated on
financial_institution_id | number (fk) | 

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
  "financial_institution_id": 691099386,
  "name": "DAIVcNGLxnUTaaeFHYNTVClDLJdNUGzWVrbxDZmJMDXGsmgFVoNIdGTZjCMKXgK",
  "type": "webhook",
  "event": "merchant_site_updates_top",
  "config": {
    "YGamKhvUmrYT": ")#NwKlT9(SexQh/j,ax{IT",
    "sqkRBkMJgsNK": 5,
    "XBdNthNIIlhV": false
  },
  "html_template": "KlgQiGZJgI",
  "text_template": "wNKWGodivsgfXyteaqBxrNcn"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 691099386 },
	{ "name", "DAIVcNGLxnUTaaeFHYNTVClDLJdNUGzWVrbxDZmJMDXGsmgFVoNIdGTZjCMKXgK" },
	{ "type", "webhook" },
	{ "event", "merchant_site_updates_top" },
	{ "html_template", "KlgQiGZJgI" },
	{ "text_template", "wNKWGodivsgfXyteaqBxrNcn" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 691099386 )
	.add("name", "DAIVcNGLxnUTaaeFHYNTVClDLJdNUGzWVrbxDZmJMDXGsmgFVoNIdGTZjCMKXgK" )
	.add("type", "webhook" )
	.add("event", "merchant_site_updates_top" )
	.add("html_template", "KlgQiGZJgI" )
	.add("text_template", "wNKWGodivsgfXyteaqBxrNcn" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":691099386,\"name\":\"DAIVcNGLxnUTaaeFHYNTVClDLJdNUGzWVrbxDZmJMDXGsmgFVoNIdGTZjCMKXgK\",\"type\":\"webhook\",\"event\":\"merchant_site_updates_top\",\"config\":{\"YGamKhvUmrYT\":\")#NwKlT9(SexQh/j,ax{IT\",\"sqkRBkMJgsNK\":5,\"XBdNthNIIlhV\":false},\"html_template\":\"KlgQiGZJgI\",\"text_template\":\"wNKWGodivsgfXyteaqBxrNcn\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
const notification = await session.updateNotification(1, {
  "name": "cigexwwwVtmnjxqwVQLoMCgkDAubfLKKLwRvqASqjZiJmnBhWkzvKGDTFZKEeis",
  "type": "webhook",
  "event": "webhook_error_summary",
  "config": {
    "XksUhGXTqJkA": "H3a+B@",
    "rUxtXUsbJnZC": 7,
    "gtYZCDAtqmEC": true
  },
  "html_template": "Yfdvnq",
  "text_template": "sKJqVOVvZIumgJRhvQwGydvkmrX"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "cigexwwwVtmnjxqwVQLoMCgkDAubfLKKLwRvqASqjZiJmnBhWkzvKGDTFZKEeis" },
	{ "type", "webhook" },
	{ "event", "webhook_error_summary" },
	{ "html_template", "Yfdvnq" },
	{ "text_template", "sKJqVOVvZIumgJRhvQwGydvkmrX" },
	{ "id", "1" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "cigexwwwVtmnjxqwVQLoMCgkDAubfLKKLwRvqASqjZiJmnBhWkzvKGDTFZKEeis" )
	.add("type", "webhook" )
	.add("event", "webhook_error_summary" )
	.add("html_template", "Yfdvnq" )
	.add("text_template", "sKJqVOVvZIumgJRhvQwGydvkmrX" )
	.add("id", "1" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"cigexwwwVtmnjxqwVQLoMCgkDAubfLKKLwRvqASqjZiJmnBhWkzvKGDTFZKEeis\",\"type\":\"webhook\",\"event\":\"webhook_error_summary\",\"config\":{\"XksUhGXTqJkA\":\"H3a+B@\",\"rUxtXUsbJnZC\":7,\"gtYZCDAtqmEC\":true},\"html_template\":\"Yfdvnq\",\"text_template\":\"sKJqVOVvZIumgJRhvQwGydvkmrX\",\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/618389227
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
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/618389227
```

```javascript
await session.deleteNotification(618389227);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(618389227);
```

```java
JsonValue notification = session.delete("/notifications", 618389227, null);
```

### Path

DELETE /notifications/{id}

### Description

Delete a notification and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [notification response parameters](#response-notification).


# Notification results
A notification result record that defines how to take action on CardSavr events like jobs completing or sessions ending.
## Get notification result

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notification_results/1961547417
```

```javascript
const notificationresults = await session.getNotificationResults(1961547417);
```

```csharp
CardSavrResponse<NotificationResults> notificationresults = await session.GetNotificationResultsAsync(1961547417);
```

```java
JsonValue notificationresults = session.get("/notification_results", 1961547417, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1961547417,
  "last_attempt_date": "2007-08-01T10:17:39.020Z",
  "fi_lookup_key": "uIOIHljylkZdGHKiuyGojVvSTBbIZAXQRqqeAVmWCmELLrYKQNAqNbriMFYTpbT",
  "cuid": "SuBDOYFkuNTKGpQQQwJc",
  "status": "success",
  "attempts": 1672463723,
  "notification_data": {
    "iaDBzKKWoQDT": "gx%UW,O^C!%A{,u@ToSSHgJ^hI_g",
    "pbwzaoffLAUE": 4,
    "mOuLUwgDnUsI": true
  },
  "created_on": "1981-01-16T13:24:42.891Z",
  "last_updated_on": "2013-08-29T00:49:00.377Z",
  "notification_id": 1060313744
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

**Example GET request path:**<br>`/notification_results/1961547417`

### <a name="response-notification_result"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
last_attempt_date | date | Date of last attempt to post this notification result
fi_lookup_key | string | 
cuid | string | 
status | string | 
attempts | number | 
notification_data | object | 
created_on | date | Date this notification result was created on
last_updated_on | date | Date this notification result was last updated on
notification_id | number (fk) | 

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
  "notification_id": 1060313744,
  "fi_lookup_key": "uIOIHljylkZdGHKiuyGojVvSTBbIZAXQRqqeAVmWCmELLrYKQNAqNbriMFYTpbT",
  "cuid": "SuBDOYFkuNTKGpQQQwJc",
  "status": "success",
  "attempts": 1672463723,
  "notification_data": {
    "iaDBzKKWoQDT": "gx%UW,O^C!%A{,u@ToSSHgJ^hI_g",
    "pbwzaoffLAUE": 4,
    "mOuLUwgDnUsI": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 1060313744 },
	{ "fi_lookup_key", "uIOIHljylkZdGHKiuyGojVvSTBbIZAXQRqqeAVmWCmELLrYKQNAqNbriMFYTpbT" },
	{ "cuid", "SuBDOYFkuNTKGpQQQwJc" },
	{ "status", "success" },
	{ "attempts", 1672463723 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 1060313744 )
	.add("fi_lookup_key", "uIOIHljylkZdGHKiuyGojVvSTBbIZAXQRqqeAVmWCmELLrYKQNAqNbriMFYTpbT" )
	.add("cuid", "SuBDOYFkuNTKGpQQQwJc" )
	.add("status", "success" )
	.add("attempts", 1672463723 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":1060313744,\"fi_lookup_key\":\"uIOIHljylkZdGHKiuyGojVvSTBbIZAXQRqqeAVmWCmELLrYKQNAqNbriMFYTpbT\",\"cuid\":\"SuBDOYFkuNTKGpQQQwJc\",\"status\":\"success\",\"attempts\":1672463723,\"notification_data\":{\"iaDBzKKWoQDT\":\"gx%UW,O^C!%A{,u@ToSSHgJ^hI_g\",\"pbwzaoffLAUE\":4,\"mOuLUwgDnUsI\":true}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
A place_card_on_single_site_job object
## Get single-site job

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1567962848
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(1567962848);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(1567962848);
```

```java
JsonValue singlesitejobs = session.get("/place_card_on_single_site_jobs", 1567962848, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1567962848,
  "card_id": 768340104,
  "card_placement_result_id": "ArzDpDClhVVBCYwIwrRcUhZx",
  "status": "MAX_LIMIT_OF_STORED_CARDS",
  "custom_data": {
    "XVGjlRbxDiIl": "4xNgC",
    "XBqYJnVpzUSN": 36,
    "QQLiIeyCYQaE": false
  },
  "failure_reason": "TYzLTEXobBmDOelYqrzTYfuoIY",
  "messaging_addresses": "y",
  "current_state": "pPNtxEYDXeWlvejVDGcrWCPriDduKOCZpNOJdnUuPmJLYHgTRcTZpjYQurfPGGQ",
  "notification_sent": true,
  "time_elapsed": 1358583570,
  "run_count": 1780102538,
  "job_ready_on": "1976-01-21T15:35:03.361Z",
  "started_on": "1975-06-06T16:23:32.269Z",
  "completed_on": "2005-01-20T16:21:13.257Z",
  "expiration_date": "2000-02-23T04:54:35.783Z",
  "created_on": "1989-09-21T03:19:52.332Z",
  "last_updated_on": "2012-02-16T16:55:09.138Z",
  "cardholder_id": 3239160,
  "account_id": 795149067,
  "type": "INTEGRATION_TEST"
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/1567962848`

### <a name="response-place_card_on_single_site_job"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
card_id | number (fk) | 
card_placement_result_id | string | 
status | string | 
custom_data | object | 
failure_reason | string | 
messaging_addresses | string | 
current_state | string | 
notification_sent | boolean | 
time_elapsed | number | 
run_count | number | 
job_ready_on | date | 
started_on | date | 
completed_on | date | 
expiration_date | date | 
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) | 
account_id | number (fk) | 
type | string | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- cardholder_ids
- card_ids
- account_ids
- card_placement_result_ids
- type
- status
- status_include / status_exclude
- current_state
- notification_sent
- time_elapsed_min / time_elapsed_max
- run_count_min / run_count_max
- job_ready_on_min / job_ready_on_max
- started_on_min / started_on_max
- completed_on_min / completed_on_max
- expiration_date_min / expiration_date_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create single-site job

```javascript
const singlesitejob = await session.createSingleSiteJob({
  "cardholder_id": 3239160,
  "card_id": 768340104,
  "account_id": 795149067,
  "type": "INTEGRATION_TEST",
  "status": "MAX_LIMIT_OF_STORED_CARDS",
  "custom_data": {
    "XVGjlRbxDiIl": "4xNgC",
    "XBqYJnVpzUSN": 36,
    "QQLiIeyCYQaE": false
  },
  "failure_reason": "TYzLTEXobBmDOelYqrzTYfuoIY",
  "current_state": "pPNtxEYDXeWlvejVDGcrWCPriDduKOCZpNOJdnUuPmJLYHgTRcTZpjYQurfPGGQ",
  "notification_sent": true,
  "time_elapsed": 1358583570,
  "run_count": 1780102538,
  "started_on": "1975-06-06T16:23:32.269Z",
  "completed_on": "2005-01-20T16:21:13.257Z",
  "expiration_date": "2000-02-23T04:54:35.783Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 3239160 },
	{ "card_id", 768340104 },
	{ "account_id", 795149067 },
	{ "type", "INTEGRATION_TEST" },
	{ "status", "MAX_LIMIT_OF_STORED_CARDS" },
	{ "failure_reason", "TYzLTEXobBmDOelYqrzTYfuoIY" },
	{ "current_state", "pPNtxEYDXeWlvejVDGcrWCPriDduKOCZpNOJdnUuPmJLYHgTRcTZpjYQurfPGGQ" },
	{ "notification_sent", true },
	{ "time_elapsed", 1358583570 },
	{ "run_count", 1780102538 },
	{ "started_on", "1975-06-06T16:23:32.269Z" },
	{ "completed_on", "2005-01-20T16:21:13.257Z" },
	{ "expiration_date", "2000-02-23T04:54:35.783Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 3239160 )
	.add("card_id", 768340104 )
	.add("account_id", 795149067 )
	.add("type", "INTEGRATION_TEST" )
	.add("status", "MAX_LIMIT_OF_STORED_CARDS" )
	.add("failure_reason", "TYzLTEXobBmDOelYqrzTYfuoIY" )
	.add("current_state", "pPNtxEYDXeWlvejVDGcrWCPriDduKOCZpNOJdnUuPmJLYHgTRcTZpjYQurfPGGQ" )
	.add("notification_sent", true )
	.add("time_elapsed", 1358583570 )
	.add("run_count", 1780102538 )
	.add("started_on", "1975-06-06T16:23:32.269Z" )
	.add("completed_on", "2005-01-20T16:21:13.257Z" )
	.add("expiration_date", "2000-02-23T04:54:35.783Z" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":3239160,\"card_id\":768340104,\"account_id\":795149067,\"type\":\"INTEGRATION_TEST\",\"status\":\"MAX_LIMIT_OF_STORED_CARDS\",\"custom_data\":{\"XVGjlRbxDiIl\":\"4xNgC\",\"XBqYJnVpzUSN\":36,\"QQLiIeyCYQaE\":false},\"failure_reason\":\"TYzLTEXobBmDOelYqrzTYfuoIY\",\"current_state\":\"pPNtxEYDXeWlvejVDGcrWCPriDduKOCZpNOJdnUuPmJLYHgTRcTZpjYQurfPGGQ\",\"notification_sent\":true,\"time_elapsed\":1358583570,\"run_count\":1780102538,\"started_on\":\"1975-06-06T16:23:32.269Z\",\"completed_on\":\"2005-01-20T16:21:13.257Z\",\"expiration_date\":\"2000-02-23T04:54:35.783Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
type | [string enum](#post-place_card_on_single_site_job-1)* | no
status | [string enum](#post-place_card_on_single_site_job-2)** | no
custom_data | object | no
failure_reason | string | no
current_state | string | no
notification_sent | boolean | no
time_elapsed | number | no
run_count | number | no
started_on | date | no
completed_on | date | no
expiration_date | date | no

See [single-site job response attributes](#response-place_card_on_single_site_job).

#### <a name="post-place_card_on_single_site_job-1"></a>string enum*
- CARD_PLACEMENT
- TURBO_MODE
- INTEGRATION_TEST
- API_TEST

#### <a name="post-place_card_on_single_site_job-2"></a>string enum**
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
- ACCOUNT_NOT_SUPPORTED
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
const singlesitejob = await session.updateSingleSiteJob({
  "card_id": 1593063560,
  "status": "TFA_CODE_RECEIVED",
  "custom_data": {
    "SvpyCqyKWMzy": "whi[^UqUoaVl)3JyD.R&eV_I+[Dx",
    "JWGAqyEqNUUW": 76,
    "qwEMwtpunjGl": true
  },
  "failure_reason": "BZfqLIoQVVPoqrem",
  "current_state": "NnvSBQUFJlAyQIASbtRjQuNwbdIajCrnMYntkpnPElGPRVUBOHAQrbskrswuDxy",
  "notification_sent": false,
  "time_elapsed": 1925485109,
  "run_count": 1137645647,
  "started_on": "1970-03-17T00:21:35.028Z",
  "completed_on": "2003-08-10T04:35:40.510Z",
  "expiration_date": "2009-02-21T02:28:16.359Z",
  "id": "1"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 1593063560 },
	{ "status", "TFA_CODE_RECEIVED" },
	{ "failure_reason", "BZfqLIoQVVPoqrem" },
	{ "current_state", "NnvSBQUFJlAyQIASbtRjQuNwbdIajCrnMYntkpnPElGPRVUBOHAQrbskrswuDxy" },
	{ "notification_sent", false },
	{ "time_elapsed", 1925485109 },
	{ "run_count", 1137645647 },
	{ "started_on", "1970-03-17T00:21:35.028Z" },
	{ "completed_on", "2003-08-10T04:35:40.510Z" },
	{ "expiration_date", "2009-02-21T02:28:16.359Z" },
	{ "id", "1" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 1593063560 )
	.add("status", "TFA_CODE_RECEIVED" )
	.add("failure_reason", "BZfqLIoQVVPoqrem" )
	.add("current_state", "NnvSBQUFJlAyQIASbtRjQuNwbdIajCrnMYntkpnPElGPRVUBOHAQrbskrswuDxy" )
	.add("notification_sent", false )
	.add("time_elapsed", 1925485109 )
	.add("run_count", 1137645647 )
	.add("started_on", "1970-03-17T00:21:35.028Z" )
	.add("completed_on", "2003-08-10T04:35:40.510Z" )
	.add("expiration_date", "2009-02-21T02:28:16.359Z" )
	.add("id", "1" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":1593063560,\"status\":\"TFA_CODE_RECEIVED\",\"custom_data\":{\"SvpyCqyKWMzy\":\"whi[^UqUoaVl)3JyD.R&eV_I+[Dx\",\"JWGAqyEqNUUW\":76,\"qwEMwtpunjGl\":true},\"failure_reason\":\"BZfqLIoQVVPoqrem\",\"current_state\":\"NnvSBQUFJlAyQIASbtRjQuNwbdIajCrnMYntkpnPElGPRVUBOHAQrbskrswuDxy\",\"notification_sent\":false,\"time_elapsed\":1925485109,\"run_count\":1137645647,\"started_on\":\"1970-03-17T00:21:35.028Z\",\"completed_on\":\"2003-08-10T04:35:40.510Z\",\"expiration_date\":\"2009-02-21T02:28:16.359Z\",\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1567962848
```

### Path

PUT /place_card_on_single_site_jobs OR /place_card_on_single_site_jobs/{id}

### Description

Update a single-site job and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
card_id | number |
status | [string enum](#post-place_card_on_single_site_job-2)** |
custom_data | object |
failure_reason | string |
current_state | string |
notification_sent | boolean |
time_elapsed | number |
run_count | number |
started_on | date |
completed_on | date |
expiration_date | date |

See [single-site job response parameters](#response-place_card_on_single_site_job).

<aside class="notice">Update calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete single-site job

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1567962848
```

```javascript
await session.deleteSingleSiteJob(1567962848);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(1567962848);
```

```java
JsonValue singlesitejob = session.delete("/place_card_on_single_site_jobs", 1567962848, null);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [single-site job response parameters](#response-place_card_on_single_site_job).

