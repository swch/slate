# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

```shell
curl -H "Content-Type: application/javascript
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/6491809
```

```javascript
const account = await session.getAccount(6491809, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Account> account = await session.GetAccountAsync(6491809, CARDHOLDER_SAFE_KEY);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 6491809,
  "last_card_placed_id": 6541720,
  "username": "jsmith123",
  "password": "Pa$$w0rd",
  "last_login": "2011-08-25T02:12:40.103Z",
  "last_password_update": "1989-12-07T19:48:56.614Z",
  "last_saved_card": "2011-08-16T17:44:24.077Z",
  "created_on": "2017-04-25T05:29:15.797Z",
  "last_updated_on": "1972-12-03T12:58:37.416Z",
  "cardholder_id": 1850876,
  "merchant_site_id": 506073
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
  "cardholder_id": 1850876,
  "merchant_site_id": 506073,
  "last_card_placed_id": 6541720,
  "username": "jsmith123",
  "password": "Pa$$w0rd"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1850876 },
	{ "merchant_site_id", 506073 },
	{ "last_card_placed_id", 6541720 },
	{ "username", "jsmith123" },
	{ "password", "Pa$$w0rd" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":1850876,\"merchant_site_id\":506073,\"last_card_placed_id\":6541720,\"username\":\"jsmith123\",\"password\":\"Pa$$w0rd\"}"
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
  "last_card_placed_id": 8402136,
  "username": "jsmith123",
  "password": "Pa$$w0rd"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 8402136 },
	{ "username", "jsmith123" },
	{ "password", "Pa$$w0rd" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"last_card_placed_id\":8402136,\"username\":\"jsmith123\",\"password\":\"Pa$$w0rd\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/6491809
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
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/6491809
```

```javascript
await session.deleteAccount(6491809, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(6491809, CARDHOLDER_SAFE_KEY);
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
curl -H "Content-Type: application/javascript
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/2253825
```

```javascript
const address = await session.getAddress(2253825);
```

```csharp
CardSavrResponse<Address> address = await session.GetAddressAsync(2253825);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2253825,
  "address1": "zAjEWAJkgcpHWgzqYBOBXVRytiULbHMsHYfCFsjvgneiYdkXGldJjTowEAbkxGUViZkxiAbaxTKbiIJCumzOYqQaxHqtpjWeMSo",
  "address2": "jmXAHEDqXHNZeTOUXxXtClfjyeZuHMxOQuzgiRiyUVysqEbNvbUEUZISkIsYIoMzGbDNaSGlkybWGFXsFlJcKFiHmnMoZiNWehq",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "created_on": "2009-01-30T07:54:42.579Z",
  "last_updated_on": "1974-01-10T03:23:59.112Z",
  "user_id": 7237203
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
  "user_id": 7237203,
  "address1": "zAjEWAJkgcpHWgzqYBOBXVRytiULbHMsHYfCFsjvgneiYdkXGldJjTowEAbkxGUViZkxiAbaxTKbiIJCumzOYqQaxHqtpjWeMSo",
  "address2": "jmXAHEDqXHNZeTOUXxXtClfjyeZuHMxOQuzgiRiyUVysqEbNvbUEUZISkIsYIoMzGbDNaSGlkybWGFXsFlJcKFiHmnMoZiNWehq",
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
	{ "user_id", 7237203 },
	{ "address1", "zAjEWAJkgcpHWgzqYBOBXVRytiULbHMsHYfCFsjvgneiYdkXGldJjTowEAbkxGUViZkxiAbaxTKbiIJCumzOYqQaxHqtpjWeMSo" },
	{ "address2", "jmXAHEDqXHNZeTOUXxXtClfjyeZuHMxOQuzgiRiyUVysqEbNvbUEUZISkIsYIoMzGbDNaSGlkybWGFXsFlJcKFiHmnMoZiNWehq" },
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
curl -d "{\"user_id\":7237203,\"address1\":\"zAjEWAJkgcpHWgzqYBOBXVRytiULbHMsHYfCFsjvgneiYdkXGldJjTowEAbkxGUViZkxiAbaxTKbiIJCumzOYqQaxHqtpjWeMSo\",\"address2\":\"jmXAHEDqXHNZeTOUXxXtClfjyeZuHMxOQuzgiRiyUVysqEbNvbUEUZISkIsYIoMzGbDNaSGlkybWGFXsFlJcKFiHmnMoZiNWehq\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true}"
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
  "address1": "zBddiqVeJaTTFRKlflOUIuTjloQELVguwWzzYlWwZMkUGwMXjuPffQwjFVknAxoNhnJitjaJFyLnHcAxHJEonOJcLZsfPeaygCv",
  "address2": "cbLelpGODXoujUYRJNhjIPcuUtHEqNBzQeMMXOWhcWvujzpNlmPvppjGKSBubZKEVHtHwqCalpZwwBVmUdtnwqDyKPsReAARkTv",
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
	{ "address1", "zBddiqVeJaTTFRKlflOUIuTjloQELVguwWzzYlWwZMkUGwMXjuPffQwjFVknAxoNhnJitjaJFyLnHcAxHJEonOJcLZsfPeaygCv" },
	{ "address2", "cbLelpGODXoujUYRJNhjIPcuUtHEqNBzQeMMXOWhcWvujzpNlmPvppjGKSBubZKEVHtHwqCalpZwwBVmUdtnwqDyKPsReAARkTv" },
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
curl -d "{\"address1\":\"zBddiqVeJaTTFRKlflOUIuTjloQELVguwWzzYlWwZMkUGwMXjuPffQwjFVknAxoNhnJitjaJFyLnHcAxHJEonOJcLZsfPeaygCv\",\"address2\":\"cbLelpGODXoujUYRJNhjIPcuUtHEqNBzQeMMXOWhcWvujzpNlmPvppjGKSBubZKEVHtHwqCalpZwwBVmUdtnwqDyKPsReAARkTv\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/2253825
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/2253825
```

