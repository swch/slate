# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

```shell
curl -H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/4240249
```

```javascript
const account = await session.getAccount(4240249, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Account> account = await session.GetAccountAsync(4240249, CARDHOLDER_SAFE_KEY);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 4240249,
  "last_card_placed_id": 1475897,
  "username": "jsmith123",
  "password": "Pa$$w0rd",
  "last_login": "2010-10-11T23:11:14.807Z",
  "last_password_update": "2018-04-22T22:01:09.972Z",
  "last_saved_card": "2000-02-15T10:10:54.916Z",
  "created_on": "1989-12-05T17:34:28.217Z",
  "last_updated_on": "1995-05-24T11:36:45.864Z",
  "cardholder_id": 7318333,
  "merchant_site_id": 5497727
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
  "cardholder_id": 7318333,
  "merchant_site_id": 5497727,
  "last_card_placed_id": 1475897,
  "username": "jsmith123",
  "password": "Pa$$w0rd"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 7318333 },
	{ "merchant_site_id", 5497727 },
	{ "last_card_placed_id", 1475897 },
	{ "username", "jsmith123" },
	{ "password", "Pa$$w0rd" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":7318333,\"merchant_site_id\":5497727,\"last_card_placed_id\":1475897,\"username\":\"jsmith123\",\"password\":\"Pa$$w0rd\"}"
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
  "last_card_placed_id": 2823891,
  "username": "jsmith123",
  "password": "Pa$$w0rd"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 2823891 },
	{ "username", "jsmith123" },
	{ "password", "Pa$$w0rd" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"last_card_placed_id\":2823891,\"username\":\"jsmith123\",\"password\":\"Pa$$w0rd\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/4240249
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
curl -X DELETE -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/4240249
```

```javascript
await session.deleteAccount(4240249, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(4240249, CARDHOLDER_SAFE_KEY);
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/9082643
```

```javascript
const address = await session.getAddress(9082643);
```

```csharp
CardSavrResponse<Address> address = await session.GetAddressAsync(9082643);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 9082643,
  "address1": "OWPpqnJJJcBxgxUprFHLaotrvQGwCjGGlDjdVzldbTmRNhIldifhLBaQReeKimhOjpQsXHegwsoXaxTToGQzOsizbyYOjAcsiQz",
  "address2": "ampvphADrdiauCDTdSQjMovDtHdZNFEtBOYuiKwOsBIWurXKTxBhwAnvwZVApNdeYXhqGrNGaIyBMYPllxkjdLOAPpJuPZDoFfn",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "created_on": "1978-06-12T20:09:46.344Z",
  "last_updated_on": "1995-11-05T00:37:22.352Z",
  "user_id": 4214315
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
  "user_id": 4214315,
  "address1": "OWPpqnJJJcBxgxUprFHLaotrvQGwCjGGlDjdVzldbTmRNhIldifhLBaQReeKimhOjpQsXHegwsoXaxTToGQzOsizbyYOjAcsiQz",
  "address2": "ampvphADrdiauCDTdSQjMovDtHdZNFEtBOYuiKwOsBIWurXKTxBhwAnvwZVApNdeYXhqGrNGaIyBMYPllxkjdLOAPpJuPZDoFfn",
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
	{ "user_id", 4214315 },
	{ "address1", "OWPpqnJJJcBxgxUprFHLaotrvQGwCjGGlDjdVzldbTmRNhIldifhLBaQReeKimhOjpQsXHegwsoXaxTToGQzOsizbyYOjAcsiQz" },
	{ "address2", "ampvphADrdiauCDTdSQjMovDtHdZNFEtBOYuiKwOsBIWurXKTxBhwAnvwZVApNdeYXhqGrNGaIyBMYPllxkjdLOAPpJuPZDoFfn" },
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
curl -d "{\"user_id\":4214315,\"address1\":\"OWPpqnJJJcBxgxUprFHLaotrvQGwCjGGlDjdVzldbTmRNhIldifhLBaQReeKimhOjpQsXHegwsoXaxTToGQzOsizbyYOjAcsiQz\",\"address2\":\"ampvphADrdiauCDTdSQjMovDtHdZNFEtBOYuiKwOsBIWurXKTxBhwAnvwZVApNdeYXhqGrNGaIyBMYPllxkjdLOAPpJuPZDoFfn\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true}"
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
  "address1": "RAOAgsFiOtlIsAwHhGFKzBvrEsXIOdIizluiVJOvVBoVGeuwyTUSmEXEoZWglxFoiekMlWiEpauyrFkWMvbwTNmOElmOGRAArfJ",
  "address2": "ohpwhrxUaNybpwPeDGJQRTUArBTHjDnQGatSsRTDsGEnJUORgQmzFDuTGlyJANNiVKveYFCSQXsydGeekXfuFFzNfjICzDpExOH",
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
	{ "address1", "RAOAgsFiOtlIsAwHhGFKzBvrEsXIOdIizluiVJOvVBoVGeuwyTUSmEXEoZWglxFoiekMlWiEpauyrFkWMvbwTNmOElmOGRAArfJ" },
	{ "address2", "ohpwhrxUaNybpwPeDGJQRTUArBTHjDnQGatSsRTDsGEnJUORgQmzFDuTGlyJANNiVKveYFCSQXsydGeekXfuFFzNfjICzDpExOH" },
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
curl -d "{\"address1\":\"RAOAgsFiOtlIsAwHhGFKzBvrEsXIOdIizluiVJOvVBoVGeuwyTUSmEXEoZWglxFoiekMlWiEpauyrFkWMvbwTNmOElmOGRAArfJ\",\"address2\":\"ohpwhrxUaNybpwPeDGJQRTUArBTHjDnQGatSsRTDsGEnJUORgQmzFDuTGlyJANNiVKveYFCSQXsydGeekXfuFFzNfjICzDpExOH\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/9082643
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
curl -X DELETE -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/9082643
```

