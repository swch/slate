# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

```shell
curl -H "Content-Type: application/javascript
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1379872
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1379872,
  "last_card_placed_id": 9886028,
  "username": "jsmith123",
  "password": "Pa$$w0rd",
  "last_login": "2013-02-14T05:14:07.708Z",
  "last_password_update": "2008-10-17T03:53:01.821Z",
  "last_saved_card": "2018-08-26T18:06:21.205Z",
  "created_on": "1983-09-21T09:36:51.829Z",
  "last_updated_on": "1970-09-29T04:52:15.486Z",
  "cardholder_id": 2260598,
  "merchant_site_id": 9315732
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
await session.createAccount({
  "cardholder_id": 2260598,
  "merchant_site_id": 9315732,
  "last_card_placed_id": 9886028,
  "username": "jsmith123",
  "password": "Pa$$w0rd"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 2260598 },
	{ "merchant_site_id", 9315732 },
	{ "last_card_placed_id", 9886028 },
	{ "username", "jsmith123" },
	{ "password", "Pa$$w0rd" }
};

CardSavrResponse<Account> account = await cardholder.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":2260598,\"merchant_site_id\":9315732,\"last_card_placed_id\":9886028,\"username\":\"jsmith123\",\"password\":\"Pa$$w0rd\"}"
-X POST -H "Content-Type: application/javascript"
-H "new-cardholder-safe-key: NEWCARDHODLER_SAFE_KEY"
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
await session.updateAccount({
  "last_card_placed_id": 8655242,
  "username": "jsmith123",
  "password": "Pa$$w0rd"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 8655242 },
	{ "username", "jsmith123" },
	{ "password", "Pa$$w0rd" }
};

CardSavrResponse<Account> account = await cardholder.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"last_card_placed_id\":8655242,\"username\":\"jsmith123\",\"password\":\"Pa$$w0rd\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1379872
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
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1379872
```

```javascript
await session.deleteAccount(1379872, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Account> account = await cardholder.DeleteAccountAsync(1379872, CARDHOLDER_SAFE_KEY);
```

### Path

DELETE /cardsavr_accounts/{id}

### Description

Delete a account and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Addresses
Address objects contain billing address information for a particular user.
## Get address

```shell
curl -H "Content-Type: application/javascript
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1657778
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1657778,
  "address1": "XOuVcXLNBTrMacPpHDltWGtmhUWmfOOIyzPpgWlwGDCLHwqdQKJeXFrjdbOAKywvCnFngIqVcPEIobnxGxJKqNwPpzLKxdDtGBx",
  "address2": "TMryAmeSvijJNqifWeDHQIbHIycyENvWvljcYpflxvJPMLVKUYAqKFxvDhyEgKTmXZUDBbvRUccpYyxjcXNBkCXolLUHxkDpTie",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "created_on": "1985-11-14T16:19:00.749Z",
  "last_updated_on": "1979-08-26T21:59:50.406Z",
  "user_id": 6084500
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
await session.createAddress({
  "user_id": 6084500,
  "address1": "XOuVcXLNBTrMacPpHDltWGtmhUWmfOOIyzPpgWlwGDCLHwqdQKJeXFrjdbOAKywvCnFngIqVcPEIobnxGxJKqNwPpzLKxdDtGBx",
  "address2": "TMryAmeSvijJNqifWeDHQIbHIycyENvWvljcYpflxvJPMLVKUYAqKFxvDhyEgKTmXZUDBbvRUccpYyxjcXNBkCXolLUHxkDpTie",
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
	{ "user_id", 6084500 },
	{ "address1", "XOuVcXLNBTrMacPpHDltWGtmhUWmfOOIyzPpgWlwGDCLHwqdQKJeXFrjdbOAKywvCnFngIqVcPEIobnxGxJKqNwPpzLKxdDtGBx" },
	{ "address2", "TMryAmeSvijJNqifWeDHQIbHIycyENvWvljcYpflxvJPMLVKUYAqKFxvDhyEgKTmXZUDBbvRUccpYyxjcXNBkCXolLUHxkDpTie" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true }
};

CardSavrResponse<Address> address = await cardholder.CreateAddressAsync(body);
```

```shell
curl -d "{\"user_id\":6084500,\"address1\":\"XOuVcXLNBTrMacPpHDltWGtmhUWmfOOIyzPpgWlwGDCLHwqdQKJeXFrjdbOAKywvCnFngIqVcPEIobnxGxJKqNwPpzLKxdDtGBx\",\"address2\":\"TMryAmeSvijJNqifWeDHQIbHIycyENvWvljcYpflxvJPMLVKUYAqKFxvDhyEgKTmXZUDBbvRUccpYyxjcXNBkCXolLUHxkDpTie\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true}"
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
await session.updateAddress({
  "address1": "ovlftxeVqgQWdXoRnfayrQIplkLrsqbubdzsfVaHsWewbmlVoEENoGpjoiFIHSouZopFkugxxTsUmLqxortSUkPxwUiguaLmTRs",
  "address2": "AeKpYZNAMMuZJVyRLpzHTDYfrncSVTuzUTpniDOqeJoXnmQgbNnhZLFuuXppHCfFLfSxjPvoAPCWFjwHZqThNScNUFMeNtrLDbV",
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
	{ "address1", "ovlftxeVqgQWdXoRnfayrQIplkLrsqbubdzsfVaHsWewbmlVoEENoGpjoiFIHSouZopFkugxxTsUmLqxortSUkPxwUiguaLmTRs" },
	{ "address2", "AeKpYZNAMMuZJVyRLpzHTDYfrncSVTuzUTpniDOqeJoXnmQgbNnhZLFuuXppHCfFLfSxjPvoAPCWFjwHZqThNScNUFMeNtrLDbV" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false }
};

CardSavrResponse<Address> address = await cardholder.UpdateAddressAsync(body);
```

