
# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1254917610
```

```javascript
const accounts = await session.getAccounts(1254917610);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(1254917610);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1254917610,
  "last_card_placed_id": 1434361030,
  "last_login": "1985-06-26T05:00:05.188Z",
  "last_password_update": "2005-08-09T21:21:34.102Z",
  "last_saved_card": "2008-11-20T19:29:01.139Z",
  "created_on": "2012-11-24T08:49:17.699Z",
  "last_updated_on": "1971-11-03T07:21:50.826Z",
  "cardholder_id": 750294823,
  "merchant_site_id": 414264814
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
  "cardholder_id": 750294823,
  "merchant_site_id": 414264814,
  "last_card_placed_id": 1434361030,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 750294823 },
	{ "merchant_site_id", 414264814 },
	{ "last_card_placed_id", 1434361030 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":750294823,\"merchant_site_id\":414264814,\"last_card_placed_id\":1434361030,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
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
  "last_card_placed_id": 1739525609,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 1739525609 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"last_card_placed_id\":1739525609,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1254917610
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
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1254917610
```

```javascript
await session.deleteAccount(1254917610, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(1254917610, CARDHOLDER_SAFE_KEY);
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/63017600
```

```javascript
const addresses = await session.getAddresses(63017600);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(63017600);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 63017600,
  "address1": "SGTClNSCCMqlfjuzTmJuepDyFgvWhlCMRycXlKGiRIooOJJkoXeObOcAwJMGeqjSDWfhTHobAWMimcCynMIQcvlBFSbMQlwUFyJ",
  "address2": "AyFgoCTjCLXUQVylBAfkHJOtqkkKJjuaLHnmJpSctqBOQueIvciyAUPqYoFpkiAPlkGjgPuabhAPCHFPvaxciObOmIBvBUWpngD",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "created_on": "2014-07-31T13:06:28.866Z",
  "last_updated_on": "1975-01-29T15:40:11.758Z",
  "user_id": 2081302826
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
  "user_id": 2081302826,
  "address1": "SGTClNSCCMqlfjuzTmJuepDyFgvWhlCMRycXlKGiRIooOJJkoXeObOcAwJMGeqjSDWfhTHobAWMimcCynMIQcvlBFSbMQlwUFyJ",
  "address2": "AyFgoCTjCLXUQVylBAfkHJOtqkkKJjuaLHnmJpSctqBOQueIvciyAUPqYoFpkiAPlkGjgPuabhAPCHFPvaxciObOmIBvBUWpngD",
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
	{ "user_id", 2081302826 },
	{ "address1", "SGTClNSCCMqlfjuzTmJuepDyFgvWhlCMRycXlKGiRIooOJJkoXeObOcAwJMGeqjSDWfhTHobAWMimcCynMIQcvlBFSbMQlwUFyJ" },
	{ "address2", "AyFgoCTjCLXUQVylBAfkHJOtqkkKJjuaLHnmJpSctqBOQueIvciyAUPqYoFpkiAPlkGjgPuabhAPCHFPvaxciObOmIBvBUWpngD" },
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
curl -d "{\"user_id\":2081302826,\"address1\":\"SGTClNSCCMqlfjuzTmJuepDyFgvWhlCMRycXlKGiRIooOJJkoXeObOcAwJMGeqjSDWfhTHobAWMimcCynMIQcvlBFSbMQlwUFyJ\",\"address2\":\"AyFgoCTjCLXUQVylBAfkHJOtqkkKJjuaLHnmJpSctqBOQueIvciyAUPqYoFpkiAPlkGjgPuabhAPCHFPvaxciObOmIBvBUWpngD\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true}"
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
  "address1": "esFiEgaRLTRYDiAasjYFgIHjImXzWvBHsBsEGCHwNehxjiogcXZdHoBWaSeNwvwcQGUgcTPGXIWTOPGIVrOBPqocbuFYmCZnfxR",
  "address2": "pjTyizRhJpVLZyRIZglUtyvOIxrWtOzVyHFPLuYAzEIWwfOAFJKspYoClBEmvDiiBNpRDXrMXWGfnTDvAjTPTdRQJFNoaYsrQgP",
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
	{ "address1", "esFiEgaRLTRYDiAasjYFgIHjImXzWvBHsBsEGCHwNehxjiogcXZdHoBWaSeNwvwcQGUgcTPGXIWTOPGIVrOBPqocbuFYmCZnfxR" },
	{ "address2", "pjTyizRhJpVLZyRIZglUtyvOIxrWtOzVyHFPLuYAzEIWwfOAFJKspYoClBEmvDiiBNpRDXrMXWGfnTDvAjTPTdRQJFNoaYsrQgP" },
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
curl -d "{\"address1\":\"esFiEgaRLTRYDiAasjYFgIHjImXzWvBHsBsEGCHwNehxjiogcXZdHoBWaSeNwvwcQGUgcTPGXIWTOPGIVrOBPqocbuFYmCZnfxR\",\"address2\":\"pjTyizRhJpVLZyRIZglUtyvOIxrWtOzVyHFPLuYAzEIWwfOAFJKspYoClBEmvDiiBNpRDXrMXWGfnTDvAjTPTdRQJFNoaYsrQgP\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/63017600
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/63017600
```

```javascript
await session.deleteAddress(63017600);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(63017600);
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1068245439
```

```javascript
const bins = await session.getBins(1068245439);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(1068245439);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1068245439,
  "financial_institution_id": 21597956,
  "created_on": "2019-03-18T18:48:13.718Z",
  "last_updated_on": "2017-11-13T06:26:38.646Z",
  "bank_identification_number": "57610465"
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
  "financial_institution_id": 21597956,
  "bank_identification_number": "57610465",
  "brand": "ggmOuIooyOxrbdTuItd",
  "issuer": "qLkiICwDgBbBaiuDwGjYZyztwzwxLPxhOZwtRVGwBpRhHWIJRpEwnxSZchAzisSKjZlMipTqxJJgGrpacIrFHJUIazoRVSjXRVe",
  "type": "kSOWgHaVoJEJOv",
  "level": "VRktFWpetQDhlJaiwRtSKBLsoGLuoIvRZxmpbeyxKZSBScQOzlmVIuxsxlfzNamQxUBZEnasRcjSDbaewVGWAcZEIzAFvRwOTpa"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 21597956 },
	{ "bank_identification_number", "57610465" },
	{ "brand", "ggmOuIooyOxrbdTuItd" },
	{ "issuer", "qLkiICwDgBbBaiuDwGjYZyztwzwxLPxhOZwtRVGwBpRhHWIJRpEwnxSZchAzisSKjZlMipTqxJJgGrpacIrFHJUIazoRVSjXRVe" },
	{ "type", "kSOWgHaVoJEJOv" },
	{ "level", "VRktFWpetQDhlJaiwRtSKBLsoGLuoIvRZxmpbeyxKZSBScQOzlmVIuxsxlfzNamQxUBZEnasRcjSDbaewVGWAcZEIzAFvRwOTpa" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":21597956,\"bank_identification_number\":\"57610465\",\"brand\":\"ggmOuIooyOxrbdTuItd\",\"issuer\":\"qLkiICwDgBbBaiuDwGjYZyztwzwxLPxhOZwtRVGwBpRhHWIJRpEwnxSZchAzisSKjZlMipTqxJJgGrpacIrFHJUIazoRVSjXRVe\",\"type\":\"kSOWgHaVoJEJOv\",\"level\":\"VRktFWpetQDhlJaiwRtSKBLsoGLuoIvRZxmpbeyxKZSBScQOzlmVIuxsxlfzNamQxUBZEnasRcjSDbaewVGWAcZEIzAFvRwOTpa\"}"
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
  "financial_institution_id": 72022,
  "brand": "AggqlDwBapKsxtPeCDN",
  "issuer": "wxJbzgpMVbALgLQGNmNDKZIbmTYfWVWkmmVjezktlBWjuxYswpDWsiHTJvLkHWULQHEaFzrhIzdQYpRrZYrowlIIkCizViFoOHS",
  "type": "vFMnjzptQqdxGt",
  "level": "hnraJNdgYaEtlxDuaWCnIZoHmtytEbLvCxlQMMDWqhGAcliNJWrtDNnMkAyrwiQCpRPxPIPMtFTwolDPIGXLKuPPoonWDRGcWYm"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 72022 },
	{ "brand", "AggqlDwBapKsxtPeCDN" },
	{ "issuer", "wxJbzgpMVbALgLQGNmNDKZIbmTYfWVWkmmVjezktlBWjuxYswpDWsiHTJvLkHWULQHEaFzrhIzdQYpRrZYrowlIIkCizViFoOHS" },
	{ "type", "vFMnjzptQqdxGt" },
	{ "level", "hnraJNdgYaEtlxDuaWCnIZoHmtytEbLvCxlQMMDWqhGAcliNJWrtDNnMkAyrwiQCpRPxPIPMtFTwolDPIGXLKuPPoonWDRGcWYm" }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":72022,\"brand\":\"AggqlDwBapKsxtPeCDN\",\"issuer\":\"wxJbzgpMVbALgLQGNmNDKZIbmTYfWVWkmmVjezktlBWjuxYswpDWsiHTJvLkHWULQHEaFzrhIzdQYpRrZYrowlIIkCizViFoOHS\",\"type\":\"vFMnjzptQqdxGt\",\"level\":\"hnraJNdgYaEtlxDuaWCnIZoHmtytEbLvCxlQMMDWqhGAcliNJWrtDNnMkAyrwiQCpRPxPIPMtFTwolDPIGXLKuPPoonWDRGcWYm\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1068245439
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1068245439
```

```javascript
await session.deleteBin(1068245439);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(1068245439);
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/700666573
```

```javascript
const cards = await session.getCards(700666573);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(700666573);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 700666573,
  "address_id": 45385119,
  "bin_id": 1440114383,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "created_on": "1990-11-27T02:25:35.592Z",
  "last_updated_on": "2010-08-26T01:25:24.762Z",
  "expiration_month": 12,
  "expiration_year": 24,
  "cardholder_id": 826588782,
  "par": "peLpzDnEHdhiiWEtuhUgICEonxScm"
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
  "cardholder_id": 826588782,
  "address_id": 45385119,
  "bin_id": 1440114383,
  "par": "peLpzDnEHdhiiWEtuhUgICEonxScm",
  "pan": "KOnalFfwdrBXlZD",
  "cvv": "oAc",
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
	{ "cardholder_id", 826588782 },
	{ "address_id", 45385119 },
	{ "bin_id", 1440114383 },
	{ "par", "peLpzDnEHdhiiWEtuhUgICEonxScm" },
	{ "pan", "KOnalFfwdrBXlZD" },
	{ "cvv", "oAc" },
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
curl -d "{\"cardholder_id\":826588782,\"address_id\":45385119,\"bin_id\":1440114383,\"par\":\"peLpzDnEHdhiiWEtuhUgICEonxScm\",\"pan\":\"KOnalFfwdrBXlZD\",\"cvv\":\"oAc\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
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
  "address_id": 1411017416,
  "bin_id": 1662363636,
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
	{ "address_id", 1411017416 },
	{ "bin_id", 1662363636 },
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
curl -d "{\"address_id\":1411017416,\"bin_id\":1662363636,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"expiration_month\":12,\"expiration_year\":24,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/700666573
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/700666573
```

```javascript
await session.deleteCard(700666573, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(700666573, CARDHOLDER_SAFE_KEY);
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/1248542319
```

```javascript
const users = await session.getUsers(1248542319);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(1248542319);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1248542319,
  "financial_institution_id": 752705796,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "2005-10-08T08:23:13.754Z",
  "is_locked": false,
  "password_lifetime": 126,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "swch_agent",
  "phone_number": "nwwoliauzqRUdy",
  "custom_data": {
    "bBebEJyzNtMy": "}[*T(r})WVf~$9mB$c5%(RuJ1!cZ",
    "CgwTsPNRyhcK": 79,
    "dGAbWLYXOiCe": false
  },
  "next_rotation_on": "2014-02-04T19:44:36.841Z",
  "created_on": "1985-11-03T04:46:38.691Z",
  "last_updated_on": "1981-10-17T07:23:46.866Z",
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
  "financial_institution_id": 752705796,
  "username": "jsmith123",
  "last_password": "TqtLHPoI73dXI9palXHGmK6zZeJEz9CpDgXCMwgua3s=",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "next_password": "jbG2I7YlBBP5huqSu2C+TihxGq1OwQzeTiK2SSGf2hE=",
  "expired_password_1": "TsBuiZFSxifV8fZkB2riSL4zYx7eR+uqipaztlfdbKo=",
  "expired_password_2": "WYCnDg24LSUZEaCE7kM6qzw6VA8GMVSiAOFD7gZPqYo=",
  "cardholder_safe_key": "KQY1TrLsywrPWEg65VcCn8Ww8F4/G3Z6kGc2wxsCjaQ=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 126,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "swch_agent",
  "phone_number": "nwwoliauzqRUdy",
  "custom_data": {
    "bBebEJyzNtMy": "}[*T(r})WVf~$9mB$c5%(RuJ1!cZ",
    "CgwTsPNRyhcK": 79,
    "dGAbWLYXOiCe": false
  },
  "next_rotation_on": "2014-02-04T19:44:36.841Z"
}, NEW_CARDHODLER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 752705796 },
	{ "username", "jsmith123" },
	{ "last_password", "TqtLHPoI73dXI9palXHGmK6zZeJEz9CpDgXCMwgua3s=" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "next_password", "jbG2I7YlBBP5huqSu2C+TihxGq1OwQzeTiK2SSGf2hE=" },
	{ "expired_password_1", "TsBuiZFSxifV8fZkB2riSL4zYx7eR+uqipaztlfdbKo=" },
	{ "expired_password_2", "WYCnDg24LSUZEaCE7kM6qzw6VA8GMVSiAOFD7gZPqYo=" },
	{ "cardholder_safe_key", "KQY1TrLsywrPWEg65VcCn8Ww8F4/G3Z6kGc2wxsCjaQ=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 126 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "swch_agent" },
	{ "phone_number", "nwwoliauzqRUdy" },
	{ "next_rotation_on", "2014-02-04T19:44:36.841Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, NEW_CARDHODLER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":752705796,\"username\":\"jsmith123\",\"last_password\":\"TqtLHPoI73dXI9palXHGmK6zZeJEz9CpDgXCMwgua3s=\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"next_password\":\"jbG2I7YlBBP5huqSu2C+TihxGq1OwQzeTiK2SSGf2hE=\",\"expired_password_1\":\"TsBuiZFSxifV8fZkB2riSL4zYx7eR+uqipaztlfdbKo=\",\"expired_password_2\":\"WYCnDg24LSUZEaCE7kM6qzw6VA8GMVSiAOFD7gZPqYo=\",\"cardholder_safe_key\":\"KQY1TrLsywrPWEg65VcCn8Ww8F4/G3Z6kGc2wxsCjaQ=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":126,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"swch_agent\",\"phone_number\":\"nwwoliauzqRUdy\",\"custom_data\":{\"bBebEJyzNtMy\":\"}[*T(r})WVf~$9mB$c5%(RuJ1!cZ\",\"CgwTsPNRyhcK\":79,\"dGAbWLYXOiCe\":false},\"next_rotation_on\":\"2014-02-04T19:44:36.841Z\"}"
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
  "financial_institution_id": 66900656,
  "last_password": "Jy0qQFOseUmLrGnya+1RW0QydqmcWiVHdeaALntm08U=",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "next_password": "Szwvzv14vfAr0t/f6ks2SqzxZX7Daq2ECr59FuwyovU=",
  "expired_password_1": "tb16J4Bo5lSDmD+5Fpi7p7wEgUXrveGw+LWHaPaVVYM=",
  "expired_password_2": "+LgIucRe5iKEVKzgJk0NZApY3jNJTqGfsYfr7igjORU=",
  "cardholder_safe_key": "fsqQoYnKIuH/1niMj0+pZ26akHTi2S0oxSwN8dxK1Ac=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 306,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "cardholder",
  "phone_number": "LlCuEAkuVYkkzP",
  "custom_data": {
    "gAhjfBIqHtkO": "q#+(U>&eq",
    "yJcSmoErlyyv": 92,
    "EQcYOuivYGoK": true
  },
  "next_rotation_on": "1981-02-09T07:43:28.580Z",
  "username": "jsmith123"
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 66900656 },
	{ "last_password", "Jy0qQFOseUmLrGnya+1RW0QydqmcWiVHdeaALntm08U=" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "next_password", "Szwvzv14vfAr0t/f6ks2SqzxZX7Daq2ECr59FuwyovU=" },
	{ "expired_password_1", "tb16J4Bo5lSDmD+5Fpi7p7wEgUXrveGw+LWHaPaVVYM=" },
	{ "expired_password_2", "+LgIucRe5iKEVKzgJk0NZApY3jNJTqGfsYfr7igjORU=" },
	{ "cardholder_safe_key", "fsqQoYnKIuH/1niMj0+pZ26akHTi2S0oxSwN8dxK1Ac=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 306 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "cardholder" },
	{ "phone_number", "LlCuEAkuVYkkzP" },
	{ "next_rotation_on", "1981-02-09T07:43:28.580Z" },
	{ "username", "jsmith123" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":66900656,\"last_password\":\"Jy0qQFOseUmLrGnya+1RW0QydqmcWiVHdeaALntm08U=\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"next_password\":\"Szwvzv14vfAr0t/f6ks2SqzxZX7Daq2ECr59FuwyovU=\",\"expired_password_1\":\"tb16J4Bo5lSDmD+5Fpi7p7wEgUXrveGw+LWHaPaVVYM=\",\"expired_password_2\":\"+LgIucRe5iKEVKzgJk0NZApY3jNJTqGfsYfr7igjORU=\",\"cardholder_safe_key\":\"fsqQoYnKIuH/1niMj0+pZ26akHTi2S0oxSwN8dxK1Ac=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":306,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"cardholder\",\"phone_number\":\"LlCuEAkuVYkkzP\",\"custom_data\":{\"gAhjfBIqHtkO\":\"q#+(U>&eq\",\"yJcSmoErlyyv\":92,\"EQcYOuivYGoK\":true},\"next_rotation_on\":\"1981-02-09T07:43:28.580Z\",\"username\":\"jsmith123\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/1248542319
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/1248542319
```

```javascript
await session.deleteUser(1248542319);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(1248542319);
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
https://api.INSTANCE.cardsavr.io/financial_institutions/525502309
```

```javascript
const financialinstitutions = await session.getFinancialInstitutions(525502309);
```

```csharp
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(525502309);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 525502309,
  "name": "HkjUocrhdXQMEdWGzoWFHbTaMMZGjqpNVqIuNUAYcACSvTHlGrPEicHiqEislYj",
  "description": "DWtztCQiCECpSmjeIuvYilDU",
  "lookup_key": "BFNAMHWjHSqxqjnkUWzwEMHSmzgUmUqrrmfLjOamqANQLrQjPMpVJbgqlRUEwYx",
  "alternate_lookup_key": "QckAIoqvGoTRIIIctTKfAysqTyOspHDlBXNUkdTfDZdKluFxkswPOxWDCjFrzuy",
  "created_on": "2015-08-26T06:17:20.269Z",
  "last_updated_on": "2017-03-14T07:03:46.739Z"
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
  "name": "HkjUocrhdXQMEdWGzoWFHbTaMMZGjqpNVqIuNUAYcACSvTHlGrPEicHiqEislYj",
  "description": "DWtztCQiCECpSmjeIuvYilDU",
  "lookup_key": "BFNAMHWjHSqxqjnkUWzwEMHSmzgUmUqrrmfLjOamqANQLrQjPMpVJbgqlRUEwYx",
  "alternate_lookup_key": "QckAIoqvGoTRIIIctTKfAysqTyOspHDlBXNUkdTfDZdKluFxkswPOxWDCjFrzuy"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "HkjUocrhdXQMEdWGzoWFHbTaMMZGjqpNVqIuNUAYcACSvTHlGrPEicHiqEislYj" },
	{ "description", "DWtztCQiCECpSmjeIuvYilDU" },
	{ "lookup_key", "BFNAMHWjHSqxqjnkUWzwEMHSmzgUmUqrrmfLjOamqANQLrQjPMpVJbgqlRUEwYx" },
	{ "alternate_lookup_key", "QckAIoqvGoTRIIIctTKfAysqTyOspHDlBXNUkdTfDZdKluFxkswPOxWDCjFrzuy" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"HkjUocrhdXQMEdWGzoWFHbTaMMZGjqpNVqIuNUAYcACSvTHlGrPEicHiqEislYj\",\"description\":\"DWtztCQiCECpSmjeIuvYilDU\",\"lookup_key\":\"BFNAMHWjHSqxqjnkUWzwEMHSmzgUmUqrrmfLjOamqANQLrQjPMpVJbgqlRUEwYx\",\"alternate_lookup_key\":\"QckAIoqvGoTRIIIctTKfAysqTyOspHDlBXNUkdTfDZdKluFxkswPOxWDCjFrzuy\"}"
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
const financialinstitution = await session.updateFinancialInstitution({
  "name": "swOMsSNTOZfflyuXkUbjMybTYFbWoGZARcsgaHDhKQEDzZNIsMUrpwahZCWmopw",
  "description": "GAzwNDLJ",
  "lookup_key": "tAhYvVNABdjVhHdyKuVOILHgmKqpIPHHfdtLcowYRKbuBbXgUMelJaAsGdSopJU",
  "alternate_lookup_key": "tyUXHcXAniFcxAFdxAbuDkNMOytIddKLrOBAWyOchhZHDKeqYixunwCiyscMLWD"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "swOMsSNTOZfflyuXkUbjMybTYFbWoGZARcsgaHDhKQEDzZNIsMUrpwahZCWmopw" },
	{ "description", "GAzwNDLJ" },
	{ "lookup_key", "tAhYvVNABdjVhHdyKuVOILHgmKqpIPHHfdtLcowYRKbuBbXgUMelJaAsGdSopJU" },
	{ "alternate_lookup_key", "tyUXHcXAniFcxAFdxAbuDkNMOytIddKLrOBAWyOchhZHDKeqYixunwCiyscMLWD" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"swOMsSNTOZfflyuXkUbjMybTYFbWoGZARcsgaHDhKQEDzZNIsMUrpwahZCWmopw\",\"description\":\"GAzwNDLJ\",\"lookup_key\":\"tAhYvVNABdjVhHdyKuVOILHgmKqpIPHHfdtLcowYRKbuBbXgUMelJaAsGdSopJU\",\"alternate_lookup_key\":\"tyUXHcXAniFcxAFdxAbuDkNMOytIddKLrOBAWyOchhZHDKeqYixunwCiyscMLWD\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/525502309
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
https://api.INSTANCE.cardsavr.io/financial_institutions/525502309
```

```javascript
await session.deleteFinancialInstitution(525502309);
```

```csharp
CardSavrResponse<FinancialInstitution> financialinstitution = await http.DeleteFinancialInstitutionAsync(525502309);
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
https://api.INSTANCE.cardsavr.io/integrators/1646209542
```

```javascript
const integrators = await session.getIntegrators(1646209542);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(1646209542);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1646209542,
  "name": "rDozmvFKevafVHJQPOftqvVcfFHIAyhLlIJpiYsttmdGRWeaY",
  "integrator_type": "application",
  "description": "JstdTzaRsxahBuvxwqo",
  "last_key": "7tfnslrd7ZOq5ER+sbjqBAEW2QesHEya80iUjD9kifA=",
  "current_key": "RoKnkfro+5rvtl8F38p01kk+APwjdaWzmuiKJrGz/vA=",
  "next_key": "Hh7QIfDyVTqhpo+hDx+Tjn9bKv8sa5sTzd89bE7cT7k=",
  "key_lifetime": 227,
  "next_rotation_on": "1987-08-02T03:22:19.292Z",
  "created_on": "1984-04-03T11:46:47.574Z",
  "last_updated_on": "2016-10-23T05:56:25.972Z"
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
  "name": "rDozmvFKevafVHJQPOftqvVcfFHIAyhLlIJpiYsttmdGRWeaY",
  "integrator_type": "application",
  "description": "JstdTzaRsxahBuvxwqo",
  "last_key": "7tfnslrd7ZOq5ER+sbjqBAEW2QesHEya80iUjD9kifA=",
  "current_key": "RoKnkfro+5rvtl8F38p01kk+APwjdaWzmuiKJrGz/vA=",
  "next_key": "Hh7QIfDyVTqhpo+hDx+Tjn9bKv8sa5sTzd89bE7cT7k=",
  "key_lifetime": 227,
  "next_rotation_on": "1987-08-02T03:22:19.292Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "rDozmvFKevafVHJQPOftqvVcfFHIAyhLlIJpiYsttmdGRWeaY" },
	{ "integrator_type", "application" },
	{ "description", "JstdTzaRsxahBuvxwqo" },
	{ "last_key", "7tfnslrd7ZOq5ER+sbjqBAEW2QesHEya80iUjD9kifA=" },
	{ "current_key", "RoKnkfro+5rvtl8F38p01kk+APwjdaWzmuiKJrGz/vA=" },
	{ "next_key", "Hh7QIfDyVTqhpo+hDx+Tjn9bKv8sa5sTzd89bE7cT7k=" },
	{ "key_lifetime", 227 },
	{ "next_rotation_on", "1987-08-02T03:22:19.292Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"rDozmvFKevafVHJQPOftqvVcfFHIAyhLlIJpiYsttmdGRWeaY\",\"integrator_type\":\"application\",\"description\":\"JstdTzaRsxahBuvxwqo\",\"last_key\":\"7tfnslrd7ZOq5ER+sbjqBAEW2QesHEya80iUjD9kifA=\",\"current_key\":\"RoKnkfro+5rvtl8F38p01kk+APwjdaWzmuiKJrGz/vA=\",\"next_key\":\"Hh7QIfDyVTqhpo+hDx+Tjn9bKv8sa5sTzd89bE7cT7k=\",\"key_lifetime\":227,\"next_rotation_on\":\"1987-08-02T03:22:19.292Z\"}"
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
  "name": "khSFHaAPznQoluFbJGuOqjxeAmJcWYxEfkXoBABhvMkiEfims",
  "integrator_type": "cust_internal",
  "description": "PqZXcMfGSzRZLssEMkuIzmm",
  "last_key": "J4KOhm7b9CTthCP2B3seV/1TEuzpFWQCwn533fnhIII=",
  "current_key": "3b7eFLPj9yRc+5oLc4cAswzoiMNDJL8CTcaBleXXUPI=",
  "next_key": "ETPaHR/6WMa8cRK8Eq+mXD9kmvR0+TTGRrbiiH5Myn8=",
  "key_lifetime": 60,
  "next_rotation_on": "2016-06-09T23:50:07.751Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "khSFHaAPznQoluFbJGuOqjxeAmJcWYxEfkXoBABhvMkiEfims" },
	{ "integrator_type", "cust_internal" },
	{ "description", "PqZXcMfGSzRZLssEMkuIzmm" },
	{ "last_key", "J4KOhm7b9CTthCP2B3seV/1TEuzpFWQCwn533fnhIII=" },
	{ "current_key", "3b7eFLPj9yRc+5oLc4cAswzoiMNDJL8CTcaBleXXUPI=" },
	{ "next_key", "ETPaHR/6WMa8cRK8Eq+mXD9kmvR0+TTGRrbiiH5Myn8=" },
	{ "key_lifetime", 60 },
	{ "next_rotation_on", "2016-06-09T23:50:07.751Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"khSFHaAPznQoluFbJGuOqjxeAmJcWYxEfkXoBABhvMkiEfims\",\"integrator_type\":\"cust_internal\",\"description\":\"PqZXcMfGSzRZLssEMkuIzmm\",\"last_key\":\"J4KOhm7b9CTthCP2B3seV/1TEuzpFWQCwn533fnhIII=\",\"current_key\":\"3b7eFLPj9yRc+5oLc4cAswzoiMNDJL8CTcaBleXXUPI=\",\"next_key\":\"ETPaHR/6WMa8cRK8Eq+mXD9kmvR0+TTGRrbiiH5Myn8=\",\"key_lifetime\":60,\"next_rotation_on\":\"2016-06-09T23:50:07.751Z\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/1646209542
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
https://api.INSTANCE.cardsavr.io/integrators/1646209542
```

```javascript
await session.deleteIntegrator(1646209542);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(1646209542);
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
https://api.INSTANCE.cardsavr.io/merchant_sites/563989828
```

```javascript
const merchantsites = await session.getMerchantSites(563989828);
```

```csharp
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(563989828);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 563989828,
  "name": "xjqXYAclPztqtWhCteRdDISAwfiuSB",
  "host": "umwHiGrJ",
  "image_lookup_key": "vZsG",
  "images": [
    {
      "EnaNhpmAVcEj": "RdBC-$R&]6-=tbx3n/!(1",
      "xCWAPFsFmFwQ": 73,
      "NLSkHvVydfLM": false
    },
    {
      "lJCLBqwQuNlU": "/E%f@BKS.@/w@2(F3(>j%(",
      "RGDEkePcPKBU": 64,
      "rxrihOhFtUAT": true
    },
    {
      "AyVLFESpqbVU": "Vq+Y%vs6qRXmSnO",
      "JSucGWNLOnVP": 46,
      "ZzSfAaJIYjqq": false
    }
  ],
  "mfa": true,
  "tags": "geYISeEdyHrZBU",
  "login": {
    "NiFPutfcMRer": "*OYrOi",
    "YsHPUJtLpAgE": 32,
    "aFIHcTqflGVb": true
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
https://api.INSTANCE.cardsavr.io/notifications/1840727998
```

```javascript
const notifications = await session.getNotifications(1840727998);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(1840727998);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1840727998,
  "name": "lryrIEpRwoqLaudBfmARsJYScxupBUuzpHQFplkOodbFlWeWfOWTgmpEUUpoZcI",
  "type": "webhook",
  "config": {
    "GSGItArzrpUN": "uzV&<VEnFd_@2/[",
    "dYoufmZllnPc": 36,
    "cTyUSGcHjKES": false
  },
  "created_on": "1987-01-19T11:46:37.990Z",
  "last_updated_on": "1987-12-22T10:08:40.543Z",
  "financial_institution_id": 530874802
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
  "financial_institution_id": 530874802,
  "name": "lryrIEpRwoqLaudBfmARsJYScxupBUuzpHQFplkOodbFlWeWfOWTgmpEUUpoZcI",
  "type": "webhook",
  "config": {
    "GSGItArzrpUN": "uzV&<VEnFd_@2/[",
    "dYoufmZllnPc": 36,
    "cTyUSGcHjKES": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 530874802 },
	{ "name", "lryrIEpRwoqLaudBfmARsJYScxupBUuzpHQFplkOodbFlWeWfOWTgmpEUUpoZcI" },
	{ "type", "webhook" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":530874802,\"name\":\"lryrIEpRwoqLaudBfmARsJYScxupBUuzpHQFplkOodbFlWeWfOWTgmpEUUpoZcI\",\"type\":\"webhook\",\"config\":{\"GSGItArzrpUN\":\"uzV&<VEnFd_@2/[\",\"dYoufmZllnPc\":36,\"cTyUSGcHjKES\":false}}"
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
  "name": "aoajQXTMGwPsbtsonCWnXmbOnXowXkPRDImeAzuGNYYiSriBwKkQowEijjHszqR",
  "type": "email",
  "config": {
    "lPOnANjXfyyN": "_A3&by1VeaRfZza9dnKg8~J%~$U<6",
    "DqOfvDjPzSFU": 73,
    "ZWwzmILNNmUJ": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "aoajQXTMGwPsbtsonCWnXmbOnXowXkPRDImeAzuGNYYiSriBwKkQowEijjHszqR" },
	{ "type", "email" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```shell
curl -d "{\"name\":\"aoajQXTMGwPsbtsonCWnXmbOnXowXkPRDImeAzuGNYYiSriBwKkQowEijjHszqR\",\"type\":\"email\",\"config\":{\"lPOnANjXfyyN\":\"_A3&by1VeaRfZza9dnKg8~J%~$U<6\",\"DqOfvDjPzSFU\":73,\"ZWwzmILNNmUJ\":false}}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/1840727998
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
https://api.INSTANCE.cardsavr.io/notifications/1840727998
```

```javascript
await session.deleteNotification(1840727998);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(1840727998);
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/195746757
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(195746757);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(195746757);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 195746757,
  "card_placement_result_id": "JOsgQpzxnyhmWaQzy",
  "status": "TOO_MANY_TFA_FAILURES",
  "custom_data": {
    "kYFQVuqBOhRP": "4}!Xjx{d.$A2K$9",
    "dZtmhPKcNJps": 51,
    "evjhVoYDooWJ": false
  },
  "failure_reason": "GXCAR",
  "messaging_addresses": "cd",
  "current_state": "PraXPoVHabnWtXVRZnKuGTaFYbszfXmuCLIGzzQHVstuAGpbmwlbguYElMPwwNG",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 956982786,
  "job_ready_on": "2019-01-04T05:30:40.385Z",
  "started_on": "1989-07-19T19:38:09.305Z",
  "completed_on": "1984-02-04T03:57:32.756Z",
  "expiration_date": "1971-08-14T15:39:55.635Z",
  "created_on": "1973-01-17T22:05:42.761Z",
  "last_updated_on": "2018-05-29T11:11:48.993Z",
  "user_id": 1512325034,
  "card_id": 1679965998,
  "account_id": 2083901572
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
  "place_card_on_multiple_sites_job_id": 673853672,
  "user_id": 1512325034,
  "card_id": 1679965998,
  "account_id": 2083901572,
  "status": "TOO_MANY_TFA_FAILURES",
  "custom_data": {
    "kYFQVuqBOhRP": "4}!Xjx{d.$A2K$9",
    "dZtmhPKcNJps": 51,
    "evjhVoYDooWJ": false
  },
  "failure_reason": "GXCAR",
  "current_state": "PraXPoVHabnWtXVRZnKuGTaFYbszfXmuCLIGzzQHVstuAGpbmwlbguYElMPwwNG",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 956982786,
  "started_on": "1989-07-19T19:38:09.305Z",
  "completed_on": "1984-02-04T03:57:32.756Z",
  "expiration_date": "1971-08-14T15:39:55.635Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "place_card_on_multiple_sites_job_id", 673853672 },
	{ "user_id", 1512325034 },
	{ "card_id", 1679965998 },
	{ "account_id", 2083901572 },
	{ "status", "TOO_MANY_TFA_FAILURES" },
	{ "failure_reason", "GXCAR" },
	{ "current_state", "PraXPoVHabnWtXVRZnKuGTaFYbszfXmuCLIGzzQHVstuAGpbmwlbguYElMPwwNG" },
	{ "do_not_queue", true },
	{ "user_is_present", false },
	{ "time_elapsed", 956982786 },
	{ "started_on", "1989-07-19T19:38:09.305Z" },
	{ "completed_on", "1984-02-04T03:57:32.756Z" },
	{ "expiration_date", "1971-08-14T15:39:55.635Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"place_card_on_multiple_sites_job_id\":673853672,\"user_id\":1512325034,\"card_id\":1679965998,\"account_id\":2083901572,\"status\":\"TOO_MANY_TFA_FAILURES\",\"custom_data\":{\"kYFQVuqBOhRP\":\"4}!Xjx{d.$A2K$9\",\"dZtmhPKcNJps\":51,\"evjhVoYDooWJ\":false},\"failure_reason\":\"GXCAR\",\"current_state\":\"PraXPoVHabnWtXVRZnKuGTaFYbszfXmuCLIGzzQHVstuAGpbmwlbguYElMPwwNG\",\"do_not_queue\":true,\"user_is_present\":false,\"time_elapsed\":956982786,\"started_on\":\"1989-07-19T19:38:09.305Z\",\"completed_on\":\"1984-02-04T03:57:32.756Z\",\"expiration_date\":\"1971-08-14T15:39:55.635Z\"}"
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

<aside class="notice">Create calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe for added security.</aside>

## Update single-site job

```javascript
const singlesitejob = await session.updateSingleSiteJob({
  "status": "KILLED",
  "custom_data": {
    "zAUAoHHFGSni": "9vx_.rh",
    "AoPogapwWLYp": 8,
    "mlrRcnERnRBt": true
  },
  "failure_reason": "NVVCZXcnmwKDh",
  "current_state": "VxSLvdRtdhmcMZYCBEDJXnryUPCWlPqiaBdbUhERknSkoXQfOsXpJHhamPHicGz",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 1826285844,
  "started_on": "1973-03-24T03:37:56.557Z",
  "completed_on": "2003-01-06T17:08:16.379Z",
  "expiration_date": "1972-09-21T02:39:27.985Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "status", "KILLED" },
	{ "failure_reason", "NVVCZXcnmwKDh" },
	{ "current_state", "VxSLvdRtdhmcMZYCBEDJXnryUPCWlPqiaBdbUhERknSkoXQfOsXpJHhamPHicGz" },
	{ "do_not_queue", true },
	{ "user_is_present", false },
	{ "time_elapsed", 1826285844 },
	{ "started_on", "1973-03-24T03:37:56.557Z" },
	{ "completed_on", "2003-01-06T17:08:16.379Z" },
	{ "expiration_date", "1972-09-21T02:39:27.985Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"status\":\"KILLED\",\"custom_data\":{\"zAUAoHHFGSni\":\"9vx_.rh\",\"AoPogapwWLYp\":8,\"mlrRcnERnRBt\":true},\"failure_reason\":\"NVVCZXcnmwKDh\",\"current_state\":\"VxSLvdRtdhmcMZYCBEDJXnryUPCWlPqiaBdbUhERknSkoXQfOsXpJHhamPHicGz\",\"do_not_queue\":true,\"user_is_present\":false,\"time_elapsed\":1826285844,\"started_on\":\"1973-03-24T03:37:56.557Z\",\"completed_on\":\"2003-01-06T17:08:16.379Z\",\"expiration_date\":\"1972-09-21T02:39:27.985Z\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/195746757
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

<aside class="notice">Update calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe for added security. The safe keys are not required if updating other user properties.</aside>

## Delete single-site job

```shell
curl -X DELETE
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/195746757
```

```javascript
await session.deleteSingleSiteJob(195746757);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(195746757);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [single-site job response parameters](#response-place_card_on_single_site_job).