```javascript
await session.deleteAddress(9082643);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(9082643);
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/6615151
```

```javascript
const bin = await session.getBin(6615151);
```

```csharp
CardSavrResponse<Bin> bin = await session.GetBinAsync(6615151);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 6615151,
  "financial_institution_id": 6513809,
  "brand": "ngrSCJwztbCulVcrGAE",
  "issuer": "rqfbIccnLVZxhlpnOLhqqNQKcileqtDImVPVSHximNpfnIriOovPxCFpPTBfGFEkPvEvJvYBZLSLsltVwWcjUNQqwvpMTcOiCRa",
  "type": "mXXEixRXcjKBGw",
  "level": "ySuBsqVNRhUqSoZElyaAawAPMEpVAUiRpSkyTzCFYDjSMRhDsylqewFYvqiRQyQGDlatzgDsBniYLnWULdAFlQftoaaHRHDvkIv",
  "created_on": "1971-02-17T15:33:18.457Z",
  "last_updated_on": "2018-01-09T03:10:39.677Z",
  "bank_identification_number": "67140652"
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
  "financial_institution_id": 6513809,
  "bank_identification_number": "67140652",
  "brand": "ngrSCJwztbCulVcrGAE",
  "issuer": "rqfbIccnLVZxhlpnOLhqqNQKcileqtDImVPVSHximNpfnIriOovPxCFpPTBfGFEkPvEvJvYBZLSLsltVwWcjUNQqwvpMTcOiCRa",
  "type": "mXXEixRXcjKBGw",
  "level": "ySuBsqVNRhUqSoZElyaAawAPMEpVAUiRpSkyTzCFYDjSMRhDsylqewFYvqiRQyQGDlatzgDsBniYLnWULdAFlQftoaaHRHDvkIv"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 6513809 },
	{ "bank_identification_number", "67140652" },
	{ "brand", "ngrSCJwztbCulVcrGAE" },
	{ "issuer", "rqfbIccnLVZxhlpnOLhqqNQKcileqtDImVPVSHximNpfnIriOovPxCFpPTBfGFEkPvEvJvYBZLSLsltVwWcjUNQqwvpMTcOiCRa" },
	{ "type", "mXXEixRXcjKBGw" },
	{ "level", "ySuBsqVNRhUqSoZElyaAawAPMEpVAUiRpSkyTzCFYDjSMRhDsylqewFYvqiRQyQGDlatzgDsBniYLnWULdAFlQftoaaHRHDvkIv" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":6513809,\"bank_identification_number\":\"67140652\",\"brand\":\"ngrSCJwztbCulVcrGAE\",\"issuer\":\"rqfbIccnLVZxhlpnOLhqqNQKcileqtDImVPVSHximNpfnIriOovPxCFpPTBfGFEkPvEvJvYBZLSLsltVwWcjUNQqwvpMTcOiCRa\",\"type\":\"mXXEixRXcjKBGw\",\"level\":\"ySuBsqVNRhUqSoZElyaAawAPMEpVAUiRpSkyTzCFYDjSMRhDsylqewFYvqiRQyQGDlatzgDsBniYLnWULdAFlQftoaaHRHDvkIv\"}"
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
  "financial_institution_id": 7443567,
  "brand": "vQPDPmRshhQEpXvvqUT",
  "issuer": "DqYPlLxVvDPWXqpORmNvpcwVXjUEtcibCSfcTeUeHXleKtsDguQWamZMDSnRpNqxNuoSJXaVaXLtidfdjwICdStsveDpXeqBQlE",
  "type": "HSoRHINTVfIHyk",
  "level": "pyDqiJJaXZajOaXYwaVtkQSVIdtxGAWLVyjXOeHwRcMlLfxXFrNNSyCtrYdUIeIBYtyoUBMUTYeTDJgaqGKCYtikMrqIXpXqrTH"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 7443567 },
	{ "brand", "vQPDPmRshhQEpXvvqUT" },
	{ "issuer", "DqYPlLxVvDPWXqpORmNvpcwVXjUEtcibCSfcTeUeHXleKtsDguQWamZMDSnRpNqxNuoSJXaVaXLtidfdjwICdStsveDpXeqBQlE" },
	{ "type", "HSoRHINTVfIHyk" },
	{ "level", "pyDqiJJaXZajOaXYwaVtkQSVIdtxGAWLVyjXOeHwRcMlLfxXFrNNSyCtrYdUIeIBYtyoUBMUTYeTDJgaqGKCYtikMrqIXpXqrTH" }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":7443567,\"brand\":\"vQPDPmRshhQEpXvvqUT\",\"issuer\":\"DqYPlLxVvDPWXqpORmNvpcwVXjUEtcibCSfcTeUeHXleKtsDguQWamZMDSnRpNqxNuoSJXaVaXLtidfdjwICdStsveDpXeqBQlE\",\"type\":\"HSoRHINTVfIHyk\",\"level\":\"pyDqiJJaXZajOaXYwaVtkQSVIdtxGAWLVyjXOeHwRcMlLfxXFrNNSyCtrYdUIeIBYtyoUBMUTYeTDJgaqGKCYtikMrqIXpXqrTH\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/6615151
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
curl -X DELETE -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/6615151
```