```javascript
await session.deleteAddress(2253825);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(2253825);
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/6986475
```

```javascript
const bin = await session.getBin(6986475);
```

```csharp
CardSavrResponse<Bin> bin = await session.GetBinAsync(6986475);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 6986475,
  "financial_institution_id": 6919875,
  "brand": "EflLjmILFFYpwKhaNZD",
  "issuer": "znvPNlrwJwvZHJjTjwLkvPkzPUFGXOesfZwrImnEHTFMifGQtciMTWmgHcoBBBuWQrkKsoRwYEZllTxrPlLthiyTJdwcSJwhoyj",
  "type": "RaOctifWuVWpWv",
  "level": "beinCBNMWNAYTGgtNMFUqhlHxFOCzApujWezetaqUjVKCORADtZFsBfoGbnAIljnKPNbbDWDdDAkYaqdZnfUwdLZkNRtOjVsRyY",
  "created_on": "1986-12-23T03:45:12.206Z",
  "last_updated_on": "1979-11-10T05:04:31.295Z",
  "bank_identification_number": "19301882"
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
  "financial_institution_id": 6919875,
  "bank_identification_number": "19301882",
  "brand": "EflLjmILFFYpwKhaNZD",
  "issuer": "znvPNlrwJwvZHJjTjwLkvPkzPUFGXOesfZwrImnEHTFMifGQtciMTWmgHcoBBBuWQrkKsoRwYEZllTxrPlLthiyTJdwcSJwhoyj",
  "type": "RaOctifWuVWpWv",
  "level": "beinCBNMWNAYTGgtNMFUqhlHxFOCzApujWezetaqUjVKCORADtZFsBfoGbnAIljnKPNbbDWDdDAkYaqdZnfUwdLZkNRtOjVsRyY"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 6919875 },
	{ "bank_identification_number", "19301882" },
	{ "brand", "EflLjmILFFYpwKhaNZD" },
	{ "issuer", "znvPNlrwJwvZHJjTjwLkvPkzPUFGXOesfZwrImnEHTFMifGQtciMTWmgHcoBBBuWQrkKsoRwYEZllTxrPlLthiyTJdwcSJwhoyj" },
	{ "type", "RaOctifWuVWpWv" },
	{ "level", "beinCBNMWNAYTGgtNMFUqhlHxFOCzApujWezetaqUjVKCORADtZFsBfoGbnAIljnKPNbbDWDdDAkYaqdZnfUwdLZkNRtOjVsRyY" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":6919875,\"bank_identification_number\":\"19301882\",\"brand\":\"EflLjmILFFYpwKhaNZD\",\"issuer\":\"znvPNlrwJwvZHJjTjwLkvPkzPUFGXOesfZwrImnEHTFMifGQtciMTWmgHcoBBBuWQrkKsoRwYEZllTxrPlLthiyTJdwcSJwhoyj\",\"type\":\"RaOctifWuVWpWv\",\"level\":\"beinCBNMWNAYTGgtNMFUqhlHxFOCzApujWezetaqUjVKCORADtZFsBfoGbnAIljnKPNbbDWDdDAkYaqdZnfUwdLZkNRtOjVsRyY\"}"
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
  "financial_institution_id": 8226981,
  "brand": "cQkRgTIrdjYRGvoahUi",
  "issuer": "LbdYcrLpItkIotflAtIGcpZYHXlIDhDcgwMtqREjSoZqzboFEAcqBOpewDVyFIbOQipUEqFOApiNWNBiyxLQjkMwJUZqVTMVHzp",
  "type": "twsKOkNTIeVvta",
  "level": "YNYiyocictTQaueugjNyAgLFnnXsgNDIZCHVunqliFGCjyXwpMLQrlTfCjQSNTxaBLKHCuzXlfiSpCsXmMMgMzAQIKylkEmTwCk"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 8226981 },
	{ "brand", "cQkRgTIrdjYRGvoahUi" },
	{ "issuer", "LbdYcrLpItkIotflAtIGcpZYHXlIDhDcgwMtqREjSoZqzboFEAcqBOpewDVyFIbOQipUEqFOApiNWNBiyxLQjkMwJUZqVTMVHzp" },
	{ "type", "twsKOkNTIeVvta" },
	{ "level", "YNYiyocictTQaueugjNyAgLFnnXsgNDIZCHVunqliFGCjyXwpMLQrlTfCjQSNTxaBLKHCuzXlfiSpCsXmMMgMzAQIKylkEmTwCk" }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":8226981,\"brand\":\"cQkRgTIrdjYRGvoahUi\",\"issuer\":\"LbdYcrLpItkIotflAtIGcpZYHXlIDhDcgwMtqREjSoZqzboFEAcqBOpewDVyFIbOQipUEqFOApiNWNBiyxLQjkMwJUZqVTMVHzp\",\"type\":\"twsKOkNTIeVvta\",\"level\":\"YNYiyocictTQaueugjNyAgLFnnXsgNDIZCHVunqliFGCjyXwpMLQrlTfCjQSNTxaBLKHCuzXlfiSpCsXmMMgMzAQIKylkEmTwCk\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_bins/6986475
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/6986475
```

