
# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1323586494
```

```javascript
const accounts = await session.getAccounts(1323586494);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(1323586494);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1323586494,
  "last_card_placed_id": 2054970278,
  "last_login": "2003-05-30T05:24:32.118Z",
  "last_password_update": "2018-09-02T16:07:45.015Z",
  "last_saved_card": "1994-07-18T06:22:42.181Z",
  "created_on": "1992-11-24T00:14:46.570Z",
  "last_updated_on": "1976-05-09T04:33:05.899Z",
  "cardholder_id": 873608744,
  "merchant_site_id": 481636656
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

**Example batch GET request path:**<br>`/cardsavr_accounts/12`

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
  "cardholder_id": 873608744,
  "merchant_site_id": 481636656,
  "last_card_placed_id": 2054970278,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 873608744 },
	{ "merchant_site_id", 481636656 },
	{ "last_card_placed_id", 2054970278 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":873608744,\"merchant_site_id\":481636656,\"last_card_placed_id\":2054970278,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
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
  "last_card_placed_id": 1872706233,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 1872706233 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"last_card_placed_id\":1872706233,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1323586494
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
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1323586494
```

```javascript
await session.deleteAccount(1323586494, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(1323586494, CARDHOLDER_SAFE_KEY);
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/2011943011
```

```javascript
const addresses = await session.getAddresses(2011943011);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(2011943011);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2011943011,
  "address1": "RUwWABnADHNCpoRbuasTlTubQYLmMvZqpkSOMdhIAGEvDQlFCuwsPFDgqyebIpKfNRYqZOFhyBoNwUjqAwiWCCVEjKyXHsHsUqG",
  "address2": "DpDzXZLwbRcwWIpvWuWaLpZDVHwgiWaqnlRANhDvwqfGbVOieKErPJqrqtxVHvbbupxSuDyccZLdZfOaxtWokyHJttCQaWSwAkf",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "created_on": "2010-12-14T11:20:21.505Z",
  "last_updated_on": "2012-04-27T17:38:08.126Z",
  "user_id": 2128665774
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

**Example batch GET request path:**<br>`/cardsavr_addresses/12`

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
  "user_id": 2128665774,
  "address1": "RUwWABnADHNCpoRbuasTlTubQYLmMvZqpkSOMdhIAGEvDQlFCuwsPFDgqyebIpKfNRYqZOFhyBoNwUjqAwiWCCVEjKyXHsHsUqG",
  "address2": "DpDzXZLwbRcwWIpvWuWaLpZDVHwgiWaqnlRANhDvwqfGbVOieKErPJqrqtxVHvbbupxSuDyccZLdZfOaxtWokyHJttCQaWSwAkf",
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
	{ "user_id", 2128665774 },
	{ "address1", "RUwWABnADHNCpoRbuasTlTubQYLmMvZqpkSOMdhIAGEvDQlFCuwsPFDgqyebIpKfNRYqZOFhyBoNwUjqAwiWCCVEjKyXHsHsUqG" },
	{ "address2", "DpDzXZLwbRcwWIpvWuWaLpZDVHwgiWaqnlRANhDvwqfGbVOieKErPJqrqtxVHvbbupxSuDyccZLdZfOaxtWokyHJttCQaWSwAkf" },
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
curl -d "{\"user_id\":2128665774,\"address1\":\"RUwWABnADHNCpoRbuasTlTubQYLmMvZqpkSOMdhIAGEvDQlFCuwsPFDgqyebIpKfNRYqZOFhyBoNwUjqAwiWCCVEjKyXHsHsUqG\",\"address2\":\"DpDzXZLwbRcwWIpvWuWaLpZDVHwgiWaqnlRANhDvwqfGbVOieKErPJqrqtxVHvbbupxSuDyccZLdZfOaxtWokyHJttCQaWSwAkf\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true}"
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
  "address1": "JGZGVtRoJDMYWxAXdHthwLFseCIFwUahxpvcuNsmAZOutopuiUwSnhDSzKtAyZPRrGeQBSBBtCLNHfJSudRUBxKxkJInOgvUdJE",
  "address2": "DhqitxlFAHODUWNNlxDQtEAsOsQpMDEZNYcoCWautLscAVIpEgpDAKsqBZbMyUHGesRbwDuaxAIYSOdFjrvGIOurtFYErnjhCYq",
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
	{ "address1", "JGZGVtRoJDMYWxAXdHthwLFseCIFwUahxpvcuNsmAZOutopuiUwSnhDSzKtAyZPRrGeQBSBBtCLNHfJSudRUBxKxkJInOgvUdJE" },
	{ "address2", "DhqitxlFAHODUWNNlxDQtEAsOsQpMDEZNYcoCWautLscAVIpEgpDAKsqBZbMyUHGesRbwDuaxAIYSOdFjrvGIOurtFYErnjhCYq" },
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
curl -d "{\"address1\":\"JGZGVtRoJDMYWxAXdHthwLFseCIFwUahxpvcuNsmAZOutopuiUwSnhDSzKtAyZPRrGeQBSBBtCLNHfJSudRUBxKxkJInOgvUdJE\",\"address2\":\"DhqitxlFAHODUWNNlxDQtEAsOsQpMDEZNYcoCWautLscAVIpEgpDAKsqBZbMyUHGesRbwDuaxAIYSOdFjrvGIOurtFYErnjhCYq\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/2011943011
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/2011943011
```

```javascript
await session.deleteAddress(2011943011);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(2011943011);
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1198524001
```

```javascript
const bins = await session.getBins(1198524001);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(1198524001);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1198524001,
  "financial_institution_id": 990309234,
  "created_on": "2010-10-17T17:00:01.799Z",
  "last_updated_on": "2011-10-19T12:27:59.516Z",
  "bank_identification_number": "25860060"
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

**Example batch GET request path:**<br>`/cardsavr_bins/12`

### <a name="response-cardsavr_bin"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
financial_institution_id | number (fk) | 
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
  "financial_institution_id": 990309234,
  "bank_identification_number": "25860060"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 990309234 },
	{ "bank_identification_number", "25860060" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":990309234,\"bank_identification_number\":\"25860060\"}"
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

See [bin response attributes](#response-cardsavr_bin).


## Update bin

```javascript
const bin = await session.updateBin({
  "financial_institution_id": 1221462697
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1221462697 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":1221462697}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1198524001
```

### Path

PUT /cardsavr_bins OR /cardsavr_bins/{id}

### Description

Update a bin and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
financial_institution_id | number |

See [bin response parameters](#response-cardsavr_bin).


## Delete bin

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1198524001
```

```javascript
await session.deleteBin(1198524001);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(1198524001);
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1622084841
```

```javascript
const cards = await session.getCards(1622084841);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(1622084841);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1622084841,
  "address_id": 847988075,
  "bin_id": 1189319232,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "created_on": "1972-12-15T06:08:39.015Z",
  "last_updated_on": "1986-10-06T00:41:19.287Z",
  "expiration_month": 12,
  "expiration_year": 24,
  "cardholder_id": 1773112016,
  "par": "ASxJsElKFGVtokFSxmAyhhtWRxQmo"
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

**Example batch GET request path:**<br>`/cardsavr_cards/12`

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
  "cardholder_id": 1773112016,
  "address_id": 847988075,
  "bin_id": 1189319232,
  "par": "ASxJsElKFGVtokFSxmAyhhtWRxQmo",
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
	{ "cardholder_id", 1773112016 },
	{ "address_id", 847988075 },
	{ "bin_id", 1189319232 },
	{ "par", "ASxJsElKFGVtokFSxmAyhhtWRxQmo" },
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
curl -d "{\"cardholder_id\":1773112016,\"address_id\":847988075,\"bin_id\":1189319232,\"par\":\"ASxJsElKFGVtokFSxmAyhhtWRxQmo\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
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
  "address_id": 1089948691,
  "bin_id": 1062811705,
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
	{ "address_id", 1089948691 },
	{ "bin_id", 1062811705 },
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
curl -d "{\"address_id\":1089948691,\"bin_id\":1062811705,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1622084841
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1622084841
```

```javascript
await session.deleteCard(1622084841, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(1622084841, CARDHOLDER_SAFE_KEY);
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/336332035
```

```javascript
const users = await session.getUsers(336332035);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(336332035);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 336332035,
  "financial_institution_id": 2146693797,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1988-05-18T13:31:20.254Z",
  "is_locked": false,
  "password_lifetime": 365,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "debugger",
  "phone_number": "kWpoilzojouyfW",
  "custom_data": {
    "aHJZoKDlcWnb": "YPf$gCElwY%ZoYrgo7$dQ[",
    "aMKpcslsaoDn": 28,
    "jjEfkQPCPMEK": true
  },
  "next_rotation_on": "1989-07-09T01:35:43.261Z",
  "created_on": "1976-04-19T03:25:07.153Z",
  "last_updated_on": "1989-04-20T10:30:21.497Z",
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

**Example batch GET request path:**<br>`/cardsavr_users/12`

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
  "financial_institution_id": 2146693797,
  "username": "jsmith123",
  "last_password": "WYBDWlGb22PdkWf/HAfO73OY1GcUX1GvbtnN3X0JNyo=",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "next_password": "D5KC4quBEZL/S3dQP9qjBq/XdD0BA3EerdzrPBslWGM=",
  "expired_password_1": "PD8i1VS8t9s5rbzhYofDmftWtaD25suIyVVmRIEzn1c=",
  "expired_password_2": "sLl8B/vNvD57k6NTe42hhukVqgWyPqw/HDIMv2EShAI=",
  "cardholder_safe_key": "cqeoQRpzYv6GKNwOmHa7P6PzlrBycRyl1YRefDnu8dc=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 365,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "debugger",
  "phone_number": "kWpoilzojouyfW",
  "custom_data": {
    "aHJZoKDlcWnb": "YPf$gCElwY%ZoYrgo7$dQ[",
    "aMKpcslsaoDn": 28,
    "jjEfkQPCPMEK": true
  },
  "next_rotation_on": "1989-07-09T01:35:43.261Z"
}, NEW_CARDHODLER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 2146693797 },
	{ "username", "jsmith123" },
	{ "last_password", "WYBDWlGb22PdkWf/HAfO73OY1GcUX1GvbtnN3X0JNyo=" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "next_password", "D5KC4quBEZL/S3dQP9qjBq/XdD0BA3EerdzrPBslWGM=" },
	{ "expired_password_1", "PD8i1VS8t9s5rbzhYofDmftWtaD25suIyVVmRIEzn1c=" },
	{ "expired_password_2", "sLl8B/vNvD57k6NTe42hhukVqgWyPqw/HDIMv2EShAI=" },
	{ "cardholder_safe_key", "cqeoQRpzYv6GKNwOmHa7P6PzlrBycRyl1YRefDnu8dc=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 365 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "debugger" },
	{ "phone_number", "kWpoilzojouyfW" },
	{ "next_rotation_on", "1989-07-09T01:35:43.261Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, NEW_CARDHODLER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":2146693797,\"username\":\"jsmith123\",\"last_password\":\"WYBDWlGb22PdkWf/HAfO73OY1GcUX1GvbtnN3X0JNyo=\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"next_password\":\"D5KC4quBEZL/S3dQP9qjBq/XdD0BA3EerdzrPBslWGM=\",\"expired_password_1\":\"PD8i1VS8t9s5rbzhYofDmftWtaD25suIyVVmRIEzn1c=\",\"expired_password_2\":\"sLl8B/vNvD57k6NTe42hhukVqgWyPqw/HDIMv2EShAI=\",\"cardholder_safe_key\":\"cqeoQRpzYv6GKNwOmHa7P6PzlrBycRyl1YRefDnu8dc=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":365,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"debugger\",\"phone_number\":\"kWpoilzojouyfW\",\"custom_data\":{\"aHJZoKDlcWnb\":\"YPf$gCElwY%ZoYrgo7$dQ[\",\"aMKpcslsaoDn\":28,\"jjEfkQPCPMEK\":true},\"next_rotation_on\":\"1989-07-09T01:35:43.261Z\"}"
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
  "financial_institution_id": 696544774,
  "last_password": "aRxj8hwDZ+YviXB0Q/7ygBuSWIkdBiKKEIC82r2f+ag=",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "next_password": "8MmRi5pHu01LTUmZTNVOEk9eAoPgbWkrVYj7e+g+lso=",
  "expired_password_1": "EMHz+QRwOLoOgQNNzrbVJj/ycu0HgjX5WxuzqHqRZZk=",
  "expired_password_2": "LK8ABtrPaoPw+xDCz3oC/Dp/gW5I8d6cq018MQzp8XE=",
  "cardholder_safe_key": "+6yY41m8r2JYx1HLyyrbmjpG7tkD/DKSaAczb+zDKNs=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 78,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_auditor",
  "phone_number": "sybdxFoSPZJCdb",
  "custom_data": {
    "NCTABBzeyAzV": "YA2",
    "GtfottcyUWrX": 17,
    "wXYwGiYanCKK": true
  },
  "next_rotation_on": "1970-09-16T20:24:59.302Z",
  "username": "jsmith123"
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 696544774 },
	{ "last_password", "aRxj8hwDZ+YviXB0Q/7ygBuSWIkdBiKKEIC82r2f+ag=" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "next_password", "8MmRi5pHu01LTUmZTNVOEk9eAoPgbWkrVYj7e+g+lso=" },
	{ "expired_password_1", "EMHz+QRwOLoOgQNNzrbVJj/ycu0HgjX5WxuzqHqRZZk=" },
	{ "expired_password_2", "LK8ABtrPaoPw+xDCz3oC/Dp/gW5I8d6cq018MQzp8XE=" },
	{ "cardholder_safe_key", "+6yY41m8r2JYx1HLyyrbmjpG7tkD/DKSaAczb+zDKNs=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 78 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "swch_auditor" },
	{ "phone_number", "sybdxFoSPZJCdb" },
	{ "next_rotation_on", "1970-09-16T20:24:59.302Z" },
	{ "username", "jsmith123" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":696544774,\"last_password\":\"aRxj8hwDZ+YviXB0Q/7ygBuSWIkdBiKKEIC82r2f+ag=\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"next_password\":\"8MmRi5pHu01LTUmZTNVOEk9eAoPgbWkrVYj7e+g+lso=\",\"expired_password_1\":\"EMHz+QRwOLoOgQNNzrbVJj/ycu0HgjX5WxuzqHqRZZk=\",\"expired_password_2\":\"LK8ABtrPaoPw+xDCz3oC/Dp/gW5I8d6cq018MQzp8XE=\",\"cardholder_safe_key\":\"+6yY41m8r2JYx1HLyyrbmjpG7tkD/DKSaAczb+zDKNs=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":78,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"swch_auditor\",\"phone_number\":\"sybdxFoSPZJCdb\",\"custom_data\":{\"NCTABBzeyAzV\":\"YA2\",\"GtfottcyUWrX\":17,\"wXYwGiYanCKK\":true},\"next_rotation_on\":\"1970-09-16T20:24:59.302Z\",\"username\":\"jsmith123\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/336332035
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/336332035
```

```javascript
await session.deleteUser(336332035);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(336332035);
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
https://api.INSTANCE.cardsavr.io/financial_institutions/1701284200
```

```javascript
const financialinstitutions = await session.getFinancialInstitutions(1701284200);
```

```csharp
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(1701284200);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1701284200,
  "name": "gQnjntiapUrTaMbSqQrYbUlzCtgOrXuHPrPyGKCiRINzvTdbAgFwBLvHKLjtNwO",
  "description": "dbKfqYcObMbpaKHwvZHQVRUP",
  "lookup_key": "fUpfNCIUxnPDwGaYWhHoZBVlnzQfThfAPndXdOjoyGtDmXgXnGmmdcrccZOPrsH",
  "alternate_lookup_key": "lYmHvJeLdxlLHTOnuorczuXDZbphbOUtQhJrMGqcaWQnUjLoiBOpMvKbABBCXJv",
  "created_on": "1989-06-07T19:23:58.941Z",
  "last_updated_on": "1984-01-08T03:47:41.733Z"
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

**Example batch GET request path:**<br>`/financial_institutions/12`

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
  "name": "gQnjntiapUrTaMbSqQrYbUlzCtgOrXuHPrPyGKCiRINzvTdbAgFwBLvHKLjtNwO",
  "description": "dbKfqYcObMbpaKHwvZHQVRUP",
  "lookup_key": "fUpfNCIUxnPDwGaYWhHoZBVlnzQfThfAPndXdOjoyGtDmXgXnGmmdcrccZOPrsH",
  "alternate_lookup_key": "lYmHvJeLdxlLHTOnuorczuXDZbphbOUtQhJrMGqcaWQnUjLoiBOpMvKbABBCXJv"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "gQnjntiapUrTaMbSqQrYbUlzCtgOrXuHPrPyGKCiRINzvTdbAgFwBLvHKLjtNwO" },
	{ "description", "dbKfqYcObMbpaKHwvZHQVRUP" },
	{ "lookup_key", "fUpfNCIUxnPDwGaYWhHoZBVlnzQfThfAPndXdOjoyGtDmXgXnGmmdcrccZOPrsH" },
	{ "alternate_lookup_key", "lYmHvJeLdxlLHTOnuorczuXDZbphbOUtQhJrMGqcaWQnUjLoiBOpMvKbABBCXJv" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"gQnjntiapUrTaMbSqQrYbUlzCtgOrXuHPrPyGKCiRINzvTdbAgFwBLvHKLjtNwO\",\"description\":\"dbKfqYcObMbpaKHwvZHQVRUP\",\"lookup_key\":\"fUpfNCIUxnPDwGaYWhHoZBVlnzQfThfAPndXdOjoyGtDmXgXnGmmdcrccZOPrsH\",\"alternate_lookup_key\":\"lYmHvJeLdxlLHTOnuorczuXDZbphbOUtQhJrMGqcaWQnUjLoiBOpMvKbABBCXJv\"}"
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
  "name": "YBzzLlwqXtSZOZgTQygWwohTwwxMXNXIGetvGFrJOzCTjFgrWMhHFOZNwiFZpyK",
  "description": "nnQMzuVEGXXKuuXmkshYYBCYUaIskxr",
  "lookup_key": "mceyUUDcjwjyknXkiiJGlzrMfVQOXLCEecbwsCxTSbEjnbITzlrcSQFWCMhwXWg",
  "alternate_lookup_key": "DMtVPfBELECmaMoAATIEgLoeQImglfxbUnmOMRvAufVsepYpJepzeyqMedGWGeL"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "YBzzLlwqXtSZOZgTQygWwohTwwxMXNXIGetvGFrJOzCTjFgrWMhHFOZNwiFZpyK" },
	{ "description", "nnQMzuVEGXXKuuXmkshYYBCYUaIskxr" },
	{ "lookup_key", "mceyUUDcjwjyknXkiiJGlzrMfVQOXLCEecbwsCxTSbEjnbITzlrcSQFWCMhwXWg" },
	{ "alternate_lookup_key", "DMtVPfBELECmaMoAATIEgLoeQImglfxbUnmOMRvAufVsepYpJepzeyqMedGWGeL" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"YBzzLlwqXtSZOZgTQygWwohTwwxMXNXIGetvGFrJOzCTjFgrWMhHFOZNwiFZpyK\",\"description\":\"nnQMzuVEGXXKuuXmkshYYBCYUaIskxr\",\"lookup_key\":\"mceyUUDcjwjyknXkiiJGlzrMfVQOXLCEecbwsCxTSbEjnbITzlrcSQFWCMhwXWg\",\"alternate_lookup_key\":\"DMtVPfBELECmaMoAATIEgLoeQImglfxbUnmOMRvAufVsepYpJepzeyqMedGWGeL\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/1701284200
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
https://api.INSTANCE.cardsavr.io/financial_institutions/1701284200
```

```javascript
await session.deleteFinancialInstitution(1701284200);
```

```csharp
CardSavrResponse<FinancialInstitution> financialinstitution = await http.DeleteFinancialInstitutionAsync(1701284200);
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
https://api.INSTANCE.cardsavr.io/integrators/646604047
```

```javascript
const integrators = await session.getIntegrators(646604047);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(646604047);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 646604047,
  "name": "aAlddNsCvXcmWAIDtTiDAGLzSyVkuvyZZUGkeunDdNXCaEhHP",
  "integrator_type": "swch_internal",
  "description": "vOHQfLqDDarhMrJwwMgBXLWPXrSPv",
  "last_key": "SoenMNfdaKBgOAEYuSNlAT/12QtqkNE99Nt29X5oloc=",
  "current_key": "HRUgcnoc5atjiYS6dH7bCfVxxsB54DDob99b1SY/urg=",
  "next_key": "439cr+RfqA41AyLfljlBixSU1q73wTN9nM07l1+1FGo=",
  "key_lifetime": 81,
  "next_rotation_on": "1987-10-31T17:17:41.300Z",
  "created_on": "1990-06-27T02:07:53.436Z",
  "last_updated_on": "1997-09-03T08:16:56.856Z"
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

**Example batch GET request path:**<br>`/integrators/12`

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
  "name": "aAlddNsCvXcmWAIDtTiDAGLzSyVkuvyZZUGkeunDdNXCaEhHP",
  "integrator_type": "swch_internal",
  "description": "vOHQfLqDDarhMrJwwMgBXLWPXrSPv",
  "last_key": "SoenMNfdaKBgOAEYuSNlAT/12QtqkNE99Nt29X5oloc=",
  "current_key": "HRUgcnoc5atjiYS6dH7bCfVxxsB54DDob99b1SY/urg=",
  "next_key": "439cr+RfqA41AyLfljlBixSU1q73wTN9nM07l1+1FGo=",
  "key_lifetime": 81,
  "next_rotation_on": "1987-10-31T17:17:41.300Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "aAlddNsCvXcmWAIDtTiDAGLzSyVkuvyZZUGkeunDdNXCaEhHP" },
	{ "integrator_type", "swch_internal" },
	{ "description", "vOHQfLqDDarhMrJwwMgBXLWPXrSPv" },
	{ "last_key", "SoenMNfdaKBgOAEYuSNlAT/12QtqkNE99Nt29X5oloc=" },
	{ "current_key", "HRUgcnoc5atjiYS6dH7bCfVxxsB54DDob99b1SY/urg=" },
	{ "next_key", "439cr+RfqA41AyLfljlBixSU1q73wTN9nM07l1+1FGo=" },
	{ "key_lifetime", 81 },
	{ "next_rotation_on", "1987-10-31T17:17:41.300Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"aAlddNsCvXcmWAIDtTiDAGLzSyVkuvyZZUGkeunDdNXCaEhHP\",\"integrator_type\":\"swch_internal\",\"description\":\"vOHQfLqDDarhMrJwwMgBXLWPXrSPv\",\"last_key\":\"SoenMNfdaKBgOAEYuSNlAT/12QtqkNE99Nt29X5oloc=\",\"current_key\":\"HRUgcnoc5atjiYS6dH7bCfVxxsB54DDob99b1SY/urg=\",\"next_key\":\"439cr+RfqA41AyLfljlBixSU1q73wTN9nM07l1+1FGo=\",\"key_lifetime\":81,\"next_rotation_on\":\"1987-10-31T17:17:41.300Z\"}"
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
  "name": "CgMlIcjusAIrEdmJpbdwxqXmAcsyzrEACWDsFOSAvZQhuOOaW",
  "integrator_type": "application",
  "description": "dntlZdmzoNTDzihWvNpzLGl",
  "last_key": "YEiHFcpa0W6vMeRuZxFwPqoKBzZitLZt5lsOoBwJ+Tw=",
  "current_key": "fmRjHBDG27jOT1a034O2OrEi7imXf7YDOmuviygpvl0=",
  "next_key": "Gs3qRKn/BD8nwNBRG+H+zfZCbZauDjVgrPmIyfamR4A=",
  "key_lifetime": 203,
  "next_rotation_on": "2010-04-10T03:39:51.915Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "CgMlIcjusAIrEdmJpbdwxqXmAcsyzrEACWDsFOSAvZQhuOOaW" },
	{ "integrator_type", "application" },
	{ "description", "dntlZdmzoNTDzihWvNpzLGl" },
	{ "last_key", "YEiHFcpa0W6vMeRuZxFwPqoKBzZitLZt5lsOoBwJ+Tw=" },
	{ "current_key", "fmRjHBDG27jOT1a034O2OrEi7imXf7YDOmuviygpvl0=" },
	{ "next_key", "Gs3qRKn/BD8nwNBRG+H+zfZCbZauDjVgrPmIyfamR4A=" },
	{ "key_lifetime", 203 },
	{ "next_rotation_on", "2010-04-10T03:39:51.915Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"CgMlIcjusAIrEdmJpbdwxqXmAcsyzrEACWDsFOSAvZQhuOOaW\",\"integrator_type\":\"application\",\"description\":\"dntlZdmzoNTDzihWvNpzLGl\",\"last_key\":\"YEiHFcpa0W6vMeRuZxFwPqoKBzZitLZt5lsOoBwJ+Tw=\",\"current_key\":\"fmRjHBDG27jOT1a034O2OrEi7imXf7YDOmuviygpvl0=\",\"next_key\":\"Gs3qRKn/BD8nwNBRG+H+zfZCbZauDjVgrPmIyfamR4A=\",\"key_lifetime\":203,\"next_rotation_on\":\"2010-04-10T03:39:51.915Z\"}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/646604047
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
https://api.INSTANCE.cardsavr.io/integrators/646604047
```

```javascript
await session.deleteIntegrator(646604047);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(646604047);
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
https://api.INSTANCE.cardsavr.io/merchant_sites/1137304726
```

```javascript
const merchantsites = await session.getMerchantSites(1137304726);
```

```csharp
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(1137304726);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1137304726,
  "name": "nNNvxgBRcOErUJJiTOPKEWNyHBswrk",
  "host": "sSeqXUkxaagEDWRHYGEPLhwYdMlkzUz",
  "image_lookup_key": "GYybckychLEoFpWu",
  "images": [
    {
      "PIpTnXZROHtN": "/*qRRVq[-GXt!vnk]&seDv",
      "HDYhuxmTiSor": 41,
      "vJRfLFbwtznp": false
    },
    {
      "MwaKWEaYBoKN": "xkdI#E}bNJas6N*p~{}<Df^sA3xnct",
      "GdvErjxBDpPX": 51,
      "KQbfTugBqzYr": true
    },
    {
      "JNsqbCAboUVX": "x<",
      "JarLQkkJxBOA": 7,
      "qziJDlKjMasW": false
    }
  ],
  "mfa": true,
  "tags": "nbfHbLvrUNZBQtigA",
  "login": {
    "YKHEnLQRsTSx": "!ya",
    "AiBMUmyztEfo": 49,
    "OxZaGlWJQqTS": false
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

**Example batch GET request path:**<br>`/merchant_sites/12`

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
https://api.INSTANCE.cardsavr.io/notifications/375723508
```

```javascript
const notifications = await session.getNotifications(375723508);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(375723508);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 375723508,
  "name": "datWYpLoLfVnRjMaAFbagaNLlYzeHQAOvkmTTfhEDyZgkYUEsGiiXtcDpyGiQAF",
  "type": "email",
  "config": {
    "BlviQsideIew": "_9&+aL!<#",
    "EEueflGGCOJx": 60,
    "QmNuDdKyqyrH": true
  },
  "created_on": "2012-03-16T05:57:36.402Z",
  "last_updated_on": "2013-02-16T19:30:17.267Z",
  "financial_institution_id": 1758859646
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

**Example batch GET request path:**<br>`/notifications/12`

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
  "financial_institution_id": 1758859646,
  "name": "datWYpLoLfVnRjMaAFbagaNLlYzeHQAOvkmTTfhEDyZgkYUEsGiiXtcDpyGiQAF",
  "type": "email",
  "config": {
    "BlviQsideIew": "_9&+aL!<#",
    "EEueflGGCOJx": 60,
    "QmNuDdKyqyrH": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1758859646 },
	{ "name", "datWYpLoLfVnRjMaAFbagaNLlYzeHQAOvkmTTfhEDyZgkYUEsGiiXtcDpyGiQAF" },
	{ "type", "email" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":1758859646,\"name\":\"datWYpLoLfVnRjMaAFbagaNLlYzeHQAOvkmTTfhEDyZgkYUEsGiiXtcDpyGiQAF\",\"type\":\"email\",\"config\":{\"BlviQsideIew\":\"_9&+aL!<#\",\"EEueflGGCOJx\":60,\"QmNuDdKyqyrH\":true}}"
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
  "name": "sytUcFmJoVnGZBROQDeZNBJeARBYZszRtGKWmjfTsDIlRXZmjsPXDQMbGXgeXnH",
  "type": "webhook",
  "config": {
    "fxyhunnpMYno": "d_Q88VoBXHf0w}xe+BUDGa%fSsvl",
    "qEjLolVEJkZc": 37,
    "kXTorfIKqkaM": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "sytUcFmJoVnGZBROQDeZNBJeARBYZszRtGKWmjfTsDIlRXZmjsPXDQMbGXgeXnH" },
	{ "type", "webhook" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```shell
curl -d "{\"name\":\"sytUcFmJoVnGZBROQDeZNBJeARBYZszRtGKWmjfTsDIlRXZmjsPXDQMbGXgeXnH\",\"type\":\"webhook\",\"config\":{\"fxyhunnpMYno\":\"d_Q88VoBXHf0w}xe+BUDGa%fSsvl\",\"qEjLolVEJkZc\":37,\"kXTorfIKqkaM\":true}}"
-X PUT -H "Content-Type: application/json"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/375723508
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
https://api.INSTANCE.cardsavr.io/notifications/375723508
```

```javascript
await session.deleteNotification(375723508);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(375723508);
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/2098779728
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(2098779728);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(2098779728);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2098779728,
  "card_placement_result_id": "eudZUaltxidFZcyijdVyqVrs",
  "status": "INVALID_CVV",
  "custom_data": {
    "OIPpByzALkos": "nqVyq2Jfp%c>8%CtK-$n6hiP#o6h5>",
    "bQGbDWkCoThk": 0,
    "nytACDIyfvEN": true
  },
  "failure_reason": "NwRAMw",
  "messaging_addresses": "pgLwJYlyLUAAHsPASXCHtdbgXiJbm",
  "current_state": "pdaMKxdrxesmUXQpbTPLWStqrmwRgSOxIDwNrcpHKZKZVXbgvYZSFVpvEENKoMK",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 88558525,
  "job_ready_on": "1972-01-17T07:07:13.681Z",
  "started_on": "1971-02-16T04:46:05.229Z",
  "completed_on": "1973-04-04T06:28:14.753Z",
  "expiration_date": "1987-07-09T12:41:15.423Z",
  "created_on": "1995-11-27T00:18:01.339Z",
  "last_updated_on": "2002-02-07T13:44:12.319Z",
  "user_id": 1983581417,
  "card_id": 956774473,
  "account_id": 1641269600
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

**Example batch GET request path:**<br>`/place_card_on_single_site_jobs/12`

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
  "place_card_on_multiple_sites_job_id": 1858338258,
  "user_id": 1983581417,
  "card_id": 956774473,
  "account_id": 1641269600,
  "status": "INVALID_CVV",
  "custom_data": {
    "OIPpByzALkos": "nqVyq2Jfp%c>8%CtK-$n6hiP#o6h5>",
    "bQGbDWkCoThk": 0,
    "nytACDIyfvEN": true
  },
  "failure_reason": "NwRAMw",
  "current_state": "pdaMKxdrxesmUXQpbTPLWStqrmwRgSOxIDwNrcpHKZKZVXbgvYZSFVpvEENKoMK",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 88558525,
  "started_on": "1971-02-16T04:46:05.229Z",
  "completed_on": "1973-04-04T06:28:14.753Z",
  "expiration_date": "1987-07-09T12:41:15.423Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "place_card_on_multiple_sites_job_id", 1858338258 },
	{ "user_id", 1983581417 },
	{ "card_id", 956774473 },
	{ "account_id", 1641269600 },
	{ "status", "INVALID_CVV" },
	{ "failure_reason", "NwRAMw" },
	{ "current_state", "pdaMKxdrxesmUXQpbTPLWStqrmwRgSOxIDwNrcpHKZKZVXbgvYZSFVpvEENKoMK" },
	{ "do_not_queue", true },
	{ "user_is_present", false },
	{ "time_elapsed", 88558525 },
	{ "started_on", "1971-02-16T04:46:05.229Z" },
	{ "completed_on", "1973-04-04T06:28:14.753Z" },
	{ "expiration_date", "1987-07-09T12:41:15.423Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"place_card_on_multiple_sites_job_id\":1858338258,\"user_id\":1983581417,\"card_id\":956774473,\"account_id\":1641269600,\"status\":\"INVALID_CVV\",\"custom_data\":{\"OIPpByzALkos\":\"nqVyq2Jfp%c>8%CtK-$n6hiP#o6h5>\",\"bQGbDWkCoThk\":0,\"nytACDIyfvEN\":true},\"failure_reason\":\"NwRAMw\",\"current_state\":\"pdaMKxdrxesmUXQpbTPLWStqrmwRgSOxIDwNrcpHKZKZVXbgvYZSFVpvEENKoMK\",\"do_not_queue\":true,\"user_is_present\":false,\"time_elapsed\":88558525,\"started_on\":\"1971-02-16T04:46:05.229Z\",\"completed_on\":\"1973-04-04T06:28:14.753Z\",\"expiration_date\":\"1987-07-09T12:41:15.423Z\"}"
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
  "status": "INVALID_NETWORK",
  "custom_data": {
    "boxiFcKOSyan": "@!,U7c9U5UgV",
    "HLZJnuqHeKTL": 57,
    "qktToLNMbAJN": true
  },
  "failure_reason": "IfXCLAuRUGhDuFHBJO",
  "current_state": "DbVyXanUbLnsuWSCVkpDvtYBcNdbLamtAPQkwnbyurrZwuUwUTAJiwghFdYWfHB",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 2065794618,
  "started_on": "2002-12-25T09:02:50.263Z",
  "completed_on": "1971-04-11T02:37:44.126Z",
  "expiration_date": "2004-03-19T22:35:59.764Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "status", "INVALID_NETWORK" },
	{ "failure_reason", "IfXCLAuRUGhDuFHBJO" },
	{ "current_state", "DbVyXanUbLnsuWSCVkpDvtYBcNdbLamtAPQkwnbyurrZwuUwUTAJiwghFdYWfHB" },
	{ "do_not_queue", true },
	{ "user_is_present", false },
	{ "time_elapsed", 2065794618 },
	{ "started_on", "2002-12-25T09:02:50.263Z" },
	{ "completed_on", "1971-04-11T02:37:44.126Z" },
	{ "expiration_date", "2004-03-19T22:35:59.764Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"status\":\"INVALID_NETWORK\",\"custom_data\":{\"boxiFcKOSyan\":\"@!,U7c9U5UgV\",\"HLZJnuqHeKTL\":57,\"qktToLNMbAJN\":true},\"failure_reason\":\"IfXCLAuRUGhDuFHBJO\",\"current_state\":\"DbVyXanUbLnsuWSCVkpDvtYBcNdbLamtAPQkwnbyurrZwuUwUTAJiwghFdYWfHB\",\"do_not_queue\":true,\"user_is_present\":false,\"time_elapsed\":2065794618,\"started_on\":\"2002-12-25T09:02:50.263Z\",\"completed_on\":\"1971-04-11T02:37:44.126Z\",\"expiration_date\":\"2004-03-19T22:35:59.764Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/2098779728
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/2098779728
```

```javascript
await session.deleteSingleSiteJob(2098779728);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(2098779728);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [single-site job response parameters](#response-place_card_on_single_site_job).