```javascript
await session.deleteBin(6615151);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(6615151);
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1164603
```

```javascript
const card = await session.getCard(1164603, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Card> card = await session.GetCardAsync(1164603, CARDHOLDER_SAFE_KEY);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1164603,
  "address_id": 4039436,
  "bin_id": 13124,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "first_6": "WHoQVXZcRVFfdCxfgpzavdQloejVzxXE",
  "first_7": "fttjUMdWxZIyhzFIWfQqVbKsEDlQkJpH",
  "first_8": "tGIzBGjqqnGKWCxDOkvzTbZkrasFhEfV",
  "created_on": "1981-12-13T17:57:16.238Z",
  "last_updated_on": "1973-09-12T04:35:59.799Z",
  "expiration_month": 1,
  "expiration_year": 31,
  "cardholder_id": 5899312,
  "par": "sQcaUeMkIhVXFXCQstpRhPqFjvptc",
  "pan": "MGFicAkqPQgcNkO",
  "cvv": "tZT"
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
  "cardholder_id": 5899312,
  "address_id": 4039436,
  "bin_id": 13124,
  "par": "sQcaUeMkIhVXFXCQstpRhPqFjvptc",
  "pan": "MGFicAkqPQgcNkO",
  "cvv": "tZT",
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
	{ "cardholder_id", 5899312 },
	{ "address_id", 4039436 },
	{ "bin_id", 13124 },
	{ "par", "sQcaUeMkIhVXFXCQstpRhPqFjvptc" },
	{ "pan", "MGFicAkqPQgcNkO" },
	{ "cvv", "tZT" },
	{ "expiration_month", 1 },
	{ "expiration_year", 31 },
	{ "name_on_card", "Joe C Smith" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" }
};

CardSavrResponse<Card> card = await http.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":5899312,\"address_id\":4039436,\"bin_id\":13124,\"par\":\"sQcaUeMkIhVXFXCQstpRhPqFjvptc\",\"pan\":\"MGFicAkqPQgcNkO\",\"cvv\":\"tZT\",\"expiration_month\":1,\"expiration_year\":31,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\"}"
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
  "address_id": 1854011,
  "bin_id": 7410488,
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
	{ "address_id", 1854011 },
	{ "bin_id", 7410488 },
	{ "name_on_card", "Joe C Smith" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "expiration_month", 1 },
	{ "expiration_year", 31 }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"address_id\":1854011,\"bin_id\":7410488,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"expiration_month\":1,\"expiration_year\":31}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1164603
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
curl -X DELETE -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1164603
```

```javascript
await session.deleteCard(1164603, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(1164603, CARDHOLDER_SAFE_KEY);
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/1867867
```