```javascript
await session.deleteBin(6986475);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(6986475);
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/4831347
```

```javascript
const card = await session.getCard(4831347, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Card> card = await session.GetCardAsync(4831347, CARDHOLDER_SAFE_KEY);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 4831347,
  "address_id": 5267631,
  "bin_id": 4244517,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "first_6": "qZnsaAEnwroucrCUNVVGyBMhLYlCoYPf",
  "first_7": "OEteaJUOQjnCExOZqjEvuzLbjIaPOcki",
  "first_8": "CXxZMEhhghotAoVVJHMMLWwTYANEHGtg",
  "created_on": "1980-02-29T10:52:53.909Z",
  "last_updated_on": "1980-11-01T04:46:34.751Z",
  "expiration_month": 1,
  "expiration_year": 31,
  "cardholder_id": 6185274,
  "par": "DqYeMYaAZFuhuUjqDpMlcpoFfQaHq",
  "pan": "tewGxJojsbnqBZf",
  "cvv": "pek"
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
  "cardholder_id": 6185274,
  "address_id": 5267631,
  "bin_id": 4244517,
  "par": "DqYeMYaAZFuhuUjqDpMlcpoFfQaHq",
  "pan": "tewGxJojsbnqBZf",
  "cvv": "pek",
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
	{ "cardholder_id", 6185274 },
	{ "address_id", 5267631 },
	{ "bin_id", 4244517 },
	{ "par", "DqYeMYaAZFuhuUjqDpMlcpoFfQaHq" },
	{ "pan", "tewGxJojsbnqBZf" },
	{ "cvv", "pek" },
	{ "expiration_month", 1 },
	{ "expiration_year", 31 },
	{ "name_on_card", "Joe C Smith" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" }
};

CardSavrResponse<Card> card = await http.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"cardholder_id\":6185274,\"address_id\":5267631,\"bin_id\":4244517,\"par\":\"DqYeMYaAZFuhuUjqDpMlcpoFfQaHq\",\"pan\":\"tewGxJojsbnqBZf\",\"cvv\":\"pek\",\"expiration_month\":1,\"expiration_year\":31,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\"}"
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
  "address_id": 9886531,
  "bin_id": 7620161,
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
	{ "address_id", 9886531 },
	{ "bin_id", 7620161 },
	{ "name_on_card", "Joe C Smith" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "expiration_month", 1 },
	{ "expiration_year", 31 }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"address_id\":9886531,\"bin_id\":7620161,\"name_on_card\":\"Joe C Smith\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"expiration_month\":1,\"expiration_year\":31}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_cards/4831347
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/4831347
```

```javascript
await session.deleteCard(4831347, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(4831347, CARDHOLDER_SAFE_KEY);
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
curl -H "Content-Type: application/javascript
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/9636868
```

```javascript
const user = await session.getUser(9636868, CARDHOLDER_SAFE_KEY);
```

