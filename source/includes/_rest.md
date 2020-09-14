
# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1767173014
```

```javascript
const accounts = await session.getAccounts(1767173014);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(1767173014);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1767173014,
  "last_card_placed_id": 1840566664,
  "last_login": "1979-09-01T01:32:16.638Z",
  "last_password_update": "2006-04-04T07:03:00.034Z",
  "last_saved_card": "2017-01-11T02:56:49.886Z",
  "created_on": "2019-10-27T19:53:59.139Z",
  "last_updated_on": "1991-08-26T23:24:38.946Z",
  "cardholder_id": 769265424,
  "merchant_site_id": 65959158
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

**Example GET request path:**<br>`/cardsavr_accounts/1767173014`

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
  "cardholder_id": 769265424,
  "merchant_site_id": 65959158,
  "last_card_placed_id": 1840566664,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 769265424 },
	{ "merchant_site_id", 65959158 },
	{ "last_card_placed_id", 1840566664 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":769265424,\"merchant_site_id\":65959158,\"last_card_placed_id\":1840566664,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
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
  "last_card_placed_id": 765859657,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 765859657 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"last_card_placed_id\":765859657,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1767173014
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

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username and password when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Delete account

```shell
curl -X DELETE
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1767173014
```

```javascript
await session.deleteAccount(1767173014, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(1767173014, CARDHOLDER_SAFE_KEY);
```

### Path

DELETE /cardsavr_accounts/{id}

### Description

Delete a account and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [account response parameters](#response-cardsavr_account).

<aside class="notice">The cardholder_safe_key header is required to delete accounts for third party managed safe key stores.</aside>


# Addresses
Address objects contain billing address information for a particular user.
## Get address

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1767844842
```

```javascript
const addresses = await session.getAddresses(1767844842);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(1767844842);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1767844842,
  "address1": "IWxYfXBwJuZSQhSMMcnPBfffIvPNeoaKMxNYTXxbHIBFnyrJtGLSzCweOvjGdUQPQgzqVDTNZolgAvvpSuYXVTXjYFEyauCBHCN",
  "address2": "otWdWjIkTAzqXlrPhtQDYcMaoqFCeEeCSSAFYXYjrooSYMmNtACUqGoosOTFRjcBDixZQHbJAXIPTinEyuPdLdgEpNjUgVMcKhm",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "created_on": "1970-09-23T00:34:32.437Z",
  "last_updated_on": "2015-07-15T03:51:03.756Z",
  "user_id": 1827023952
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

**Example GET request path:**<br>`/cardsavr_addresses/1767844842`

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
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
user_id | number | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- user_ids
- is_primary
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create address

```javascript
const address = await session.createAddress({
  "user_id": 1827023952,
  "address1": "IWxYfXBwJuZSQhSMMcnPBfffIvPNeoaKMxNYTXxbHIBFnyrJtGLSzCweOvjGdUQPQgzqVDTNZolgAvvpSuYXVTXjYFEyauCBHCN",
  "address2": "otWdWjIkTAzqXlrPhtQDYcMaoqFCeEeCSSAFYXYjrooSYMmNtACUqGoosOTFRjcBDixZQHbJAXIPTinEyuPdLdgEpNjUgVMcKhm",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "user_id", 1827023952 },
	{ "address1", "IWxYfXBwJuZSQhSMMcnPBfffIvPNeoaKMxNYTXxbHIBFnyrJtGLSzCweOvjGdUQPQgzqVDTNZolgAvvpSuYXVTXjYFEyauCBHCN" },
	{ "address2", "otWdWjIkTAzqXlrPhtQDYcMaoqFCeEeCSSAFYXYjrooSYMmNtACUqGoosOTFRjcBDixZQHbJAXIPTinEyuPdLdgEpNjUgVMcKhm" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```shell
curl -d "{\"user_id\":1827023952,\"address1\":\"IWxYfXBwJuZSQhSMMcnPBfffIvPNeoaKMxNYTXxbHIBFnyrJtGLSzCweOvjGdUQPQgzqVDTNZolgAvvpSuYXVTXjYFEyauCBHCN\",\"address2\":\"otWdWjIkTAzqXlrPhtQDYcMaoqFCeEeCSSAFYXYjrooSYMmNtACUqGoosOTFRjcBDixZQHbJAXIPTinEyuPdLdgEpNjUgVMcKhm\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true}"
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
user_id | number | no
address1 | string | yes
address2 | string | no
city | string | yes
subnational | string | yes
postal_code | string | yes
postal_other | string | no
country | string | no
is_primary | boolean | yes

See [address response attributes](#response-cardsavr_address).


## Update address

```javascript
const address = await session.updateAddress({
  "address1": "VoMigeXHcyMZvhTpjJrTMkFUkZpzyTCqzkPjekxzFtQQPDBBGvkQHYWYmQNUBkyikgebwYiulHgGzWscFeUqxQVoMynRkMvMLhB",
  "address2": "vanOsSZlWdFHxZXfHWfNiSbjnjKtvsAMFxLdbEAtPBNxbnXBWusxPrrNTlDXuXXLLHcuapraPkDSoDltStaGvskaCaGPxlhnbeF",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "VoMigeXHcyMZvhTpjJrTMkFUkZpzyTCqzkPjekxzFtQQPDBBGvkQHYWYmQNUBkyikgebwYiulHgGzWscFeUqxQVoMynRkMvMLhB" },
	{ "address2", "vanOsSZlWdFHxZXfHWfNiSbjnjKtvsAMFxLdbEAtPBNxbnXBWusxPrrNTlDXuXXLLHcuapraPkDSoDltStaGvskaCaGPxlhnbeF" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```shell
curl -d "{\"address1\":\"VoMigeXHcyMZvhTpjJrTMkFUkZpzyTCqzkPjekxzFtQQPDBBGvkQHYWYmQNUBkyikgebwYiulHgGzWscFeUqxQVoMynRkMvMLhB\",\"address2\":\"vanOsSZlWdFHxZXfHWfNiSbjnjKtvsAMFxLdbEAtPBNxbnXBWusxPrrNTlDXuXXLLHcuapraPkDSoDltStaGvskaCaGPxlhnbeF\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1767844842
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

See [address response parameters](#response-cardsavr_address).


## Delete address

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1767844842
```

```javascript
await session.deleteAddress(1767844842);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(1767844842);
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/286275215
```

```javascript
const bins = await session.getBins(286275215);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(286275215);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 286275215,
  "financial_institution_id": 2147081497,
  "custom_data": {
    "ZDmeWPsxzfoH": "Vji0s>JGn7)c",
    "zkKfiOlmoKMk": 30,
    "MRyQutGMsHzV": true
  },
  "created_on": "2015-05-18T09:42:52.227Z",
  "last_updated_on": "2011-10-08T13:36:54.330Z",
  "bank_identification_number": "91917177"
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

**Example GET request path:**<br>`/cardsavr_bins/286275215`

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
  "financial_institution_id": 2147081497,
  "bank_identification_number": "91917177",
  "custom_data": {
    "ZDmeWPsxzfoH": "Vji0s>JGn7)c",
    "zkKfiOlmoKMk": 30,
    "MRyQutGMsHzV": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 2147081497 },
	{ "bank_identification_number", "91917177" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":2147081497,\"bank_identification_number\":\"91917177\",\"custom_data\":{\"ZDmeWPsxzfoH\":\"Vji0s>JGn7)c\",\"zkKfiOlmoKMk\":30,\"MRyQutGMsHzV\":true}}"
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
  "financial_institution_id": 342668772,
  "custom_data": {
    "FRiJgcqFFXpT": "R7fQ83%J",
    "zHIzMRBGoEFC": 5,
    "xURVOLtDrrtH": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 342668772 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":342668772,\"custom_data\":{\"FRiJgcqFFXpT\":\"R7fQ83%J\",\"zHIzMRBGoEFC\":5,\"xURVOLtDrrtH\":true}}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/286275215
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/286275215
```

```javascript
await session.deleteBin(286275215);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(286275215);
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1731148776
```

```javascript
const cards = await session.getCards(1731148776);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(1731148776);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1731148776,
  "address_id": 605935990,
  "bin_id": 712147951,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "created_on": "1978-02-20T06:23:35.151Z",
  "last_updated_on": "1983-05-06T04:44:26.470Z",
  "expiration_month": 12,
  "expiration_year": 24,
  "cardholder_id": 2048383684,
  "par": "TZqHuvKKJAJOtDTyqJOdnDpxXmGWX"
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

**Example GET request path:**<br>`/cardsavr_cards/1731148776`

### <a name="response-cardsavr_card"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
address_id | number | 
bin_id | number (fk) | 
name_on_card | string | 
first_name | string | 
last_name | string | 
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
  "cardholder_id": 2048383684,
  "address_id": 605935990,
  "bin_id": 712147951,
  "par": "TZqHuvKKJAJOtDTyqJOdnDpxXmGWX",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 2048383684 },
	{ "address_id", 605935990 },
	{ "bin_id", 712147951 },
	{ "par", "TZqHuvKKJAJOtDTyqJOdnDpxXmGWX" },
	{ "pan", "4111111111111111" },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Joe C Smith" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "first_6", "000000" },
	{ "first_7", "0000000" },
	{ "first_8", "00000000" }
};

CardSavrResponse<Card> card = await http.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":2048383684,\"address_id\":605935990,\"bin_id\":712147951,\"par\":\"TZqHuvKKJAJOtDTyqJOdnDpxXmGWX\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
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
first_name | string | yes
last_name | string | yes

See [card response attributes](#response-cardsavr_card).

<aside class="notice">Update calls to /cardsavr_cards require the cardholder's personal cardholder_safe_key header to encrypt and save the pan and cvv when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Update card

```javascript
const card = await session.updateCard({
  "address_id": 1070180329,
  "bin_id": 1421399525,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
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
	{ "address_id", 1070180329 },
	{ "bin_id", 1421399525 },
	{ "name_on_card", "Joe C Smith" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
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

```shell
curl -d "{\"address_id\":1070180329,\"bin_id\":1421399525,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1731148776
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
first_name | string |
last_name | string |

See [card response parameters](#response-cardsavr_card).


## Delete card

```shell
curl -X DELETE
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1731148776
```

```javascript
await session.deleteCard(1731148776, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(1731148776, CARDHOLDER_SAFE_KEY);
```

### Path

DELETE /cardsavr_cards/{id}

### Description

Delete a card and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [card response parameters](#response-cardsavr_card).

<aside class="notice">The cardholder_safe_key header is required to delete cards for third party managed safe key stores.</aside>


# Users
User objects correspond to a single CardSavr user.
## Get user

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/1025967282
```

```javascript
const users = await session.getUsers(1025967282);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(1025967282);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1025967282,
  "financial_institution_id": 1470905032,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1972-12-29T00:35:37.581Z",
  "is_locked": false,
  "password_lifetime": 33,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "admin",
  "phone_number": "OoiiyztCiIzNBe",
  "custom_data": {
    "zJZYnZLchaNu": "Nj$_1)%pn3x",
    "RgxaylmBkbad": 40,
    "BkoUMMVigjGE": false
  },
  "next_rotation_on": "1993-11-10T13:21:58.485Z",
  "created_on": "1971-02-24T01:17:21.516Z",
  "last_updated_on": "2007-02-19T11:10:15.942Z",
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

**Example GET request path:**<br>`/cardsavr_users/1025967282`

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
phone_number | string | 
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
  "financial_institution_id": 1470905032,
  "username": "jsmith123",
  "last_password": "MrDpFmj7VFpnIAZ+OUMF3P8QjNoALus4Rq+R/CDqwIE=",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "next_password": "LJHWSxD2HpL/e0uIP03AQfu49tTQpofiwABY5ThpJPU=",
  "expired_password_1": "k1fWvK227+M2KrOnRWXCBIX2vCvlDT7LPIvgUfAKk5A=",
  "expired_password_2": "LcmMy4ByYWkXf/+qBYxrl+MwOL7OUEhI1NPAOawtsy8=",
  "cardholder_safe_key": "8kJ+CCJ941raEAQMGZC0fx3bqxXC9nN+rH4g8KshZlA=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 33,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "admin",
  "phone_number": "OoiiyztCiIzNBe",
  "custom_data": {
    "zJZYnZLchaNu": "Nj$_1)%pn3x",
    "RgxaylmBkbad": 40,
    "BkoUMMVigjGE": false
  },
  "next_rotation_on": "1993-11-10T13:21:58.485Z"
}, NEW_CARDHODLER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1470905032 },
	{ "username", "jsmith123" },
	{ "last_password", "MrDpFmj7VFpnIAZ+OUMF3P8QjNoALus4Rq+R/CDqwIE=" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "next_password", "LJHWSxD2HpL/e0uIP03AQfu49tTQpofiwABY5ThpJPU=" },
	{ "expired_password_1", "k1fWvK227+M2KrOnRWXCBIX2vCvlDT7LPIvgUfAKk5A=" },
	{ "expired_password_2", "LcmMy4ByYWkXf/+qBYxrl+MwOL7OUEhI1NPAOawtsy8=" },
	{ "cardholder_safe_key", "8kJ+CCJ941raEAQMGZC0fx3bqxXC9nN+rH4g8KshZlA=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 33 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "admin" },
	{ "phone_number", "OoiiyztCiIzNBe" },
	{ "next_rotation_on", "1993-11-10T13:21:58.485Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, NEW_CARDHODLER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":1470905032,\"username\":\"jsmith123\",\"last_password\":\"MrDpFmj7VFpnIAZ+OUMF3P8QjNoALus4Rq+R/CDqwIE=\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"next_password\":\"LJHWSxD2HpL/e0uIP03AQfu49tTQpofiwABY5ThpJPU=\",\"expired_password_1\":\"k1fWvK227+M2KrOnRWXCBIX2vCvlDT7LPIvgUfAKk5A=\",\"expired_password_2\":\"LcmMy4ByYWkXf/+qBYxrl+MwOL7OUEhI1NPAOawtsy8=\",\"cardholder_safe_key\":\"8kJ+CCJ941raEAQMGZC0fx3bqxXC9nN+rH4g8KshZlA=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":33,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"admin\",\"phone_number\":\"OoiiyztCiIzNBe\",\"custom_data\":{\"zJZYnZLchaNu\":\"Nj$_1)%pn3x\",\"RgxaylmBkbad\":40,\"BkoUMMVigjGE\":false},\"next_rotation_on\":\"1993-11-10T13:21:58.485Z\"}"
-X POST -H "Content-Type: application/json"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
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
cardholder_safe_key | string | no
first_name | string | no
last_name | string | no
password_lifetime | number | no
email | string | no
is_password_update_required | boolean | no
role | [string enum](#post-cardsavr_user-1)* | yes
phone_number | string | no
custom_data | object | no
next_rotation_on | date | no

See [user response attributes](#response-cardsavr_user).

#### <a name="post-cardsavr_user-1"></a>string enum*
- admin
- analyst
- cardholder
- developer
- cardholder_agent
- customer_agent
- swch_agent
- swch_auditor
- customer_auditor
- debugger_ro
- debugger
- cust_key_handler

<aside class="notice">Update calls to /cardsavr_users require the cardholder's personal cardholder_safe_key header to encrypt and save the safe when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Update user

```javascript
const user = await session.updateUser({
  "financial_institution_id": 2058704806,
  "last_password": "CCmHo+Bon7AEyrdVTfC/ZMIBteY45rf8aXynG2yabPk=",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "next_password": "TToyhYyF+Q0MDnJOSms8HkGEwMQmU6xm8IMmENzesJk=",
  "expired_password_1": "hSVht25vuqnIwPrDCBcieXv56fKNEnXgPpC6s8hVAaI=",
  "expired_password_2": "3ajb1oOHM48zD+LZxnZuFe80I0SrCPpRHIwT7p505bI=",
  "cardholder_safe_key": "qeaKP4KU28Zxep98yomKjT91hEjhz9OkgM9iywEdtXs=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 155,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "swch_auditor",
  "phone_number": "HQAJanSQjTynPy",
  "custom_data": {
    "pdmIefeJwnPN": "F(p)n5PLdcGpu7mct$",
    "WRfOQUtqOIGK": 85,
    "bzVGULvcHyJW": true
  },
  "next_rotation_on": "1988-07-17T12:24:50.754Z",
  "username": "jsmith123"
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 2058704806 },
	{ "last_password", "CCmHo+Bon7AEyrdVTfC/ZMIBteY45rf8aXynG2yabPk=" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "next_password", "TToyhYyF+Q0MDnJOSms8HkGEwMQmU6xm8IMmENzesJk=" },
	{ "expired_password_1", "hSVht25vuqnIwPrDCBcieXv56fKNEnXgPpC6s8hVAaI=" },
	{ "expired_password_2", "3ajb1oOHM48zD+LZxnZuFe80I0SrCPpRHIwT7p505bI=" },
	{ "cardholder_safe_key", "qeaKP4KU28Zxep98yomKjT91hEjhz9OkgM9iywEdtXs=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 155 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "swch_auditor" },
	{ "phone_number", "HQAJanSQjTynPy" },
	{ "next_rotation_on", "1988-07-17T12:24:50.754Z" },
	{ "username", "jsmith123" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":2058704806,\"last_password\":\"CCmHo+Bon7AEyrdVTfC/ZMIBteY45rf8aXynG2yabPk=\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"next_password\":\"TToyhYyF+Q0MDnJOSms8HkGEwMQmU6xm8IMmENzesJk=\",\"expired_password_1\":\"hSVht25vuqnIwPrDCBcieXv56fKNEnXgPpC6s8hVAaI=\",\"expired_password_2\":\"3ajb1oOHM48zD+LZxnZuFe80I0SrCPpRHIwT7p505bI=\",\"cardholder_safe_key\":\"qeaKP4KU28Zxep98yomKjT91hEjhz9OkgM9iywEdtXs=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":155,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"swch_auditor\",\"phone_number\":\"HQAJanSQjTynPy\",\"custom_data\":{\"pdmIefeJwnPN\":\"F(p)n5PLdcGpu7mct$\",\"WRfOQUtqOIGK\":85,\"bzVGULvcHyJW\":true},\"next_rotation_on\":\"1988-07-17T12:24:50.754Z\",\"username\":\"jsmith123\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/1025967282
```

### Path

PUT /cardsavr_users OR /cardsavr_users/{id}

### Description

Update a user and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
financial_institution_id | number |
cardholder_safe_key | string |
first_name | string |
last_name | string |
password_lifetime | number |
email | string |
is_password_update_required | boolean |
role | [string enum](#post-cardsavr_user-1)* |
phone_number | string |
custom_data | object |
next_rotation_on | date |

See [user response parameters](#response-cardsavr_user).

<aside class="notice">Update calls to /cardsavr_users require the cardholder's current cardholder-safe-key, and the new new-cardholder-safe-key headers when rotating the cardholder_safe_key.</aside>

## Delete user

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/1025967282
```

```javascript
await session.deleteUser(1025967282);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(1025967282);
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
https://api.INSTANCE.cardsavr.io/financial_institutions/794669063
```

```javascript
const financialinstitutions = await session.getFinancialInstitutions(794669063);
```

```csharp
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(794669063);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 794669063,
  "name": "UfXEsbnKnwkDxoNECFsVZcFIskWQZmzTKaUTnlnshxZGRyeIpMZrNKVYkTicXYX",
  "description": "zuOVaBEmotbIaWDhLwdoVa",
  "lookup_key": "SQfHABNGGMDkWGrnaEVEDrjnojMFIlwPyXYqlaShvPAfkSSiafeHvuCVbBlPcEo",
  "alternate_lookup_key": "IyhekdPYakqGymHhYEBqGHNoJScMgiyvrKNIshvpasReXomcQFAlakRWFaMDCBe",
  "created_on": "2003-05-13T20:04:18.806Z",
  "last_updated_on": "1986-06-09T02:42:22.159Z"
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

**Example GET request path:**<br>`/financial_institutions/794669063`

### <a name="response-financial_institution"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
name | string | 
description | string | 
lookup_key | string | 
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
  "name": "UfXEsbnKnwkDxoNECFsVZcFIskWQZmzTKaUTnlnshxZGRyeIpMZrNKVYkTicXYX",
  "description": "zuOVaBEmotbIaWDhLwdoVa",
  "lookup_key": "SQfHABNGGMDkWGrnaEVEDrjnojMFIlwPyXYqlaShvPAfkSSiafeHvuCVbBlPcEo",
  "alternate_lookup_key": "IyhekdPYakqGymHhYEBqGHNoJScMgiyvrKNIshvpasReXomcQFAlakRWFaMDCBe"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "UfXEsbnKnwkDxoNECFsVZcFIskWQZmzTKaUTnlnshxZGRyeIpMZrNKVYkTicXYX" },
	{ "description", "zuOVaBEmotbIaWDhLwdoVa" },
	{ "lookup_key", "SQfHABNGGMDkWGrnaEVEDrjnojMFIlwPyXYqlaShvPAfkSSiafeHvuCVbBlPcEo" },
	{ "alternate_lookup_key", "IyhekdPYakqGymHhYEBqGHNoJScMgiyvrKNIshvpasReXomcQFAlakRWFaMDCBe" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"UfXEsbnKnwkDxoNECFsVZcFIskWQZmzTKaUTnlnshxZGRyeIpMZrNKVYkTicXYX\",\"description\":\"zuOVaBEmotbIaWDhLwdoVa\",\"lookup_key\":\"SQfHABNGGMDkWGrnaEVEDrjnojMFIlwPyXYqlaShvPAfkSSiafeHvuCVbBlPcEo\",\"alternate_lookup_key\":\"IyhekdPYakqGymHhYEBqGHNoJScMgiyvrKNIshvpasReXomcQFAlakRWFaMDCBe\"}"
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

See [financial institution response attributes](#response-financial_institution).


## Update financial institution

```javascript
const financialinstitution = await session.updateFinancialInstitution({
  "name": "YABdXXqSqnLyRHZhsAIXdpxPTsPpuBgBLPsyohyaGTsOwbZMoyQearWenfVhvoE",
  "description": "WeIVbtzebCjZCwiWsskxK",
  "lookup_key": "hEtWVNhkvvpKhNQTlRCrTuIFZeZZivnRgMbwcdbVDsTzQKzDARgbYDteohCTHXm",
  "alternate_lookup_key": "YGjTmXKtUcesrOeAXUgliWnLDzqAfGdbZNgEfalEYNHCsJtsTyxynfqxjbyxHNG"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "YABdXXqSqnLyRHZhsAIXdpxPTsPpuBgBLPsyohyaGTsOwbZMoyQearWenfVhvoE" },
	{ "description", "WeIVbtzebCjZCwiWsskxK" },
	{ "lookup_key", "hEtWVNhkvvpKhNQTlRCrTuIFZeZZivnRgMbwcdbVDsTzQKzDARgbYDteohCTHXm" },
	{ "alternate_lookup_key", "YGjTmXKtUcesrOeAXUgliWnLDzqAfGdbZNgEfalEYNHCsJtsTyxynfqxjbyxHNG" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"YABdXXqSqnLyRHZhsAIXdpxPTsPpuBgBLPsyohyaGTsOwbZMoyQearWenfVhvoE\",\"description\":\"WeIVbtzebCjZCwiWsskxK\",\"lookup_key\":\"hEtWVNhkvvpKhNQTlRCrTuIFZeZZivnRgMbwcdbVDsTzQKzDARgbYDteohCTHXm\",\"alternate_lookup_key\":\"YGjTmXKtUcesrOeAXUgliWnLDzqAfGdbZNgEfalEYNHCsJtsTyxynfqxjbyxHNG\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/794669063
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
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/794669063
```

```javascript
await session.deleteFinancialInstitution(794669063);
```

```csharp
CardSavrResponse<FinancialInstitution> financialinstitution = await http.DeleteFinancialInstitutionAsync(794669063);
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
https://api.INSTANCE.cardsavr.io/integrators/2135136323
```

```javascript
const integrators = await session.getIntegrators(2135136323);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(2135136323);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2135136323,
  "name": "BdLaTDqVQLCXEYMSBOoZvALtUMtpBcmqzeyeyshqSDDsiGlUX",
  "integrator_type": "cust_internal",
  "description": "RptbprgjAdpaWPVrXB",
  "last_key": "FCRE+3xVbmjf5kLOBJ9LAsEpRaYtbT8f1npzGsFaMDU=",
  "current_key": "NYLVamMGnZYDQ96n8UGhYDBilSOijfFxBtmdl9EQxzY=",
  "next_key": "155GjKW+oUssfGCJSfWAvo+PfVeawJYI7ZPX41RzfDo=",
  "key_lifetime": 8,
  "next_rotation_on": "2014-07-15T02:45:16.157Z",
  "created_on": "2003-08-28T17:15:27.057Z",
  "last_updated_on": "2009-02-21T09:45:00.131Z"
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

**Example GET request path:**<br>`/integrators/2135136323`

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
  "name": "BdLaTDqVQLCXEYMSBOoZvALtUMtpBcmqzeyeyshqSDDsiGlUX",
  "integrator_type": "cust_internal",
  "description": "RptbprgjAdpaWPVrXB",
  "last_key": "FCRE+3xVbmjf5kLOBJ9LAsEpRaYtbT8f1npzGsFaMDU=",
  "current_key": "NYLVamMGnZYDQ96n8UGhYDBilSOijfFxBtmdl9EQxzY=",
  "next_key": "155GjKW+oUssfGCJSfWAvo+PfVeawJYI7ZPX41RzfDo=",
  "key_lifetime": 8,
  "next_rotation_on": "2014-07-15T02:45:16.157Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "BdLaTDqVQLCXEYMSBOoZvALtUMtpBcmqzeyeyshqSDDsiGlUX" },
	{ "integrator_type", "cust_internal" },
	{ "description", "RptbprgjAdpaWPVrXB" },
	{ "last_key", "FCRE+3xVbmjf5kLOBJ9LAsEpRaYtbT8f1npzGsFaMDU=" },
	{ "current_key", "NYLVamMGnZYDQ96n8UGhYDBilSOijfFxBtmdl9EQxzY=" },
	{ "next_key", "155GjKW+oUssfGCJSfWAvo+PfVeawJYI7ZPX41RzfDo=" },
	{ "key_lifetime", 8 },
	{ "next_rotation_on", "2014-07-15T02:45:16.157Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"BdLaTDqVQLCXEYMSBOoZvALtUMtpBcmqzeyeyshqSDDsiGlUX\",\"integrator_type\":\"cust_internal\",\"description\":\"RptbprgjAdpaWPVrXB\",\"last_key\":\"FCRE+3xVbmjf5kLOBJ9LAsEpRaYtbT8f1npzGsFaMDU=\",\"current_key\":\"NYLVamMGnZYDQ96n8UGhYDBilSOijfFxBtmdl9EQxzY=\",\"next_key\":\"155GjKW+oUssfGCJSfWAvo+PfVeawJYI7ZPX41RzfDo=\",\"key_lifetime\":8,\"next_rotation_on\":\"2014-07-15T02:45:16.157Z\"}"
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
  "name": "lqrnMjNJXnbkHKDUvdbUBpwksHBloTbhinwVaRMCQqTcrfABA",
  "integrator_type": "swch_internal",
  "description": "skVRVuq",
  "last_key": "MwSCxbyW8Xak0sfGds/43q2cdYvFNNTNXKHZMn7TaWg=",
  "current_key": "dmDRbAcOSntbF38uf5oWxgT4XlD/IPqk5mmzooPHAto=",
  "next_key": "C+cFOKlrJB8uAimNv2YaN5RHPKOoaRX56o2a9vbY07w=",
  "key_lifetime": 182,
  "next_rotation_on": "2008-07-15T06:00:50.941Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "lqrnMjNJXnbkHKDUvdbUBpwksHBloTbhinwVaRMCQqTcrfABA" },
	{ "integrator_type", "swch_internal" },
	{ "description", "skVRVuq" },
	{ "last_key", "MwSCxbyW8Xak0sfGds/43q2cdYvFNNTNXKHZMn7TaWg=" },
	{ "current_key", "dmDRbAcOSntbF38uf5oWxgT4XlD/IPqk5mmzooPHAto=" },
	{ "next_key", "C+cFOKlrJB8uAimNv2YaN5RHPKOoaRX56o2a9vbY07w=" },
	{ "key_lifetime", 182 },
	{ "next_rotation_on", "2008-07-15T06:00:50.941Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"lqrnMjNJXnbkHKDUvdbUBpwksHBloTbhinwVaRMCQqTcrfABA\",\"integrator_type\":\"swch_internal\",\"description\":\"skVRVuq\",\"last_key\":\"MwSCxbyW8Xak0sfGds/43q2cdYvFNNTNXKHZMn7TaWg=\",\"current_key\":\"dmDRbAcOSntbF38uf5oWxgT4XlD/IPqk5mmzooPHAto=\",\"next_key\":\"C+cFOKlrJB8uAimNv2YaN5RHPKOoaRX56o2a9vbY07w=\",\"key_lifetime\":182,\"next_rotation_on\":\"2008-07-15T06:00:50.941Z\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/2135136323
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
https://api.INSTANCE.cardsavr.io/integrators/2135136323
```

```javascript
await session.deleteIntegrator(2135136323);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(2135136323);
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
https://api.INSTANCE.cardsavr.io/merchant_sites/2023842094
```

```javascript
const merchantsites = await session.getMerchantSites(2023842094);
```

```csharp
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(2023842094);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2023842094,
  "name": "KHIDN",
  "host": "jdhPiSMqYBCtybOjwHPmswzdY",
  "image_lookup_key": "ZOtSUdlttiguAY",
  "images": [
    {
      "dKGiMsOFjaEt": "E}[",
      "BEnWfiGowSnc": 89,
      "tssVPCfbBUPU": true
    },
    {
      "jGOgOaLzcQVl": "HC_",
      "YDElShtQvizj": 47,
      "nZRhwwyOlbZB": true
    },
    {
      "SqtTwrRXNGZu": ">Ow&Q^]KO=c2{3ZQhRZQ5&j6r1RX)W^",
      "RAcgRmRupXcI": 68,
      "UKGGOwNBJITY": true
    }
  ],
  "mfa": false,
  "tags": "fBONzsrLnUISDRDvkk",
  "login": {
    "iqKfeOZYzMHi": "#2xjAI]W+WIyH",
    "MVdiKMICKgrX": 59,
    "XIThWLMaaEmC": true
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

**Example GET request path:**<br>`/merchant_sites/2023842094`

### <a name="response-merchant_site"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
name | string | 
host | string | 
image_lookup_key | string | 
images | array | 
mfa | boolean | 
tags | string | 
login | object | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- top_ids
- name_starts_with
- hosts
- host
- top_hosts
- host_starts_with
- tags

# Notifications
A notification record that defines how to take action on CardSavr events like jobs completing or sessions ending.
## Get notification

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/841805412
```

```javascript
const notifications = await session.getNotifications(841805412);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(841805412);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 841805412,
  "name": "UoZaslHLKovAkeDMvlBxLdOFWUuekGTiULPrrOeyQKzpwGZAZRtCoqXalXgqaZC",
  "type": "email",
  "config": {
    "oPTRqvXoqpei": "2i!v})cjLU/sj6gO6DyG7mJhhR}KE9wM",
    "EsbqqJtVxYAj": 62,
    "DZiflQvcROPY": false
  },
  "created_on": "1997-01-10T07:51:08.158Z",
  "last_updated_on": "1981-04-28T21:12:32.028Z",
  "financial_institution_id": 1821272350
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

**Example GET request path:**<br>`/notifications/841805412`

### <a name="response-notification"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
name | string | 
type | string | 
event | string | 
config | object | 
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
  "financial_institution_id": 1821272350,
  "name": "UoZaslHLKovAkeDMvlBxLdOFWUuekGTiULPrrOeyQKzpwGZAZRtCoqXalXgqaZC",
  "type": "email",
  "config": {
    "oPTRqvXoqpei": "2i!v})cjLU/sj6gO6DyG7mJhhR}KE9wM",
    "EsbqqJtVxYAj": 62,
    "DZiflQvcROPY": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1821272350 },
	{ "name", "UoZaslHLKovAkeDMvlBxLdOFWUuekGTiULPrrOeyQKzpwGZAZRtCoqXalXgqaZC" },
	{ "type", "email" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":1821272350,\"name\":\"UoZaslHLKovAkeDMvlBxLdOFWUuekGTiULPrrOeyQKzpwGZAZRtCoqXalXgqaZC\",\"type\":\"email\",\"config\":{\"oPTRqvXoqpei\":\"2i!v})cjLU/sj6gO6DyG7mJhhR}KE9wM\",\"EsbqqJtVxYAj\":62,\"DZiflQvcROPY\":false}}"
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

See [notification response attributes](#response-notification).

#### <a name="post-notification-1"></a>string enum*
- email
- webhook

#### <a name="post-notification-2"></a>string enum**
- session_complete


## Update notification

```javascript
const notification = await session.updateNotification({
  "name": "ALBuTLoGnNTTmpBIDlUJFHeNqPGWCiwaJdAphjvrguhUpaGzdiXDpySqGQdjkRy",
  "type": "email",
  "config": {
    "QeGoKBYZhGlE": "I!^i,4OJ+hfe>b",
    "WBxaOdpLkNKk": 23,
    "XkscXDnXYuzc": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "ALBuTLoGnNTTmpBIDlUJFHeNqPGWCiwaJdAphjvrguhUpaGzdiXDpySqGQdjkRy" },
	{ "type", "email" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```shell
curl -d "{\"name\":\"ALBuTLoGnNTTmpBIDlUJFHeNqPGWCiwaJdAphjvrguhUpaGzdiXDpySqGQdjkRy\",\"type\":\"email\",\"config\":{\"QeGoKBYZhGlE\":\"I!^i,4OJ+hfe>b\",\"WBxaOdpLkNKk\":23,\"XkscXDnXYuzc\":true}}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/841805412
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

See [notification response parameters](#response-notification).


## Delete notification

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/841805412
```

```javascript
await session.deleteNotification(841805412);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(841805412);
```

### Path

DELETE /notifications/{id}

### Description

Delete a notification and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [notification response parameters](#response-notification).


# Single-site jobs
A place_card_on_single_site_job object
## Get single-site job

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1657709819
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(1657709819);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(1657709819);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1657709819,
  "card_placement_result_id": "EsZZfCnTJHFRDAPutYfJCHWOYRFzgX",
  "status": "IN_PROGRESS",
  "custom_data": {
    "mQcKhfOrliTH": "z",
    "mMvvIVHYbCDE": 28,
    "FJvGusNyYtGg": false
  },
  "failure_reason": "dcpw",
  "messaging_addresses": "ZKNFYeOGCryHJxyjX",
  "current_state": "iVehoGsjieTjWjEQvwDJulbTKVsmGGZyUfZQmSvXcdUTzJiYVCyVSwZnZQWBVfp",
  "do_not_queue": true,
  "user_is_present": true,
  "time_elapsed": 543836749,
  "job_ready_on": "2005-03-14T06:13:38.227Z",
  "started_on": "1998-12-08T09:13:06.504Z",
  "completed_on": "2010-05-13T04:39:07.186Z",
  "expiration_date": "2014-12-02T05:01:31.741Z",
  "created_on": "1978-10-28T08:36:09.970Z",
  "last_updated_on": "2019-04-01T11:15:25.912Z",
  "user_id": 391803332,
  "card_id": 746827490,
  "account_id": 366509156
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/1657709819`

### <a name="response-place_card_on_single_site_job"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
card_placement_result_id | string | 
status | string | 
custom_data | object | 
failure_reason | string | 
messaging_addresses | string | 
current_state | string | 
do_not_queue | boolean | 
user_is_present | boolean | 
time_elapsed | number | 
job_ready_on | date | 
started_on | date | 
completed_on | date | 
expiration_date | date | 
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
user_id | number (fk) | 
card_id | number (fk) | 
account_id | number (fk) | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- user_ids
- card_ids
- account_ids
- card_placement_result_ids
- status
- status_include / status_exclude
- current_state
- do_not_queue
- user_is_present
- time_elapsed_min / time_elapsed_max
- job_ready_on_min / job_ready_on_max
- started_on_min / started_on_max
- completed_on_min / completed_on_max
- expiration_date_min / expiration_date_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create single-site job

```javascript
const singlesitejob = await session.createSingleSiteJob({
  "place_card_on_multiple_sites_job_id": 1441439773,
  "user_id": 391803332,
  "card_id": 746827490,
  "account_id": 366509156,
  "status": "IN_PROGRESS",
  "custom_data": {
    "mQcKhfOrliTH": "z",
    "mMvvIVHYbCDE": 28,
    "FJvGusNyYtGg": false
  },
  "failure_reason": "dcpw",
  "current_state": "iVehoGsjieTjWjEQvwDJulbTKVsmGGZyUfZQmSvXcdUTzJiYVCyVSwZnZQWBVfp",
  "do_not_queue": true,
  "user_is_present": true,
  "time_elapsed": 543836749,
  "started_on": "1998-12-08T09:13:06.504Z",
  "completed_on": "2010-05-13T04:39:07.186Z",
  "expiration_date": "2014-12-02T05:01:31.741Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "place_card_on_multiple_sites_job_id", 1441439773 },
	{ "user_id", 391803332 },
	{ "card_id", 746827490 },
	{ "account_id", 366509156 },
	{ "status", "IN_PROGRESS" },
	{ "failure_reason", "dcpw" },
	{ "current_state", "iVehoGsjieTjWjEQvwDJulbTKVsmGGZyUfZQmSvXcdUTzJiYVCyVSwZnZQWBVfp" },
	{ "do_not_queue", true },
	{ "user_is_present", true },
	{ "time_elapsed", 543836749 },
	{ "started_on", "1998-12-08T09:13:06.504Z" },
	{ "completed_on", "2010-05-13T04:39:07.186Z" },
	{ "expiration_date", "2014-12-02T05:01:31.741Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"place_card_on_multiple_sites_job_id\":1441439773,\"user_id\":391803332,\"card_id\":746827490,\"account_id\":366509156,\"status\":\"IN_PROGRESS\",\"custom_data\":{\"mQcKhfOrliTH\":\"z\",\"mMvvIVHYbCDE\":28,\"FJvGusNyYtGg\":false},\"failure_reason\":\"dcpw\",\"current_state\":\"iVehoGsjieTjWjEQvwDJulbTKVsmGGZyUfZQmSvXcdUTzJiYVCyVSwZnZQWBVfp\",\"do_not_queue\":true,\"user_is_present\":true,\"time_elapsed\":543836749,\"started_on\":\"1998-12-08T09:13:06.504Z\",\"completed_on\":\"2010-05-13T04:39:07.186Z\",\"expiration_date\":\"2014-12-02T05:01:31.741Z\"}"
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
user_id | number | yes
card_id | number | yes
account_id | number | yes
status | [string enum](#post-place_card_on_single_site_job-1)* | no
custom_data | object | no
failure_reason | string | no
current_state | string | no
do_not_queue | boolean | no
user_is_present | boolean | no
time_elapsed | number | no
started_on | date | no
completed_on | date | no
expiration_date | date | no

See [single-site job response attributes](#response-place_card_on_single_site_job).

#### <a name="post-place_card_on_single_site_job-1"></a>string enum*
- INITIATED
- REQUESTED
- IN_PROGRESS
- AUTH
- UPDATING
- QUEUED
- NOT_QUEUED_BR
- CANCEL_REQUESTED
- CANCELLED
- CANCELLED_QUICKSTART
- ABANDONED
- ABANDONED_QUICKSTART
- KILLED
- FREE_ACCOUNT
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
- SUCCESS
- FAILURE
- COMPLETED

<aside class="notice">Update calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Update single-site job

```javascript
const singlesitejob = await session.updateSingleSiteJob({
  "status": "COMPLETED",
  "custom_data": {
    "xBlxRhyktgoM": "wsXmIlioEaz)$[AuTcV$Bp.K<2uA15w",
    "XerpFhWZDzrm": 93,
    "mqWklCLfmnop": false
  },
  "failure_reason": "IzNBCKPGnEYMTrlopEOQ",
  "current_state": "QZhPnyVUBLiQdJMzZBhKcZgwQRtOWxeBXwhoMNBDbVTqHUDZLOPLVxjFCZYHeIf",
  "do_not_queue": false,
  "user_is_present": true,
  "time_elapsed": 483546004,
  "started_on": "2008-09-25T11:50:48.634Z",
  "completed_on": "1986-10-08T04:35:02.068Z",
  "expiration_date": "1990-12-19T16:52:55.771Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "status", "COMPLETED" },
	{ "failure_reason", "IzNBCKPGnEYMTrlopEOQ" },
	{ "current_state", "QZhPnyVUBLiQdJMzZBhKcZgwQRtOWxeBXwhoMNBDbVTqHUDZLOPLVxjFCZYHeIf" },
	{ "do_not_queue", false },
	{ "user_is_present", true },
	{ "time_elapsed", 483546004 },
	{ "started_on", "2008-09-25T11:50:48.634Z" },
	{ "completed_on", "1986-10-08T04:35:02.068Z" },
	{ "expiration_date", "1990-12-19T16:52:55.771Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"status\":\"COMPLETED\",\"custom_data\":{\"xBlxRhyktgoM\":\"wsXmIlioEaz)$[AuTcV$Bp.K<2uA15w\",\"XerpFhWZDzrm\":93,\"mqWklCLfmnop\":false},\"failure_reason\":\"IzNBCKPGnEYMTrlopEOQ\",\"current_state\":\"QZhPnyVUBLiQdJMzZBhKcZgwQRtOWxeBXwhoMNBDbVTqHUDZLOPLVxjFCZYHeIf\",\"do_not_queue\":false,\"user_is_present\":true,\"time_elapsed\":483546004,\"started_on\":\"2008-09-25T11:50:48.634Z\",\"completed_on\":\"1986-10-08T04:35:02.068Z\",\"expiration_date\":\"1990-12-19T16:52:55.771Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1657709819
```

### Path

PUT /place_card_on_single_site_jobs OR /place_card_on_single_site_jobs/{id}

### Description

Update a single-site job and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
status | [string enum](#post-place_card_on_single_site_job-1)* |
custom_data | object |
failure_reason | string |
current_state | string |
do_not_queue | boolean |
user_is_present | boolean |
time_elapsed | number |
started_on | date |
completed_on | date |
expiration_date | date |

See [single-site job response parameters](#response-place_card_on_single_site_job).

<aside class="notice">Update calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Delete single-site job

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1657709819
```

```javascript
await session.deleteSingleSiteJob(1657709819);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(1657709819);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [single-site job response parameters](#response-place_card_on_single_site_job).