```javascript
const user = await session.getUser(1867867, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<User> user = await session.GetUserAsync(1867867, CARDHOLDER_SAFE_KEY);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1867867,
  "financial_institution_id": 9424399,
  "last_password": "HQmwfa/jboHJtcTxQ8Pt5JpFz5yEcDeMEJ7Zh44WJHw=",
  "password": "Pa$$w0rd",
  "next_password": "RCMJmsJAeaio9YqtKO+SfFHNof72TFIlg4Lxs7rt5SE=",
  "expired_password_1": "O8DJDJuE+XpcblWYyNbvg8jt5zDh7/A5GvVe5+vwKIM=",
  "expired_password_2": "o63A9FM+mOdHqYduyxId8yE938biOtVOhNm2GU0o0rk=",
  "cardholder_safe_key": "JJlbT4DbIM2M5iszMrAFgvWEz4OtQdZwu4TSCPQf8Og=",
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1979-04-08T21:29:04.488Z",
  "is_locked": true,
  "password_lifetime": 223,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_auditor",
  "phone_number": "acslAwosgVeBri",
  "custom_data": {
    "hBrsahEBZYut": "@,#70ybOe[M$I/qXZ*_8-dc+hgYX@fj",
    "nMZkWJsRiXti": 65,
    "xVMAbbXKwzWF": true
  },
  "next_rotation_on": "2015-03-30T18:46:39.849Z",
  "created_on": "1975-12-30T09:41:54.147Z",
  "last_updated_on": "1995-12-08T10:42:33.681Z",
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
  "financial_institution_id": 9424399,
  "username": "jsmith123",
  "password": "Pa$$w0rd",
  "next_password": "RCMJmsJAeaio9YqtKO+SfFHNof72TFIlg4Lxs7rt5SE=",
  "cardholder_safe_key": "JJlbT4DbIM2M5iszMrAFgvWEz4OtQdZwu4TSCPQf8Og=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 223,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_auditor",
  "phone_number": "acslAwosgVeBri",
  "custom_data": {
    "hBrsahEBZYut": "@,#70ybOe[M$I/qXZ*_8-dc+hgYX@fj",
    "nMZkWJsRiXti": 65,
    "xVMAbbXKwzWF": true
  },
  "next_rotation_on": "2015-03-30T18:46:39.849Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 9424399 },
	{ "username", "jsmith123" },
	{ "password", "Pa$$w0rd" },
	{ "next_password", "RCMJmsJAeaio9YqtKO+SfFHNof72TFIlg4Lxs7rt5SE=" },
	{ "cardholder_safe_key", "JJlbT4DbIM2M5iszMrAFgvWEz4OtQdZwu4TSCPQf8Og=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 223 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "swch_auditor" },
	{ "phone_number", "acslAwosgVeBri" },
	{ "next_rotation_on", "2015-03-30T18:46:39.849Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":9424399,\"username\":\"jsmith123\",\"password\":\"Pa$$w0rd\",\"next_password\":\"RCMJmsJAeaio9YqtKO+SfFHNof72TFIlg4Lxs7rt5SE=\",\"cardholder_safe_key\":\"JJlbT4DbIM2M5iszMrAFgvWEz4OtQdZwu4TSCPQf8Og=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":223,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"swch_auditor\",\"phone_number\":\"acslAwosgVeBri\",\"custom_data\":{\"hBrsahEBZYut\":\"@,#70ybOe[M$I/qXZ*_8-dc+hgYX@fj\",\"nMZkWJsRiXti\":65,\"xVMAbbXKwzWF\":true},\"next_rotation_on\":\"2015-03-30T18:46:39.849Z\"}"
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
  "financial_institution_id": 5877948,
  "password": "Pa$$w0rd",
  "next_password": "Nv/7YULEpoU3IP9jSi0AQwqjXbDswrryjT7iyGAdpR8=",
  "cardholder_safe_key": "L2dP/A7ZHo9dpLXIIOy/ZCAOXrhc4ww87MZyaObn00k=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 250,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "customer_agent",
  "phone_number": "UAMIPhkEvTPgOU",
  "custom_data": {
    "FSysOCdMPbsn": "Xh",
    "fZZYSWANtOZU": 85,
    "ZeqNBariyCHz": true
  },
  "next_rotation_on": "1975-12-20T02:51:41.892Z",
  "username": "jsmith123"
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 5877948 },
	{ "password", "Pa$$w0rd" },
	{ "next_password", "Nv/7YULEpoU3IP9jSi0AQwqjXbDswrryjT7iyGAdpR8=" },
	{ "cardholder_safe_key", "L2dP/A7ZHo9dpLXIIOy/ZCAOXrhc4ww87MZyaObn00k=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 250 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "customer_agent" },
	{ "phone_number", "UAMIPhkEvTPgOU" },
	{ "next_rotation_on", "1975-12-20T02:51:41.892Z" },
	{ "username", "jsmith123" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":5877948,\"password\":\"Pa$$w0rd\",\"next_password\":\"Nv/7YULEpoU3IP9jSi0AQwqjXbDswrryjT7iyGAdpR8=\",\"cardholder_safe_key\":\"L2dP/A7ZHo9dpLXIIOy/ZCAOXrhc4ww87MZyaObn00k=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":250,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"customer_agent\",\"phone_number\":\"UAMIPhkEvTPgOU\",\"custom_data\":{\"FSysOCdMPbsn\":\"Xh\",\"fZZYSWANtOZU\":85,\"ZeqNBariyCHz\":true},\"next_rotation_on\":\"1975-12-20T02:51:41.892Z\",\"username\":\"jsmith123\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/1867867
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
curl -X DELETE -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/1867867
```

```javascript
await session.deleteUser(1867867);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(1867867);
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
https://api.INSTANCE.cardsavr.io/financial_institutions/8585447
```

```javascript
const financial institution = await session.getFinancial Institution(8585447);
```