```csharp
CardSavrResponse<User> user = await session.GetUserAsync(9636868, CARDHOLDER_SAFE_KEY);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 9636868,
  "financial_institution_id": 4976990,
  "last_password": "BNDjClnw6B6p2AuKLgnQ1fnm2UrgfqGEUy66bLIMYcc=",
  "password": "Pa$$w0rd",
  "next_password": "rS0vIftWkEXc/R5P1NdR7EnBM0JKfUajbDaOBxcXZDw=",
  "expired_password_1": "tABlmuMJNfFOKFFhEi+zY3KHmDW+knNg9TO85zFYiEQ=",
  "expired_password_2": "gL+JqDjZaYjyP8CkfE9awNcc6vglSUv2B/9Bnx90/Dk=",
  "cardholder_safe_key": "8gm79ZU46SgKwjPaKrQ8TVjJh1slllsDL/ybRMbO1x4=",
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "2013-11-29T09:53:25.348Z",
  "is_locked": true,
  "password_lifetime": 364,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "developer",
  "phone_number": "eNWxnDWakWAGGL",
  "custom_data": {
    "yZYlSfjRttmp": "yTun=X%vHx]7BD_mdlL",
    "qDYWdmptkZzV": 0,
    "RqElOkScaMMK": true
  },
  "next_rotation_on": "2001-01-29T15:48:50.634Z",
  "created_on": "1979-07-07T05:35:14.728Z",
  "last_updated_on": "1992-07-23T01:04:44.019Z",
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
  "financial_institution_id": 4976990,
  "username": "jsmith123",
  "password": "Pa$$w0rd",
  "next_password": "rS0vIftWkEXc/R5P1NdR7EnBM0JKfUajbDaOBxcXZDw=",
  "cardholder_safe_key": "8gm79ZU46SgKwjPaKrQ8TVjJh1slllsDL/ybRMbO1x4=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 364,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "developer",
  "phone_number": "eNWxnDWakWAGGL",
  "custom_data": {
    "yZYlSfjRttmp": "yTun=X%vHx]7BD_mdlL",
    "qDYWdmptkZzV": 0,
    "RqElOkScaMMK": true
  },
  "next_rotation_on": "2001-01-29T15:48:50.634Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 4976990 },
	{ "username", "jsmith123" },
	{ "password", "Pa$$w0rd" },
	{ "next_password", "rS0vIftWkEXc/R5P1NdR7EnBM0JKfUajbDaOBxcXZDw=" },
	{ "cardholder_safe_key", "8gm79ZU46SgKwjPaKrQ8TVjJh1slllsDL/ybRMbO1x4=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 364 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "developer" },
	{ "phone_number", "eNWxnDWakWAGGL" },
	{ "next_rotation_on", "2001-01-29T15:48:50.634Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":4976990,\"username\":\"jsmith123\",\"password\":\"Pa$$w0rd\",\"next_password\":\"rS0vIftWkEXc/R5P1NdR7EnBM0JKfUajbDaOBxcXZDw=\",\"cardholder_safe_key\":\"8gm79ZU46SgKwjPaKrQ8TVjJh1slllsDL/ybRMbO1x4=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":364,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"developer\",\"phone_number\":\"eNWxnDWakWAGGL\",\"custom_data\":{\"yZYlSfjRttmp\":\"yTun=X%vHx]7BD_mdlL\",\"qDYWdmptkZzV\":0,\"RqElOkScaMMK\":true},\"next_rotation_on\":\"2001-01-29T15:48:50.634Z\"}"
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
  "financial_institution_id": 5970667,
  "password": "Pa$$w0rd",
  "next_password": "5cZ0nZy5LfCWjsP0BAhHwP3oCb4rAa1Rdv2bmWdNTLc=",
  "cardholder_safe_key": "3nkpZpyTaPCYdXLlXD7uCe9TUtP2SqHBgnuELxsK7GA=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 276,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "cardholder",
  "phone_number": "RCGeScYOvXfPSf",
  "custom_data": {
    "JFlqIbPLPIJF": "~.a9M~.-uC~-qqx7Ese",
    "suwqIZWmckwK": 100,
    "JYhQYJNmKUwm": false
  },
  "next_rotation_on": "2003-02-12T14:40:08.449Z",
  "username": "jsmith123"
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 5970667 },
	{ "password", "Pa$$w0rd" },
	{ "next_password", "5cZ0nZy5LfCWjsP0BAhHwP3oCb4rAa1Rdv2bmWdNTLc=" },
	{ "cardholder_safe_key", "3nkpZpyTaPCYdXLlXD7uCe9TUtP2SqHBgnuELxsK7GA=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 276 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "cardholder" },
	{ "phone_number", "RCGeScYOvXfPSf" },
	{ "next_rotation_on", "2003-02-12T14:40:08.449Z" },
	{ "username", "jsmith123" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```shell
curl -d "{\"financial_institution_id\":5970667,\"password\":\"Pa$$w0rd\",\"next_password\":\"5cZ0nZy5LfCWjsP0BAhHwP3oCb4rAa1Rdv2bmWdNTLc=\",\"cardholder_safe_key\":\"3nkpZpyTaPCYdXLlXD7uCe9TUtP2SqHBgnuELxsK7GA=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":276,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"cardholder\",\"phone_number\":\"RCGeScYOvXfPSf\",\"custom_data\":{\"JFlqIbPLPIJF\":\"~.a9M~.-uC~-qqx7Ese\",\"suwqIZWmckwK\":100,\"JYhQYJNmKUwm\":false},\"next_rotation_on\":\"2003-02-12T14:40:08.449Z\",\"username\":\"jsmith123\"}"
-X PUT -H "Content-Type: application/javascript"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/cardsavr_users/9636868
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/9636868
```

```javascript
await session.deleteUser(9636868);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(9636868);
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
https://api.INSTANCE.cardsavr.io/financial_institutions/2790463
```

```javascript
const financial institution = await session.getFinancial Institution(2790463);
```

```csharp
CardSavrResponse<Financial Institution> financial institution = await session.GetFinancial InstitutionAsync(2790463);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2790463,
  "name": "mMxymoLVanpxXRfHJuzoyYdFnBGxckTPoNRiteXBqFRHBlNSNIoYPoRpcQkquem",
  "description": "NgythYbMTPPTDzFelNbmazrYuWXn",
  "lookup_key": "abEWjPeKTHWZZwagyqSCSKhqBdXYoLgXaNPHNyGZMlJJUkzBxKnCmzyUqnSdtxP",
  "alternate_lookup_key": "QymSFOgEJYSdEXQpzIOJwHQPiDtDmmvXBEsOhTlwhmJqDPkTFIOuJkuFxqDzvnH",
  "created_on": "2004-09-17T21:08:00.217Z",
  "last_updated_on": "1997-12-23T20:39:13.109Z"
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
  "name": "mMxymoLVanpxXRfHJuzoyYdFnBGxckTPoNRiteXBqFRHBlNSNIoYPoRpcQkquem",
  "description": "NgythYbMTPPTDzFelNbmazrYuWXn",
  "lookup_key": "abEWjPeKTHWZZwagyqSCSKhqBdXYoLgXaNPHNyGZMlJJUkzBxKnCmzyUqnSdtxP",
  "alternate_lookup_key": "QymSFOgEJYSdEXQpzIOJwHQPiDtDmmvXBEsOhTlwhmJqDPkTFIOuJkuFxqDzvnH"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "mMxymoLVanpxXRfHJuzoyYdFnBGxckTPoNRiteXBqFRHBlNSNIoYPoRpcQkquem" },
	{ "description", "NgythYbMTPPTDzFelNbmazrYuWXn" },
	{ "lookup_key", "abEWjPeKTHWZZwagyqSCSKhqBdXYoLgXaNPHNyGZMlJJUkzBxKnCmzyUqnSdtxP" },
	{ "alternate_lookup_key", "QymSFOgEJYSdEXQpzIOJwHQPiDtDmmvXBEsOhTlwhmJqDPkTFIOuJkuFxqDzvnH" }
};