```shell
curl -d "{\"address1\":\"ovlftxeVqgQWdXoRnfayrQIplkLrsqbubdzsfVaHsWewbmlVoEENoGpjoiFIHSouZopFkugxxTsUmLqxortSUkPxwUiguaLmTRs\",\"address2\":\"AeKpYZNAMMuZJVyRLpzHTDYfrncSVTuzUTpniDOqeJoXnmQgbNnhZLFuuXppHCfFLfSxjPvoAPCWFjwHZqThNScNUFMeNtrLDbV\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1657778
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1657778
```

```javascript
await session.deleteAddress(1657778);
```

```csharp
CardSavrResponse<Address> address = await cardholder.DeleteAddressAsync(1657778);
```

### Path

DELETE /cardsavr_addresses/{id}

### Description

Delete a address and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Bins
A cardsavr_bin object
## Get bin

```shell
curl -H "Content-Type: application/javascript
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1725753
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1725753,
  "financial_institution_id": 5651508,
  "brand": "TuyRahTUPNUgxgsKhIh",
  "issuer": "MyLvIlkExQYFhVUVxaEyJcCljxwYPwXHhKeEOdNtJizTcsNUJCGkuTAQzdCRnZiYihycuBrvUctTWouxOaaqmHGcrzOxqKAOmBv",
  "type": "WKXvdCnJwvbQVO",
  "level": "dDIgOGvmLrPxtxXgvNeNcevVyDOgTmjHytdMqNWVlMNkSKsVmuLWlVfzEGRoTqXdMakfTyEkWcwnBONorgxxknxFHDWYIOfRYvl",
  "created_on": "1972-07-28T08:27:03.970Z",
  "last_updated_on": "1972-01-28T09:50:10.789Z",
  "bank_identification_number": "24424147"
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
await session.createBin({
  "financial_institution_id": 5651508,
  "bank_identification_number": "24424147",
  "brand": "TuyRahTUPNUgxgsKhIh",
  "issuer": "MyLvIlkExQYFhVUVxaEyJcCljxwYPwXHhKeEOdNtJizTcsNUJCGkuTAQzdCRnZiYihycuBrvUctTWouxOaaqmHGcrzOxqKAOmBv",
  "type": "WKXvdCnJwvbQVO",
  "level": "dDIgOGvmLrPxtxXgvNeNcevVyDOgTmjHytdMqNWVlMNkSKsVmuLWlVfzEGRoTqXdMakfTyEkWcwnBONorgxxknxFHDWYIOfRYvl"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 5651508 },
	{ "bank_identification_number", "24424147" },
	{ "brand", "TuyRahTUPNUgxgsKhIh" },
	{ "issuer", "MyLvIlkExQYFhVUVxaEyJcCljxwYPwXHhKeEOdNtJizTcsNUJCGkuTAQzdCRnZiYihycuBrvUctTWouxOaaqmHGcrzOxqKAOmBv" },
	{ "type", "WKXvdCnJwvbQVO" },
	{ "level", "dDIgOGvmLrPxtxXgvNeNcevVyDOgTmjHytdMqNWVlMNkSKsVmuLWlVfzEGRoTqXdMakfTyEkWcwnBONorgxxknxFHDWYIOfRYvl" }
};

CardSavrResponse<Bin> bin = await cardholder.CreateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":5651508,\"bank_identification_number\":\"24424147\",\"brand\":\"TuyRahTUPNUgxgsKhIh\",\"issuer\":\"MyLvIlkExQYFhVUVxaEyJcCljxwYPwXHhKeEOdNtJizTcsNUJCGkuTAQzdCRnZiYihycuBrvUctTWouxOaaqmHGcrzOxqKAOmBv\",\"type\":\"WKXvdCnJwvbQVO\",\"level\":\"dDIgOGvmLrPxtxXgvNeNcevVyDOgTmjHytdMqNWVlMNkSKsVmuLWlVfzEGRoTqXdMakfTyEkWcwnBONorgxxknxFHDWYIOfRYvl\"}"
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
await session.updateBin({
  "financial_institution_id": 4583865,
  "brand": "FJjxRrjbmlEXBwYqpYB",
  "issuer": "JKOKVyhgyQPHdGLMUknMOSMAZoKcClPHTIIDHQIwlGREGrWgatICJKmQbgofpmYvebekhqhfMLomsXEllfNZVdEvqFyFfPZZqDd",
  "type": "tzDPZlyLRrtoiH",
  "level": "SDXhFodTcqxLoiDRxfhrTyFeMpjOilHgbLBtQmBGrTJqeSaqTLoEcpWuGGBgXldKRQHUjPmKdVEEBQphcgVcpaRqGGzcDyqDdpE"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 4583865 },
	{ "brand", "FJjxRrjbmlEXBwYqpYB" },
	{ "issuer", "JKOKVyhgyQPHdGLMUknMOSMAZoKcClPHTIIDHQIwlGREGrWgatICJKmQbgofpmYvebekhqhfMLomsXEllfNZVdEvqFyFfPZZqDd" },
	{ "type", "tzDPZlyLRrtoiH" },
	{ "level", "SDXhFodTcqxLoiDRxfhrTyFeMpjOilHgbLBtQmBGrTJqeSaqTLoEcpWuGGBgXldKRQHUjPmKdVEEBQphcgVcpaRqGGzcDyqDdpE" }
};

CardSavrResponse<Bin> bin = await cardholder.UpdateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":4583865,\"brand\":\"FJjxRrjbmlEXBwYqpYB\",\"issuer\":\"JKOKVyhgyQPHdGLMUknMOSMAZoKcClPHTIIDHQIwlGREGrWgatICJKmQbgofpmYvebekhqhfMLomsXEllfNZVdEvqFyFfPZZqDd\",\"type\":\"tzDPZlyLRrtoiH\",\"level\":\"SDXhFodTcqxLoiDRxfhrTyFeMpjOilHgbLBtQmBGrTJqeSaqTLoEcpWuGGBgXldKRQHUjPmKdVEEBQphcgVcpaRqGGzcDyqDdpE\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1725753
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1725753
```