```csharp
CardSavrResponse<Financial Institution> financial institution = await session.GetFinancial InstitutionAsync(8585447);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 8585447,
  "name": "ILqXJvYZTAsbxUFtUujBrwXvzqAerOCFUNwLvKBxsTACuCrPvKDsLWFXiMrKVHk",
  "description": "aqSvTNdlyIeXWBRfrCWdQsErvM",
  "lookup_key": "MkdNuRlgykbdtarZsIqlOPfXyFMEqBbXZqABfaaBptnJGGLrbfZTkQUJCEueTVj",
  "alternate_lookup_key": "KmKrtgAZsadPXroCnKfBgOEIlfXXtmTgHobrHdXIoDdfuImDULMFuWgJlAOlaQe",
  "created_on": "2010-07-28T23:41:20.126Z",
  "last_updated_on": "1996-10-12T17:47:32.740Z"
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
  "name": "ILqXJvYZTAsbxUFtUujBrwXvzqAerOCFUNwLvKBxsTACuCrPvKDsLWFXiMrKVHk",
  "description": "aqSvTNdlyIeXWBRfrCWdQsErvM",
  "lookup_key": "MkdNuRlgykbdtarZsIqlOPfXyFMEqBbXZqABfaaBptnJGGLrbfZTkQUJCEueTVj",
  "alternate_lookup_key": "KmKrtgAZsadPXroCnKfBgOEIlfXXtmTgHobrHdXIoDdfuImDULMFuWgJlAOlaQe"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "ILqXJvYZTAsbxUFtUujBrwXvzqAerOCFUNwLvKBxsTACuCrPvKDsLWFXiMrKVHk" },
	{ "description", "aqSvTNdlyIeXWBRfrCWdQsErvM" },
	{ "lookup_key", "MkdNuRlgykbdtarZsIqlOPfXyFMEqBbXZqABfaaBptnJGGLrbfZTkQUJCEueTVj" },
	{ "alternate_lookup_key", "KmKrtgAZsadPXroCnKfBgOEIlfXXtmTgHobrHdXIoDdfuImDULMFuWgJlAOlaQe" }
};

CardSavrResponse<Financial Institution> financial institution = await http.CreateFinancial InstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"ILqXJvYZTAsbxUFtUujBrwXvzqAerOCFUNwLvKBxsTACuCrPvKDsLWFXiMrKVHk\",\"description\":\"aqSvTNdlyIeXWBRfrCWdQsErvM\",\"lookup_key\":\"MkdNuRlgykbdtarZsIqlOPfXyFMEqBbXZqABfaaBptnJGGLrbfZTkQUJCEueTVj\",\"alternate_lookup_key\":\"KmKrtgAZsadPXroCnKfBgOEIlfXXtmTgHobrHdXIoDdfuImDULMFuWgJlAOlaQe\"}"
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
  "name": "uoUQVVveHYPNvPIGbhKBFskcFjdUZeyTdtzgvvfPKFTbkJIauHfABvTAUjPdlzq",
  "description": "BvMCbpj",
  "lookup_key": "kaIiNVyjfBQYFJJlwgNZJxcpEsvKqSKfolWSipkhPLxJKZSDDVEhnnIZBVeHYLn",
  "alternate_lookup_key": "cYBQyQciPYfDuwkljPawyQmWOKLzsAmnRuroPFoCDtfAPYrkQXlMJucBmKgYabL"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "uoUQVVveHYPNvPIGbhKBFskcFjdUZeyTdtzgvvfPKFTbkJIauHfABvTAUjPdlzq" },
	{ "description", "BvMCbpj" },
	{ "lookup_key", "kaIiNVyjfBQYFJJlwgNZJxcpEsvKqSKfolWSipkhPLxJKZSDDVEhnnIZBVeHYLn" },
	{ "alternate_lookup_key", "cYBQyQciPYfDuwkljPawyQmWOKLzsAmnRuroPFoCDtfAPYrkQXlMJucBmKgYabL" }
};

CardSavrResponse<Financial Institution> financial institution = await http.UpdateFinancial InstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"uoUQVVveHYPNvPIGbhKBFskcFjdUZeyTdtzgvvfPKFTbkJIauHfABvTAUjPdlzq\",\"description\":\"BvMCbpj\",\"lookup_key\":\"kaIiNVyjfBQYFJJlwgNZJxcpEsvKqSKfolWSipkhPLxJKZSDDVEhnnIZBVeHYLn\",\"alternate_lookup_key\":\"cYBQyQciPYfDuwkljPawyQmWOKLzsAmnRuroPFoCDtfAPYrkQXlMJucBmKgYabL\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/8585447
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
curl -X DELETE -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/8585447
```

```javascript
await session.deleteFinancial Institution(8585447);
```

```csharp
CardSavrResponse<Financial Institution> financial institution = await http.DeleteFinancial InstitutionAsync(8585447);
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
https://api.INSTANCE.cardsavr.io/integrators/2715875
```

```javascript
const integrator = await session.getIntegrator(2715875);
```

