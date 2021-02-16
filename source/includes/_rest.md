
# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/364616943
```

```javascript
const accounts = await session.getAccounts(364616943);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(364616943);
```

```java
JsonValue accounts = session.get("/cardsavr_accounts", 364616943, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 364616943,
  "last_card_placed_id": 603201103,
  "last_login": "1996-10-05T21:44:41.281Z",
  "last_password_update": "2016-08-29T19:11:12.358Z",
  "last_saved_card": "1998-03-06T04:14:09.336Z",
  "created_on": "1999-10-18T14:46:44.034Z",
  "last_updated_on": "1974-01-06T07:35:31.501Z",
  "cardholder_id": 130300740,
  "merchant_site_id": 131815713
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

**Example GET request path:**<br>`/cardsavr_accounts/364616943`

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
  "cardholder_id": 130300740,
  "merchant_site_id": 131815713,
  "last_card_placed_id": 603201103,
  "username": "jsmith123",
  "username_hash": "tgzKRPwJbTxaZRLjxlLQQrZNPJmBshfFAUXuVScEIaMNbIGNbglQVHdNuiV",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 130300740 },
	{ "merchant_site_id", 131815713 },
	{ "last_card_placed_id", 603201103 },
	{ "username", "jsmith123" },
	{ "username_hash", "tgzKRPwJbTxaZRLjxlLQQrZNPJmBshfFAUXuVScEIaMNbIGNbglQVHdNuiV" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 130300740 )
	.add("merchant_site_id", 131815713 )
	.add("last_card_placed_id", 603201103 )
	.add("username", "jsmith123" )
	.add("username_hash", "tgzKRPwJbTxaZRLjxlLQQrZNPJmBshfFAUXuVScEIaMNbIGNbglQVHdNuiV" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":130300740,\"merchant_site_id\":131815713,\"last_card_placed_id\":603201103,\"username\":\"jsmith123\",\"username_hash\":\"tgzKRPwJbTxaZRLjxlLQQrZNPJmBshfFAUXuVScEIaMNbIGNbglQVHdNuiV\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X POST -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
  "last_card_placed_id": 844094962,
  "username": "jsmith123",
  "username_hash": "hoohjiZfUvnlwmlARKwBGNEQhPZZXTuliaqMWPekfXKTEYkYVpKsUhbTGNX",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "id", 1 },
	{ "last_card_placed_id", 844094962 },
	{ "username", "jsmith123" },
	{ "username_hash", "hoohjiZfUvnlwmlARKwBGNEQhPZZXTuliaqMWPekfXKTEYkYVpKsUhbTGNX" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("id", 1)
	.add("last_card_placed_id", 844094962 )
	.add("username", "jsmith123" )
	.add("username_hash", "hoohjiZfUvnlwmlARKwBGNEQhPZZXTuliaqMWPekfXKTEYkYVpKsUhbTGNX" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":844094962,\"username\":\"jsmith123\",\"username_hash\":\"hoohjiZfUvnlwmlARKwBGNEQhPZZXTuliaqMWPekfXKTEYkYVpKsUhbTGNX\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/364616943
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
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/364616943
```

```javascript
await session.deleteAccount(364616943);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(364616943);
```

```java
JsonValue account = session.delete("/cardsavr_accounts", 364616943, null, null);
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
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1582374804
```

```javascript
const addresses = await session.getAddresses(1582374804);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(1582374804);
```

```java
JsonValue addresses = session.get("/cardsavr_addresses", 1582374804, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1582374804,
  "address1": "XoOnOkqYFIAVtrxOkGuftHQRJIcKPFCHELjEtjlXBbBloNKHKnbTlQGwVXJoKyHbXEzTolHZXFHhkebxWDSBLOSZIahwGozYvjI",
  "address2": "uVcJMyxIIRISneOzesKnhVOpIdsEtybEKYvdASgbbQrJPeagjupYLcvlfvbeFzShzKqPhKbJHUkLkJMNpsNZgAdIcTCDWljbdRA",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "bRVceGtNdFd",
  "created_on": "1985-07-30T04:39:31.352Z",
  "last_updated_on": "1977-11-24T12:04:07.989Z",
  "cardholder_id": 565138889
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

**Example GET request path:**<br>`/cardsavr_addresses/1582374804`

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
  "cardholder_id": 565138889,
  "address1": "XoOnOkqYFIAVtrxOkGuftHQRJIcKPFCHELjEtjlXBbBloNKHKnbTlQGwVXJoKyHbXEzTolHZXFHhkebxWDSBLOSZIahwGozYvjI",
  "address2": "uVcJMyxIIRISneOzesKnhVOpIdsEtybEKYvdASgbbQrJPeagjupYLcvlfvbeFzShzKqPhKbJHUkLkJMNpsNZgAdIcTCDWljbdRA",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "bRVceGtNdFd"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 565138889 },
	{ "address1", "XoOnOkqYFIAVtrxOkGuftHQRJIcKPFCHELjEtjlXBbBloNKHKnbTlQGwVXJoKyHbXEzTolHZXFHhkebxWDSBLOSZIahwGozYvjI" },
	{ "address2", "uVcJMyxIIRISneOzesKnhVOpIdsEtybEKYvdASgbbQrJPeagjupYLcvlfvbeFzShzKqPhKbJHUkLkJMNpsNZgAdIcTCDWljbdRA" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "phone_number", "bRVceGtNdFd" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 565138889 )
	.add("address1", "XoOnOkqYFIAVtrxOkGuftHQRJIcKPFCHELjEtjlXBbBloNKHKnbTlQGwVXJoKyHbXEzTolHZXFHhkebxWDSBLOSZIahwGozYvjI" )
	.add("address2", "uVcJMyxIIRISneOzesKnhVOpIdsEtybEKYvdASgbbQrJPeagjupYLcvlfvbeFzShzKqPhKbJHUkLkJMNpsNZgAdIcTCDWljbdRA" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", false )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("phone_number", "bRVceGtNdFd" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":565138889,\"address1\":\"XoOnOkqYFIAVtrxOkGuftHQRJIcKPFCHELjEtjlXBbBloNKHKnbTlQGwVXJoKyHbXEzTolHZXFHhkebxWDSBLOSZIahwGozYvjI\",\"address2\":\"uVcJMyxIIRISneOzesKnhVOpIdsEtybEKYvdASgbbQrJPeagjupYLcvlfvbeFzShzKqPhKbJHUkLkJMNpsNZgAdIcTCDWljbdRA\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"phone_number\":\"bRVceGtNdFd\"}"
-X POST -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
  "address1": "kwsOoUqVCLiQCaTwNgjwgycYYQfsRZeOZhwuGqdbJCvLuVMLbVdDmdQeBgnCuiRYdUsrZibTCUGzqSLyMysDTfTeUztZklrCltg",
  "address2": "aZYomjgWGmTSuZvehlTnPesZmMbhrdyMJDikYAkliIcJjnxUBICNlrLYThtUqvxjHoaiCDPmOPOsdcoydnxfYQtXogYCryLKjiy",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "OEPDjYZovJXwPRXZEfwsx"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "id", 1 },
	{ "address1", "kwsOoUqVCLiQCaTwNgjwgycYYQfsRZeOZhwuGqdbJCvLuVMLbVdDmdQeBgnCuiRYdUsrZibTCUGzqSLyMysDTfTeUztZklrCltg" },
	{ "address2", "aZYomjgWGmTSuZvehlTnPesZmMbhrdyMJDikYAkliIcJjnxUBICNlrLYThtUqvxjHoaiCDPmOPOsdcoydnxfYQtXogYCryLKjiy" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "phone_number", "OEPDjYZovJXwPRXZEfwsx" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("id", 1)
	.add("address1", "kwsOoUqVCLiQCaTwNgjwgycYYQfsRZeOZhwuGqdbJCvLuVMLbVdDmdQeBgnCuiRYdUsrZibTCUGzqSLyMysDTfTeUztZklrCltg" )
	.add("address2", "aZYomjgWGmTSuZvehlTnPesZmMbhrdyMJDikYAkliIcJjnxUBICNlrLYThtUqvxjHoaiCDPmOPOsdcoydnxfYQtXogYCryLKjiy" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", false )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("phone_number", "OEPDjYZovJXwPRXZEfwsx" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"kwsOoUqVCLiQCaTwNgjwgycYYQfsRZeOZhwuGqdbJCvLuVMLbVdDmdQeBgnCuiRYdUsrZibTCUGzqSLyMysDTfTeUztZklrCltg\",\"address2\":\"aZYomjgWGmTSuZvehlTnPesZmMbhrdyMJDikYAkliIcJjnxUBICNlrLYThtUqvxjHoaiCDPmOPOsdcoydnxfYQtXogYCryLKjiy\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"phone_number\":\"OEPDjYZovJXwPRXZEfwsx\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1582374804
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
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1582374804
```

```javascript
await session.deleteAddress(1582374804);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(1582374804);
```

```java
JsonValue address = session.delete("/cardsavr_addresses", 1582374804, null, null);
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
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1145354241
```

```javascript
const bins = await session.getBins(1145354241);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(1145354241);
```

```java
JsonValue bins = session.get("/cardsavr_bins", 1145354241, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1145354241,
  "financial_institution_id": 473491801,
  "custom_data": {
    "RtTgCGcEVkEc": "ufI/x_]r-R4]YhT7s",
    "qxTkuLeiRiwv": 42,
    "RJXqulHlnneD": false
  },
  "created_on": "1991-02-22T07:20:35.951Z",
  "last_updated_on": "1973-08-12T00:27:46.847Z",
  "bank_identification_number": "79450441"
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

**Example GET request path:**<br>`/cardsavr_bins/1145354241`

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
  "financial_institution_id": 473491801,
  "bank_identification_number": "79450441",
  "custom_data": {
    "RtTgCGcEVkEc": "ufI/x_]r-R4]YhT7s",
    "qxTkuLeiRiwv": 42,
    "RJXqulHlnneD": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 473491801 },
	{ "bank_identification_number", "79450441" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 473491801 )
	.add("bank_identification_number", "79450441" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":473491801,\"bank_identification_number\":\"79450441\",\"custom_data\":{\"RtTgCGcEVkEc\":\"ufI/x_]r-R4]YhT7s\",\"qxTkuLeiRiwv\":42,\"RJXqulHlnneD\":false}}"
-X POST -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
  "financial_institution_id": 1717797510,
  "custom_data": {
    "NBiWjKZoykBn": "5K.~6DP%&4>}pDDb&YtAK&A)Lnt",
    "hxbAzGMPHave": 39,
    "AtuBISIKABWl": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "id", 1 },
	{ "financial_institution_id", 1717797510 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("id", 1)
	.add("financial_institution_id", 1717797510 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1717797510,\"custom_data\":{\"NBiWjKZoykBn\":\"5K.~6DP%&4>}pDDb&YtAK&A)Lnt\",\"hxbAzGMPHave\":39,\"AtuBISIKABWl\":true}}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1145354241
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
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1145354241
```

```javascript
await session.deleteBin(1145354241);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(1145354241);
```

```java
JsonValue bin = session.delete("/cardsavr_bins", 1145354241, null, null);
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
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/334788666
```

```javascript
const cards = await session.getCards(334788666);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(334788666);
```

```java
JsonValue cards = session.get("/cardsavr_cards", 334788666, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 334788666,
  "address_id": 1841935816,
  "bin_id": 1440585602,
  "name_on_card": "Joe C Smith",
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "created_on": "1985-12-23T17:27:27.756Z",
  "last_updated_on": "2012-03-16T10:16:23.972Z",
  "expiration_month": 12,
  "expiration_year": 24,
  "cardholder_id": 128279421,
  "par": "sMdeScOZbDgYCqyFxQnBdxFKBJnTv"
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

**Example GET request path:**<br>`/cardsavr_cards/334788666`

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
  "cardholder_id": 128279421,
  "address_id": 1841935816,
  "bin_id": 1440585602,
  "par": "sMdeScOZbDgYCqyFxQnBdxFKBJnTv",
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
	{ "cardholder_id", 128279421 },
	{ "address_id", 1841935816 },
	{ "bin_id", 1440585602 },
	{ "par", "sMdeScOZbDgYCqyFxQnBdxFKBJnTv" },
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
	.add("cardholder_id", 128279421 )
	.add("address_id", 1841935816 )
	.add("bin_id", 1440585602 )
	.add("par", "sMdeScOZbDgYCqyFxQnBdxFKBJnTv" )
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
curl -d "{\"cardholder_id\":128279421,\"address_id\":1841935816,\"bin_id\":1440585602,\"par\":\"sMdeScOZbDgYCqyFxQnBdxFKBJnTv\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\",\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
-X POST -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
  "address_id": 1034625486,
  "bin_id": 503281770,
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
	{ "id", 1 },
	{ "address_id", 1034625486 },
	{ "bin_id", 503281770 },
	{ "name_on_card", "Joe C Smith" },
	{ "pan", "4111111111111111" },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "first_6", "000000" },
	{ "first_7", "0000000" },
	{ "first_8", "00000000" }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("id", 1)
	.add("address_id", 1034625486 )
	.add("bin_id", 503281770 )
	.add("name_on_card", "Joe C Smith" )
	.add("pan", "4111111111111111" )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("first_6", "000000" )
	.add("first_7", "0000000" )
	.add("first_8", "00000000" )
	.build();
JsonValue card = session.put("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"address_id\":1034625486,\"bin_id\":503281770,\"name_on_card\":\"Joe C Smith\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/334788666
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
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/334788666
```

```javascript
await session.deleteCard(334788666);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(334788666);
```

```java
JsonValue card = session.delete("/cardsavr_cards", 334788666, null, null);
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
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardholders/1605038454
```

```javascript
const cardholders = await session.getCardholders(1605038454);
```

```csharp
CardSavrResponse<Cardholders> cardholders = await session.GetCardholdersAsync(1605038454);
```

```java
JsonValue cardholders = session.get("/cardholders", 1605038454, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1605038454,
  "financial_institution_id": 1764584786,
  "agent_session_id": "AGPh",
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "Mri",
  "custom_data": {
    "AoHMJlCvzlEv": "5)F<}E1&7w",
    "eCBdoOjeZink": 62,
    "xOIHyZnyihGc": false
  },
  "created_on": "1997-05-22T23:10:10.499Z",
  "last_updated_on": "2013-09-06T02:01:37.577Z",
  "cuid": "RBTuzBVafJhCHIzJgZgJnDJoyWuvgWVD"
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

**Example GET request path:**<br>`/cardholders/1605038454`

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
  "financial_institution_id": 1764584786,
  "cuid": "RBTuzBVafJhCHIzJgZgJnDJoyWuvgWVD",
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "Mri",
  "custom_data": {
    "AoHMJlCvzlEv": "5)F<}E1&7w",
    "eCBdoOjeZink": 62,
    "xOIHyZnyihGc": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1764584786 },
	{ "cuid", "RBTuzBVafJhCHIzJgZgJnDJoyWuvgWVD" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "Mri" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1764584786 )
	.add("cuid", "RBTuzBVafJhCHIzJgZgJnDJoyWuvgWVD" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "Mri" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1764584786,\"cuid\":\"RBTuzBVafJhCHIzJgZgJnDJoyWuvgWVD\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"Mri\",\"custom_data\":{\"AoHMJlCvzlEv\":\"5)F<}E1&7w\",\"eCBdoOjeZink\":62,\"xOIHyZnyihGc\":false}}"
-X POST -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
  "financial_institution_id": 355966719,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "gSFxzOpMNlqaBzFbgMKYBMtu",
  "custom_data": {
    "auQNUtTPtagq": "]xEC/",
    "bjLUYbBwtmTa": 26,
    "AvehwwymUPmU": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "id", 1 },
	{ "financial_institution_id", 355966719 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "gSFxzOpMNlqaBzFbgMKYBMtu" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("id", 1)
	.add("financial_institution_id", 355966719 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "gSFxzOpMNlqaBzFbgMKYBMtu" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":355966719,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"gSFxzOpMNlqaBzFbgMKYBMtu\",\"custom_data\":{\"auQNUtTPtagq\":\"]xEC/\",\"bjLUYbBwtmTa\":26,\"AvehwwymUPmU\":true}}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardholders/1605038454
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
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardholders/1605038454
```

```javascript
await session.deleteCardholder(1605038454);
```

```csharp
CardSavrResponse<Cardholder> cardholder = await http.DeleteCardholderAsync(1605038454);
```

```java
JsonValue cardholder = session.delete("/cardholders", 1605038454, null, null);
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
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/536103088
```

```javascript
const users = await session.getUsers(536103088);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(536103088);
```

```java
JsonValue users = session.get("/cardsavr_users", 536103088, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 536103088,
  "financial_institution_id": 656857636,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "2004-02-06T13:52:38.994Z",
  "is_locked": false,
  "password_lifetime": 113,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "admin",
  "custom_data": {
    "fdmdHOPbhAox": "9$7Sjo#yo5@z/h<YBa",
    "PQXOIAKeQcLs": 57,
    "gJMLWwkReugT": false
  },
  "next_rotation_on": "1979-02-18T21:33:32.598Z",
  "created_on": "1990-07-11T07:16:35.933Z",
  "last_updated_on": "2011-08-09T00:18:08.708Z",
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

**Example GET request path:**<br>`/cardsavr_users/536103088`

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
  "financial_institution_id": 656857636,
  "username": "jsmith123",
  "last_password": "elTnOYj8SfbeylLc+paLG+wBkZQJKNd8Rxncyp/XVQ4=",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "next_password": "XdzP9azYpht+hyLkxFrtZKs4GZgIlV1zS/aww0BEXu0=",
  "expired_password_1": "D0GRInqvsfq74Tu7yTfdjcrfiI/tGnUVsFGiAipmY2Q=",
  "expired_password_2": "W9xuO9zXaY4Nq+HAf8wwpGeFBYFeyRaqyEBtiPLzX+o=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 113,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "admin",
  "custom_data": {
    "fdmdHOPbhAox": "9$7Sjo#yo5@z/h<YBa",
    "PQXOIAKeQcLs": 57,
    "gJMLWwkReugT": false
  },
  "next_rotation_on": "1979-02-18T21:33:32.598Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 656857636 },
	{ "username", "jsmith123" },
	{ "last_password", "elTnOYj8SfbeylLc+paLG+wBkZQJKNd8Rxncyp/XVQ4=" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "next_password", "XdzP9azYpht+hyLkxFrtZKs4GZgIlV1zS/aww0BEXu0=" },
	{ "expired_password_1", "D0GRInqvsfq74Tu7yTfdjcrfiI/tGnUVsFGiAipmY2Q=" },
	{ "expired_password_2", "W9xuO9zXaY4Nq+HAf8wwpGeFBYFeyRaqyEBtiPLzX+o=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 113 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "admin" },
	{ "next_rotation_on", "1979-02-18T21:33:32.598Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 656857636 )
	.add("username", "jsmith123" )
	.add("last_password", "elTnOYj8SfbeylLc+paLG+wBkZQJKNd8Rxncyp/XVQ4=" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("next_password", "XdzP9azYpht+hyLkxFrtZKs4GZgIlV1zS/aww0BEXu0=" )
	.add("expired_password_1", "D0GRInqvsfq74Tu7yTfdjcrfiI/tGnUVsFGiAipmY2Q=" )
	.add("expired_password_2", "W9xuO9zXaY4Nq+HAf8wwpGeFBYFeyRaqyEBtiPLzX+o=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 113 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "admin" )
	.add("next_rotation_on", "1979-02-18T21:33:32.598Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":656857636,\"username\":\"jsmith123\",\"last_password\":\"elTnOYj8SfbeylLc+paLG+wBkZQJKNd8Rxncyp/XVQ4=\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"next_password\":\"XdzP9azYpht+hyLkxFrtZKs4GZgIlV1zS/aww0BEXu0=\",\"expired_password_1\":\"D0GRInqvsfq74Tu7yTfdjcrfiI/tGnUVsFGiAipmY2Q=\",\"expired_password_2\":\"W9xuO9zXaY4Nq+HAf8wwpGeFBYFeyRaqyEBtiPLzX+o=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":113,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"admin\",\"custom_data\":{\"fdmdHOPbhAox\":\"9$7Sjo#yo5@z/h<YBa\",\"PQXOIAKeQcLs\":57,\"gJMLWwkReugT\":false},\"next_rotation_on\":\"1979-02-18T21:33:32.598Z\"}"
-X POST -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
  "financial_institution_id": 1216921206,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 294,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "admin",
  "custom_data": {
    "QaPwBYBwQOyd": "^pOjz9rQ~8I-@&<n-j",
    "QMcPtmZPJWYI": 91,
    "ONzNYaSflZQq": true
  },
  "next_rotation_on": "1989-10-04T20:31:16.797Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "id", 1 },
	{ "financial_institution_id", 1216921206 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 294 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "admin" },
	{ "next_rotation_on", "1989-10-04T20:31:16.797Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("id", 1)
	.add("financial_institution_id", 1216921206 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 294 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "admin" )
	.add("next_rotation_on", "1989-10-04T20:31:16.797Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1216921206,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":294,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"admin\",\"custom_data\":{\"QaPwBYBwQOyd\":\"^pOjz9rQ~8I-@&<n-j\",\"QMcPtmZPJWYI\":91,\"ONzNYaSflZQq\":true},\"next_rotation_on\":\"1989-10-04T20:31:16.797Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/536103088
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
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/536103088
```

```javascript
await session.deleteUser(536103088);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(536103088);
```

```java
JsonValue user = session.delete("/cardsavr_users", 536103088, null, null);
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
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/508904065
```

```javascript
const financialinstitutions = await session.getFinancialInstitutions(508904065);
```

```csharp
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(508904065);
```

```java
JsonValue financialinstitutions = session.get("/financial_institutions", 508904065, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 508904065,
  "name": "fhydYvPFBBcjgvukLGWxZlgMAmMlyVsBQmrFQNrGDrIrxxKgWSfUQwyArudCtfL",
  "description": "nhNWuKauWc",
  "lookup_key": "nHImhgzIeVUxKWhGMcusLkLtgiiITGoMyvNpwccAeuAAKFFyBVwVImHBmrhLxsr",
  "alternate_lookup_key": "QbHbXYzWmoEfipFGGopBmeYFroaByBrYHCgrQADTAZnNTjyIkQryCFGdTVjUaHC",
  "config": {
    "kdTHFNihAqLs": "TDfH+RvKw%t=D2!G%]<0UKV%hn",
    "rJKIrJAugQiG": 67,
    "DiSfPjGemVND": false
  },
  "email_config": {
    "CnCYfhmPeIMa": "vhC",
    "GDjaMDJqGhrg": 94,
    "ewKzqJEBZHEB": true
  },
  "created_on": "2003-07-11T15:13:59.757Z",
  "last_updated_on": "1975-06-13T14:00:41.108Z"
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

**Example GET request path:**<br>`/financial_institutions/508904065`

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
  "name": "fhydYvPFBBcjgvukLGWxZlgMAmMlyVsBQmrFQNrGDrIrxxKgWSfUQwyArudCtfL",
  "description": "nhNWuKauWc",
  "lookup_key": "nHImhgzIeVUxKWhGMcusLkLtgiiITGoMyvNpwccAeuAAKFFyBVwVImHBmrhLxsr",
  "alternate_lookup_key": "QbHbXYzWmoEfipFGGopBmeYFroaByBrYHCgrQADTAZnNTjyIkQryCFGdTVjUaHC",
  "config": {
    "kdTHFNihAqLs": "TDfH+RvKw%t=D2!G%]<0UKV%hn",
    "rJKIrJAugQiG": 67,
    "DiSfPjGemVND": false
  },
  "email_config": {
    "CnCYfhmPeIMa": "vhC",
    "GDjaMDJqGhrg": 94,
    "ewKzqJEBZHEB": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "fhydYvPFBBcjgvukLGWxZlgMAmMlyVsBQmrFQNrGDrIrxxKgWSfUQwyArudCtfL" },
	{ "description", "nhNWuKauWc" },
	{ "lookup_key", "nHImhgzIeVUxKWhGMcusLkLtgiiITGoMyvNpwccAeuAAKFFyBVwVImHBmrhLxsr" },
	{ "alternate_lookup_key", "QbHbXYzWmoEfipFGGopBmeYFroaByBrYHCgrQADTAZnNTjyIkQryCFGdTVjUaHC" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "fhydYvPFBBcjgvukLGWxZlgMAmMlyVsBQmrFQNrGDrIrxxKgWSfUQwyArudCtfL" )
	.add("description", "nhNWuKauWc" )
	.add("lookup_key", "nHImhgzIeVUxKWhGMcusLkLtgiiITGoMyvNpwccAeuAAKFFyBVwVImHBmrhLxsr" )
	.add("alternate_lookup_key", "QbHbXYzWmoEfipFGGopBmeYFroaByBrYHCgrQADTAZnNTjyIkQryCFGdTVjUaHC" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"fhydYvPFBBcjgvukLGWxZlgMAmMlyVsBQmrFQNrGDrIrxxKgWSfUQwyArudCtfL\",\"description\":\"nhNWuKauWc\",\"lookup_key\":\"nHImhgzIeVUxKWhGMcusLkLtgiiITGoMyvNpwccAeuAAKFFyBVwVImHBmrhLxsr\",\"alternate_lookup_key\":\"QbHbXYzWmoEfipFGGopBmeYFroaByBrYHCgrQADTAZnNTjyIkQryCFGdTVjUaHC\",\"config\":{\"kdTHFNihAqLs\":\"TDfH+RvKw%t=D2!G%]<0UKV%hn\",\"rJKIrJAugQiG\":67,\"DiSfPjGemVND\":false},\"email_config\":{\"CnCYfhmPeIMa\":\"vhC\",\"GDjaMDJqGhrg\":94,\"ewKzqJEBZHEB\":true}}"
-X POST -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
  "name": "JqAcamoyBTNpbpGobSlKJmwAZsIcmSJEpMOpOkUScXylEwHbFdQkwtoSdFUBvKa",
  "description": "ncpILtLMAgBHmrsTAqd",
  "lookup_key": "XkzjVlvWmaJRsRohkYOXKkbIKruaZqUKrQkWBlOveKqOxfXJpLyvSzBzZNQrhjr",
  "alternate_lookup_key": "xaZQfNqsrHfKujPaylApljESxfYhKceKjuxUzgMoIDOQIWPiFYzgmajZGPBtgJE",
  "config": {
    "UKDaLMnEdjhG": "ZCoA&8%H",
    "pwghhBurekKc": 37,
    "lTJJhhtpuzvS": true
  },
  "email_config": {
    "OwlAPYgxIpOH": "#{=zEFZu]XI(uie",
    "dphmzvyVWDrb": 86,
    "gLLrcSQPZscJ": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "id", 1 },
	{ "name", "JqAcamoyBTNpbpGobSlKJmwAZsIcmSJEpMOpOkUScXylEwHbFdQkwtoSdFUBvKa" },
	{ "description", "ncpILtLMAgBHmrsTAqd" },
	{ "lookup_key", "XkzjVlvWmaJRsRohkYOXKkbIKruaZqUKrQkWBlOveKqOxfXJpLyvSzBzZNQrhjr" },
	{ "alternate_lookup_key", "xaZQfNqsrHfKujPaylApljESxfYhKceKjuxUzgMoIDOQIWPiFYzgmajZGPBtgJE" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("id", 1)
	.add("name", "JqAcamoyBTNpbpGobSlKJmwAZsIcmSJEpMOpOkUScXylEwHbFdQkwtoSdFUBvKa" )
	.add("description", "ncpILtLMAgBHmrsTAqd" )
	.add("lookup_key", "XkzjVlvWmaJRsRohkYOXKkbIKruaZqUKrQkWBlOveKqOxfXJpLyvSzBzZNQrhjr" )
	.add("alternate_lookup_key", "xaZQfNqsrHfKujPaylApljESxfYhKceKjuxUzgMoIDOQIWPiFYzgmajZGPBtgJE" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"JqAcamoyBTNpbpGobSlKJmwAZsIcmSJEpMOpOkUScXylEwHbFdQkwtoSdFUBvKa\",\"description\":\"ncpILtLMAgBHmrsTAqd\",\"lookup_key\":\"XkzjVlvWmaJRsRohkYOXKkbIKruaZqUKrQkWBlOveKqOxfXJpLyvSzBzZNQrhjr\",\"alternate_lookup_key\":\"xaZQfNqsrHfKujPaylApljESxfYhKceKjuxUzgMoIDOQIWPiFYzgmajZGPBtgJE\",\"config\":{\"UKDaLMnEdjhG\":\"ZCoA&8%H\",\"pwghhBurekKc\":37,\"lTJJhhtpuzvS\":true},\"email_config\":{\"OwlAPYgxIpOH\":\"#{=zEFZu]XI(uie\",\"dphmzvyVWDrb\":86,\"gLLrcSQPZscJ\":false}}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/508904065
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
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/508904065
```

```javascript
await session.deleteFinancialInstitution(508904065);
```

```csharp
CardSavrResponse<FinancialInstitution> financialinstitution = await http.DeleteFinancialInstitutionAsync(508904065);
```

```java
JsonValue financialinstitution = session.delete("/financial_institutions", 508904065, null, null);
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
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/2086750369
```

```javascript
const integrators = await session.getIntegrators(2086750369);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(2086750369);
```

```java
JsonValue integrators = session.get("/integrators", 2086750369, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2086750369,
  "name": "SidWNTzzxpPyfqNvyuxWWUFkSwrVFhbmUvaOgEcxNPFqlUQBn",
  "integrator_type": "cust_internal",
  "description": "keCCRCIpkqByxiOMoKtpj",
  "last_key": "tfpNjYvvYnQQHfl52EGKO+s28e8QT2LwB0fl/+6J/xs=",
  "current_key": "d1Fg79431dEzU848F+5jXZDPDYkvsgOfiiuQNTa+ahI=",
  "next_key": "L/fgFi2zyCXRJnLKQ0mMUyDXj2Nvp3gwlxLqlmfoDWQ=",
  "key_lifetime": 305,
  "next_rotation_on": "2000-11-21T13:12:19.009Z",
  "created_on": "1987-03-04T20:58:06.833Z",
  "last_updated_on": "2007-09-04T17:32:39.187Z"
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

**Example GET request path:**<br>`/integrators/2086750369`

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
  "name": "SidWNTzzxpPyfqNvyuxWWUFkSwrVFhbmUvaOgEcxNPFqlUQBn",
  "integrator_type": "cust_internal",
  "description": "keCCRCIpkqByxiOMoKtpj",
  "last_key": "tfpNjYvvYnQQHfl52EGKO+s28e8QT2LwB0fl/+6J/xs=",
  "current_key": "d1Fg79431dEzU848F+5jXZDPDYkvsgOfiiuQNTa+ahI=",
  "next_key": "L/fgFi2zyCXRJnLKQ0mMUyDXj2Nvp3gwlxLqlmfoDWQ=",
  "key_lifetime": 305,
  "next_rotation_on": "2000-11-21T13:12:19.009Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "SidWNTzzxpPyfqNvyuxWWUFkSwrVFhbmUvaOgEcxNPFqlUQBn" },
	{ "integrator_type", "cust_internal" },
	{ "description", "keCCRCIpkqByxiOMoKtpj" },
	{ "last_key", "tfpNjYvvYnQQHfl52EGKO+s28e8QT2LwB0fl/+6J/xs=" },
	{ "current_key", "d1Fg79431dEzU848F+5jXZDPDYkvsgOfiiuQNTa+ahI=" },
	{ "next_key", "L/fgFi2zyCXRJnLKQ0mMUyDXj2Nvp3gwlxLqlmfoDWQ=" },
	{ "key_lifetime", 305 },
	{ "next_rotation_on", "2000-11-21T13:12:19.009Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "SidWNTzzxpPyfqNvyuxWWUFkSwrVFhbmUvaOgEcxNPFqlUQBn" )
	.add("integrator_type", "cust_internal" )
	.add("description", "keCCRCIpkqByxiOMoKtpj" )
	.add("last_key", "tfpNjYvvYnQQHfl52EGKO+s28e8QT2LwB0fl/+6J/xs=" )
	.add("current_key", "d1Fg79431dEzU848F+5jXZDPDYkvsgOfiiuQNTa+ahI=" )
	.add("next_key", "L/fgFi2zyCXRJnLKQ0mMUyDXj2Nvp3gwlxLqlmfoDWQ=" )
	.add("key_lifetime", 305 )
	.add("next_rotation_on", "2000-11-21T13:12:19.009Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"SidWNTzzxpPyfqNvyuxWWUFkSwrVFhbmUvaOgEcxNPFqlUQBn\",\"integrator_type\":\"cust_internal\",\"description\":\"keCCRCIpkqByxiOMoKtpj\",\"last_key\":\"tfpNjYvvYnQQHfl52EGKO+s28e8QT2LwB0fl/+6J/xs=\",\"current_key\":\"d1Fg79431dEzU848F+5jXZDPDYkvsgOfiiuQNTa+ahI=\",\"next_key\":\"L/fgFi2zyCXRJnLKQ0mMUyDXj2Nvp3gwlxLqlmfoDWQ=\",\"key_lifetime\":305,\"next_rotation_on\":\"2000-11-21T13:12:19.009Z\"}"
-X POST -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
  "name": "lVTaqxohVmZGyhCatPFitsjdCBcVDzBTWsHqexSiiafEhDYyD",
  "integrator_type": "application",
  "description": "ZJyeUqwgVDEjmw",
  "last_key": "qpCoF0D90M21oiABfprnxQMAC9DQ7GwZo74xMhdDWHQ=",
  "current_key": "pPrJ0ryoeeLvDZLTsHGAOnO+bcwRcgGJuFLQfKXMuiw=",
  "next_key": "d3nP+gD4om/O12tGP7uABduYoGZ1oeTe+EBayK7jWeo=",
  "key_lifetime": 7,
  "next_rotation_on": "1988-06-19T06:29:52.090Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "id", 1 },
	{ "name", "lVTaqxohVmZGyhCatPFitsjdCBcVDzBTWsHqexSiiafEhDYyD" },
	{ "integrator_type", "application" },
	{ "description", "ZJyeUqwgVDEjmw" },
	{ "last_key", "qpCoF0D90M21oiABfprnxQMAC9DQ7GwZo74xMhdDWHQ=" },
	{ "current_key", "pPrJ0ryoeeLvDZLTsHGAOnO+bcwRcgGJuFLQfKXMuiw=" },
	{ "next_key", "d3nP+gD4om/O12tGP7uABduYoGZ1oeTe+EBayK7jWeo=" },
	{ "key_lifetime", 7 },
	{ "next_rotation_on", "1988-06-19T06:29:52.090Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("id", 1)
	.add("name", "lVTaqxohVmZGyhCatPFitsjdCBcVDzBTWsHqexSiiafEhDYyD" )
	.add("integrator_type", "application" )
	.add("description", "ZJyeUqwgVDEjmw" )
	.add("last_key", "qpCoF0D90M21oiABfprnxQMAC9DQ7GwZo74xMhdDWHQ=" )
	.add("current_key", "pPrJ0ryoeeLvDZLTsHGAOnO+bcwRcgGJuFLQfKXMuiw=" )
	.add("next_key", "d3nP+gD4om/O12tGP7uABduYoGZ1oeTe+EBayK7jWeo=" )
	.add("key_lifetime", 7 )
	.add("next_rotation_on", "1988-06-19T06:29:52.090Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"lVTaqxohVmZGyhCatPFitsjdCBcVDzBTWsHqexSiiafEhDYyD\",\"integrator_type\":\"application\",\"description\":\"ZJyeUqwgVDEjmw\",\"last_key\":\"qpCoF0D90M21oiABfprnxQMAC9DQ7GwZo74xMhdDWHQ=\",\"current_key\":\"pPrJ0ryoeeLvDZLTsHGAOnO+bcwRcgGJuFLQfKXMuiw=\",\"next_key\":\"d3nP+gD4om/O12tGP7uABduYoGZ1oeTe+EBayK7jWeo=\",\"key_lifetime\":7,\"next_rotation_on\":\"1988-06-19T06:29:52.090Z\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/2086750369
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
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/2086750369
```

```javascript
await session.deleteIntegrator(2086750369);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(2086750369);
```

```java
JsonValue integrator = session.delete("/integrators", 2086750369, null, null);
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
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/merchant_sites/280519635
```

```javascript
const merchantsites = await session.getMerchantSites(280519635);
```

```csharp
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(280519635);
```

```java
JsonValue merchantsites = session.get("/merchant_sites", 280519635, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 280519635,
  "name": "bCiHtiBbnPry",
  "host": "xCGVnEBuQrEYGssbySohFqDbMoj",
  "images": [
    {
      "lkynbIknBoQA": "G$F2}XPI&hR<_(ZvY^[M",
      "CdCAbKNZCgwW": 44,
      "lcgYrHGDSymV": false
    },
    {
      "TtlzHwRgoOwe": "(*Qgv!M1di]@=obbx",
      "PBbHfCjNiueJ": 98,
      "YZqBoWpZfANI": true
    },
    {
      "hmEVbwXZiMwL": "r<K7W1<[<VE8LsDjG~",
      "KOVkRnhGwtQj": 58,
      "TlJNNVnuUDqE": true
    }
  ],
  "mfa": true,
  "tags": "xlnY",
  "quick_start": false,
  "login": {
    "dSIeuGJwUGCR": "&RLy=OdD",
    "GUiKYxqXkLdu": 27,
    "NAyVrEMDzoww": true
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

**Example GET request path:**<br>`/merchant_sites/280519635`

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
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/1157946564
```

```javascript
const notifications = await session.getNotifications(1157946564);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(1157946564);
```

```java
JsonValue notifications = session.get("/notifications", 1157946564, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1157946564,
  "name": "NqmJoGOOJMDOaNhNPxYYPKZjZCeMxCHjeayClgbzdgzzeYYgfvDQkdixAPfLvyV",
  "type": "webhook",
  "event": "session_complete",
  "config": {
    "NmcKBHaDJToh": "*VolP52@(TS@73*ugsb8W#15TpNKl&",
    "OhfJMSePpExF": 51,
    "SAnQOBqGEyzw": true
  },
  "html_template": "IpKpZflIiBGnLLNjQngigsoYmUekAwrM",
  "text_template": "WqmBDnUnaXNsnfWDNRkAqEqT",
  "created_on": "2008-12-09T15:25:29.605Z",
  "last_updated_on": "2008-04-28T08:28:53.267Z",
  "financial_institution_id": 1795369387
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

**Example GET request path:**<br>`/notifications/1157946564`

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
  "financial_institution_id": 1795369387,
  "name": "NqmJoGOOJMDOaNhNPxYYPKZjZCeMxCHjeayClgbzdgzzeYYgfvDQkdixAPfLvyV",
  "type": "webhook",
  "event": "session_complete",
  "config": {
    "NmcKBHaDJToh": "*VolP52@(TS@73*ugsb8W#15TpNKl&",
    "OhfJMSePpExF": 51,
    "SAnQOBqGEyzw": true
  },
  "html_template": "IpKpZflIiBGnLLNjQngigsoYmUekAwrM",
  "text_template": "WqmBDnUnaXNsnfWDNRkAqEqT"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1795369387 },
	{ "name", "NqmJoGOOJMDOaNhNPxYYPKZjZCeMxCHjeayClgbzdgzzeYYgfvDQkdixAPfLvyV" },
	{ "type", "webhook" },
	{ "event", "session_complete" },
	{ "html_template", "IpKpZflIiBGnLLNjQngigsoYmUekAwrM" },
	{ "text_template", "WqmBDnUnaXNsnfWDNRkAqEqT" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1795369387 )
	.add("name", "NqmJoGOOJMDOaNhNPxYYPKZjZCeMxCHjeayClgbzdgzzeYYgfvDQkdixAPfLvyV" )
	.add("type", "webhook" )
	.add("event", "session_complete" )
	.add("html_template", "IpKpZflIiBGnLLNjQngigsoYmUekAwrM" )
	.add("text_template", "WqmBDnUnaXNsnfWDNRkAqEqT" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1795369387,\"name\":\"NqmJoGOOJMDOaNhNPxYYPKZjZCeMxCHjeayClgbzdgzzeYYgfvDQkdixAPfLvyV\",\"type\":\"webhook\",\"event\":\"session_complete\",\"config\":{\"NmcKBHaDJToh\":\"*VolP52@(TS@73*ugsb8W#15TpNKl&\",\"OhfJMSePpExF\":51,\"SAnQOBqGEyzw\":true},\"html_template\":\"IpKpZflIiBGnLLNjQngigsoYmUekAwrM\",\"text_template\":\"WqmBDnUnaXNsnfWDNRkAqEqT\"}"
-X POST -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
  "name": "rrTGPibFQHftxbPQvPvKTjORyIibZYGEzApkskTIsonOKUWvgFyBnmZXvKcdnBk",
  "type": "email",
  "event": "session_complete",
  "config": {
    "JCMHatybceqG": "dj__",
    "QCBWpSVMRqev": 86,
    "awXpVaKmTwrS": true
  },
  "html_template": "urdwGGEtDzNCmDwzKmJ",
  "text_template": "RKNsMPUANaxzQdwRF"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "id", 1 },
	{ "name", "rrTGPibFQHftxbPQvPvKTjORyIibZYGEzApkskTIsonOKUWvgFyBnmZXvKcdnBk" },
	{ "type", "email" },
	{ "event", "session_complete" },
	{ "html_template", "urdwGGEtDzNCmDwzKmJ" },
	{ "text_template", "RKNsMPUANaxzQdwRF" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("id", 1)
	.add("name", "rrTGPibFQHftxbPQvPvKTjORyIibZYGEzApkskTIsonOKUWvgFyBnmZXvKcdnBk" )
	.add("type", "email" )
	.add("event", "session_complete" )
	.add("html_template", "urdwGGEtDzNCmDwzKmJ" )
	.add("text_template", "RKNsMPUANaxzQdwRF" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"rrTGPibFQHftxbPQvPvKTjORyIibZYGEzApkskTIsonOKUWvgFyBnmZXvKcdnBk\",\"type\":\"email\",\"event\":\"session_complete\",\"config\":{\"JCMHatybceqG\":\"dj__\",\"QCBWpSVMRqev\":86,\"awXpVaKmTwrS\":true},\"html_template\":\"urdwGGEtDzNCmDwzKmJ\",\"text_template\":\"RKNsMPUANaxzQdwRF\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/1157946564
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
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/1157946564
```

```javascript
await session.deleteNotification(1157946564);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(1157946564);
```

```java
JsonValue notification = session.delete("/notifications", 1157946564, null, null);
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
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notification_results/453222460
```

```javascript
const notificationresults = await session.getNotificationResults(453222460);
```

```csharp
CardSavrResponse<NotificationResults> notificationresults = await session.GetNotificationResultsAsync(453222460);
```

```java
JsonValue notificationresults = session.get("/notification_results", 453222460, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 453222460,
  "last_attempt_date": "1973-12-23T00:08:55.494Z",
  "fi_lookup_key": "ZoYpqqtIYpSGhoxczueegSdCMDuaPDBLraVhMVQqTDrPDGjxTrPClhQjWvgOmpg",
  "cuid": "NfxmppryYjXvkkCDeqigpthzlRyLsuYQ",
  "status": "failure",
  "attempts": 854236669,
  "notification_data": {
    "dgZDbXdlDQVW": "4h3~Tp{",
    "CvdZusvCoFXu": 90,
    "yekQeQcEpJTj": false
  },
  "created_on": "2016-06-04T12:46:31.964Z",
  "last_updated_on": "1992-12-17T14:46:35.632Z",
  "notification_id": 107372155
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

**Example GET request path:**<br>`/notification_results/453222460`

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
  "notification_id": 107372155,
  "fi_lookup_key": "ZoYpqqtIYpSGhoxczueegSdCMDuaPDBLraVhMVQqTDrPDGjxTrPClhQjWvgOmpg",
  "cuid": "NfxmppryYjXvkkCDeqigpthzlRyLsuYQ",
  "status": "failure",
  "attempts": 854236669,
  "notification_data": {
    "dgZDbXdlDQVW": "4h3~Tp{",
    "CvdZusvCoFXu": 90,
    "yekQeQcEpJTj": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 107372155 },
	{ "fi_lookup_key", "ZoYpqqtIYpSGhoxczueegSdCMDuaPDBLraVhMVQqTDrPDGjxTrPClhQjWvgOmpg" },
	{ "cuid", "NfxmppryYjXvkkCDeqigpthzlRyLsuYQ" },
	{ "status", "failure" },
	{ "attempts", 854236669 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 107372155 )
	.add("fi_lookup_key", "ZoYpqqtIYpSGhoxczueegSdCMDuaPDBLraVhMVQqTDrPDGjxTrPClhQjWvgOmpg" )
	.add("cuid", "NfxmppryYjXvkkCDeqigpthzlRyLsuYQ" )
	.add("status", "failure" )
	.add("attempts", 854236669 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":107372155,\"fi_lookup_key\":\"ZoYpqqtIYpSGhoxczueegSdCMDuaPDBLraVhMVQqTDrPDGjxTrPClhQjWvgOmpg\",\"cuid\":\"NfxmppryYjXvkkCDeqigpthzlRyLsuYQ\",\"status\":\"failure\",\"attempts\":854236669,\"notification_data\":{\"dgZDbXdlDQVW\":\"4h3~Tp{\",\"CvdZusvCoFXu\":90,\"yekQeQcEpJTj\":false}}"
-X POST -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
  "fi_lookup_key": "QuKwuAtxJBHqlOLmDbFAVSMswoBtJdJzvVxkzfWxveqBWHvXvNKUrONPbJtOBLI",
  "cuid": "mKcJAEdl",
  "status": "success",
  "attempts": 1303430704,
  "notification_data": {
    "OBqyZtCIVeUM": ".2_NWI*lDj.oH}g",
    "MMIKMFwxngWq": 43,
    "GEpEtEvtIamz": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "id", 1 },
	{ "fi_lookup_key", "QuKwuAtxJBHqlOLmDbFAVSMswoBtJdJzvVxkzfWxveqBWHvXvNKUrONPbJtOBLI" },
	{ "cuid", "mKcJAEdl" },
	{ "status", "success" },
	{ "attempts", 1303430704 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.UpdateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("id", 1)
	.add("fi_lookup_key", "QuKwuAtxJBHqlOLmDbFAVSMswoBtJdJzvVxkzfWxveqBWHvXvNKUrONPbJtOBLI" )
	.add("cuid", "mKcJAEdl" )
	.add("status", "success" )
	.add("attempts", 1303430704 )
	.build();
JsonValue notificationresult = session.put("/notification_results", body, null, null);
```

```shell
curl -d "{\"fi_lookup_key\":\"QuKwuAtxJBHqlOLmDbFAVSMswoBtJdJzvVxkzfWxveqBWHvXvNKUrONPbJtOBLI\",\"cuid\":\"mKcJAEdl\",\"status\":\"success\",\"attempts\":1303430704,\"notification_data\":{\"OBqyZtCIVeUM\":\".2_NWI*lDj.oH}g\",\"MMIKMFwxngWq\":43,\"GEpEtEvtIamz\":true}}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notification_results/453222460
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
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notification_results/453222460
```

```javascript
await session.deleteNotificationResult(453222460);
```

```csharp
CardSavrResponse<NotificationResult> notificationresult = await http.DeleteNotificationResultAsync(453222460);
```

```java
JsonValue notificationresult = session.delete("/notification_results", 453222460, null, null);
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
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/93798229
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(93798229);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(93798229);
```

```java
JsonValue singlesitejobs = session.get("/place_card_on_single_site_jobs", 93798229, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 93798229,
  "card_id": 2073755562,
  "card_placement_result_id": "Q",
  "status": "TIMEOUT_CREDENTIALS",
  "custom_data": {
    "tjlXUMKVGlwN": "UH+0>idD,2tT",
    "tHIhznrHPuOr": 87,
    "GGbTLHLWSgPs": true
  },
  "failure_reason": "fdOYSLxarxAxGtx",
  "messaging_addresses": "cnuPDdqEEmliMuwZwBHWtxQkbwMIw",
  "current_state": "UNDTXpsriHrunNCWbTCohCdAaATRUOOmpKySomeXTrTmVFDtruxbKeBCwvxHOHh",
  "notification_sent": false,
  "time_elapsed": 1111694362,
  "run_count": 1023056077,
  "job_ready_on": "2015-09-14T23:11:41.220Z",
  "started_on": "2012-10-19T14:43:09.370Z",
  "completed_on": "1970-01-19T16:59:20.079Z",
  "expiration_date": "1982-12-11T02:24:12.361Z",
  "created_on": "2003-05-24T20:38:04.093Z",
  "last_updated_on": "1992-04-27T23:53:08.849Z",
  "cardholder_id": 401403069,
  "account_id": 1177359705,
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/93798229`

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
  "cardholder_id": 401403069,
  "card_id": 2073755562,
  "account_id": 1177359705,
  "type": "CARD_PLACEMENT",
  "status": "TIMEOUT_CREDENTIALS",
  "custom_data": {
    "tjlXUMKVGlwN": "UH+0>idD,2tT",
    "tHIhznrHPuOr": 87,
    "GGbTLHLWSgPs": true
  },
  "failure_reason": "fdOYSLxarxAxGtx",
  "current_state": "UNDTXpsriHrunNCWbTCohCdAaATRUOOmpKySomeXTrTmVFDtruxbKeBCwvxHOHh",
  "notification_sent": false,
  "time_elapsed": 1111694362,
  "run_count": 1023056077,
  "started_on": "2012-10-19T14:43:09.370Z",
  "completed_on": "1970-01-19T16:59:20.079Z",
  "expiration_date": "1982-12-11T02:24:12.361Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 401403069 },
	{ "card_id", 2073755562 },
	{ "account_id", 1177359705 },
	{ "type", "CARD_PLACEMENT" },
	{ "status", "TIMEOUT_CREDENTIALS" },
	{ "failure_reason", "fdOYSLxarxAxGtx" },
	{ "current_state", "UNDTXpsriHrunNCWbTCohCdAaATRUOOmpKySomeXTrTmVFDtruxbKeBCwvxHOHh" },
	{ "notification_sent", false },
	{ "time_elapsed", 1111694362 },
	{ "run_count", 1023056077 },
	{ "started_on", "2012-10-19T14:43:09.370Z" },
	{ "completed_on", "1970-01-19T16:59:20.079Z" },
	{ "expiration_date", "1982-12-11T02:24:12.361Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 401403069 )
	.add("card_id", 2073755562 )
	.add("account_id", 1177359705 )
	.add("type", "CARD_PLACEMENT" )
	.add("status", "TIMEOUT_CREDENTIALS" )
	.add("failure_reason", "fdOYSLxarxAxGtx" )
	.add("current_state", "UNDTXpsriHrunNCWbTCohCdAaATRUOOmpKySomeXTrTmVFDtruxbKeBCwvxHOHh" )
	.add("notification_sent", false )
	.add("time_elapsed", 1111694362 )
	.add("run_count", 1023056077 )
	.add("started_on", "2012-10-19T14:43:09.370Z" )
	.add("completed_on", "1970-01-19T16:59:20.079Z" )
	.add("expiration_date", "1982-12-11T02:24:12.361Z" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":401403069,\"card_id\":2073755562,\"account_id\":1177359705,\"type\":\"CARD_PLACEMENT\",\"status\":\"TIMEOUT_CREDENTIALS\",\"custom_data\":{\"tjlXUMKVGlwN\":\"UH+0>idD,2tT\",\"tHIhznrHPuOr\":87,\"GGbTLHLWSgPs\":true},\"failure_reason\":\"fdOYSLxarxAxGtx\",\"current_state\":\"UNDTXpsriHrunNCWbTCohCdAaATRUOOmpKySomeXTrTmVFDtruxbKeBCwvxHOHh\",\"notification_sent\":false,\"time_elapsed\":1111694362,\"run_count\":1023056077,\"started_on\":\"2012-10-19T14:43:09.370Z\",\"completed_on\":\"1970-01-19T16:59:20.079Z\",\"expiration_date\":\"1982-12-11T02:24:12.361Z\"}"
-X POST -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
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
  "card_id": 1737258897,
  "status": "VBS_TIMEOUT",
  "custom_data": {
    "aPNyalLQEGqV": "xaQMM",
    "TxTRJcXnIQgb": 90,
    "OUhbDkfqPjog": true
  },
  "failure_reason": "F",
  "current_state": "nHVfdOwXFfXsZVjdvXntyUtSTgVcfDBztjcVANoSWIiTNjOgloIhIiWGOZgihOi",
  "notification_sent": false,
  "time_elapsed": 618069211,
  "run_count": 438324818,
  "started_on": "1987-12-14T05:07:10.716Z",
  "completed_on": "1995-07-07T07:18:46.294Z",
  "expiration_date": "1982-08-08T20:02:53.525Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "id", 1 },
	{ "card_id", 1737258897 },
	{ "status", "VBS_TIMEOUT" },
	{ "failure_reason", "F" },
	{ "current_state", "nHVfdOwXFfXsZVjdvXntyUtSTgVcfDBztjcVANoSWIiTNjOgloIhIiWGOZgihOi" },
	{ "notification_sent", false },
	{ "time_elapsed", 618069211 },
	{ "run_count", 438324818 },
	{ "started_on", "1987-12-14T05:07:10.716Z" },
	{ "completed_on", "1995-07-07T07:18:46.294Z" },
	{ "expiration_date", "1982-08-08T20:02:53.525Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("id", 1)
	.add("card_id", 1737258897 )
	.add("status", "VBS_TIMEOUT" )
	.add("failure_reason", "F" )
	.add("current_state", "nHVfdOwXFfXsZVjdvXntyUtSTgVcfDBztjcVANoSWIiTNjOgloIhIiWGOZgihOi" )
	.add("notification_sent", false )
	.add("time_elapsed", 618069211 )
	.add("run_count", 438324818 )
	.add("started_on", "1987-12-14T05:07:10.716Z" )
	.add("completed_on", "1995-07-07T07:18:46.294Z" )
	.add("expiration_date", "1982-08-08T20:02:53.525Z" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":1737258897,\"status\":\"VBS_TIMEOUT\",\"custom_data\":{\"aPNyalLQEGqV\":\"xaQMM\",\"TxTRJcXnIQgb\":90,\"OUhbDkfqPjog\":true},\"failure_reason\":\"F\",\"current_state\":\"nHVfdOwXFfXsZVjdvXntyUtSTgVcfDBztjcVANoSWIiTNjOgloIhIiWGOZgihOi\",\"notification_sent\":false,\"time_elapsed\":618069211,\"run_count\":438324818,\"started_on\":\"1987-12-14T05:07:10.716Z\",\"completed_on\":\"1995-07-07T07:18:46.294Z\",\"expiration_date\":\"1982-08-08T20:02:53.525Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/93798229
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
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/93798229
```

```javascript
await session.deleteSingleSiteJob(93798229);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(93798229);
```

```java
JsonValue singlesitejob = session.delete("/place_card_on_single_site_jobs", 93798229, null, null);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [single-site job response parameters](#response-place_card_on_single_site_job).