```javascript
await session.deleteBin(1725753);
```

```csharp
CardSavrResponse<Bin> bin = await cardholder.DeleteBinAsync(1725753);
```

### Path

DELETE /cardsavr_bins/{id}

### Description

Delete a bin and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Cards
Card objects contain information about a payment card belonging to a single cardholder. Card objects are used to populate users' payment information on merchant sites.
## Get card

```shell
curl -H "Content-Type: application/javascript
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/5257953
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 5257953,
  "address_id": 6515817,
  "bin_id": 8068657,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "first_6": "tTLZbwLGFRPlZQBuxNxldedUvWoSKpDh",
  "first_7": "qAjdXbFiYNjCJKdIEzxaFprCYUdwDFSw",
  "first_8": "jehWirtYWwMkApRweBpxNXWOVwCeDNwl",
  "created_on": "2006-04-12T15:41:17.212Z",
  "last_updated_on": "2015-09-25T14:09:15.795Z",
  "expiration_month": 1,
  "expiration_year": 31,
  "cardholder_id": 4909304,
  "par": "vlAxinInjMHLmZOPlpeERTrRYFMsm",
  "pan": "CvTMBprTeuAEIvp",
  "cvv": "Jdb"
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
await session.createCard({
  "cardholder_id": 4909304,
  "address_id": 6515817,
  "bin_id": 8068657,
  "par": "vlAxinInjMHLmZOPlpeERTrRYFMsm",
  "pan": "CvTMBprTeuAEIvp",
  "cvv": "Jdb",
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
	{ "cardholder_id", 4909304 },
	{ "address_id", 6515817 },
	{ "bin_id", 8068657 },
	{ "par", "vlAxinInjMHLmZOPlpeERTrRYFMsm" },
	{ "pan", "CvTMBprTeuAEIvp" },
	{ "cvv", "Jdb" },
	{ "expiration_month", 1 },
	{ "expiration_year", 31 },
	{ "name_on_card", "Joe C Smith" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" }
};

CardSavrResponse<Card> card = await cardholder.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":4909304,\"address_id\":6515817,\"bin_id\":8068657,\"par\":\"vlAxinInjMHLmZOPlpeERTrRYFMsm\",\"pan\":\"CvTMBprTeuAEIvp\",\"cvv\":\"Jdb\",\"expiration_month\":1,\"expiration_year\":31,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\"}"
-X POST -H "Content-Type: application/javascript"
-H "new-cardholder-safe-key: NEWCARDHODLER_SAFE_KEY"
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
await session.updateCard({
  "address_id": 1619884,
  "bin_id": 8782098,
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
	{ "address_id", 1619884 },
	{ "bin_id", 8782098 },
	{ "name_on_card", "Joe C Smith" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "expiration_month", 1 },
	{ "expiration_year", 31 }
};

CardSavrResponse<Card> card = await cardholder.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"address_id\":1619884,\"bin_id\":8782098,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"expiration_month\":1,\"expiration_year\":31}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/5257953
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/5257953
```

```javascript
await session.deleteCard(5257953, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Card> card = await cardholder.DeleteCardAsync(5257953, CARDHOLDER_SAFE_KEY);
```

### Path

DELETE /cardsavr_cards/{id}

### Description

Delete a card and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Users
User objects correspond to a single CardSavr user.
## Get user