```csharp
CardSavrResponse<Integrator> integrator = await session.GetIntegratorAsync(2715875);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2715875,
  "name": "mXWVnuGDLYARQSuLfWqGIMiTCFHlNTZIVhtCnfeWsisSZwMUM",
  "integrator_type": "swch_internal",
  "description": "BVTyqvQTSvkT",
  "last_key": "xWWlZm5OU6lsARBHix6X6w5NrGoTEG9nNIitzYlOMz0=",
  "current_key": "nnTdmtAgy/3BGEIbeN6MKoF8vjm6r4JASZ9OTd1B+6g=",
  "next_key": "RItscP+WIb10mQa5nnoo1vXnOqvwm5U/UkmmIxLAhzo=",
  "key_lifetime": 143,
  "next_rotation_on": "2001-11-07T16:17:52.264Z",
  "created_on": "1977-06-27T09:19:34.490Z",
  "last_updated_on": "1978-10-05T09:34:59.517Z"
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
  "name": "mXWVnuGDLYARQSuLfWqGIMiTCFHlNTZIVhtCnfeWsisSZwMUM",
  "integrator_type": "swch_internal",
  "description": "BVTyqvQTSvkT",
  "last_key": "xWWlZm5OU6lsARBHix6X6w5NrGoTEG9nNIitzYlOMz0=",
  "current_key": "nnTdmtAgy/3BGEIbeN6MKoF8vjm6r4JASZ9OTd1B+6g=",
  "next_key": "RItscP+WIb10mQa5nnoo1vXnOqvwm5U/UkmmIxLAhzo=",
  "key_lifetime": 143,
  "next_rotation_on": "2001-11-07T16:17:52.264Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "mXWVnuGDLYARQSuLfWqGIMiTCFHlNTZIVhtCnfeWsisSZwMUM" },
	{ "integrator_type", "swch_internal" },
	{ "description", "BVTyqvQTSvkT" },
	{ "last_key", "xWWlZm5OU6lsARBHix6X6w5NrGoTEG9nNIitzYlOMz0=" },
	{ "current_key", "nnTdmtAgy/3BGEIbeN6MKoF8vjm6r4JASZ9OTd1B+6g=" },
	{ "next_key", "RItscP+WIb10mQa5nnoo1vXnOqvwm5U/UkmmIxLAhzo=" },
	{ "key_lifetime", 143 },
	{ "next_rotation_on", "2001-11-07T16:17:52.264Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"mXWVnuGDLYARQSuLfWqGIMiTCFHlNTZIVhtCnfeWsisSZwMUM\",\"integrator_type\":\"swch_internal\",\"description\":\"BVTyqvQTSvkT\",\"last_key\":\"xWWlZm5OU6lsARBHix6X6w5NrGoTEG9nNIitzYlOMz0=\",\"current_key\":\"nnTdmtAgy/3BGEIbeN6MKoF8vjm6r4JASZ9OTd1B+6g=\",\"next_key\":\"RItscP+WIb10mQa5nnoo1vXnOqvwm5U/UkmmIxLAhzo=\",\"key_lifetime\":143,\"next_rotation_on\":\"2001-11-07T16:17:52.264Z\"}"
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
  "name": "rSvdzfSYTMyyLBrPNgmVAftnEbhNhunPYCdWhhQxRJTqYiFHr",
  "integrator_type": "swch_internal",
  "description": "jzKRkHrbxwfuItfzxAkUo",
  "last_key": "OWO6vGJbRirZM4EtQt/Zwj5gooBDW4uxYyD7BRo71CA=",
  "current_key": "oQ6InO1Ejdin/VyJNv3QG9IzrD/NR1D4Wn4vVbdHuyY=",
  "next_key": "NR6DPKEPYQOSDrovQ5DsA9/7XT3RmyZfXoR5ql12tLs=",
  "key_lifetime": 168,
  "next_rotation_on": "2010-05-31T03:53:28.347Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "rSvdzfSYTMyyLBrPNgmVAftnEbhNhunPYCdWhhQxRJTqYiFHr" },
	{ "integrator_type", "swch_internal" },
	{ "description", "jzKRkHrbxwfuItfzxAkUo" },
	{ "last_key", "OWO6vGJbRirZM4EtQt/Zwj5gooBDW4uxYyD7BRo71CA=" },
	{ "current_key", "oQ6InO1Ejdin/VyJNv3QG9IzrD/NR1D4Wn4vVbdHuyY=" },
	{ "next_key", "NR6DPKEPYQOSDrovQ5DsA9/7XT3RmyZfXoR5ql12tLs=" },
	{ "key_lifetime", 168 },
	{ "next_rotation_on", "2010-05-31T03:53:28.347Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"rSvdzfSYTMyyLBrPNgmVAftnEbhNhunPYCdWhhQxRJTqYiFHr\",\"integrator_type\":\"swch_internal\",\"description\":\"jzKRkHrbxwfuItfzxAkUo\",\"last_key\":\"OWO6vGJbRirZM4EtQt/Zwj5gooBDW4uxYyD7BRo71CA=\",\"current_key\":\"oQ6InO1Ejdin/VyJNv3QG9IzrD/NR1D4Wn4vVbdHuyY=\",\"next_key\":\"NR6DPKEPYQOSDrovQ5DsA9/7XT3RmyZfXoR5ql12tLs=\",\"key_lifetime\":168,\"next_rotation_on\":\"2010-05-31T03:53:28.347Z\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/2715875
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
curl -X DELETE -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/2715875
```

```javascript
await session.deleteIntegrator(2715875);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(2715875);
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
https://api.INSTANCE.cardsavr.io/merchant_sites/834246
```

```javascript
const merchant site = await session.getMerchant Site(834246);
```

