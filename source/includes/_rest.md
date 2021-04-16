
# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1396911080
```

```javascript
const accounts = await session.getAccounts(1396911080);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(1396911080);
```

```java
JsonValue accounts = session.get("/cardsavr_accounts", 1396911080, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1396911080,
  "last_card_placed_id": 1685342613,
  "last_login": "1971-03-08T10:25:11.275Z",
  "last_password_update": "1985-12-28T04:22:30.834Z",
  "last_saved_card": "2020-01-23T22:56:44.407Z",
  "created_on": "2016-02-07T12:23:43.793Z",
  "last_updated_on": "2016-09-28T16:34:47.535Z",
  "cardholder_id": 1809823831,
  "merchant_site_id": 1188585392
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

**Example GET request path:**<br>`/cardsavr_accounts/1396911080`

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
  "cardholder_id": 1809823831,
  "merchant_site_id": 1188585392,
  "last_card_placed_id": 1685342613,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1809823831 },
	{ "merchant_site_id", 1188585392 },
	{ "last_card_placed_id", 1685342613 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1809823831 )
	.add("merchant_site_id", 1188585392 )
	.add("last_card_placed_id", 1685342613 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1809823831,\"merchant_site_id\":1188585392,\"last_card_placed_id\":1685342613,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X POST -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
last_card_placed_id | number | no
username | string | no
password | string | no

See [account response attributes](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username and password when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Update account

```javascript
const account = await session.updateAccount({
  "last_card_placed_id": 823616754,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "id": "1"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 823616754 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "id", "1" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 823616754 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("id", "1" )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":823616754,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1396911080
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
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1396911080
```

```javascript
await session.deleteAccount(1396911080);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(1396911080);
```

```java
JsonValue account = session.delete("/cardsavr_accounts", 1396911080, null);
```

### Path

DELETE /cardsavr_accounts/{id}

### Description

Delete a account and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [account response parameters](#response-cardsavr_account).


# Addresses
Address objects contain billing address information for a particular user.
## Get address

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1417469372
```

```javascript
const addresses = await session.getAddresses(1417469372);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(1417469372);
```

```java
JsonValue addresses = session.get("/cardsavr_addresses", 1417469372, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1417469372,
  "address1": "AbqJOjrphlYjiuaYDdKsPmpcZloyqTfNAfrtzbbIlyRwyvVbLOkENqRcZzYtjFVSZrkPAePDJdvCuIrQlDzwoIJUWITMvVwzyuF",
  "address2": "MHzHVNnaguyEmIpqadXIFXuTwBQOwEkPhOksktuuPfcPUHrQAmEowYNqVsbRmNPfHOHmfxbWlLuogJhZYaqEBSOiarSAbdEEEXz",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "MXuKpzpNyCtDCugZQN",
  "created_on": "2000-09-05T10:23:00.481Z",
  "last_updated_on": "2000-05-02T06:50:29.672Z",
  "cardholder_id": 735897442
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

**Example GET request path:**<br>`/cardsavr_addresses/1417469372`

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
  "cardholder_id": 735897442,
  "address1": "AbqJOjrphlYjiuaYDdKsPmpcZloyqTfNAfrtzbbIlyRwyvVbLOkENqRcZzYtjFVSZrkPAePDJdvCuIrQlDzwoIJUWITMvVwzyuF",
  "address2": "MHzHVNnaguyEmIpqadXIFXuTwBQOwEkPhOksktuuPfcPUHrQAmEowYNqVsbRmNPfHOHmfxbWlLuogJhZYaqEBSOiarSAbdEEEXz",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "MXuKpzpNyCtDCugZQN"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 735897442 },
	{ "address1", "AbqJOjrphlYjiuaYDdKsPmpcZloyqTfNAfrtzbbIlyRwyvVbLOkENqRcZzYtjFVSZrkPAePDJdvCuIrQlDzwoIJUWITMvVwzyuF" },
	{ "address2", "MHzHVNnaguyEmIpqadXIFXuTwBQOwEkPhOksktuuPfcPUHrQAmEowYNqVsbRmNPfHOHmfxbWlLuogJhZYaqEBSOiarSAbdEEEXz" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "phone_number", "MXuKpzpNyCtDCugZQN" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 735897442 )
	.add("address1", "AbqJOjrphlYjiuaYDdKsPmpcZloyqTfNAfrtzbbIlyRwyvVbLOkENqRcZzYtjFVSZrkPAePDJdvCuIrQlDzwoIJUWITMvVwzyuF" )
	.add("address2", "MHzHVNnaguyEmIpqadXIFXuTwBQOwEkPhOksktuuPfcPUHrQAmEowYNqVsbRmNPfHOHmfxbWlLuogJhZYaqEBSOiarSAbdEEEXz" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", false )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("phone_number", "MXuKpzpNyCtDCugZQN" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":735897442,\"address1\":\"AbqJOjrphlYjiuaYDdKsPmpcZloyqTfNAfrtzbbIlyRwyvVbLOkENqRcZzYtjFVSZrkPAePDJdvCuIrQlDzwoIJUWITMvVwzyuF\",\"address2\":\"MHzHVNnaguyEmIpqadXIFXuTwBQOwEkPhOksktuuPfcPUHrQAmEowYNqVsbRmNPfHOHmfxbWlLuogJhZYaqEBSOiarSAbdEEEXz\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"phone_number\":\"MXuKpzpNyCtDCugZQN\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
const address = await session.updateAddress({
  "address1": "edmSFfiGYQfedyEAlnxmuFcqvFjCTGXcOYAIxXwNJxamyxeaHENNDInbttqivYIXldfsCwOkuKOVXqrwensXjhMJJodIweyRgAc",
  "address2": "LRypCjZDOtGntXUoDUyMESkkajSMPmoBhKMepTSxjaAoNhPjmzzfClrqtRHdXyLdEXiQpjILzhoWIhtTgGnpiygMdAjqDWXAZYv",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "XTwwgdvZJgFfBE",
  "id": "1"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "edmSFfiGYQfedyEAlnxmuFcqvFjCTGXcOYAIxXwNJxamyxeaHENNDInbttqivYIXldfsCwOkuKOVXqrwensXjhMJJodIweyRgAc" },
	{ "address2", "LRypCjZDOtGntXUoDUyMESkkajSMPmoBhKMepTSxjaAoNhPjmzzfClrqtRHdXyLdEXiQpjILzhoWIhtTgGnpiygMdAjqDWXAZYv" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "phone_number", "XTwwgdvZJgFfBE" },
	{ "id", "1" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "edmSFfiGYQfedyEAlnxmuFcqvFjCTGXcOYAIxXwNJxamyxeaHENNDInbttqivYIXldfsCwOkuKOVXqrwensXjhMJJodIweyRgAc" )
	.add("address2", "LRypCjZDOtGntXUoDUyMESkkajSMPmoBhKMepTSxjaAoNhPjmzzfClrqtRHdXyLdEXiQpjILzhoWIhtTgGnpiygMdAjqDWXAZYv" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", false )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("phone_number", "XTwwgdvZJgFfBE" )
	.add("id", "1" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"edmSFfiGYQfedyEAlnxmuFcqvFjCTGXcOYAIxXwNJxamyxeaHENNDInbttqivYIXldfsCwOkuKOVXqrwensXjhMJJodIweyRgAc\",\"address2\":\"LRypCjZDOtGntXUoDUyMESkkajSMPmoBhKMepTSxjaAoNhPjmzzfClrqtRHdXyLdEXiQpjILzhoWIhtTgGnpiygMdAjqDWXAZYv\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"phone_number\":\"XTwwgdvZJgFfBE\",\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1417469372
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1417469372
```

```javascript
await session.deleteAddress(1417469372);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(1417469372);
```

```java
JsonValue address = session.delete("/cardsavr_addresses", 1417469372, null);
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/589781932
```

```javascript
const bins = await session.getBins(589781932);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(589781932);
```

```java
JsonValue bins = session.get("/cardsavr_bins", 589781932, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 589781932,
  "financial_institution_id": 1637080527,
  "custom_data": {
    "PzOIAHRxrtlL": "~",
    "BOGqRxpCbAlz": 93,
    "RQFyIkvwIraK": false
  },
  "created_on": "1973-12-06T05:12:31.427Z",
  "last_updated_on": "1976-12-05T03:03:35.708Z",
  "bank_identification_number": "41315847"
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

**Example GET request path:**<br>`/cardsavr_bins/589781932`

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
  "financial_institution_id": 1637080527,
  "bank_identification_number": "41315847",
  "custom_data": {
    "PzOIAHRxrtlL": "~",
    "BOGqRxpCbAlz": 93,
    "RQFyIkvwIraK": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1637080527 },
	{ "bank_identification_number", "41315847" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1637080527 )
	.add("bank_identification_number", "41315847" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1637080527,\"bank_identification_number\":\"41315847\",\"custom_data\":{\"PzOIAHRxrtlL\":\"~\",\"BOGqRxpCbAlz\":93,\"RQFyIkvwIraK\":false}}"
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
  "financial_institution_id": 633498482,
  "custom_data": {
    "cADrUIpcRfrY": "j]hajb",
    "oAPRfIlVYhMa": 98,
    "VENlMYTgXlai": false
  },
  "id": "1"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 633498482 },
	{ "id", "1" }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 633498482 )
	.add("id", "1" )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":633498482,\"custom_data\":{\"cADrUIpcRfrY\":\"j]hajb\",\"oAPRfIlVYhMa\":98,\"VENlMYTgXlai\":false},\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/589781932
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/589781932
```

```javascript
await session.deleteBin(589781932);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(589781932);
```

```java
JsonValue bin = session.delete("/cardsavr_bins", 589781932, null);
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/182972531
```

```javascript
const cards = await session.getCards(182972531);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(182972531);
```

```java
JsonValue cards = session.get("/cardsavr_cards", 182972531, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 182972531,
  "address_id": 1141519658,
  "bin_id": 1050920062,
  "name_on_card": "Joe C Smith",
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "created_on": "1999-06-23T17:45:18.407Z",
  "last_updated_on": "1999-03-15T06:59:42.076Z",
  "expiration_month": 12,
  "expiration_year": 24,
  "cardholder_id": 1179397314,
  "par": "fEwdmDRAFeWANOwPaoLqaNtOiRGhr"
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

**Example GET request path:**<br>`/cardsavr_cards/182972531`

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
  "cardholder_id": 1179397314,
  "address_id": 1141519658,
  "bin_id": 1050920062,
  "par": "fEwdmDRAFeWANOwPaoLqaNtOiRGhr",
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
	{ "cardholder_id", 1179397314 },
	{ "address_id", 1141519658 },
	{ "bin_id", 1050920062 },
	{ "par", "fEwdmDRAFeWANOwPaoLqaNtOiRGhr" },
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
	.add("cardholder_id", 1179397314 )
	.add("address_id", 1141519658 )
	.add("bin_id", 1050920062 )
	.add("par", "fEwdmDRAFeWANOwPaoLqaNtOiRGhr" )
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
curl -d "{\"cardholder_id\":1179397314,\"address_id\":1141519658,\"bin_id\":1050920062,\"par\":\"fEwdmDRAFeWANOwPaoLqaNtOiRGhr\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\",\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
-X POST -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
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
const card = await session.updateCard({
  "address_id": 1957280579,
  "bin_id": 619743663,
  "name_on_card": "Joe C Smith",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "id": "1"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address_id", 1957280579 },
	{ "bin_id", 619743663 },
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
	.add("address_id", 1957280579 )
	.add("bin_id", 619743663 )
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
curl -d "{\"address_id\":1957280579,\"bin_id\":619743663,\"name_on_card\":\"Joe C Smith\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\",\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/182972531
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/182972531
```

```javascript
await session.deleteCard(182972531);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(182972531);
```

```java
JsonValue card = session.delete("/cardsavr_cards", 182972531, null);
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
https://api.INSTANCE.cardsavr.io/cardholders/1834555247
```

```javascript
const cardholders = await session.getCardholders(1834555247);
```

```csharp
CardSavrResponse<Cardholders> cardholders = await session.GetCardholdersAsync(1834555247);
```

```java
JsonValue cardholders = session.get("/cardholders", 1834555247, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1834555247,
  "financial_institution_id": 1957712361,
  "agent_session_id": "MUJrEbU",
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "hINBAKP",
  "custom_data": {
    "GzbkgLsTcUMx": "5niN",
    "kyNuIQZRMmDP": 2,
    "ChpIjblYXiME": false
  },
  "created_on": "1997-03-13T11:56:36.974Z",
  "last_updated_on": "2001-03-18T17:34:53.339Z",
  "cuid": "xfAuuMtvJTFaofflJN"
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

**Example GET request path:**<br>`/cardholders/1834555247`

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
  "financial_institution_id": 1957712361,
  "cuid": "xfAuuMtvJTFaofflJN",
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "hINBAKP",
  "custom_data": {
    "GzbkgLsTcUMx": "5niN",
    "kyNuIQZRMmDP": 2,
    "ChpIjblYXiME": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1957712361 },
	{ "cuid", "xfAuuMtvJTFaofflJN" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "hINBAKP" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1957712361 )
	.add("cuid", "xfAuuMtvJTFaofflJN" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "hINBAKP" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1957712361,\"cuid\":\"xfAuuMtvJTFaofflJN\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"hINBAKP\",\"custom_data\":{\"GzbkgLsTcUMx\":\"5niN\",\"kyNuIQZRMmDP\":2,\"ChpIjblYXiME\":false}}"
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
  "financial_institution_id": 637421332,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "jIXlyWwEYiIVtA",
  "custom_data": {
    "DGYYmUTdxXqv": "Kxe9-pHr3L/",
    "nzEEJCgkUyvq": 49,
    "cVNIOzspzthI": true
  },
  "id": "1"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 637421332 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "jIXlyWwEYiIVtA" },
	{ "id", "1" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 637421332 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "jIXlyWwEYiIVtA" )
	.add("id", "1" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":637421332,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"jIXlyWwEYiIVtA\",\"custom_data\":{\"DGYYmUTdxXqv\":\"Kxe9-pHr3L/\",\"nzEEJCgkUyvq\":49,\"cVNIOzspzthI\":true},\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardholders/1834555247
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
https://api.INSTANCE.cardsavr.io/cardholders/1834555247
```

```javascript
await session.deleteCardholder(1834555247);
```

```csharp
CardSavrResponse<Cardholder> cardholder = await http.DeleteCardholderAsync(1834555247);
```

```java
JsonValue cardholder = session.delete("/cardholders", 1834555247, null);
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/101796096
```

```javascript
const users = await session.getUsers(101796096);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(101796096);
```

```java
JsonValue users = session.get("/cardsavr_users", 101796096, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 101796096,
  "financial_institution_id": 1887786998,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "2016-03-29T20:18:53.501Z",
  "is_locked": false,
  "password_lifetime": 196,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_agent",
  "custom_data": {
    "CxRqTIkADxhp": "XnI,E[Nqc-*1I0%@{+F",
    "jdBExRhrvxVH": 99,
    "BEMQxXxOOovR": false
  },
  "next_rotation_on": "2018-10-26T15:08:28.795Z",
  "created_on": "2001-06-01T09:16:35.928Z",
  "last_updated_on": "1970-10-26T00:06:22.268Z",
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

**Example GET request path:**<br>`/cardsavr_users/101796096`

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
  "financial_institution_id": 1887786998,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 196,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_agent",
  "custom_data": {
    "CxRqTIkADxhp": "XnI,E[Nqc-*1I0%@{+F",
    "jdBExRhrvxVH": 99,
    "BEMQxXxOOovR": false
  },
  "next_rotation_on": "2018-10-26T15:08:28.795Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1887786998 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 196 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "swch_agent" },
	{ "next_rotation_on", "2018-10-26T15:08:28.795Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1887786998 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 196 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "swch_agent" )
	.add("next_rotation_on", "2018-10-26T15:08:28.795Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1887786998,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":196,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"swch_agent\",\"custom_data\":{\"CxRqTIkADxhp\":\"XnI,E[Nqc-*1I0%@{+F\",\"jdBExRhrvxVH\":99,\"BEMQxXxOOovR\":false},\"next_rotation_on\":\"2018-10-26T15:08:28.795Z\"}"
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
  "financial_institution_id": 1997298528,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 343,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_agent",
  "custom_data": {
    "PbyGuUHDgIxw": "5hi9d5.g0nY_@i)>C8!))b1l(MG*/w_{",
    "IMauNOhJkBhM": 34,
    "zrNajCAAuUby": true
  },
  "next_rotation_on": "1976-09-16T11:49:24.611Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "id": "1"
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1997298528 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 343 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "cardholder_agent" },
	{ "next_rotation_on", "1976-09-16T11:49:24.611Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "id", "1" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1997298528 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 343 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "cardholder_agent" )
	.add("next_rotation_on", "1976-09-16T11:49:24.611Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("id", "1" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1997298528,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":343,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"cardholder_agent\",\"custom_data\":{\"PbyGuUHDgIxw\":\"5hi9d5.g0nY_@i)>C8!))b1l(MG*/w_{\",\"IMauNOhJkBhM\":34,\"zrNajCAAuUby\":true},\"next_rotation_on\":\"1976-09-16T11:49:24.611Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/101796096
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/101796096
```

```javascript
await session.deleteUser(101796096);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(101796096);
```

```java
JsonValue user = session.delete("/cardsavr_users", 101796096, null);
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
https://api.INSTANCE.cardsavr.io/financial_institutions/450069908
```

```javascript
const financialinstitutions = await session.getFinancialInstitutions(450069908);
```

```csharp
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(450069908);
```

```java
JsonValue financialinstitutions = session.get("/financial_institutions", 450069908, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 450069908,
  "name": "DDrXlgUBwxHOotughyRdzXpwJzgGQKkWXwJhXXXzmfDaQWNioFHLNCXwxQnudLa",
  "description": "yHGltNSTuCkTnurgrIhS",
  "lookup_key": "sZdtMYjeHImXLeCOJLaAYOtvfJUBQdJKzdPlXLtcnXDVVTZpzdSsvqDRknNsaoG",
  "alternate_lookup_key": "ywKwkIQgJVAKIWgaTOolXnrGMwhZVMkHlwImyVUZXKTbOGDJJnJhTbGOqFVJrYe",
  "config": {
    "hBRaBkkvXOEH": "w7^{37Gd",
    "RhywaTAZsXGt": 88,
    "rsVbEBsJSfIv": false
  },
  "email_config": {
    "HqPmBLZBEHDg": "w%l>>HarPO$rM&eSGpyt#",
    "ytMieTYVKUER": 94,
    "mJrTvveizcRC": false
  },
  "created_on": "2011-10-17T23:48:02.832Z",
  "last_updated_on": "1982-09-30T17:18:42.146Z"
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

**Example GET request path:**<br>`/financial_institutions/450069908`

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
  "name": "DDrXlgUBwxHOotughyRdzXpwJzgGQKkWXwJhXXXzmfDaQWNioFHLNCXwxQnudLa",
  "description": "yHGltNSTuCkTnurgrIhS",
  "lookup_key": "sZdtMYjeHImXLeCOJLaAYOtvfJUBQdJKzdPlXLtcnXDVVTZpzdSsvqDRknNsaoG",
  "alternate_lookup_key": "ywKwkIQgJVAKIWgaTOolXnrGMwhZVMkHlwImyVUZXKTbOGDJJnJhTbGOqFVJrYe",
  "config": {
    "hBRaBkkvXOEH": "w7^{37Gd",
    "RhywaTAZsXGt": 88,
    "rsVbEBsJSfIv": false
  },
  "email_config": {
    "HqPmBLZBEHDg": "w%l>>HarPO$rM&eSGpyt#",
    "ytMieTYVKUER": 94,
    "mJrTvveizcRC": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "DDrXlgUBwxHOotughyRdzXpwJzgGQKkWXwJhXXXzmfDaQWNioFHLNCXwxQnudLa" },
	{ "description", "yHGltNSTuCkTnurgrIhS" },
	{ "lookup_key", "sZdtMYjeHImXLeCOJLaAYOtvfJUBQdJKzdPlXLtcnXDVVTZpzdSsvqDRknNsaoG" },
	{ "alternate_lookup_key", "ywKwkIQgJVAKIWgaTOolXnrGMwhZVMkHlwImyVUZXKTbOGDJJnJhTbGOqFVJrYe" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "DDrXlgUBwxHOotughyRdzXpwJzgGQKkWXwJhXXXzmfDaQWNioFHLNCXwxQnudLa" )
	.add("description", "yHGltNSTuCkTnurgrIhS" )
	.add("lookup_key", "sZdtMYjeHImXLeCOJLaAYOtvfJUBQdJKzdPlXLtcnXDVVTZpzdSsvqDRknNsaoG" )
	.add("alternate_lookup_key", "ywKwkIQgJVAKIWgaTOolXnrGMwhZVMkHlwImyVUZXKTbOGDJJnJhTbGOqFVJrYe" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"DDrXlgUBwxHOotughyRdzXpwJzgGQKkWXwJhXXXzmfDaQWNioFHLNCXwxQnudLa\",\"description\":\"yHGltNSTuCkTnurgrIhS\",\"lookup_key\":\"sZdtMYjeHImXLeCOJLaAYOtvfJUBQdJKzdPlXLtcnXDVVTZpzdSsvqDRknNsaoG\",\"alternate_lookup_key\":\"ywKwkIQgJVAKIWgaTOolXnrGMwhZVMkHlwImyVUZXKTbOGDJJnJhTbGOqFVJrYe\",\"config\":{\"hBRaBkkvXOEH\":\"w7^{37Gd\",\"RhywaTAZsXGt\":88,\"rsVbEBsJSfIv\":false},\"email_config\":{\"HqPmBLZBEHDg\":\"w%l>>HarPO$rM&eSGpyt#\",\"ytMieTYVKUER\":94,\"mJrTvveizcRC\":false}}"
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
  "name": "CrhgJDopSIgINNDRWbDWwvYAhsYVLauBDpVshWPKtuRQqhjKajJdMpDvfgXOgYe",
  "description": "lhrVjLCcSpubglSgCdAuAcYsZiVRZfFz",
  "lookup_key": "cguALztMxIqrdZOgFdjannAbFOgrPNEKUbpkrcqUHCxOMhexgcgvaNuFFFstIGt",
  "alternate_lookup_key": "eVccCEYEGHkgtybKGyKrIEhNooQvwQRGPjZIjoVQZStBhwHpHaUMOrEqHqldPRU",
  "config": {
    "pkUAZuAbgovT": "4PflVUvrj!q5A!^TU8Q",
    "qrdKpzJXEXrO": 35,
    "sjYdBevnfRvs": true
  },
  "email_config": {
    "ueziKfDuHupm": "jmKE!i-KiJ@#",
    "FsuFgkfdxsNZ": 80,
    "CLkuzWlTMWTF": true
  },
  "id": "1"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "CrhgJDopSIgINNDRWbDWwvYAhsYVLauBDpVshWPKtuRQqhjKajJdMpDvfgXOgYe" },
	{ "description", "lhrVjLCcSpubglSgCdAuAcYsZiVRZfFz" },
	{ "lookup_key", "cguALztMxIqrdZOgFdjannAbFOgrPNEKUbpkrcqUHCxOMhexgcgvaNuFFFstIGt" },
	{ "alternate_lookup_key", "eVccCEYEGHkgtybKGyKrIEhNooQvwQRGPjZIjoVQZStBhwHpHaUMOrEqHqldPRU" },
	{ "id", "1" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "CrhgJDopSIgINNDRWbDWwvYAhsYVLauBDpVshWPKtuRQqhjKajJdMpDvfgXOgYe" )
	.add("description", "lhrVjLCcSpubglSgCdAuAcYsZiVRZfFz" )
	.add("lookup_key", "cguALztMxIqrdZOgFdjannAbFOgrPNEKUbpkrcqUHCxOMhexgcgvaNuFFFstIGt" )
	.add("alternate_lookup_key", "eVccCEYEGHkgtybKGyKrIEhNooQvwQRGPjZIjoVQZStBhwHpHaUMOrEqHqldPRU" )
	.add("id", "1" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"CrhgJDopSIgINNDRWbDWwvYAhsYVLauBDpVshWPKtuRQqhjKajJdMpDvfgXOgYe\",\"description\":\"lhrVjLCcSpubglSgCdAuAcYsZiVRZfFz\",\"lookup_key\":\"cguALztMxIqrdZOgFdjannAbFOgrPNEKUbpkrcqUHCxOMhexgcgvaNuFFFstIGt\",\"alternate_lookup_key\":\"eVccCEYEGHkgtybKGyKrIEhNooQvwQRGPjZIjoVQZStBhwHpHaUMOrEqHqldPRU\",\"config\":{\"pkUAZuAbgovT\":\"4PflVUvrj!q5A!^TU8Q\",\"qrdKpzJXEXrO\":35,\"sjYdBevnfRvs\":true},\"email_config\":{\"ueziKfDuHupm\":\"jmKE!i-KiJ@#\",\"FsuFgkfdxsNZ\":80,\"CLkuzWlTMWTF\":true},\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/450069908
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
https://api.INSTANCE.cardsavr.io/financial_institutions/450069908
```

```javascript
await session.deleteFinancialInstitution(450069908);
```

```csharp
CardSavrResponse<FinancialInstitution> financialinstitution = await http.DeleteFinancialInstitutionAsync(450069908);
```

```java
JsonValue financialinstitution = session.delete("/financial_institutions", 450069908, null);
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
https://api.INSTANCE.cardsavr.io/integrators/2055073532
```

```javascript
const integrators = await session.getIntegrators(2055073532);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(2055073532);
```

```java
JsonValue integrators = session.get("/integrators", 2055073532, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2055073532,
  "name": "fvIHFKLaRwRuGTWWnAiujBJLIymcfeQUZLljNdrraBhvNocXw",
  "integrator_type": "swch_internal",
  "description": "iptrBXKZIG",
  "last_key": "6ZdkbvgvBWPbO4FZvjbvcsw3/v/8e9re6eDhrHp8Z+Q=",
  "current_key": "mvGZEVYhGi3dMcWMNXFB6d1nIrLa8eMovmstMaKeAfI=",
  "next_key": "rd++sPXLCudRjI0tUHtcSAntzzzwIa2fpjng6in32W8=",
  "key_lifetime": 39,
  "next_rotation_on": "2017-12-29T03:24:55.086Z",
  "created_on": "1976-03-28T19:36:33.943Z",
  "last_updated_on": "1981-08-18T02:21:12.068Z"
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

**Example GET request path:**<br>`/integrators/2055073532`

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
  "name": "fvIHFKLaRwRuGTWWnAiujBJLIymcfeQUZLljNdrraBhvNocXw",
  "integrator_type": "swch_internal",
  "description": "iptrBXKZIG",
  "last_key": "6ZdkbvgvBWPbO4FZvjbvcsw3/v/8e9re6eDhrHp8Z+Q=",
  "current_key": "mvGZEVYhGi3dMcWMNXFB6d1nIrLa8eMovmstMaKeAfI=",
  "next_key": "rd++sPXLCudRjI0tUHtcSAntzzzwIa2fpjng6in32W8=",
  "key_lifetime": 39,
  "next_rotation_on": "2017-12-29T03:24:55.086Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "fvIHFKLaRwRuGTWWnAiujBJLIymcfeQUZLljNdrraBhvNocXw" },
	{ "integrator_type", "swch_internal" },
	{ "description", "iptrBXKZIG" },
	{ "last_key", "6ZdkbvgvBWPbO4FZvjbvcsw3/v/8e9re6eDhrHp8Z+Q=" },
	{ "current_key", "mvGZEVYhGi3dMcWMNXFB6d1nIrLa8eMovmstMaKeAfI=" },
	{ "next_key", "rd++sPXLCudRjI0tUHtcSAntzzzwIa2fpjng6in32W8=" },
	{ "key_lifetime", 39 },
	{ "next_rotation_on", "2017-12-29T03:24:55.086Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "fvIHFKLaRwRuGTWWnAiujBJLIymcfeQUZLljNdrraBhvNocXw" )
	.add("integrator_type", "swch_internal" )
	.add("description", "iptrBXKZIG" )
	.add("last_key", "6ZdkbvgvBWPbO4FZvjbvcsw3/v/8e9re6eDhrHp8Z+Q=" )
	.add("current_key", "mvGZEVYhGi3dMcWMNXFB6d1nIrLa8eMovmstMaKeAfI=" )
	.add("next_key", "rd++sPXLCudRjI0tUHtcSAntzzzwIa2fpjng6in32W8=" )
	.add("key_lifetime", 39 )
	.add("next_rotation_on", "2017-12-29T03:24:55.086Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"fvIHFKLaRwRuGTWWnAiujBJLIymcfeQUZLljNdrraBhvNocXw\",\"integrator_type\":\"swch_internal\",\"description\":\"iptrBXKZIG\",\"last_key\":\"6ZdkbvgvBWPbO4FZvjbvcsw3/v/8e9re6eDhrHp8Z+Q=\",\"current_key\":\"mvGZEVYhGi3dMcWMNXFB6d1nIrLa8eMovmstMaKeAfI=\",\"next_key\":\"rd++sPXLCudRjI0tUHtcSAntzzzwIa2fpjng6in32W8=\",\"key_lifetime\":39,\"next_rotation_on\":\"2017-12-29T03:24:55.086Z\"}"
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
const integrator = await session.updateIntegrator({
  "name": "yUBRxuyqzgSayMBnllZPzzNlVAKJlNQCKLWPhipjqoopJGmYz",
  "integrator_type": "swch_internal",
  "description": "gTmWVxzUZIYnqJqhvxwO",
  "last_key": "11L5AM0VR4WeGkCSCFkWzHBBUt5+sWV6CmqZYPdPHtY=",
  "current_key": "+emomt6LY2W1vhvW9VtOUNyiwDUzcptw7BfMA7koTYk=",
  "next_key": "XVW8fJUWuUwawCgsJTL6X7JTV9aneEZ8y7Q6GIew0O8=",
  "key_lifetime": 167,
  "next_rotation_on": "1994-06-19T04:18:56.271Z",
  "id": "1"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "yUBRxuyqzgSayMBnllZPzzNlVAKJlNQCKLWPhipjqoopJGmYz" },
	{ "integrator_type", "swch_internal" },
	{ "description", "gTmWVxzUZIYnqJqhvxwO" },
	{ "last_key", "11L5AM0VR4WeGkCSCFkWzHBBUt5+sWV6CmqZYPdPHtY=" },
	{ "current_key", "+emomt6LY2W1vhvW9VtOUNyiwDUzcptw7BfMA7koTYk=" },
	{ "next_key", "XVW8fJUWuUwawCgsJTL6X7JTV9aneEZ8y7Q6GIew0O8=" },
	{ "key_lifetime", 167 },
	{ "next_rotation_on", "1994-06-19T04:18:56.271Z" },
	{ "id", "1" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "yUBRxuyqzgSayMBnllZPzzNlVAKJlNQCKLWPhipjqoopJGmYz" )
	.add("integrator_type", "swch_internal" )
	.add("description", "gTmWVxzUZIYnqJqhvxwO" )
	.add("last_key", "11L5AM0VR4WeGkCSCFkWzHBBUt5+sWV6CmqZYPdPHtY=" )
	.add("current_key", "+emomt6LY2W1vhvW9VtOUNyiwDUzcptw7BfMA7koTYk=" )
	.add("next_key", "XVW8fJUWuUwawCgsJTL6X7JTV9aneEZ8y7Q6GIew0O8=" )
	.add("key_lifetime", 167 )
	.add("next_rotation_on", "1994-06-19T04:18:56.271Z" )
	.add("id", "1" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"yUBRxuyqzgSayMBnllZPzzNlVAKJlNQCKLWPhipjqoopJGmYz\",\"integrator_type\":\"swch_internal\",\"description\":\"gTmWVxzUZIYnqJqhvxwO\",\"last_key\":\"11L5AM0VR4WeGkCSCFkWzHBBUt5+sWV6CmqZYPdPHtY=\",\"current_key\":\"+emomt6LY2W1vhvW9VtOUNyiwDUzcptw7BfMA7koTYk=\",\"next_key\":\"XVW8fJUWuUwawCgsJTL6X7JTV9aneEZ8y7Q6GIew0O8=\",\"key_lifetime\":167,\"next_rotation_on\":\"1994-06-19T04:18:56.271Z\",\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/2055073532
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
https://api.INSTANCE.cardsavr.io/integrators/2055073532
```

```javascript
await session.deleteIntegrator(2055073532);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(2055073532);
```

```java
JsonValue integrator = session.delete("/integrators", 2055073532, null);
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
https://api.INSTANCE.cardsavr.io/merchant_sites/1057188696
```

```javascript
const merchantsites = await session.getMerchantSites(1057188696);
```

```csharp
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(1057188696);
```

```java
JsonValue merchantsites = session.get("/merchant_sites", 1057188696, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1057188696,
  "name": "rQNUFXEOREb",
  "host": "sxnHUDi",
  "images": [
    {
      "zwuGCqvQNEBZ": "H_gSy5X@>S2y^JJHbTRGB/fh",
      "vHmdsnToscVe": 8,
      "xXChWQELCPAz": true
    },
    {
      "RBgLCuzNEKov": "*Bg(}Cu=p>!f$}4~ZM<OF_xZ.!rK",
      "JvbNRfodYmWX": 50,
      "bwMNnyqVePnO": true
    },
    {
      "yHhdMgPucTjg": "YV",
      "kBMleEPArwXR": 10,
      "FAfudEjKnomK": true
    }
  ],
  "mfa": false,
  "tags": "L",
  "quick_start": true,
  "login": {
    "ckDtydJmnIpM": "]zHftFJ~X7>OQ1BR",
    "MiDMhwdIHDXo": 0,
    "EHdzcEdjOuso": true
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

**Example GET request path:**<br>`/merchant_sites/1057188696`

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
https://api.INSTANCE.cardsavr.io/notifications/38530108
```

```javascript
const notifications = await session.getNotifications(38530108);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(38530108);
```

```java
JsonValue notifications = session.get("/notifications", 38530108, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 38530108,
  "name": "NnNLbpogpMXjTiIkXTeFnrgLxCeLVcfwGdwxVAiMovtsMVxvelewabxnQlQviyF",
  "type": "email",
  "event": "session_complete",
  "config": {
    "DIHbBJkiesxQ": "#n3,Jox9j*=A0OzgSR",
    "WyCQgCbyMvVj": 39,
    "gbYBtcDsUbkH": true
  },
  "html_template": "xLoTzDk",
  "text_template": "cDXqalYeeHysNfISdrviziF",
  "created_on": "2003-01-04T05:32:10.913Z",
  "last_updated_on": "1991-08-18T01:01:20.087Z",
  "financial_institution_id": 434397638
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

**Example GET request path:**<br>`/notifications/38530108`

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
- event
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create notification

```javascript
const notification = await session.createNotification({
  "financial_institution_id": 434397638,
  "name": "NnNLbpogpMXjTiIkXTeFnrgLxCeLVcfwGdwxVAiMovtsMVxvelewabxnQlQviyF",
  "type": "email",
  "event": "session_complete",
  "config": {
    "DIHbBJkiesxQ": "#n3,Jox9j*=A0OzgSR",
    "WyCQgCbyMvVj": 39,
    "gbYBtcDsUbkH": true
  },
  "html_template": "xLoTzDk",
  "text_template": "cDXqalYeeHysNfISdrviziF"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 434397638 },
	{ "name", "NnNLbpogpMXjTiIkXTeFnrgLxCeLVcfwGdwxVAiMovtsMVxvelewabxnQlQviyF" },
	{ "type", "email" },
	{ "event", "session_complete" },
	{ "html_template", "xLoTzDk" },
	{ "text_template", "cDXqalYeeHysNfISdrviziF" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 434397638 )
	.add("name", "NnNLbpogpMXjTiIkXTeFnrgLxCeLVcfwGdwxVAiMovtsMVxvelewabxnQlQviyF" )
	.add("type", "email" )
	.add("event", "session_complete" )
	.add("html_template", "xLoTzDk" )
	.add("text_template", "cDXqalYeeHysNfISdrviziF" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":434397638,\"name\":\"NnNLbpogpMXjTiIkXTeFnrgLxCeLVcfwGdwxVAiMovtsMVxvelewabxnQlQviyF\",\"type\":\"email\",\"event\":\"session_complete\",\"config\":{\"DIHbBJkiesxQ\":\"#n3,Jox9j*=A0OzgSR\",\"WyCQgCbyMvVj\":39,\"gbYBtcDsUbkH\":true},\"html_template\":\"xLoTzDk\",\"text_template\":\"cDXqalYeeHysNfISdrviziF\"}"
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


## Update notification

```javascript
const notification = await session.updateNotification({
  "name": "HehCmsQNkNmGlWhMvWXNWxkMbHhkbelEsnTFTvjNOzzHFfzfmbpGdIQignEVSCN",
  "type": "email",
  "event": "webhook_error_summary",
  "config": {
    "rCcUtBNlRfJJ": "/%WiWil$&}",
    "BtHwzQaPacAZ": 44,
    "hKLIdqHOXBYU": true
  },
  "html_template": "BRgiudjdoxzdQtOvdrFNLHT",
  "text_template": "xUpYws",
  "id": "1"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "HehCmsQNkNmGlWhMvWXNWxkMbHhkbelEsnTFTvjNOzzHFfzfmbpGdIQignEVSCN" },
	{ "type", "email" },
	{ "event", "webhook_error_summary" },
	{ "html_template", "BRgiudjdoxzdQtOvdrFNLHT" },
	{ "text_template", "xUpYws" },
	{ "id", "1" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "HehCmsQNkNmGlWhMvWXNWxkMbHhkbelEsnTFTvjNOzzHFfzfmbpGdIQignEVSCN" )
	.add("type", "email" )
	.add("event", "webhook_error_summary" )
	.add("html_template", "BRgiudjdoxzdQtOvdrFNLHT" )
	.add("text_template", "xUpYws" )
	.add("id", "1" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"HehCmsQNkNmGlWhMvWXNWxkMbHhkbelEsnTFTvjNOzzHFfzfmbpGdIQignEVSCN\",\"type\":\"email\",\"event\":\"webhook_error_summary\",\"config\":{\"rCcUtBNlRfJJ\":\"/%WiWil$&}\",\"BtHwzQaPacAZ\":44,\"hKLIdqHOXBYU\":true},\"html_template\":\"BRgiudjdoxzdQtOvdrFNLHT\",\"text_template\":\"xUpYws\",\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/38530108
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
https://api.INSTANCE.cardsavr.io/notifications/38530108
```

```javascript
await session.deleteNotification(38530108);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(38530108);
```

```java
JsonValue notification = session.delete("/notifications", 38530108, null);
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
https://api.INSTANCE.cardsavr.io/notification_results/1531634943
```

```javascript
const notificationresults = await session.getNotificationResults(1531634943);
```

```csharp
CardSavrResponse<NotificationResults> notificationresults = await session.GetNotificationResultsAsync(1531634943);
```

```java
JsonValue notificationresults = session.get("/notification_results", 1531634943, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1531634943,
  "last_attempt_date": "1997-03-18T22:40:46.226Z",
  "fi_lookup_key": "qIxllucNNxryGuPzUvXbLewLWiLIvfVsoDDCAKWYwpbWYIiwaDHBaQbzzgUFtPQ",
  "cuid": "pntNDqTGCUtFSdj",
  "status": "failure",
  "attempts": 1778469782,
  "notification_data": {
    "UbOFUUsbLJXF": "&UJqS)&I1ypa$5",
    "YHVIJGzTRifC": 29,
    "beaOTDQDUCFE": true
  },
  "created_on": "1992-10-29T10:47:46.840Z",
  "last_updated_on": "1975-05-23T00:14:41.206Z",
  "notification_id": 1800838945
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

**Example GET request path:**<br>`/notification_results/1531634943`

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
  "notification_id": 1800838945,
  "fi_lookup_key": "qIxllucNNxryGuPzUvXbLewLWiLIvfVsoDDCAKWYwpbWYIiwaDHBaQbzzgUFtPQ",
  "cuid": "pntNDqTGCUtFSdj",
  "status": "failure",
  "attempts": 1778469782,
  "notification_data": {
    "UbOFUUsbLJXF": "&UJqS)&I1ypa$5",
    "YHVIJGzTRifC": 29,
    "beaOTDQDUCFE": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 1800838945 },
	{ "fi_lookup_key", "qIxllucNNxryGuPzUvXbLewLWiLIvfVsoDDCAKWYwpbWYIiwaDHBaQbzzgUFtPQ" },
	{ "cuid", "pntNDqTGCUtFSdj" },
	{ "status", "failure" },
	{ "attempts", 1778469782 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 1800838945 )
	.add("fi_lookup_key", "qIxllucNNxryGuPzUvXbLewLWiLIvfVsoDDCAKWYwpbWYIiwaDHBaQbzzgUFtPQ" )
	.add("cuid", "pntNDqTGCUtFSdj" )
	.add("status", "failure" )
	.add("attempts", 1778469782 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":1800838945,\"fi_lookup_key\":\"qIxllucNNxryGuPzUvXbLewLWiLIvfVsoDDCAKWYwpbWYIiwaDHBaQbzzgUFtPQ\",\"cuid\":\"pntNDqTGCUtFSdj\",\"status\":\"failure\",\"attempts\":1778469782,\"notification_data\":{\"UbOFUUsbLJXF\":\"&UJqS)&I1ypa$5\",\"YHVIJGzTRifC\":29,\"beaOTDQDUCFE\":true}}"
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


## Update notification result

```javascript
const notificationresult = await session.updateNotificationResult({
  "fi_lookup_key": "CeOFQwvNkFbXgEpgDMpjrRDAkDMIBZaPoGMlVIKzHFNdPKumfUOstCTffkgHRET",
  "cuid": "VanxdNlcmbubyBrzOOgva",
  "status": "failure",
  "attempts": 1204580799,
  "notification_data": {
    "PWnaTKVLOOjf": "zh=ZV^A<-FhrnW",
    "aJyQQldKtDBc": 8,
    "axoUWgDbijkr": true
  },
  "id": "1"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "fi_lookup_key", "CeOFQwvNkFbXgEpgDMpjrRDAkDMIBZaPoGMlVIKzHFNdPKumfUOstCTffkgHRET" },
	{ "cuid", "VanxdNlcmbubyBrzOOgva" },
	{ "status", "failure" },
	{ "attempts", 1204580799 },
	{ "id", "1" }
};

CardSavrResponse<NotificationResult> notificationresult = await http.UpdateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("fi_lookup_key", "CeOFQwvNkFbXgEpgDMpjrRDAkDMIBZaPoGMlVIKzHFNdPKumfUOstCTffkgHRET" )
	.add("cuid", "VanxdNlcmbubyBrzOOgva" )
	.add("status", "failure" )
	.add("attempts", 1204580799 )
	.add("id", "1" )
	.build();
JsonValue notificationresult = session.put("/notification_results", body, null, null);
```

```shell
curl -d "{\"fi_lookup_key\":\"CeOFQwvNkFbXgEpgDMpjrRDAkDMIBZaPoGMlVIKzHFNdPKumfUOstCTffkgHRET\",\"cuid\":\"VanxdNlcmbubyBrzOOgva\",\"status\":\"failure\",\"attempts\":1204580799,\"notification_data\":{\"PWnaTKVLOOjf\":\"zh=ZV^A<-FhrnW\",\"aJyQQldKtDBc\":8,\"axoUWgDbijkr\":true},\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notification_results/1531634943
```

### Path

PUT /notification_results OR /notification_results/{id}

### Description

Update a notification result and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
fi_lookup_key | string |
cuid | string |
status | [string enum](#post-notification_result-1)* |
attempts | number |
notification_data | object |

See [notification result response parameters](#response-notification_result).


## Delete notification result

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notification_results/1531634943
```

```javascript
await session.deleteNotificationResult(1531634943);
```

```csharp
CardSavrResponse<NotificationResult> notificationresult = await http.DeleteNotificationResultAsync(1531634943);
```

```java
JsonValue notificationresult = session.delete("/notification_results", 1531634943, null);
```

### Path

DELETE /notification_results/{id}

### Description

Delete a notification result and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [notification result response parameters](#response-notification_result).


# Single-site jobs
A place_card_on_single_site_job object
## Get single-site job

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1531167200
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(1531167200);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(1531167200);
```

```java
JsonValue singlesitejobs = session.get("/place_card_on_single_site_jobs", 1531167200, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1531167200,
  "card_id": 1297599480,
  "card_placement_result_id": "tzxYXMsnQwBIXdqWcgP",
  "status": "BILLED_THROUGH_DISNEY_PLUS",
  "custom_data": {
    "SYNtjaImGsbz": "(*pHd6AX",
    "OvbrIGVIYvvD": 68,
    "lTtygWZsOIbl": false
  },
  "failure_reason": "EuVxqG",
  "messaging_addresses": "lHVOWPmdizZuIADFGxUPwtFCUSCYWO",
  "current_state": "GxhmLDFExRKBcfDCiVnXbIcCIyDTBXliqZYfsLXJbpWyiisBpGMyXzwnWIfYWXU",
  "notification_sent": true,
  "time_elapsed": 2067677545,
  "run_count": 904160363,
  "job_ready_on": "1985-03-12T17:50:09.197Z",
  "started_on": "1974-07-20T10:05:31.589Z",
  "completed_on": "1992-06-30T01:29:38.535Z",
  "expiration_date": "1972-08-21T01:56:14.841Z",
  "created_on": "1978-12-11T06:37:18.919Z",
  "last_updated_on": "2004-05-02T06:53:58.260Z",
  "cardholder_id": 974030370,
  "account_id": 1542097756,
  "type": "CARD_PLACEMENT"
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/1531167200`

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
  "cardholder_id": 974030370,
  "card_id": 1297599480,
  "account_id": 1542097756,
  "type": "CARD_PLACEMENT",
  "status": "BILLED_THROUGH_DISNEY_PLUS",
  "custom_data": {
    "SYNtjaImGsbz": "(*pHd6AX",
    "OvbrIGVIYvvD": 68,
    "lTtygWZsOIbl": false
  },
  "failure_reason": "EuVxqG",
  "current_state": "GxhmLDFExRKBcfDCiVnXbIcCIyDTBXliqZYfsLXJbpWyiisBpGMyXzwnWIfYWXU",
  "notification_sent": true,
  "time_elapsed": 2067677545,
  "run_count": 904160363,
  "started_on": "1974-07-20T10:05:31.589Z",
  "completed_on": "1992-06-30T01:29:38.535Z",
  "expiration_date": "1972-08-21T01:56:14.841Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 974030370 },
	{ "card_id", 1297599480 },
	{ "account_id", 1542097756 },
	{ "type", "CARD_PLACEMENT" },
	{ "status", "BILLED_THROUGH_DISNEY_PLUS" },
	{ "failure_reason", "EuVxqG" },
	{ "current_state", "GxhmLDFExRKBcfDCiVnXbIcCIyDTBXliqZYfsLXJbpWyiisBpGMyXzwnWIfYWXU" },
	{ "notification_sent", true },
	{ "time_elapsed", 2067677545 },
	{ "run_count", 904160363 },
	{ "started_on", "1974-07-20T10:05:31.589Z" },
	{ "completed_on", "1992-06-30T01:29:38.535Z" },
	{ "expiration_date", "1972-08-21T01:56:14.841Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 974030370 )
	.add("card_id", 1297599480 )
	.add("account_id", 1542097756 )
	.add("type", "CARD_PLACEMENT" )
	.add("status", "BILLED_THROUGH_DISNEY_PLUS" )
	.add("failure_reason", "EuVxqG" )
	.add("current_state", "GxhmLDFExRKBcfDCiVnXbIcCIyDTBXliqZYfsLXJbpWyiisBpGMyXzwnWIfYWXU" )
	.add("notification_sent", true )
	.add("time_elapsed", 2067677545 )
	.add("run_count", 904160363 )
	.add("started_on", "1974-07-20T10:05:31.589Z" )
	.add("completed_on", "1992-06-30T01:29:38.535Z" )
	.add("expiration_date", "1972-08-21T01:56:14.841Z" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":974030370,\"card_id\":1297599480,\"account_id\":1542097756,\"type\":\"CARD_PLACEMENT\",\"status\":\"BILLED_THROUGH_DISNEY_PLUS\",\"custom_data\":{\"SYNtjaImGsbz\":\"(*pHd6AX\",\"OvbrIGVIYvvD\":68,\"lTtygWZsOIbl\":false},\"failure_reason\":\"EuVxqG\",\"current_state\":\"GxhmLDFExRKBcfDCiVnXbIcCIyDTBXliqZYfsLXJbpWyiisBpGMyXzwnWIfYWXU\",\"notification_sent\":true,\"time_elapsed\":2067677545,\"run_count\":904160363,\"started_on\":\"1974-07-20T10:05:31.589Z\",\"completed_on\":\"1992-06-30T01:29:38.535Z\",\"expiration_date\":\"1972-08-21T01:56:14.841Z\"}"
-X POST -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
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
- INTEGRATION_TEST
- API_TEST

#### <a name="post-place_card_on_single_site_job-2"></a>string enum**
- INITIATED
- REQUESTED
- IN_PROGRESS
- AUTH
- LOGIN_SUBMITTED
- PENDING_CREDS
- PENDING_NEWCREDS
- PENDING_CARD
- LOGIN_RESUBMITTED
- PENDING_TFA
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
- PREPAID_ACCOUNT
- INACTIVE_ACCOUNT
- INVALID_CARD
- PASSWORD_RESET_REQUIRED
- BILLED_THROUGH_GOOGLE_PLAY
- BILLED_THROUGH_DISNEY_PLUS
- BUNDLED_SUBSCRIPTION
- FREE_ACCOUNT
- ACCOUNT_LOCKED
- DUPLICATE_CARD
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
  "card_id": 253423468,
  "status": "PASSWORD_RESET_REQUIRED",
  "custom_data": {
    "dtQcpeueDlnM": "gP9<,HH0uM-{bAdE=,dH>H",
    "ogDXVWWqwZNY": 21,
    "DuDXjPmgFbfB": false
  },
  "failure_reason": "WupXyFTAfvLE",
  "current_state": "XwdKarFpLhyJbxAElRZUICNyezrCppVPGWkQMCyJGOGtfPzBtVgOspIAhcvwsCb",
  "notification_sent": false,
  "time_elapsed": 23495911,
  "run_count": 152840528,
  "started_on": "1993-06-01T06:08:12.120Z",
  "completed_on": "1992-12-29T23:14:05.340Z",
  "expiration_date": "1974-12-03T00:50:07.366Z",
  "id": "1"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 253423468 },
	{ "status", "PASSWORD_RESET_REQUIRED" },
	{ "failure_reason", "WupXyFTAfvLE" },
	{ "current_state", "XwdKarFpLhyJbxAElRZUICNyezrCppVPGWkQMCyJGOGtfPzBtVgOspIAhcvwsCb" },
	{ "notification_sent", false },
	{ "time_elapsed", 23495911 },
	{ "run_count", 152840528 },
	{ "started_on", "1993-06-01T06:08:12.120Z" },
	{ "completed_on", "1992-12-29T23:14:05.340Z" },
	{ "expiration_date", "1974-12-03T00:50:07.366Z" },
	{ "id", "1" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 253423468 )
	.add("status", "PASSWORD_RESET_REQUIRED" )
	.add("failure_reason", "WupXyFTAfvLE" )
	.add("current_state", "XwdKarFpLhyJbxAElRZUICNyezrCppVPGWkQMCyJGOGtfPzBtVgOspIAhcvwsCb" )
	.add("notification_sent", false )
	.add("time_elapsed", 23495911 )
	.add("run_count", 152840528 )
	.add("started_on", "1993-06-01T06:08:12.120Z" )
	.add("completed_on", "1992-12-29T23:14:05.340Z" )
	.add("expiration_date", "1974-12-03T00:50:07.366Z" )
	.add("id", "1" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":253423468,\"status\":\"PASSWORD_RESET_REQUIRED\",\"custom_data\":{\"dtQcpeueDlnM\":\"gP9<,HH0uM-{bAdE=,dH>H\",\"ogDXVWWqwZNY\":21,\"DuDXjPmgFbfB\":false},\"failure_reason\":\"WupXyFTAfvLE\",\"current_state\":\"XwdKarFpLhyJbxAElRZUICNyezrCppVPGWkQMCyJGOGtfPzBtVgOspIAhcvwsCb\",\"notification_sent\":false,\"time_elapsed\":23495911,\"run_count\":152840528,\"started_on\":\"1993-06-01T06:08:12.120Z\",\"completed_on\":\"1992-12-29T23:14:05.340Z\",\"expiration_date\":\"1974-12-03T00:50:07.366Z\",\"id\":\"1\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1531167200
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1531167200
```

```javascript
await session.deleteSingleSiteJob(1531167200);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(1531167200);
```

```java
JsonValue singlesitejob = session.delete("/place_card_on_single_site_jobs", 1531167200, null);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [single-site job response parameters](#response-place_card_on_single_site_job).