```shell
curl -H "Content-Type: application/javascript
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/7182434
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 7182434,
  "financial_institution_id": 5294451,
  "last_password": "rt8HQef6L8Aydx6HIGeP/W6Wl+Hw9buj1xNdh11NxzE=",
  "password": "Pa$$w0rd",
  "next_password": "JmwMmnKCotJ+RFfhACfS/Woy+5ghFXxKnXIkC3ixcIQ=",
  "expired_password_1": "Kd79LQ/xtcuv77Nn3nZwSRk7BFRImm+VUr0X9U0DQVY=",
  "expired_password_2": "FZfjpG5/IhJkmpjjAI53FYxTvP6qG0lGCJI7qYboz1E=",
  "cardholder_safe_key": "4RvY8qiRbGUpAM9LyM74K6B5DGcSsSzENr2abHcfD6g=",
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1980-08-24T11:01:10.241Z",
  "is_locked": false,
  "password_lifetime": 37,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "developer",
  "phone_number": "vIYpiMdWqGSdIH",
  "custom_data": {
    "pLSezLaYuDfD": "~fpNs(!fQV.(MZ)/3,",
    "HsVbNiXNQagK": 9,
    "RIoAmhpUytfZ": true
  },
  "next_rotation_on": "1995-12-05T13:21:13.451Z",
  "created_on": "2010-06-13T10:45:09.761Z",
  "last_updated_on": "1992-03-08T05:06:26.338Z",
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
await session.createUser({
  "financial_institution_id": 5294451,
  "username": "jsmith123",
  "password": "Pa$$w0rd",
  "next_password": "JmwMmnKCotJ+RFfhACfS/Woy+5ghFXxKnXIkC3ixcIQ=",
  "cardholder_safe_key": "4RvY8qiRbGUpAM9LyM74K6B5DGcSsSzENr2abHcfD6g=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 37,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "developer",
  "phone_number": "vIYpiMdWqGSdIH",
  "custom_data": {
    "pLSezLaYuDfD": "~fpNs(!fQV.(MZ)/3,",
    "HsVbNiXNQagK": 9,
    "RIoAmhpUytfZ": true
  },
  "next_rotation_on": "1995-12-05T13:21:13.451Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 5294451 },
	{ "username", "jsmith123" },
	{ "password", "Pa$$w0rd" },
	{ "next_password", "JmwMmnKCotJ+RFfhACfS/Woy+5ghFXxKnXIkC3ixcIQ=" },
	{ "cardholder_safe_key", "4RvY8qiRbGUpAM9LyM74K6B5DGcSsSzENr2abHcfD6g=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 37 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "developer" },
	{ "phone_number", "vIYpiMdWqGSdIH" },
	{ "next_rotation_on", "1995-12-05T13:21:13.451Z" }
};

CardSavrResponse<User> user = await cardholder.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":5294451,\"username\":\"jsmith123\",\"password\":\"Pa$$w0rd\",\"next_password\":\"JmwMmnKCotJ+RFfhACfS/Woy+5ghFXxKnXIkC3ixcIQ=\",\"cardholder_safe_key\":\"4RvY8qiRbGUpAM9LyM74K6B5DGcSsSzENr2abHcfD6g=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":37,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"developer\",\"phone_number\":\"vIYpiMdWqGSdIH\",\"custom_data\":{\"pLSezLaYuDfD\":\"~fpNs(!fQV.(MZ)/3,\",\"HsVbNiXNQagK\":9,\"RIoAmhpUytfZ\":true},\"next_rotation_on\":\"1995-12-05T13:21:13.451Z\"}"
-X POST -H "Content-Type: application/javascript"
-H "new-cardholder-safe-key: NEWCARDHODLER_SAFE_KEY"
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
await session.updateUser({
  "financial_institution_id": 6648813,
  "password": "Pa$$w0rd",
  "next_password": "+MFo3fV2xmJM2ZWF6INadqhKleD7tv5Go54bElQejSU=",
  "cardholder_safe_key": "4CfEt4vhefhAHGbVVMe23e/gYEpwH6TrELgsEeYxR8w=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 131,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "debugger_ro",
  "phone_number": "wMPUWzSOwbqWhU",
  "custom_data": {
    "XwsuuzkWDYUX": "5TY8sHL%0_<f=q[LK>aHAU^fZ%-m",
    "sORDXEdjuQOa": 29,
    "FGSnAVgIHQSz": false
  },
  "next_rotation_on": "2002-10-27T04:16:42.954Z",
  "username": "jsmith123"
}, NEWCARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 6648813 },
	{ "password", "Pa$$w0rd" },
	{ "next_password", "+MFo3fV2xmJM2ZWF6INadqhKleD7tv5Go54bElQejSU=" },
	{ "cardholder_safe_key", "4CfEt4vhefhAHGbVVMe23e/gYEpwH6TrELgsEeYxR8w=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 131 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "debugger_ro" },
	{ "phone_number", "wMPUWzSOwbqWhU" },
	{ "next_rotation_on", "2002-10-27T04:16:42.954Z" },
	{ "username", "jsmith123" }
};

CardSavrResponse<User> user = await cardholder.UpdateUserAsync(body, NEWCARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":6648813,\"password\":\"Pa$$w0rd\",\"next_password\":\"+MFo3fV2xmJM2ZWF6INadqhKleD7tv5Go54bElQejSU=\",\"cardholder_safe_key\":\"4CfEt4vhefhAHGbVVMe23e/gYEpwH6TrELgsEeYxR8w=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":131,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"debugger_ro\",\"phone_number\":\"wMPUWzSOwbqWhU\",\"custom_data\":{\"XwsuuzkWDYUX\":\"5TY8sHL%0_<f=q[LK>aHAU^fZ%-m\",\"sORDXEdjuQOa\":29,\"FGSnAVgIHQSz\":false},\"next_rotation_on\":\"2002-10-27T04:16:42.954Z\",\"username\":\"jsmith123\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "new-cardholder-safe-key: NEWCARDHODLER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/7182434
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/7182434
```

```javascript
await session.deleteUser(7182434);
```

```csharp
CardSavrResponse<User> user = await cardholder.DeleteUserAsync(7182434);
```

### Path

DELETE /cardsavr_users/{id}

### Description

Delete a user and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Financial Institutions
A CardSavr Financial Institution that can be associated with jobs and users.
## Get financial institution

