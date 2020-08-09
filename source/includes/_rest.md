# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1544408
```

```javascript
const accounts = await session.getAccounts(1544408);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(1544408);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1544408,
  "last_card_placed_id": 7369358,
  "username": "jsmith123",
  "password": "Pa$$w0rd",
  "last_login": "2004-01-26T19:57:33.363Z",
  "last_password_update": "2002-12-26T00:18:42.113Z",
  "last_saved_card": "2017-02-21T21:33:04.647Z",
  "created_on": "1980-07-21T07:14:58.493Z",
  "last_updated_on": "1998-07-16T20:59:08.109Z",
  "cardholder_id": 9533530,
  "merchant_site_id": 5043428
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

### Filter parameters

Filter | Type | Description
------ | ---- | -----------
id | integer | 
ids | integer | 
cardholder_ids | integer | 
merchant_site_ids | integer | 
last_card_placed_ids | integer | 
last_login_min /<br> last_login_max | date | 
last_password_update_min /<br> last_password_update_max | date | 
last_saved_card_min /<br> last_saved_card_max | date | 
created_on_min /<br> created_on_max | date | 
last_updated_on_min /<br> last_updated_on_max | date | 


## Create account

```javascript
const account = await session.createAccount({
  "cardholder_id": 9533530,
  "merchant_site_id": 5043428,
  "last_card_placed_id": 7369358,
  "username": "jsmith123",
  "password": "Pa$$w0rd"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 9533530 },
	{ "merchant_site_id", 5043428 },
	{ "last_card_placed_id", 7369358 },
	{ "username", "jsmith123" },
	{ "password", "Pa$$w0rd" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":9533530,\"merchant_site_id\":5043428,\"last_card_placed_id\":7369358,\"username\":\"jsmith123\",\"password\":\"Pa$$w0rd\"}"
-X POST -H "Content-Type: application/javascript"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
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
cardholder_id | integer | yes
merchant_site_id | integer | yes
last_card_placed_id | integer | no
username | string | no
password | string | no

<aside class="notice">Create calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username and password for added security.</aside>

## Update account

```javascript
const account = await session.updateAccount({
  "last_card_placed_id": 6692642,
  "username": "jsmith123",
  "password": "Pa$$w0rd"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 6692642 },
	{ "username", "jsmith123" },
	{ "password", "Pa$$w0rd" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"last_card_placed_id\":6692642,\"username\":\"jsmith123\",\"password\":\"Pa$$w0rd\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1544408
```

### Path

PUT /cardsavr_accounts OR /cardsavr_accounts/{id}

### Description

Update a account and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
last_card_placed_id | integer |
username | string |
password | string |

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username and password for added security. The safe keys are not required if updating other user properties.</aside>

## Delete account

```shell
curl -X DELETE
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1544408
```

```javascript
await session.deleteAccount(1544408, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(1544408, CARDHOLDER_SAFE_KEY);
```

### Path

DELETE /cardsavr_accounts/{id}

### Description

Delete a account and purge its [related items](#cascading-delete).  An id is required on every delete request.

<aside class="notice">The cardholder_safe_key header is required to delete accounts.</aside>

# Addresses
Address objects contain billing address information for a particular user.
## Get address

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/7388630
```

```javascript
const addresses = await session.getAddresses(7388630);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(7388630);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 7388630,
  "address1": "svjpNQFXEdeqiILSbMjUsFHRJeBzUyOMUUExCFFhUNmqBhMfrOcGXukVkLvjXsEdMkxfgjDClAHqOEUoxRZrSWjGvrVANqSqdoG",
  "address2": "pJEzYwDVicrAJARleNKmqbHafkupTAmvCGEcsmWoPsGhiBeMzQdXgZqmModJAogZXwQCNNFjMuVKMdUUFFZGRvsOYtKWChAuQMk",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "created_on": "1979-04-10T22:25:12.118Z",
  "last_updated_on": "2004-07-15T19:43:30.695Z",
  "user_id": 3182108
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

### Filter parameters

Filter | Type | Description
------ | ---- | -----------
id | integer | 
ids | integer | 
user_ids | integer | 
is_primary | boolean | 
created_on_min /<br> created_on_max | date | 
last_updated_on_min /<br> last_updated_on_max | date | 


## Create address

```javascript
const address = await session.createAddress({
  "user_id": 3182108,
  "address1": "svjpNQFXEdeqiILSbMjUsFHRJeBzUyOMUUExCFFhUNmqBhMfrOcGXukVkLvjXsEdMkxfgjDClAHqOEUoxRZrSWjGvrVANqSqdoG",
  "address2": "pJEzYwDVicrAJARleNKmqbHafkupTAmvCGEcsmWoPsGhiBeMzQdXgZqmModJAogZXwQCNNFjMuVKMdUUFFZGRvsOYtKWChAuQMk",
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
	{ "user_id", 3182108 },
	{ "address1", "svjpNQFXEdeqiILSbMjUsFHRJeBzUyOMUUExCFFhUNmqBhMfrOcGXukVkLvjXsEdMkxfgjDClAHqOEUoxRZrSWjGvrVANqSqdoG" },
	{ "address2", "pJEzYwDVicrAJARleNKmqbHafkupTAmvCGEcsmWoPsGhiBeMzQdXgZqmModJAogZXwQCNNFjMuVKMdUUFFZGRvsOYtKWChAuQMk" },
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
curl -d "{\"user_id\":3182108,\"address1\":\"svjpNQFXEdeqiILSbMjUsFHRJeBzUyOMUUExCFFhUNmqBhMfrOcGXukVkLvjXsEdMkxfgjDClAHqOEUoxRZrSWjGvrVANqSqdoG\",\"address2\":\"pJEzYwDVicrAJARleNKmqbHafkupTAmvCGEcsmWoPsGhiBeMzQdXgZqmModJAogZXwQCNNFjMuVKMdUUFFZGRvsOYtKWChAuQMk\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true}"
-X POST -H "Content-Type: application/javascript"
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
user_id | integer | no
address1 | string | yes
address2 | string | no
city | string | yes
subnational | string | yes
postal_code | string | yes
postal_other | string | no
country | string | no
is_primary | boolean | yes


## Update address

```javascript
const address = await session.updateAddress({
  "address1": "pFNEVtTOatDjZOybjeMpBOJrBaqOCtKenuyywNxxDnGPaWtdqsSmSTkkBOTifQNrfYKlrbAUhkmhwyENetuWjvyQEyrzftMintN",
  "address2": "eTjFdVPuVTIUTWrlfxnQDwVWmNBmKATaPUjoGUlKsHdHagXrdiMpErUbAyzbaHOSuzOoHgCumSWVhrIWlqvSnqZRRMXUepaUMXh",
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
	{ "address1", "pFNEVtTOatDjZOybjeMpBOJrBaqOCtKenuyywNxxDnGPaWtdqsSmSTkkBOTifQNrfYKlrbAUhkmhwyENetuWjvyQEyrzftMintN" },
	{ "address2", "eTjFdVPuVTIUTWrlfxnQDwVWmNBmKATaPUjoGUlKsHdHagXrdiMpErUbAyzbaHOSuzOoHgCumSWVhrIWlqvSnqZRRMXUepaUMXh" },
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
curl -d "{\"address1\":\"pFNEVtTOatDjZOybjeMpBOJrBaqOCtKenuyywNxxDnGPaWtdqsSmSTkkBOTifQNrfYKlrbAUhkmhwyENetuWjvyQEyrzftMintN\",\"address2\":\"eTjFdVPuVTIUTWrlfxnQDwVWmNBmKATaPUjoGUlKsHdHagXrdiMpErUbAyzbaHOSuzOoHgCumSWVhrIWlqvSnqZRRMXUepaUMXh\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/7388630
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


## Delete address

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/7388630
```

```javascript
await session.deleteAddress(7388630);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(7388630);
```

### Path

DELETE /cardsavr_addresses/{id}

### Description

Delete a address and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Bins
A cardsavr_bin object
## Get bin

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/6168733
```

```javascript
const bins = await session.getBins(6168733);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(6168733);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 6168733,
  "financial_institution_id": 4952151,
  "brand": "kutpkDTarWFPaxtNiLf",
  "issuer": "mZaCWzPAfqTpqzgXNkhXNeQMTRrWNtHIHUuTkoWbEUvPnUntpLMJZRxCJwwYwaicZvZAWqBLGahejIhCehsIgiIwipefvhfcrOd",
  "type": "FYFJuQOEDXJuJh",
  "level": "PNCHuVwdFUSDIpWRetCqXnaGefkjSFaPJFuNZYrIJvWZeIokFjCoiwAaDmxhLAyKIAYvglhbpjngxZpXiotXoKFjOZyJarMbmbD",
  "created_on": "1993-07-02T13:17:53.687Z",
  "last_updated_on": "1983-12-16T20:19:18.572Z",
  "bank_identification_number": "53820658"
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

### Filter parameters

Filter | Type | Description
------ | ---- | -----------
id | integer | 
ids | integer | 
financial_institution_ids | integer | 
bank_identification_numbers | integer | 
created_on_min /<br> created_on_max | date | 
last_updated_on_min /<br> last_updated_on_max | date | 


## Create bin

```javascript
const bin = await session.createBin({
  "financial_institution_id": 4952151,
  "bank_identification_number": "53820658",
  "brand": "kutpkDTarWFPaxtNiLf",
  "issuer": "mZaCWzPAfqTpqzgXNkhXNeQMTRrWNtHIHUuTkoWbEUvPnUntpLMJZRxCJwwYwaicZvZAWqBLGahejIhCehsIgiIwipefvhfcrOd",
  "type": "FYFJuQOEDXJuJh",
  "level": "PNCHuVwdFUSDIpWRetCqXnaGefkjSFaPJFuNZYrIJvWZeIokFjCoiwAaDmxhLAyKIAYvglhbpjngxZpXiotXoKFjOZyJarMbmbD"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 4952151 },
	{ "bank_identification_number", "53820658" },
	{ "brand", "kutpkDTarWFPaxtNiLf" },
	{ "issuer", "mZaCWzPAfqTpqzgXNkhXNeQMTRrWNtHIHUuTkoWbEUvPnUntpLMJZRxCJwwYwaicZvZAWqBLGahejIhCehsIgiIwipefvhfcrOd" },
	{ "type", "FYFJuQOEDXJuJh" },
	{ "level", "PNCHuVwdFUSDIpWRetCqXnaGefkjSFaPJFuNZYrIJvWZeIokFjCoiwAaDmxhLAyKIAYvglhbpjngxZpXiotXoKFjOZyJarMbmbD" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":4952151,\"bank_identification_number\":\"53820658\",\"brand\":\"kutpkDTarWFPaxtNiLf\",\"issuer\":\"mZaCWzPAfqTpqzgXNkhXNeQMTRrWNtHIHUuTkoWbEUvPnUntpLMJZRxCJwwYwaicZvZAWqBLGahejIhCehsIgiIwipefvhfcrOd\",\"type\":\"FYFJuQOEDXJuJh\",\"level\":\"PNCHuVwdFUSDIpWRetCqXnaGefkjSFaPJFuNZYrIJvWZeIokFjCoiwAaDmxhLAyKIAYvglhbpjngxZpXiotXoKFjOZyJarMbmbD\"}"
-X POST -H "Content-Type: application/javascript"
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
financial_institution_id | integer | yes
bank_identification_number | integer | yes


## Update bin

```javascript
const bin = await session.updateBin({
  "financial_institution_id": 3074351,
  "brand": "oSFpBpsiYEgZPXjoTCH",
  "issuer": "fuAkXKVeUAiZESPYHgSPYmrgUUGBFIqNaQgEjQelZTKyRVrXicNESSKuruMKMayXiDttcGffWzMSFfZImCIqvqtcPTmkxCJItcN",
  "type": "rkslPDcdKNRqiK",
  "level": "PBdSrISSuiVkqKwUlXtIufhvjErwupWEVRsyehjoaREdIRpnEchVDzQLnOoILxdWOOXjAPEJGEXaeFPUPBXdzwlFEkXanIfmLQq"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 3074351 },
	{ "brand", "oSFpBpsiYEgZPXjoTCH" },
	{ "issuer", "fuAkXKVeUAiZESPYHgSPYmrgUUGBFIqNaQgEjQelZTKyRVrXicNESSKuruMKMayXiDttcGffWzMSFfZImCIqvqtcPTmkxCJItcN" },
	{ "type", "rkslPDcdKNRqiK" },
	{ "level", "PBdSrISSuiVkqKwUlXtIufhvjErwupWEVRsyehjoaREdIRpnEchVDzQLnOoILxdWOOXjAPEJGEXaeFPUPBXdzwlFEkXanIfmLQq" }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":3074351,\"brand\":\"oSFpBpsiYEgZPXjoTCH\",\"issuer\":\"fuAkXKVeUAiZESPYHgSPYmrgUUGBFIqNaQgEjQelZTKyRVrXicNESSKuruMKMayXiDttcGffWzMSFfZImCIqvqtcPTmkxCJItcN\",\"type\":\"rkslPDcdKNRqiK\",\"level\":\"PBdSrISSuiVkqKwUlXtIufhvjErwupWEVRsyehjoaREdIRpnEchVDzQLnOoILxdWOOXjAPEJGEXaeFPUPBXdzwlFEkXanIfmLQq\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/6168733
```

### Path

PUT /cardsavr_bins OR /cardsavr_bins/{id}

### Description

Update a bin and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
financial_institution_id | integer |


## Delete bin

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/6168733
```

```javascript
await session.deleteBin(6168733);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(6168733);
```

### Path

DELETE /cardsavr_bins/{id}

### Description

Delete a bin and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Cards
Card objects contain information about a payment card belonging to a single cardholder. Card objects are used to populate users' payment information on merchant sites.
## Get card

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/2064092
```

```javascript
const cards = await session.getCards(2064092);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(2064092);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2064092,
  "address_id": 5729432,
  "bin_id": 118814,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "first_6": "iWHzmveQgSLyLgINaWUUuOwdNXcPlccj",
  "first_7": "KSqLQttDjeefdMFXOlJkccdNlRuHULjj",
  "first_8": "saGZhNMmjwTphNsWchUvlSNhZkdeqKgI",
  "created_on": "2003-02-21T15:26:43.415Z",
  "last_updated_on": "2002-10-15T18:23:43.109Z",
  "expiration_month": 1,
  "expiration_year": 31,
  "cardholder_id": 6874080,
  "par": "QoGlhEcZwoqonhtvlTTcsjKSHOlrx",
  "pan": "KPfZrdFzlaDjbdf",
  "cvv": "UEy"
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

### Filter parameters

Filter | Type | Description
------ | ---- | -----------
id | integer | 
ids | integer | 
cardholder_ids | integer | 
address_ids | integer | 
bin_ids | integer | 
pars | string | 
first_6 | string | 
first_7 | string | 
first_8 | string | 
created_on_min /<br> created_on_max | date | 
last_updated_on_min /<br> last_updated_on_max | date | 


## Create card

```javascript
const card = await session.createCard({
  "cardholder_id": 6874080,
  "address_id": 5729432,
  "bin_id": 118814,
  "par": "QoGlhEcZwoqonhtvlTTcsjKSHOlrx",
  "pan": "KPfZrdFzlaDjbdf",
  "cvv": "UEy",
  "expiration_month": 1,
  "expiration_year": 31,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 6874080 },
	{ "address_id", 5729432 },
	{ "bin_id", 118814 },
	{ "par", "QoGlhEcZwoqonhtvlTTcsjKSHOlrx" },
	{ "pan", "KPfZrdFzlaDjbdf" },
	{ "cvv", "UEy" },
	{ "expiration_month", 1 },
	{ "expiration_year", 31 },
	{ "name_on_card", "Joe C Smith" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" }
};

CardSavrResponse<Card> card = await http.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":6874080,\"address_id\":5729432,\"bin_id\":118814,\"par\":\"QoGlhEcZwoqonhtvlTTcsjKSHOlrx\",\"pan\":\"KPfZrdFzlaDjbdf\",\"cvv\":\"UEy\",\"expiration_month\":1,\"expiration_year\":31,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\"}"
-X POST -H "Content-Type: application/javascript"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
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
cardholder_id | integer | yes
address_id | integer | no
bin_id | integer | no
par | string | yes
pan | string | yes
cvv | string | yes
expiration_month | string | yes
expiration_year | string | yes
name_on_card | string | yes
first_name | string | yes
last_name | string | yes

<aside class="notice">Create calls to /cardsavr_cards require the cardholder's personal cardholder_safe_key header to encrypt and save the pan and cvv for added security.</aside>

## Update card

```javascript
const card = await session.updateCard({
  "address_id": 7360585,
  "bin_id": 1016824,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "expiration_month": 1,
  "expiration_year": 31
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address_id", 7360585 },
	{ "bin_id", 1016824 },
	{ "name_on_card", "Joe C Smith" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "expiration_month", 1 },
	{ "expiration_year", 31 }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"address_id\":7360585,\"bin_id\":1016824,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"expiration_month\":1,\"expiration_year\":31}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/2064092
```

### Path

PUT /cardsavr_cards OR /cardsavr_cards/{id}

### Description

Update a card and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
address_id | integer |
bin_id | integer |
name_on_card | string |
first_name | string |
last_name | string |


## Delete card

```shell
curl -X DELETE
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/2064092
```

```javascript
await session.deleteCard(2064092, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(2064092, CARDHOLDER_SAFE_KEY);
```

### Path

DELETE /cardsavr_cards/{id}

### Description

Delete a card and purge its [related items](#cascading-delete).  An id is required on every delete request.

<aside class="notice">The cardholder_safe_key header is required to delete cards.</aside>

# Users
User objects correspond to a single CardSavr user.
## Get user

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/2726525
```

```javascript
const users = await session.getUsers(2726525);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(2726525);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2726525,
  "financial_institution_id": 3407133,
  "last_password": "H9OoKJxtDrLHDq1z2fg+r/n80zg7REtnYc1waREOW5M=",
  "password": "Pa$$w0rd",
  "next_password": "bsHrpPLNh/+1zc1DHSbOZaKYsEbY6eDKM+mNhLfshE4=",
  "expired_password_1": "U9CNPZIKwwBoIVPzGfdHz5btfl3XNohV/FFZECwVb1w=",
  "expired_password_2": "cPDysKXdzm0nhP/AFEWjce0z4ekXdHOg/K2LoeZuYzY=",
  "cardholder_safe_key": "OmsPNUBDjwRtFxSv15YEsO8S8kY1dAxgll4Ckdix19w=",
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1971-01-10T11:41:17.981Z",
  "is_locked": true,
  "password_lifetime": 164,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "debugger_ro",
  "phone_number": "ozGSBdoIYkRwgm",
  "custom_data": {
    "VYquUjwqRaxY": "04lO.EO}=JqFo9Tr+kalN]R<MJE!z",
    "FOBXituErjAq": 80,
    "WTpfOvLvvMDD": false
  },
  "next_rotation_on": "1976-03-13T17:43:13.614Z",
  "created_on": "1974-06-22T03:56:52.428Z",
  "last_updated_on": "1978-12-16T03:02:46.581Z",
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

### Filter parameters

Filter | Type | Description
------ | ---- | -----------
id | integer | 
ids | integer | 
financial_institution_ids | integer | 
usernames | string | 
username | string | 
first_name | string | 
last_name | string | 
last_login_time_min /<br> last_login_time_max | date | 
is_locked | boolean | 
email | string | 
is_password_update_required | boolean | 
role | enum | 
roles_include /<br> roles_exclude | enum | 
created_on_min /<br> created_on_max | date | 
last_updated_on_min /<br> last_updated_on_max | date | 


## Create user

```javascript
const user = await session.createUser({
  "financial_institution_id": 3407133,
  "username": "jsmith123",
  "password": "Pa$$w0rd",
  "next_password": "bsHrpPLNh/+1zc1DHSbOZaKYsEbY6eDKM+mNhLfshE4=",
  "cardholder_safe_key": "OmsPNUBDjwRtFxSv15YEsO8S8kY1dAxgll4Ckdix19w=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 164,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "debugger_ro",
  "phone_number": "ozGSBdoIYkRwgm",
  "custom_data": {
    "VYquUjwqRaxY": "04lO.EO}=JqFo9Tr+kalN]R<MJE!z",
    "FOBXituErjAq": 80,
    "WTpfOvLvvMDD": false
  },
  "next_rotation_on": "1976-03-13T17:43:13.614Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 3407133 },
	{ "username", "jsmith123" },
	{ "password", "Pa$$w0rd" },
	{ "next_password", "bsHrpPLNh/+1zc1DHSbOZaKYsEbY6eDKM+mNhLfshE4=" },
	{ "cardholder_safe_key", "OmsPNUBDjwRtFxSv15YEsO8S8kY1dAxgll4Ckdix19w=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 164 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "debugger_ro" },
	{ "phone_number", "ozGSBdoIYkRwgm" },
	{ "next_rotation_on", "1976-03-13T17:43:13.614Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":3407133,\"username\":\"jsmith123\",\"password\":\"Pa$$w0rd\",\"next_password\":\"bsHrpPLNh/+1zc1DHSbOZaKYsEbY6eDKM+mNhLfshE4=\",\"cardholder_safe_key\":\"OmsPNUBDjwRtFxSv15YEsO8S8kY1dAxgll4Ckdix19w=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":164,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"debugger_ro\",\"phone_number\":\"ozGSBdoIYkRwgm\",\"custom_data\":{\"VYquUjwqRaxY\":\"04lO.EO}=JqFo9Tr+kalN]R<MJE!z\",\"FOBXituErjAq\":80,\"WTpfOvLvvMDD\":false},\"next_rotation_on\":\"1976-03-13T17:43:13.614Z\"}"
-X POST -H "Content-Type: application/javascript"
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
financial_institution_id | integer | no
username | string | yes
password | base64 | no
next_password | base64 | no
cardholder_safe_key | base64 | no
first_name | string | no
last_name | string | no
password_lifetime | integer | no
email | string | no
is_password_update_required | boolean | no
role | enum | yes
phone_number | string | no
custom_data | object | no
next_rotation_on | date | no

<aside class="notice">Create calls to /cardsavr_users require the cardholder's personal cardholder_safe_key header to encrypt and save the safe for added security.</aside>

## Update user

```javascript
const user = await session.updateUser({
  "financial_institution_id": 731125,
  "password": "Pa$$w0rd",
  "next_password": "hdN9lXokJMiNdo6jpAX4ciecs5DQUxdZOSInb6xIXOU=",
  "cardholder_safe_key": "JzDnUPwxgsu4UdqpmuStFvjokI4j++j1uK8bTqvriqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 5,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "customer_agent",
  "phone_number": "eaUNuVlwmLQPTV",
  "custom_data": {
    "YMqYKphQJXUQ": "g5(b+La~$A6SiolZ",
    "StBRIBWxnBZc": 7,
    "wsZJoltTvaoZ": true
  },
  "next_rotation_on": "2014-06-16T02:28:35.991Z",
  "username": "jsmith123"
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 731125 },
	{ "password", "Pa$$w0rd" },
	{ "next_password", "hdN9lXokJMiNdo6jpAX4ciecs5DQUxdZOSInb6xIXOU=" },
	{ "cardholder_safe_key", "JzDnUPwxgsu4UdqpmuStFvjokI4j++j1uK8bTqvriqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 5 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "customer_agent" },
	{ "phone_number", "eaUNuVlwmLQPTV" },
	{ "next_rotation_on", "2014-06-16T02:28:35.991Z" },
	{ "username", "jsmith123" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":731125,\"password\":\"Pa$$w0rd\",\"next_password\":\"hdN9lXokJMiNdo6jpAX4ciecs5DQUxdZOSInb6xIXOU=\",\"cardholder_safe_key\":\"JzDnUPwxgsu4UdqpmuStFvjokI4j++j1uK8bTqvriqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":5,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"customer_agent\",\"phone_number\":\"eaUNuVlwmLQPTV\",\"custom_data\":{\"YMqYKphQJXUQ\":\"g5(b+La~$A6SiolZ\",\"StBRIBWxnBZc\":7,\"wsZJoltTvaoZ\":true},\"next_rotation_on\":\"2014-06-16T02:28:35.991Z\",\"username\":\"jsmith123\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/2726525
```

### Path

PUT /cardsavr_users OR /cardsavr_users/{id}

### Description

Update a user and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
financial_institution_id | integer |
password | base64 |
next_password | base64 |
cardholder_safe_key | base64 |
first_name | string |
last_name | string |
password_lifetime | integer |
email | string |
is_password_update_required | boolean |
role | enum |
phone_number | string |
custom_data | object |
next_rotation_on | date |

<aside class="notice">Update calls to /cardsavr_users require the cardholder's current cardholder-safe-key, and the new new-cardholder-safe-key headers when rotating the cardholder_safe_key.</aside>

## Delete user

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/2726525
```

```javascript
await session.deleteUser(2726525);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(2726525);
```

### Path

DELETE /cardsavr_users/{id}

### Description

Delete a user and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Financial Institutions
A CardSavr Financial Institution that can be associated with jobs and users.
## Get financial institution

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/7736760
```

```javascript
const financial institutions = await session.getFinancial Institutions(7736760);
```

```csharp
CardSavrResponse<Financial Institutions> financial institutions = await session.GetFinancial InstitutionsAsync(7736760);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 7736760,
  "name": "ixkMcOHDkDsVIgPeDZNfMBsItJqLIyqtczeTtfKgCbiyzSepkofsYuyNosLxWFV",
  "description": "kYlH",
  "lookup_key": "QKLrfdNcBSfwaReTMRuJavUhiAiIrsTLqkyyMzoYeEvHSCJlkKoRxgnlzmrBlbn",
  "alternate_lookup_key": "PahHBliWwrgmwiqlJvaLDfApggtdzDLJCNpMIzUUIQQJuuiLTBegbbWkxfwwmMF",
  "created_on": "1992-01-22T11:32:12.633Z",
  "last_updated_on": "1987-02-25T09:10:44.893Z"
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

### Filter parameters

Filter | Type | Description
------ | ---- | -----------
id | integer | 
ids | integer | 
names | string | 
lookup_key | string | 
alternate_lookup_key | string | 
created_on_min /<br> created_on_max | date | 
last_updated_on_min /<br> last_updated_on_max | date | 


## Create financial institution

```javascript
const financial institution = await session.createFinancial Institution({
  "name": "ixkMcOHDkDsVIgPeDZNfMBsItJqLIyqtczeTtfKgCbiyzSepkofsYuyNosLxWFV",
  "description": "kYlH",
  "lookup_key": "QKLrfdNcBSfwaReTMRuJavUhiAiIrsTLqkyyMzoYeEvHSCJlkKoRxgnlzmrBlbn",
  "alternate_lookup_key": "PahHBliWwrgmwiqlJvaLDfApggtdzDLJCNpMIzUUIQQJuuiLTBegbbWkxfwwmMF"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "ixkMcOHDkDsVIgPeDZNfMBsItJqLIyqtczeTtfKgCbiyzSepkofsYuyNosLxWFV" },
	{ "description", "kYlH" },
	{ "lookup_key", "QKLrfdNcBSfwaReTMRuJavUhiAiIrsTLqkyyMzoYeEvHSCJlkKoRxgnlzmrBlbn" },
	{ "alternate_lookup_key", "PahHBliWwrgmwiqlJvaLDfApggtdzDLJCNpMIzUUIQQJuuiLTBegbbWkxfwwmMF" }
};

CardSavrResponse<Financial Institution> financial institution = await http.CreateFinancial InstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"ixkMcOHDkDsVIgPeDZNfMBsItJqLIyqtczeTtfKgCbiyzSepkofsYuyNosLxWFV\",\"description\":\"kYlH\",\"lookup_key\":\"QKLrfdNcBSfwaReTMRuJavUhiAiIrsTLqkyyMzoYeEvHSCJlkKoRxgnlzmrBlbn\",\"alternate_lookup_key\":\"PahHBliWwrgmwiqlJvaLDfApggtdzDLJCNpMIzUUIQQJuuiLTBegbbWkxfwwmMF\"}"
-X POST -H "Content-Type: application/javascript"
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


## Update financial institution

```javascript
const financial institution = await session.updateFinancial Institution({
  "name": "ZKSrtTmTKBxEJijQXqbwXEVymAQLxCAVijNjqEKpntTUxwXifJESeIqxqiOPDPw",
  "description": "x",
  "lookup_key": "fZXsQUWiHqtPRaAnYFXYFSMgpQMapPbwuFNfQbDcsANmXzdyfBRIxWZQOkppogW",
  "alternate_lookup_key": "YWLXcxDBjQAKmikIAvvrjmOxyUfQXrHFfdqHiLjbbvjskXCRngsoLFBmleqsoaX"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "ZKSrtTmTKBxEJijQXqbwXEVymAQLxCAVijNjqEKpntTUxwXifJESeIqxqiOPDPw" },
	{ "description", "x" },
	{ "lookup_key", "fZXsQUWiHqtPRaAnYFXYFSMgpQMapPbwuFNfQbDcsANmXzdyfBRIxWZQOkppogW" },
	{ "alternate_lookup_key", "YWLXcxDBjQAKmikIAvvrjmOxyUfQXrHFfdqHiLjbbvjskXCRngsoLFBmleqsoaX" }
};

CardSavrResponse<Financial Institution> financial institution = await http.UpdateFinancial InstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"ZKSrtTmTKBxEJijQXqbwXEVymAQLxCAVijNjqEKpntTUxwXifJESeIqxqiOPDPw\",\"description\":\"x\",\"lookup_key\":\"fZXsQUWiHqtPRaAnYFXYFSMgpQMapPbwuFNfQbDcsANmXzdyfBRIxWZQOkppogW\",\"alternate_lookup_key\":\"YWLXcxDBjQAKmikIAvvrjmOxyUfQXrHFfdqHiLjbbvjskXCRngsoLFBmleqsoaX\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/7736760
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


## Delete financial institution

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/7736760
```

```javascript
await session.deleteFinancial Institution(7736760);
```

```csharp
CardSavrResponse<Financial Institution> financial institution = await http.DeleteFinancial InstitutionAsync(7736760);
```

### Path

DELETE /financial_institutions/{id}

### Description

Delete a financial institution and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Integrators
An integrator object represents an integrator that implements CardSavr.
## Get integrator

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/2354524
```

```javascript
const integrators = await session.getIntegrators(2354524);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(2354524);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2354524,
  "name": "IOxRUkXhbGXZTqRaPdwsMLmRbGxuFDyFsBcSPmXMZHvCNWRbM",
  "integrator_type": "application",
  "description": "RtEKzBZbyKTCRrFkpljkDpwA",
  "last_key": "7ch/McbU/yHC5TWDMYhdh1dUhvkYDOknQvPIUy+MtnM=",
  "current_key": "YY8l6U1VVSRcojKb+X7uAQ4dxmpFyK9PfYzgwKZAr7g=",
  "next_key": "/ViK8qrjnYtiJZrAQTrLfxw/GtTMd07ezoASnuZUXL4=",
  "key_lifetime": 51,
  "next_rotation_on": "1980-11-26T09:23:51.145Z",
  "created_on": "2007-01-28T21:05:16.371Z",
  "last_updated_on": "2006-09-09T17:20:12.464Z"
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

### Filter parameters

Filter | Type | Description
------ | ---- | -----------
id | integer | 
ids | integer | 
names | string | 
name | string | 
integrator_type | enum | 
integrator_types_include /<br> integrator_types_exclude | enum | 
next_rotation_on_min /<br> next_rotation_on_max | date | 
created_on_min /<br> created_on_max | date | 
last_updated_on_min /<br> last_updated_on_max | date | 


## Create integrator

```javascript
const integrator = await session.createIntegrator({
  "name": "IOxRUkXhbGXZTqRaPdwsMLmRbGxuFDyFsBcSPmXMZHvCNWRbM",
  "integrator_type": "application",
  "description": "RtEKzBZbyKTCRrFkpljkDpwA",
  "last_key": "7ch/McbU/yHC5TWDMYhdh1dUhvkYDOknQvPIUy+MtnM=",
  "current_key": "YY8l6U1VVSRcojKb+X7uAQ4dxmpFyK9PfYzgwKZAr7g=",
  "next_key": "/ViK8qrjnYtiJZrAQTrLfxw/GtTMd07ezoASnuZUXL4=",
  "key_lifetime": 51,
  "next_rotation_on": "1980-11-26T09:23:51.145Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "IOxRUkXhbGXZTqRaPdwsMLmRbGxuFDyFsBcSPmXMZHvCNWRbM" },
	{ "integrator_type", "application" },
	{ "description", "RtEKzBZbyKTCRrFkpljkDpwA" },
	{ "last_key", "7ch/McbU/yHC5TWDMYhdh1dUhvkYDOknQvPIUy+MtnM=" },
	{ "current_key", "YY8l6U1VVSRcojKb+X7uAQ4dxmpFyK9PfYzgwKZAr7g=" },
	{ "next_key", "/ViK8qrjnYtiJZrAQTrLfxw/GtTMd07ezoASnuZUXL4=" },
	{ "key_lifetime", 51 },
	{ "next_rotation_on", "1980-11-26T09:23:51.145Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"IOxRUkXhbGXZTqRaPdwsMLmRbGxuFDyFsBcSPmXMZHvCNWRbM\",\"integrator_type\":\"application\",\"description\":\"RtEKzBZbyKTCRrFkpljkDpwA\",\"last_key\":\"7ch/McbU/yHC5TWDMYhdh1dUhvkYDOknQvPIUy+MtnM=\",\"current_key\":\"YY8l6U1VVSRcojKb+X7uAQ4dxmpFyK9PfYzgwKZAr7g=\",\"next_key\":\"/ViK8qrjnYtiJZrAQTrLfxw/GtTMd07ezoASnuZUXL4=\",\"key_lifetime\":51,\"next_rotation_on\":\"1980-11-26T09:23:51.145Z\"}"
-X POST -H "Content-Type: application/javascript"
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
integrator_type | enum | yes
description | string | no
last_key | base64 | no
current_key | base64 | no
next_key | base64 | no
key_lifetime | integer | no
next_rotation_on | date | no


## Update integrator

```javascript
const integrator = await session.updateIntegrator({
  "name": "kvAWFIOTizzrqifhRhpAwKyVlbymypgzdrlUtdAVhDMXBBhlU",
  "integrator_type": "application",
  "description": "zvYILifHvJCccyPj",
  "last_key": "1sMw69s0i82D9j5Cm+MJ/BUAwnaEFKQkN/6SW2h8Gmc=",
  "current_key": "QnVg67sPyweeLP54AQPdfS1FZ6yaAu5K18kvXThR9L8=",
  "next_key": "PW4sBJpt4i5fad7WIILco/QMN3GdKpQbrIV7Q9OiEsY=",
  "key_lifetime": 107,
  "next_rotation_on": "1993-01-06T10:52:03.721Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "kvAWFIOTizzrqifhRhpAwKyVlbymypgzdrlUtdAVhDMXBBhlU" },
	{ "integrator_type", "application" },
	{ "description", "zvYILifHvJCccyPj" },
	{ "last_key", "1sMw69s0i82D9j5Cm+MJ/BUAwnaEFKQkN/6SW2h8Gmc=" },
	{ "current_key", "QnVg67sPyweeLP54AQPdfS1FZ6yaAu5K18kvXThR9L8=" },
	{ "next_key", "PW4sBJpt4i5fad7WIILco/QMN3GdKpQbrIV7Q9OiEsY=" },
	{ "key_lifetime", 107 },
	{ "next_rotation_on", "1993-01-06T10:52:03.721Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"kvAWFIOTizzrqifhRhpAwKyVlbymypgzdrlUtdAVhDMXBBhlU\",\"integrator_type\":\"application\",\"description\":\"zvYILifHvJCccyPj\",\"last_key\":\"1sMw69s0i82D9j5Cm+MJ/BUAwnaEFKQkN/6SW2h8Gmc=\",\"current_key\":\"QnVg67sPyweeLP54AQPdfS1FZ6yaAu5K18kvXThR9L8=\",\"next_key\":\"PW4sBJpt4i5fad7WIILco/QMN3GdKpQbrIV7Q9OiEsY=\",\"key_lifetime\":107,\"next_rotation_on\":\"1993-01-06T10:52:03.721Z\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/2354524
```

### Path

PUT /integrators OR /integrators/{id}

### Description

Update a integrator and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
name | string |
integrator_type | enum |
description | string |
last_key | base64 |
current_key | base64 |
next_key | base64 |
key_lifetime | integer |
next_rotation_on | date |


## Delete integrator

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/2354524
```

```javascript
await session.deleteIntegrator(2354524);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(2354524);
```

### Path

DELETE /integrators/{id}

### Description

Delete a integrator and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Merchant Sites
Merchant site objects contain information about CardSavr-supported merchant sites.
## Get merchant site

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/merchant_sites/2005346
```

```javascript
const merchant sites = await session.getMerchant Sites(2005346);
```

```csharp
CardSavrResponse<Merchant Sites> merchant sites = await session.GetMerchant SitesAsync(2005346);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2005346,
  "name": "GonyVUzRXTazddVKsMt",
  "host": "FnJxgbHsXQhidaRaFRGPutUBoxMtH",
  "image_lookup_key": "LAKvbcBlMFZWFxMajgnihgV",
  "images": [
    {
      "pZLVGqVGRPwJ": "R}NE63FTlp7qG8i+g<Nd$7cS.oS5c_))",
      "FbmqLNBQYOnh": 91,
      "xEBEiyqNdxsO": true
    },
    {
      "dEOAttjptDRN": "SgG",
      "myrLCfzRfeOe": 76,
      "mQqljSIKEkyX": true
    },
    {
      "snvlEElDpqTU": "v0$axfo2i@+]UT^fb",
      "cMXFAMUpYGCz": 2,
      "cRgUFlNVqpMY": true
    }
  ],
  "mfa": true,
  "tags": "vKhKVqxSUhVsocDDhcukrn",
  "login": {
    "mFLXohIYoOdU": "R}[rY{*QMO,<5I",
    "MDWMXzmoWwQZ": 40,
    "gjcTaQtlKIAF": false
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

### Filter parameters

Filter | Type | Description
------ | ---- | -----------
id | integer | 
ids | integer | 
top_ids | integer | 
name_starts_with | string | 
hosts | string | 
host | string | 
top_hosts | string | 
host_starts_with | string | 
tags | string | 


# Notifications
A noficiation record that defines how to take action CardSavr events like jobs completing or sessions ending.
## Get notification

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/6443250
```

```javascript
const notifications = await session.getNotifications(6443250);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(6443250);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 6443250,
  "name": "JRHNMigjRdwVMYRmGdVQgNuFIkaKlesOBqnhviZbhfysXBxEuqwTmlCpKDrWnzN",
  "type": "email",
  "config": {
    "ZODWgDQrGVsC": "1F)$",
    "dnXwLwgXBdrA": 58,
    "aPGuFcrEZgvx": false
  },
  "created_on": "2009-10-03T22:58:21.668Z",
  "last_updated_on": "1974-05-24T18:51:48.957Z",
  "financial_institution_id": 540657
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

### Filter parameters

Filter | Type | Description
------ | ---- | -----------
id | integer | 
ids | integer | 
financial_institution_ids | integer | 
names | string | 
type | enum | 
event | enum | 
created_on_min /<br> created_on_max | date | 
last_updated_on_min /<br> last_updated_on_max | date | 


## Create notification

```javascript
const notification = await session.createNotification({
  "financial_institution_id": 540657,
  "name": "JRHNMigjRdwVMYRmGdVQgNuFIkaKlesOBqnhviZbhfysXBxEuqwTmlCpKDrWnzN",
  "type": "email",
  "config": {
    "ZODWgDQrGVsC": "1F)$",
    "dnXwLwgXBdrA": 58,
    "aPGuFcrEZgvx": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 540657 },
	{ "name", "JRHNMigjRdwVMYRmGdVQgNuFIkaKlesOBqnhviZbhfysXBxEuqwTmlCpKDrWnzN" },
	{ "type", "email" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":540657,\"name\":\"JRHNMigjRdwVMYRmGdVQgNuFIkaKlesOBqnhviZbhfysXBxEuqwTmlCpKDrWnzN\",\"type\":\"email\",\"config\":{\"ZODWgDQrGVsC\":\"1F)$\",\"dnXwLwgXBdrA\":58,\"aPGuFcrEZgvx\":false}}"
-X POST -H "Content-Type: application/javascript"
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
financial_institution_id | integer | yes
name | string | yes
type | enum | yes
event | enum | yes
config | object | no


## Update notification

```javascript
const notification = await session.updateNotification({
  "name": "jEuaNufLToUoYXAJCdrAmtEUGstDHWzdLpWecZreSVFHKkReqcbgwkKXWGcskoH",
  "type": "webhook",
  "config": {
    "vKApdHSmWaWT": "#A7NO>(o!D-Cz%w7gus",
    "QolxmxcYnWDs": 6,
    "rzxecvtNXAix": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "jEuaNufLToUoYXAJCdrAmtEUGstDHWzdLpWecZreSVFHKkReqcbgwkKXWGcskoH" },
	{ "type", "webhook" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```shell
curl -d "{\"name\":\"jEuaNufLToUoYXAJCdrAmtEUGstDHWzdLpWecZreSVFHKkReqcbgwkKXWGcskoH\",\"type\":\"webhook\",\"config\":{\"vKApdHSmWaWT\":\"#A7NO>(o!D-Cz%w7gus\",\"QolxmxcYnWDs\":6,\"rzxecvtNXAix\":true}}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/6443250
```

### Path

PUT /notifications OR /notifications/{id}

### Description

Update a notification and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
name | string |
type | enum |
event | enum |
config | object |


## Delete notification

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/6443250
```

```javascript
await session.deleteNotification(6443250);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(6443250);
```

### Path

DELETE /notifications/{id}

### Description

Delete a notification and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Single-site jobs
A place_card_on_single_site_job object
## Get single-site job

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/6692227
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(6692227);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(6692227);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 6692227,
  "card_placement_result_id": "jctwEzIgaqLHfZOJnThzEXaMjscz",
  "status": "CANCELLED_QUICKSTART",
  "safe_blob": "NH",
  "safe_nonce": "wREuHhkPyfvBMbCBLWlsTTlfPrYo",
  "custom_data": {
    "vkfEqcgJPONd": "[NZ^!OHb*L)^,mwBxrh,yT!Bn6>",
    "npNsYShldExm": 35,
    "LjuBNscFjLPq": false
  },
  "failure_reason": "xd",
  "messaging_addresses": "bpoUtLYOXPJErUlWThiWjEmj",
  "current_state": "GgyijNWULuYoxnavByQldwoAtuIsBHjDKvEpgerZIintoqByNsGBqonQzlRtjxW",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 8979426,
  "job_ready_on": "1973-06-05T14:46:41.897Z",
  "started_on": "2004-07-14T12:22:06.639Z",
  "completed_on": "1978-04-18T21:03:57.241Z",
  "expiration_date": "1973-04-17T05:40:08.810Z",
  "created_on": "2012-11-24T22:21:02.014Z",
  "last_updated_on": "2013-02-21T10:50:53.879Z",
  "place_card_on_multiple_sites_job_id": 1258051,
  "user_id": 2191393,
  "card_id": 7885022,
  "account_id": 7158359
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

### Filter parameters

Filter | Type | Description
------ | ---- | -----------
id | integer | 
ids | integer | 
user_ids | integer | 
card_ids | integer | 
account_ids | integer | 
card_placement_result_ids | string | 
status | enum | 
status_include /<br> status_exclude | enum | 
queue_name | enum | 
current_state | string | 
do_not_queue | boolean | 
user_is_present | boolean | 
time_elapsed_min /<br> time_elapsed_max | integer | 
job_ready_on_min /<br> job_ready_on_max | date | 
started_on_min /<br> started_on_max | date | 
completed_on_min /<br> completed_on_max | date | 
expiration_date_min /<br> expiration_date_max | date | 
created_on_min /<br> created_on_max | date | 
last_updated_on_min /<br> last_updated_on_max | date | 


## Create single-site job

```javascript
const singlesitejob = await session.createSingleSiteJob({
  "place_card_on_multiple_sites_job_id": 1258051,
  "user_id": 2191393,
  "card_id": 7885022,
  "account_id": 7158359,
  "status": "CANCELLED_QUICKSTART",
  "custom_data": {
    "vkfEqcgJPONd": "[NZ^!OHb*L)^,mwBxrh,yT!Bn6>",
    "npNsYShldExm": 35,
    "LjuBNscFjLPq": false
  },
  "failure_reason": "xd",
  "current_state": "GgyijNWULuYoxnavByQldwoAtuIsBHjDKvEpgerZIintoqByNsGBqonQzlRtjxW",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 8979426,
  "started_on": "2004-07-14T12:22:06.639Z",
  "completed_on": "1978-04-18T21:03:57.241Z",
  "expiration_date": "1973-04-17T05:40:08.810Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "place_card_on_multiple_sites_job_id", 1258051 },
	{ "user_id", 2191393 },
	{ "card_id", 7885022 },
	{ "account_id", 7158359 },
	{ "status", "CANCELLED_QUICKSTART" },
	{ "failure_reason", "xd" },
	{ "current_state", "GgyijNWULuYoxnavByQldwoAtuIsBHjDKvEpgerZIintoqByNsGBqonQzlRtjxW" },
	{ "do_not_queue", true },
	{ "user_is_present", false },
	{ "time_elapsed", 8979426 },
	{ "started_on", "2004-07-14T12:22:06.639Z" },
	{ "completed_on", "1978-04-18T21:03:57.241Z" },
	{ "expiration_date", "1973-04-17T05:40:08.810Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body);
```

```shell
curl -d "{\"place_card_on_multiple_sites_job_id\":1258051,\"user_id\":2191393,\"card_id\":7885022,\"account_id\":7158359,\"status\":\"CANCELLED_QUICKSTART\",\"custom_data\":{\"vkfEqcgJPONd\":\"[NZ^!OHb*L)^,mwBxrh,yT!Bn6>\",\"npNsYShldExm\":35,\"LjuBNscFjLPq\":false},\"failure_reason\":\"xd\",\"current_state\":\"GgyijNWULuYoxnavByQldwoAtuIsBHjDKvEpgerZIintoqByNsGBqonQzlRtjxW\",\"do_not_queue\":true,\"user_is_present\":false,\"time_elapsed\":8979426,\"started_on\":\"2004-07-14T12:22:06.639Z\",\"completed_on\":\"1978-04-18T21:03:57.241Z\",\"expiration_date\":\"1973-04-17T05:40:08.810Z\"}"
-X POST -H "Content-Type: application/javascript"
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
user_id | integer | yes
card_id | integer | yes
account_id | integer | yes
status | enum | no
queue_name | enum | no
custom_data | object | no
failure_reason | string | no
current_state | string | no
do_not_queue | boolean | no
user_is_present | boolean | no
time_elapsed | integer | no
started_on | date | no
completed_on | date | no
expiration_date | date | no


## Update single-site job

```javascript
const singlesitejob = await session.updateSingleSiteJob({
  "status": "SUCCESS",
  "custom_data": {
    "pVVmiASzcXYa": "r1WdOIo",
    "MWeIAdqeBweR": 18,
    "tqlpqzXoMzoT": true
  },
  "failure_reason": "AgJduEXLVT",
  "current_state": "gGFDYTQNwWCXofbFLBPeBvXQNRqRWvbXnFKzlAjQzWSBWLGcQCfuyDMOMGXdMbL",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 6199371,
  "started_on": "2009-11-08T08:21:42.637Z",
  "completed_on": "2005-07-21T13:24:44.711Z",
  "expiration_date": "2001-10-07T04:52:37.030Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "status", "SUCCESS" },
	{ "failure_reason", "AgJduEXLVT" },
	{ "current_state", "gGFDYTQNwWCXofbFLBPeBvXQNRqRWvbXnFKzlAjQzWSBWLGcQCfuyDMOMGXdMbL" },
	{ "do_not_queue", true },
	{ "user_is_present", false },
	{ "time_elapsed", 6199371 },
	{ "started_on", "2009-11-08T08:21:42.637Z" },
	{ "completed_on", "2005-07-21T13:24:44.711Z" },
	{ "expiration_date", "2001-10-07T04:52:37.030Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body);
```

```shell
curl -d "{\"status\":\"SUCCESS\",\"custom_data\":{\"pVVmiASzcXYa\":\"r1WdOIo\",\"MWeIAdqeBweR\":18,\"tqlpqzXoMzoT\":true},\"failure_reason\":\"AgJduEXLVT\",\"current_state\":\"gGFDYTQNwWCXofbFLBPeBvXQNRqRWvbXnFKzlAjQzWSBWLGcQCfuyDMOMGXdMbL\",\"do_not_queue\":true,\"user_is_present\":false,\"time_elapsed\":6199371,\"started_on\":\"2009-11-08T08:21:42.637Z\",\"completed_on\":\"2005-07-21T13:24:44.711Z\",\"expiration_date\":\"2001-10-07T04:52:37.030Z\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/6692227
```

### Path

PUT /place_card_on_single_site_jobs OR /place_card_on_single_site_jobs/{id}

### Description

Update a single-site job and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
status | enum |
queue_name | enum |
custom_data | object |
failure_reason | string |
current_state | string |
do_not_queue | boolean |
user_is_present | boolean |
time_elapsed | integer |
started_on | date |
completed_on | date |
expiration_date | date |


## Delete single-site job

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/6692227
```

```javascript
await session.deleteSingleSiteJob(6692227);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(6692227);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

