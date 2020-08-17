
# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/4471103
```

```javascript
const accounts = await session.getAccounts(4471103);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(4471103);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 4471103,
  "last_card_placed_id": 5872757,
  "last_login": "1987-04-21T17:26:24.475Z",
  "last_password_update": "1981-06-21T01:51:17.547Z",
  "last_saved_card": "2011-10-14T10:47:08.047Z",
  "created_on": "1970-12-22T18:26:35.414Z",
  "last_updated_on": "1995-02-25T21:58:21.023Z",
  "cardholder_id": 5575679,
  "merchant_site_id": 4498329
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
  "cardholder_id": 5575679,
  "merchant_site_id": 4498329,
  "last_card_placed_id": 5872757,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 5575679 },
	{ "merchant_site_id", 4498329 },
	{ "last_card_placed_id", 5872757 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":5575679,\"merchant_site_id\":4498329,\"last_card_placed_id\":5872757,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
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
  "last_card_placed_id": 4938176,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 4938176 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"last_card_placed_id\":4938176,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/4471103
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
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/4471103
```

```javascript
await session.deleteAccount(4471103, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(4471103, CARDHOLDER_SAFE_KEY);
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/39923
```

```javascript
const addresses = await session.getAddresses(39923);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(39923);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 39923,
  "address1": "OnPXrOIRZgmpclotxcBuBhEyqZUQZeloQBzhmcKYgYppzzxYWZGZVtabHhpOHKkLIskVtpbEUvROQEYuKhNhKmTcVzPkGiYFfdW",
  "address2": "xSamTncKhYMCuyikYKPAqYOuKNVDMgxPHldXDxWynyGXQztdRMChgmCxpSvHlDcUpvrfvHdxzysRLXSzrdVWxWCBIWPYRnniasc",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "created_on": "2012-04-18T15:36:36.513Z",
  "last_updated_on": "1985-07-25T04:35:16.271Z",
  "user_id": 116349
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
  "user_id": 116349,
  "address1": "OnPXrOIRZgmpclotxcBuBhEyqZUQZeloQBzhmcKYgYppzzxYWZGZVtabHhpOHKkLIskVtpbEUvROQEYuKhNhKmTcVzPkGiYFfdW",
  "address2": "xSamTncKhYMCuyikYKPAqYOuKNVDMgxPHldXDxWynyGXQztdRMChgmCxpSvHlDcUpvrfvHdxzysRLXSzrdVWxWCBIWPYRnniasc",
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
	{ "user_id", 116349 },
	{ "address1", "OnPXrOIRZgmpclotxcBuBhEyqZUQZeloQBzhmcKYgYppzzxYWZGZVtabHhpOHKkLIskVtpbEUvROQEYuKhNhKmTcVzPkGiYFfdW" },
	{ "address2", "xSamTncKhYMCuyikYKPAqYOuKNVDMgxPHldXDxWynyGXQztdRMChgmCxpSvHlDcUpvrfvHdxzysRLXSzrdVWxWCBIWPYRnniasc" },
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
curl -d "{\"user_id\":116349,\"address1\":\"OnPXrOIRZgmpclotxcBuBhEyqZUQZeloQBzhmcKYgYppzzxYWZGZVtabHhpOHKkLIskVtpbEUvROQEYuKhNhKmTcVzPkGiYFfdW\",\"address2\":\"xSamTncKhYMCuyikYKPAqYOuKNVDMgxPHldXDxWynyGXQztdRMChgmCxpSvHlDcUpvrfvHdxzysRLXSzrdVWxWCBIWPYRnniasc\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true}"
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
  "address1": "pjzITItszZuUfNhmggIDaFewKlJiXYJIOJAoZqOSAmRjLdRZuMpbqNKkUyujqtlEqKkaRHigmlaLHDHnmPVbMtoFKmVEuFRgPUB",
  "address2": "qSXTiSPjECrNPZXjNPqKdjFCxzqECjZSkMzVwNmDgKtAYGjJapcaCCKvNOMzttDuYJRTCXjnjCfRGrHmhSRBJmolgGbpafKgEZr",
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
	{ "address1", "pjzITItszZuUfNhmggIDaFewKlJiXYJIOJAoZqOSAmRjLdRZuMpbqNKkUyujqtlEqKkaRHigmlaLHDHnmPVbMtoFKmVEuFRgPUB" },
	{ "address2", "qSXTiSPjECrNPZXjNPqKdjFCxzqECjZSkMzVwNmDgKtAYGjJapcaCCKvNOMzttDuYJRTCXjnjCfRGrHmhSRBJmolgGbpafKgEZr" },
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
curl -d "{\"address1\":\"pjzITItszZuUfNhmggIDaFewKlJiXYJIOJAoZqOSAmRjLdRZuMpbqNKkUyujqtlEqKkaRHigmlaLHDHnmPVbMtoFKmVEuFRgPUB\",\"address2\":\"qSXTiSPjECrNPZXjNPqKdjFCxzqECjZSkMzVwNmDgKtAYGjJapcaCCKvNOMzttDuYJRTCXjnjCfRGrHmhSRBJmolgGbpafKgEZr\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/39923
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/39923
```

```javascript
await session.deleteAddress(39923);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(39923);
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/401848
```

```javascript
const bins = await session.getBins(401848);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(401848);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 401848,
  "financial_institution_id": 9231722,
  "created_on": "1975-07-02T01:13:13.472Z",
  "last_updated_on": "2016-06-29T18:40:12.753Z",
  "bank_identification_number": "56059051"
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
  "financial_institution_id": 9231722,
  "bank_identification_number": "56059051",
  "brand": "LyHhsASmmKaWBHNVRRM",
  "issuer": "DLRAOuKmgumpocIQMuUTNDkbhQLLLOTWiWDssQhMpscfQciJuCEfSwNPFTdEjBDuyRJiSnUnLgFOlhwxNkGAsazLxQDWcDgcUdQ",
  "type": "RqNpUnxnJeSKTd",
  "level": "AdJLlGAgWngCousFZrPnAUBctqHjgaxGBECvbxLnWMpPnRrEIuvBbFYfgmsnoiZcokEYtBVadajKzkAKKPdTgCtmHvMVEJqUpgk"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 9231722 },
	{ "bank_identification_number", "56059051" },
	{ "brand", "LyHhsASmmKaWBHNVRRM" },
	{ "issuer", "DLRAOuKmgumpocIQMuUTNDkbhQLLLOTWiWDssQhMpscfQciJuCEfSwNPFTdEjBDuyRJiSnUnLgFOlhwxNkGAsazLxQDWcDgcUdQ" },
	{ "type", "RqNpUnxnJeSKTd" },
	{ "level", "AdJLlGAgWngCousFZrPnAUBctqHjgaxGBECvbxLnWMpPnRrEIuvBbFYfgmsnoiZcokEYtBVadajKzkAKKPdTgCtmHvMVEJqUpgk" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":9231722,\"bank_identification_number\":\"56059051\",\"brand\":\"LyHhsASmmKaWBHNVRRM\",\"issuer\":\"DLRAOuKmgumpocIQMuUTNDkbhQLLLOTWiWDssQhMpscfQciJuCEfSwNPFTdEjBDuyRJiSnUnLgFOlhwxNkGAsazLxQDWcDgcUdQ\",\"type\":\"RqNpUnxnJeSKTd\",\"level\":\"AdJLlGAgWngCousFZrPnAUBctqHjgaxGBECvbxLnWMpPnRrEIuvBbFYfgmsnoiZcokEYtBVadajKzkAKKPdTgCtmHvMVEJqUpgk\"}"
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
  "financial_institution_id": 4488243,
  "brand": "DyNNioVwAcwiaQSPTSI",
  "issuer": "FOAAnrIbtpNEHgCqGrXQpZssTERDxkSfOLilymOwOlMQUdszeunMsuVUSvsHTTGSIKHpXcsOMVuObvsgsNgUwXITLlKNoSIuphV",
  "type": "rKRPGhdZxnggWm",
  "level": "bVFWLLWOffkHAOZFbUBudZYOpsxFLRIZCQhouUUfSzIWKSDxjLgIPVyRnouIpUTgxCMbuivDOODIZSymKxTzlTpZVtiWgBHuOOY"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 4488243 },
	{ "brand", "DyNNioVwAcwiaQSPTSI" },
	{ "issuer", "FOAAnrIbtpNEHgCqGrXQpZssTERDxkSfOLilymOwOlMQUdszeunMsuVUSvsHTTGSIKHpXcsOMVuObvsgsNgUwXITLlKNoSIuphV" },
	{ "type", "rKRPGhdZxnggWm" },
	{ "level", "bVFWLLWOffkHAOZFbUBudZYOpsxFLRIZCQhouUUfSzIWKSDxjLgIPVyRnouIpUTgxCMbuivDOODIZSymKxTzlTpZVtiWgBHuOOY" }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":4488243,\"brand\":\"DyNNioVwAcwiaQSPTSI\",\"issuer\":\"FOAAnrIbtpNEHgCqGrXQpZssTERDxkSfOLilymOwOlMQUdszeunMsuVUSvsHTTGSIKHpXcsOMVuObvsgsNgUwXITLlKNoSIuphV\",\"type\":\"rKRPGhdZxnggWm\",\"level\":\"bVFWLLWOffkHAOZFbUBudZYOpsxFLRIZCQhouUUfSzIWKSDxjLgIPVyRnouIpUTgxCMbuivDOODIZSymKxTzlTpZVtiWgBHuOOY\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/401848
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/401848
```

```javascript
await session.deleteBin(401848);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(401848);
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/5082031
```

```javascript
const cards = await session.getCards(5082031);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(5082031);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 5082031,
  "address_id": 1193731,
  "bin_id": 3454287,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "created_on": "1980-07-08T10:07:31.206Z",
  "last_updated_on": "1971-02-10T04:42:36.698Z",
  "expiration_month": 12,
  "expiration_year": 24,
  "cardholder_id": 6780914,
  "par": "qGRPVyWZRsDTWKITyNCQIzETYZuow"
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
  "cardholder_id": 6780914,
  "address_id": 1193731,
  "bin_id": 3454287,
  "par": "qGRPVyWZRsDTWKITyNCQIzETYZuow",
  "pan": "MirorUPQlRmLtrI",
  "cvv": "tDn",
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
	{ "cardholder_id", 6780914 },
	{ "address_id", 1193731 },
	{ "bin_id", 3454287 },
	{ "par", "qGRPVyWZRsDTWKITyNCQIzETYZuow" },
	{ "pan", "MirorUPQlRmLtrI" },
	{ "cvv", "tDn" },
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
curl -d "{\"cardholder_id\":6780914,\"address_id\":1193731,\"bin_id\":3454287,\"par\":\"qGRPVyWZRsDTWKITyNCQIzETYZuow\",\"pan\":\"MirorUPQlRmLtrI\",\"cvv\":\"tDn\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
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
  "address_id": 9211061,
  "bin_id": 1355352,
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
	{ "address_id", 9211061 },
	{ "bin_id", 1355352 },
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
curl -d "{\"address_id\":9211061,\"bin_id\":1355352,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"expiration_month\":12,\"expiration_year\":24,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/5082031
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/5082031
```

```javascript
await session.deleteCard(5082031, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(5082031, CARDHOLDER_SAFE_KEY);
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/5494733
```

```javascript
const users = await session.getUsers(5494733);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(5494733);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 5494733,
  "financial_institution_id": 9241484,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1973-05-05T12:07:49.669Z",
  "is_locked": false,
  "password_lifetime": 156,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "customer_agent",
  "phone_number": "UAqKzKjxnjuQXv",
  "custom_data": {
    "ffbMLwSgXjSB": "f9lbb!",
    "nwgVuYgzhpFM": 23,
    "IlWlHnEavRlK": false
  },
  "next_rotation_on": "1979-08-09T17:11:46.470Z",
  "created_on": "1984-11-05T20:46:06.288Z",
  "last_updated_on": "2014-08-30T17:36:41.001Z",
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
  "financial_institution_id": 9241484,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "next_password": "8/MXIg7CkNcBAovtf5ulw9M3BjlfWhTml+nqJIocds8=",
  "cardholder_safe_key": "IHvc+aFR4CKMb4J/uV518CmVmAAMcnhwBtyGtv9p3mk=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 156,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "customer_agent",
  "phone_number": "UAqKzKjxnjuQXv",
  "custom_data": {
    "ffbMLwSgXjSB": "f9lbb!",
    "nwgVuYgzhpFM": 23,
    "IlWlHnEavRlK": false
  },
  "next_rotation_on": "1979-08-09T17:11:46.470Z"
}, NEW_CARDHODLER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 9241484 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "next_password", "8/MXIg7CkNcBAovtf5ulw9M3BjlfWhTml+nqJIocds8=" },
	{ "cardholder_safe_key", "IHvc+aFR4CKMb4J/uV518CmVmAAMcnhwBtyGtv9p3mk=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 156 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "customer_agent" },
	{ "phone_number", "UAqKzKjxnjuQXv" },
	{ "next_rotation_on", "1979-08-09T17:11:46.470Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, NEW_CARDHODLER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":9241484,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"next_password\":\"8/MXIg7CkNcBAovtf5ulw9M3BjlfWhTml+nqJIocds8=\",\"cardholder_safe_key\":\"IHvc+aFR4CKMb4J/uV518CmVmAAMcnhwBtyGtv9p3mk=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":156,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"customer_agent\",\"phone_number\":\"UAqKzKjxnjuQXv\",\"custom_data\":{\"ffbMLwSgXjSB\":\"f9lbb!\",\"nwgVuYgzhpFM\":23,\"IlWlHnEavRlK\":false},\"next_rotation_on\":\"1979-08-09T17:11:46.470Z\"}"
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
  "financial_institution_id": 3331786,
  "next_password": "XDXWwxguyYeqkull3EC5aUBxE0YyT8HoU12nUulkJkk=",
  "cardholder_safe_key": "3cI+cKMNz1gMJz2HtFI+qbr6Oxit9I7qPv/rlWsf684=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 20,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "customer_auditor",
  "phone_number": "ZVgXNNveNlENvn",
  "custom_data": {
    "gtEiMOXYzPqv": "o$Rh[91!eD]Wkc!ZwmC<A92",
    "SoWoWVrHIqUW": 26,
    "tKmCwKSdTxXD": false
  },
  "next_rotation_on": "1974-08-22T11:13:33.257Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 3331786 },
	{ "next_password", "XDXWwxguyYeqkull3EC5aUBxE0YyT8HoU12nUulkJkk=" },
	{ "cardholder_safe_key", "3cI+cKMNz1gMJz2HtFI+qbr6Oxit9I7qPv/rlWsf684=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 20 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "customer_auditor" },
	{ "phone_number", "ZVgXNNveNlENvn" },
	{ "next_rotation_on", "1974-08-22T11:13:33.257Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":3331786,\"next_password\":\"XDXWwxguyYeqkull3EC5aUBxE0YyT8HoU12nUulkJkk=\",\"cardholder_safe_key\":\"3cI+cKMNz1gMJz2HtFI+qbr6Oxit9I7qPv/rlWsf684=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":20,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"customer_auditor\",\"phone_number\":\"ZVgXNNveNlENvn\",\"custom_data\":{\"gtEiMOXYzPqv\":\"o$Rh[91!eD]Wkc!ZwmC<A92\",\"SoWoWVrHIqUW\":26,\"tKmCwKSdTxXD\":false},\"next_rotation_on\":\"1974-08-22T11:13:33.257Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/5494733
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/5494733
```

```javascript
await session.deleteUser(5494733);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(5494733);
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
https://api.INSTANCE.cardsavr.io/financial_institutions/2682876
```

```javascript
const financialinstitutions = await session.getFinancialInstitutions(2682876);
```

```csharp
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(2682876);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2682876,
  "name": "xmmlksbPJNezQCWwgNwoCRWcvHkDDXjOQKmbmDZuNyHMwCRQSeqTiZznCljEZVx",
  "description": "UtuZAVYkzbsYfa",
  "lookup_key": "YKfjBHrrQoVSgYqMKmLrlnavHnVkVbjPLxtNZPtbRqQEzODnekrrXgtrkkJCRqp",
  "alternate_lookup_key": "aRHvwlNBSBPOMVqVxZYuLSWmMBXCCTKHADrMLtksjgAAxGyjmZDFgKJPehLhUEB",
  "created_on": "1985-03-30T05:49:04.112Z",
  "last_updated_on": "1998-10-29T17:28:42.862Z"
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
  "name": "xmmlksbPJNezQCWwgNwoCRWcvHkDDXjOQKmbmDZuNyHMwCRQSeqTiZznCljEZVx",
  "description": "UtuZAVYkzbsYfa",
  "lookup_key": "YKfjBHrrQoVSgYqMKmLrlnavHnVkVbjPLxtNZPtbRqQEzODnekrrXgtrkkJCRqp",
  "alternate_lookup_key": "aRHvwlNBSBPOMVqVxZYuLSWmMBXCCTKHADrMLtksjgAAxGyjmZDFgKJPehLhUEB"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "xmmlksbPJNezQCWwgNwoCRWcvHkDDXjOQKmbmDZuNyHMwCRQSeqTiZznCljEZVx" },
	{ "description", "UtuZAVYkzbsYfa" },
	{ "lookup_key", "YKfjBHrrQoVSgYqMKmLrlnavHnVkVbjPLxtNZPtbRqQEzODnekrrXgtrkkJCRqp" },
	{ "alternate_lookup_key", "aRHvwlNBSBPOMVqVxZYuLSWmMBXCCTKHADrMLtksjgAAxGyjmZDFgKJPehLhUEB" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"xmmlksbPJNezQCWwgNwoCRWcvHkDDXjOQKmbmDZuNyHMwCRQSeqTiZznCljEZVx\",\"description\":\"UtuZAVYkzbsYfa\",\"lookup_key\":\"YKfjBHrrQoVSgYqMKmLrlnavHnVkVbjPLxtNZPtbRqQEzODnekrrXgtrkkJCRqp\",\"alternate_lookup_key\":\"aRHvwlNBSBPOMVqVxZYuLSWmMBXCCTKHADrMLtksjgAAxGyjmZDFgKJPehLhUEB\"}"
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
  "name": "JXPalLDpjwKoUnqfdukIxvIPSvdZNziCCKtwZsCJlFBDBDNEnoMlctDGXgEbRBN",
  "description": "hIPxPYjVvPNNpXPDFktIJ",
  "lookup_key": "zJGCAkFjOlDhAPmhFpcTypWvtXuAKSmJjrTtULFkwQpSXHPMhSbtECOTAaDilPr",
  "alternate_lookup_key": "mukUfvyOMGxtuVbaoPZHWKUMTvdRLPzhBUtakZRBjLTwUrTPnffJNXVLDJZhElV"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "JXPalLDpjwKoUnqfdukIxvIPSvdZNziCCKtwZsCJlFBDBDNEnoMlctDGXgEbRBN" },
	{ "description", "hIPxPYjVvPNNpXPDFktIJ" },
	{ "lookup_key", "zJGCAkFjOlDhAPmhFpcTypWvtXuAKSmJjrTtULFkwQpSXHPMhSbtECOTAaDilPr" },
	{ "alternate_lookup_key", "mukUfvyOMGxtuVbaoPZHWKUMTvdRLPzhBUtakZRBjLTwUrTPnffJNXVLDJZhElV" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"JXPalLDpjwKoUnqfdukIxvIPSvdZNziCCKtwZsCJlFBDBDNEnoMlctDGXgEbRBN\",\"description\":\"hIPxPYjVvPNNpXPDFktIJ\",\"lookup_key\":\"zJGCAkFjOlDhAPmhFpcTypWvtXuAKSmJjrTtULFkwQpSXHPMhSbtECOTAaDilPr\",\"alternate_lookup_key\":\"mukUfvyOMGxtuVbaoPZHWKUMTvdRLPzhBUtakZRBjLTwUrTPnffJNXVLDJZhElV\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/2682876
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
https://api.INSTANCE.cardsavr.io/financial_institutions/2682876
```

```javascript
await session.deleteFinancialInstitution(2682876);
```

```csharp
CardSavrResponse<FinancialInstitution> financialinstitution = await http.DeleteFinancialInstitutionAsync(2682876);
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
https://api.INSTANCE.cardsavr.io/integrators/4970980
```

```javascript
const integrators = await session.getIntegrators(4970980);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(4970980);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 4970980,
  "name": "ZZCUArvgYmElkyjUJjTKygsKRYaeXflfZMbRffBSgSzDQULEa",
  "integrator_type": "swch_internal",
  "description": "hgHqDWfNFnQgczOWYxzkcIEdn",
  "last_key": "Fk6xqqxLSDi8w0NSL2uxWKm943EpRt8p6xXm5prud+8=",
  "current_key": "gk/3kMmUbFeNFmYETInVupUDtiXs7Js8kz8KsLJNZ0Q=",
  "next_key": "eBK903rhJHL/p8iH9++4gRwGItp1gViaabyjj4dRYqM=",
  "key_lifetime": 82,
  "next_rotation_on": "1991-12-20T14:26:10.317Z",
  "created_on": "2003-05-11T14:20:48.329Z",
  "last_updated_on": "2004-05-27T05:51:21.466Z"
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
  "name": "ZZCUArvgYmElkyjUJjTKygsKRYaeXflfZMbRffBSgSzDQULEa",
  "integrator_type": "swch_internal",
  "description": "hgHqDWfNFnQgczOWYxzkcIEdn",
  "last_key": "Fk6xqqxLSDi8w0NSL2uxWKm943EpRt8p6xXm5prud+8=",
  "current_key": "gk/3kMmUbFeNFmYETInVupUDtiXs7Js8kz8KsLJNZ0Q=",
  "next_key": "eBK903rhJHL/p8iH9++4gRwGItp1gViaabyjj4dRYqM=",
  "key_lifetime": 82,
  "next_rotation_on": "1991-12-20T14:26:10.317Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "ZZCUArvgYmElkyjUJjTKygsKRYaeXflfZMbRffBSgSzDQULEa" },
	{ "integrator_type", "swch_internal" },
	{ "description", "hgHqDWfNFnQgczOWYxzkcIEdn" },
	{ "last_key", "Fk6xqqxLSDi8w0NSL2uxWKm943EpRt8p6xXm5prud+8=" },
	{ "current_key", "gk/3kMmUbFeNFmYETInVupUDtiXs7Js8kz8KsLJNZ0Q=" },
	{ "next_key", "eBK903rhJHL/p8iH9++4gRwGItp1gViaabyjj4dRYqM=" },
	{ "key_lifetime", 82 },
	{ "next_rotation_on", "1991-12-20T14:26:10.317Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"ZZCUArvgYmElkyjUJjTKygsKRYaeXflfZMbRffBSgSzDQULEa\",\"integrator_type\":\"swch_internal\",\"description\":\"hgHqDWfNFnQgczOWYxzkcIEdn\",\"last_key\":\"Fk6xqqxLSDi8w0NSL2uxWKm943EpRt8p6xXm5prud+8=\",\"current_key\":\"gk/3kMmUbFeNFmYETInVupUDtiXs7Js8kz8KsLJNZ0Q=\",\"next_key\":\"eBK903rhJHL/p8iH9++4gRwGItp1gViaabyjj4dRYqM=\",\"key_lifetime\":82,\"next_rotation_on\":\"1991-12-20T14:26:10.317Z\"}"
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
  "name": "QcacWGyBfPPcTRMRtOHxKJCEFUybisieDmtYJzzSQazBBxKvo",
  "integrator_type": "application",
  "description": "AVkuLAOkKjrFzKG",
  "last_key": "RbHu/THr/HR8OKThExMGwAlCzNsgmG5ChBrTwnF+zHI=",
  "current_key": "ueRs2U4snWwDd9uYDyrV6fTCyRmI83jVrSCeyru/or0=",
  "next_key": "Mmc5vi/Zlme6vNwHmq8wy6ASrI/WNCm+2HqPAuem3dc=",
  "key_lifetime": 363,
  "next_rotation_on": "2009-08-02T12:25:48.433Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "QcacWGyBfPPcTRMRtOHxKJCEFUybisieDmtYJzzSQazBBxKvo" },
	{ "integrator_type", "application" },
	{ "description", "AVkuLAOkKjrFzKG" },
	{ "last_key", "RbHu/THr/HR8OKThExMGwAlCzNsgmG5ChBrTwnF+zHI=" },
	{ "current_key", "ueRs2U4snWwDd9uYDyrV6fTCyRmI83jVrSCeyru/or0=" },
	{ "next_key", "Mmc5vi/Zlme6vNwHmq8wy6ASrI/WNCm+2HqPAuem3dc=" },
	{ "key_lifetime", 363 },
	{ "next_rotation_on", "2009-08-02T12:25:48.433Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"QcacWGyBfPPcTRMRtOHxKJCEFUybisieDmtYJzzSQazBBxKvo\",\"integrator_type\":\"application\",\"description\":\"AVkuLAOkKjrFzKG\",\"last_key\":\"RbHu/THr/HR8OKThExMGwAlCzNsgmG5ChBrTwnF+zHI=\",\"current_key\":\"ueRs2U4snWwDd9uYDyrV6fTCyRmI83jVrSCeyru/or0=\",\"next_key\":\"Mmc5vi/Zlme6vNwHmq8wy6ASrI/WNCm+2HqPAuem3dc=\",\"key_lifetime\":363,\"next_rotation_on\":\"2009-08-02T12:25:48.433Z\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/4970980
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
https://api.INSTANCE.cardsavr.io/integrators/4970980
```

```javascript
await session.deleteIntegrator(4970980);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(4970980);
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
https://api.INSTANCE.cardsavr.io/merchant_sites/1307191
```

```javascript
const merchantsites = await session.getMerchantSites(1307191);
```

```csharp
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(1307191);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1307191,
  "name": "lMUNNexE",
  "host": "LEa",
  "image_lookup_key": "gUyRERbdLqDiOEexQTFNhFNkCvGHQKaI",
  "images": [
    {
      "oskzDlLAPnQJ": "!Z&Z$7}Q%qUf[$rd*<bRgmn$pH(^~",
      "ylLzjYciEOfe": 59,
      "pnLMrbyMnSSw": true
    },
    {
      "oPSLKxhwVJPN": "#KQgFeR)P0bGIX#0",
      "ecoFIRLYXGeP": 30,
      "jSvZxlgrKNkl": false
    },
    {
      "TElKPDbTEjhR": "vBH_J[+_zh~$rJMRomC5",
      "GdvnKvozLzhm": 55,
      "iQIDhVRFBgCU": true
    }
  ],
  "mfa": false,
  "tags": "HNmcbqGucBjoKiRL",
  "login": {
    "jEzKLRzoiuZb": "XKZtR2I5$m-bfLITwXjqMKWHh^",
    "CPqKsnTCEVjQ": 90,
    "dYVPxRUPuXxG": true
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
https://api.INSTANCE.cardsavr.io/notifications/1551544
```

```javascript
const notifications = await session.getNotifications(1551544);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(1551544);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1551544,
  "name": "fwLJETjvCVevHwiPjVBCtrAYJeLryUngJHYcrKCAcFSVLErAAyEUngRRjKBoKUa",
  "type": "email",
  "config": {
    "xIWnBRcHeoOn": "XFeI2K,_2TGS69U+]7/h0lc~cH_gjT",
    "rhLCwKAgjyUG": 4,
    "OxnkOmDBvadG": true
  },
  "created_on": "1985-02-08T07:59:50.540Z",
  "last_updated_on": "1998-10-31T18:09:21.555Z",
  "financial_institution_id": 810838
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
  "financial_institution_id": 810838,
  "name": "fwLJETjvCVevHwiPjVBCtrAYJeLryUngJHYcrKCAcFSVLErAAyEUngRRjKBoKUa",
  "type": "email",
  "config": {
    "xIWnBRcHeoOn": "XFeI2K,_2TGS69U+]7/h0lc~cH_gjT",
    "rhLCwKAgjyUG": 4,
    "OxnkOmDBvadG": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 810838 },
	{ "name", "fwLJETjvCVevHwiPjVBCtrAYJeLryUngJHYcrKCAcFSVLErAAyEUngRRjKBoKUa" },
	{ "type", "email" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":810838,\"name\":\"fwLJETjvCVevHwiPjVBCtrAYJeLryUngJHYcrKCAcFSVLErAAyEUngRRjKBoKUa\",\"type\":\"email\",\"config\":{\"xIWnBRcHeoOn\":\"XFeI2K,_2TGS69U+]7/h0lc~cH_gjT\",\"rhLCwKAgjyUG\":4,\"OxnkOmDBvadG\":true}}"
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
  "name": "MyoZFHSyPgWoerLzqENaBlazvxpmJyeOIvutCTzYcidmlFrzIJGdeOMnOXagnem",
  "type": "email",
  "config": {
    "xEpEBHAEZoRV": "U-xmQC<,%dpmeD,aq%lB.ZFeIU-K=S",
    "fchRNZFwzABT": 64,
    "oXeHgEuLnRVg": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "MyoZFHSyPgWoerLzqENaBlazvxpmJyeOIvutCTzYcidmlFrzIJGdeOMnOXagnem" },
	{ "type", "email" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```shell
curl -d "{\"name\":\"MyoZFHSyPgWoerLzqENaBlazvxpmJyeOIvutCTzYcidmlFrzIJGdeOMnOXagnem\",\"type\":\"email\",\"config\":{\"xEpEBHAEZoRV\":\"U-xmQC<,%dpmeD,aq%lB.ZFeIU-K=S\",\"fchRNZFwzABT\":64,\"oXeHgEuLnRVg\":true}}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/1551544
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
https://api.INSTANCE.cardsavr.io/notifications/1551544
```

```javascript
await session.deleteNotification(1551544);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(1551544);
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/6924313
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(6924313);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(6924313);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 6924313,
  "card_placement_result_id": "CNPXeQxxMgXJHYWA",
  "status": "PROXY_PROBE_FAILED",
  "custom_data": {
    "KnoBHqhwBEhK": "8",
    "WQPgaVeAdnNM": 97,
    "ZpleBAeEKvkL": false
  },
  "failure_reason": "IqMHTNYgRUEVOtmXK",
  "messaging_addresses": "ttA",
  "current_state": "NWwlCwPlvdUhCMvcHvUUEhFmpxnnXZyTWpNgDwdDoHKTKxRZHgEuKozCaIgBJGM",
  "do_not_queue": false,
  "user_is_present": true,
  "time_elapsed": 1240143,
  "job_ready_on": "1975-04-03T12:52:55.062Z",
  "started_on": "2007-04-03T16:51:40.067Z",
  "completed_on": "2004-04-17T02:54:29.448Z",
  "expiration_date": "1972-04-13T07:22:30.591Z",
  "created_on": "1970-07-01T01:30:12.059Z",
  "last_updated_on": "2020-07-14T18:26:51.300Z",
  "user_id": 7141806,
  "card_id": 7465902,
  "account_id": 2624357
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
  "place_card_on_multiple_sites_job_id": 3676391,
  "user_id": 7141806,
  "card_id": 7465902,
  "account_id": 2624357,
  "status": "PROXY_PROBE_FAILED",
  "custom_data": {
    "KnoBHqhwBEhK": "8",
    "WQPgaVeAdnNM": 97,
    "ZpleBAeEKvkL": false
  },
  "failure_reason": "IqMHTNYgRUEVOtmXK",
  "current_state": "NWwlCwPlvdUhCMvcHvUUEhFmpxnnXZyTWpNgDwdDoHKTKxRZHgEuKozCaIgBJGM",
  "do_not_queue": false,
  "user_is_present": true,
  "time_elapsed": 1240143,
  "started_on": "2007-04-03T16:51:40.067Z",
  "completed_on": "2004-04-17T02:54:29.448Z",
  "expiration_date": "1972-04-13T07:22:30.591Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "place_card_on_multiple_sites_job_id", 3676391 },
	{ "user_id", 7141806 },
	{ "card_id", 7465902 },
	{ "account_id", 2624357 },
	{ "status", "PROXY_PROBE_FAILED" },
	{ "failure_reason", "IqMHTNYgRUEVOtmXK" },
	{ "current_state", "NWwlCwPlvdUhCMvcHvUUEhFmpxnnXZyTWpNgDwdDoHKTKxRZHgEuKozCaIgBJGM" },
	{ "do_not_queue", false },
	{ "user_is_present", true },
	{ "time_elapsed", 1240143 },
	{ "started_on", "2007-04-03T16:51:40.067Z" },
	{ "completed_on", "2004-04-17T02:54:29.448Z" },
	{ "expiration_date", "1972-04-13T07:22:30.591Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"place_card_on_multiple_sites_job_id\":3676391,\"user_id\":7141806,\"card_id\":7465902,\"account_id\":2624357,\"status\":\"PROXY_PROBE_FAILED\",\"custom_data\":{\"KnoBHqhwBEhK\":\"8\",\"WQPgaVeAdnNM\":97,\"ZpleBAeEKvkL\":false},\"failure_reason\":\"IqMHTNYgRUEVOtmXK\",\"current_state\":\"NWwlCwPlvdUhCMvcHvUUEhFmpxnnXZyTWpNgDwdDoHKTKxRZHgEuKozCaIgBJGM\",\"do_not_queue\":false,\"user_is_present\":true,\"time_elapsed\":1240143,\"started_on\":\"2007-04-03T16:51:40.067Z\",\"completed_on\":\"2004-04-17T02:54:29.448Z\",\"expiration_date\":\"1972-04-13T07:22:30.591Z\"}"
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
  "status": "CANCEL_REQUESTED",
  "custom_data": {
    "plCXYwrlLwxv": "L~WSLDp",
    "SiZBtUzzgmAu": 92,
    "cOZdCFHMrfXd": true
  },
  "failure_reason": "mVtZ",
  "current_state": "lJXjrVBNRWwjbKghMFNdenFGnfxZIYyidhgkvRfSJOsoZygYsafBEVkaStGXgiF",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 8133781,
  "started_on": "1982-06-07T18:48:29.725Z",
  "completed_on": "1980-07-01T08:34:37.308Z",
  "expiration_date": "1988-07-23T12:33:22.963Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "status", "CANCEL_REQUESTED" },
	{ "failure_reason", "mVtZ" },
	{ "current_state", "lJXjrVBNRWwjbKghMFNdenFGnfxZIYyidhgkvRfSJOsoZygYsafBEVkaStGXgiF" },
	{ "do_not_queue", true },
	{ "user_is_present", false },
	{ "time_elapsed", 8133781 },
	{ "started_on", "1982-06-07T18:48:29.725Z" },
	{ "completed_on", "1980-07-01T08:34:37.308Z" },
	{ "expiration_date", "1988-07-23T12:33:22.963Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"status\":\"CANCEL_REQUESTED\",\"custom_data\":{\"plCXYwrlLwxv\":\"L~WSLDp\",\"SiZBtUzzgmAu\":92,\"cOZdCFHMrfXd\":true},\"failure_reason\":\"mVtZ\",\"current_state\":\"lJXjrVBNRWwjbKghMFNdenFGnfxZIYyidhgkvRfSJOsoZygYsafBEVkaStGXgiF\",\"do_not_queue\":true,\"user_is_present\":false,\"time_elapsed\":8133781,\"started_on\":\"1982-06-07T18:48:29.725Z\",\"completed_on\":\"1980-07-01T08:34:37.308Z\",\"expiration_date\":\"1988-07-23T12:33:22.963Z\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/6924313
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/6924313
```

```javascript
await session.deleteSingleSiteJob(6924313);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(6924313);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [single-site job response parameters](#response-place_card_on_single_site_job).