```shell
curl -H "Content-Type: application/javascript
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/703692
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 703692,
  "name": "kOmDebJVHRIXBMUBephEsnRYrDifjyfFvBnkNfuIBjSlUpAwQUjzDAyBMqGnmLE",
  "description": "mcTelJiwElPUJcNbrJ",
  "lookup_key": "bnlmExYZCXwhYRvsDrpcCgDrGwpjnwOYSEUfsEWgUkpzhzpZybzKBXTTVTBtGxZ",
  "alternate_lookup_key": "CuYPpQlNTSCZdAfXsrvYEaRjimCPUWKUvanKkwQbeWhLHnczfRHOwpBMuYGOnnz",
  "created_on": "2015-03-05T22:07:51.442Z",
  "last_updated_on": "1975-11-28T19:13:08.348Z"
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
await session.createFinancial Institution({
  "name": "kOmDebJVHRIXBMUBephEsnRYrDifjyfFvBnkNfuIBjSlUpAwQUjzDAyBMqGnmLE",
  "description": "mcTelJiwElPUJcNbrJ",
  "lookup_key": "bnlmExYZCXwhYRvsDrpcCgDrGwpjnwOYSEUfsEWgUkpzhzpZybzKBXTTVTBtGxZ",
  "alternate_lookup_key": "CuYPpQlNTSCZdAfXsrvYEaRjimCPUWKUvanKkwQbeWhLHnczfRHOwpBMuYGOnnz"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "kOmDebJVHRIXBMUBephEsnRYrDifjyfFvBnkNfuIBjSlUpAwQUjzDAyBMqGnmLE" },
	{ "description", "mcTelJiwElPUJcNbrJ" },
	{ "lookup_key", "bnlmExYZCXwhYRvsDrpcCgDrGwpjnwOYSEUfsEWgUkpzhzpZybzKBXTTVTBtGxZ" },
	{ "alternate_lookup_key", "CuYPpQlNTSCZdAfXsrvYEaRjimCPUWKUvanKkwQbeWhLHnczfRHOwpBMuYGOnnz" }
};

CardSavrResponse<Financial Institution> financial institution = await cardholder.CreateFinancial InstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"kOmDebJVHRIXBMUBephEsnRYrDifjyfFvBnkNfuIBjSlUpAwQUjzDAyBMqGnmLE\",\"description\":\"mcTelJiwElPUJcNbrJ\",\"lookup_key\":\"bnlmExYZCXwhYRvsDrpcCgDrGwpjnwOYSEUfsEWgUkpzhzpZybzKBXTTVTBtGxZ\",\"alternate_lookup_key\":\"CuYPpQlNTSCZdAfXsrvYEaRjimCPUWKUvanKkwQbeWhLHnczfRHOwpBMuYGOnnz\"}"
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
await session.updateFinancial Institution({
  "name": "tOpPNJNVHsMWJfDkfJWFlWWcATzcUyidkqrFXyfXsvDJxpLesjumbdhGqusxmMk",
  "description": "SQEKHwNSNMKqQXZwmHaxkNn",
  "lookup_key": "piQuXFlRDTNrlAtHfYSGCEMVjLpgGRmIqYgPELejWaQqXLYGNvXXoRQRJcPECSN",
  "alternate_lookup_key": "eHqbOeOdhhLYVzfSNOSIeloSSCbjqQudbIKpxsYEEwrkPKNxphQmmzYrMTLtrNN"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "tOpPNJNVHsMWJfDkfJWFlWWcATzcUyidkqrFXyfXsvDJxpLesjumbdhGqusxmMk" },
	{ "description", "SQEKHwNSNMKqQXZwmHaxkNn" },
	{ "lookup_key", "piQuXFlRDTNrlAtHfYSGCEMVjLpgGRmIqYgPELejWaQqXLYGNvXXoRQRJcPECSN" },
	{ "alternate_lookup_key", "eHqbOeOdhhLYVzfSNOSIeloSSCbjqQudbIKpxsYEEwrkPKNxphQmmzYrMTLtrNN" }
};

CardSavrResponse<Financial Institution> financial institution = await cardholder.UpdateFinancial InstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"tOpPNJNVHsMWJfDkfJWFlWWcATzcUyidkqrFXyfXsvDJxpLesjumbdhGqusxmMk\",\"description\":\"SQEKHwNSNMKqQXZwmHaxkNn\",\"lookup_key\":\"piQuXFlRDTNrlAtHfYSGCEMVjLpgGRmIqYgPELejWaQqXLYGNvXXoRQRJcPECSN\",\"alternate_lookup_key\":\"eHqbOeOdhhLYVzfSNOSIeloSSCbjqQudbIKpxsYEEwrkPKNxphQmmzYrMTLtrNN\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/703692
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
https://api.INSTANCE.cardsavr.io/financial_institutions/703692
```

```javascript
await session.deleteFinancial Institution(703692);
```

```csharp
CardSavrResponse<Financial Institution> financial institution = await cardholder.DeleteFinancial InstitutionAsync(703692);
```

### Path

DELETE /financial_institutions/{id}

### Description

Delete a financial institution and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Integrators
An integrator object represents an integrator that implements CardSavr.
## Get integrator

