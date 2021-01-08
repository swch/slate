
# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/368518281
```

```javascript
const accounts = await session.getAccounts(368518281);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(368518281);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 368518281,
  "last_card_placed_id": 1498292412,
  "last_login": "2016-10-05T11:19:36.423Z",
  "last_password_update": "2017-07-06T00:24:51.568Z",
  "last_saved_card": "2012-11-05T19:25:52.220Z",
  "created_on": "1973-08-31T01:05:10.018Z",
  "last_updated_on": "1989-11-22T10:46:07.187Z",
  "cardholder_id": 823210165,
  "merchant_site_id": 772502923
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

**Example GET request path:**<br>`/cardsavr_accounts/368518281`

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
  "cardholder_id": 823210165,
  "merchant_site_id": 772502923,
  "last_card_placed_id": 1498292412,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 823210165 },
	{ "merchant_site_id", 772502923 },
	{ "last_card_placed_id", 1498292412 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":823210165,\"merchant_site_id\":772502923,\"last_card_placed_id\":1498292412,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
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
  "last_card_placed_id": 1141952702,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 1141952702 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"last_card_placed_id\":1141952702,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/368518281
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
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/368518281
```

```javascript
await session.deleteAccount(368518281, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(368518281, CARDHOLDER_SAFE_KEY);
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1831582549
```

```javascript
const addresses = await session.getAddresses(1831582549);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(1831582549);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1831582549,
  "address1": "TskVlyYOhgcYrLXeIGvjOEqyGMaGySfGpHTUHhwMfNtgXTOiufMdVKIbEKAmWRMdKrwEONMLLWpNukLZyCEmsAUMDfgecaUNCzo",
  "address2": "osuzIAhmHDaDRvBcmAPOnAPOhRGcladALelMRfKiVCjODxqEMBIOyHLpVNgkNdvWITAgDUoLYDDCXBvvNRrweMdPLZqwstJumHV",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "created_on": "1972-09-28T00:19:19.017Z",
  "last_updated_on": "2009-06-14T04:53:07.709Z",
  "user_id": 1076216857
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

**Example GET request path:**<br>`/cardsavr_addresses/1831582549`

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
user_id | number (fk) | 

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
  "user_id": 1076216857,
  "address1": "TskVlyYOhgcYrLXeIGvjOEqyGMaGySfGpHTUHhwMfNtgXTOiufMdVKIbEKAmWRMdKrwEONMLLWpNukLZyCEmsAUMDfgecaUNCzo",
  "address2": "osuzIAhmHDaDRvBcmAPOnAPOhRGcladALelMRfKiVCjODxqEMBIOyHLpVNgkNdvWITAgDUoLYDDCXBvvNRrweMdPLZqwstJumHV",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "user_id", 1076216857 },
	{ "address1", "TskVlyYOhgcYrLXeIGvjOEqyGMaGySfGpHTUHhwMfNtgXTOiufMdVKIbEKAmWRMdKrwEONMLLWpNukLZyCEmsAUMDfgecaUNCzo" },
	{ "address2", "osuzIAhmHDaDRvBcmAPOnAPOhRGcladALelMRfKiVCjODxqEMBIOyHLpVNgkNdvWITAgDUoLYDDCXBvvNRrweMdPLZqwstJumHV" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```shell
curl -d "{\"user_id\":1076216857,\"address1\":\"TskVlyYOhgcYrLXeIGvjOEqyGMaGySfGpHTUHhwMfNtgXTOiufMdVKIbEKAmWRMdKrwEONMLLWpNukLZyCEmsAUMDfgecaUNCzo\",\"address2\":\"osuzIAhmHDaDRvBcmAPOnAPOhRGcladALelMRfKiVCjODxqEMBIOyHLpVNgkNdvWITAgDUoLYDDCXBvvNRrweMdPLZqwstJumHV\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false}"
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
user_id | number | yes
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
  "address1": "cRppmRrgzyVcWVpIrqgTLRvJFmFCECdNeXJByrCMoFQiaBSttDwWndjXGHFUbCwISRaZFuIqahOnjSLIcFMOrTAaBvlQHWYmKsX",
  "address2": "tzVJBPXeIcTInVLEkunhjLKryfhPLOLhIbhWpMnBZkyzYxqGCbZgQGlZaqrjwEfSjhVgvkFcQLclHvJTkZSiXYBiglYkIekvUgb",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "cRppmRrgzyVcWVpIrqgTLRvJFmFCECdNeXJByrCMoFQiaBSttDwWndjXGHFUbCwISRaZFuIqahOnjSLIcFMOrTAaBvlQHWYmKsX" },
	{ "address2", "tzVJBPXeIcTInVLEkunhjLKryfhPLOLhIbhWpMnBZkyzYxqGCbZgQGlZaqrjwEfSjhVgvkFcQLclHvJTkZSiXYBiglYkIekvUgb" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```shell
curl -d "{\"address1\":\"cRppmRrgzyVcWVpIrqgTLRvJFmFCECdNeXJByrCMoFQiaBSttDwWndjXGHFUbCwISRaZFuIqahOnjSLIcFMOrTAaBvlQHWYmKsX\",\"address2\":\"tzVJBPXeIcTInVLEkunhjLKryfhPLOLhIbhWpMnBZkyzYxqGCbZgQGlZaqrjwEfSjhVgvkFcQLclHvJTkZSiXYBiglYkIekvUgb\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1831582549
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1831582549
```

```javascript
await session.deleteAddress(1831582549);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(1831582549);
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/862449046
```

```javascript
const bins = await session.getBins(862449046);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(862449046);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 862449046,
  "financial_institution_id": 1453963918,
  "custom_data": {
    "GPrEUjZntNGY": "kuR4lh_is6htKOAtE]55-CpoE",
    "sFcAruvGErbX": 56,
    "qZHvPjekgRHQ": true
  },
  "created_on": "2006-03-22T08:53:54.846Z",
  "last_updated_on": "2003-05-20T21:31:24.379Z",
  "bank_identification_number": "94983043"
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

**Example GET request path:**<br>`/cardsavr_bins/862449046`

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
  "financial_institution_id": 1453963918,
  "bank_identification_number": "94983043",
  "custom_data": {
    "GPrEUjZntNGY": "kuR4lh_is6htKOAtE]55-CpoE",
    "sFcAruvGErbX": 56,
    "qZHvPjekgRHQ": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1453963918 },
	{ "bank_identification_number", "94983043" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":1453963918,\"bank_identification_number\":\"94983043\",\"custom_data\":{\"GPrEUjZntNGY\":\"kuR4lh_is6htKOAtE]55-CpoE\",\"sFcAruvGErbX\":56,\"qZHvPjekgRHQ\":true}}"
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
  "financial_institution_id": 1482636326,
  "custom_data": {
    "kBgDaxcngjZE": "EV803vUY$6#5Q{aU+p_@Q(CR&oV)Ol}",
    "EEhtyRKjKIMe": 39,
    "vlelavcyYmQl": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1482636326 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":1482636326,\"custom_data\":{\"kBgDaxcngjZE\":\"EV803vUY$6#5Q{aU+p_@Q(CR&oV)Ol}\",\"EEhtyRKjKIMe\":39,\"vlelavcyYmQl\":true}}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/862449046
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/862449046
```

```javascript
await session.deleteBin(862449046);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(862449046);
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1230855314
```

```javascript
const cards = await session.getCards(1230855314);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(1230855314);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1230855314,
  "address_id": 1651880689,
  "bin_id": 2019158344,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "created_on": "2016-11-18T12:13:41.161Z",
  "last_updated_on": "1972-07-10T21:30:37.442Z",
  "expiration_month": 12,
  "expiration_year": 24,
  "cardholder_id": 1340995024,
  "par": "XMrNQHEgxDmQXwUvKZwZPfIHSnsep"
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

**Example GET request path:**<br>`/cardsavr_cards/1230855314`

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
  "cardholder_id": 1340995024,
  "address_id": 1651880689,
  "bin_id": 2019158344,
  "par": "XMrNQHEgxDmQXwUvKZwZPfIHSnsep",
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
	{ "cardholder_id", 1340995024 },
	{ "address_id", 1651880689 },
	{ "bin_id", 2019158344 },
	{ "par", "XMrNQHEgxDmQXwUvKZwZPfIHSnsep" },
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
curl -d "{\"cardholder_id\":1340995024,\"address_id\":1651880689,\"bin_id\":2019158344,\"par\":\"XMrNQHEgxDmQXwUvKZwZPfIHSnsep\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
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
  "address_id": 541449661,
  "bin_id": 1160425406,
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
	{ "address_id", 541449661 },
	{ "bin_id", 1160425406 },
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
curl -d "{\"address_id\":541449661,\"bin_id\":1160425406,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1230855314
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1230855314
```

```javascript
await session.deleteCard(1230855314, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(1230855314, CARDHOLDER_SAFE_KEY);
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/504209920
```

```javascript
const users = await session.getUsers(504209920);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(504209920);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 504209920,
  "financial_institution_id": 442190347,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "2014-11-14T10:40:43.810Z",
  "is_locked": false,
  "password_lifetime": 96,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_agent",
  "phone_number": "jGZkVYTDsZwdkI",
  "custom_data": {
    "TmJJkonjraTU": "4-jI",
    "VGivhdxXAqWi": 2,
    "BsiaeITBVpaB": true
  },
  "next_rotation_on": "2010-04-06T04:12:23.882Z",
  "created_on": "1982-10-27T05:07:03.785Z",
  "last_updated_on": "1994-05-09T19:37:40.734Z",
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

**Example GET request path:**<br>`/cardsavr_users/504209920`

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
  "financial_institution_id": 442190347,
  "username": "jsmith123",
  "last_password": "Xh3XJheXPwuBO0oFDs0ugMDZ2mLBtB8WqhhWw8kD9qE=",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "next_password": "m/e3QdYpzjreYTdINkpfKWH5bNkasu2enoOyN1lC/Cw=",
  "expired_password_1": "eVs8HelUixPMOceAmZNoIdRaDvF8tpjO8fUt2bZRxH4=",
  "expired_password_2": "7XJUKTNqK7Thk+VxdGk4yePKrZOgz7QW8ipLZeG6+N4=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 96,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_agent",
  "phone_number": "jGZkVYTDsZwdkI",
  "custom_data": {
    "TmJJkonjraTU": "4-jI",
    "VGivhdxXAqWi": 2,
    "BsiaeITBVpaB": true
  },
  "next_rotation_on": "2010-04-06T04:12:23.882Z"
}, NEW_CARDHODLER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 442190347 },
	{ "username", "jsmith123" },
	{ "last_password", "Xh3XJheXPwuBO0oFDs0ugMDZ2mLBtB8WqhhWw8kD9qE=" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "next_password", "m/e3QdYpzjreYTdINkpfKWH5bNkasu2enoOyN1lC/Cw=" },
	{ "expired_password_1", "eVs8HelUixPMOceAmZNoIdRaDvF8tpjO8fUt2bZRxH4=" },
	{ "expired_password_2", "7XJUKTNqK7Thk+VxdGk4yePKrZOgz7QW8ipLZeG6+N4=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 96 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "swch_agent" },
	{ "phone_number", "jGZkVYTDsZwdkI" },
	{ "next_rotation_on", "2010-04-06T04:12:23.882Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, NEW_CARDHODLER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":442190347,\"username\":\"jsmith123\",\"last_password\":\"Xh3XJheXPwuBO0oFDs0ugMDZ2mLBtB8WqhhWw8kD9qE=\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"next_password\":\"m/e3QdYpzjreYTdINkpfKWH5bNkasu2enoOyN1lC/Cw=\",\"expired_password_1\":\"eVs8HelUixPMOceAmZNoIdRaDvF8tpjO8fUt2bZRxH4=\",\"expired_password_2\":\"7XJUKTNqK7Thk+VxdGk4yePKrZOgz7QW8ipLZeG6+N4=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":96,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"swch_agent\",\"phone_number\":\"jGZkVYTDsZwdkI\",\"custom_data\":{\"TmJJkonjraTU\":\"4-jI\",\"VGivhdxXAqWi\":2,\"BsiaeITBVpaB\":true},\"next_rotation_on\":\"2010-04-06T04:12:23.882Z\"}"
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
  "financial_institution_id": 244059331,
  "last_password": "gPjRZrJFnqUypy0tDs601n15aubI6ryNOQ5m9FQDktg=",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "next_password": "5kAwrCjHI+N+ZSH1NctaammsfxB1h+1QNM+HPuuzaZY=",
  "expired_password_1": "t0BLOuPY6PavH38EPoZDdoukioH/LHLHgOZ9y4Ktqjk=",
  "expired_password_2": "CvWcjyZ/1jywI2SKSK3/+qgP/2XInpxFUWn/ULMRM44=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 230,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_agent",
  "phone_number": "WlqTwVHyfCbVyL",
  "custom_data": {
    "vWqbtFCpfXUq": "Lo~2L",
    "JaXqlzdppZSF": 58,
    "OfHjNCNpJEUp": false
  },
  "next_rotation_on": "2002-09-28T09:13:44.938Z",
  "username": "jsmith123"
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 244059331 },
	{ "last_password", "gPjRZrJFnqUypy0tDs601n15aubI6ryNOQ5m9FQDktg=" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "next_password", "5kAwrCjHI+N+ZSH1NctaammsfxB1h+1QNM+HPuuzaZY=" },
	{ "expired_password_1", "t0BLOuPY6PavH38EPoZDdoukioH/LHLHgOZ9y4Ktqjk=" },
	{ "expired_password_2", "CvWcjyZ/1jywI2SKSK3/+qgP/2XInpxFUWn/ULMRM44=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 230 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "swch_agent" },
	{ "phone_number", "WlqTwVHyfCbVyL" },
	{ "next_rotation_on", "2002-09-28T09:13:44.938Z" },
	{ "username", "jsmith123" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":244059331,\"last_password\":\"gPjRZrJFnqUypy0tDs601n15aubI6ryNOQ5m9FQDktg=\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"next_password\":\"5kAwrCjHI+N+ZSH1NctaammsfxB1h+1QNM+HPuuzaZY=\",\"expired_password_1\":\"t0BLOuPY6PavH38EPoZDdoukioH/LHLHgOZ9y4Ktqjk=\",\"expired_password_2\":\"CvWcjyZ/1jywI2SKSK3/+qgP/2XInpxFUWn/ULMRM44=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":230,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"swch_agent\",\"phone_number\":\"WlqTwVHyfCbVyL\",\"custom_data\":{\"vWqbtFCpfXUq\":\"Lo~2L\",\"JaXqlzdppZSF\":58,\"OfHjNCNpJEUp\":false},\"next_rotation_on\":\"2002-09-28T09:13:44.938Z\",\"username\":\"jsmith123\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/504209920
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
phone_number | string |
custom_data | object |
next_rotation_on | date |

See [user response parameters](#response-cardsavr_user).

<aside class="notice">Update calls to /cardsavr_users require the cardholder's current cardholder-safe-key, and the new new-cardholder-safe-key headers when rotating the cardholder_safe_key.</aside>

## Delete user

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/504209920
```

```javascript
await session.deleteUser(504209920);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(504209920);
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
https://api.INSTANCE.cardsavr.io/financial_institutions/124476814
```

```javascript
const financialinstitutions = await session.getFinancialInstitutions(124476814);
```

```csharp
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(124476814);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 124476814,
  "name": "FnxRcasqoZdxFIoLwgyZsvDWYriXDnrspNcxWBHdjHmHllxCvicVyBoVptounnt",
  "description": "iFzEPOTQdsUUsYyg",
  "lookup_key": "tNqFjeeiUchakYXrEmFwKkgFYvjwFuOpfGewQMhuzTAzjqZXwewHQxpmmfnXoLs",
  "alternate_lookup_key": "WKIqoFTADjXPklZHLmZKAJKRTeqlNSaDpxSEdfGMLQbzoQOCeQnlaTdEYOrUFCH",
  "created_on": "1975-10-17T00:53:08.099Z",
  "last_updated_on": "1980-08-01T04:40:52.246Z"
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

**Example GET request path:**<br>`/financial_institutions/124476814`

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
  "name": "FnxRcasqoZdxFIoLwgyZsvDWYriXDnrspNcxWBHdjHmHllxCvicVyBoVptounnt",
  "description": "iFzEPOTQdsUUsYyg",
  "lookup_key": "tNqFjeeiUchakYXrEmFwKkgFYvjwFuOpfGewQMhuzTAzjqZXwewHQxpmmfnXoLs",
  "alternate_lookup_key": "WKIqoFTADjXPklZHLmZKAJKRTeqlNSaDpxSEdfGMLQbzoQOCeQnlaTdEYOrUFCH"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "FnxRcasqoZdxFIoLwgyZsvDWYriXDnrspNcxWBHdjHmHllxCvicVyBoVptounnt" },
	{ "description", "iFzEPOTQdsUUsYyg" },
	{ "lookup_key", "tNqFjeeiUchakYXrEmFwKkgFYvjwFuOpfGewQMhuzTAzjqZXwewHQxpmmfnXoLs" },
	{ "alternate_lookup_key", "WKIqoFTADjXPklZHLmZKAJKRTeqlNSaDpxSEdfGMLQbzoQOCeQnlaTdEYOrUFCH" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"FnxRcasqoZdxFIoLwgyZsvDWYriXDnrspNcxWBHdjHmHllxCvicVyBoVptounnt\",\"description\":\"iFzEPOTQdsUUsYyg\",\"lookup_key\":\"tNqFjeeiUchakYXrEmFwKkgFYvjwFuOpfGewQMhuzTAzjqZXwewHQxpmmfnXoLs\",\"alternate_lookup_key\":\"WKIqoFTADjXPklZHLmZKAJKRTeqlNSaDpxSEdfGMLQbzoQOCeQnlaTdEYOrUFCH\"}"
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
  "name": "NkKPqNmrhJxJmnzKCGdsdrcLqgMZCVZbPiSXfjsCohSGTsjRbEoWLsDNTYoqDaE",
  "description": "BdUrlIRQ",
  "lookup_key": "wqGMQlWOYAsddOItbTmdDXRHwgcaUFxfWgSQGJlAjKIOsymTlRMbfebEPuYXXOR",
  "alternate_lookup_key": "csdRoTatlLwWTbFQOzadaMoSmqnXzCIpXMmAgjmNpEohrXwIzeVzuutnZnzVclO"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "NkKPqNmrhJxJmnzKCGdsdrcLqgMZCVZbPiSXfjsCohSGTsjRbEoWLsDNTYoqDaE" },
	{ "description", "BdUrlIRQ" },
	{ "lookup_key", "wqGMQlWOYAsddOItbTmdDXRHwgcaUFxfWgSQGJlAjKIOsymTlRMbfebEPuYXXOR" },
	{ "alternate_lookup_key", "csdRoTatlLwWTbFQOzadaMoSmqnXzCIpXMmAgjmNpEohrXwIzeVzuutnZnzVclO" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"NkKPqNmrhJxJmnzKCGdsdrcLqgMZCVZbPiSXfjsCohSGTsjRbEoWLsDNTYoqDaE\",\"description\":\"BdUrlIRQ\",\"lookup_key\":\"wqGMQlWOYAsddOItbTmdDXRHwgcaUFxfWgSQGJlAjKIOsymTlRMbfebEPuYXXOR\",\"alternate_lookup_key\":\"csdRoTatlLwWTbFQOzadaMoSmqnXzCIpXMmAgjmNpEohrXwIzeVzuutnZnzVclO\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/124476814
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
https://api.INSTANCE.cardsavr.io/financial_institutions/124476814
```

```javascript
await session.deleteFinancialInstitution(124476814);
```

```csharp
CardSavrResponse<FinancialInstitution> financialinstitution = await http.DeleteFinancialInstitutionAsync(124476814);
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
https://api.INSTANCE.cardsavr.io/integrators/1400792844
```

```javascript
const integrators = await session.getIntegrators(1400792844);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(1400792844);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1400792844,
  "name": "IwADccARbdrYRhtgAXArOOjRQCWsjSHrAbJCTCXpDnwPlzbxt",
  "integrator_type": "swch_internal",
  "description": "kONmzanA",
  "last_key": "H3mO2acC33NHizBb/LFQ43/OkOd302fG4wAko2AuRLo=",
  "current_key": "tbAUqJh+n1RDrkklF0nEIo8pVb+pF2Awk7vzPqhLWgA=",
  "next_key": "CKBPWHEaV+DnN56lYMlzbMfWerqYaV2MnEelt6JOVvQ=",
  "key_lifetime": 94,
  "next_rotation_on": "1997-06-13T19:41:32.649Z",
  "created_on": "2018-10-02T12:17:11.857Z",
  "last_updated_on": "1971-03-03T15:41:43.348Z"
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

**Example GET request path:**<br>`/integrators/1400792844`

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
  "name": "IwADccARbdrYRhtgAXArOOjRQCWsjSHrAbJCTCXpDnwPlzbxt",
  "integrator_type": "swch_internal",
  "description": "kONmzanA",
  "last_key": "H3mO2acC33NHizBb/LFQ43/OkOd302fG4wAko2AuRLo=",
  "current_key": "tbAUqJh+n1RDrkklF0nEIo8pVb+pF2Awk7vzPqhLWgA=",
  "next_key": "CKBPWHEaV+DnN56lYMlzbMfWerqYaV2MnEelt6JOVvQ=",
  "key_lifetime": 94,
  "next_rotation_on": "1997-06-13T19:41:32.649Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "IwADccARbdrYRhtgAXArOOjRQCWsjSHrAbJCTCXpDnwPlzbxt" },
	{ "integrator_type", "swch_internal" },
	{ "description", "kONmzanA" },
	{ "last_key", "H3mO2acC33NHizBb/LFQ43/OkOd302fG4wAko2AuRLo=" },
	{ "current_key", "tbAUqJh+n1RDrkklF0nEIo8pVb+pF2Awk7vzPqhLWgA=" },
	{ "next_key", "CKBPWHEaV+DnN56lYMlzbMfWerqYaV2MnEelt6JOVvQ=" },
	{ "key_lifetime", 94 },
	{ "next_rotation_on", "1997-06-13T19:41:32.649Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"IwADccARbdrYRhtgAXArOOjRQCWsjSHrAbJCTCXpDnwPlzbxt\",\"integrator_type\":\"swch_internal\",\"description\":\"kONmzanA\",\"last_key\":\"H3mO2acC33NHizBb/LFQ43/OkOd302fG4wAko2AuRLo=\",\"current_key\":\"tbAUqJh+n1RDrkklF0nEIo8pVb+pF2Awk7vzPqhLWgA=\",\"next_key\":\"CKBPWHEaV+DnN56lYMlzbMfWerqYaV2MnEelt6JOVvQ=\",\"key_lifetime\":94,\"next_rotation_on\":\"1997-06-13T19:41:32.649Z\"}"
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
  "name": "EsfkImcIfYptanFMehEhybQQgiJefFYJYftHMdBwDvAmKjPVV",
  "integrator_type": "application",
  "description": "QTzdtGyGCZVteRszU",
  "last_key": "lUK0RP60OZ4kub0RdUz1oyFPGOZ8ww6FEFR/2fSgjv8=",
  "current_key": "nBbi61aT05lcB7GdEgP9Nkf7QQBqSTYUcmzdbHT6U5Q=",
  "next_key": "PnDNcT9SE1d/LPGSIKklCFnilMP/1vXoEMoSzUCVwu8=",
  "key_lifetime": 346,
  "next_rotation_on": "1998-03-25T10:16:01.860Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "EsfkImcIfYptanFMehEhybQQgiJefFYJYftHMdBwDvAmKjPVV" },
	{ "integrator_type", "application" },
	{ "description", "QTzdtGyGCZVteRszU" },
	{ "last_key", "lUK0RP60OZ4kub0RdUz1oyFPGOZ8ww6FEFR/2fSgjv8=" },
	{ "current_key", "nBbi61aT05lcB7GdEgP9Nkf7QQBqSTYUcmzdbHT6U5Q=" },
	{ "next_key", "PnDNcT9SE1d/LPGSIKklCFnilMP/1vXoEMoSzUCVwu8=" },
	{ "key_lifetime", 346 },
	{ "next_rotation_on", "1998-03-25T10:16:01.860Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"EsfkImcIfYptanFMehEhybQQgiJefFYJYftHMdBwDvAmKjPVV\",\"integrator_type\":\"application\",\"description\":\"QTzdtGyGCZVteRszU\",\"last_key\":\"lUK0RP60OZ4kub0RdUz1oyFPGOZ8ww6FEFR/2fSgjv8=\",\"current_key\":\"nBbi61aT05lcB7GdEgP9Nkf7QQBqSTYUcmzdbHT6U5Q=\",\"next_key\":\"PnDNcT9SE1d/LPGSIKklCFnilMP/1vXoEMoSzUCVwu8=\",\"key_lifetime\":346,\"next_rotation_on\":\"1998-03-25T10:16:01.860Z\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/1400792844
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
https://api.INSTANCE.cardsavr.io/integrators/1400792844
```

```javascript
await session.deleteIntegrator(1400792844);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(1400792844);
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
https://api.INSTANCE.cardsavr.io/merchant_sites/1008136911
```

```javascript
const merchantsites = await session.getMerchantSites(1008136911);
```

```csharp
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(1008136911);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1008136911,
  "name": "l",
  "host": "fAzyg",
  "images": [
    {
      "LBuGDMtBgJTO": "wT5v}aOm7v",
      "STGqDDZbFRys": 40,
      "bEqSFWFLCRUb": false
    },
    {
      "fpbKdonNMAUY": "$N8)#m2qj",
      "lQAMwGAJBzhK": 98,
      "SPJsvVLdmMCI": false
    },
    {
      "TnvukKXMDeYo": "r/P,K!(SsEXT[[+^s",
      "dcVJjBMeViZc": 98,
      "ihUFwgKXXyMK": false
    }
  ],
  "mfa": false,
  "tags": "tgszAyXzeYA",
  "quick_start": false,
  "login": {
    "qjeyAjeimCiA": "f1S_/-xLi!X$j[$^Rpb",
    "QhQdyyHOitkW": 9,
    "AvhbrmfBxCUj": false
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

**Example GET request path:**<br>`/merchant_sites/1008136911`

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
https://api.INSTANCE.cardsavr.io/notifications/1096844547
```

```javascript
const notifications = await session.getNotifications(1096844547);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(1096844547);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1096844547,
  "name": "MmOBrhUyDMzvbSpUjvFJuByTPeOuXIaiLgcILTsGsGpNfdtINiXlDwICxBFjPUQ",
  "type": "email",
  "config": {
    "NrBGRzBuKdGK": "9+O,zw9a/yW0qVb(hR*",
    "WRrhiJxwyhik": 1,
    "uskAHgPUxjLX": true
  },
  "created_on": "1987-09-26T03:37:21.647Z",
  "last_updated_on": "1995-04-21T09:34:23.636Z",
  "financial_institution_id": 1379732361
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

**Example GET request path:**<br>`/notifications/1096844547`

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
  "financial_institution_id": 1379732361,
  "name": "MmOBrhUyDMzvbSpUjvFJuByTPeOuXIaiLgcILTsGsGpNfdtINiXlDwICxBFjPUQ",
  "type": "email",
  "config": {
    "NrBGRzBuKdGK": "9+O,zw9a/yW0qVb(hR*",
    "WRrhiJxwyhik": 1,
    "uskAHgPUxjLX": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1379732361 },
	{ "name", "MmOBrhUyDMzvbSpUjvFJuByTPeOuXIaiLgcILTsGsGpNfdtINiXlDwICxBFjPUQ" },
	{ "type", "email" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":1379732361,\"name\":\"MmOBrhUyDMzvbSpUjvFJuByTPeOuXIaiLgcILTsGsGpNfdtINiXlDwICxBFjPUQ\",\"type\":\"email\",\"config\":{\"NrBGRzBuKdGK\":\"9+O,zw9a/yW0qVb(hR*\",\"WRrhiJxwyhik\":1,\"uskAHgPUxjLX\":true}}"
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
  "name": "ZcRlbnYSxpfIHfNmAwUAaRaSvBNWURjCUepELIESYlsEpQDlVCqqcNaVmdPSJHA",
  "type": "email",
  "config": {
    "MnMQNltMHFha": "pJ>1<hY*i",
    "lGTwMlGSLixv": 39,
    "uFTiCVDvOSMy": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "ZcRlbnYSxpfIHfNmAwUAaRaSvBNWURjCUepELIESYlsEpQDlVCqqcNaVmdPSJHA" },
	{ "type", "email" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```shell
curl -d "{\"name\":\"ZcRlbnYSxpfIHfNmAwUAaRaSvBNWURjCUepELIESYlsEpQDlVCqqcNaVmdPSJHA\",\"type\":\"email\",\"config\":{\"MnMQNltMHFha\":\"pJ>1<hY*i\",\"lGTwMlGSLixv\":39,\"uFTiCVDvOSMy\":true}}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/1096844547
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
https://api.INSTANCE.cardsavr.io/notifications/1096844547
```

```javascript
await session.deleteNotification(1096844547);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(1096844547);
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
https://api.INSTANCE.cardsavr.io/notification_results/1832599456
```

```javascript
const notificationresults = await session.getNotificationResults(1832599456);
```

```csharp
CardSavrResponse<NotificationResults> notificationresults = await session.GetNotificationResultsAsync(1832599456);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1832599456,
  "last_attempt_date": "1997-01-20T21:36:24.065Z",
  "fi_lookup_key": "HvswwMETFnQAiluhmLwokZhXCbOhgyMhkNsGPjTvnBskMVJhNeGBkhtrrXIoJoe",
  "username": "jsmith123",
  "status": "success",
  "attempts": 1895816034,
  "created_on": "1992-12-05T22:26:22.235Z",
  "last_updated_on": "2007-07-29T14:39:37.311Z",
  "notification_id": 1720903513
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

**Example GET request path:**<br>`/notification_results/1832599456`

### <a name="response-notification_result"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
last_attempt_date | date | Date of last attempt to post this notification result
fi_lookup_key | string | 
username | string | 
status | string | 
attempts | number | 
created_on | date | Date this notification result was created on
last_updated_on | date | Date this notification result was last updated on
notification_id | number (fk) | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- notification_ids
- last_attempt_date_min / last_attempt_date_max
- fi_lookup_keys
- usernames
- username
- status
- attempts
- attempts_min / attempts_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create notification result

```javascript
const notificationresult = await session.createNotificationResult({
  "notification_id": 1720903513,
  "fi_lookup_key": "HvswwMETFnQAiluhmLwokZhXCbOhgyMhkNsGPjTvnBskMVJhNeGBkhtrrXIoJoe",
  "username": "jsmith123",
  "status": "success",
  "attempts": 1895816034
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 1720903513 },
	{ "fi_lookup_key", "HvswwMETFnQAiluhmLwokZhXCbOhgyMhkNsGPjTvnBskMVJhNeGBkhtrrXIoJoe" },
	{ "username", "jsmith123" },
	{ "status", "success" },
	{ "attempts", 1895816034 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```shell
curl -d "{\"notification_id\":1720903513,\"fi_lookup_key\":\"HvswwMETFnQAiluhmLwokZhXCbOhgyMhkNsGPjTvnBskMVJhNeGBkhtrrXIoJoe\",\"username\":\"jsmith123\",\"status\":\"success\",\"attempts\":1895816034}"
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
username | string | yes
status | [string enum](#post-notification_result-1)* | yes
attempts | number | yes

See [notification result response attributes](#response-notification_result).

#### <a name="post-notification_result-1"></a>string enum*
- success
- failure


## Update notification result

```javascript
const notificationresult = await session.updateNotificationResult({
  "fi_lookup_key": "ShPXUgFVoHzqkMPCSFnzIFngfnnnsDAEXqYvXvvtzHDftuntXRYUikBMsLBRpXJ",
  "username": "jsmith123",
  "status": "success",
  "attempts": 1168602285
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "fi_lookup_key", "ShPXUgFVoHzqkMPCSFnzIFngfnnnsDAEXqYvXvvtzHDftuntXRYUikBMsLBRpXJ" },
	{ "username", "jsmith123" },
	{ "status", "success" },
	{ "attempts", 1168602285 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.UpdateNotificationResultAsync(body);
```

```shell
curl -d "{\"fi_lookup_key\":\"ShPXUgFVoHzqkMPCSFnzIFngfnnnsDAEXqYvXvvtzHDftuntXRYUikBMsLBRpXJ\",\"username\":\"jsmith123\",\"status\":\"success\",\"attempts\":1168602285}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notification_results/1832599456
```

### Path

PUT /notification_results OR /notification_results/{id}

### Description

Update a notification result and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
fi_lookup_key | string |
username | string |
status | [string enum](#post-notification_result-1)* |
attempts | number |

See [notification result response parameters](#response-notification_result).


## Delete notification result

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notification_results/1832599456
```

```javascript
await session.deleteNotificationResult(1832599456);
```

```csharp
CardSavrResponse<NotificationResult> notificationresult = await http.DeleteNotificationResultAsync(1832599456);
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1058327950
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(1058327950);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(1058327950);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1058327950,
  "card_id": 1756252723,
  "card_placement_result_id": "hBCqUwrWXVDqhGtyhmLOgytl",
  "status": "KILLED",
  "custom_data": {
    "QVBmTygANdhj": "epV2T^$*v8bYp[=g+",
    "LdGboSrmdXeR": 82,
    "ZPPLsElimdhu": false
  },
  "failure_reason": "JHrrpRvUCMVOLhBwxlomHIyd",
  "messaging_addresses": "cBUAKDxO",
  "current_state": "cOiiJHAdnzVuJmQusIaemxoWUTYNaQGkKyHLnxurrlMmmiyfCsbTjQaAPrkdedy",
  "do_not_queue": true,
  "user_is_present": true,
  "time_elapsed": 164187699,
  "job_ready_on": "2011-07-28T06:17:43.430Z",
  "started_on": "2000-07-10T01:52:35.437Z",
  "completed_on": "1998-01-29T16:57:04.426Z",
  "expiration_date": "1987-08-15T19:46:42.674Z",
  "created_on": "2008-06-24T07:25:14.529Z",
  "last_updated_on": "2020-01-27T12:48:59.878Z",
  "user_id": 274774299,
  "account_id": 1221898789
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/1058327950`

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
  "place_card_on_multiple_sites_job_id": 1394381155,
  "user_id": 274774299,
  "card_id": 1756252723,
  "account_id": 1221898789,
  "status": "KILLED",
  "custom_data": {
    "QVBmTygANdhj": "epV2T^$*v8bYp[=g+",
    "LdGboSrmdXeR": 82,
    "ZPPLsElimdhu": false
  },
  "failure_reason": "JHrrpRvUCMVOLhBwxlomHIyd",
  "current_state": "cOiiJHAdnzVuJmQusIaemxoWUTYNaQGkKyHLnxurrlMmmiyfCsbTjQaAPrkdedy",
  "do_not_queue": true,
  "user_is_present": true,
  "time_elapsed": 164187699,
  "started_on": "2000-07-10T01:52:35.437Z",
  "completed_on": "1998-01-29T16:57:04.426Z",
  "expiration_date": "1987-08-15T19:46:42.674Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "place_card_on_multiple_sites_job_id", 1394381155 },
	{ "user_id", 274774299 },
	{ "card_id", 1756252723 },
	{ "account_id", 1221898789 },
	{ "status", "KILLED" },
	{ "failure_reason", "JHrrpRvUCMVOLhBwxlomHIyd" },
	{ "current_state", "cOiiJHAdnzVuJmQusIaemxoWUTYNaQGkKyHLnxurrlMmmiyfCsbTjQaAPrkdedy" },
	{ "do_not_queue", true },
	{ "user_is_present", true },
	{ "time_elapsed", 164187699 },
	{ "started_on", "2000-07-10T01:52:35.437Z" },
	{ "completed_on", "1998-01-29T16:57:04.426Z" },
	{ "expiration_date", "1987-08-15T19:46:42.674Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"place_card_on_multiple_sites_job_id\":1394381155,\"user_id\":274774299,\"card_id\":1756252723,\"account_id\":1221898789,\"status\":\"KILLED\",\"custom_data\":{\"QVBmTygANdhj\":\"epV2T^$*v8bYp[=g+\",\"LdGboSrmdXeR\":82,\"ZPPLsElimdhu\":false},\"failure_reason\":\"JHrrpRvUCMVOLhBwxlomHIyd\",\"current_state\":\"cOiiJHAdnzVuJmQusIaemxoWUTYNaQGkKyHLnxurrlMmmiyfCsbTjQaAPrkdedy\",\"do_not_queue\":true,\"user_is_present\":true,\"time_elapsed\":164187699,\"started_on\":\"2000-07-10T01:52:35.437Z\",\"completed_on\":\"1998-01-29T16:57:04.426Z\",\"expiration_date\":\"1987-08-15T19:46:42.674Z\"}"
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
card_id | number | no
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
- LOGIN_SUBMITTED
- PENDING_CREDS
- PENDING_NEWCREDS
- PENDING_CARD
- LOGIN_RESUBMITTED
- PENDING_TFA
- UPDATING
- QUEUED
- NOT_QUEUED_BR
- CANCEL_REQUESTED
- CANCELLED
- CANCELLED_QUICKSTART
- ABANDONED
- ABANDONED_QUICKSTART
- KILLED
- BILLED_THROUGH_DISNEY_PLUS
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
  "card_id": 1375777176,
  "status": "REQUESTED",
  "custom_data": {
    "npdunkuArDlW": "TU*J=5JZ0)a@b]2<vP",
    "RqtuweqJneQR": 2,
    "FHUsYeOuHXHq": false
  },
  "failure_reason": "fuVKvtOaB",
  "current_state": "CIkFXGOkGXYdgtmsLFTGZpNigGGEbwsXmJRSnOWDPgfCuDSqXErJSzuyPgdzEqm",
  "do_not_queue": true,
  "user_is_present": true,
  "time_elapsed": 1938106904,
  "started_on": "2008-11-29T05:54:52.063Z",
  "completed_on": "2000-09-07T07:58:21.504Z",
  "expiration_date": "2002-04-30T03:58:24.475Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 1375777176 },
	{ "status", "REQUESTED" },
	{ "failure_reason", "fuVKvtOaB" },
	{ "current_state", "CIkFXGOkGXYdgtmsLFTGZpNigGGEbwsXmJRSnOWDPgfCuDSqXErJSzuyPgdzEqm" },
	{ "do_not_queue", true },
	{ "user_is_present", true },
	{ "time_elapsed", 1938106904 },
	{ "started_on", "2008-11-29T05:54:52.063Z" },
	{ "completed_on", "2000-09-07T07:58:21.504Z" },
	{ "expiration_date", "2002-04-30T03:58:24.475Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"card_id\":1375777176,\"status\":\"REQUESTED\",\"custom_data\":{\"npdunkuArDlW\":\"TU*J=5JZ0)a@b]2<vP\",\"RqtuweqJneQR\":2,\"FHUsYeOuHXHq\":false},\"failure_reason\":\"fuVKvtOaB\",\"current_state\":\"CIkFXGOkGXYdgtmsLFTGZpNigGGEbwsXmJRSnOWDPgfCuDSqXErJSzuyPgdzEqm\",\"do_not_queue\":true,\"user_is_present\":true,\"time_elapsed\":1938106904,\"started_on\":\"2008-11-29T05:54:52.063Z\",\"completed_on\":\"2000-09-07T07:58:21.504Z\",\"expiration_date\":\"2002-04-30T03:58:24.475Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1058327950
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1058327950
```

```javascript
await session.deleteSingleSiteJob(1058327950);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(1058327950);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [single-site job response parameters](#response-place_card_on_single_site_job).