CardSavrResponse<Financial Institution> financial institution = await http.CreateFinancial InstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"mMxymoLVanpxXRfHJuzoyYdFnBGxckTPoNRiteXBqFRHBlNSNIoYPoRpcQkquem\",\"description\":\"NgythYbMTPPTDzFelNbmazrYuWXn\",\"lookup_key\":\"abEWjPeKTHWZZwagyqSCSKhqBdXYoLgXaNPHNyGZMlJJUkzBxKnCmzyUqnSdtxP\",\"alternate_lookup_key\":\"QymSFOgEJYSdEXQpzIOJwHQPiDtDmmvXBEsOhTlwhmJqDPkTFIOuJkuFxqDzvnH\"}"
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
  "name": "ffJKBJNBkXnsQndLqgwchFEoEaoYTEGTccgEDUxLwoDDpyGkRbFKFlCTJQgpgMP",
  "description": "BpQDxHLPQv",
  "lookup_key": "nCWZHUBsAthlskpDBrzLGxXvPlrQDxKiahwhMMUqOiNDUKaVkTJEidqkPMoecne",
  "alternate_lookup_key": "ehAhLHloyNBkXmBKfiYldhKjnfbbRIwRVdPlWXrtaCTNLFKZDPFDpTcyvLFkMeI"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "ffJKBJNBkXnsQndLqgwchFEoEaoYTEGTccgEDUxLwoDDpyGkRbFKFlCTJQgpgMP" },
	{ "description", "BpQDxHLPQv" },
	{ "lookup_key", "nCWZHUBsAthlskpDBrzLGxXvPlrQDxKiahwhMMUqOiNDUKaVkTJEidqkPMoecne" },
	{ "alternate_lookup_key", "ehAhLHloyNBkXmBKfiYldhKjnfbbRIwRVdPlWXrtaCTNLFKZDPFDpTcyvLFkMeI" }
};