```shell
curl -H "Content-Type: application/javascript
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/3239585
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 3239585,
  "name": "cGPtCvympnkcvOlQHHhofdicOmfNdaHDvkXTePgXskpPBydRm",
  "integrator_type": "cust_internal",
  "description": "kRcDmvn",
  "last_key": "8J9bjYuYejoDXKkirZSAKVXROMQ49EMevW4tC/BP2dU=",
  "current_key": "G0VyUzJtV43vNFctjEwmicsZF0PduP3QrPM+pRz6Kwc=",
  "next_key": "luDOPtMNACgq5seHlj3Nqjq5iSbmMhSqNyWtq4//OeA=",
  "key_lifetime": 151,
  "next_rotation_on": "1992-11-12T08:48:45.337Z",
  "created_on": "2011-04-07T01:40:41.835Z",
  "last_updated_on": "2012-01-02T05:28:25.845Z"
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
await session.createIntegrator({
  "name": "cGPtCvympnkcvOlQHHhofdicOmfNdaHDvkXTePgXskpPBydRm",
  "integrator_type": "cust_internal",
  "description": "kRcDmvn",
  "last_key": "8J9bjYuYejoDXKkirZSAKVXROMQ49EMevW4tC/BP2dU=",
  "current_key": "G0VyUzJtV43vNFctjEwmicsZF0PduP3QrPM+pRz6Kwc=",
  "next_key": "luDOPtMNACgq5seHlj3Nqjq5iSbmMhSqNyWtq4//OeA=",
  "key_lifetime": 151,
  "next_rotation_on": "1992-11-12T08:48:45.337Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "cGPtCvympnkcvOlQHHhofdicOmfNdaHDvkXTePgXskpPBydRm" },
	{ "integrator_type", "cust_internal" },
	{ "description", "kRcDmvn" },
	{ "last_key", "8J9bjYuYejoDXKkirZSAKVXROMQ49EMevW4tC/BP2dU=" },
	{ "current_key", "G0VyUzJtV43vNFctjEwmicsZF0PduP3QrPM+pRz6Kwc=" },
	{ "next_key", "luDOPtMNACgq5seHlj3Nqjq5iSbmMhSqNyWtq4//OeA=" },
	{ "key_lifetime", 151 },
	{ "next_rotation_on", "1992-11-12T08:48:45.337Z" }
};

CardSavrResponse<Integrator> integrator = await cardholder.CreateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"cGPtCvympnkcvOlQHHhofdicOmfNdaHDvkXTePgXskpPBydRm\",\"integrator_type\":\"cust_internal\",\"description\":\"kRcDmvn\",\"last_key\":\"8J9bjYuYejoDXKkirZSAKVXROMQ49EMevW4tC/BP2dU=\",\"current_key\":\"G0VyUzJtV43vNFctjEwmicsZF0PduP3QrPM+pRz6Kwc=\",\"next_key\":\"luDOPtMNACgq5seHlj3Nqjq5iSbmMhSqNyWtq4//OeA=\",\"key_lifetime\":151,\"next_rotation_on\":\"1992-11-12T08:48:45.337Z\"}"
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
await session.updateIntegrator({
  "name": "hmILdrNEudaphVLBuWQHHQOChkGWEczRmLHGsXNXCvcduGOkL",
  "integrator_type": "cust_internal",
  "description": "E",
  "last_key": "j/Oqnq8hC7Y9pXwsTk21NPGYHRR4YHVchNU2zgWlUbA=",
  "current_key": "S075aMI+XmXVdorAyFp4+9GAvjSrBKeEvi2YwVd8smo=",
  "next_key": "WeAIgqVwRG81hrGzhTWdHo6OcO9Hr+qtNK05mbx/R7s=",
  "key_lifetime": 109,
  "next_rotation_on": "1998-05-07T12:31:19.488Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "hmILdrNEudaphVLBuWQHHQOChkGWEczRmLHGsXNXCvcduGOkL" },
	{ "integrator_type", "cust_internal" },
	{ "description", "E" },
	{ "last_key", "j/Oqnq8hC7Y9pXwsTk21NPGYHRR4YHVchNU2zgWlUbA=" },
	{ "current_key", "S075aMI+XmXVdorAyFp4+9GAvjSrBKeEvi2YwVd8smo=" },
	{ "next_key", "WeAIgqVwRG81hrGzhTWdHo6OcO9Hr+qtNK05mbx/R7s=" },
	{ "key_lifetime", 109 },
	{ "next_rotation_on", "1998-05-07T12:31:19.488Z" }
};

CardSavrResponse<Integrator> integrator = await cardholder.UpdateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"hmILdrNEudaphVLBuWQHHQOChkGWEczRmLHGsXNXCvcduGOkL\",\"integrator_type\":\"cust_internal\",\"description\":\"E\",\"last_key\":\"j/Oqnq8hC7Y9pXwsTk21NPGYHRR4YHVchNU2zgWlUbA=\",\"current_key\":\"S075aMI+XmXVdorAyFp4+9GAvjSrBKeEvi2YwVd8smo=\",\"next_key\":\"WeAIgqVwRG81hrGzhTWdHo6OcO9Hr+qtNK05mbx/R7s=\",\"key_lifetime\":109,\"next_rotation_on\":\"1998-05-07T12:31:19.488Z\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/3239585
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
https://api.INSTANCE.cardsavr.io/integrators/3239585
```

```javascript
await session.deleteIntegrator(3239585);
```

```csharp
CardSavrResponse<Integrator> integrator = await cardholder.DeleteIntegratorAsync(3239585);
```

### Path

DELETE /integrators/{id}

### Description

Delete a integrator and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Merchant Sites
Merchant site objects contain information about CardSavr-supported merchant sites.
## Get merchant site