```csharp
CardSavrResponse<Merchant Site> merchant site = await session.GetMerchant SiteAsync(834246);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 834246,
  "name": "UnlZ",
  "host": "xggdSkByWudAQNYdRaRruUUokhj",
  "image_lookup_key": "RfhiJcoJNwLVtgisGniRLwXAUb",
  "images": [
    {
      "gdeVVFSCKErU": "f(2OZh!,4,Dc#Okmuz",
      "fextoQMRDkiI": 51,
      "NykMKouOPOIp": false
    },
    {
      "fMMMSWHdoTZE": "Gc1Gv3+<,XrqH,EFSo$<@,D*kH8,UEBe",
      "tPgjKqeidbmt": 22,
      "IDEHQjpDKDmL": true
    },
    {
      "duAGuzUtLUks": "LGHXEoM6Kvq6raW67Vn_.15uU*2sr,g",
      "JRXCuQaBdyGy": 27,
      "HZOaBsIqRAvc": false
    }
  ],
  "mfa": true,
  "tags": "QIWnOWeqPaMiRoeXnhMY",
  "login": {
    "EYvWgjLcyimY": "RVG}EK$t7m~l",
    "lOLHOmbtkxNW": 88,
    "JPPdcAJDZuit": true
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
https://api.INSTANCE.cardsavr.io/notifications/6594872
```

```javascript
const notification = await session.getNotification(6594872);
```

```csharp
CardSavrResponse<Notification> notification = await session.GetNotificationAsync(6594872);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 6594872,
  "name": "jpcyZjyQpniNtfUMGdYBXamJTMBsmwywxYevkusMpIhrUbLfKVyGKhoOqVOTMTQ",
  "type": "webhook",
  "config": {
    "sMSRrSGWrTzb": "Qe5%4bUsHH(MI56Z",
    "oissbxjkRonJ": 92,
    "eSsiVUwRvlWc": true
  },
  "created_on": "1989-08-04T22:48:39.401Z",
  "last_updated_on": "2002-08-29T00:16:24.327Z",
  "financial_institution_id": 3287356
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
  "financial_institution_id": 3287356,
  "name": "jpcyZjyQpniNtfUMGdYBXamJTMBsmwywxYevkusMpIhrUbLfKVyGKhoOqVOTMTQ",
  "type": "webhook",
  "config": {
    "sMSRrSGWrTzb": "Qe5%4bUsHH(MI56Z",
    "oissbxjkRonJ": 92,
    "eSsiVUwRvlWc": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 3287356 },
	{ "name", "jpcyZjyQpniNtfUMGdYBXamJTMBsmwywxYevkusMpIhrUbLfKVyGKhoOqVOTMTQ" },
	{ "type", "webhook" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":3287356,\"name\":\"jpcyZjyQpniNtfUMGdYBXamJTMBsmwywxYevkusMpIhrUbLfKVyGKhoOqVOTMTQ\",\"type\":\"webhook\",\"config\":{\"sMSRrSGWrTzb\":\"Qe5%4bUsHH(MI56Z\",\"oissbxjkRonJ\":92,\"eSsiVUwRvlWc\":true}}"
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
  "name": "dQKSlpGkNdRqKjXBNnJJuKxvDCIFyekuqMmcOjIxbeVEBOAuTUylMvZqswjEoOH",
  "type": "email",
  "config": {
    "AibnAMzcUZhD": "LMDFR)J00_(nzMXN~",
    "FtegpKDTGVdV": 54,
    "YYrQHYWQwFUi": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "dQKSlpGkNdRqKjXBNnJJuKxvDCIFyekuqMmcOjIxbeVEBOAuTUylMvZqswjEoOH" },
	{ "type", "email" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```shell
