
# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1897418321
```

```javascript
const accounts = await session.getAccounts(1897418321);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(1897418321);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1897418321,
  "last_card_placed_id": 1537206994,
  "last_login": "1984-01-09T19:19:26.639Z",
  "last_password_update": "1983-08-04T03:30:00.593Z",
  "last_saved_card": "1991-06-16T03:29:30.337Z",
  "created_on": "1978-09-15T18:40:00.397Z",
  "last_updated_on": "2012-10-21T06:19:50.697Z",
  "cardholder_id": 1801944937,
  "merchant_site_id": 1491797886
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

**Example GET request path:**<br>`/cardsavr_accounts/1897418321`

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
  "cardholder_id": 1801944937,
  "merchant_site_id": 1491797886,
  "last_card_placed_id": 1537206994,
  "username": "jsmith123",
  "username_hash": "CaGCBLscifQGQGfhiDnaWEMpvogsmhmPSYOfoAZJHQUTjDzsFBiKtVWWSzz",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1801944937 },
	{ "merchant_site_id", 1491797886 },
	{ "last_card_placed_id", 1537206994 },
	{ "username", "jsmith123" },
	{ "username_hash", "CaGCBLscifQGQGfhiDnaWEMpvogsmhmPSYOfoAZJHQUTjDzsFBiKtVWWSzz" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":1801944937,\"merchant_site_id\":1491797886,\"last_card_placed_id\":1537206994,\"username\":\"jsmith123\",\"username_hash\":\"CaGCBLscifQGQGfhiDnaWEMpvogsmhmPSYOfoAZJHQUTjDzsFBiKtVWWSzz\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
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
username_hash | string | no
password | string | no

See [account response attributes](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username, username_hash and password when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Update account

```javascript
const account = await session.updateAccount({
  "last_card_placed_id": 2017104561,
  "username": "jsmith123",
  "username_hash": "fiIEgiPMzGbwvyIubKZoIPDGZSHUDRglaqMyNPalKlpjFRGLshHNrkHsnAL",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 2017104561 },
	{ "username", "jsmith123" },
	{ "username_hash", "fiIEgiPMzGbwvyIubKZoIPDGZSHUDRglaqMyNPalKlpjFRGLshHNrkHsnAL" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"last_card_placed_id\":2017104561,\"username\":\"jsmith123\",\"username_hash\":\"fiIEgiPMzGbwvyIubKZoIPDGZSHUDRglaqMyNPalKlpjFRGLshHNrkHsnAL\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1897418321
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
username_hash | string |
password | string |

See [account response parameters](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username, username_hash and password when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Delete account

```shell
curl -X DELETE
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1897418321
```

```javascript
await session.deleteAccount(1897418321, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(1897418321, CARDHOLDER_SAFE_KEY);
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/127215413
```

```javascript
const addresses = await session.getAddresses(127215413);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(127215413);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 127215413,
  "address1": "EpYygvqWkvrufovcBoEbupUhSFBLvYdsRsBHttHqoRDcFDjycGywHqIXsehTQPPVKAUpRnyluohkQxcbaDeBhdDhhCyHfTdighy",
  "address2": "EtmvEgAGOYkwYiWGCwFZjoNimTARwnYQBMNEMWYdfjronvUPgucCNMuWOfbVWsUYSLndRLSAvYAgkyIttxcXxrgAbfuPIYNzrAW",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "oxUnPNTwMzRfGW",
  "created_on": "2010-06-18T04:39:01.483Z",
  "last_updated_on": "1970-11-16T13:14:38.648Z",
  "cardholder_id": 473758669
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

**Example GET request path:**<br>`/cardsavr_addresses/127215413`

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
  "cardholder_id": 473758669,
  "address1": "EpYygvqWkvrufovcBoEbupUhSFBLvYdsRsBHttHqoRDcFDjycGywHqIXsehTQPPVKAUpRnyluohkQxcbaDeBhdDhhCyHfTdighy",
  "address2": "EtmvEgAGOYkwYiWGCwFZjoNimTARwnYQBMNEMWYdfjronvUPgucCNMuWOfbVWsUYSLndRLSAvYAgkyIttxcXxrgAbfuPIYNzrAW",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "oxUnPNTwMzRfGW"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 473758669 },
	{ "address1", "EpYygvqWkvrufovcBoEbupUhSFBLvYdsRsBHttHqoRDcFDjycGywHqIXsehTQPPVKAUpRnyluohkQxcbaDeBhdDhhCyHfTdighy" },
	{ "address2", "EtmvEgAGOYkwYiWGCwFZjoNimTARwnYQBMNEMWYdfjronvUPgucCNMuWOfbVWsUYSLndRLSAvYAgkyIttxcXxrgAbfuPIYNzrAW" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "phone_number", "oxUnPNTwMzRfGW" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```shell
curl -d "{\"cardholder_id\":473758669,\"address1\":\"EpYygvqWkvrufovcBoEbupUhSFBLvYdsRsBHttHqoRDcFDjycGywHqIXsehTQPPVKAUpRnyluohkQxcbaDeBhdDhhCyHfTdighy\",\"address2\":\"EtmvEgAGOYkwYiWGCwFZjoNimTARwnYQBMNEMWYdfjronvUPgucCNMuWOfbVWsUYSLndRLSAvYAgkyIttxcXxrgAbfuPIYNzrAW\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"phone_number\":\"oxUnPNTwMzRfGW\"}"
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
  "address1": "jJAeMtcGSqQKsruXkkHdtFWzouUPagycfQoYHLOOtAigTbcTYqfuKiDRMDjKXHfMFeEBTYMCXLFhSaRNcGDtTnejEVBqtVRWlvM",
  "address2": "unlEmGFUtPHeygvPozGzrihSHdRVVGUtFXecOuFQJbymseLKpPVtDgnmiXYRpDETYGOEjudzXpJfCYcyqTYymvOTTqRBTMBGkRM",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "OxHUAiZfNCGrw"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "jJAeMtcGSqQKsruXkkHdtFWzouUPagycfQoYHLOOtAigTbcTYqfuKiDRMDjKXHfMFeEBTYMCXLFhSaRNcGDtTnejEVBqtVRWlvM" },
	{ "address2", "unlEmGFUtPHeygvPozGzrihSHdRVVGUtFXecOuFQJbymseLKpPVtDgnmiXYRpDETYGOEjudzXpJfCYcyqTYymvOTTqRBTMBGkRM" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "phone_number", "OxHUAiZfNCGrw" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```shell
curl -d "{\"address1\":\"jJAeMtcGSqQKsruXkkHdtFWzouUPagycfQoYHLOOtAigTbcTYqfuKiDRMDjKXHfMFeEBTYMCXLFhSaRNcGDtTnejEVBqtVRWlvM\",\"address2\":\"unlEmGFUtPHeygvPozGzrihSHdRVVGUtFXecOuFQJbymseLKpPVtDgnmiXYRpDETYGOEjudzXpJfCYcyqTYymvOTTqRBTMBGkRM\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"phone_number\":\"OxHUAiZfNCGrw\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/127215413
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/127215413
```

```javascript
await session.deleteAddress(127215413);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(127215413);
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1227245615
```

```javascript
const bins = await session.getBins(1227245615);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(1227245615);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1227245615,
  "financial_institution_id": 386517225,
  "custom_data": {
    "rmcosfKUMKNQ": "%8e@nwg5r!ks",
    "uqLYSmPpcKpD": 63,
    "eTpEqnIAtUnY": true
  },
  "created_on": "1975-11-06T14:16:54.674Z",
  "last_updated_on": "1975-08-13T02:57:22.928Z",
  "bank_identification_number": "15730222"
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

**Example GET request path:**<br>`/cardsavr_bins/1227245615`

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
  "financial_institution_id": 386517225,
  "bank_identification_number": "15730222",
  "custom_data": {
    "rmcosfKUMKNQ": "%8e@nwg5r!ks",
    "uqLYSmPpcKpD": 63,
    "eTpEqnIAtUnY": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 386517225 },
	{ "bank_identification_number", "15730222" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":386517225,\"bank_identification_number\":\"15730222\",\"custom_data\":{\"rmcosfKUMKNQ\":\"%8e@nwg5r!ks\",\"uqLYSmPpcKpD\":63,\"eTpEqnIAtUnY\":true}}"
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
  "financial_institution_id": 2136851029,
  "custom_data": {
    "YBNqAbTqedLT": "dNoZ&Y,&j",
    "IPNEjuazDJpE": 56,
    "vPAOrIjzyVDi": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 2136851029 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":2136851029,\"custom_data\":{\"YBNqAbTqedLT\":\"dNoZ&Y,&j\",\"IPNEjuazDJpE\":56,\"vPAOrIjzyVDi\":false}}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1227245615
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1227245615
```

```javascript
await session.deleteBin(1227245615);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(1227245615);
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/438675393
```

```javascript
const cards = await session.getCards(438675393);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(438675393);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 438675393,
  "address_id": 2057867321,
  "bin_id": 674603899,
  "name_on_card": "Joe C Smith",
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "created_on": "1984-08-24T22:07:29.154Z",
  "last_updated_on": "1989-04-10T07:16:14.176Z",
  "expiration_month": 12,
  "expiration_year": 24,
  "cardholder_id": 1745700563,
  "par": "EDZxlWUwbpbpTSXvIuovxvCepPPeE"
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

**Example GET request path:**<br>`/cardsavr_cards/438675393`

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
  "cardholder_id": 1745700563,
  "address_id": 2057867321,
  "bin_id": 674603899,
  "par": "EDZxlWUwbpbpTSXvIuovxvCepPPeE",
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
	{ "cardholder_id", 1745700563 },
	{ "address_id", 2057867321 },
	{ "bin_id", 674603899 },
	{ "par", "EDZxlWUwbpbpTSXvIuovxvCepPPeE" },
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

```shell
curl -d "{\"cardholder_id\":1745700563,\"address_id\":2057867321,\"bin_id\":674603899,\"par\":\"EDZxlWUwbpbpTSXvIuovxvCepPPeE\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\",\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
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
  "address_id": 1258603618,
  "bin_id": 626858606,
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
	{ "address_id", 1258603618 },
	{ "bin_id", 626858606 },
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

```shell
curl -d "{\"address_id\":1258603618,\"bin_id\":626858606,\"name_on_card\":\"Joe C Smith\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/438675393
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
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/438675393
```

```javascript
await session.deleteCard(438675393, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(438675393, CARDHOLDER_SAFE_KEY);
```

### Path

DELETE /cardsavr_cards/{id}

### Description

Delete a card and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [card response parameters](#response-cardsavr_card).

<aside class="notice">The cardholder_safe_key header is required to delete cards for third party managed safe key stores.</aside>


# Cardholders
Entities which represent end-users/cardholders.
## Get cardholder

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardholders/1369194926
```

```javascript
const cardholders = await session.getCardholders(1369194926);
```

```csharp
CardSavrResponse<Cardholders> cardholders = await session.GetCardholdersAsync(1369194926);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1369194926,
  "financial_institution_id": 270760466,
  "agent_session_id": "GFYMq",
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "lWycEdcZhCVVyjHEgkZoYWEEChbAP",
  "custom_data": {
    "cdCACzRqLcOp": "FvByrQE&0j(,#Y4w]^!y",
    "CdfwPLzAFZqZ": 27,
    "ZwGUvUoRxYTf": true
  },
  "created_on": "1983-05-02T07:24:44.279Z",
  "last_updated_on": "1985-12-01T08:44:03.521Z",
  "cuid": "dvbYvqYQnjjuNR"
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

**Example GET request path:**<br>`/cardholders/1369194926`

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
  "financial_institution_id": 270760466,
  "cuid": "dvbYvqYQnjjuNR",
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "lWycEdcZhCVVyjHEgkZoYWEEChbAP",
  "custom_data": {
    "cdCACzRqLcOp": "FvByrQE&0j(,#Y4w]^!y",
    "CdfwPLzAFZqZ": 27,
    "ZwGUvUoRxYTf": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 270760466 },
	{ "cuid", "dvbYvqYQnjjuNR" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "lWycEdcZhCVVyjHEgkZoYWEEChbAP" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":270760466,\"cuid\":\"dvbYvqYQnjjuNR\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"lWycEdcZhCVVyjHEgkZoYWEEChbAP\",\"custom_data\":{\"cdCACzRqLcOp\":\"FvByrQE&0j(,#Y4w]^!y\",\"CdfwPLzAFZqZ\":27,\"ZwGUvUoRxYTf\":true}}"
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
  "financial_institution_id": 2070919138,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "MpRHCcsfjYFxnnoahTskqlIjtzMGTk",
  "custom_data": {
    "qRiCzOnCyDOj": "NCY[ja~N6lzca",
    "OfbftGMMwoQM": 48,
    "pNovjupBGgJS": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 2070919138 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "MpRHCcsfjYFxnnoahTskqlIjtzMGTk" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":2070919138,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"MpRHCcsfjYFxnnoahTskqlIjtzMGTk\",\"custom_data\":{\"qRiCzOnCyDOj\":\"NCY[ja~N6lzca\",\"OfbftGMMwoQM\":48,\"pNovjupBGgJS\":false}}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardholders/1369194926
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
https://api.INSTANCE.cardsavr.io/cardholders/1369194926
```

```javascript
await session.deleteCardholder(1369194926);
```

```csharp
CardSavrResponse<Cardholder> cardholder = await http.DeleteCardholderAsync(1369194926);
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/311858371
```

```javascript
const users = await session.getUsers(311858371);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(311858371);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 311858371,
  "financial_institution_id": 435198278,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1980-05-26T09:06:01.271Z",
  "is_locked": false,
  "password_lifetime": 309,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "cardholder_agent",
  "custom_data": {
    "CJQVSOhCqvEQ": "y16vTRyQs8*CSIMmc~LA}Yk6*Ypdi#r",
    "KTzgPIDagGwn": 100,
    "UPMbBVYuHAHd": false
  },
  "next_rotation_on": "2000-05-23T21:42:49.249Z",
  "created_on": "1985-04-24T14:52:03.789Z",
  "last_updated_on": "1996-04-04T13:13:41.155Z",
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

**Example GET request path:**<br>`/cardsavr_users/311858371`

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
  "financial_institution_id": 435198278,
  "username": "jsmith123",
  "last_password": "m4KXzZ2xjE9q4mnIMIcOdmqTfziooEtyVFJtfBcNeKU=",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "next_password": "XYfktYHgXRZdNWww/uAA6s2cPXhM73Ep+/u2GHklnQ8=",
  "expired_password_1": "uhpZY2YasWRM/9cCD/GL8U8kB2c4vfn+8dUFlkIDI7c=",
  "expired_password_2": "ZrlaeyKW/JwFqPETWkVgiOUcVbeaXigndcFv1OEvOno=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 309,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "cardholder_agent",
  "custom_data": {
    "CJQVSOhCqvEQ": "y16vTRyQs8*CSIMmc~LA}Yk6*Ypdi#r",
    "KTzgPIDagGwn": 100,
    "UPMbBVYuHAHd": false
  },
  "next_rotation_on": "2000-05-23T21:42:49.249Z"
}, NEW_CARDHODLER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 435198278 },
	{ "username", "jsmith123" },
	{ "last_password", "m4KXzZ2xjE9q4mnIMIcOdmqTfziooEtyVFJtfBcNeKU=" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "next_password", "XYfktYHgXRZdNWww/uAA6s2cPXhM73Ep+/u2GHklnQ8=" },
	{ "expired_password_1", "uhpZY2YasWRM/9cCD/GL8U8kB2c4vfn+8dUFlkIDI7c=" },
	{ "expired_password_2", "ZrlaeyKW/JwFqPETWkVgiOUcVbeaXigndcFv1OEvOno=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 309 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "cardholder_agent" },
	{ "next_rotation_on", "2000-05-23T21:42:49.249Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, NEW_CARDHODLER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":435198278,\"username\":\"jsmith123\",\"last_password\":\"m4KXzZ2xjE9q4mnIMIcOdmqTfziooEtyVFJtfBcNeKU=\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"next_password\":\"XYfktYHgXRZdNWww/uAA6s2cPXhM73Ep+/u2GHklnQ8=\",\"expired_password_1\":\"uhpZY2YasWRM/9cCD/GL8U8kB2c4vfn+8dUFlkIDI7c=\",\"expired_password_2\":\"ZrlaeyKW/JwFqPETWkVgiOUcVbeaXigndcFv1OEvOno=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":309,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"cardholder_agent\",\"custom_data\":{\"CJQVSOhCqvEQ\":\"y16vTRyQs8*CSIMmc~LA}Yk6*Ypdi#r\",\"KTzgPIDagGwn\":100,\"UPMbBVYuHAHd\":false},\"next_rotation_on\":\"2000-05-23T21:42:49.249Z\"}"
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
custom_data | object | no
next_rotation_on | date | no

See [user response attributes](#response-cardsavr_user).

#### <a name="post-cardsavr_user-1"></a>string enum*
- admin
- cardholder_agent
- customer_agent
- swch_agent

<aside class="notice">Update calls to /cardsavr_users require the cardholder's personal cardholder_safe_key header to encrypt and save the safe when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Update user

```javascript
const user = await session.updateUser({
  "financial_institution_id": 1774283853,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 147,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "admin",
  "custom_data": {
    "AEBTnIYzPFoF": "Fzf^#-h$~3LmCT5]%q}nh=l%&L[k!",
    "lcCghKXffchd": 2,
    "XEZKzgqFnLNa": true
  },
  "next_rotation_on": "1989-02-08T06:15:15.736Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1774283853 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 147 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "admin" },
	{ "next_rotation_on", "1989-02-08T06:15:15.736Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":1774283853,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":147,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"admin\",\"custom_data\":{\"AEBTnIYzPFoF\":\"Fzf^#-h$~3LmCT5]%q}nh=l%&L[k!\",\"lcCghKXffchd\":2,\"XEZKzgqFnLNa\":true},\"next_rotation_on\":\"1989-02-08T06:15:15.736Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/311858371
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

<aside class="notice">Update calls to /cardsavr_users require the cardholder's current cardholder-safe-key, and the new new-cardholder-safe-key headers when rotating the cardholder_safe_key.</aside>

## Delete user

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/311858371
```

```javascript
await session.deleteUser(311858371);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(311858371);
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
https://api.INSTANCE.cardsavr.io/financial_institutions/1459428804
```

```javascript
const financialinstitutions = await session.getFinancialInstitutions(1459428804);
```

```csharp
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(1459428804);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1459428804,
  "name": "GuTiQUnAAyXdvboSEgljpaJZfOgTfSaQlEWXAZvwzqlRyTlcYzZbcwZvkcibevI",
  "description": "PYoqDyijkcWB",
  "lookup_key": "MYOGDOyzZVuHNJCbXXcJgOEpQMsYtsqitDzhrOrXnkeafwCxfwCRdTBQbievOqj",
  "alternate_lookup_key": "QZJiynByuHynocozXGMhYtfvFKaOPiOypjtlaSyLzGQuvhkiLjmrPUecBeHQrBr",
  "config": {
    "sOjxDPPSWUbK": "z)+3hIPeh5W*J_x>k&^^uYt5QmwS9",
    "yyWSxmIUyxeA": 96,
    "XqiqQfqiOSnx": false
  },
  "email_config": {
    "ApZdWJOvhbuF": "!Xur1U^k]N",
    "GYqUmxpXIaRa": 89,
    "TFDWMUKglqkM": true
  },
  "created_on": "1972-04-24T00:51:07.526Z",
  "last_updated_on": "1973-08-05T06:24:33.241Z"
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

**Example GET request path:**<br>`/financial_institutions/1459428804`

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
  "name": "GuTiQUnAAyXdvboSEgljpaJZfOgTfSaQlEWXAZvwzqlRyTlcYzZbcwZvkcibevI",
  "description": "PYoqDyijkcWB",
  "lookup_key": "MYOGDOyzZVuHNJCbXXcJgOEpQMsYtsqitDzhrOrXnkeafwCxfwCRdTBQbievOqj",
  "alternate_lookup_key": "QZJiynByuHynocozXGMhYtfvFKaOPiOypjtlaSyLzGQuvhkiLjmrPUecBeHQrBr",
  "config": {
    "sOjxDPPSWUbK": "z)+3hIPeh5W*J_x>k&^^uYt5QmwS9",
    "yyWSxmIUyxeA": 96,
    "XqiqQfqiOSnx": false
  },
  "email_config": {
    "ApZdWJOvhbuF": "!Xur1U^k]N",
    "GYqUmxpXIaRa": 89,
    "TFDWMUKglqkM": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "GuTiQUnAAyXdvboSEgljpaJZfOgTfSaQlEWXAZvwzqlRyTlcYzZbcwZvkcibevI" },
	{ "description", "PYoqDyijkcWB" },
	{ "lookup_key", "MYOGDOyzZVuHNJCbXXcJgOEpQMsYtsqitDzhrOrXnkeafwCxfwCRdTBQbievOqj" },
	{ "alternate_lookup_key", "QZJiynByuHynocozXGMhYtfvFKaOPiOypjtlaSyLzGQuvhkiLjmrPUecBeHQrBr" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"GuTiQUnAAyXdvboSEgljpaJZfOgTfSaQlEWXAZvwzqlRyTlcYzZbcwZvkcibevI\",\"description\":\"PYoqDyijkcWB\",\"lookup_key\":\"MYOGDOyzZVuHNJCbXXcJgOEpQMsYtsqitDzhrOrXnkeafwCxfwCRdTBQbievOqj\",\"alternate_lookup_key\":\"QZJiynByuHynocozXGMhYtfvFKaOPiOypjtlaSyLzGQuvhkiLjmrPUecBeHQrBr\",\"config\":{\"sOjxDPPSWUbK\":\"z)+3hIPeh5W*J_x>k&^^uYt5QmwS9\",\"yyWSxmIUyxeA\":96,\"XqiqQfqiOSnx\":false},\"email_config\":{\"ApZdWJOvhbuF\":\"!Xur1U^k]N\",\"GYqUmxpXIaRa\":89,\"TFDWMUKglqkM\":true}}"
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
  "name": "YoLgOfoCKwVrUHfcqGTDFNCFjMkEIGSwiWfGEIdrFYvNYWyhInaZYbBDjzEcwYz",
  "description": "TDbBUDJUrwh",
  "lookup_key": "oDbIXOydxBTGNPZSJftuGJlfRSsqREBgKbfDNBgjahOvHMwTmVtaZNnPBpQOMlr",
  "alternate_lookup_key": "nfGsIZDyPXtOiLvATTGZIUxydxsEhagEyJPLGyQXovwmliubWgmyhSycmPSdace",
  "config": {
    "yqwgQhsSoSXO": "&w-hS+Y*iz}_cpllym&-<b-9JN/b",
    "NYOgXVXjEgPa": 13,
    "gASoOmIRFQXG": false
  },
  "email_config": {
    "ZKpOCvHXHZkk": "*)xHK%c)$_@v%6m,MV5=/&4I479FsI",
    "GnFSxMAcCAEZ": 11,
    "iWLDDUwyhrfh": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "YoLgOfoCKwVrUHfcqGTDFNCFjMkEIGSwiWfGEIdrFYvNYWyhInaZYbBDjzEcwYz" },
	{ "description", "TDbBUDJUrwh" },
	{ "lookup_key", "oDbIXOydxBTGNPZSJftuGJlfRSsqREBgKbfDNBgjahOvHMwTmVtaZNnPBpQOMlr" },
	{ "alternate_lookup_key", "nfGsIZDyPXtOiLvATTGZIUxydxsEhagEyJPLGyQXovwmliubWgmyhSycmPSdace" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"YoLgOfoCKwVrUHfcqGTDFNCFjMkEIGSwiWfGEIdrFYvNYWyhInaZYbBDjzEcwYz\",\"description\":\"TDbBUDJUrwh\",\"lookup_key\":\"oDbIXOydxBTGNPZSJftuGJlfRSsqREBgKbfDNBgjahOvHMwTmVtaZNnPBpQOMlr\",\"alternate_lookup_key\":\"nfGsIZDyPXtOiLvATTGZIUxydxsEhagEyJPLGyQXovwmliubWgmyhSycmPSdace\",\"config\":{\"yqwgQhsSoSXO\":\"&w-hS+Y*iz}_cpllym&-<b-9JN/b\",\"NYOgXVXjEgPa\":13,\"gASoOmIRFQXG\":false},\"email_config\":{\"ZKpOCvHXHZkk\":\"*)xHK%c)$_@v%6m,MV5=/&4I479FsI\",\"GnFSxMAcCAEZ\":11,\"iWLDDUwyhrfh\":true}}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/1459428804
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
https://api.INSTANCE.cardsavr.io/financial_institutions/1459428804
```

```javascript
await session.deleteFinancialInstitution(1459428804);
```

```csharp
CardSavrResponse<FinancialInstitution> financialinstitution = await http.DeleteFinancialInstitutionAsync(1459428804);
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
https://api.INSTANCE.cardsavr.io/integrators/1718887636
```

```javascript
const integrators = await session.getIntegrators(1718887636);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(1718887636);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1718887636,
  "name": "cqksRXnOAjoBnkzZFyYdUNyhapLKJMSxwxyrdTlRXUwkLExOM",
  "integrator_type": "swch_internal",
  "description": "flziklitY",
  "last_key": "3XU+oWn0EewG7t4Z8J9FyJqMU1UPnTdULEhkhJylsSM=",
  "current_key": "tcyeyGaEkKLh2OkHTCmXKkY1sl/7KwxOo139Lo7vetA=",
  "next_key": "I772ZEA6OWvPydlfziTZL17hIYds3cRqk55bBsGoXv0=",
  "key_lifetime": 246,
  "next_rotation_on": "1984-06-20T20:53:08.707Z",
  "created_on": "1999-02-23T19:39:05.811Z",
  "last_updated_on": "1985-03-09T21:55:24.462Z"
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

**Example GET request path:**<br>`/integrators/1718887636`

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
  "name": "cqksRXnOAjoBnkzZFyYdUNyhapLKJMSxwxyrdTlRXUwkLExOM",
  "integrator_type": "swch_internal",
  "description": "flziklitY",
  "last_key": "3XU+oWn0EewG7t4Z8J9FyJqMU1UPnTdULEhkhJylsSM=",
  "current_key": "tcyeyGaEkKLh2OkHTCmXKkY1sl/7KwxOo139Lo7vetA=",
  "next_key": "I772ZEA6OWvPydlfziTZL17hIYds3cRqk55bBsGoXv0=",
  "key_lifetime": 246,
  "next_rotation_on": "1984-06-20T20:53:08.707Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "cqksRXnOAjoBnkzZFyYdUNyhapLKJMSxwxyrdTlRXUwkLExOM" },
	{ "integrator_type", "swch_internal" },
	{ "description", "flziklitY" },
	{ "last_key", "3XU+oWn0EewG7t4Z8J9FyJqMU1UPnTdULEhkhJylsSM=" },
	{ "current_key", "tcyeyGaEkKLh2OkHTCmXKkY1sl/7KwxOo139Lo7vetA=" },
	{ "next_key", "I772ZEA6OWvPydlfziTZL17hIYds3cRqk55bBsGoXv0=" },
	{ "key_lifetime", 246 },
	{ "next_rotation_on", "1984-06-20T20:53:08.707Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"cqksRXnOAjoBnkzZFyYdUNyhapLKJMSxwxyrdTlRXUwkLExOM\",\"integrator_type\":\"swch_internal\",\"description\":\"flziklitY\",\"last_key\":\"3XU+oWn0EewG7t4Z8J9FyJqMU1UPnTdULEhkhJylsSM=\",\"current_key\":\"tcyeyGaEkKLh2OkHTCmXKkY1sl/7KwxOo139Lo7vetA=\",\"next_key\":\"I772ZEA6OWvPydlfziTZL17hIYds3cRqk55bBsGoXv0=\",\"key_lifetime\":246,\"next_rotation_on\":\"1984-06-20T20:53:08.707Z\"}"
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
  "name": "diyaQrRDOpZsEdFsofJBYOGgiZmEsiamEgIDXtGsiEewqtzGE",
  "integrator_type": "swch_internal",
  "description": "EaOPbDbRDjOMuPZOjdPRKCs",
  "last_key": "KNtMYXKuecFPF5J2erJe2GP0A23z0h1Jj/P/uBSi828=",
  "current_key": "lbh3ir8UmYY/ACaysmGZwMTBcNORKf2G2CmrLyscpkg=",
  "next_key": "DfNLR0/ifiyPvzuIiwGGhl690EDELp2uNCkzrOsYyuA=",
  "key_lifetime": 93,
  "next_rotation_on": "1989-02-10T10:13:14.634Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "diyaQrRDOpZsEdFsofJBYOGgiZmEsiamEgIDXtGsiEewqtzGE" },
	{ "integrator_type", "swch_internal" },
	{ "description", "EaOPbDbRDjOMuPZOjdPRKCs" },
	{ "last_key", "KNtMYXKuecFPF5J2erJe2GP0A23z0h1Jj/P/uBSi828=" },
	{ "current_key", "lbh3ir8UmYY/ACaysmGZwMTBcNORKf2G2CmrLyscpkg=" },
	{ "next_key", "DfNLR0/ifiyPvzuIiwGGhl690EDELp2uNCkzrOsYyuA=" },
	{ "key_lifetime", 93 },
	{ "next_rotation_on", "1989-02-10T10:13:14.634Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"diyaQrRDOpZsEdFsofJBYOGgiZmEsiamEgIDXtGsiEewqtzGE\",\"integrator_type\":\"swch_internal\",\"description\":\"EaOPbDbRDjOMuPZOjdPRKCs\",\"last_key\":\"KNtMYXKuecFPF5J2erJe2GP0A23z0h1Jj/P/uBSi828=\",\"current_key\":\"lbh3ir8UmYY/ACaysmGZwMTBcNORKf2G2CmrLyscpkg=\",\"next_key\":\"DfNLR0/ifiyPvzuIiwGGhl690EDELp2uNCkzrOsYyuA=\",\"key_lifetime\":93,\"next_rotation_on\":\"1989-02-10T10:13:14.634Z\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/1718887636
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
https://api.INSTANCE.cardsavr.io/integrators/1718887636
```

```javascript
await session.deleteIntegrator(1718887636);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(1718887636);
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
https://api.INSTANCE.cardsavr.io/merchant_sites/1591524844
```

```javascript
const merchantsites = await session.getMerchantSites(1591524844);
```

```csharp
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(1591524844);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1591524844,
  "name": "EVwEfvuZjmFYSuZe",
  "host": "JymFWc",
  "images": [
    {
      "oocxkPgfRXlp": "6F4Zj<eZ8,v2fU",
      "WrLERUyufDWb": 62,
      "ftDAjyLnNnuv": true
    },
    {
      "coLnMRCApDGh": "4hMQ}LsV*v)1Y06gq-a~O9D",
      "UOKdxoTJrMko": 63,
      "hgpOeoIzveTL": false
    },
    {
      "bsmsqmerxyfP": "D8@*Gj7ecHMfkyMQBK3*<2#[Mo,",
      "NWBvUGsdxpkR": 38,
      "LgucztOCArke": true
    }
  ],
  "mfa": false,
  "tags": "hdahjGeUnEzmhnUJKcMcsIirA",
  "quick_start": false,
  "login": {
    "WZMoLIgripeE": "$S>VQ~8MAw$A{}05K]uEf%+31vr",
    "JxMfQnMyRWCH": 77,
    "pWYDhFeSCOEx": false
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

**Example GET request path:**<br>`/merchant_sites/1591524844`

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
https://api.INSTANCE.cardsavr.io/notifications/1321651775
```

```javascript
const notifications = await session.getNotifications(1321651775);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(1321651775);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1321651775,
  "name": "nRiYFUJyGoKTJsPCqdVJyWGGLXsPuVrVkJoSvTmkhnjiHiKAxNDtYXsGcAPCmev",
  "type": "webhook",
  "event": "session_complete",
  "config": {
    "scbYXXuglEfH": "Oc)9E=#~Mb5{LH,f@Onc",
    "LNEXeendAECf": 66,
    "akspRbEaaWeR": false
  },
  "html_template": "mcXItMkeJqZA",
  "text_template": "aMbAmtasxmPkPSbyEEdDwcgCpxz",
  "created_on": "1982-09-09T05:56:22.823Z",
  "last_updated_on": "1973-10-23T05:25:10.621Z",
  "financial_institution_id": 2081179247
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

**Example GET request path:**<br>`/notifications/1321651775`

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
  "financial_institution_id": 2081179247,
  "name": "nRiYFUJyGoKTJsPCqdVJyWGGLXsPuVrVkJoSvTmkhnjiHiKAxNDtYXsGcAPCmev",
  "type": "webhook",
  "event": "session_complete",
  "config": {
    "scbYXXuglEfH": "Oc)9E=#~Mb5{LH,f@Onc",
    "LNEXeendAECf": 66,
    "akspRbEaaWeR": false
  },
  "html_template": "mcXItMkeJqZA",
  "text_template": "aMbAmtasxmPkPSbyEEdDwcgCpxz"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 2081179247 },
	{ "name", "nRiYFUJyGoKTJsPCqdVJyWGGLXsPuVrVkJoSvTmkhnjiHiKAxNDtYXsGcAPCmev" },
	{ "type", "webhook" },
	{ "event", "session_complete" },
	{ "html_template", "mcXItMkeJqZA" },
	{ "text_template", "aMbAmtasxmPkPSbyEEdDwcgCpxz" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":2081179247,\"name\":\"nRiYFUJyGoKTJsPCqdVJyWGGLXsPuVrVkJoSvTmkhnjiHiKAxNDtYXsGcAPCmev\",\"type\":\"webhook\",\"event\":\"session_complete\",\"config\":{\"scbYXXuglEfH\":\"Oc)9E=#~Mb5{LH,f@Onc\",\"LNEXeendAECf\":66,\"akspRbEaaWeR\":false},\"html_template\":\"mcXItMkeJqZA\",\"text_template\":\"aMbAmtasxmPkPSbyEEdDwcgCpxz\"}"
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
  "name": "WniTQgRetSrNSUcbaqgBabpuzunMEamTmSqwrmjiUApIbuuGsEehtEVvoFPEMoD",
  "type": "email",
  "event": "session_complete",
  "config": {
    "soQAfyOrgeBE": "J$CkdwkH.G&kmap.kKu^fV+",
    "dhuqUpIyTezb": 31,
    "GplHCAOBBwFh": true
  },
  "html_template": "eVEOiZNxqASwS",
  "text_template": "LxynqBrsnPOmpfSkSllAcgMTjLddlD"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "WniTQgRetSrNSUcbaqgBabpuzunMEamTmSqwrmjiUApIbuuGsEehtEVvoFPEMoD" },
	{ "type", "email" },
	{ "event", "session_complete" },
	{ "html_template", "eVEOiZNxqASwS" },
	{ "text_template", "LxynqBrsnPOmpfSkSllAcgMTjLddlD" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```shell
curl -d "{\"name\":\"WniTQgRetSrNSUcbaqgBabpuzunMEamTmSqwrmjiUApIbuuGsEehtEVvoFPEMoD\",\"type\":\"email\",\"event\":\"session_complete\",\"config\":{\"soQAfyOrgeBE\":\"J$CkdwkH.G&kmap.kKu^fV+\",\"dhuqUpIyTezb\":31,\"GplHCAOBBwFh\":true},\"html_template\":\"eVEOiZNxqASwS\",\"text_template\":\"LxynqBrsnPOmpfSkSllAcgMTjLddlD\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/1321651775
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
https://api.INSTANCE.cardsavr.io/notifications/1321651775
```

```javascript
await session.deleteNotification(1321651775);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(1321651775);
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
https://api.INSTANCE.cardsavr.io/notification_results/739901312
```

```javascript
const notificationresults = await session.getNotificationResults(739901312);
```

```csharp
CardSavrResponse<NotificationResults> notificationresults = await session.GetNotificationResultsAsync(739901312);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 739901312,
  "last_attempt_date": "2017-12-03T02:36:00.318Z",
  "fi_lookup_key": "MaialmvodlAFOFlYPipumsQMjSLhXXDazvLeSnhydkCCnfbgScJpmrLDWkBgEFS",
  "cuid": "FeGNdwMAunQJSkPjUVmESiMlhagAz",
  "status": "failure",
  "attempts": 673250411,
  "notification_data": {
    "ezxpGpXLixjb": "CBMxd<Wb(f6npB133}GdF&Ke-/2jn",
    "PpvmgvpQlvhm": 64,
    "GyNrGaLmsySG": false
  },
  "created_on": "2008-04-02T20:37:57.236Z",
  "last_updated_on": "1991-06-02T02:27:11.613Z",
  "notification_id": 1419426953
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

**Example GET request path:**<br>`/notification_results/739901312`

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
  "notification_id": 1419426953,
  "fi_lookup_key": "MaialmvodlAFOFlYPipumsQMjSLhXXDazvLeSnhydkCCnfbgScJpmrLDWkBgEFS",
  "cuid": "FeGNdwMAunQJSkPjUVmESiMlhagAz",
  "status": "failure",
  "attempts": 673250411,
  "notification_data": {
    "ezxpGpXLixjb": "CBMxd<Wb(f6npB133}GdF&Ke-/2jn",
    "PpvmgvpQlvhm": 64,
    "GyNrGaLmsySG": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 1419426953 },
	{ "fi_lookup_key", "MaialmvodlAFOFlYPipumsQMjSLhXXDazvLeSnhydkCCnfbgScJpmrLDWkBgEFS" },
	{ "cuid", "FeGNdwMAunQJSkPjUVmESiMlhagAz" },
	{ "status", "failure" },
	{ "attempts", 673250411 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```shell
curl -d "{\"notification_id\":1419426953,\"fi_lookup_key\":\"MaialmvodlAFOFlYPipumsQMjSLhXXDazvLeSnhydkCCnfbgScJpmrLDWkBgEFS\",\"cuid\":\"FeGNdwMAunQJSkPjUVmESiMlhagAz\",\"status\":\"failure\",\"attempts\":673250411,\"notification_data\":{\"ezxpGpXLixjb\":\"CBMxd<Wb(f6npB133}GdF&Ke-/2jn\",\"PpvmgvpQlvhm\":64,\"GyNrGaLmsySG\":false}}"
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
  "fi_lookup_key": "JJDtdcMdWNEDqCJBOEhNBIBydcExoraefPiFmQsZVljQELMJIigzaqZBBZdEyOq",
  "cuid": "nc",
  "status": "success",
  "attempts": 1722689298,
  "notification_data": {
    "hikxrxsvZxUo": "t-hlI#5Rt4KQvka^{BN_x{3@/I0A+Vf",
    "CWUWbmujTBAX": 2,
    "UGiWgBqpJwMf": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "fi_lookup_key", "JJDtdcMdWNEDqCJBOEhNBIBydcExoraefPiFmQsZVljQELMJIigzaqZBBZdEyOq" },
	{ "cuid", "nc" },
	{ "status", "success" },
	{ "attempts", 1722689298 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.UpdateNotificationResultAsync(body);
```

```shell
curl -d "{\"fi_lookup_key\":\"JJDtdcMdWNEDqCJBOEhNBIBydcExoraefPiFmQsZVljQELMJIigzaqZBBZdEyOq\",\"cuid\":\"nc\",\"status\":\"success\",\"attempts\":1722689298,\"notification_data\":{\"hikxrxsvZxUo\":\"t-hlI#5Rt4KQvka^{BN_x{3@/I0A+Vf\",\"CWUWbmujTBAX\":2,\"UGiWgBqpJwMf\":true}}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notification_results/739901312
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
https://api.INSTANCE.cardsavr.io/notification_results/739901312
```

```javascript
await session.deleteNotificationResult(739901312);
```

```csharp
CardSavrResponse<NotificationResult> notificationresult = await http.DeleteNotificationResultAsync(739901312);
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/64957903
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(64957903);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(64957903);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 64957903,
  "card_id": 1197428942,
  "card_placement_result_id": "stCrlkqOPMxPZrPUW",
  "status": "TIMEOUT_CREDENTIALS",
  "custom_data": {
    "uVlEKlGXeYAt": ")r",
    "sFWRZfdiJoEF": 67,
    "lgYHhXdsoCio": false
  },
  "failure_reason": "NwMJBycgTUyurEBpXkZIwAUCDeGCPdu",
  "messaging_addresses": "BIDnNIPUtTiPxvtLmDfCRiTnzoUh",
  "current_state": "OzxGygbBqrrLJJgYhzqsSJcuDrQsXSQRrVxQEwFAQFhrFtebbINqypkbuSBeCRx",
  "notification_sent": true,
  "time_elapsed": 1543256029,
  "run_count": 1066485078,
  "job_ready_on": "1995-02-01T19:37:34.126Z",
  "started_on": "1984-06-25T04:31:40.975Z",
  "completed_on": "1980-05-16T14:31:39.064Z",
  "expiration_date": "1970-05-22T10:01:48.259Z",
  "created_on": "1977-01-15T20:11:54.896Z",
  "last_updated_on": "1998-06-26T21:20:10.657Z",
  "cardholder_id": 399098115,
  "account_id": 1176478769,
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/64957903`

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
  "cardholder_id": 399098115,
  "card_id": 1197428942,
  "account_id": 1176478769,
  "type": "CARD_PLACEMENT",
  "status": "TIMEOUT_CREDENTIALS",
  "custom_data": {
    "uVlEKlGXeYAt": ")r",
    "sFWRZfdiJoEF": 67,
    "lgYHhXdsoCio": false
  },
  "failure_reason": "NwMJBycgTUyurEBpXkZIwAUCDeGCPdu",
  "current_state": "OzxGygbBqrrLJJgYhzqsSJcuDrQsXSQRrVxQEwFAQFhrFtebbINqypkbuSBeCRx",
  "notification_sent": true,
  "time_elapsed": 1543256029,
  "run_count": 1066485078,
  "started_on": "1984-06-25T04:31:40.975Z",
  "completed_on": "1980-05-16T14:31:39.064Z",
  "expiration_date": "1970-05-22T10:01:48.259Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 399098115 },
	{ "card_id", 1197428942 },
	{ "account_id", 1176478769 },
	{ "type", "CARD_PLACEMENT" },
	{ "status", "TIMEOUT_CREDENTIALS" },
	{ "failure_reason", "NwMJBycgTUyurEBpXkZIwAUCDeGCPdu" },
	{ "current_state", "OzxGygbBqrrLJJgYhzqsSJcuDrQsXSQRrVxQEwFAQFhrFtebbINqypkbuSBeCRx" },
	{ "notification_sent", true },
	{ "time_elapsed", 1543256029 },
	{ "run_count", 1066485078 },
	{ "started_on", "1984-06-25T04:31:40.975Z" },
	{ "completed_on", "1980-05-16T14:31:39.064Z" },
	{ "expiration_date", "1970-05-22T10:01:48.259Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":399098115,\"card_id\":1197428942,\"account_id\":1176478769,\"type\":\"CARD_PLACEMENT\",\"status\":\"TIMEOUT_CREDENTIALS\",\"custom_data\":{\"uVlEKlGXeYAt\":\")r\",\"sFWRZfdiJoEF\":67,\"lgYHhXdsoCio\":false},\"failure_reason\":\"NwMJBycgTUyurEBpXkZIwAUCDeGCPdu\",\"current_state\":\"OzxGygbBqrrLJJgYhzqsSJcuDrQsXSQRrVxQEwFAQFhrFtebbINqypkbuSBeCRx\",\"notification_sent\":true,\"time_elapsed\":1543256029,\"run_count\":1066485078,\"started_on\":\"1984-06-25T04:31:40.975Z\",\"completed_on\":\"1980-05-16T14:31:39.064Z\",\"expiration_date\":\"1970-05-22T10:01:48.259Z\"}"
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
  "card_id": 696990567,
  "status": "LOGIN_RESUBMITTED",
  "custom_data": {
    "rUrOndQsHQpU": "@BjU})uAjK*Tv]R<3*3Y}C#M54x}e6s",
    "tvarOzLnuwtv": 96,
    "fBFxgfoaxbFr": true
  },
  "failure_reason": "IFKMaDdwLbeyDltPbgofiGJwop",
  "current_state": "asAAniPSoftkAnguWvcKNhWAwOnqBoNOJMILgojbxuoPfGMRyicReoKbxAWfarV",
  "notification_sent": false,
  "time_elapsed": 453526831,
  "run_count": 216418398,
  "started_on": "1980-09-28T22:11:59.835Z",
  "completed_on": "2007-05-18T13:56:05.831Z",
  "expiration_date": "1994-03-06T04:36:23.657Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 696990567 },
	{ "status", "LOGIN_RESUBMITTED" },
	{ "failure_reason", "IFKMaDdwLbeyDltPbgofiGJwop" },
	{ "current_state", "asAAniPSoftkAnguWvcKNhWAwOnqBoNOJMILgojbxuoPfGMRyicReoKbxAWfarV" },
	{ "notification_sent", false },
	{ "time_elapsed", 453526831 },
	{ "run_count", 216418398 },
	{ "started_on", "1980-09-28T22:11:59.835Z" },
	{ "completed_on", "2007-05-18T13:56:05.831Z" },
	{ "expiration_date", "1994-03-06T04:36:23.657Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"card_id\":696990567,\"status\":\"LOGIN_RESUBMITTED\",\"custom_data\":{\"rUrOndQsHQpU\":\"@BjU})uAjK*Tv]R<3*3Y}C#M54x}e6s\",\"tvarOzLnuwtv\":96,\"fBFxgfoaxbFr\":true},\"failure_reason\":\"IFKMaDdwLbeyDltPbgofiGJwop\",\"current_state\":\"asAAniPSoftkAnguWvcKNhWAwOnqBoNOJMILgojbxuoPfGMRyicReoKbxAWfarV\",\"notification_sent\":false,\"time_elapsed\":453526831,\"run_count\":216418398,\"started_on\":\"1980-09-28T22:11:59.835Z\",\"completed_on\":\"2007-05-18T13:56:05.831Z\",\"expiration_date\":\"1994-03-06T04:36:23.657Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/64957903
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

<aside class="notice">Update calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Delete single-site job

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/64957903
```

```javascript
await session.deleteSingleSiteJob(64957903);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(64957903);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [single-site job response parameters](#response-place_card_on_single_site_job).