```shell
curl -H "Content-Type: application/javascript
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/merchant_sites/4159591
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 4159591,
  "name": "DqTzitVSPGAKK",
  "host": "FDiqLZvUKTPwsuKnQEskwNtIaWusP",
  "image_lookup_key": "SujELJTcH",
  "images": [
    {
      "BwwLtoasQJzk": "mYZ9wAFHG~i$y&I8M7HzUR",
      "sqgPBLoePkzy": 18,
      "TndoiMmEGSef": true
    },
    {
      "jpYvgPmDpghU": "ZszvMJ3N7.N(HV1hmKrfZeTRh",
      "CyIjDBZnXqqs": 21,
      "EnYRJNBQFZhe": false
    },
    {
      "HafzFmZidlzO": "^tFN%3N*J-tZ<gKNl",
      "XmXjGTJKAgDu": 30,
      "UQoVQIPZsJDy": false
    }
  ],
  "mfa": true,
  "tags": "noypOjHxFrsSQyAcmxubf",
  "login": {
    "uuUcakAZqEdK": "0/<Fq*tKlheiI/w6(D_1",
    "vCGCSsnSfGjB": 68,
    "WrBQpyLwIBYZ": false
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
curl -H "Content-Type: application/javascript
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/1343144
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1343144,
  "name": "ElqKvlQaAfXnfswtxnnroMHNIkrMeyCcNKZlSXyUFvOZsMuMJDbWZogxpBuHrLB",
  "type": "webhook",
  "config": {
    "uCwbIOoqqRDr": "4[gzb~fe=+daf(kk2yRPWz^w",
    "nabTPCxJDAvV": 99,
    "TNTolnsmdFDV": false
  },
  "created_on": "2001-08-15T08:40:50.921Z",
  "last_updated_on": "1991-09-03T08:52:43.292Z",
  "financial_institution_id": 9655296
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
await session.createNotification({
  "financial_institution_id": 9655296,
  "name": "ElqKvlQaAfXnfswtxnnroMHNIkrMeyCcNKZlSXyUFvOZsMuMJDbWZogxpBuHrLB",
  "type": "webhook",
  "config": {
    "uCwbIOoqqRDr": "4[gzb~fe=+daf(kk2yRPWz^w",
    "nabTPCxJDAvV": 99,
    "TNTolnsmdFDV": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 9655296 },
	{ "name", "ElqKvlQaAfXnfswtxnnroMHNIkrMeyCcNKZlSXyUFvOZsMuMJDbWZogxpBuHrLB" },
	{ "type", "webhook" }
};

CardSavrResponse<Notification> notification = await cardholder.CreateNotificationAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":9655296,\"name\":\"ElqKvlQaAfXnfswtxnnroMHNIkrMeyCcNKZlSXyUFvOZsMuMJDbWZogxpBuHrLB\",\"type\":\"webhook\",\"config\":{\"uCwbIOoqqRDr\":\"4[gzb~fe=+daf(kk2yRPWz^w\",\"nabTPCxJDAvV\":99,\"TNTolnsmdFDV\":false}}"
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
await session.updateNotification({
  "name": "MNDcyrJffxyGZnHAliPQnLtHQeprWgqZKSnAExHNKFYvXyFofqforGQqsQthReQ",
  "type": "email",
  "config": {
    "NJRFeGiWSvZk": "8kvo#6{RW*l5w-1",
    "BNmLUDBASuOC": 10,
    "VYpGrAYVFmFQ": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "MNDcyrJffxyGZnHAliPQnLtHQeprWgqZKSnAExHNKFYvXyFofqforGQqsQthReQ" },
	{ "type", "email" }
};

CardSavrResponse<Notification> notification = await cardholder.UpdateNotificationAsync(body);
```

```shell
curl -d "{\"name\":\"MNDcyrJffxyGZnHAliPQnLtHQeprWgqZKSnAExHNKFYvXyFofqforGQqsQthReQ\",\"type\":\"email\",\"config\":{\"NJRFeGiWSvZk\":\"8kvo#6{RW*l5w-1\",\"BNmLUDBASuOC\":10,\"VYpGrAYVFmFQ\":true}}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/1343144
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
https://api.INSTANCE.cardsavr.io/notifications/1343144
```

```javascript
await session.deleteNotification(1343144);
```

```csharp
CardSavrResponse<Notification> notification = await cardholder.DeleteNotificationAsync(1343144);
```

### Path

DELETE /notifications/{id}

### Description

Delete a notification and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Single-site jobs
A place_card_on_single_site_job object
## Get single-site job

