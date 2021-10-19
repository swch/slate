
# Accounts
A cardholder account for a specific merchant site.
## Get account

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1725417479
```

```javascript
const accounts = await session.getAccounts(1725417479);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(1725417479);
```

```java
JsonValue accounts = session.get("/cardsavr_accounts", 1725417479, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1725417479,
  "last_card_placed_id": 435855850,
  "last_login": "2002-01-29T11:39:33.051Z",
  "last_password_update": "1970-02-02T04:15:31.775Z",
  "last_saved_card": "1989-11-24T21:58:55.371Z",
  "created_on": "2002-01-08T19:44:17.845Z",
  "last_updated_on": "1991-10-01T11:42:28.592Z",
  "cardholder_id": 615511803,
  "merchant_site_id": 1984395377,
  "customer_key": "aAXufyiPtszbyIFfwSb"
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

**Example GET request path:**<br>`/cardsavr_accounts/1725417479`

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
customer_key | string | A key of merchant host and cuid.  This can potentially violate a constraint with two accounts of the same merchant site.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- cardholder_ids
- merchant_site_ids
- customer_key
- last_card_placed_ids
- last_login_min / last_login_max
- last_password_update_min / last_password_update_max
- last_saved_card_min / last_saved_card_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create account

```javascript
const account = await session.createAccount({
  "cardholder_id": 615511803,
  "merchant_site_id": 1984395377,
  "customer_key": "aAXufyiPtszbyIFfwSb",
  "last_card_placed_id": 435855850,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 615511803 },
	{ "merchant_site_id", 1984395377 },
	{ "customer_key", "aAXufyiPtszbyIFfwSb" },
	{ "last_card_placed_id", 435855850 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 615511803 )
	.add("merchant_site_id", 1984395377 )
	.add("customer_key", "aAXufyiPtszbyIFfwSb" )
	.add("last_card_placed_id", 435855850 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":615511803,\"merchant_site_id\":1984395377,\"customer_key\":\"aAXufyiPtszbyIFfwSb\",\"last_card_placed_id\":435855850,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
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
customer_key | string | no
last_card_placed_id | number | no
username | string | no
password | string | no

See [account response attributes](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username and password when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Update account

```javascript
const account = await session.updateAccount(1,{
  "last_card_placed_id": 600426364,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 600426364 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 600426364 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":600426364,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1725417479
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
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1725417479
```

```javascript
await session.deleteAccount(1725417479);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(1725417479);
```

```java
JsonValue account = session.delete("/cardsavr_accounts", 1725417479, null);
```

### Path

DELETE /cardsavr_accounts/{id}

### Description

Delete a account and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [account response parameters](#response-cardsavr_account).


# Addresses
Billing address information for a cardholder.
## Get address

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1502302891
```

```javascript
const addresses = await session.getAddresses(1502302891);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(1502302891);
```

```java
JsonValue addresses = session.get("/cardsavr_addresses", 1502302891, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1502302891,
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
  "phone_number": "2065555555",
  "created_on": "2002-04-07T05:12:56.385Z",
  "last_updated_on": "2019-05-31T20:25:58.337Z",
  "cardholder_id": 195824875
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

**Example GET request path:**<br>`/cardsavr_addresses/1502302891`

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
  "cardholder_id": 195824875,
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
	{ "cardholder_id", 195824875 },
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

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 195824875 )
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
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":195824875,\"address1\":\"123 Main St.\",\"address2\":\"Unit A\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"phone_number\":\"2065555555\"}"
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
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1502302891
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1502302891
```

```javascript
await session.deleteAddress(1502302891);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(1502302891);
```

```java
JsonValue address = session.delete("/cardsavr_addresses", 1502302891, null);
```

### Path

DELETE /cardsavr_addresses/{id}

### Description

Delete a address and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [address response parameters](#response-cardsavr_address).


# Bins
A Bank Identification Number (BIN).
## Get bin

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/582686612
```

```javascript
const bins = await session.getBins(582686612);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(582686612);
```

```java
JsonValue bins = session.get("/cardsavr_bins", 582686612, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 582686612,
  "financial_institution_id": 238253952,
  "custom_data": {
    "kRhhEfCUJADA": "~jsPy6NSaBsgsiYQT->^9{Agxegl)2xp",
    "oIYLGQsvfJJj": 31,
    "sPHGnorHyWBF": true
  },
  "created_on": "1988-10-04T12:36:34.093Z",
  "last_updated_on": "2017-08-30T08:29:12.745Z",
  "bank_identification_number": "35553750"
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

**Example GET request path:**<br>`/cardsavr_bins/582686612`

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
  "financial_institution_id": 238253952,
  "bank_identification_number": "35553750",
  "custom_data": {
    "kRhhEfCUJADA": "~jsPy6NSaBsgsiYQT->^9{Agxegl)2xp",
    "oIYLGQsvfJJj": 31,
    "sPHGnorHyWBF": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 238253952 },
	{ "bank_identification_number", "35553750" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 238253952 )
	.add("bank_identification_number", "35553750" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":238253952,\"bank_identification_number\":\"35553750\",\"custom_data\":{\"kRhhEfCUJADA\":\"~jsPy6NSaBsgsiYQT->^9{Agxegl)2xp\",\"oIYLGQsvfJJj\":31,\"sPHGnorHyWBF\":true}}"
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
const bin = await session.updateBin(1,{
  "financial_institution_id": 1102074499,
  "custom_data": {
    "wDYNIuJTKGRy": "#D^ea-6*rYkW=X",
    "XQnvqtTUNxGw": 36,
    "oZxJRPtZrgxn": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1102074499 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1102074499 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1102074499,\"custom_data\":{\"wDYNIuJTKGRy\":\"#D^ea-6*rYkW=X\",\"XQnvqtTUNxGw\":36,\"oZxJRPtZrgxn\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/582686612
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/582686612
```

```javascript
await session.deleteBin(582686612);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(582686612);
```

```java
JsonValue bin = session.delete("/cardsavr_bins", 582686612, null);
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1565772637
```

```javascript
const cards = await session.getCards(1565772637);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(1565772637);
```

```java
JsonValue cards = session.get("/cardsavr_cards", 1565772637, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1565772637,
  "address_id": 510857866,
  "bin_id": 850427922,
  "name_on_card": "Joe C Smith",
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "created_on": "1985-10-15T17:34:04.978Z",
  "last_updated_on": "1981-08-29T07:51:51.571Z",
  "expiration_month": 12,
  "expiration_year": 24,
  "cardholder_id": 720601065,
  "par": "jxLwydcCXQFZtVBZyISuZPUNSYSEG"
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

**Example GET request path:**<br>`/cardsavr_cards/1565772637`

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
par | string | Unique Personal Account Reference number for this card, to be used for card lookup. Generated automatically from PAN, expiration date, and username if using the SDK.

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
  "cardholder_id": 720601065,
  "address_id": 510857866,
  "bin_id": 850427922,
  "par": "jxLwydcCXQFZtVBZyISuZPUNSYSEG",
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
	{ "cardholder_id", 720601065 },
	{ "address_id", 510857866 },
	{ "bin_id", 850427922 },
	{ "par", "jxLwydcCXQFZtVBZyISuZPUNSYSEG" },
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
	.add("cardholder_id", 720601065 )
	.add("address_id", 510857866 )
	.add("bin_id", 850427922 )
	.add("par", "jxLwydcCXQFZtVBZyISuZPUNSYSEG" )
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
curl -d "{\"cardholder_id\":720601065,\"address_id\":510857866,\"bin_id\":850427922,\"par\":\"jxLwydcCXQFZtVBZyISuZPUNSYSEG\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\",\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
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
const card = await session.updateCard(1,{
  "address_id": 1578237051,
  "bin_id": 1901745952,
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
	{ "address_id", 1578237051 },
	{ "bin_id", 1901745952 },
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
	.add("address_id", 1578237051 )
	.add("bin_id", 1901745952 )
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
curl -d "{\"address_id\":1578237051,\"bin_id\":1901745952,\"name_on_card\":\"Joe C Smith\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1565772637
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1565772637
```

```javascript
await session.deleteCard(1565772637);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(1565772637);
```

```java
JsonValue card = session.delete("/cardsavr_cards", 1565772637, null);
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
https://api.INSTANCE.cardsavr.io/cardholders/1866614974
```

```javascript
const cardholders = await session.getCardholders(1866614974);
```

```csharp
CardSavrResponse<Cardholders> cardholders = await session.GetCardholdersAsync(1866614974);
```

```java
JsonValue cardholders = session.get("/cardholders", 1866614974, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1866614974,
  "financial_institution_id": 1508137671,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "MB9810411",
  "custom_data": {
    "sptecGcyfGTr": "9Ie7fN&zblL^.udf1n@b9@(_TZ}=X",
    "EJRDKOQxYsVV": 52,
    "RyhFXFdUXXuw": true
  },
  "created_on": "1998-01-28T21:49:35.555Z",
  "last_updated_on": "1996-05-08T21:36:27.411Z",
  "cuid": "iJrKzgIlPoK"
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

**Example GET request path:**<br>`/cardholders/1866614974`

### <a name="response-cardholder"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
financial_institution_id | number (fk) | 
type | string | 
first_name | string | 
last_name | string | 
email | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
custom_data | object | 
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cuid | string | Unique ID for cardholder--can be email address, phone number, etc.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- financial_institution_ids
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
  "financial_institution_id": 1508137671,
  "cuid": "iJrKzgIlPoK",
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "MB9810411",
  "custom_data": {
    "sptecGcyfGTr": "9Ie7fN&zblL^.udf1n@b9@(_TZ}=X",
    "EJRDKOQxYsVV": 52,
    "RyhFXFdUXXuw": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1508137671 },
	{ "cuid", "iJrKzgIlPoK" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "MB9810411" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1508137671 )
	.add("cuid", "iJrKzgIlPoK" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "MB9810411" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1508137671,\"cuid\":\"iJrKzgIlPoK\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"MB9810411\",\"custom_data\":{\"sptecGcyfGTr\":\"9Ie7fN&zblL^.udf1n@b9@(_TZ}=X\",\"EJRDKOQxYsVV\":52,\"RyhFXFdUXXuw\":true}}"
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
const cardholder = await session.updateCardholder(1,{
  "financial_institution_id": 605626639,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "MB9810411",
  "custom_data": {
    "XaUoFcAHapuy": "]kqoH{a</(l",
    "orirNqgWwzHx": 32,
    "pQMZVwRpNzWD": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 605626639 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "MB9810411" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 605626639 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "MB9810411" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":605626639,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"MB9810411\",\"custom_data\":{\"XaUoFcAHapuy\":\"]kqoH{a</(l\",\"orirNqgWwzHx\":32,\"pQMZVwRpNzWD\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardholders/1866614974
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
https://api.INSTANCE.cardsavr.io/cardholders/1866614974
```

```javascript
await session.deleteCardholder(1866614974);
```

```csharp
CardSavrResponse<Cardholder> cardholder = await http.DeleteCardholderAsync(1866614974);
```

```java
JsonValue cardholder = session.delete("/cardholders", 1866614974, null);
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/1436106366
```

```javascript
const users = await session.getUsers(1436106366);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(1436106366);
```

```java
JsonValue users = session.get("/cardsavr_users", 1436106366, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1436106366,
  "financial_institution_id": 1108729745,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1991-09-15T20:27:44.431Z",
  "is_locked": false,
  "password_lifetime": 350,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_agent",
  "custom_data": {
    "fVfAjwQoQVBr": "qSHJH,K^S-",
    "xABqYXqBDEmH": 60,
    "HpJPronSpXOe": false
  },
  "next_rotation_on": "1997-01-02T19:17:30.857Z",
  "created_on": "1987-11-01T09:10:36.025Z",
  "last_updated_on": "1982-11-22T04:46:52.176Z",
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

**Example GET request path:**<br>`/cardsavr_users/1436106366`

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
  "financial_institution_id": 1108729745,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 350,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_agent",
  "custom_data": {
    "fVfAjwQoQVBr": "qSHJH,K^S-",
    "xABqYXqBDEmH": 60,
    "HpJPronSpXOe": false
  },
  "next_rotation_on": "1997-01-02T19:17:30.857Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1108729745 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 350 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "cardholder_agent" },
	{ "next_rotation_on", "1997-01-02T19:17:30.857Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1108729745 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 350 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "cardholder_agent" )
	.add("next_rotation_on", "1997-01-02T19:17:30.857Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1108729745,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":350,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"cardholder_agent\",\"custom_data\":{\"fVfAjwQoQVBr\":\"qSHJH,K^S-\",\"xABqYXqBDEmH\":60,\"HpJPronSpXOe\":false},\"next_rotation_on\":\"1997-01-02T19:17:30.857Z\"}"
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
const user = await session.updateUser(1,{
  "financial_institution_id": 1359812470,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 148,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "customer_agent",
  "custom_data": {
    "owhtkRvCmpFw": "hQ%tg0$NY9NzC8mmKU@",
    "nYQbYuDgKDUs": 69,
    "sRnKnMaAcbWH": true
  },
  "next_rotation_on": "1990-11-21T21:51:35.297Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1359812470 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 148 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "customer_agent" },
	{ "next_rotation_on", "1990-11-21T21:51:35.297Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1359812470 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 148 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "customer_agent" )
	.add("next_rotation_on", "1990-11-21T21:51:35.297Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1359812470,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":148,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"customer_agent\",\"custom_data\":{\"owhtkRvCmpFw\":\"hQ%tg0$NY9NzC8mmKU@\",\"nYQbYuDgKDUs\":69,\"sRnKnMaAcbWH\":true},\"next_rotation_on\":\"1990-11-21T21:51:35.297Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/1436106366
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/1436106366
```

```javascript
await session.deleteUser(1436106366);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(1436106366);
```

```java
JsonValue user = session.delete("/cardsavr_users", 1436106366, null);
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
https://api.INSTANCE.cardsavr.io/financial_institutions/783612746
```

```javascript
const financialinstitutions = await session.getFinancialInstitutions(783612746);
```

```csharp
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(783612746);
```

```java
JsonValue financialinstitutions = session.get("/financial_institutions", 783612746, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 783612746,
  "name": "Amazon",
  "description": "ZPrKWvOUYBmreQJWkpqfX",
  "lookup_key": "cdYFHLPpXjxqmdRyRjMYBqJgQztOagScpyuwTQJgxNXWfZdmSihRClsBjGmYAxs",
  "alternate_lookup_key": "oAyGIMFEhwVsCTuJxuVzFWQgsWIGYquKNoGMBPtSJWvLHuRFrYllESIazoXSieV",
  "created_on": "1992-11-20T07:52:43.856Z",
  "last_updated_on": "1983-03-09T16:38:17.365Z"
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

**Example GET request path:**<br>`/financial_institutions/783612746`

### <a name="response-financial_institution"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
name | string | 
description | string | 
lookup_key | string | Unique key used to identify financial institution.
alternate_lookup_key | string | 
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
  "name": "Amazon",
  "description": "ZPrKWvOUYBmreQJWkpqfX",
  "lookup_key": "cdYFHLPpXjxqmdRyRjMYBqJgQztOagScpyuwTQJgxNXWfZdmSihRClsBjGmYAxs",
  "alternate_lookup_key": "oAyGIMFEhwVsCTuJxuVzFWQgsWIGYquKNoGMBPtSJWvLHuRFrYllESIazoXSieV"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Amazon" },
	{ "description", "ZPrKWvOUYBmreQJWkpqfX" },
	{ "lookup_key", "cdYFHLPpXjxqmdRyRjMYBqJgQztOagScpyuwTQJgxNXWfZdmSihRClsBjGmYAxs" },
	{ "alternate_lookup_key", "oAyGIMFEhwVsCTuJxuVzFWQgsWIGYquKNoGMBPtSJWvLHuRFrYllESIazoXSieV" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Amazon" )
	.add("description", "ZPrKWvOUYBmreQJWkpqfX" )
	.add("lookup_key", "cdYFHLPpXjxqmdRyRjMYBqJgQztOagScpyuwTQJgxNXWfZdmSihRClsBjGmYAxs" )
	.add("alternate_lookup_key", "oAyGIMFEhwVsCTuJxuVzFWQgsWIGYquKNoGMBPtSJWvLHuRFrYllESIazoXSieV" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"Amazon\",\"description\":\"ZPrKWvOUYBmreQJWkpqfX\",\"lookup_key\":\"cdYFHLPpXjxqmdRyRjMYBqJgQztOagScpyuwTQJgxNXWfZdmSihRClsBjGmYAxs\",\"alternate_lookup_key\":\"oAyGIMFEhwVsCTuJxuVzFWQgsWIGYquKNoGMBPtSJWvLHuRFrYllESIazoXSieV\"}"
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

See [financial institution response attributes](#response-financial_institution).


## Update financial institution

```javascript
const financialinstitution = await session.updateFinancialInstitution(1,{
  "name": "Amazon",
  "description": "VpwgVtP",
  "lookup_key": "IQGhsioJfmSOjiJHjUBqDBTEzJjfZKpBzYjqylPinIFIvPFvZHbdsdnYnnEdSwy",
  "alternate_lookup_key": "pPDdvNjGsujesDgyBDrfMZeiTefwtppPHOiiwQSpjeXTDoDcfCYgPOeyBvtLwaO"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Amazon" },
	{ "description", "VpwgVtP" },
	{ "lookup_key", "IQGhsioJfmSOjiJHjUBqDBTEzJjfZKpBzYjqylPinIFIvPFvZHbdsdnYnnEdSwy" },
	{ "alternate_lookup_key", "pPDdvNjGsujesDgyBDrfMZeiTefwtppPHOiiwQSpjeXTDoDcfCYgPOeyBvtLwaO" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Amazon" )
	.add("description", "VpwgVtP" )
	.add("lookup_key", "IQGhsioJfmSOjiJHjUBqDBTEzJjfZKpBzYjqylPinIFIvPFvZHbdsdnYnnEdSwy" )
	.add("alternate_lookup_key", "pPDdvNjGsujesDgyBDrfMZeiTefwtppPHOiiwQSpjeXTDoDcfCYgPOeyBvtLwaO" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"Amazon\",\"description\":\"VpwgVtP\",\"lookup_key\":\"IQGhsioJfmSOjiJHjUBqDBTEzJjfZKpBzYjqylPinIFIvPFvZHbdsdnYnnEdSwy\",\"alternate_lookup_key\":\"pPDdvNjGsujesDgyBDrfMZeiTefwtppPHOiiwQSpjeXTDoDcfCYgPOeyBvtLwaO\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/783612746
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
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/783612746
```

```javascript
await session.deleteFinancialInstitution(783612746);
```

```csharp
CardSavrResponse<FinancialInstitution> financialinstitution = await http.DeleteFinancialInstitutionAsync(783612746);
```

```java
JsonValue financialinstitution = session.delete("/financial_institutions", 783612746, null);
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
https://api.INSTANCE.cardsavr.io/integrators/1869026258
```

```javascript
const integrators = await session.getIntegrators(1869026258);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(1869026258);
```

```java
JsonValue integrators = session.get("/integrators", 1869026258, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1869026258,
  "name": "Amazon",
  "integrator_type": "application",
  "description": "ODQjucFVROwTZu",
  "last_key": "JqgAVsqmG5YQM+sLSy7EFEEO9mZSROXj6C9OZijL+eU=",
  "current_key": "tKKjSQlz8+qmRgjf5TgezavM0O+cjhPVZQBAeqyBPRU=",
  "next_key": "uO4sbKwXmS2nW2RtIkiETe0I8rfslmM3Jeh1Y4s4Mm0=",
  "key_lifetime": 175,
  "next_rotation_on": "2017-08-21T11:42:59.449Z",
  "created_on": "1974-11-30T12:39:00.890Z",
  "last_updated_on": "2020-06-12T23:34:45.942Z"
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

**Example GET request path:**<br>`/integrators/1869026258`

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
  "name": "Amazon",
  "integrator_type": "application",
  "description": "ODQjucFVROwTZu",
  "last_key": "JqgAVsqmG5YQM+sLSy7EFEEO9mZSROXj6C9OZijL+eU=",
  "current_key": "tKKjSQlz8+qmRgjf5TgezavM0O+cjhPVZQBAeqyBPRU=",
  "next_key": "uO4sbKwXmS2nW2RtIkiETe0I8rfslmM3Jeh1Y4s4Mm0=",
  "key_lifetime": 175,
  "next_rotation_on": "2017-08-21T11:42:59.449Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Amazon" },
	{ "integrator_type", "application" },
	{ "description", "ODQjucFVROwTZu" },
	{ "last_key", "JqgAVsqmG5YQM+sLSy7EFEEO9mZSROXj6C9OZijL+eU=" },
	{ "current_key", "tKKjSQlz8+qmRgjf5TgezavM0O+cjhPVZQBAeqyBPRU=" },
	{ "next_key", "uO4sbKwXmS2nW2RtIkiETe0I8rfslmM3Jeh1Y4s4Mm0=" },
	{ "key_lifetime", 175 },
	{ "next_rotation_on", "2017-08-21T11:42:59.449Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Amazon" )
	.add("integrator_type", "application" )
	.add("description", "ODQjucFVROwTZu" )
	.add("last_key", "JqgAVsqmG5YQM+sLSy7EFEEO9mZSROXj6C9OZijL+eU=" )
	.add("current_key", "tKKjSQlz8+qmRgjf5TgezavM0O+cjhPVZQBAeqyBPRU=" )
	.add("next_key", "uO4sbKwXmS2nW2RtIkiETe0I8rfslmM3Jeh1Y4s4Mm0=" )
	.add("key_lifetime", 175 )
	.add("next_rotation_on", "2017-08-21T11:42:59.449Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"Amazon\",\"integrator_type\":\"application\",\"description\":\"ODQjucFVROwTZu\",\"last_key\":\"JqgAVsqmG5YQM+sLSy7EFEEO9mZSROXj6C9OZijL+eU=\",\"current_key\":\"tKKjSQlz8+qmRgjf5TgezavM0O+cjhPVZQBAeqyBPRU=\",\"next_key\":\"uO4sbKwXmS2nW2RtIkiETe0I8rfslmM3Jeh1Y4s4Mm0=\",\"key_lifetime\":175,\"next_rotation_on\":\"2017-08-21T11:42:59.449Z\"}"
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
const integrator = await session.updateIntegrator(1,{
  "name": "Amazon",
  "integrator_type": "application",
  "description": "eHUXzrgFXYlQkgwblMCYTvF",
  "last_key": "TY/02Nvz5O1HIETBz7n1zt8jvgsNPZI7wR2Y1SdMGlU=",
  "current_key": "k/jbg3qeOvQrqFv8Efc6/dXkvEgoQmr+2/KIORlQndI=",
  "next_key": "uu0pBJOdRHmvDlc/D7IjZ2DMdaNG7hCazgOakNLLB/k=",
  "key_lifetime": 165,
  "next_rotation_on": "1995-02-19T07:32:16.119Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Amazon" },
	{ "integrator_type", "application" },
	{ "description", "eHUXzrgFXYlQkgwblMCYTvF" },
	{ "last_key", "TY/02Nvz5O1HIETBz7n1zt8jvgsNPZI7wR2Y1SdMGlU=" },
	{ "current_key", "k/jbg3qeOvQrqFv8Efc6/dXkvEgoQmr+2/KIORlQndI=" },
	{ "next_key", "uu0pBJOdRHmvDlc/D7IjZ2DMdaNG7hCazgOakNLLB/k=" },
	{ "key_lifetime", 165 },
	{ "next_rotation_on", "1995-02-19T07:32:16.119Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Amazon" )
	.add("integrator_type", "application" )
	.add("description", "eHUXzrgFXYlQkgwblMCYTvF" )
	.add("last_key", "TY/02Nvz5O1HIETBz7n1zt8jvgsNPZI7wR2Y1SdMGlU=" )
	.add("current_key", "k/jbg3qeOvQrqFv8Efc6/dXkvEgoQmr+2/KIORlQndI=" )
	.add("next_key", "uu0pBJOdRHmvDlc/D7IjZ2DMdaNG7hCazgOakNLLB/k=" )
	.add("key_lifetime", 165 )
	.add("next_rotation_on", "1995-02-19T07:32:16.119Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"Amazon\",\"integrator_type\":\"application\",\"description\":\"eHUXzrgFXYlQkgwblMCYTvF\",\"last_key\":\"TY/02Nvz5O1HIETBz7n1zt8jvgsNPZI7wR2Y1SdMGlU=\",\"current_key\":\"k/jbg3qeOvQrqFv8Efc6/dXkvEgoQmr+2/KIORlQndI=\",\"next_key\":\"uu0pBJOdRHmvDlc/D7IjZ2DMdaNG7hCazgOakNLLB/k=\",\"key_lifetime\":165,\"next_rotation_on\":\"1995-02-19T07:32:16.119Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/1869026258
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
https://api.INSTANCE.cardsavr.io/integrators/1869026258
```

```javascript
await session.deleteIntegrator(1869026258);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(1869026258);
```

```java
JsonValue integrator = session.delete("/integrators", 1869026258, null);
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
https://api.INSTANCE.cardsavr.io/merchant_sites/769980684
```

```javascript
const merchantsites = await session.getMerchantSites(769980684);
```

```csharp
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(769980684);
```

```java
JsonValue merchantsites = session.get("/merchant_sites", 769980684, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 769980684,
  "name": "Amazon",
  "host": "amazon.com",
  "tags": "ogFYwWYoGZIKQfPG",
  "queue_name": "vbs_queue",
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
    "LJDipsgLXffh": "I0%S@Kp*NdidT",
    "SodsKPVxLrGZ": 53,
    "IzYxeHXssmRQ": true
  },
  "messages": {
    "HNMuFcmKuQQf": "dWIziGN>LK2.zLk@&2)D2rF3p/TGz5",
    "lptOsdeCfYov": 68,
    "krafYtKmmLWD": true
  },
  "mfa": false,
  "move_mouse_to_element": false,
  "proxy_order": [
    "primary_static",
    "primary_residential"
  ],
  "credit_card_page": "https://www.merchantsite.com/credit_card",
  "forgot_password_page": "https://www.merchantsite.com/forgot_password",
  "quick_start": false,
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

**Example GET request path:**<br>`/merchant_sites/769980684`

### <a name="response-merchant_site"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
name | string | 
host | string | 
tags | string | 
queue_name | string | 
required_form_fields | array | 
images | array | 
account_identification | object | 
messages | object | 
mfa | boolean | 
move_mouse_to_element | boolean | 
proxy_order | array | 
credit_card_page | string | 
forgot_password_page | string | 
quick_start | boolean | 
login_page | string | 
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
A notification record that defines how to take action on CardSavr events like jobs completing or sessions ending.
## Get notification

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/954034410
```

```javascript
const notifications = await session.getNotifications(954034410);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(954034410);
```

```java
JsonValue notifications = session.get("/notifications", 954034410, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 954034410,
  "name": "Amazon",
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
  "html_template": "uUVJRdsXBgRzwMWCuvjHzq",
  "text_template": "JcgnqdaJsjvyNdnuJoObSrnfGv",
  "created_on": "2001-04-13T07:58:29.936Z",
  "last_updated_on": "1997-10-12T00:00:06.247Z",
  "financial_institution_id": 1874309120
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

**Example GET request path:**<br>`/notifications/954034410`

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
  "financial_institution_id": 1874309120,
  "name": "Amazon",
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
  "html_template": "uUVJRdsXBgRzwMWCuvjHzq",
  "text_template": "JcgnqdaJsjvyNdnuJoObSrnfGv"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1874309120 },
	{ "name", "Amazon" },
	{ "type", "webhook" },
	{ "event", "session_complete" },
	{ "html_template", "uUVJRdsXBgRzwMWCuvjHzq" },
	{ "text_template", "JcgnqdaJsjvyNdnuJoObSrnfGv" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1874309120 )
	.add("name", "Amazon" )
	.add("type", "webhook" )
	.add("event", "session_complete" )
	.add("html_template", "uUVJRdsXBgRzwMWCuvjHzq" )
	.add("text_template", "JcgnqdaJsjvyNdnuJoObSrnfGv" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1874309120,\"name\":\"Amazon\",\"type\":\"webhook\",\"event\":\"session_complete\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"uUVJRdsXBgRzwMWCuvjHzq\",\"text_template\":\"JcgnqdaJsjvyNdnuJoObSrnfGv\"}"
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
const notification = await session.updateNotification(1,{
  "name": "Amazon",
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
  "html_template": "GJeNQVZkmha",
  "text_template": "ReveyWsKg"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Amazon" },
	{ "type", "webhook" },
	{ "event", "merchant_site_updates_all" },
	{ "html_template", "GJeNQVZkmha" },
	{ "text_template", "ReveyWsKg" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Amazon" )
	.add("type", "webhook" )
	.add("event", "merchant_site_updates_all" )
	.add("html_template", "GJeNQVZkmha" )
	.add("text_template", "ReveyWsKg" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"Amazon\",\"type\":\"webhook\",\"event\":\"merchant_site_updates_all\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"GJeNQVZkmha\",\"text_template\":\"ReveyWsKg\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/954034410
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
https://api.INSTANCE.cardsavr.io/notifications/954034410
```

```javascript
await session.deleteNotification(954034410);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(954034410);
```

```java
JsonValue notification = session.delete("/notifications", 954034410, null);
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
https://api.INSTANCE.cardsavr.io/notification_results/2037003210
```

```javascript
const notificationresults = await session.getNotificationResults(2037003210);
```

```csharp
CardSavrResponse<NotificationResults> notificationresults = await session.GetNotificationResultsAsync(2037003210);
```

```java
JsonValue notificationresults = session.get("/notification_results", 2037003210, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2037003210,
  "last_attempt_date": "2017-08-18T00:44:05.721Z",
  "fi_lookup_key": "CjLUeUtKkYrNEGQSEoUWFyklgfqivwLxwbgOTgpxDWEqEmGcKXudyofOtCXHVWO",
  "cuid": "PWLwzsr",
  "status": "failure",
  "attempts": 3,
  "notification_data": {
    "status_code": 200,
    "webhook_request": {
      "request_data": 123
    },
    "webhook_response": "OK"
  },
  "created_on": "1971-09-23T09:27:13.846Z",
  "last_updated_on": "1981-03-17T15:54:52.637Z",
  "notification_id": 1026563
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

**Example GET request path:**<br>`/notification_results/2037003210`

### <a name="response-notification_result"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
last_attempt_date | date | Date of last attempt to post this notification result
fi_lookup_key | string | 
cuid | string | Unique ID for cardholder--can be email address, phone number, etc.
status | string | 
attempts | number | Number of attempts made to send or posst notification.
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
  "notification_id": 1026563,
  "fi_lookup_key": "CjLUeUtKkYrNEGQSEoUWFyklgfqivwLxwbgOTgpxDWEqEmGcKXudyofOtCXHVWO",
  "cuid": "PWLwzsr",
  "status": "failure",
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
	{ "notification_id", 1026563 },
	{ "fi_lookup_key", "CjLUeUtKkYrNEGQSEoUWFyklgfqivwLxwbgOTgpxDWEqEmGcKXudyofOtCXHVWO" },
	{ "cuid", "PWLwzsr" },
	{ "status", "failure" },
	{ "attempts", 3 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 1026563 )
	.add("fi_lookup_key", "CjLUeUtKkYrNEGQSEoUWFyklgfqivwLxwbgOTgpxDWEqEmGcKXudyofOtCXHVWO" )
	.add("cuid", "PWLwzsr" )
	.add("status", "failure" )
	.add("attempts", 3 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":1026563,\"fi_lookup_key\":\"CjLUeUtKkYrNEGQSEoUWFyklgfqivwLxwbgOTgpxDWEqEmGcKXudyofOtCXHVWO\",\"cuid\":\"PWLwzsr\",\"status\":\"failure\",\"attempts\":3,\"notification_data\":{\"status_code\":200,\"webhook_request\":{\"request_data\":123},\"webhook_response\":\"OK\"}}"
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1894381770
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(1894381770);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(1894381770);
```

```java
JsonValue singlesitejobs = session.get("/place_card_on_single_site_jobs", 1894381770, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1894381770,
  "card_id": 588520420,
  "card_placement_result_id": 500635106,
  "status": "UNSUCCESSFUL",
  "custom_data": {
    "yyzgHaQkHEQB": "2Ddnl^aFA(2=9qZ1BRy",
    "qdbYtkTRsjLG": 71,
    "VlicdAaZQeuW": true
  },
  "failure_reason": "QmlpfURPQupmSlqsFbwcuvPLSnG",
  "current_state": "aPkywdhGyyuHFYHlCjTOAvfGvhSgboycQFzbgFkdXPxBjLIKdkGfCrhalkizgzU",
  "notification_sent": true,
  "time_elapsed": 1367593996,
  "run_count": 710423104,
  "job_ready_on": "2019-03-28T11:54:13.581Z",
  "started_on": "1988-05-13T01:03:27.678Z",
  "completed_on": "2006-06-27T07:33:17.692Z",
  "expiration_date": "1990-01-30T08:18:22.156Z",
  "created_on": "1975-01-06T18:16:37.344Z",
  "last_updated_on": "1977-11-18T00:09:13.839Z",
  "cardholder_id": 1443144087,
  "account_id": 1139076978,
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/1894381770`

### <a name="response-place_card_on_single_site_job"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
card_id | number (fk) | 
card_placement_result_id | string | 
status | string | 
custom_data | object | 
failure_reason | string | 
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

NOTE: [credential_requests](#get-credential-requests) for a job can be [hydrated](#hydration) on single-site jobs. See response for example.

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
  "cardholder_id": 1443144087,
  "card_id": 588520420,
  "account_id": 1139076978,
  "type": "INTEGRATION_TEST",
  "status": "UNSUCCESSFUL",
  "custom_data": {
    "yyzgHaQkHEQB": "2Ddnl^aFA(2=9qZ1BRy",
    "qdbYtkTRsjLG": 71,
    "VlicdAaZQeuW": true
  },
  "failure_reason": "QmlpfURPQupmSlqsFbwcuvPLSnG",
  "current_state": "aPkywdhGyyuHFYHlCjTOAvfGvhSgboycQFzbgFkdXPxBjLIKdkGfCrhalkizgzU",
  "notification_sent": true,
  "time_elapsed": 1367593996,
  "run_count": 710423104,
  "started_on": "1988-05-13T01:03:27.678Z",
  "completed_on": "2006-06-27T07:33:17.692Z",
  "expiration_date": "1990-01-30T08:18:22.156Z",
  "card_placement_result_id": 500635106
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1443144087 },
	{ "card_id", 588520420 },
	{ "account_id", 1139076978 },
	{ "type", "INTEGRATION_TEST" },
	{ "status", "UNSUCCESSFUL" },
	{ "failure_reason", "QmlpfURPQupmSlqsFbwcuvPLSnG" },
	{ "current_state", "aPkywdhGyyuHFYHlCjTOAvfGvhSgboycQFzbgFkdXPxBjLIKdkGfCrhalkizgzU" },
	{ "notification_sent", true },
	{ "time_elapsed", 1367593996 },
	{ "run_count", 710423104 },
	{ "started_on", "1988-05-13T01:03:27.678Z" },
	{ "completed_on", "2006-06-27T07:33:17.692Z" },
	{ "expiration_date", "1990-01-30T08:18:22.156Z" },
	{ "card_placement_result_id", 500635106 }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1443144087 )
	.add("card_id", 588520420 )
	.add("account_id", 1139076978 )
	.add("type", "INTEGRATION_TEST" )
	.add("status", "UNSUCCESSFUL" )
	.add("failure_reason", "QmlpfURPQupmSlqsFbwcuvPLSnG" )
	.add("current_state", "aPkywdhGyyuHFYHlCjTOAvfGvhSgboycQFzbgFkdXPxBjLIKdkGfCrhalkizgzU" )
	.add("notification_sent", true )
	.add("time_elapsed", 1367593996 )
	.add("run_count", 710423104 )
	.add("started_on", "1988-05-13T01:03:27.678Z" )
	.add("completed_on", "2006-06-27T07:33:17.692Z" )
	.add("expiration_date", "1990-01-30T08:18:22.156Z" )
	.add("card_placement_result_id", 500635106 )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1443144087,\"card_id\":588520420,\"account_id\":1139076978,\"type\":\"INTEGRATION_TEST\",\"status\":\"UNSUCCESSFUL\",\"custom_data\":{\"yyzgHaQkHEQB\":\"2Ddnl^aFA(2=9qZ1BRy\",\"qdbYtkTRsjLG\":71,\"VlicdAaZQeuW\":true},\"failure_reason\":\"QmlpfURPQupmSlqsFbwcuvPLSnG\",\"current_state\":\"aPkywdhGyyuHFYHlCjTOAvfGvhSgboycQFzbgFkdXPxBjLIKdkGfCrhalkizgzU\",\"notification_sent\":true,\"time_elapsed\":1367593996,\"run_count\":710423104,\"started_on\":\"1988-05-13T01:03:27.678Z\",\"completed_on\":\"2006-06-27T07:33:17.692Z\",\"expiration_date\":\"1990-01-30T08:18:22.156Z\",\"card_placement_result_id\":500635106}"
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
  "card_id": 2052747044,
  "status": "ABANDONED_QUICKSTART",
  "custom_data": {
    "pWCaSaIcONdQ": "1O>[*=+o-b",
    "qpnVylaUkpJf": 35,
    "xFRPVnWOsAOC": true
  },
  "failure_reason": "QvnlmtIcKsN",
  "current_state": "pHuxTvcdcrApwwgSttxckbCCYgRnSobOyctYJDqPGQMqrLVtlWHNVESOgjhuXIh",
  "notification_sent": false,
  "time_elapsed": 1856276553,
  "run_count": 2144994577,
  "started_on": "1976-03-30T19:42:45.393Z",
  "completed_on": "2020-04-24T01:32:15.650Z",
  "expiration_date": "2012-03-24T19:02:47.069Z",
  "card_placement_result_id": 500635106
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 2052747044 },
	{ "status", "ABANDONED_QUICKSTART" },
	{ "failure_reason", "QvnlmtIcKsN" },
	{ "current_state", "pHuxTvcdcrApwwgSttxckbCCYgRnSobOyctYJDqPGQMqrLVtlWHNVESOgjhuXIh" },
	{ "notification_sent", false },
	{ "time_elapsed", 1856276553 },
	{ "run_count", 2144994577 },
	{ "started_on", "1976-03-30T19:42:45.393Z" },
	{ "completed_on", "2020-04-24T01:32:15.650Z" },
	{ "expiration_date", "2012-03-24T19:02:47.069Z" },
	{ "card_placement_result_id", 500635106 }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 2052747044 )
	.add("status", "ABANDONED_QUICKSTART" )
	.add("failure_reason", "QvnlmtIcKsN" )
	.add("current_state", "pHuxTvcdcrApwwgSttxckbCCYgRnSobOyctYJDqPGQMqrLVtlWHNVESOgjhuXIh" )
	.add("notification_sent", false )
	.add("time_elapsed", 1856276553 )
	.add("run_count", 2144994577 )
	.add("started_on", "1976-03-30T19:42:45.393Z" )
	.add("completed_on", "2020-04-24T01:32:15.650Z" )
	.add("expiration_date", "2012-03-24T19:02:47.069Z" )
	.add("card_placement_result_id", 500635106 )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":2052747044,\"status\":\"ABANDONED_QUICKSTART\",\"custom_data\":{\"pWCaSaIcONdQ\":\"1O>[*=+o-b\",\"qpnVylaUkpJf\":35,\"xFRPVnWOsAOC\":true},\"failure_reason\":\"QvnlmtIcKsN\",\"current_state\":\"pHuxTvcdcrApwwgSttxckbCCYgRnSobOyctYJDqPGQMqrLVtlWHNVESOgjhuXIh\",\"notification_sent\":false,\"time_elapsed\":1856276553,\"run_count\":2144994577,\"started_on\":\"1976-03-30T19:42:45.393Z\",\"completed_on\":\"2020-04-24T01:32:15.650Z\",\"expiration_date\":\"2012-03-24T19:02:47.069Z\",\"card_placement_result_id\":500635106}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1894381770
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1894381770
```

```javascript
await session.deleteSingleSiteJob(1894381770);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(1894381770);
```

```java
JsonValue singlesitejob = session.delete("/place_card_on_single_site_jobs", 1894381770, null);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [single-site job response parameters](#response-place_card_on_single_site_job).