curl -d "{\"name\":\"dQKSlpGkNdRqKjXBNnJJuKxvDCIFyekuqMmcOjIxbeVEBOAuTUylMvZqswjEoOH\",\"type\":\"email\",\"config\":{\"AibnAMzcUZhD\":\"LMDFR)J00_(nzMXN~\",\"FtegpKDTGVdV\":54,\"YYrQHYWQwFUi\":false}}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/6594872
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
curl -X DELETE -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/6594872
```

```javascript
await session.deleteNotification(6594872);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(6594872);
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1148807
```

```javascript
const singlesitejob = await session.getSingleSiteJob(1148807);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await session.GetSingleSiteJobAsync(1148807);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1148807,
  "card_placement_result_id": "yIHPOXAOKlAPQ",
  "status": "REQUESTED",
  "safe_blob": "MvKhnAhDvfNiahrogtWsut",
  "safe_nonce": "yuEBQqWLgB",
  "custom_data": {
    "VRIpjwPhoCJT": "(p8",
    "aXctXQQTZCqO": 51,
    "XSrPoZaljvRI": false
  },
  "failure_reason": "WybJbmqPSTilGY",
  "messaging_addresses": "otaPXqGqRDcnVqFWWVCakwcSiNGoALO",
  "current_state": "QaIhPfvoqkouRCnadqfnssUorCtdCBixAwgOqsusNumzBWDMBJLLvkqKndPboKF",
  "do_not_queue": false,
  "user_is_present": false,
  "time_elapsed": 1463114,
  "job_ready_on": "1983-07-10T19:07:32.082Z",
  "started_on": "1982-02-01T13:43:04.446Z",
  "completed_on": "2011-05-29T13:49:43.296Z",
  "expiration_date": "1975-06-20T10:14:51.273Z",
  "created_on": "2014-05-04T05:06:28.177Z",
  "last_updated_on": "1989-08-12T05:02:50.241Z",
  "place_card_on_multiple_sites_job_id": 3064372,
  "user_id": 8731577,
  "card_id": 9901248,
  "account_id": 1658957
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
  "place_card_on_multiple_sites_job_id": 3064372,
  "user_id": 8731577,
  "card_id": 9901248,
  "account_id": 1658957,
  "status": "REQUESTED",
  "custom_data": {
    "VRIpjwPhoCJT": "(p8",
    "aXctXQQTZCqO": 51,
    "XSrPoZaljvRI": false
  },
  "failure_reason": "WybJbmqPSTilGY",
  "current_state": "QaIhPfvoqkouRCnadqfnssUorCtdCBixAwgOqsusNumzBWDMBJLLvkqKndPboKF",
  "do_not_queue": false,
  "user_is_present": false,
  "time_elapsed": 1463114,
  "started_on": "1982-02-01T13:43:04.446Z",
  "completed_on": "2011-05-29T13:49:43.296Z",
  "expiration_date": "1975-06-20T10:14:51.273Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "place_card_on_multiple_sites_job_id", 3064372 },
	{ "user_id", 8731577 },
	{ "card_id", 9901248 },
	{ "account_id", 1658957 },
	{ "status", "REQUESTED" },
	{ "failure_reason", "WybJbmqPSTilGY" },
	{ "current_state", "QaIhPfvoqkouRCnadqfnssUorCtdCBixAwgOqsusNumzBWDMBJLLvkqKndPboKF" },
	{ "do_not_queue", false },
	{ "user_is_present", false },
	{ "time_elapsed", 1463114 },
	{ "started_on", "1982-02-01T13:43:04.446Z" },
	{ "completed_on", "2011-05-29T13:49:43.296Z" },
	{ "expiration_date", "1975-06-20T10:14:51.273Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body);
```

```shell
curl -d "{\"place_card_on_multiple_sites_job_id\":3064372,\"user_id\":8731577,\"card_id\":9901248,\"account_id\":1658957,\"status\":\"REQUESTED\",\"custom_data\":{\"VRIpjwPhoCJT\":\"(p8\",\"aXctXQQTZCqO\":51,\"XSrPoZaljvRI\":false},\"failure_reason\":\"WybJbmqPSTilGY\",\"current_state\":\"QaIhPfvoqkouRCnadqfnssUorCtdCBixAwgOqsusNumzBWDMBJLLvkqKndPboKF\",\"do_not_queue\":false,\"user_is_present\":false,\"time_elapsed\":1463114,\"started_on\":\"1982-02-01T13:43:04.446Z\",\"completed_on\":\"2011-05-29T13:49:43.296Z\",\"expiration_date\":\"1975-06-20T10:14:51.273Z\"}"
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
  "status": "INVALID_NETWORK",
  "custom_data": {
    "ufwoSomZwZsh": ",34s#$F1K%w/U,y0m-_!^rD>8L<d",
    "rgXemdWZcmMe": 17,
    "tKAanbshlaPo": true
  },
  "failure_reason": "spUzoRkjtmOVvbePNbgF",
  "current_state": "XBxFxNfcyBYUOosmODPjeLeRTWhrjvpIABmSLSlZdWDDBaGidMsjFyyyTKpLYJZ",
  "do_not_queue": true,
  "user_is_present": true,
  "time_elapsed": 9005859,
  "started_on": "1976-06-15T18:44:46.706Z",
  "completed_on": "2000-07-10T21:57:32.667Z",
  "expiration_date": "2004-06-05T14:58:27.467Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "status", "INVALID_NETWORK" },
	{ "failure_reason", "spUzoRkjtmOVvbePNbgF" },
	{ "current_state", "XBxFxNfcyBYUOosmODPjeLeRTWhrjvpIABmSLSlZdWDDBaGidMsjFyyyTKpLYJZ" },
	{ "do_not_queue", true },
	{ "user_is_present", true },
	{ "time_elapsed", 9005859 },
	{ "started_on", "1976-06-15T18:44:46.706Z" },
	{ "completed_on", "2000-07-10T21:57:32.667Z" },
	{ "expiration_date", "2004-06-05T14:58:27.467Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body);
```

```shell
curl -d "{\"status\":\"INVALID_NETWORK\",\"custom_data\":{\"ufwoSomZwZsh\":\",34s#$F1K%w/U,y0m-_!^rD>8L<d\",\"rgXemdWZcmMe\":17,\"tKAanbshlaPo\":true},\"failure_reason\":\"spUzoRkjtmOVvbePNbgF\",\"current_state\":\"XBxFxNfcyBYUOosmODPjeLeRTWhrjvpIABmSLSlZdWDDBaGidMsjFyyyTKpLYJZ\",\"do_not_queue\":true,\"user_is_present\":true,\"time_elapsed\":9005859,\"started_on\":\"1976-06-15T18:44:46.706Z\",\"completed_on\":\"2000-07-10T21:57:32.667Z\",\"expiration_date\":\"2004-06-05T14:58:27.467Z\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1148807
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
curl -X DELETE -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1148807
```

```javascript
await session.deleteSingleSiteJob(1148807);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(1148807);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