```shell
curl -H "Content-Type: application/javascript
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/407474
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 407474,
  "card_placement_result_id": "IDjQwlXYJgFZswjLQSgPaWDkhSxoE",
  "status": "ABANDONED",
  "safe_blob": "LrzAzCtvyYwOqprbDRufJNq",
  "safe_nonce": "VNKuHyuGzHaOofMGXhZcVwhh",
  "custom_data": {
    "rbKPGChWYtMb": "N>GIA1o(TDmNhcfLn%8#RV",
    "cpAHlVTfuurp": 88,
    "yKhWpYcNqtbd": false
  },
  "failure_reason": "JgYmgGEFWnVHMJClEdlRQVUJS",
  "messaging_addresses": "wpdwKmVLjxjKHQhcgCQOxpyfsF",
  "current_state": "xPQGembxMkfmfRaWUbevBJMCiYuimYCHkZDmojDRXGKnPSDhhkqfLrOgldcGxeo",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 9708232,
  "job_ready_on": "1986-01-13T00:49:48.389Z",
  "started_on": "1996-06-18T07:37:57.652Z",
  "completed_on": "2009-04-04T18:55:24.541Z",
  "expiration_date": "2003-04-25T19:53:36.859Z",
  "created_on": "1998-04-10T02:19:46.607Z",
  "last_updated_on": "2011-12-18T17:27:54.002Z",
  "place_card_on_multiple_sites_job_id": 7154954,
  "user_id": 5784509,
  "card_id": 3381191,
  "account_id": 9576178
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
await session.createSingleSiteJob({
  "place_card_on_multiple_sites_job_id": 7154954,
  "user_id": 5784509,
  "card_id": 3381191,
  "account_id": 9576178,
  "status": "ABANDONED",
  "custom_data": {
    "rbKPGChWYtMb": "N>GIA1o(TDmNhcfLn%8#RV",
    "cpAHlVTfuurp": 88,
    "yKhWpYcNqtbd": false
  },
  "failure_reason": "JgYmgGEFWnVHMJClEdlRQVUJS",
  "current_state": "xPQGembxMkfmfRaWUbevBJMCiYuimYCHkZDmojDRXGKnPSDhhkqfLrOgldcGxeo",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 9708232,
  "started_on": "1996-06-18T07:37:57.652Z",
  "completed_on": "2009-04-04T18:55:24.541Z",
  "expiration_date": "2003-04-25T19:53:36.859Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "place_card_on_multiple_sites_job_id", 7154954 },
	{ "user_id", 5784509 },
	{ "card_id", 3381191 },
	{ "account_id", 9576178 },
	{ "status", "ABANDONED" },
	{ "failure_reason", "JgYmgGEFWnVHMJClEdlRQVUJS" },
	{ "current_state", "xPQGembxMkfmfRaWUbevBJMCiYuimYCHkZDmojDRXGKnPSDhhkqfLrOgldcGxeo" },
	{ "do_not_queue", true },
	{ "user_is_present", false },
	{ "time_elapsed", 9708232 },
	{ "started_on", "1996-06-18T07:37:57.652Z" },
	{ "completed_on", "2009-04-04T18:55:24.541Z" },
	{ "expiration_date", "2003-04-25T19:53:36.859Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await cardholder.CreateSingleSiteJobAsync(body);
```

```shell
curl -d "{\"place_card_on_multiple_sites_job_id\":7154954,\"user_id\":5784509,\"card_id\":3381191,\"account_id\":9576178,\"status\":\"ABANDONED\",\"custom_data\":{\"rbKPGChWYtMb\":\"N>GIA1o(TDmNhcfLn%8#RV\",\"cpAHlVTfuurp\":88,\"yKhWpYcNqtbd\":false},\"failure_reason\":\"JgYmgGEFWnVHMJClEdlRQVUJS\",\"current_state\":\"xPQGembxMkfmfRaWUbevBJMCiYuimYCHkZDmojDRXGKnPSDhhkqfLrOgldcGxeo\",\"do_not_queue\":true,\"user_is_present\":false,\"time_elapsed\":9708232,\"started_on\":\"1996-06-18T07:37:57.652Z\",\"completed_on\":\"2009-04-04T18:55:24.541Z\",\"expiration_date\":\"2003-04-25T19:53:36.859Z\"}"
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
await session.updateSingleSiteJob({
  "status": "DUPLICATE_CARD",
  "custom_data": {
    "ScHCwvldTQNO": "&Y]R[",
    "CdHoKRHTvZrL": 57,
    "DvcjUoqRiUFH": true
  },
  "failure_reason": "dPxKofN",
  "current_state": "tYoBjfRnZfEnhKumgyKXNLanbtDudbeDqpJMyoKWgIxYGHBiUuZDqjwGWOQlkWM",
  "do_not_queue": false,
  "user_is_present": true,
  "time_elapsed": 2575669,
  "started_on": "1985-07-29T03:38:19.398Z",
  "completed_on": "1993-10-28T08:36:00.460Z",
  "expiration_date": "1990-07-11T06:27:00.231Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "status", "DUPLICATE_CARD" },
	{ "failure_reason", "dPxKofN" },
	{ "current_state", "tYoBjfRnZfEnhKumgyKXNLanbtDudbeDqpJMyoKWgIxYGHBiUuZDqjwGWOQlkWM" },
	{ "do_not_queue", false },
	{ "user_is_present", true },
	{ "time_elapsed", 2575669 },
	{ "started_on", "1985-07-29T03:38:19.398Z" },
	{ "completed_on", "1993-10-28T08:36:00.460Z" },
	{ "expiration_date", "1990-07-11T06:27:00.231Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await cardholder.UpdateSingleSiteJobAsync(body);
```

```shell
curl -d "{\"status\":\"DUPLICATE_CARD\",\"custom_data\":{\"ScHCwvldTQNO\":\"&Y]R[\",\"CdHoKRHTvZrL\":57,\"DvcjUoqRiUFH\":true},\"failure_reason\":\"dPxKofN\",\"current_state\":\"tYoBjfRnZfEnhKumgyKXNLanbtDudbeDqpJMyoKWgIxYGHBiUuZDqjwGWOQlkWM\",\"do_not_queue\":false,\"user_is_present\":true,\"time_elapsed\":2575669,\"started_on\":\"1985-07-29T03:38:19.398Z\",\"completed_on\":\"1993-10-28T08:36:00.460Z\",\"expiration_date\":\"1990-07-11T06:27:00.231Z\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/407474
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/407474
```

```javascript
await session.deleteSingleSiteJob(407474);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await cardholder.DeleteSingleSiteJobAsync(407474);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

