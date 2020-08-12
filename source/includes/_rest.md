
# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/4524758
```

```javascript
const accounts = await session.getAccounts(4524758);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(4524758);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 4524758,
  "last_card_placed_id": 1848272,
  "last_login": "1994-07-23T03:05:51.498Z",
  "last_password_update": "2014-04-04T06:53:35.903Z",
  "last_saved_card": "1991-12-29T19:34:12.204Z",
  "created_on": "2014-08-20T23:17:06.691Z",
  "last_updated_on": "1992-06-02T03:38:40.020Z",
  "cardholder_id": 4493896,
  "merchant_site_id": 6177210
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
  "cardholder_id": 4493896,
  "merchant_site_id": 6177210,
  "last_card_placed_id": 1848272,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 4493896 },
	{ "merchant_site_id", 6177210 },
	{ "last_card_placed_id", 1848272 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":4493896,\"merchant_site_id\":6177210,\"last_card_placed_id\":1848272,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X POST -H "Content-Type: application/javascript"
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

<aside class="notice">Create calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username and password for added security.</aside>

## Update account

```javascript
const account = await session.updateAccount({
  "last_card_placed_id": 8795411,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 8795411 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"last_card_placed_id\":8795411,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/4524758
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

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username and password for added security. The safe keys are not required if updating other user properties.</aside>

## Delete account

```shell
curl -X DELETE
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/4524758
```

```javascript
await session.deleteAccount(4524758, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(4524758, CARDHOLDER_SAFE_KEY);
```

### Path

DELETE /cardsavr_accounts/{id}

### Description

Delete a account and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [account response parameters](#response-cardsavr_account).

<aside class="notice">The cardholder_safe_key header is required to delete accounts.</aside>


# Addresses
Address objects contain billing address information for a particular user.
## Get address

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/2258263
```

```javascript
const addresses = await session.getAddresses(2258263);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(2258263);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2258263,
  "address1": "FXPjFYktFmDvPTFGyBwayLogduZrnDOabjSNMUIeFMCJCFOZcObIJmzqmrDEAyVOIdMSGDxMTCQxFptPgDxehyrACWNJlmZqMzg",
  "address2": "cGZDpshHXSrtekxbhVBGvbDajJcncxBeKJqxbELNuJAVCuMXFXVmBBReExPcqopnBqEHbCNFaAIxUbFnXEUzlKToPqwaGYLwLiQ",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "created_on": "1972-04-11T03:14:27.467Z",
  "last_updated_on": "2004-12-21T13:36:08.594Z",
  "user_id": 6095690
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
  "user_id": 6095690,
  "address1": "FXPjFYktFmDvPTFGyBwayLogduZrnDOabjSNMUIeFMCJCFOZcObIJmzqmrDEAyVOIdMSGDxMTCQxFptPgDxehyrACWNJlmZqMzg",
  "address2": "cGZDpshHXSrtekxbhVBGvbDajJcncxBeKJqxbELNuJAVCuMXFXVmBBReExPcqopnBqEHbCNFaAIxUbFnXEUzlKToPqwaGYLwLiQ",
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
	{ "user_id", 6095690 },
	{ "address1", "FXPjFYktFmDvPTFGyBwayLogduZrnDOabjSNMUIeFMCJCFOZcObIJmzqmrDEAyVOIdMSGDxMTCQxFptPgDxehyrACWNJlmZqMzg" },
	{ "address2", "cGZDpshHXSrtekxbhVBGvbDajJcncxBeKJqxbELNuJAVCuMXFXVmBBReExPcqopnBqEHbCNFaAIxUbFnXEUzlKToPqwaGYLwLiQ" },
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
curl -d "{\"user_id\":6095690,\"address1\":\"FXPjFYktFmDvPTFGyBwayLogduZrnDOabjSNMUIeFMCJCFOZcObIJmzqmrDEAyVOIdMSGDxMTCQxFptPgDxehyrACWNJlmZqMzg\",\"address2\":\"cGZDpshHXSrtekxbhVBGvbDajJcncxBeKJqxbELNuJAVCuMXFXVmBBReExPcqopnBqEHbCNFaAIxUbFnXEUzlKToPqwaGYLwLiQ\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false}"
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
  "address1": "RlWSjrJioQCVNeGsAlFkluvyVtqXDgoSTSMzaZPSxGayouBXUCxwiEiZwpBzUfLgUoozsLczMzoYFVDcxLmdXMHGVZhuRJeQsXC",
  "address2": "YUwsmZdSgvnpUqxtbYVRYJUCikASUJSAmGkoTBPMhqzJEafxqxvKnuijYIcGNcMdrpfkybiAmevhyTdJLtrvhYQjPbTVUhQRLED",
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
	{ "address1", "RlWSjrJioQCVNeGsAlFkluvyVtqXDgoSTSMzaZPSxGayouBXUCxwiEiZwpBzUfLgUoozsLczMzoYFVDcxLmdXMHGVZhuRJeQsXC" },
	{ "address2", "YUwsmZdSgvnpUqxtbYVRYJUCikASUJSAmGkoTBPMhqzJEafxqxvKnuijYIcGNcMdrpfkybiAmevhyTdJLtrvhYQjPbTVUhQRLED" },
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
curl -d "{\"address1\":\"RlWSjrJioQCVNeGsAlFkluvyVtqXDgoSTSMzaZPSxGayouBXUCxwiEiZwpBzUfLgUoozsLczMzoYFVDcxLmdXMHGVZhuRJeQsXC\",\"address2\":\"YUwsmZdSgvnpUqxtbYVRYJUCikASUJSAmGkoTBPMhqzJEafxqxvKnuijYIcGNcMdrpfkybiAmevhyTdJLtrvhYQjPbTVUhQRLED\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/2258263
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/2258263
```

```javascript
await session.deleteAddress(2258263);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(2258263);
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/3617826
```

```javascript
const bins = await session.getBins(3617826);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(3617826);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 3617826,
  "financial_institution_id": 136810,
  "created_on": "1977-03-27T15:32:55.167Z",
  "last_updated_on": "2013-04-27T00:58:41.315Z",
  "bank_identification_number": "47773237"
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
  "financial_institution_id": 136810,
  "bank_identification_number": "47773237",
  "brand": "daJeJdWFCVGEDxiuSwk",
  "issuer": "BNyZHqhtINgcyYrgrYJGFdFKDYapHFLjELgrfUEnNLCHgefIuwbyrjnrRbdJhmqhpRPnguzDWFhbwyeytysVyUuKvJVetYntNDX",
  "type": "AXJTgBIuzRKnvr",
  "level": "DCkyKSQQMdUayLEUqEXhuzBuFYnSNqTltDjeDOlPWHlADyrAlkfkRDJcZzAyGiPeNFHzNDycrxOgFcsQLgHLxIYCILMMDuLPpMl"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 136810 },
	{ "bank_identification_number", "47773237" },
	{ "brand", "daJeJdWFCVGEDxiuSwk" },
	{ "issuer", "BNyZHqhtINgcyYrgrYJGFdFKDYapHFLjELgrfUEnNLCHgefIuwbyrjnrRbdJhmqhpRPnguzDWFhbwyeytysVyUuKvJVetYntNDX" },
	{ "type", "AXJTgBIuzRKnvr" },
	{ "level", "DCkyKSQQMdUayLEUqEXhuzBuFYnSNqTltDjeDOlPWHlADyrAlkfkRDJcZzAyGiPeNFHzNDycrxOgFcsQLgHLxIYCILMMDuLPpMl" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":136810,\"bank_identification_number\":\"47773237\",\"brand\":\"daJeJdWFCVGEDxiuSwk\",\"issuer\":\"BNyZHqhtINgcyYrgrYJGFdFKDYapHFLjELgrfUEnNLCHgefIuwbyrjnrRbdJhmqhpRPnguzDWFhbwyeytysVyUuKvJVetYntNDX\",\"type\":\"AXJTgBIuzRKnvr\",\"level\":\"DCkyKSQQMdUayLEUqEXhuzBuFYnSNqTltDjeDOlPWHlADyrAlkfkRDJcZzAyGiPeNFHzNDycrxOgFcsQLgHLxIYCILMMDuLPpMl\"}"
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
financial_institution_id | number | yes
bank_identification_number | string | yes

See [bin response attributes](#response-cardsavr_bin).


## Update bin

```javascript
const bin = await session.updateBin({
  "financial_institution_id": 5855232,
  "brand": "WfszeQtSNFDPZLpieNn",
  "issuer": "cWEmGkptwhFMomHOBSRRKjEcYOWghngzYTrNnFMqxxfqWDFyPaeBISKklHBBeKLSlxxtnbtISSsDTvBZXNSVlTGQWwlLPzAjrRN",
  "type": "lGhkazmuxqqDWI",
  "level": "pZfbvJdBApPOOPykNKtEpHWdEniSUZOuEaSwKpSanKuyuzXhvspXuTDdVVwGNSHIISyLEcsetdSLnSAdwomqVhXUFsZgBdiYvXW"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 5855232 },
	{ "brand", "WfszeQtSNFDPZLpieNn" },
	{ "issuer", "cWEmGkptwhFMomHOBSRRKjEcYOWghngzYTrNnFMqxxfqWDFyPaeBISKklHBBeKLSlxxtnbtISSsDTvBZXNSVlTGQWwlLPzAjrRN" },
	{ "type", "lGhkazmuxqqDWI" },
	{ "level", "pZfbvJdBApPOOPykNKtEpHWdEniSUZOuEaSwKpSanKuyuzXhvspXuTDdVVwGNSHIISyLEcsetdSLnSAdwomqVhXUFsZgBdiYvXW" }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":5855232,\"brand\":\"WfszeQtSNFDPZLpieNn\",\"issuer\":\"cWEmGkptwhFMomHOBSRRKjEcYOWghngzYTrNnFMqxxfqWDFyPaeBISKklHBBeKLSlxxtnbtISSsDTvBZXNSVlTGQWwlLPzAjrRN\",\"type\":\"lGhkazmuxqqDWI\",\"level\":\"pZfbvJdBApPOOPykNKtEpHWdEniSUZOuEaSwKpSanKuyuzXhvspXuTDdVVwGNSHIISyLEcsetdSLnSAdwomqVhXUFsZgBdiYvXW\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/3617826
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/3617826
```

```javascript
await session.deleteBin(3617826);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(3617826);
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1336533
```

```javascript
const cards = await session.getCards(1336533);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(1336533);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1336533,
  "address_id": 1310090,
  "bin_id": 311258,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "created_on": "1997-07-05T23:03:34.288Z",
  "last_updated_on": "1995-02-18T06:09:18.659Z",
  "expiration_month": 12,
  "expiration_year": 24,
  "cardholder_id": 1508491,
  "par": "WegtXeFSHsUypfQIRADJecaSavueG"
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
  "cardholder_id": 1508491,
  "address_id": 1310090,
  "bin_id": 311258,
  "par": "WegtXeFSHsUypfQIRADJecaSavueG",
  "pan": "arKnNxIXmJVGBeY",
  "cvv": "rvS",
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
	{ "cardholder_id", 1508491 },
	{ "address_id", 1310090 },
	{ "bin_id", 311258 },
	{ "par", "WegtXeFSHsUypfQIRADJecaSavueG" },
	{ "pan", "arKnNxIXmJVGBeY" },
	{ "cvv", "rvS" },
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
curl -d "{\"cardholder_id\":1508491,\"address_id\":1310090,\"bin_id\":311258,\"par\":\"WegtXeFSHsUypfQIRADJecaSavueG\",\"pan\":\"arKnNxIXmJVGBeY\",\"cvv\":\"rvS\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
-X POST -H "Content-Type: application/javascript"
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

<aside class="notice">Create calls to /cardsavr_cards require the cardholder's personal cardholder_safe_key header to encrypt and save the pan and cvv for added security.</aside>

## Update card

```javascript
const card = await session.updateCard({
  "address_id": 6437638,
  "bin_id": 4244979,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
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
	{ "address_id", 6437638 },
	{ "bin_id", 4244979 },
	{ "name_on_card", "Joe C Smith" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "first_6", "000000" },
	{ "first_7", "0000000" },
	{ "first_8", "00000000" }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"address_id\":6437638,\"bin_id\":4244979,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"expiration_month\":12,\"expiration_year\":24,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1336533
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1336533
```

```javascript
await session.deleteCard(1336533, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(1336533, CARDHOLDER_SAFE_KEY);
```

### Path

DELETE /cardsavr_cards/{id}

### Description

Delete a card and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [card response parameters](#response-cardsavr_card).

<aside class="notice">The cardholder_safe_key header is required to delete cards.</aside>


# Users
User objects correspond to a single CardSavr user.
## Get user

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/3374518
```

```javascript
const users = await session.getUsers(3374518);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(3374518);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 3374518,
  "financial_institution_id": 3020348,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1981-12-09T01:34:09.558Z",
  "is_locked": false,
  "password_lifetime": 342,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "admin",
  "phone_number": "GAHctMlCIRjCQU",
  "custom_data": {
    "TGyzlsOtCelj": "N0i>.q{{MZGAR6J1V{.ag{",
    "fSvAJmUhihny": 59,
    "duDXsCLKdOlT": true
  },
  "next_rotation_on": "1977-12-04T08:41:33.911Z",
  "created_on": "1984-10-04T05:55:08.052Z",
  "last_updated_on": "2015-07-05T22:38:56.406Z",
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
  "financial_institution_id": 3020348,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "next_password": "KtcnxDlX5hQLyK7Hv2PX9UNsbIEtp8ncFBxRhfHB/uk=",
  "cardholder_safe_key": "cfr9xUXUX+dJNvsW2MrED51mX9DAK+lSEjJgFdQxtR8=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 342,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "admin",
  "phone_number": "GAHctMlCIRjCQU",
  "custom_data": {
    "TGyzlsOtCelj": "N0i>.q{{MZGAR6J1V{.ag{",
    "fSvAJmUhihny": 59,
    "duDXsCLKdOlT": true
  },
  "next_rotation_on": "1977-12-04T08:41:33.911Z"
}, NEW_CARDHODLER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 3020348 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "next_password", "KtcnxDlX5hQLyK7Hv2PX9UNsbIEtp8ncFBxRhfHB/uk=" },
	{ "cardholder_safe_key", "cfr9xUXUX+dJNvsW2MrED51mX9DAK+lSEjJgFdQxtR8=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 342 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "admin" },
	{ "phone_number", "GAHctMlCIRjCQU" },
	{ "next_rotation_on", "1977-12-04T08:41:33.911Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, NEW_CARDHODLER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":3020348,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"next_password\":\"KtcnxDlX5hQLyK7Hv2PX9UNsbIEtp8ncFBxRhfHB/uk=\",\"cardholder_safe_key\":\"cfr9xUXUX+dJNvsW2MrED51mX9DAK+lSEjJgFdQxtR8=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":342,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"admin\",\"phone_number\":\"GAHctMlCIRjCQU\",\"custom_data\":{\"TGyzlsOtCelj\":\"N0i>.q{{MZGAR6J1V{.ag{\",\"fSvAJmUhihny\":59,\"duDXsCLKdOlT\":true},\"next_rotation_on\":\"1977-12-04T08:41:33.911Z\"}"
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
financial_institution_id | number | no
username | string | yes
password | string | no
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

<aside class="notice">Create calls to /cardsavr_users require the cardholder's personal cardholder_safe_key header to encrypt and save the safe for added security.</aside>

## Update user

```javascript
const user = await session.updateUser({
  "financial_institution_id": 7076833,
  "next_password": "JViHCOJGZQ+N3FQw749RT2o+Y0DmCwuluYqEWwka5MU=",
  "cardholder_safe_key": "Z4XAYWfvamoLX+4UFwb29ahqNMuSnNSNxSTpbi3Covs=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 127,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_agent",
  "phone_number": "GJlDHUApnwaFhi",
  "custom_data": {
    "yWLccLiGkMhW": "WAQ.8E2&T],MgBRoBt*~7B#617",
    "XxcGrmzoSqLO": 66,
    "WkocOZCeZFaD": false
  },
  "next_rotation_on": "1992-01-12T15:38:49.842Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 7076833 },
	{ "next_password", "JViHCOJGZQ+N3FQw749RT2o+Y0DmCwuluYqEWwka5MU=" },
	{ "cardholder_safe_key", "Z4XAYWfvamoLX+4UFwb29ahqNMuSnNSNxSTpbi3Covs=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 127 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "swch_agent" },
	{ "phone_number", "GJlDHUApnwaFhi" },
	{ "next_rotation_on", "1992-01-12T15:38:49.842Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":7076833,\"next_password\":\"JViHCOJGZQ+N3FQw749RT2o+Y0DmCwuluYqEWwka5MU=\",\"cardholder_safe_key\":\"Z4XAYWfvamoLX+4UFwb29ahqNMuSnNSNxSTpbi3Covs=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":127,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"swch_agent\",\"phone_number\":\"GJlDHUApnwaFhi\",\"custom_data\":{\"yWLccLiGkMhW\":\"WAQ.8E2&T],MgBRoBt*~7B#617\",\"XxcGrmzoSqLO\":66,\"WkocOZCeZFaD\":false},\"next_rotation_on\":\"1992-01-12T15:38:49.842Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/3374518
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/3374518
```

```javascript
await session.deleteUser(3374518);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(3374518);
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
https://api.INSTANCE.cardsavr.io/financial_institutions/8519984
```

```javascript
const financial institutions = await session.getFinancial Institutions(8519984);
```

```csharp
CardSavrResponse<Financial Institutions> financial institutions = await session.GetFinancial InstitutionsAsync(8519984);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 8519984,
  "name": "szinNqDqYSqTRaGhLUAjhcjIgkxFmvnAVDjokBTWhrGcfsMhOIqNYHeoUPJlFth",
  "description": "SsyzEKKDAoxAK",
  "lookup_key": "UObdRNYpgcyOOynxXSROaZSnfaJlMnEcLrgtwuYzCOVCezcDChkDJgNELbcvkkZ",
  "alternate_lookup_key": "wKlKZTiYcCkIcGgvFeYindojsyMvwQVqdLZmTsQZvKjouYFztcLZyNUvAQMwfMz",
  "created_on": "1970-03-04T22:44:36.666Z",
  "last_updated_on": "1973-10-13T18:09:59.783Z"
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
const financial institution = await session.createFinancial Institution({
  "name": "szinNqDqYSqTRaGhLUAjhcjIgkxFmvnAVDjokBTWhrGcfsMhOIqNYHeoUPJlFth",
  "description": "SsyzEKKDAoxAK",
  "lookup_key": "UObdRNYpgcyOOynxXSROaZSnfaJlMnEcLrgtwuYzCOVCezcDChkDJgNELbcvkkZ",
  "alternate_lookup_key": "wKlKZTiYcCkIcGgvFeYindojsyMvwQVqdLZmTsQZvKjouYFztcLZyNUvAQMwfMz"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "szinNqDqYSqTRaGhLUAjhcjIgkxFmvnAVDjokBTWhrGcfsMhOIqNYHeoUPJlFth" },
	{ "description", "SsyzEKKDAoxAK" },
	{ "lookup_key", "UObdRNYpgcyOOynxXSROaZSnfaJlMnEcLrgtwuYzCOVCezcDChkDJgNELbcvkkZ" },
	{ "alternate_lookup_key", "wKlKZTiYcCkIcGgvFeYindojsyMvwQVqdLZmTsQZvKjouYFztcLZyNUvAQMwfMz" }
};

CardSavrResponse<Financial Institution> financial institution = await http.CreateFinancial InstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"szinNqDqYSqTRaGhLUAjhcjIgkxFmvnAVDjokBTWhrGcfsMhOIqNYHeoUPJlFth\",\"description\":\"SsyzEKKDAoxAK\",\"lookup_key\":\"UObdRNYpgcyOOynxXSROaZSnfaJlMnEcLrgtwuYzCOVCezcDChkDJgNELbcvkkZ\",\"alternate_lookup_key\":\"wKlKZTiYcCkIcGgvFeYindojsyMvwQVqdLZmTsQZvKjouYFztcLZyNUvAQMwfMz\"}"
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

See [financial institution response attributes](#response-financial_institution).


## Update financial institution

```javascript
const financial institution = await session.updateFinancial Institution({
  "name": "HhDjuvvYYMcCamhJsjhLjXMRzKfOkyFWHtNmMiCSgKhvXtPmEyXFFWriZoFrWSD",
  "description": "AdpEFJGperrjcKCmYf",
  "lookup_key": "ifKOwMsFePJZMqukCoGHQNkFlATOexLCzaxGrMtFWnyxKQQAdaCZKEMveNwZpha",
  "alternate_lookup_key": "LTNRUiSDpUWyUZqCGnLZZRSVWUkPuiAZARpfzifaBWGjkIOhGBAEZeusrwQICaS"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "HhDjuvvYYMcCamhJsjhLjXMRzKfOkyFWHtNmMiCSgKhvXtPmEyXFFWriZoFrWSD" },
	{ "description", "AdpEFJGperrjcKCmYf" },
	{ "lookup_key", "ifKOwMsFePJZMqukCoGHQNkFlATOexLCzaxGrMtFWnyxKQQAdaCZKEMveNwZpha" },
	{ "alternate_lookup_key", "LTNRUiSDpUWyUZqCGnLZZRSVWUkPuiAZARpfzifaBWGjkIOhGBAEZeusrwQICaS" }
};

CardSavrResponse<Financial Institution> financial institution = await http.UpdateFinancial InstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"HhDjuvvYYMcCamhJsjhLjXMRzKfOkyFWHtNmMiCSgKhvXtPmEyXFFWriZoFrWSD\",\"description\":\"AdpEFJGperrjcKCmYf\",\"lookup_key\":\"ifKOwMsFePJZMqukCoGHQNkFlATOexLCzaxGrMtFWnyxKQQAdaCZKEMveNwZpha\",\"alternate_lookup_key\":\"LTNRUiSDpUWyUZqCGnLZZRSVWUkPuiAZARpfzifaBWGjkIOhGBAEZeusrwQICaS\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/8519984
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
https://api.INSTANCE.cardsavr.io/financial_institutions/8519984
```

```javascript
await session.deleteFinancial Institution(8519984);
```

```csharp
CardSavrResponse<Financial Institution> financial institution = await http.DeleteFinancial InstitutionAsync(8519984);
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
https://api.INSTANCE.cardsavr.io/integrators/4684729
```

```javascript
const integrators = await session.getIntegrators(4684729);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(4684729);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 4684729,
  "name": "TIMYSQHrbQlPNiVfjEnciAnumyeSLvdlfHpYGOvnQfwXDhvLn",
  "integrator_type": "swch_internal",
  "description": "JjAl",
  "last_key": "K8JwHgYcomghR6xfSwk6CLVXFkbFBm5Q7BZe6Sg1VAg=",
  "current_key": "sPBIFFrSFVK1HLCPfs89YkY/JE884GA8ZCbeq3knC58=",
  "next_key": "7FfJf/iTakAd1HzbCzQw+akePiPJKqfepqIfav9dueA=",
  "key_lifetime": 85,
  "next_rotation_on": "1979-06-26T20:39:31.368Z",
  "created_on": "2001-10-18T17:29:31.898Z",
  "last_updated_on": "2019-07-17T08:00:04.360Z"
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
  "name": "TIMYSQHrbQlPNiVfjEnciAnumyeSLvdlfHpYGOvnQfwXDhvLn",
  "integrator_type": "swch_internal",
  "description": "JjAl",
  "last_key": "K8JwHgYcomghR6xfSwk6CLVXFkbFBm5Q7BZe6Sg1VAg=",
  "current_key": "sPBIFFrSFVK1HLCPfs89YkY/JE884GA8ZCbeq3knC58=",
  "next_key": "7FfJf/iTakAd1HzbCzQw+akePiPJKqfepqIfav9dueA=",
  "key_lifetime": 85,
  "next_rotation_on": "1979-06-26T20:39:31.368Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "TIMYSQHrbQlPNiVfjEnciAnumyeSLvdlfHpYGOvnQfwXDhvLn" },
	{ "integrator_type", "swch_internal" },
	{ "description", "JjAl" },
	{ "last_key", "K8JwHgYcomghR6xfSwk6CLVXFkbFBm5Q7BZe6Sg1VAg=" },
	{ "current_key", "sPBIFFrSFVK1HLCPfs89YkY/JE884GA8ZCbeq3knC58=" },
	{ "next_key", "7FfJf/iTakAd1HzbCzQw+akePiPJKqfepqIfav9dueA=" },
	{ "key_lifetime", 85 },
	{ "next_rotation_on", "1979-06-26T20:39:31.368Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"TIMYSQHrbQlPNiVfjEnciAnumyeSLvdlfHpYGOvnQfwXDhvLn\",\"integrator_type\":\"swch_internal\",\"description\":\"JjAl\",\"last_key\":\"K8JwHgYcomghR6xfSwk6CLVXFkbFBm5Q7BZe6Sg1VAg=\",\"current_key\":\"sPBIFFrSFVK1HLCPfs89YkY/JE884GA8ZCbeq3knC58=\",\"next_key\":\"7FfJf/iTakAd1HzbCzQw+akePiPJKqfepqIfav9dueA=\",\"key_lifetime\":85,\"next_rotation_on\":\"1979-06-26T20:39:31.368Z\"}"
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
  "name": "IAbGQWdyYJERrAGOqJWhLvyKpdHJMUOjIMUZjbehsEpLegoCf",
  "integrator_type": "swch_internal",
  "description": "UQfFZleqVaFO",
  "last_key": "+MGenaS2ku8nDYb78272k6ERWgb+RogR6NzWVffxgto=",
  "current_key": "iKV9yJjx1VrRjnXefm6ljx6+0y3eu8ONDSAUwzy7uXo=",
  "next_key": "KIxPI2CKJDDryercrQGNs0VrRhxqMyjlit6Jbb+Oqy0=",
  "key_lifetime": 240,
  "next_rotation_on": "2005-09-09T02:59:52.662Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "IAbGQWdyYJERrAGOqJWhLvyKpdHJMUOjIMUZjbehsEpLegoCf" },
	{ "integrator_type", "swch_internal" },
	{ "description", "UQfFZleqVaFO" },
	{ "last_key", "+MGenaS2ku8nDYb78272k6ERWgb+RogR6NzWVffxgto=" },
	{ "current_key", "iKV9yJjx1VrRjnXefm6ljx6+0y3eu8ONDSAUwzy7uXo=" },
	{ "next_key", "KIxPI2CKJDDryercrQGNs0VrRhxqMyjlit6Jbb+Oqy0=" },
	{ "key_lifetime", 240 },
	{ "next_rotation_on", "2005-09-09T02:59:52.662Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"IAbGQWdyYJERrAGOqJWhLvyKpdHJMUOjIMUZjbehsEpLegoCf\",\"integrator_type\":\"swch_internal\",\"description\":\"UQfFZleqVaFO\",\"last_key\":\"+MGenaS2ku8nDYb78272k6ERWgb+RogR6NzWVffxgto=\",\"current_key\":\"iKV9yJjx1VrRjnXefm6ljx6+0y3eu8ONDSAUwzy7uXo=\",\"next_key\":\"KIxPI2CKJDDryercrQGNs0VrRhxqMyjlit6Jbb+Oqy0=\",\"key_lifetime\":240,\"next_rotation_on\":\"2005-09-09T02:59:52.662Z\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/4684729
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
https://api.INSTANCE.cardsavr.io/integrators/4684729
```

```javascript
await session.deleteIntegrator(4684729);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(4684729);
```

### Path

DELETE /integrators/{id}

### Description

Delete a integrator and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [integrator response parameters](#response-integrator).


# Merchant Sites
Merchant site objects contain information about CardSavr-supported merchant sites.
## Get merchant site

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/merchant_sites/1479309
```

```javascript
const merchant sites = await session.getMerchant Sites(1479309);
```

```csharp
CardSavrResponse<Merchant Sites> merchant sites = await session.GetMerchant SitesAsync(1479309);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1479309,
  "name": "iLQfOULCKFUWldNzYsuaWY",
  "host": "pEXdMGsLFFczAEMpiPaUIlK",
  "image_lookup_key": "gcSNqmeSEJP",
  "images": [
    {
      "xpskRvrldkCD": "3$pwO<e727",
      "hAOlPCzWKziG": 94,
      "AtfrncPIsYZT": false
    },
    {
      "IkAOdnrnElIJ": "2p1",
      "MTlfurYJtNOW": 99,
      "HLZkZLUURqUA": true
    },
    {
      "nxjzzcJbWFqR": "Z-f3(!YUEl3tFQU+J=GyZh~_",
      "sXmWRqaJYUWS": 60,
      "YdWyzWUxwoVY": false
    }
  ],
  "mfa": false,
  "tags": "aOrHVEYIOFKcskFDOYnvzghwtA",
  "login": {
    "PyfYXpIdctHh": "vTHdb%_R(Z%mc32F2fcV2/U#fQ5#]}r",
    "VWNWSEPfaifc": 62,
    "IwkUpKHrMqTv": true
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
A noficiation record that defines how to take action CardSavr events like jobs completing or sessions ending.
## Get notification

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/2559996
```

```javascript
const notifications = await session.getNotifications(2559996);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(2559996);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2559996,
  "name": "ysqppZWSPbLZQMIKWBofqVQvMLMLflxQbgYWtypFBIJtCHilIaaAdeBOXfAVJWc",
  "type": "email",
  "config": {
    "ECcevvhybtAK": "*#zokbL",
    "DinVVyXDNzfW": 59,
    "rmukHPBHvvBc": false
  },
  "created_on": "2014-01-16T23:06:43.309Z",
  "last_updated_on": "1987-10-02T16:09:24.624Z",
  "financial_institution_id": 1864695
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
  "financial_institution_id": 1864695,
  "name": "ysqppZWSPbLZQMIKWBofqVQvMLMLflxQbgYWtypFBIJtCHilIaaAdeBOXfAVJWc",
  "type": "email",
  "config": {
    "ECcevvhybtAK": "*#zokbL",
    "DinVVyXDNzfW": 59,
    "rmukHPBHvvBc": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1864695 },
	{ "name", "ysqppZWSPbLZQMIKWBofqVQvMLMLflxQbgYWtypFBIJtCHilIaaAdeBOXfAVJWc" },
	{ "type", "email" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":1864695,\"name\":\"ysqppZWSPbLZQMIKWBofqVQvMLMLflxQbgYWtypFBIJtCHilIaaAdeBOXfAVJWc\",\"type\":\"email\",\"config\":{\"ECcevvhybtAK\":\"*#zokbL\",\"DinVVyXDNzfW\":59,\"rmukHPBHvvBc\":false}}"
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
  "name": "SnTAGHraczomEiymQYXsgsUxQcmAjUJkWGpnhtDnbCMWjkwtgxVkwPhjhngiXYE",
  "type": "webhook",
  "config": {
    "qgSqITBVxhjz": "aunqWGZWp_f7Q_*C-%)L!+em#",
    "nMQghhYZzHnA": 22,
    "hjLkOIEiTscw": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "SnTAGHraczomEiymQYXsgsUxQcmAjUJkWGpnhtDnbCMWjkwtgxVkwPhjhngiXYE" },
	{ "type", "webhook" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```shell
curl -d "{\"name\":\"SnTAGHraczomEiymQYXsgsUxQcmAjUJkWGpnhtDnbCMWjkwtgxVkwPhjhngiXYE\",\"type\":\"webhook\",\"config\":{\"qgSqITBVxhjz\":\"aunqWGZWp_f7Q_*C-%)L!+em#\",\"nMQghhYZzHnA\":22,\"hjLkOIEiTscw\":true}}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/2559996
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
https://api.INSTANCE.cardsavr.io/notifications/2559996
```

```javascript
await session.deleteNotification(2559996);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(2559996);
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/7899847
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(7899847);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(7899847);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 7899847,
  "card_placement_result_id": "bGsixTAphWWGcmLluqL",
  "status": "TIMEOUT_CREDENTIALS",
  "safe_blob": "niQw",
  "safe_nonce": "cDRElHpmIZSyozSwhRqUsbeJpQHsQXdm",
  "custom_data": {
    "rqcKYseLoXjJ": "V.##BgUgjG1zfpX2rmNsC>g5q4WMg~>",
    "GKZiRSPkoyoN": 57,
    "ksiYlfEmABOc": false
  },
  "failure_reason": "gDUJavtBWmH",
  "messaging_addresses": "HFTkJkYCAaQ",
  "current_state": "jgAppAguJYOnvaPluWkaAzcUPejvBlRxQSaMhgSumEtcYVgGCzNVBbKTtDPmsEG",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 6532709,
  "job_ready_on": "1994-03-01T20:33:37.924Z",
  "started_on": "2020-03-19T09:33:48.979Z",
  "completed_on": "2015-02-25T23:01:34.775Z",
  "expiration_date": "2008-06-12T12:30:47.204Z",
  "created_on": "1992-11-26T04:56:06.019Z",
  "last_updated_on": "2001-07-16T22:37:56.507Z",
  "user_id": 5317468,
  "card_id": 9663291,
  "account_id": 7013403
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
safe_blob | string | 
safe_nonce | string | 
queue_name | string | 
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
- queue_name
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
  "place_card_on_multiple_sites_job_id": 4767858,
  "user_id": 5317468,
  "card_id": 9663291,
  "account_id": 7013403,
  "status": "TIMEOUT_CREDENTIALS",
  "custom_data": {
    "rqcKYseLoXjJ": "V.##BgUgjG1zfpX2rmNsC>g5q4WMg~>",
    "GKZiRSPkoyoN": 57,
    "ksiYlfEmABOc": false
  },
  "failure_reason": "gDUJavtBWmH",
  "current_state": "jgAppAguJYOnvaPluWkaAzcUPejvBlRxQSaMhgSumEtcYVgGCzNVBbKTtDPmsEG",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 6532709,
  "started_on": "2020-03-19T09:33:48.979Z",
  "completed_on": "2015-02-25T23:01:34.775Z",
  "expiration_date": "2008-06-12T12:30:47.204Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "place_card_on_multiple_sites_job_id", 4767858 },
	{ "user_id", 5317468 },
	{ "card_id", 9663291 },
	{ "account_id", 7013403 },
	{ "status", "TIMEOUT_CREDENTIALS" },
	{ "failure_reason", "gDUJavtBWmH" },
	{ "current_state", "jgAppAguJYOnvaPluWkaAzcUPejvBlRxQSaMhgSumEtcYVgGCzNVBbKTtDPmsEG" },
	{ "do_not_queue", true },
	{ "user_is_present", false },
	{ "time_elapsed", 6532709 },
	{ "started_on", "2020-03-19T09:33:48.979Z" },
	{ "completed_on", "2015-02-25T23:01:34.775Z" },
	{ "expiration_date", "2008-06-12T12:30:47.204Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"place_card_on_multiple_sites_job_id\":4767858,\"user_id\":5317468,\"card_id\":9663291,\"account_id\":7013403,\"status\":\"TIMEOUT_CREDENTIALS\",\"custom_data\":{\"rqcKYseLoXjJ\":\"V.##BgUgjG1zfpX2rmNsC>g5q4WMg~>\",\"GKZiRSPkoyoN\":57,\"ksiYlfEmABOc\":false},\"failure_reason\":\"gDUJavtBWmH\",\"current_state\":\"jgAppAguJYOnvaPluWkaAzcUPejvBlRxQSaMhgSumEtcYVgGCzNVBbKTtDPmsEG\",\"do_not_queue\":true,\"user_is_present\":false,\"time_elapsed\":6532709,\"started_on\":\"2020-03-19T09:33:48.979Z\",\"completed_on\":\"2015-02-25T23:01:34.775Z\",\"expiration_date\":\"2008-06-12T12:30:47.204Z\"}"
-X POST -H "Content-Type: application/javascript"
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
queue_name | [string enum](#post-place_card_on_single_site_job-2)** | no
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

#### <a name="post-place_card_on_single_site_job-2"></a>string enum**
- vbs_queue

<aside class="notice">Create calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe for added security.</aside>

## Update single-site job

```javascript
const singlesitejob = await session.updateSingleSiteJob({
  "status": "UNSUCCESSFUL",
  "custom_data": {
    "UBCyXNqajwPy": "l1L$/",
    "FwjBgfaZHFOF": 43,
    "oFOlFaxUAfdq": false
  },
  "failure_reason": "EqhcnRvAoy",
  "current_state": "vwFbqHuWFsBIgXiuiADySceuZMhqTZOAnwqogOVCXHIPFuwfTFNrCjINIcbrKXL",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 5549767,
  "started_on": "2005-10-10T16:59:35.990Z",
  "completed_on": "2010-11-22T22:08:06.287Z",
  "expiration_date": "2013-01-12T10:06:42.631Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "status", "UNSUCCESSFUL" },
	{ "failure_reason", "EqhcnRvAoy" },
	{ "current_state", "vwFbqHuWFsBIgXiuiADySceuZMhqTZOAnwqogOVCXHIPFuwfTFNrCjINIcbrKXL" },
	{ "do_not_queue", true },
	{ "user_is_present", false },
	{ "time_elapsed", 5549767 },
	{ "started_on", "2005-10-10T16:59:35.990Z" },
	{ "completed_on", "2010-11-22T22:08:06.287Z" },
	{ "expiration_date", "2013-01-12T10:06:42.631Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"status\":\"UNSUCCESSFUL\",\"custom_data\":{\"UBCyXNqajwPy\":\"l1L$/\",\"FwjBgfaZHFOF\":43,\"oFOlFaxUAfdq\":false},\"failure_reason\":\"EqhcnRvAoy\",\"current_state\":\"vwFbqHuWFsBIgXiuiADySceuZMhqTZOAnwqogOVCXHIPFuwfTFNrCjINIcbrKXL\",\"do_not_queue\":true,\"user_is_present\":false,\"time_elapsed\":5549767,\"started_on\":\"2005-10-10T16:59:35.990Z\",\"completed_on\":\"2010-11-22T22:08:06.287Z\",\"expiration_date\":\"2013-01-12T10:06:42.631Z\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/7899847
```

### Path

PUT /place_card_on_single_site_jobs OR /place_card_on_single_site_jobs/{id}

### Description

Update a single-site job and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
status | [string enum](#post-place_card_on_single_site_job-1)* |
queue_name | [string enum](#post-place_card_on_single_site_job-2)** |
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

<aside class="notice">Update calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe for added security. The safe keys are not required if updating other user properties.</aside>

## Delete single-site job

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/7899847
```

```javascript
await session.deleteSingleSiteJob(7899847);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(7899847);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [single-site job response parameters](#response-place_card_on_single_site_job).