CardSavrResponse<Financial Institution> financial institution = await http.UpdateFinancial InstitutionAsync(body);
```

```shell
curl -d "{\"name\":\"ffJKBJNBkXnsQndLqgwchFEoEaoYTEGTccgEDUxLwoDDpyGkRbFKFlCTJQgpgMP\",\"description\":\"BpQDxHLPQv\",\"lookup_key\":\"nCWZHUBsAthlskpDBrzLGxXvPlrQDxKiahwhMMUqOiNDUKaVkTJEidqkPMoecne\",\"alternate_lookup_key\":\"ehAhLHloyNBkXmBKfiYldhKjnfbbRIwRVdPlWXrtaCTNLFKZDPFDpTcyvLFkMeI\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/financial_institutions/2790463
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
https://api.INSTANCE.cardsavr.io/financial_institutions/2790463
```

```javascript
await session.deleteFinancial Institution(2790463);
```

```csharp
CardSavrResponse<Financial Institution> financial institution = await http.DeleteFinancial InstitutionAsync(2790463);
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
https://api.INSTANCE.cardsavr.io/integrators/8358602
```

```javascript
const integrator = await session.getIntegrator(8358602);
```

```csharp
CardSavrResponse<Integrator> integrator = await session.GetIntegratorAsync(8358602);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 8358602,
  "name": "jYVTapXHCNMwwqurVicDVomxQmiZIeVDTYLaySRyfDhvtiVAG",
  "integrator_type": "swch_internal",
  "description": "CfVhnxUOQhjGcfdQNGce",
  "last_key": "FmJYLLvT82Wf6kmBJlCCiz72yh0QF7AkS1OePnsauNw=",
  "current_key": "TK/xNW7+llCYVoRc49CKcb/j1I0Q3DAvOPM4sWr+jZo=",
  "next_key": "C5pWoF/olqGb7U5vYZuiGBtqO+gt9doAvPHTAYO7AzE=",
  "key_lifetime": 159,
  "next_rotation_on": "2019-10-28T20:33:46.755Z",
  "created_on": "2016-04-16T08:32:49.070Z",
  "last_updated_on": "1993-06-15T22:49:22.035Z"
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
  "name": "jYVTapXHCNMwwqurVicDVomxQmiZIeVDTYLaySRyfDhvtiVAG",
  "integrator_type": "swch_internal",
  "description": "CfVhnxUOQhjGcfdQNGce",
  "last_key": "FmJYLLvT82Wf6kmBJlCCiz72yh0QF7AkS1OePnsauNw=",
  "current_key": "TK/xNW7+llCYVoRc49CKcb/j1I0Q3DAvOPM4sWr+jZo=",
  "next_key": "C5pWoF/olqGb7U5vYZuiGBtqO+gt9doAvPHTAYO7AzE=",
  "key_lifetime": 159,
  "next_rotation_on": "2019-10-28T20:33:46.755Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "jYVTapXHCNMwwqurVicDVomxQmiZIeVDTYLaySRyfDhvtiVAG" },
	{ "integrator_type", "swch_internal" },
	{ "description", "CfVhnxUOQhjGcfdQNGce" },
	{ "last_key", "FmJYLLvT82Wf6kmBJlCCiz72yh0QF7AkS1OePnsauNw=" },
	{ "current_key", "TK/xNW7+llCYVoRc49CKcb/j1I0Q3DAvOPM4sWr+jZo=" },
	{ "next_key", "C5pWoF/olqGb7U5vYZuiGBtqO+gt9doAvPHTAYO7AzE=" },
	{ "key_lifetime", 159 },
	{ "next_rotation_on", "2019-10-28T20:33:46.755Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"jYVTapXHCNMwwqurVicDVomxQmiZIeVDTYLaySRyfDhvtiVAG\",\"integrator_type\":\"swch_internal\",\"description\":\"CfVhnxUOQhjGcfdQNGce\",\"last_key\":\"FmJYLLvT82Wf6kmBJlCCiz72yh0QF7AkS1OePnsauNw=\",\"current_key\":\"TK/xNW7+llCYVoRc49CKcb/j1I0Q3DAvOPM4sWr+jZo=\",\"next_key\":\"C5pWoF/olqGb7U5vYZuiGBtqO+gt9doAvPHTAYO7AzE=\",\"key_lifetime\":159,\"next_rotation_on\":\"2019-10-28T20:33:46.755Z\"}"
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
  "name": "oYkjzxYSkJkAjCSCVPMqCnhFfcymnYafirsogFzwbBcpBKQmu",
  "integrator_type": "cust_internal",
  "description": "yWRsBWPmfilbFpIOotJnXqS",
  "last_key": "Ef6CS609S0GvPq3ARQ+BzUMmUcXd1usc5//cAM6QbHg=",
  "current_key": "1aCBt9qbbHG9XmEGIgxA2o+4Uk2pU078Y4ObHjleS3k=",
  "next_key": "Ulh3/0VQ33OpI6N+o98qji59vKqpPhsauH1ledH4Df4=",
  "key_lifetime": 21,
  "next_rotation_on": "1980-03-09T11:06:53.598Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "oYkjzxYSkJkAjCSCVPMqCnhFfcymnYafirsogFzwbBcpBKQmu" },
	{ "integrator_type", "cust_internal" },
	{ "description", "yWRsBWPmfilbFpIOotJnXqS" },
	{ "last_key", "Ef6CS609S0GvPq3ARQ+BzUMmUcXd1usc5//cAM6QbHg=" },
	{ "current_key", "1aCBt9qbbHG9XmEGIgxA2o+4Uk2pU078Y4ObHjleS3k=" },
	{ "next_key", "Ulh3/0VQ33OpI6N+o98qji59vKqpPhsauH1ledH4Df4=" },
	{ "key_lifetime", 21 },
	{ "next_rotation_on", "1980-03-09T11:06:53.598Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```shell
curl -d "{\"name\":\"oYkjzxYSkJkAjCSCVPMqCnhFfcymnYafirsogFzwbBcpBKQmu\",\"integrator_type\":\"cust_internal\",\"description\":\"yWRsBWPmfilbFpIOotJnXqS\",\"last_key\":\"Ef6CS609S0GvPq3ARQ+BzUMmUcXd1usc5//cAM6QbHg=\",\"current_key\":\"1aCBt9qbbHG9XmEGIgxA2o+4Uk2pU078Y4ObHjleS3k=\",\"next_key\":\"Ulh3/0VQ33OpI6N+o98qji59vKqpPhsauH1ledH4Df4=\",\"key_lifetime\":21,\"next_rotation_on\":\"1980-03-09T11:06:53.598Z\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/integrators/8358602
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
https://api.INSTANCE.cardsavr.io/integrators/8358602
```

```javascript
await session.deleteIntegrator(8358602);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(8358602);
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
https://api.INSTANCE.cardsavr.io/merchant_sites/6184651
```

```javascript
const merchant site = await session.getMerchant Site(6184651);
```

```csharp
CardSavrResponse<Merchant Site> merchant site = await session.GetMerchant SiteAsync(6184651);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 6184651,
  "name": "gySVDcEnRtSrggGPhdF",
  "host": "gByGaIXsAIINIlJGSnTrffaYNnF",
  "image_lookup_key": "LfGrAzrXOzMabkrfNhNOwbATj",
  "images": [
    {
      "OKSxNkyyDaMJ": "51qf20aNKqAufL1WDWjqP",
      "REwXagCboRGn": 7,
      "ivDhDZHMmBYw": false
    },
    {
      "tsDdFDgSxUgy": "%yV=s*_W}a~O#$s_af!Z/gym>o#/p1EZ",
      "FNjbxcKbONhB": 13,
      "auEIrzAzyTEe": true
    },
    {
      "vUGpzPdoiLLF": ")co4~{d>R",
      "vLzasgIFHnsO": 13,
      "ONhApAXtfdHs": true
    }
  ],
  "mfa": false,
  "tags": "TKlWgBqpRSJsbCczwVuEBerCpki",
  "login": {
    "jtYjwsYIwOHz": "4d^cckg7mofdt,8i_<cR",
    "DuetggqLDzlM": 63,
    "UKGdgPeaQGdA": true
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
https://api.INSTANCE.cardsavr.io/notifications/2670762
```

```javascript
const notification = await session.getNotification(2670762);
```

```csharp
CardSavrResponse<Notification> notification = await session.GetNotificationAsync(2670762);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2670762,
  "name": "mHQKvNptjxnQyhxCSBoKygJXszJjYBKjaEhpKZBcLpuGkfbwRHeIvAqGRWhlcbB",
  "type": "webhook",
  "event": "session_complete",
  "config": {
    "vsFUrRTTofUV": "w=06i/r~IVkO-ex@~L,8hsDNdAu18",
    "OUHfmbLYjDpd": 2,
    "WlBMMQKgddti": false
  },
  "created_on": "1993-02-28T05:32:07.381Z",
  "last_updated_on": "1987-11-23T04:02:29.751Z",
  "financial_institution_id": 2756953
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
  "financial_institution_id": 2756953,
  "name": "mHQKvNptjxnQyhxCSBoKygJXszJjYBKjaEhpKZBcLpuGkfbwRHeIvAqGRWhlcbB",
  "type": "webhook",
  "event": "session_complete",
  "config": {
    "vsFUrRTTofUV": "w=06i/r~IVkO-ex@~L,8hsDNdAu18",
    "OUHfmbLYjDpd": 2,
    "WlBMMQKgddti": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 2756953 },
	{ "name", "mHQKvNptjxnQyhxCSBoKygJXszJjYBKjaEhpKZBcLpuGkfbwRHeIvAqGRWhlcbB" },
	{ "type", "webhook" },
	{ "event", "session_complete" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```shell
curl -d "{\"financial_institution_id\":2756953,\"name\":\"mHQKvNptjxnQyhxCSBoKygJXszJjYBKjaEhpKZBcLpuGkfbwRHeIvAqGRWhlcbB\",\"type\":\"webhook\",\"event\":\"session_complete\",\"config\":{\"vsFUrRTTofUV\":\"w=06i/r~IVkO-ex@~L,8hsDNdAu18\",\"OUHfmbLYjDpd\":2,\"WlBMMQKgddti\":false}}"
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
  "name": "cPeGZPiIHcVzZVzLbMNkmIoIfDqNynNUwcGokIoiJLdOEhPXXZSGCYaHdcgGYIT",
  "type": "email",
  "config": {
    "CLRXucslXPzi": "6J>a#MR0#m900Y",
    "dVMTTyDOCAcJ": 67,
    "TTrIGsMwNfZR": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "cPeGZPiIHcVzZVzLbMNkmIoIfDqNynNUwcGokIoiJLdOEhPXXZSGCYaHdcgGYIT" },
	{ "type", "email" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```shell
curl -d "{\"name\":\"cPeGZPiIHcVzZVzLbMNkmIoIfDqNynNUwcGokIoiJLdOEhPXXZSGCYaHdcgGYIT\",\"type\":\"email\",\"config\":{\"CLRXucslXPzi\":\"6J>a#MR0#m900Y\",\"dVMTTyDOCAcJ\":67,\"TTrIGsMwNfZR\":true}}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/notifications/2670762
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
https://api.INSTANCE.cardsavr.io/notifications/2670762
```

```javascript
await session.deleteNotification(2670762);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(2670762);
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/9765662
```

```javascript
const singlesitejob = await session.getSingleSiteJob(9765662);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await session.GetSingleSiteJobAsync(9765662);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 9765662,
  "card_placement_result_id": "BrQrwOmNMHtqIQbZrQBEbdx",
  "status": "CANCELLED",
  "safe_blob": "ilHLfoFXtHwrxJRxnzP",
  "safe_nonce": "sh",
  "custom_data": {
    "oOpDyOYGqTwt": "XJ5X",
    "qwDJSPadCHLI": 6,
    "DBjleKOCThCy": false
  },
  "failure_reason": "VWFpWjiv",
  "messaging_addresses": "OxWupyrEAffhyzGHJAAoKtmnSuJZ",
  "current_state": "ouCbnhVJWYvOvXSwRcfJNDGlSdNtPrKxfCthjdkjiHWMdhMaQwkjLvandmAFMdi",
  "do_not_queue": true,
  "user_is_present": true,
  "time_elapsed": 742533,
  "job_ready_on": "1970-07-19T13:29:46.409Z",
  "started_on": "2006-06-06T18:07:38.694Z",
  "completed_on": "2017-02-20T03:45:52.261Z",
  "expiration_date": "1978-06-01T17:36:45.711Z",
  "created_on": "1994-06-14T08:16:55.644Z",
  "last_updated_on": "1994-10-23T15:13:07.350Z",
  "place_card_on_multiple_sites_job_id": 2369675,
  "user_id": 4674853,
  "card_id": 1593009,
  "account_id": 5354932
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
  "place_card_on_multiple_sites_job_id": 2369675,
  "user_id": 4674853,
  "card_id": 1593009,
  "account_id": 5354932,
  "status": "CANCELLED",
  "custom_data": {
    "oOpDyOYGqTwt": "XJ5X",
    "qwDJSPadCHLI": 6,
    "DBjleKOCThCy": false
  },
  "failure_reason": "VWFpWjiv",
  "current_state": "ouCbnhVJWYvOvXSwRcfJNDGlSdNtPrKxfCthjdkjiHWMdhMaQwkjLvandmAFMdi",
  "do_not_queue": true,
  "user_is_present": true,
  "time_elapsed": 742533,
  "started_on": "2006-06-06T18:07:38.694Z",
  "completed_on": "2017-02-20T03:45:52.261Z",
  "expiration_date": "1978-06-01T17:36:45.711Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "place_card_on_multiple_sites_job_id", 2369675 },
	{ "user_id", 4674853 },
	{ "card_id", 1593009 },
	{ "account_id", 5354932 },
	{ "status", "CANCELLED" },
	{ "failure_reason", "VWFpWjiv" },
	{ "current_state", "ouCbnhVJWYvOvXSwRcfJNDGlSdNtPrKxfCthjdkjiHWMdhMaQwkjLvandmAFMdi" },
	{ "do_not_queue", true },
	{ "user_is_present", true },
	{ "time_elapsed", 742533 },
	{ "started_on", "2006-06-06T18:07:38.694Z" },
	{ "completed_on", "2017-02-20T03:45:52.261Z" },
	{ "expiration_date", "1978-06-01T17:36:45.711Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body);
```

```shell
curl -d "{\"place_card_on_multiple_sites_job_id\":2369675,\"user_id\":4674853,\"card_id\":1593009,\"account_id\":5354932,\"status\":\"CANCELLED\",\"custom_data\":{\"oOpDyOYGqTwt\":\"XJ5X\",\"qwDJSPadCHLI\":6,\"DBjleKOCThCy\":false},\"failure_reason\":\"VWFpWjiv\",\"current_state\":\"ouCbnhVJWYvOvXSwRcfJNDGlSdNtPrKxfCthjdkjiHWMdhMaQwkjLvandmAFMdi\",\"do_not_queue\":true,\"user_is_present\":true,\"time_elapsed\":742533,\"started_on\":\"2006-06-06T18:07:38.694Z\",\"completed_on\":\"2017-02-20T03:45:52.261Z\",\"expiration_date\":\"1978-06-01T17:36:45.711Z\"}"
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
  "status": "COMPLETED",
  "custom_data": {
    "kydLelpeNSjG": "^R[4/joNK]!-",
    "mnyviBXCvqiY": 4,
    "ZjFfDgTZkXFT": true
  },
  "failure_reason": "NkhzxzoVVU",
  "current_state": "bzpsVWmFutoOVZdSUeFcGICPrJUxQISoNALzHZKvfAomArGfFyuNZiqEZcHySNe",
  "do_not_queue": false,
  "user_is_present": true,
  "time_elapsed": 8119265,
  "started_on": "1997-11-06T19:39:02.091Z",
  "completed_on": "2007-06-28T19:02:40.380Z",
  "expiration_date": "2018-05-11T11:02:22.150Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "status", "COMPLETED" },
	{ "failure_reason", "NkhzxzoVVU" },
	{ "current_state", "bzpsVWmFutoOVZdSUeFcGICPrJUxQISoNALzHZKvfAomArGfFyuNZiqEZcHySNe" },
	{ "do_not_queue", false },
	{ "user_is_present", true },
	{ "time_elapsed", 8119265 },
	{ "started_on", "1997-11-06T19:39:02.091Z" },
	{ "completed_on", "2007-06-28T19:02:40.380Z" },
	{ "expiration_date", "2018-05-11T11:02:22.150Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body);
```

```shell
curl -d "{\"status\":\"COMPLETED\",\"custom_data\":{\"kydLelpeNSjG\":\"^R[4/joNK]!-\",\"mnyviBXCvqiY\":4,\"ZjFfDgTZkXFT\":true},\"failure_reason\":\"NkhzxzoVVU\",\"current_state\":\"bzpsVWmFutoOVZdSUeFcGICPrJUxQISoNALzHZKvfAomArGfFyuNZiqEZcHySNe\",\"do_not_queue\":false,\"user_is_present\":true,\"time_elapsed\":8119265,\"started_on\":\"1997-11-06T19:39:02.091Z\",\"completed_on\":\"2007-06-28T19:02:40.380Z\",\"expiration_date\":\"2018-05-11T11:02:22.150Z\"}"
-X PUT -H "Content-Type: application/javascript"
-H "trace:{\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/9765662
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/9765662
```

```javascript
await session.deleteSingleSiteJob(9765662);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(9765662);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

