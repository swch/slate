
# Accounts
Account objects contain the account information, such as username and password, for a particular cardhoder. They are used to log in to a cardholder's account for placing a payment card.
## Get account

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1259852293
```

```javascript
const accounts = await session.getAccounts(1259852293,{"sort":"id","is_descending":true,"page":1, "page_length":25});
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(1259852293,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

```java
JsonValue accounts = session.get("/cardsavr_accounts", 1259852293,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1259852293,
  "last_password_update": "1981-04-28T08:34:36.058Z",
  "last_saved_card": "2014-07-26T12:22:58.701Z",
  "created_on": "2009-06-04T00:31:35.964Z",
  "last_updated_on": "1981-06-19T23:55:14.786Z",
  "cardholder": {
    "id": 741532548,
    "financial_institution_id": 1701627636,
    "agent_session_id": "kbnQScNkoyLHokgVjFNBGyihPyTbWIIJ",
    "type": "ephemeral",
    "first_name": "hVvIJvtZeCg",
    "last_name": "zjNGLhFBiTSsOIEYSAxibzX",
    "email": "FwjpdTJycksn@SlvoPk.QaH",
    "meta_key": "LGWGURjF",
    "cardholder_safe_key": "ou6i6LIfkw4iGS40vIRfa5IoNpG+/9d1hOo2pSE10io=",
    "custom_data": {
      "xjdMIYMlslsr": "w",
      "cyVyIECNPuCt": 33,
      "OvuTjDPPIBmH": true
    },
    "created_on": "2007-10-05T00:48:41.402Z",
    "last_updated_on": "2017-11-06T05:25:41.274Z"
  },
  "merchant_site": {
    "id": 1593129710,
    "name": "BWwPZXoUaGoyyRW",
    "host": "NZdytILJHXHvMm",
    "tags": [
      "5r~d{2VV2./{JWV<#^r%UAy",
      69,
      "^y^G*0-w}Is09HbMK2jE,,+"
    ],
    "required_form_fields": [
      "ufX>tHuSu4(K",
      23,
      "3r$bFc1Tlf64)$RY]v*m*&.(lcmd1"
    ],
    "images": [
      {
        "RzwmYexeDdJZ": "4<8a~DQ",
        "ehhUyGVxdRAa": 95,
        "NHodXieuetuh": true
      },
      {
        "tHUThhspQgmY": "3Pm=S]II}rHw6Q<",
        "woUPpzHjmwmh": 72,
        "ywXBdoKeqabA": true
      },
      {
        "vGqIENtSAjAw": "#Gzk&!A$9vM-jM_k@Njn/Lk1#GA",
        "ZATMeFOMygCE": 95,
        "rxwuUxOEhcez": false
      }
    ],
    "account_identification": {
      "jXBSSqJiuipo": "$hg*p8GH,FtBGYqI+TjoRt7@UJ7S",
      "VZqWsoaglxKZ": 19,
      "SJfKRrrOyxHD": false
    },
    "messages": {
      "JvuliKviBBVz": "0Rx3=-RVdkj+*U5FtdX)b",
      "jrSLtzNBHgqQ": 59,
      "NZmwMtrPxuLc": false
    },
    "mfa": false,
    "move_mouse_to_element": false,
    "proxy_order": [
      "oAP%8[_y4BnW)",
      43,
      "3d[IK7YeJ+%Qytpi}lY>kNQ&ON"
    ],
    "credit_card_page": "TWqHlCDh",
    "forgot_password_page": "kWaMxPJgOOFn",
    "quick_start": true,
    "login_page": "rUYvdpNjbnOQtZPEmsuH",
    "login": {
      "otddalikUXMR": "fM[hk#3",
      "DYojWZJtEZPy": 1,
      "fYjygcipMSrg": false
    }
  },
  "cardsavr_card": {
    "id": 725764063,
    "bin_id": 284014960,
    "cvv": "Wxg",
    "expiration_month": "q",
    "expiration_year": "K",
    "name_on_card": "tajielWwQFbBsqJJRybUBpEPItemBQmNosWYprCHYyESGPRreGxWwgFKvgtErCkEJdQuXquazucogJDPdQjPTpvhIFTbcCAesCpHLqJSwaZdSzhRiGizAdhgkBTjJuxKtFCaRLqyOqAzzoFuJqNWhyuQlmqiDFVipMkpnjnjSPAMuukxdLjXVSYhNeghmfTDJzAQPpybuhopjDTDmjZQpBdbAVNUFfkdaDfnQLfoeteLgCJrJhkOxpaYxmJftD",
    "first_6": "pzSsNocaSrmPjfCAANxDkwDUvrYKecXc",
    "first_7": "oSdHcTdZsGFzNSEjWDxYNEcQYQEqzVSg",
    "first_8": "ySHmRiWeGyublVYmYajtkaDDQBgkUPzi",
    "created_on": "1992-07-30T19:41:54.012Z",
    "last_updated_on": "2020-08-17T23:44:28.176Z"
  },
  "customer_key": "RKSKphafDMbzyVaHWZtbXXk"
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

**Example GET request path:**<br>`/cardsavr_accounts/1259852293`

### <a name="response-cardsavr_account"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
last_card_placed_id | number (fk) | ID of the last card placed on this account by the Virtual Browser System (VBS).
last_password_update | date | 
last_saved_card | date | Date of last card saved on this account.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) | ID of the cardholder associated with this account.
merchant_site_id | number (fk) | ID of the merchant site associated with this account.
customer_key | string | A key of merchant host and cuid. This can potentially violate a constraint with two accounts of the same merchant site.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- cardholder_ids
- merchant_site_ids
- customer_key
- last_card_placed_ids
- last_password_update_min / last_password_update_max
- last_saved_card_min / last_saved_card_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create account

```javascript
const account = await session.createAccount({
  "cardholder_id": 1989849704,
  "merchant_site_id": 515525525,
  "customer_key": "RKSKphafDMbzyVaHWZtbXXk",
  "last_card_placed_id": 636780179,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1989849704 },
	{ "merchant_site_id", 515525525 },
	{ "customer_key", "RKSKphafDMbzyVaHWZtbXXk" },
	{ "last_card_placed_id", 636780179 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1989849704 )
	.add("merchant_site_id", 515525525 )
	.add("customer_key", "RKSKphafDMbzyVaHWZtbXXk" )
	.add("last_card_placed_id", 636780179 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1989849704,\"merchant_site_id\":515525525,\"customer_key\":\"RKSKphafDMbzyVaHWZtbXXk\",\"last_card_placed_id\":636780179,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/
```

[Request hydration](## Request Hydration on POST) can be used on this endpoint. This allows you to create a new a account and all referential entities at the same time.
cardholder_id | number | yes
merchant_site_id | number | yes
customer_key | string | no
last_card_placed_id | number | no
username | string | no
password | string | no

See [account response attributes](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username and password when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Upsert account

```javascript
const account = await session.updateAccount(1,{
  "last_card_placed_id": 2070980429,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 2070980429 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 2070980429 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":2070980429,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1259852293
```

### Path

PUT /cardsavr_accounts OR /cardsavr_accounts/{id}

### Description

Upsert can be used to either update a account, create a new account, or return an existing account.  Either an id or customer_key is required for upsert. The id (in path or body), along with an updated body, can be used to update an existing account; the customer_key (in body) can likewise be used to update a account, and can also be used to create a new account, if the customer_key does not match any existing accounts. If the id or customer_key provided corresponds to a pre-existing account and no updated information has been included in the body, the existing account will be returned.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
last_card_placed_id | number |
username | string |
password | string |

See [account response parameters](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username and password when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete account

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1259852293
```

```javascript
await session.deleteAccount(undefined);
```

```csharp
CardSavrResponse<Account> account = await http.DeleteAccountAsync(undefined);
```

```java
JsonValue account = session.delete("/cardsavr_accounts", undefined, null);
```

### Path

DELETE /cardsavr_accounts/{id}

### Description

Delete a account and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [account response parameters](#response-cardsavr_account).


# Addresses
Address objects contain the billing address for a specific cardholder, and are used to populate billing address information on merchant sites. They are linked to cards and cardholders.
## Get address

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/682307500
```

```javascript
const addresses = await session.getAddresses(682307500,{"sort":"id","is_descending":true,"page":1, "page_length":25});
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(682307500,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

```java
JsonValue addresses = session.get("/cardsavr_addresses", 682307500,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 682307500,
  "address1": "EckasdmEvkncKmlJksGjNjcaqIAfeLWQJVuWYafZrgnbAlmjcEONRtqfRJpfZSOereHkwQcDYrEoDOsiEsTcShptQxHpFbdIAAF",
  "address2": "coFNuSQCodCHItVRuBukEYUJuYcESMbqirSQKUbfWBMUultGGpbEmxpTYcfATAIhaKyqiGowxKrOWEYZjbpoZRXsmOOquFTXjXm",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "ivMoiNb",
  "last_name": "PiCvOlKtRcVKievEwCX",
  "email": "RCIHQWVICUJu@uWfbhI.Csx",
  "phone_number": "2065555555",
  "created_on": "1982-12-13T00:08:15.736Z",
  "last_updated_on": "2021-09-04T14:42:25.499Z",
  "cardholder": {
    "id": 640508965,
    "financial_institution_id": 1494692725,
    "agent_session_id": "CqUpOpUYbRWxqQKrfvNOnMQSzUEBWgGu",
    "type": "persistent",
    "first_name": "cADsh",
    "last_name": "iRLcYVXvmXuy",
    "email": "OltYunQwvTEY@IBAiiN.vAr",
    "meta_key": "dQshYNqYZIiwov",
    "cardholder_safe_key": "hQm2VJTC5Dk3D0q0Rxm8QhfqbcZHI/2NJwQDiCZrKaQ=",
    "custom_data": {
      "DffmXHQpYsOf": "B<tV}70&}X!",
      "AdatsetRGTlc": 9,
      "tzacwZDXipHD": false
    },
    "created_on": "2001-02-15T14:22:01.504Z",
    "last_updated_on": "1992-04-09T05:38:31.510Z"
  }
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

**Example GET request path:**<br>`/cardsavr_addresses/682307500`

### <a name="response-cardsavr_address"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
address1 | string | 
address2 | string | 
city | string | 
subnational | string | Subnational unit (i.e. state or province).
postal_code | string | 
postal_other | string | E.g. last four digits in a zip-plus-four.
country | string | 
is_primary | boolean | Indicates if this is the primary address of this cardholder, as a cardholder can be linked to multiple addresses.
first_name | string | 
last_name | string | 
email | string | 
phone_number | string | 
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) | ID of the cardholder associated with this address.

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
  "cardholder_id": 1072346762,
  "address1": "EckasdmEvkncKmlJksGjNjcaqIAfeLWQJVuWYafZrgnbAlmjcEONRtqfRJpfZSOereHkwQcDYrEoDOsiEsTcShptQxHpFbdIAAF",
  "address2": "coFNuSQCodCHItVRuBukEYUJuYcESMbqirSQKUbfWBMUultGGpbEmxpTYcfATAIhaKyqiGowxKrOWEYZjbpoZRXsmOOquFTXjXm",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "ivMoiNb",
  "last_name": "PiCvOlKtRcVKievEwCX",
  "email": "RCIHQWVICUJu@uWfbhI.Csx",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1072346762 },
	{ "address1", "EckasdmEvkncKmlJksGjNjcaqIAfeLWQJVuWYafZrgnbAlmjcEONRtqfRJpfZSOereHkwQcDYrEoDOsiEsTcShptQxHpFbdIAAF" },
	{ "address2", "coFNuSQCodCHItVRuBukEYUJuYcESMbqirSQKUbfWBMUultGGpbEmxpTYcfATAIhaKyqiGowxKrOWEYZjbpoZRXsmOOquFTXjXm" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "ivMoiNb" },
	{ "last_name", "PiCvOlKtRcVKievEwCX" },
	{ "email", "RCIHQWVICUJu@uWfbhI.Csx" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1072346762 )
	.add("address1", "EckasdmEvkncKmlJksGjNjcaqIAfeLWQJVuWYafZrgnbAlmjcEONRtqfRJpfZSOereHkwQcDYrEoDOsiEsTcShptQxHpFbdIAAF" )
	.add("address2", "coFNuSQCodCHItVRuBukEYUJuYcESMbqirSQKUbfWBMUultGGpbEmxpTYcfATAIhaKyqiGowxKrOWEYZjbpoZRXsmOOquFTXjXm" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "ivMoiNb" )
	.add("last_name", "PiCvOlKtRcVKievEwCX" )
	.add("email", "RCIHQWVICUJu@uWfbhI.Csx" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1072346762,\"address1\":\"EckasdmEvkncKmlJksGjNjcaqIAfeLWQJVuWYafZrgnbAlmjcEONRtqfRJpfZSOereHkwQcDYrEoDOsiEsTcShptQxHpFbdIAAF\",\"address2\":\"coFNuSQCodCHItVRuBukEYUJuYcESMbqirSQKUbfWBMUultGGpbEmxpTYcfATAIhaKyqiGowxKrOWEYZjbpoZRXsmOOquFTXjXm\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"ivMoiNb\",\"last_name\":\"PiCvOlKtRcVKievEwCX\",\"email\":\"RCIHQWVICUJu@uWfbhI.Csx\",\"phone_number\":\"2065555555\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/
```

[Request hydration](## Request Hydration on POST) can be used on this endpoint. This allows you to create a new an address and all referential entities at the same time.
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
const address = await session.updateAddress(1,{
  "address1": "CczbYYRhXxkcGynSkMqIzieTCgPMfaTwTezMexHeqpCFMMweibzHcqqfwAAfAeRBaENISWFsYOfKKvqnfAwUyTIUtUQZIjVmnJM",
  "address2": "MMZebmPgIDndvfcqTORlILEerPmYuVmPawyJsmbVKXhGIZdvWzxQkMizCToBfpQIpNhICsmwIdwNdScXylLbhidrLasCMazfPzY",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "ZYZxYSj",
  "last_name": "wXZarvwDrZQFuAaSoEgqdxWFA",
  "email": "GgEiyKqFjOxz@SLfVOJ.OsB",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "CczbYYRhXxkcGynSkMqIzieTCgPMfaTwTezMexHeqpCFMMweibzHcqqfwAAfAeRBaENISWFsYOfKKvqnfAwUyTIUtUQZIjVmnJM" },
	{ "address2", "MMZebmPgIDndvfcqTORlILEerPmYuVmPawyJsmbVKXhGIZdvWzxQkMizCToBfpQIpNhICsmwIdwNdScXylLbhidrLasCMazfPzY" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "ZYZxYSj" },
	{ "last_name", "wXZarvwDrZQFuAaSoEgqdxWFA" },
	{ "email", "GgEiyKqFjOxz@SLfVOJ.OsB" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "CczbYYRhXxkcGynSkMqIzieTCgPMfaTwTezMexHeqpCFMMweibzHcqqfwAAfAeRBaENISWFsYOfKKvqnfAwUyTIUtUQZIjVmnJM" )
	.add("address2", "MMZebmPgIDndvfcqTORlILEerPmYuVmPawyJsmbVKXhGIZdvWzxQkMizCToBfpQIpNhICsmwIdwNdScXylLbhidrLasCMazfPzY" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "ZYZxYSj" )
	.add("last_name", "wXZarvwDrZQFuAaSoEgqdxWFA" )
	.add("email", "GgEiyKqFjOxz@SLfVOJ.OsB" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"CczbYYRhXxkcGynSkMqIzieTCgPMfaTwTezMexHeqpCFMMweibzHcqqfwAAfAeRBaENISWFsYOfKKvqnfAwUyTIUtUQZIjVmnJM\",\"address2\":\"MMZebmPgIDndvfcqTORlILEerPmYuVmPawyJsmbVKXhGIZdvWzxQkMizCToBfpQIpNhICsmwIdwNdScXylLbhidrLasCMazfPzY\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"ZYZxYSj\",\"last_name\":\"wXZarvwDrZQFuAaSoEgqdxWFA\",\"email\":\"GgEiyKqFjOxz@SLfVOJ.OsB\",\"phone_number\":\"2065555555\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/682307500
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
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/682307500
```

```javascript
await session.deleteAddress(undefined);
```

```csharp
CardSavrResponse<Address> address = await http.DeleteAddressAsync(undefined);
```

```java
JsonValue address = session.delete("/cardsavr_addresses", undefined, null);
```

### Path

DELETE /cardsavr_addresses/{id}

### Description

Delete a address and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [address response parameters](#response-cardsavr_address).


# Bins
A Bank Identification Number (BIN) object represents a BIN used by a financial institution in the CardSavr API. They are linked to cards and FIs and used for reporting purposes.
## Get bin

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1229023070
```

```javascript
const bins = await session.getBins(1229023070,{"sort":"id","is_descending":true,"page":1, "page_length":25});
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(1229023070,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

```java
JsonValue bins = session.get("/cardsavr_bins", 1229023070,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1229023070,
  "custom_data": {
    "ySihwBjbtTiE": "~5[^K,kCv}l1n}2G=)Ea>+EBWfd>Y",
    "niwXekWnItFW": 16,
    "EFrIvcmXZIhE": false
  },
  "created_on": "1977-01-14T20:26:24.991Z",
  "last_updated_on": "1980-12-18T03:20:16.721Z",
  "financial_institution": {
    "id": 1243235783,
    "name": "iFrMjSWnkTDeHlrtDWipyrFnoZuYJSxGaWECThAVEdeSdnattbvhRtKMlbbyEUx",
    "description": "Bmmewct",
    "lookup_key": "poKzXUbGifhcWiUhucZlUhaDMYlpdmhJBuCAFpSKnMyymSXXlMzCOHDvNWxHUmx",
    "alternate_lookup_key": "ZZhbMRhvIhzyviexoLcMKdyZNYMlLRjjTzNIRhmwWpDefEEEeMoZXZZEGjoCXdI",
    "config": {
      "gelgHJZBwWCu": "3*{",
      "yslKgxtmTwLv": 25,
      "TXHLCJIXZNBv": false
    },
    "created_on": "1991-02-11T21:58:31.778Z",
    "last_updated_on": "2002-06-26T04:31:43.238Z"
  },
  "bank_identification_number": "30461649"
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

**Example GET request path:**<br>`/cardsavr_bins/1229023070`

### <a name="response-cardsavr_bin"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
financial_institution_id | number (fk) | ID of financial institution that this Bank Identification Number belongs to.
custom_data | object | Custom data (e.g. brand, type) that can be added according to FI need.
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
  "financial_institution_id": 1569625213,
  "bank_identification_number": "30461649",
  "custom_data": {
    "ySihwBjbtTiE": "~5[^K,kCv}l1n}2G=)Ea>+EBWfd>Y",
    "niwXekWnItFW": 16,
    "EFrIvcmXZIhE": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1569625213 },
	{ "bank_identification_number", "30461649" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1569625213 )
	.add("bank_identification_number", "30461649" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1569625213,\"bank_identification_number\":\"30461649\",\"custom_data\":{\"ySihwBjbtTiE\":\"~5[^K,kCv}l1n}2G=)Ea>+EBWfd>Y\",\"niwXekWnItFW\":16,\"EFrIvcmXZIhE\":false}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/
```

[Request hydration](## Request Hydration on POST) can be used on this endpoint. This allows you to create a new a bin and all referential entities at the same time.
financial_institution_id | number | yes
bank_identification_number | string | yes
custom_data | object | no

See [bin response attributes](#response-cardsavr_bin).


## Update bin

```javascript
const bin = await session.updateBin(1,{
  "financial_institution_id": 984732499,
  "custom_data": {
    "fowXdDwcxSiN": "96(4Rql-/Qsc{y+pe[_Ml",
    "ZRwGyMPnzQAf": 78,
    "qCswrjPZNoFF": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 984732499 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 984732499 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":984732499,\"custom_data\":{\"fowXdDwcxSiN\":\"96(4Rql-/Qsc{y+pe[_Ml\",\"ZRwGyMPnzQAf\":78,\"qCswrjPZNoFF\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1229023070
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
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/1229023070
```

```javascript
await session.deleteBin(undefined);
```

```csharp
CardSavrResponse<Bin> bin = await http.DeleteBinAsync(undefined);
```

```java
JsonValue bin = session.delete("/cardsavr_bins", undefined, null);
```

### Path

DELETE /cardsavr_bins/{id}

### Description

Delete a bin and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [bin response parameters](#response-cardsavr_bin).


# Card Placement Results
Card Placement results are a flatted version of the jobs and its publily available meta data. Although sensitive data like the PAN and account creds are not available, all the details of the job are captured here for future reference after the corresponding entities may have been deleted.
## Get card placement result

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/card_placement_results/683612158
```

```javascript
const cardplacementresults = await session.getCardPlacementResults(683612158,{"sort":"id","is_descending":true,"page":1, "page_length":25});
```

```csharp
CardSavrResponse<CardPlacementResults> cardplacementresults = await session.GetCardPlacementResultsAsync(683612158,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

```java
JsonValue cardplacementresults = session.get("/card_placement_results", 683612158,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 683612158,
  "merchant_site_hostname": "usoSTYnAQoewhqNuOImlzDgJvZUNZYjaXGkLYdGedNgyyMrGCvPZlTTluIDeDIWAzocDGJXMGzVokfssoqibmDUCRZgjGLLGVsbnRLLAPFgYwcitdXkkfPYZkAGlYqEmJTSSEEvSmgCHRnHcVCevHONhKbhpHLylMkqGLJYVLgyXMWNETONcnbBbNlmgcxNuYVqEhhUHwGOsxESibxcpkLFayrFMoFWTQNWknBFaOZEFITtFeZTAhtPKOXvwTN",
  "meta_key": "MB9810411",
  "fi_name": "HvkTIDwxLQBuprlHipZQUpzWXfmgzJnMaSkkPOwgjttBIVeOmaHqzsqGFcxCTJn",
  "bank_identification_number": "55627770",
  "cuid": "NqpybxfxCWetasgrDpaZqxTAVSAYJYgfgWvkVecRXnqtkVUvoZBrucSGFYwEjISjrQzYsxGUdsAFxaDHtuSCWdjKdePYJIjwKqpxHUQphXnDpMYOQmDibObiiGEveYPvoWCKMphpJmZEmnisGOAFLXQYjxKkjDpieUffzjcVEZMqCPfgmPrUiBEZZoMqNhfhnyvttyDEgjBRPbjKjiNxvkZhcCyNeqFABYJrXdJfIlXKwThdjYvVWZtkqHUFFW",
  "par": "XzRmFfhiVJMefUZdIJHTuwisxYFFa",
  "card_customer_key": "bdhibGCUDKtJudDmfkWGTIJbrcCjDaGYqqYumLJPsEmJFQFdECvyPdUfeYZjszqphVoZcjvWiGSxYlwHWkdNpYGeukXTZdOxdfiJxnJNxpBnKzoQOhXhWogHYzwGpDwCebNjwxhChIXFMlcAXnhdJBaAOfirqbXqGMSzruXAxdovIiUhpehJCiCTGzcKHBSAHQZUCZgauQGTRtaWeJOBkjsZDWXDGZjFuNTFsbDewcnATkykgzmljAblwOwlvL",
  "account_customer_key": "NJoUAXbPqcEPnLijMHHuPQImLYXMoakSLoAberYvEYetjrmZUKJGvufILeyKHiMUPujHlmKnIkbPHXHhMsZjcFTLSFhlRETVeVTYOuyNPxeRpYgRsnworLfhWspPAaJRnfYeiSgzPpRjyGEJzXtvZHEffrNEiGHNSWxqVwulCGTTXWnXlZIzsRPtHtsLbJOdyyxxtDOrLszwAMSVmQjOMadikNQGMdMfJvaQbxSqttmaJLYWBnaOUoCOiQIqzw",
  "status": "wppBUEaVquuZbknurTLXAMoCkRJWqAyrKVgXaBDFmbhCGDZCkCBYHDbOrDMbJli",
  "status_message": "XJTIErb",
  "termination_type": "rFEWJmrmnodWdjFfYRUIJvxmCmzGnxHOzvRzzRhhSAdDkFKoyIRHeWNRluGkhKr",
  "custom_data": {
    "OooxvQHWbtof": "m(yE<wejF7-<rwI]AYE%&[hDPxz7R",
    "GoYkmxzjmJzB": 25,
    "BIGXTcOzTfeF": false
  },
  "time_elapsed": 1503225798,
  "first_6": "xZNAfoVNbDQDNgphQlBxVYILRpijGOuv",
  "first_7": "HSmtrwxyHEijEIxMKiwlVbivwDZVlddN",
  "first_8": "oVqhalMPtBYZFBBZVcWafTDFurPgHjOn",
  "trace": "zOFsBcqahoOaHQBsmvorCHAcAvnZimOfdbwGVApTrPmGiPUmmsBLIAaAwlkjWLJSZqaJrgLfCtSVqKajezNHLDTmAssVjhGmdgDrIAKFYdmYNtFSiDPwHytSDxTQwbThTAQEooINGqFLpwezgzqfpNOafpXiMcWAGNGOoSdmsHWPbMoFzeBTLwMQjRnpHNWFieeUrdvuhwXZkjMzwVzMmREjUHuHGCWXlTquPFJHjlhsXQUkiLZtsxLnweyZgF",
  "email_sent": true,
  "completed_on": "1982-12-13T09:43:00.495Z",
  "created_on": "1997-12-28T05:42:00.753Z",
  "last_updated_on": "2007-07-10T03:48:22.406Z",
  "financial_institution": {
    "id": 1736010163,
    "name": "VRstiwzGdbWSnmQWiCVjSOGiMKWIOdzAYCiYOrnQTQktFKDkPVqcKthdFSQzOqI",
    "description": "hCUliSgvybpbyvoaOXLlmCRKpEgsrMV",
    "lookup_key": "jlRbzARXjCJQzzNWbvWtIuSYmFWXbahnjdZIZyOvOUzyBePAmQbLehyDTMOplcO",
    "alternate_lookup_key": "JRTcRDSFPviYKlQxkrbHsgkWQquiybAHeMVftXVmATSxXBeAcMYKSXVIuvFKmkh",
    "config": {
      "XyJRabpCwltS": "}t$6SzKp=]g+3~vVQ*",
      "eHILbXPFunnR": 32,
      "rWqahXZtmIdQ": false
    },
    "created_on": "1974-07-21T19:12:59.806Z",
    "last_updated_on": "2019-02-25T13:51:52.529Z"
  },
  "merchant_site": {
    "id": 982524310,
    "name": "XgTdCtoVgNzMfVUmowgliVTCAAHpRvK",
    "host": "YTSxfyHhVYYGysjoPZYB",
    "tags": [
      "+JRT&8G]cZB1y",
      29,
      "7SQm_R(sk{U&V)GUZ{f"
    ],
    "queue_name": "vbs_queue",
    "required_form_fields": [
      "G1l7sl",
      25,
      "pk8JO!Bhow<YUjNQ"
    ],
    "images": [
      {
        "BxjSqWdojGJD": "^BBFV=-SSfZgrzF+_cTu9![hcG~G/s%",
        "vGHXLQncsSSv": 5,
        "JXxWoYNJdfcC": true
      },
      {
        "aEGzpvfMPIaR": "l",
        "HYpTGyLjgfgP": 23,
        "LaNfsXkwCEzD": false
      },
      {
        "tvJpHItbpSie": "2",
        "GRUuiffPXzYH": 76,
        "iYCqBJgYHkrk": false
      }
    ],
    "account_identification": {
      "mkoGpdpahhvg": "%9$DFgn2mEFbVB$/Y",
      "lqsAIbUYetkM": 43,
      "BQSuXgMJrJJo": false
    },
    "messages": {
      "BtWHpIyshzVL": "(S3M/gso0=vEhRMBtTbVM-NMZ",
      "kJDeDMoZFreW": 99,
      "umtsyafshAph": true
    },
    "mfa": true,
    "move_mouse_to_element": true,
    "proxy_order": [
      "mqI#)d{N",
      48,
      "#k7"
    ],
    "credit_card_page": "qvSEFOFdnFIlBR",
    "forgot_password_page": "vXIEuASXkSfNgCZVEfxXXXgDb",
    "quick_start": true,
    "login_page": "oqHHOgmaDGXVdLBYjZLTtO",
    "login": {
      "dShHuZXUDFCF": "dkIp%*k%64Z!fJOJXwes%$",
      "FuPwYQsJFvbZ": 90,
      "rsuhUdorXYqu": false
    }
  },
  "cardsavr_bin": {
    "id": 806408885,
    "financial_institution_id": 1451402729,
    "custom_data": {
      "jQWFOzBKwOvQ": "BBcv,SD7dqa",
      "xapvhcVZhvZf": 77,
      "wSpCoJwWlQnZ": true
    },
    "created_on": "2000-03-21T12:45:43.242Z",
    "last_updated_on": "1982-06-24T07:27:32.893Z"
  },
  "place_card_on_single_site_job_id": 181777823
}
```

### Path

GET /card_placement_results **(batch)** or GET /card_placement_results/:id **(singular)**

### Description

Returns the card placement result specified by the provided ID

#### Batch GET requests

**Batch requests** return the first page of all viewable card placement results, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/card_placement_results?ids=1,2`

#### Singular GET requests

**Singular requests** only return the card placement result matching the id provided in the path.

**Example GET request path:**<br>`/card_placement_results/683612158`

### <a name="response-card_placement_result"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
merchant_site_hostname | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
fi_name | string | 
bank_identification_number | string | 
cuid | string | 
par | string | 
card_customer_key | string | 
account_customer_key | string | 
status | string | 
status_message | string | Human readable representation of the jobs status.
termination_type | string | Final termination status of a job. (BILLABLE, SITE_INTERACTION_FAILURE, USER_DATA_FAILURE, PROCESS FAILURE)
custom_data | object | 
time_elapsed | number | 
first_6 | string | First six digits of card number.
first_7 | string | First seven digits of card number.
first_8 | string | First eight digits of card number.
trace | string | 
financial_institution_id | number (fk) | 
merchant_site_id | number (fk) | 
email_sent | boolean | 
completed_on | date | 
created_on | date | Date this job result was created on
last_updated_on | date | Date this job result was last updated on
place_card_on_single_site_job_id | number | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- merchant_site_hostnames
- merchant_site_hostname
- meta_key
- fi_name
- bank_identification_numbers
- cuids
- pars
- card_customer_keys
- account_customer_keys
- status
- termination_type
- termination_types_include / termaxation_types_exclude
- first_6
- first_7
- first_8
- place_card_on_single_site_job_ids
- financial_institution_ids
- merchant_site_ids
- email_sent
- completed_on_min / completed_on_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create card placement result

```javascript
const cardplacementresult = await session.createCardPlacementResult({
  "merchant_site_hostname": "usoSTYnAQoewhqNuOImlzDgJvZUNZYjaXGkLYdGedNgyyMrGCvPZlTTluIDeDIWAzocDGJXMGzVokfssoqibmDUCRZgjGLLGVsbnRLLAPFgYwcitdXkkfPYZkAGlYqEmJTSSEEvSmgCHRnHcVCevHONhKbhpHLylMkqGLJYVLgyXMWNETONcnbBbNlmgcxNuYVqEhhUHwGOsxESibxcpkLFayrFMoFWTQNWknBFaOZEFITtFeZTAhtPKOXvwTN",
  "meta_key": "MB9810411",
  "fi_name": "HvkTIDwxLQBuprlHipZQUpzWXfmgzJnMaSkkPOwgjttBIVeOmaHqzsqGFcxCTJn",
  "bank_identification_number": "55627770",
  "cuid": "NqpybxfxCWetasgrDpaZqxTAVSAYJYgfgWvkVecRXnqtkVUvoZBrucSGFYwEjISjrQzYsxGUdsAFxaDHtuSCWdjKdePYJIjwKqpxHUQphXnDpMYOQmDibObiiGEveYPvoWCKMphpJmZEmnisGOAFLXQYjxKkjDpieUffzjcVEZMqCPfgmPrUiBEZZoMqNhfhnyvttyDEgjBRPbjKjiNxvkZhcCyNeqFABYJrXdJfIlXKwThdjYvVWZtkqHUFFW",
  "par": "XzRmFfhiVJMefUZdIJHTuwisxYFFa",
  "card_customer_key": "bdhibGCUDKtJudDmfkWGTIJbrcCjDaGYqqYumLJPsEmJFQFdECvyPdUfeYZjszqphVoZcjvWiGSxYlwHWkdNpYGeukXTZdOxdfiJxnJNxpBnKzoQOhXhWogHYzwGpDwCebNjwxhChIXFMlcAXnhdJBaAOfirqbXqGMSzruXAxdovIiUhpehJCiCTGzcKHBSAHQZUCZgauQGTRtaWeJOBkjsZDWXDGZjFuNTFsbDewcnATkykgzmljAblwOwlvL",
  "account_customer_key": "NJoUAXbPqcEPnLijMHHuPQImLYXMoakSLoAberYvEYetjrmZUKJGvufILeyKHiMUPujHlmKnIkbPHXHhMsZjcFTLSFhlRETVeVTYOuyNPxeRpYgRsnworLfhWspPAaJRnfYeiSgzPpRjyGEJzXtvZHEffrNEiGHNSWxqVwulCGTTXWnXlZIzsRPtHtsLbJOdyyxxtDOrLszwAMSVmQjOMadikNQGMdMfJvaQbxSqttmaJLYWBnaOUoCOiQIqzw",
  "status": "wppBUEaVquuZbknurTLXAMoCkRJWqAyrKVgXaBDFmbhCGDZCkCBYHDbOrDMbJli",
  "status_message": "XJTIErb",
  "termination_type": "rFEWJmrmnodWdjFfYRUIJvxmCmzGnxHOzvRzzRhhSAdDkFKoyIRHeWNRluGkhKr",
  "custom_data": {
    "OooxvQHWbtof": "m(yE<wejF7-<rwI]AYE%&[hDPxz7R",
    "GoYkmxzjmJzB": 25,
    "BIGXTcOzTfeF": false
  },
  "time_elapsed": 1503225798,
  "first_6": "xZNAfoVNbDQDNgphQlBxVYILRpijGOuv",
  "first_7": "HSmtrwxyHEijEIxMKiwlVbivwDZVlddN",
  "first_8": "oVqhalMPtBYZFBBZVcWafTDFurPgHjOn",
  "trace": "zOFsBcqahoOaHQBsmvorCHAcAvnZimOfdbwGVApTrPmGiPUmmsBLIAaAwlkjWLJSZqaJrgLfCtSVqKajezNHLDTmAssVjhGmdgDrIAKFYdmYNtFSiDPwHytSDxTQwbThTAQEooINGqFLpwezgzqfpNOafpXiMcWAGNGOoSdmsHWPbMoFzeBTLwMQjRnpHNWFieeUrdvuhwXZkjMzwVzMmREjUHuHGCWXlTquPFJHjlhsXQUkiLZtsxLnweyZgF",
  "place_card_on_single_site_job_id": 181777823,
  "financial_institution_id": 193057576,
  "merchant_site_id": 1814886620,
  "email_sent": true,
  "completed_on": "1982-12-13T09:43:00.495Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "merchant_site_hostname", "usoSTYnAQoewhqNuOImlzDgJvZUNZYjaXGkLYdGedNgyyMrGCvPZlTTluIDeDIWAzocDGJXMGzVokfssoqibmDUCRZgjGLLGVsbnRLLAPFgYwcitdXkkfPYZkAGlYqEmJTSSEEvSmgCHRnHcVCevHONhKbhpHLylMkqGLJYVLgyXMWNETONcnbBbNlmgcxNuYVqEhhUHwGOsxESibxcpkLFayrFMoFWTQNWknBFaOZEFITtFeZTAhtPKOXvwTN" },
	{ "meta_key", "MB9810411" },
	{ "fi_name", "HvkTIDwxLQBuprlHipZQUpzWXfmgzJnMaSkkPOwgjttBIVeOmaHqzsqGFcxCTJn" },
	{ "bank_identification_number", "55627770" },
	{ "cuid", "NqpybxfxCWetasgrDpaZqxTAVSAYJYgfgWvkVecRXnqtkVUvoZBrucSGFYwEjISjrQzYsxGUdsAFxaDHtuSCWdjKdePYJIjwKqpxHUQphXnDpMYOQmDibObiiGEveYPvoWCKMphpJmZEmnisGOAFLXQYjxKkjDpieUffzjcVEZMqCPfgmPrUiBEZZoMqNhfhnyvttyDEgjBRPbjKjiNxvkZhcCyNeqFABYJrXdJfIlXKwThdjYvVWZtkqHUFFW" },
	{ "par", "XzRmFfhiVJMefUZdIJHTuwisxYFFa" },
	{ "card_customer_key", "bdhibGCUDKtJudDmfkWGTIJbrcCjDaGYqqYumLJPsEmJFQFdECvyPdUfeYZjszqphVoZcjvWiGSxYlwHWkdNpYGeukXTZdOxdfiJxnJNxpBnKzoQOhXhWogHYzwGpDwCebNjwxhChIXFMlcAXnhdJBaAOfirqbXqGMSzruXAxdovIiUhpehJCiCTGzcKHBSAHQZUCZgauQGTRtaWeJOBkjsZDWXDGZjFuNTFsbDewcnATkykgzmljAblwOwlvL" },
	{ "account_customer_key", "NJoUAXbPqcEPnLijMHHuPQImLYXMoakSLoAberYvEYetjrmZUKJGvufILeyKHiMUPujHlmKnIkbPHXHhMsZjcFTLSFhlRETVeVTYOuyNPxeRpYgRsnworLfhWspPAaJRnfYeiSgzPpRjyGEJzXtvZHEffrNEiGHNSWxqVwulCGTTXWnXlZIzsRPtHtsLbJOdyyxxtDOrLszwAMSVmQjOMadikNQGMdMfJvaQbxSqttmaJLYWBnaOUoCOiQIqzw" },
	{ "status", "wppBUEaVquuZbknurTLXAMoCkRJWqAyrKVgXaBDFmbhCGDZCkCBYHDbOrDMbJli" },
	{ "status_message", "XJTIErb" },
	{ "termination_type", "rFEWJmrmnodWdjFfYRUIJvxmCmzGnxHOzvRzzRhhSAdDkFKoyIRHeWNRluGkhKr" },
	{ "time_elapsed", 1503225798 },
	{ "first_6", "xZNAfoVNbDQDNgphQlBxVYILRpijGOuv" },
	{ "first_7", "HSmtrwxyHEijEIxMKiwlVbivwDZVlddN" },
	{ "first_8", "oVqhalMPtBYZFBBZVcWafTDFurPgHjOn" },
	{ "trace", "zOFsBcqahoOaHQBsmvorCHAcAvnZimOfdbwGVApTrPmGiPUmmsBLIAaAwlkjWLJSZqaJrgLfCtSVqKajezNHLDTmAssVjhGmdgDrIAKFYdmYNtFSiDPwHytSDxTQwbThTAQEooINGqFLpwezgzqfpNOafpXiMcWAGNGOoSdmsHWPbMoFzeBTLwMQjRnpHNWFieeUrdvuhwXZkjMzwVzMmREjUHuHGCWXlTquPFJHjlhsXQUkiLZtsxLnweyZgF" },
	{ "place_card_on_single_site_job_id", 181777823 },
	{ "financial_institution_id", 193057576 },
	{ "merchant_site_id", 1814886620 },
	{ "email_sent", true },
	{ "completed_on", "1982-12-13T09:43:00.495Z" }
};

CardSavrResponse<CardPlacementResult> cardplacementresult = await http.CreateCardPlacementResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("merchant_site_hostname", "usoSTYnAQoewhqNuOImlzDgJvZUNZYjaXGkLYdGedNgyyMrGCvPZlTTluIDeDIWAzocDGJXMGzVokfssoqibmDUCRZgjGLLGVsbnRLLAPFgYwcitdXkkfPYZkAGlYqEmJTSSEEvSmgCHRnHcVCevHONhKbhpHLylMkqGLJYVLgyXMWNETONcnbBbNlmgcxNuYVqEhhUHwGOsxESibxcpkLFayrFMoFWTQNWknBFaOZEFITtFeZTAhtPKOXvwTN" )
	.add("meta_key", "MB9810411" )
	.add("fi_name", "HvkTIDwxLQBuprlHipZQUpzWXfmgzJnMaSkkPOwgjttBIVeOmaHqzsqGFcxCTJn" )
	.add("bank_identification_number", "55627770" )
	.add("cuid", "NqpybxfxCWetasgrDpaZqxTAVSAYJYgfgWvkVecRXnqtkVUvoZBrucSGFYwEjISjrQzYsxGUdsAFxaDHtuSCWdjKdePYJIjwKqpxHUQphXnDpMYOQmDibObiiGEveYPvoWCKMphpJmZEmnisGOAFLXQYjxKkjDpieUffzjcVEZMqCPfgmPrUiBEZZoMqNhfhnyvttyDEgjBRPbjKjiNxvkZhcCyNeqFABYJrXdJfIlXKwThdjYvVWZtkqHUFFW" )
	.add("par", "XzRmFfhiVJMefUZdIJHTuwisxYFFa" )
	.add("card_customer_key", "bdhibGCUDKtJudDmfkWGTIJbrcCjDaGYqqYumLJPsEmJFQFdECvyPdUfeYZjszqphVoZcjvWiGSxYlwHWkdNpYGeukXTZdOxdfiJxnJNxpBnKzoQOhXhWogHYzwGpDwCebNjwxhChIXFMlcAXnhdJBaAOfirqbXqGMSzruXAxdovIiUhpehJCiCTGzcKHBSAHQZUCZgauQGTRtaWeJOBkjsZDWXDGZjFuNTFsbDewcnATkykgzmljAblwOwlvL" )
	.add("account_customer_key", "NJoUAXbPqcEPnLijMHHuPQImLYXMoakSLoAberYvEYetjrmZUKJGvufILeyKHiMUPujHlmKnIkbPHXHhMsZjcFTLSFhlRETVeVTYOuyNPxeRpYgRsnworLfhWspPAaJRnfYeiSgzPpRjyGEJzXtvZHEffrNEiGHNSWxqVwulCGTTXWnXlZIzsRPtHtsLbJOdyyxxtDOrLszwAMSVmQjOMadikNQGMdMfJvaQbxSqttmaJLYWBnaOUoCOiQIqzw" )
	.add("status", "wppBUEaVquuZbknurTLXAMoCkRJWqAyrKVgXaBDFmbhCGDZCkCBYHDbOrDMbJli" )
	.add("status_message", "XJTIErb" )
	.add("termination_type", "rFEWJmrmnodWdjFfYRUIJvxmCmzGnxHOzvRzzRhhSAdDkFKoyIRHeWNRluGkhKr" )
	.add("time_elapsed", 1503225798 )
	.add("first_6", "xZNAfoVNbDQDNgphQlBxVYILRpijGOuv" )
	.add("first_7", "HSmtrwxyHEijEIxMKiwlVbivwDZVlddN" )
	.add("first_8", "oVqhalMPtBYZFBBZVcWafTDFurPgHjOn" )
	.add("trace", "zOFsBcqahoOaHQBsmvorCHAcAvnZimOfdbwGVApTrPmGiPUmmsBLIAaAwlkjWLJSZqaJrgLfCtSVqKajezNHLDTmAssVjhGmdgDrIAKFYdmYNtFSiDPwHytSDxTQwbThTAQEooINGqFLpwezgzqfpNOafpXiMcWAGNGOoSdmsHWPbMoFzeBTLwMQjRnpHNWFieeUrdvuhwXZkjMzwVzMmREjUHuHGCWXlTquPFJHjlhsXQUkiLZtsxLnweyZgF" )
	.add("place_card_on_single_site_job_id", 181777823 )
	.add("financial_institution_id", 193057576 )
	.add("merchant_site_id", 1814886620 )
	.add("email_sent", true )
	.add("completed_on", "1982-12-13T09:43:00.495Z" )
	.build();
JsonValue cardplacementresult = session.post("/card_placement_results", body, null, null);
```

```shell
curl -d "{\"merchant_site_hostname\":\"usoSTYnAQoewhqNuOImlzDgJvZUNZYjaXGkLYdGedNgyyMrGCvPZlTTluIDeDIWAzocDGJXMGzVokfssoqibmDUCRZgjGLLGVsbnRLLAPFgYwcitdXkkfPYZkAGlYqEmJTSSEEvSmgCHRnHcVCevHONhKbhpHLylMkqGLJYVLgyXMWNETONcnbBbNlmgcxNuYVqEhhUHwGOsxESibxcpkLFayrFMoFWTQNWknBFaOZEFITtFeZTAhtPKOXvwTN\",\"meta_key\":\"MB9810411\",\"fi_name\":\"HvkTIDwxLQBuprlHipZQUpzWXfmgzJnMaSkkPOwgjttBIVeOmaHqzsqGFcxCTJn\",\"bank_identification_number\":\"55627770\",\"cuid\":\"NqpybxfxCWetasgrDpaZqxTAVSAYJYgfgWvkVecRXnqtkVUvoZBrucSGFYwEjISjrQzYsxGUdsAFxaDHtuSCWdjKdePYJIjwKqpxHUQphXnDpMYOQmDibObiiGEveYPvoWCKMphpJmZEmnisGOAFLXQYjxKkjDpieUffzjcVEZMqCPfgmPrUiBEZZoMqNhfhnyvttyDEgjBRPbjKjiNxvkZhcCyNeqFABYJrXdJfIlXKwThdjYvVWZtkqHUFFW\",\"par\":\"XzRmFfhiVJMefUZdIJHTuwisxYFFa\",\"card_customer_key\":\"bdhibGCUDKtJudDmfkWGTIJbrcCjDaGYqqYumLJPsEmJFQFdECvyPdUfeYZjszqphVoZcjvWiGSxYlwHWkdNpYGeukXTZdOxdfiJxnJNxpBnKzoQOhXhWogHYzwGpDwCebNjwxhChIXFMlcAXnhdJBaAOfirqbXqGMSzruXAxdovIiUhpehJCiCTGzcKHBSAHQZUCZgauQGTRtaWeJOBkjsZDWXDGZjFuNTFsbDewcnATkykgzmljAblwOwlvL\",\"account_customer_key\":\"NJoUAXbPqcEPnLijMHHuPQImLYXMoakSLoAberYvEYetjrmZUKJGvufILeyKHiMUPujHlmKnIkbPHXHhMsZjcFTLSFhlRETVeVTYOuyNPxeRpYgRsnworLfhWspPAaJRnfYeiSgzPpRjyGEJzXtvZHEffrNEiGHNSWxqVwulCGTTXWnXlZIzsRPtHtsLbJOdyyxxtDOrLszwAMSVmQjOMadikNQGMdMfJvaQbxSqttmaJLYWBnaOUoCOiQIqzw\",\"status\":\"wppBUEaVquuZbknurTLXAMoCkRJWqAyrKVgXaBDFmbhCGDZCkCBYHDbOrDMbJli\",\"status_message\":\"XJTIErb\",\"termination_type\":\"rFEWJmrmnodWdjFfYRUIJvxmCmzGnxHOzvRzzRhhSAdDkFKoyIRHeWNRluGkhKr\",\"custom_data\":{\"OooxvQHWbtof\":\"m(yE<wejF7-<rwI]AYE%&[hDPxz7R\",\"GoYkmxzjmJzB\":25,\"BIGXTcOzTfeF\":false},\"time_elapsed\":1503225798,\"first_6\":\"xZNAfoVNbDQDNgphQlBxVYILRpijGOuv\",\"first_7\":\"HSmtrwxyHEijEIxMKiwlVbivwDZVlddN\",\"first_8\":\"oVqhalMPtBYZFBBZVcWafTDFurPgHjOn\",\"trace\":\"zOFsBcqahoOaHQBsmvorCHAcAvnZimOfdbwGVApTrPmGiPUmmsBLIAaAwlkjWLJSZqaJrgLfCtSVqKajezNHLDTmAssVjhGmdgDrIAKFYdmYNtFSiDPwHytSDxTQwbThTAQEooINGqFLpwezgzqfpNOafpXiMcWAGNGOoSdmsHWPbMoFzeBTLwMQjRnpHNWFieeUrdvuhwXZkjMzwVzMmREjUHuHGCWXlTquPFJHjlhsXQUkiLZtsxLnweyZgF\",\"place_card_on_single_site_job_id\":181777823,\"financial_institution_id\":193057576,\"merchant_site_id\":1814886620,\"email_sent\":true,\"completed_on\":\"1982-12-13T09:43:00.495Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/card_placement_results/
```

[Request hydration](## Request Hydration on POST) can be used on this endpoint. This allows you to create a new a card placement result and all referential entities at the same time.
merchant_site_hostname | string | no
meta_key | string | no
fi_name | string | yes
bank_identification_number | string | no
cuid | string | yes
par | string | no
card_customer_key | string | no
account_customer_key | string | no
status | string | no
status_message | string | no
termination_type | string | no
custom_data | object | no
time_elapsed | number | no
first_6 | string | no
first_7 | string | no
first_8 | string | no
trace | string | no
place_card_on_single_site_job_id | number | no
financial_institution_id | number | yes
merchant_site_id | number | yes
email_sent | boolean | no
completed_on | date | yes

See [card placement result response attributes](#response-card_placement_result).


## Update card placement result

```javascript
const cardplacementresult = await session.updateCardPlacementResult(1,{
  "merchant_site_hostname": "LaZNhTTxSPnXNzLqwrVXJjOsipfFnhPVsBvzaIgUUuDRnzILLLMcCVGWUpzTmnJsxqaYofWSqxJtZpFPbuEXPZgTGfgdFPPnnYamtDeRPOVFWAdYNAhORCCGLDpJINKRAdLPUGxtDrtUXFDvOhgynPueBAQxYxvPljFmCKBadWrBHUJBdaczwxqVmFZMGcuMbFMHWnLQwcLGsmyxcxkfDvliHadmIbEYfjVosOakOoBPWiqASxtcfKrKUdNZyf",
  "meta_key": "MB9810411",
  "fi_name": "CtzfUJUYcralTjXfqGNusrmFERySXvOAMmaMfywiwaSbNojQaehYaJyPQwgxTke",
  "bank_identification_number": "5816771",
  "cuid": "gefAEMiDzSJHOkRCgZABJjpxBaEveUoeKmXHunLJvNVNcdTljyrJhYPkcAYLfXqPfeywWTZwOtkZDCmabyxuKHYzYBJvPdiAXrjxCIZyceqQAIFExAmQnzBHzXRcvExjNLOjFywnZCJObHpqTKUDdcyGrgpSIQkpEUgstffcQYlcLnYEHUhGkaWVWZHbmLQWCwnvhfHcAuNnOIbhQlZosUZwccplnXJBmcgiYtPFUdzyFeRGcpchptNRQIxUZz",
  "par": "IJxkIxgUsduPrqDppiPndgUsMLiGq",
  "card_customer_key": "UsmRFlwPKRDwHjHsfdXNAjGgCDeZWfupeoSEgzIECNnqyuaeKuTetMjffkvqREzFBcquzDfABbZLCpCmPcYHjsWayAOdlwVPHuKopsqVsaxVSjQHYBHGSrIscsRZkIeEWxZzcHlOraxtZATovtfrNesIuuCnqffwOwoBZnGYrzqLWLOeTWwvxpzfxVaCslruLQmNKyideJGXHCWZPmggCXvWvgjMrubcQsaQBIYlXUNyoMTvZhTqGzFVOyeAzS",
  "account_customer_key": "TjgZDNMpbtNmVvVyyoMSMmIQFOLKXEccraIAnUSMZmTeXfgKcQLAOXJTrMLgUPIUfVEiimwrTxJzfBIILDnpGvImEVnTpyrQEGHinqZYhwzvQVCBIQuGlqQwFnOtglFueTofjjlysBhjHDhaOIRjUpgLlgEyKBcSxsSGiFBocixJLbFLYiPjLlWMVuSYcNYCRYttrLaBSZwQJYnWqtbHTnTJAHbrbQWCBekfJBqKievorjLrwBlIFwisdYmxWg",
  "status": "KSvRNLlpLIbHSCTQytbehJNkbKEaQRUQBCcilldtxdqyUgoPkCiOZpYRGUxbYXx",
  "status_message": "MySzHMiTEboELXgJMooQzWiNXEsUHTU",
  "termination_type": "PtBkdrjgxrissQnrNVTnZGAEDwEueXtSoMSqOUpIXtxFkGOoQBfNbYbNEPsnyDE",
  "custom_data": {
    "yOMROtjoYqUs": "{!DAKY7I+h/-M$",
    "dhrAeMIudPkZ": 11,
    "euISpLRauYjj": false
  },
  "time_elapsed": 1069098718,
  "first_6": "pGltrIeDlHsWqzTcWKOWGwHyRLFnYIBA",
  "first_7": "lHUceiDLnHRZxnOMjKfDHdAJQGgwsiEk",
  "first_8": "RifGKIQXzvPuTldcsDeWsTYnkrwMEyte",
  "trace": "qmYiscKSjPGrBMvvVEeKDmbDqyoERmpztZWGqjueGqJzrOdElWGGMSqiEWeewkUtwPZlCkGralTtSZsdXBEXJIvnRIFThVrYLIwSysOGuPrvvBXqoqxspECuEAmubgTGRFVTDpcRKskhyMefCsSOqgkxjBwmjxgiTePPbVVsAuChCHTCsKMrOGVCGQAuPqPvupIjxOiQtLqgFZPmKhsyGEBSXomSyKzxHUKTRFXIeqoNDmzmNvZRYtHKMmoDtT",
  "financial_institution_id": 891411696,
  "merchant_site_id": 1587245707,
  "email_sent": true,
  "completed_on": "2019-01-09T07:05:18.645Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "merchant_site_hostname", "LaZNhTTxSPnXNzLqwrVXJjOsipfFnhPVsBvzaIgUUuDRnzILLLMcCVGWUpzTmnJsxqaYofWSqxJtZpFPbuEXPZgTGfgdFPPnnYamtDeRPOVFWAdYNAhORCCGLDpJINKRAdLPUGxtDrtUXFDvOhgynPueBAQxYxvPljFmCKBadWrBHUJBdaczwxqVmFZMGcuMbFMHWnLQwcLGsmyxcxkfDvliHadmIbEYfjVosOakOoBPWiqASxtcfKrKUdNZyf" },
	{ "meta_key", "MB9810411" },
	{ "fi_name", "CtzfUJUYcralTjXfqGNusrmFERySXvOAMmaMfywiwaSbNojQaehYaJyPQwgxTke" },
	{ "bank_identification_number", "5816771" },
	{ "cuid", "gefAEMiDzSJHOkRCgZABJjpxBaEveUoeKmXHunLJvNVNcdTljyrJhYPkcAYLfXqPfeywWTZwOtkZDCmabyxuKHYzYBJvPdiAXrjxCIZyceqQAIFExAmQnzBHzXRcvExjNLOjFywnZCJObHpqTKUDdcyGrgpSIQkpEUgstffcQYlcLnYEHUhGkaWVWZHbmLQWCwnvhfHcAuNnOIbhQlZosUZwccplnXJBmcgiYtPFUdzyFeRGcpchptNRQIxUZz" },
	{ "par", "IJxkIxgUsduPrqDppiPndgUsMLiGq" },
	{ "card_customer_key", "UsmRFlwPKRDwHjHsfdXNAjGgCDeZWfupeoSEgzIECNnqyuaeKuTetMjffkvqREzFBcquzDfABbZLCpCmPcYHjsWayAOdlwVPHuKopsqVsaxVSjQHYBHGSrIscsRZkIeEWxZzcHlOraxtZATovtfrNesIuuCnqffwOwoBZnGYrzqLWLOeTWwvxpzfxVaCslruLQmNKyideJGXHCWZPmggCXvWvgjMrubcQsaQBIYlXUNyoMTvZhTqGzFVOyeAzS" },
	{ "account_customer_key", "TjgZDNMpbtNmVvVyyoMSMmIQFOLKXEccraIAnUSMZmTeXfgKcQLAOXJTrMLgUPIUfVEiimwrTxJzfBIILDnpGvImEVnTpyrQEGHinqZYhwzvQVCBIQuGlqQwFnOtglFueTofjjlysBhjHDhaOIRjUpgLlgEyKBcSxsSGiFBocixJLbFLYiPjLlWMVuSYcNYCRYttrLaBSZwQJYnWqtbHTnTJAHbrbQWCBekfJBqKievorjLrwBlIFwisdYmxWg" },
	{ "status", "KSvRNLlpLIbHSCTQytbehJNkbKEaQRUQBCcilldtxdqyUgoPkCiOZpYRGUxbYXx" },
	{ "status_message", "MySzHMiTEboELXgJMooQzWiNXEsUHTU" },
	{ "termination_type", "PtBkdrjgxrissQnrNVTnZGAEDwEueXtSoMSqOUpIXtxFkGOoQBfNbYbNEPsnyDE" },
	{ "time_elapsed", 1069098718 },
	{ "first_6", "pGltrIeDlHsWqzTcWKOWGwHyRLFnYIBA" },
	{ "first_7", "lHUceiDLnHRZxnOMjKfDHdAJQGgwsiEk" },
	{ "first_8", "RifGKIQXzvPuTldcsDeWsTYnkrwMEyte" },
	{ "trace", "qmYiscKSjPGrBMvvVEeKDmbDqyoERmpztZWGqjueGqJzrOdElWGGMSqiEWeewkUtwPZlCkGralTtSZsdXBEXJIvnRIFThVrYLIwSysOGuPrvvBXqoqxspECuEAmubgTGRFVTDpcRKskhyMefCsSOqgkxjBwmjxgiTePPbVVsAuChCHTCsKMrOGVCGQAuPqPvupIjxOiQtLqgFZPmKhsyGEBSXomSyKzxHUKTRFXIeqoNDmzmNvZRYtHKMmoDtT" },
	{ "financial_institution_id", 891411696 },
	{ "merchant_site_id", 1587245707 },
	{ "email_sent", true },
	{ "completed_on", "2019-01-09T07:05:18.645Z" }
};

CardSavrResponse<CardPlacementResult> cardplacementresult = await http.UpdateCardPlacementResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("merchant_site_hostname", "LaZNhTTxSPnXNzLqwrVXJjOsipfFnhPVsBvzaIgUUuDRnzILLLMcCVGWUpzTmnJsxqaYofWSqxJtZpFPbuEXPZgTGfgdFPPnnYamtDeRPOVFWAdYNAhORCCGLDpJINKRAdLPUGxtDrtUXFDvOhgynPueBAQxYxvPljFmCKBadWrBHUJBdaczwxqVmFZMGcuMbFMHWnLQwcLGsmyxcxkfDvliHadmIbEYfjVosOakOoBPWiqASxtcfKrKUdNZyf" )
	.add("meta_key", "MB9810411" )
	.add("fi_name", "CtzfUJUYcralTjXfqGNusrmFERySXvOAMmaMfywiwaSbNojQaehYaJyPQwgxTke" )
	.add("bank_identification_number", "5816771" )
	.add("cuid", "gefAEMiDzSJHOkRCgZABJjpxBaEveUoeKmXHunLJvNVNcdTljyrJhYPkcAYLfXqPfeywWTZwOtkZDCmabyxuKHYzYBJvPdiAXrjxCIZyceqQAIFExAmQnzBHzXRcvExjNLOjFywnZCJObHpqTKUDdcyGrgpSIQkpEUgstffcQYlcLnYEHUhGkaWVWZHbmLQWCwnvhfHcAuNnOIbhQlZosUZwccplnXJBmcgiYtPFUdzyFeRGcpchptNRQIxUZz" )
	.add("par", "IJxkIxgUsduPrqDppiPndgUsMLiGq" )
	.add("card_customer_key", "UsmRFlwPKRDwHjHsfdXNAjGgCDeZWfupeoSEgzIECNnqyuaeKuTetMjffkvqREzFBcquzDfABbZLCpCmPcYHjsWayAOdlwVPHuKopsqVsaxVSjQHYBHGSrIscsRZkIeEWxZzcHlOraxtZATovtfrNesIuuCnqffwOwoBZnGYrzqLWLOeTWwvxpzfxVaCslruLQmNKyideJGXHCWZPmggCXvWvgjMrubcQsaQBIYlXUNyoMTvZhTqGzFVOyeAzS" )
	.add("account_customer_key", "TjgZDNMpbtNmVvVyyoMSMmIQFOLKXEccraIAnUSMZmTeXfgKcQLAOXJTrMLgUPIUfVEiimwrTxJzfBIILDnpGvImEVnTpyrQEGHinqZYhwzvQVCBIQuGlqQwFnOtglFueTofjjlysBhjHDhaOIRjUpgLlgEyKBcSxsSGiFBocixJLbFLYiPjLlWMVuSYcNYCRYttrLaBSZwQJYnWqtbHTnTJAHbrbQWCBekfJBqKievorjLrwBlIFwisdYmxWg" )
	.add("status", "KSvRNLlpLIbHSCTQytbehJNkbKEaQRUQBCcilldtxdqyUgoPkCiOZpYRGUxbYXx" )
	.add("status_message", "MySzHMiTEboELXgJMooQzWiNXEsUHTU" )
	.add("termination_type", "PtBkdrjgxrissQnrNVTnZGAEDwEueXtSoMSqOUpIXtxFkGOoQBfNbYbNEPsnyDE" )
	.add("time_elapsed", 1069098718 )
	.add("first_6", "pGltrIeDlHsWqzTcWKOWGwHyRLFnYIBA" )
	.add("first_7", "lHUceiDLnHRZxnOMjKfDHdAJQGgwsiEk" )
	.add("first_8", "RifGKIQXzvPuTldcsDeWsTYnkrwMEyte" )
	.add("trace", "qmYiscKSjPGrBMvvVEeKDmbDqyoERmpztZWGqjueGqJzrOdElWGGMSqiEWeewkUtwPZlCkGralTtSZsdXBEXJIvnRIFThVrYLIwSysOGuPrvvBXqoqxspECuEAmubgTGRFVTDpcRKskhyMefCsSOqgkxjBwmjxgiTePPbVVsAuChCHTCsKMrOGVCGQAuPqPvupIjxOiQtLqgFZPmKhsyGEBSXomSyKzxHUKTRFXIeqoNDmzmNvZRYtHKMmoDtT" )
	.add("financial_institution_id", 891411696 )
	.add("merchant_site_id", 1587245707 )
	.add("email_sent", true )
	.add("completed_on", "2019-01-09T07:05:18.645Z" )
	.build();
JsonValue cardplacementresult = session.put("/card_placement_results", body, null, null);
```

```shell
curl -d "{\"merchant_site_hostname\":\"LaZNhTTxSPnXNzLqwrVXJjOsipfFnhPVsBvzaIgUUuDRnzILLLMcCVGWUpzTmnJsxqaYofWSqxJtZpFPbuEXPZgTGfgdFPPnnYamtDeRPOVFWAdYNAhORCCGLDpJINKRAdLPUGxtDrtUXFDvOhgynPueBAQxYxvPljFmCKBadWrBHUJBdaczwxqVmFZMGcuMbFMHWnLQwcLGsmyxcxkfDvliHadmIbEYfjVosOakOoBPWiqASxtcfKrKUdNZyf\",\"meta_key\":\"MB9810411\",\"fi_name\":\"CtzfUJUYcralTjXfqGNusrmFERySXvOAMmaMfywiwaSbNojQaehYaJyPQwgxTke\",\"bank_identification_number\":\"5816771\",\"cuid\":\"gefAEMiDzSJHOkRCgZABJjpxBaEveUoeKmXHunLJvNVNcdTljyrJhYPkcAYLfXqPfeywWTZwOtkZDCmabyxuKHYzYBJvPdiAXrjxCIZyceqQAIFExAmQnzBHzXRcvExjNLOjFywnZCJObHpqTKUDdcyGrgpSIQkpEUgstffcQYlcLnYEHUhGkaWVWZHbmLQWCwnvhfHcAuNnOIbhQlZosUZwccplnXJBmcgiYtPFUdzyFeRGcpchptNRQIxUZz\",\"par\":\"IJxkIxgUsduPrqDppiPndgUsMLiGq\",\"card_customer_key\":\"UsmRFlwPKRDwHjHsfdXNAjGgCDeZWfupeoSEgzIECNnqyuaeKuTetMjffkvqREzFBcquzDfABbZLCpCmPcYHjsWayAOdlwVPHuKopsqVsaxVSjQHYBHGSrIscsRZkIeEWxZzcHlOraxtZATovtfrNesIuuCnqffwOwoBZnGYrzqLWLOeTWwvxpzfxVaCslruLQmNKyideJGXHCWZPmggCXvWvgjMrubcQsaQBIYlXUNyoMTvZhTqGzFVOyeAzS\",\"account_customer_key\":\"TjgZDNMpbtNmVvVyyoMSMmIQFOLKXEccraIAnUSMZmTeXfgKcQLAOXJTrMLgUPIUfVEiimwrTxJzfBIILDnpGvImEVnTpyrQEGHinqZYhwzvQVCBIQuGlqQwFnOtglFueTofjjlysBhjHDhaOIRjUpgLlgEyKBcSxsSGiFBocixJLbFLYiPjLlWMVuSYcNYCRYttrLaBSZwQJYnWqtbHTnTJAHbrbQWCBekfJBqKievorjLrwBlIFwisdYmxWg\",\"status\":\"KSvRNLlpLIbHSCTQytbehJNkbKEaQRUQBCcilldtxdqyUgoPkCiOZpYRGUxbYXx\",\"status_message\":\"MySzHMiTEboELXgJMooQzWiNXEsUHTU\",\"termination_type\":\"PtBkdrjgxrissQnrNVTnZGAEDwEueXtSoMSqOUpIXtxFkGOoQBfNbYbNEPsnyDE\",\"custom_data\":{\"yOMROtjoYqUs\":\"{!DAKY7I+h/-M$\",\"dhrAeMIudPkZ\":11,\"euISpLRauYjj\":false},\"time_elapsed\":1069098718,\"first_6\":\"pGltrIeDlHsWqzTcWKOWGwHyRLFnYIBA\",\"first_7\":\"lHUceiDLnHRZxnOMjKfDHdAJQGgwsiEk\",\"first_8\":\"RifGKIQXzvPuTldcsDeWsTYnkrwMEyte\",\"trace\":\"qmYiscKSjPGrBMvvVEeKDmbDqyoERmpztZWGqjueGqJzrOdElWGGMSqiEWeewkUtwPZlCkGralTtSZsdXBEXJIvnRIFThVrYLIwSysOGuPrvvBXqoqxspECuEAmubgTGRFVTDpcRKskhyMefCsSOqgkxjBwmjxgiTePPbVVsAuChCHTCsKMrOGVCGQAuPqPvupIjxOiQtLqgFZPmKhsyGEBSXomSyKzxHUKTRFXIeqoNDmzmNvZRYtHKMmoDtT\",\"financial_institution_id\":891411696,\"merchant_site_id\":1587245707,\"email_sent\":true,\"completed_on\":\"2019-01-09T07:05:18.645Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/card_placement_results/683612158
```

### Path

PUT /card_placement_results OR /card_placement_results/{id}

### Description

Update a card placement result and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
merchant_site_hostname | string |
meta_key | string |
fi_name | string |
bank_identification_number | string |
cuid | string |
par | string |
card_customer_key | string |
account_customer_key | string |
status | string |
status_message | string |
termination_type | string |
custom_data | object |
time_elapsed | number |
first_6 | string |
first_7 | string |
first_8 | string |
trace | string |
financial_institution_id | number |
merchant_site_id | number |
email_sent | boolean |
completed_on | date |

See [card placement result response parameters](#response-card_placement_result).

# Cards
A card object contains information about a payment card for a specific cardholder. Card objects are used to populate payment information on merchant sites.
## Get card

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/cardsavr_cards/328290666
```

```javascript
const cards = await session.getCards(328290666,{"sort":"id","is_descending":true,"page":1, "page_length":25});
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(328290666,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

```java
JsonValue cards = session.get("/cardsavr_cards", 328290666,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 328290666,
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "sACpcnvxDzNzjgdcoKDASqzBIZxAYGwUvUCykEwnZdhyEIgfbxNsefmEwkndITOdDiRGwqdkSZbSCsghDyOhYrFgyDmfluINIsKwghbUrxIoKIYNCvALBHFEsVAmZNSTqqgLtLAfclowaQEShLUJOJXsNRJThYyutrgoKOzMoAsrmEMbGwXobMraZVJQhywDfihIApqsntoQIzTvLMamnEPXFpjXuhJYNdXrJTRcwmJwIrBZpMjELumDGlcKRe",
  "created_on": "1996-09-14T20:28:07.789Z",
  "last_updated_on": "2021-07-30T15:07:44.248Z",
  "cardholder": {
    "id": 1775253146,
    "financial_institution_id": 1609859662,
    "agent_session_id": "YyOvddPEoQrLRLjIYoEMSeZ",
    "type": "persistent",
    "first_name": "kzRfEnVJicaFwTMAyVfSqZPgAPDSi",
    "last_name": "XDmdXY",
    "email": "ajJAqBOwhoqk@rTLIch.MVI",
    "meta_key": "osceWYvchrN",
    "cardholder_safe_key": "T5lcps1ZsIR4s7OafG3OBM30rAXTg19gTu71WiGNifA=",
    "custom_data": {
      "yJZeGJhnDESH": "w,(y!8>)vU_yFnXy9Q0pj^u^<]wnDo=U",
      "DZDqImNpKbMw": 91,
      "EpzmEpzSMaAO": false
    },
    "created_on": "2018-03-09T13:29:09.044Z",
    "last_updated_on": "2017-09-16T06:58:05.751Z"
  },
  "cardsavr_address": {
    "id": 1979911147,
    "address1": "LBQAdghQNtxDsAGwTozTweyHSntLNMdHARjIdUgBcUtdiQOzGjuTVESuSrCmhzXBYYQlfeuivDDDqTRAqGQIyarMbMvoRGYRvBm",
    "address2": "FSuVtmeUAZcoFcxkbAngiFrMbWBdZEnXuSKfxWqhutIijvVYzozcRYGQYXAdiICGSKyoTunhlIFCxMbsDFhUoYcGpoqHaYnDOBU",
    "city": "bvUQpOqXhMoASOgKuskBaNFbezxnbZwxQBrmDrsaBBJmSIHIgTBWvyFQqKkaZOzDIhlKMahvbqxnFkMDtsTXvqnseITudNjMlaq",
    "subnational": "TWOYgyEpikBbTPQxxUzUeqtTFwHJDLeDykKfteasQANOUJksxpJaeDuRbcddPRX",
    "postal_code": "BLpSMfCMlggQkpzwEhWIuVXVjUygQyn",
    "postal_other": "SMrfEAcvFplhiTonFMDssTOfhCUVqCm",
    "country": "rcpTwbmcKGXGZkQfYlrDZgOnNhExjyTQouNlnnmMbBMuKvbvM",
    "is_primary": false,
    "first_name": "erZz",
    "last_name": "HuAncZVoFnaKwUpTYjPQbxekR",
    "email": "bxowusdTtXTW@QucMRu.tBC",
    "phone_number": "jMnZHUloHgIx",
    "created_on": "1982-08-19T01:43:08.113Z",
    "last_updated_on": "1998-11-21T01:58:05.552Z"
  },
  "cardsavr_bin": {
    "id": 1248324905,
    "financial_institution_id": 1423800246,
    "custom_data": {
      "AssMFGFISYSP": "#S~@zW%=x}}3~%[krt=FR",
      "XKdPBeQjgdel": 38,
      "cDidueaKjmFl": false
    },
    "created_on": "2001-12-02T04:59:28.363Z",
    "last_updated_on": "2013-12-02T02:48:44.520Z"
  },
  "par": "ABfcknWCqOlzSsDbFNaYIGfqgVBcd"
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

**Example GET request path:**<br>`/cardsavr_cards/328290666`

### <a name="response-cardsavr_card"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
bin_id | number (fk) | ID of BIN associated with this card.
expiration_month | string | 
expiration_year | string | 
name_on_card | string | 
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) | ID of cardholder associated with this card.
address_id | number (fk) | ID of address associated with this card.
par | string | Unique Personal Account Reference number for this card, to be used for card lookup. Generated automatically from PAN, expiration date, and username if using the SDK.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- cardholder_ids
- address_ids
- bin_ids
- pars
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create card

```javascript
const card = await session.createCard({
  "cardholder_id": 709604460,
  "address_id": 1291989370,
  "bin_id": 1304400985,
  "par": "ABfcknWCqOlzSsDbFNaYIGfqgVBcd",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "sACpcnvxDzNzjgdcoKDASqzBIZxAYGwUvUCykEwnZdhyEIgfbxNsefmEwkndITOdDiRGwqdkSZbSCsghDyOhYrFgyDmfluINIsKwghbUrxIoKIYNCvALBHFEsVAmZNSTqqgLtLAfclowaQEShLUJOJXsNRJThYyutrgoKOzMoAsrmEMbGwXobMraZVJQhywDfihIApqsntoQIzTvLMamnEPXFpjXuhJYNdXrJTRcwmJwIrBZpMjELumDGlcKRe"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 709604460 },
	{ "address_id", 1291989370 },
	{ "bin_id", 1304400985 },
	{ "par", "ABfcknWCqOlzSsDbFNaYIGfqgVBcd" },
	{ "pan", "4111111111111111" },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "sACpcnvxDzNzjgdcoKDASqzBIZxAYGwUvUCykEwnZdhyEIgfbxNsefmEwkndITOdDiRGwqdkSZbSCsghDyOhYrFgyDmfluINIsKwghbUrxIoKIYNCvALBHFEsVAmZNSTqqgLtLAfclowaQEShLUJOJXsNRJThYyutrgoKOzMoAsrmEMbGwXobMraZVJQhywDfihIApqsntoQIzTvLMamnEPXFpjXuhJYNdXrJTRcwmJwIrBZpMjELumDGlcKRe" }
};

CardSavrResponse<Card> card = await http.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 709604460 )
	.add("address_id", 1291989370 )
	.add("bin_id", 1304400985 )
	.add("par", "ABfcknWCqOlzSsDbFNaYIGfqgVBcd" )
	.add("pan", "4111111111111111" )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "sACpcnvxDzNzjgdcoKDASqzBIZxAYGwUvUCykEwnZdhyEIgfbxNsefmEwkndITOdDiRGwqdkSZbSCsghDyOhYrFgyDmfluINIsKwghbUrxIoKIYNCvALBHFEsVAmZNSTqqgLtLAfclowaQEShLUJOJXsNRJThYyutrgoKOzMoAsrmEMbGwXobMraZVJQhywDfihIApqsntoQIzTvLMamnEPXFpjXuhJYNdXrJTRcwmJwIrBZpMjELumDGlcKRe" )
	.build();
JsonValue card = session.post("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":709604460,\"address_id\":1291989370,\"bin_id\":1304400985,\"par\":\"ABfcknWCqOlzSsDbFNaYIGfqgVBcd\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"sACpcnvxDzNzjgdcoKDASqzBIZxAYGwUvUCykEwnZdhyEIgfbxNsefmEwkndITOdDiRGwqdkSZbSCsghDyOhYrFgyDmfluINIsKwghbUrxIoKIYNCvALBHFEsVAmZNSTqqgLtLAfclowaQEShLUJOJXsNRJThYyutrgoKOzMoAsrmEMbGwXobMraZVJQhywDfihIApqsntoQIzTvLMamnEPXFpjXuhJYNdXrJTRcwmJwIrBZpMjELumDGlcKRe\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/
```

[Request hydration](## Request Hydration on POST) can be used on this endpoint. This allows you to create a new a card and all referential entities at the same time.
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

## Upsert card

```javascript
const card = await session.updateCard(1,{
  "bin_id": 1297693022,
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "ZHdYNZBVAqMymYsohiKTveiKKOoMoXLjUnnTDLroGdwUXcDZHPFEGOAtYarayCbgtUUqrDGKjOeoKFGjdeREtfzcJUWMnPygJSAIeFDnvzUgUDWNoykrptwacsMvahFpwfpmgAUkhPPvULNYKvupQxBjkUAOEleJZlqDpQynZrqxsXhMVBSUuavxZJoWpYPZEtLTMFIrrbqLatxGjtsveCfpWaZoIDooyDeZpyNqfNLqlAGONkHvxvtxxguuWI",
  "pan": "4111111111111111"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "bin_id", 1297693022 },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "ZHdYNZBVAqMymYsohiKTveiKKOoMoXLjUnnTDLroGdwUXcDZHPFEGOAtYarayCbgtUUqrDGKjOeoKFGjdeREtfzcJUWMnPygJSAIeFDnvzUgUDWNoykrptwacsMvahFpwfpmgAUkhPPvULNYKvupQxBjkUAOEleJZlqDpQynZrqxsXhMVBSUuavxZJoWpYPZEtLTMFIrrbqLatxGjtsveCfpWaZoIDooyDeZpyNqfNLqlAGONkHvxvtxxguuWI" },
	{ "pan", "4111111111111111" }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("bin_id", 1297693022 )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "ZHdYNZBVAqMymYsohiKTveiKKOoMoXLjUnnTDLroGdwUXcDZHPFEGOAtYarayCbgtUUqrDGKjOeoKFGjdeREtfzcJUWMnPygJSAIeFDnvzUgUDWNoykrptwacsMvahFpwfpmgAUkhPPvULNYKvupQxBjkUAOEleJZlqDpQynZrqxsXhMVBSUuavxZJoWpYPZEtLTMFIrrbqLatxGjtsveCfpWaZoIDooyDeZpyNqfNLqlAGONkHvxvtxxguuWI" )
	.add("pan", "4111111111111111" )
	.build();
JsonValue card = session.put("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"bin_id\":1297693022,\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"ZHdYNZBVAqMymYsohiKTveiKKOoMoXLjUnnTDLroGdwUXcDZHPFEGOAtYarayCbgtUUqrDGKjOeoKFGjdeREtfzcJUWMnPygJSAIeFDnvzUgUDWNoykrptwacsMvahFpwfpmgAUkhPPvULNYKvupQxBjkUAOEleJZlqDpQynZrqxsXhMVBSUuavxZJoWpYPZEtLTMFIrrbqLatxGjtsveCfpWaZoIDooyDeZpyNqfNLqlAGONkHvxvtxxguuWI\",\"pan\":\"4111111111111111\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/328290666
```

### Path

PUT /cardsavr_cards OR /cardsavr_cards/{id}

### Description

Upsert can be used to either update a card, create a new card, or return an existing card.  Either an id or PAR is required for upsert. The id (in path or body), along with an updated body, can be used to update an existing card; the PAR (in body) can likewise be used to update a card, and can also be used to create a new card, if the PAR does not match any existing cards. If the id or PAR provided corresponds to a pre-existing card and no updated information has been included in the body, the existing card will be returned.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
bin_id | number |
cvv | string |
expiration_month | string |
expiration_year | string |
name_on_card | string |

See [card response parameters](#response-cardsavr_card).


## Delete card

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/328290666
```

```javascript
await session.deleteCard(undefined);
```

```csharp
CardSavrResponse<Card> card = await http.DeleteCardAsync(undefined);
```

```java
JsonValue card = session.delete("/cardsavr_cards", undefined, null);
```

### Path

DELETE /cardsavr_cards/{id}

### Description

Delete a card and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [card response parameters](#response-cardsavr_card).


# Cardholders
Cardholders are the end-users of the CardSavr API, who can have their their payment information updated on merchant site(s). Cardholders can be linked to cards, accounts, and addresses.
## Get cardholder

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/cardholders/273466249
```

```javascript
const cardholders = await session.getCardholders(273466249,{"sort":"id","is_descending":true,"page":1, "page_length":25});
```

```csharp
CardSavrResponse<Cardholders> cardholders = await session.GetCardholdersAsync(273466249,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

```java
JsonValue cardholders = session.get("/cardholders", 273466249,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 273466249,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "mVMkfxwdQAhyzyvgmkLPitvpnAWij",
  "custom_data": {
    "iYKBVesAPmKo": "54dB4{!sw2WkFj*#0/W]Noke*fmA<k",
    "PcOFscZvcyym": 43,
    "GofWIzovpLTM": true
  },
  "created_on": "2002-12-05T18:17:53.857Z",
  "last_updated_on": "2005-02-21T13:51:31.594Z",
  "cuid": "NVmbeuqdj",
  "financial_institution": {
    "id": 51766725,
    "name": "XsRxQvxfJzdvvuwlFICfIQMCxxDyZsyfINBaDUYtcrXULwoQUdTHvsGVwRcfnjZ",
    "description": "MLacSmLYHShQj",
    "lookup_key": "QBqTDARYDfzGzHVoSGlPxtAkWTVtMrfMQiyPBSyHNqKjTEGlitAqBsLujjLWEew",
    "alternate_lookup_key": "uJtRLHIuDrFVyIePagLcyNpLCWPomhoIFUjwcYafctkyFmUSoISywopudfSLMAh",
    "config": {
      "ydHvvchYShVH": "PVR5<J",
      "qHFFKPAderAv": 93,
      "ogdQLvvnjCdl": true
    },
    "created_on": "1983-09-08T04:17:34.463Z",
    "last_updated_on": "2016-01-13T02:27:55.457Z"
  }
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

**Example GET request path:**<br>`/cardholders/273466249`

### <a name="response-cardholder"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
financial_institution_id | number (fk) | 
first_name | string | 
last_name | string | 
email | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
custom_data | object | Additional data that can be added to the cardholder if needed.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cuid | string | Unique ID for cardholder--can be email address, phone number, etc.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- financial_institution_ids
- cuid
- first_name
- last_name
- email
- meta_key
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create cardholder

```javascript
const cardholder = await session.createCardholder({
  "cuid": "NVmbeuqdj",
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "mVMkfxwdQAhyzyvgmkLPitvpnAWij",
  "custom_data": {
    "iYKBVesAPmKo": "54dB4{!sw2WkFj*#0/W]Noke*fmA<k",
    "PcOFscZvcyym": 43,
    "GofWIzovpLTM": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cuid", "NVmbeuqdj" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "mVMkfxwdQAhyzyvgmkLPitvpnAWij" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cuid", "NVmbeuqdj" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "mVMkfxwdQAhyzyvgmkLPitvpnAWij" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"cuid\":\"NVmbeuqdj\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"mVMkfxwdQAhyzyvgmkLPitvpnAWij\",\"custom_data\":{\"iYKBVesAPmKo\":\"54dB4{!sw2WkFj*#0/W]Noke*fmA<k\",\"PcOFscZvcyym\":43,\"GofWIzovpLTM\":true}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/
```

[Request hydration](## Request Hydration on POST) can be used on this endpoint. This allows you to create a new a cardholder and all referential entities at the same time.
cuid | string | yes
first_name | string | no
last_name | string | no
email | string | no
meta_key | string | no
custom_data | object | no

See [cardholder response attributes](#response-cardholder).


## Upsert cardholder

```javascript
const cardholder = await session.updateCardholder(1,{
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "icFeHyKbr",
  "custom_data": {
    "gJYWNevNdxHz": "fhJISFJdMEnV}v&].*H>eMvsQE!d!",
    "UUbgfVDiJXYg": 54,
    "auVPdRBMLyLs": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "icFeHyKbr" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "icFeHyKbr" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"icFeHyKbr\",\"custom_data\":{\"gJYWNevNdxHz\":\"fhJISFJdMEnV}v&].*H>eMvsQE!d!\",\"UUbgfVDiJXYg\":54,\"auVPdRBMLyLs\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/273466249
```

### Path

PUT /cardholders OR /cardholders/{id}

### Description

Upsert can be used to either update a cardholder, create a new cardholder, or return an existing cardholder.  Either an id or cuid is required for upsert. The id (in path or body), along with an updated body, can be used to update an existing cardholder; the cuid (in body) can likewise be used to update a cardholder, and can also be used to create a new cardholder, if the cuid does not match any existing cardholders. If the id or cuid provided corresponds to a pre-existing cardholder and no updated information has been included in the body, the existing cardholder will be returned.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
first_name | string |
last_name | string |
email | string |
meta_key | string |
custom_data | object |

See [cardholder response parameters](#response-cardholder).


## Delete cardholder

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/273466249
```

```javascript
await session.deleteCardholder(undefined);
```

```csharp
CardSavrResponse<Cardholder> cardholder = await http.DeleteCardholderAsync(undefined);
```

```java
JsonValue cardholder = session.delete("/cardholders", undefined, null);
```

### Path

DELETE /cardholders/{id}

### Description

Delete a cardholder and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [cardholder response parameters](#response-cardholder).


# Users
Users are internal entities, such as agents or admins, that can perform such functions as creating and deleting cardholders, fetching merchant sites, creating jobs, etc.
## Get user

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/cardsavr_users/1958220431
```

```javascript
const users = await session.getUsers(1958220431,{"sort":"id","is_descending":true,"page":1, "page_length":25});
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(1958220431,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

```java
JsonValue users = session.get("/cardsavr_users", 1958220431,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1958220431,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "2007-12-17T07:36:22.154Z",
  "is_locked": true,
  "password_lifetime": 221,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_agent",
  "next_rotation_on": "2019-01-30T16:05:58.626Z",
  "created_on": "2018-08-05T22:00:11.854Z",
  "last_updated_on": "1982-09-14T02:41:16.129Z",
  "financial_institution": {
    "id": 1597527929,
    "name": "XnXLUKhYmfsanxVmDoatvXonWgcjPPEqRSMqxNOeghDozXQMcHUrVMdAAkcWwVM",
    "description": "B",
    "lookup_key": "XOjDsOmcswVySwwjebplESmNneLBuAhMBVyevmsJdqtTkSNdcqxjMHkkFyWbqbM",
    "alternate_lookup_key": "rtelpETrBfHWzPNieKpEVpReBulvKlWtKhtLQKIqxvphNRdpJeYaoLcfYjWoyCc",
    "config": {
      "BVZCYmYKTExJ": "G%,bDh(VRI+4H&@W[B%$6.J7u0T%",
      "wRhYnwvNTMlx": 11,
      "JRuTlqcmihcW": false
    },
    "created_on": "2006-01-29T19:04:50.216Z",
    "last_updated_on": "2013-06-22T06:41:09.647Z"
  },
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

**Example GET request path:**<br>`/cardsavr_users/1958220431`

### <a name="response-cardsavr_user"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
financial_institution_id | number (fk) | 
first_name | string | 
last_name | string | 
last_login_time | date | 
is_locked | boolean | 
password_lifetime | number | Length of time that password will remain valid.
email | string | 
is_password_update_required | boolean | 
role | string | User role (cardholder_agent or customer_agent) determines the user's ability to access certain endpoints and perform certain operations within the CardSavr API. 
cardholder_agents can create cardholders, create cards addresses for those cardholders, create accounts for those cardholders, and post jobs for those cardholders.
customer_agents can peform all actions on cardholders/accounts/, but are limited to acting on cardholders/jobs/accounts/cards within their FI (unless they are assigned to the admin FI)
next_rotation_on | date | Date of next password rotation for this user.
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
  "financial_institution_id": 1617887698,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 221,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_agent",
  "next_rotation_on": "2019-01-30T16:05:58.626Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1617887698 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 221 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "swch_agent" },
	{ "next_rotation_on", "2019-01-30T16:05:58.626Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1617887698 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 221 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "swch_agent" )
	.add("next_rotation_on", "2019-01-30T16:05:58.626Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1617887698,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":221,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"swch_agent\",\"next_rotation_on\":\"2019-01-30T16:05:58.626Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/
```

[Request hydration](## Request Hydration on POST) can be used on this endpoint. This allows you to create a new a user and all referential entities at the same time.
financial_institution_id | number | no
username | string | yes
password | string | yes
first_name | string | no
last_name | string | no
password_lifetime | number | no
email | string | no
is_password_update_required | boolean | no
role | [string enum](#post-cardsavr_user-1)* | yes
next_rotation_on | date | no

See [user response attributes](#response-cardsavr_user).

#### <a name="post-cardsavr_user-1"></a>string enum*
- admin
- cardholder_agent
- customer_agent
- swch_agent


## Update user

```javascript
const user = await session.updateUser(1,{
  "financial_institution_id": 1124733326,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 1,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "customer_agent",
  "next_rotation_on": "1972-05-17T21:44:05.978Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1124733326 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 1 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "customer_agent" },
	{ "next_rotation_on", "1972-05-17T21:44:05.978Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1124733326 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 1 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "customer_agent" )
	.add("next_rotation_on", "1972-05-17T21:44:05.978Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1124733326,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":1,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"customer_agent\",\"next_rotation_on\":\"1972-05-17T21:44:05.978Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/1958220431
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
next_rotation_on | date |

See [user response parameters](#response-cardsavr_user).


## Delete user

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/1958220431
```

```javascript
await session.deleteUser(undefined);
```

```csharp
CardSavrResponse<User> user = await http.DeleteUserAsync(undefined);
```

```java
JsonValue user = session.delete("/cardsavr_users", undefined, null);
```

### Path

DELETE /cardsavr_users/{id}

### Description

Delete a user and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [user response parameters](#response-cardsavr_user).


# Financial Institutions
Financial Institution (FI) objects represent individual FIs and can be linked to users and cardholders. They also contain the configuration information that can be used to customize an FI's CardUpdatr instance, if one exists.
## Get financial institution

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/financial_institutions/525675448
```

```javascript
const financialinstitutions = await session.getFinancialInstitutions(525675448,{"sort":"id","is_descending":true,"page":1, "page_length":25});
```

```csharp
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(525675448,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

```java
JsonValue financialinstitutions = session.get("/financial_institutions", 525675448,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 525675448,
  "name": "XraqvnWCBiBCRuLCLdcQxRflVGVDicVNiBAXCLbQMDjxfHBXyZCdVQJylPtCiCS",
  "description": "ZduDQURNEZUJKGVEpqRYcFCbcMpp",
  "lookup_key": "vWHcWLLPyHeQxwXfTeLnFNWnvfqsnPbJKdrVuICESabJjfmfFNBrWwiUfihxhRf",
  "alternate_lookup_key": "GmCQgOaqlqAmFeDfRbUogMPltlRorgiatqChNIxlyYIFzzBtLHZFXUrzFMjWvLW",
  "created_on": "2000-11-22T22:55:05.760Z",
  "last_updated_on": "2010-10-06T02:30:48.000Z"
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

**Example GET request path:**<br>`/financial_institutions/525675448`

### <a name="response-financial_institution"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
name | string | 
description | string | 
lookup_key | string | Unique key used to identify financial institution.
alternate_lookup_key | string | Alternate lookup key; can be used in case of FI name change that does not match original lookup_key, in order to maintain backwards compatibility.
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
  "name": "XraqvnWCBiBCRuLCLdcQxRflVGVDicVNiBAXCLbQMDjxfHBXyZCdVQJylPtCiCS",
  "description": "ZduDQURNEZUJKGVEpqRYcFCbcMpp",
  "lookup_key": "vWHcWLLPyHeQxwXfTeLnFNWnvfqsnPbJKdrVuICESabJjfmfFNBrWwiUfihxhRf",
  "alternate_lookup_key": "GmCQgOaqlqAmFeDfRbUogMPltlRorgiatqChNIxlyYIFzzBtLHZFXUrzFMjWvLW"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "XraqvnWCBiBCRuLCLdcQxRflVGVDicVNiBAXCLbQMDjxfHBXyZCdVQJylPtCiCS" },
	{ "description", "ZduDQURNEZUJKGVEpqRYcFCbcMpp" },
	{ "lookup_key", "vWHcWLLPyHeQxwXfTeLnFNWnvfqsnPbJKdrVuICESabJjfmfFNBrWwiUfihxhRf" },
	{ "alternate_lookup_key", "GmCQgOaqlqAmFeDfRbUogMPltlRorgiatqChNIxlyYIFzzBtLHZFXUrzFMjWvLW" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "XraqvnWCBiBCRuLCLdcQxRflVGVDicVNiBAXCLbQMDjxfHBXyZCdVQJylPtCiCS" )
	.add("description", "ZduDQURNEZUJKGVEpqRYcFCbcMpp" )
	.add("lookup_key", "vWHcWLLPyHeQxwXfTeLnFNWnvfqsnPbJKdrVuICESabJjfmfFNBrWwiUfihxhRf" )
	.add("alternate_lookup_key", "GmCQgOaqlqAmFeDfRbUogMPltlRorgiatqChNIxlyYIFzzBtLHZFXUrzFMjWvLW" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"XraqvnWCBiBCRuLCLdcQxRflVGVDicVNiBAXCLbQMDjxfHBXyZCdVQJylPtCiCS\",\"description\":\"ZduDQURNEZUJKGVEpqRYcFCbcMpp\",\"lookup_key\":\"vWHcWLLPyHeQxwXfTeLnFNWnvfqsnPbJKdrVuICESabJjfmfFNBrWwiUfihxhRf\",\"alternate_lookup_key\":\"GmCQgOaqlqAmFeDfRbUogMPltlRorgiatqChNIxlyYIFzzBtLHZFXUrzFMjWvLW\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/
```

[Request hydration](## Request Hydration on POST) can be used on this endpoint. This allows you to create a new a financial institution and all referential entities at the same time.
name | string | yes
description | string | no
lookup_key | string | yes
alternate_lookup_key | string | no

See [financial institution response attributes](#response-financial_institution).


## Update financial institution

```javascript
const financialinstitution = await session.updateFinancialInstitution(1,{
  "name": "WfiQcfmGiHnAYjzlyqEtYXeVMpuNyQXFQYORZnIgwPXoRHJaquoapPJBWZPgTSi",
  "description": "bzHCnREIezrtP",
  "lookup_key": "fdefIgkpmciigoTsXusfbFFMqjWcpTvNPGpxvzQBMghcxgZiJyaBvRhbUYIUKqN",
  "alternate_lookup_key": "upyBrmFIadmWNPlyuimScZaMdaFfnXjFUjrWOSSPHrXsFgCqsTzQUXosaWBAsBA"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "WfiQcfmGiHnAYjzlyqEtYXeVMpuNyQXFQYORZnIgwPXoRHJaquoapPJBWZPgTSi" },
	{ "description", "bzHCnREIezrtP" },
	{ "lookup_key", "fdefIgkpmciigoTsXusfbFFMqjWcpTvNPGpxvzQBMghcxgZiJyaBvRhbUYIUKqN" },
	{ "alternate_lookup_key", "upyBrmFIadmWNPlyuimScZaMdaFfnXjFUjrWOSSPHrXsFgCqsTzQUXosaWBAsBA" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "WfiQcfmGiHnAYjzlyqEtYXeVMpuNyQXFQYORZnIgwPXoRHJaquoapPJBWZPgTSi" )
	.add("description", "bzHCnREIezrtP" )
	.add("lookup_key", "fdefIgkpmciigoTsXusfbFFMqjWcpTvNPGpxvzQBMghcxgZiJyaBvRhbUYIUKqN" )
	.add("alternate_lookup_key", "upyBrmFIadmWNPlyuimScZaMdaFfnXjFUjrWOSSPHrXsFgCqsTzQUXosaWBAsBA" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"WfiQcfmGiHnAYjzlyqEtYXeVMpuNyQXFQYORZnIgwPXoRHJaquoapPJBWZPgTSi\",\"description\":\"bzHCnREIezrtP\",\"lookup_key\":\"fdefIgkpmciigoTsXusfbFFMqjWcpTvNPGpxvzQBMghcxgZiJyaBvRhbUYIUKqN\",\"alternate_lookup_key\":\"upyBrmFIadmWNPlyuimScZaMdaFfnXjFUjrWOSSPHrXsFgCqsTzQUXosaWBAsBA\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/525675448
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
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/525675448
```

```javascript
await session.deleteFinancialInstitution(undefined);
```

```csharp
CardSavrResponse<FinancialInstitution> financialinstitution = await http.DeleteFinancialInstitutionAsync(undefined);
```

```java
JsonValue financialinstitution = session.delete("/financial_institutions", undefined, null);
```

### Path

DELETE /financial_institutions/{id}

### Description

Delete a financial institution and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [financial institution response parameters](#response-financial_institution).


# Integrators
Integrators are applications that integrate the CardSavr API, using their own unique integrator key. An integrator name and key are required for all calls to the CardSavr API. An integrator can be associated with multiple users.
## Get integrator

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/integrators/1322762553
```

```javascript
const integrators = await session.getIntegrators(1322762553,{"sort":"id","is_descending":true,"page":1, "page_length":25});
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(1322762553,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

```java
JsonValue integrators = session.get("/integrators", 1322762553,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1322762553,
  "name": "tSLVVuHkjhHhRYmxZMNGZWCMwTXqnbQefxFggiKoKCYCcRAuo",
  "description": "QJqzBrvDzHgNaWiYWmMcFwn",
  "current_key": "LwJ6c9CtSZsURUR6VBZ/s4zZLsqkdUn/wDJPjbeCvAo=",
  "key_lifetime": 252,
  "next_rotation_on": "1999-01-05T23:57:53.189Z",
  "created_on": "1978-10-20T19:21:32.608Z",
  "last_updated_on": "1986-07-14T22:23:42.575Z"
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

**Example GET request path:**<br>`/integrators/1322762553`

### <a name="response-integrator"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | An integrator's unique identifier
name | string | Name of integrator.
description | string | 
current_key | string | Current key for this integrator.
key_lifetime | number | Sets the duration of validity for integrator key.
next_rotation_on | date | Date of next key rotation for this integrator.
created_on | date | Date this integrator was created on
last_updated_on | date | Date this integrator was last updated on

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- names
- name
- next_rotation_on_min / next_rotation_on_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create integrator

```javascript
const integrator = await session.createIntegrator({
  "name": "tSLVVuHkjhHhRYmxZMNGZWCMwTXqnbQefxFggiKoKCYCcRAuo",
  "description": "QJqzBrvDzHgNaWiYWmMcFwn",
  "current_key": "LwJ6c9CtSZsURUR6VBZ/s4zZLsqkdUn/wDJPjbeCvAo=",
  "key_lifetime": 252,
  "next_rotation_on": "1999-01-05T23:57:53.189Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "tSLVVuHkjhHhRYmxZMNGZWCMwTXqnbQefxFggiKoKCYCcRAuo" },
	{ "description", "QJqzBrvDzHgNaWiYWmMcFwn" },
	{ "current_key", "LwJ6c9CtSZsURUR6VBZ/s4zZLsqkdUn/wDJPjbeCvAo=" },
	{ "key_lifetime", 252 },
	{ "next_rotation_on", "1999-01-05T23:57:53.189Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "tSLVVuHkjhHhRYmxZMNGZWCMwTXqnbQefxFggiKoKCYCcRAuo" )
	.add("description", "QJqzBrvDzHgNaWiYWmMcFwn" )
	.add("current_key", "LwJ6c9CtSZsURUR6VBZ/s4zZLsqkdUn/wDJPjbeCvAo=" )
	.add("key_lifetime", 252 )
	.add("next_rotation_on", "1999-01-05T23:57:53.189Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"tSLVVuHkjhHhRYmxZMNGZWCMwTXqnbQefxFggiKoKCYCcRAuo\",\"description\":\"QJqzBrvDzHgNaWiYWmMcFwn\",\"current_key\":\"LwJ6c9CtSZsURUR6VBZ/s4zZLsqkdUn/wDJPjbeCvAo=\",\"key_lifetime\":252,\"next_rotation_on\":\"1999-01-05T23:57:53.189Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/
```

[Request hydration](## Request Hydration on POST) can be used on this endpoint. This allows you to create a new a integrator and all referential entities at the same time.
name | string | yes
description | string | no
current_key | string | no
key_lifetime | number | no
next_rotation_on | date | no

See [integrator response attributes](#response-integrator).


## Update integrator

```javascript
const integrator = await session.updateIntegrator(1,{
  "name": "wAueKDIyCacCEdUkqoYDQoQivZMxxBWFUIaojZQbGnFgJLnAX",
  "description": "sHrBdABWv",
  "current_key": "djYPzkRahmdj5fk/FElMH7EW32G/x4Fldyt80rCctRE=",
  "key_lifetime": 7,
  "next_rotation_on": "2005-04-05T21:35:48.315Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "wAueKDIyCacCEdUkqoYDQoQivZMxxBWFUIaojZQbGnFgJLnAX" },
	{ "description", "sHrBdABWv" },
	{ "current_key", "djYPzkRahmdj5fk/FElMH7EW32G/x4Fldyt80rCctRE=" },
	{ "key_lifetime", 7 },
	{ "next_rotation_on", "2005-04-05T21:35:48.315Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "wAueKDIyCacCEdUkqoYDQoQivZMxxBWFUIaojZQbGnFgJLnAX" )
	.add("description", "sHrBdABWv" )
	.add("current_key", "djYPzkRahmdj5fk/FElMH7EW32G/x4Fldyt80rCctRE=" )
	.add("key_lifetime", 7 )
	.add("next_rotation_on", "2005-04-05T21:35:48.315Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"wAueKDIyCacCEdUkqoYDQoQivZMxxBWFUIaojZQbGnFgJLnAX\",\"description\":\"sHrBdABWv\",\"current_key\":\"djYPzkRahmdj5fk/FElMH7EW32G/x4Fldyt80rCctRE=\",\"key_lifetime\":7,\"next_rotation_on\":\"2005-04-05T21:35:48.315Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/1322762553
```

### Path

PUT /integrators OR /integrators/{id}

### Description

Update a integrator and return the updated object.  An id is required on every update request.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
name | string |
description | string |
current_key | string |
key_lifetime | number |
next_rotation_on | date |

See [integrator response parameters](#response-integrator).


## Delete integrator

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/1322762553
```

```javascript
await session.deleteIntegrator(undefined);
```

```csharp
CardSavrResponse<Integrator> integrator = await http.DeleteIntegratorAsync(undefined);
```

```java
JsonValue integrator = session.delete("/integrators", undefined, null);
```

### Path

DELETE /integrators/{id}

### Description

Delete a integrator and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [integrator response parameters](#response-integrator).


# Merchant sites
A merchant site object contains information, such as images URLs and hostname, for a CardSavr-supported merchant site.
## Get merchant site

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/merchant_sites/1374420639
```

```javascript
const merchantsites = await session.getMerchantSites(1374420639,{"sort":"id","is_descending":true,"page":1, "page_length":25});
```

```csharp
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(1374420639,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

```java
JsonValue merchantsites = session.get("/merchant_sites", 1374420639,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1374420639,
  "name": "Amazon",
  "host": "amazon.com",
  "tags": [
    "kC$m[Yt.Y",
    29,
    "t.LWjqKDZ!*jKZyb"
  ],
  "required_form_fields": [
    "email",
    "phone_number",
    "card_data",
    "cvv",
    "billing_address",
    "postal_code"
  ],
  "images": [
    {
      "url": "https://d1t7g1oas7m24a.cloudfront.net/tiles/dollarshaveclub.com?width=128&version=21f917315911eec1b1705bc7784ce861579cff2b",
      "width": 128,
      "grayscale": false
    },
    {
      "url": "https://d1t7g1oas7m24a.cloudfront.net/tiles/dollarshaveclub.com?width=32&version=21f917315911eec1b1705bc7784ce861579cff2b",
      "width": 32,
      "grayscale": false
    }
  ],
  "account_identification": {
    "kCXAjHkEqpam": "Yaas6u8(te9*>5UJi",
    "GuKeqSAZRMzJ": 70,
    "bxzifUrffSMo": true
  },
  "mfa": false,
  "credit_card_page": "https://www.merchantsite.com/credit_card",
  "forgot_password_page": "https://www.merchantsite.com/forgot_password",
  "login_page": "https://www.merchantsite.com/login",
  "login": {
    "username_label": "Username/Email",
    "password_label": "Password",
    "mfa_label": "Additional information required, this code may be sent to your phone or email address.",
    "additional_info_message": "",
    "auth_message": "Linking account."
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

**Example GET request path:**<br>`/merchant_sites/1374420639`

### <a name="response-merchant_site"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
name | string | 
host | string | e.g. amazon.com
tags | array | Tags for use by front-end, such as development.
required_form_fields | array | Indicates the cardholder personal information fields that are required by this site.
images | array | URLs of the images for this merchant site.
account_identification | object | The identification credentials required to authenticate with merchant site (i.e. username/password or phone number/password)
mfa | boolean | Indicates if this site is MFA-enabled.
credit_card_page | string | Merchant's credit card entry page.
forgot_password_page | string | Merchant's forgotten password page.
login_page | string | URL of login page.
login | object | 

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
Notification objects define a set of actions to be triggered by certain CardSavr events, such as session completion.
## Get notification

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/notifications/1026804810
```

```javascript
const notifications = await session.getNotifications(1026804810,{"sort":"id","is_descending":true,"page":1, "page_length":25});
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(1026804810,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

```java
JsonValue notifications = session.get("/notifications", 1026804810,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1026804810,
  "name": "Sample Notification",
  "type": "email",
  "event": "webhook_error_summary",
  "config": {
    "recipient": "cardholder",
    "url": null,
    "from_email": "CardUpdatr <no-reply@cardupdatr.app>",
    "return_path": "no-reply@cardupdatr.app",
    "send_email_time": null,
    "interval_length": null,
    "interval_type": null
  },
  "html_template": "wHggyBauJXfesVGTJXbdizJvlOM",
  "text_template": "KgxiYEHsNmnNcRDwxGxvFL",
  "created_on": "1973-04-27T06:17:46.899Z",
  "last_updated_on": "2004-01-01T08:39:19.459Z",
  "financial_institution": {
    "id": 940737157,
    "name": "HtZaxQoRtdQUAKzrsUMFGNFAurrauDWFeYdAKRlWxNOJbUgRAHshLhtUqtLMCzW",
    "description": "ZNSyNvSOaHSKKPIGPgWkvEC",
    "lookup_key": "ssRTbnkgVnhvRrwfGWzpHmvlHvNFVthzCbfBWcFlsUrPEZktlVEIIQiNtHXuRmC",
    "alternate_lookup_key": "mwrropNWTfKkYbvjVQogeFwcZIuPClggdWacpoSWcJUfxuPbLapMwtAgoiZEDxe",
    "config": {
      "tCXvDvCxNRIC": "Z.J5y9Km/DOJ*nS4(k&]2OgqqEp%",
      "TnIXtJqfiSEr": 0,
      "mIvArMbpQVia": false
    },
    "created_on": "1977-05-03T18:25:34.442Z",
    "last_updated_on": "1975-05-20T11:29:33.868Z"
  }
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

**Example GET request path:**<br>`/notifications/1026804810`

### <a name="response-notification"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
name | string | Name of this notification.
type | string | Notification type (e.g. webhook or email).
event | string | Event that will triger the notification (e.g. session complete).
config | object | 
html_template | string | Overrides the default CardUpdatr html email template (for email notifications).
text_template | string | Overrides the default CardUpdatr text email template (for email notifications).
created_on | date | Date this notification was created on
last_updated_on | date | Date this notification was last updated on
financial_institution_id | number (fk) | ID of the financial institution associated with this notification.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- financial_institution_ids
- names
- type
- events
- event
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create notification

```javascript
const notification = await session.createNotification({
  "financial_institution_id": 2108986725,
  "name": "Sample Notification",
  "type": "email",
  "event": "webhook_error_summary",
  "config": {
    "recipient": "cardholder",
    "url": null,
    "from_email": "CardUpdatr <no-reply@cardupdatr.app>",
    "return_path": "no-reply@cardupdatr.app",
    "send_email_time": null,
    "interval_length": null,
    "interval_type": null
  },
  "html_template": "wHggyBauJXfesVGTJXbdizJvlOM",
  "text_template": "KgxiYEHsNmnNcRDwxGxvFL"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 2108986725 },
	{ "name", "Sample Notification" },
	{ "type", "email" },
	{ "event", "webhook_error_summary" },
	{ "html_template", "wHggyBauJXfesVGTJXbdizJvlOM" },
	{ "text_template", "KgxiYEHsNmnNcRDwxGxvFL" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 2108986725 )
	.add("name", "Sample Notification" )
	.add("type", "email" )
	.add("event", "webhook_error_summary" )
	.add("html_template", "wHggyBauJXfesVGTJXbdizJvlOM" )
	.add("text_template", "KgxiYEHsNmnNcRDwxGxvFL" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":2108986725,\"name\":\"Sample Notification\",\"type\":\"email\",\"event\":\"webhook_error_summary\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"wHggyBauJXfesVGTJXbdizJvlOM\",\"text_template\":\"KgxiYEHsNmnNcRDwxGxvFL\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/
```

[Request hydration](## Request Hydration on POST) can be used on this endpoint. This allows you to create a new a notification and all referential entities at the same time.
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
- merchant_site_updates_top
- merchant_site_updates_all


## Update notification

```javascript
const notification = await session.updateNotification(1,{
  "name": "Sample Notification",
  "type": "webhook",
  "event": "webhook_error_summary",
  "config": {
    "recipient": "cardholder",
    "url": null,
    "from_email": "CardUpdatr <no-reply@cardupdatr.app>",
    "return_path": "no-reply@cardupdatr.app",
    "send_email_time": null,
    "interval_length": null,
    "interval_type": null
  },
  "html_template": "YjZsHXWGBPLblBQjytckxZcfoetWy",
  "text_template": "qvQBTvUHDDHNKoZiEEFAmPwfpn"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Sample Notification" },
	{ "type", "webhook" },
	{ "event", "webhook_error_summary" },
	{ "html_template", "YjZsHXWGBPLblBQjytckxZcfoetWy" },
	{ "text_template", "qvQBTvUHDDHNKoZiEEFAmPwfpn" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Sample Notification" )
	.add("type", "webhook" )
	.add("event", "webhook_error_summary" )
	.add("html_template", "YjZsHXWGBPLblBQjytckxZcfoetWy" )
	.add("text_template", "qvQBTvUHDDHNKoZiEEFAmPwfpn" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"Sample Notification\",\"type\":\"webhook\",\"event\":\"webhook_error_summary\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"YjZsHXWGBPLblBQjytckxZcfoetWy\",\"text_template\":\"qvQBTvUHDDHNKoZiEEFAmPwfpn\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/1026804810
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
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/1026804810
```

```javascript
await session.deleteNotification(undefined);
```

```csharp
CardSavrResponse<Notification> notification = await http.DeleteNotificationAsync(undefined);
```

```java
JsonValue notification = session.delete("/notifications", undefined, null);
```

### Path

DELETE /notifications/{id}

### Description

Delete a notification and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [notification response parameters](#response-notification).


# Notification results
Notification result objects are records of an attempt/attempts to send a notification, indicating success/failure and additional relevant information.
## Get notification result

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/notification_results/760791735
```

```javascript
const notificationresults = await session.getNotificationResults(760791735,{"sort":"id","is_descending":true,"page":1, "page_length":25});
```

```csharp
CardSavrResponse<NotificationResults> notificationresults = await session.GetNotificationResultsAsync(760791735,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

```java
JsonValue notificationresults = session.get("/notification_results", 760791735,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 760791735,
  "last_attempt_date": "1991-06-11T06:50:57.463Z",
  "fi_lookup_key": "fTzrjfhVKxYwZIjHCCcktXiwMGGPOjuDbpXdkAszqsVeMTnYrHpwQSVZHjSZLtu",
  "cuid": "ooUKfnUhx",
  "status": "failure",
  "attempts": 2100446690,
  "notification_data": {
    "JdUukrOSaIGh": "&0.(SELqX$qo&nq3-BJv^",
    "lbyFMuBCDiOa": 85,
    "YXEatbfynBHu": false
  },
  "created_on": "2008-01-14T08:31:41.948Z",
  "last_updated_on": "1991-01-31T16:45:49.522Z",
  "notification": {
    "id": 678809741,
    "name": "SrFQVmVgRkLsOXUfKFtMCWnqLKvMichbyMedYJgJBGWZUONrkdoVETUdcFFLTfA",
    "type": "webhook",
    "event": "merchant_site_updates_all",
    "config": {
      "bMlREoAOARQU": "J3s$&NQLWaYeBtxqZ&p75lt",
      "vKvrPgRYaEKy": 14,
      "wGZuTwkHWhbS": false
    },
    "html_template": "vjEKHRwOXIUctvMnQDFTbf",
    "text_template": "IFSA",
    "created_on": "2007-07-05T19:27:56.612Z",
    "last_updated_on": "1986-11-13T06:46:49.990Z"
  }
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

**Example GET request path:**<br>`/notification_results/760791735`

### <a name="response-notification_result"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
last_attempt_date | date | Date of last attempt to post this notification.
fi_lookup_key | string | FI lookup key associated with the attempted notification.
cuid | string | Unique ID for cardholder--can be email address, phone number, etc.
status | string | Status of the notification attempt.
attempts | number | Number of attempts made to send or post notification.
notification_data | object | Data sent with the notification.
created_on | date | Date this notification result was created on
last_updated_on | date | Date this notification result was last updated on
notification_id | number (fk) | ID of the attempted notification.

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
  "notification_id": 49153723,
  "fi_lookup_key": "fTzrjfhVKxYwZIjHCCcktXiwMGGPOjuDbpXdkAszqsVeMTnYrHpwQSVZHjSZLtu",
  "cuid": "ooUKfnUhx",
  "status": "failure",
  "attempts": 2100446690,
  "notification_data": {
    "JdUukrOSaIGh": "&0.(SELqX$qo&nq3-BJv^",
    "lbyFMuBCDiOa": 85,
    "YXEatbfynBHu": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 49153723 },
	{ "fi_lookup_key", "fTzrjfhVKxYwZIjHCCcktXiwMGGPOjuDbpXdkAszqsVeMTnYrHpwQSVZHjSZLtu" },
	{ "cuid", "ooUKfnUhx" },
	{ "status", "failure" },
	{ "attempts", 2100446690 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 49153723 )
	.add("fi_lookup_key", "fTzrjfhVKxYwZIjHCCcktXiwMGGPOjuDbpXdkAszqsVeMTnYrHpwQSVZHjSZLtu" )
	.add("cuid", "ooUKfnUhx" )
	.add("status", "failure" )
	.add("attempts", 2100446690 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":49153723,\"fi_lookup_key\":\"fTzrjfhVKxYwZIjHCCcktXiwMGGPOjuDbpXdkAszqsVeMTnYrHpwQSVZHjSZLtu\",\"cuid\":\"ooUKfnUhx\",\"status\":\"failure\",\"attempts\":2100446690,\"notification_data\":{\"JdUukrOSaIGh\":\"&0.(SELqX$qo&nq3-BJv^\",\"lbyFMuBCDiOa\":85,\"YXEatbfynBHu\":false}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notification_results/
```

[Request hydration](## Request Hydration on POST) can be used on this endpoint. This allows you to create a new a notification result and all referential entities at the same time.
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

# Single-site jobs
Single-site job objects contain the information necessary to place a payment card on a merchant site, as well as status information about the card placement attempt. They are linked to a single cardholder, account, card, and merchant site.
## Get single-site job

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1703229180
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(1703229180,{"sort":"id","is_descending":true,"page":1, "page_length":25});
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(1703229180,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

```java
JsonValue singlesitejobs = session.get("/place_card_on_single_site_jobs", 1703229180,{"sort":"id","is_descending":true,"page":1,"page_length":25});
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1703229180,
  "status": "ABANDONED_QUICKSTART",
  "status_message": "ZRGns",
  "termination_type": "BIILLABLE",
  "custom_data": {
    "okLAHoxrhjNT": "=_q+*s!wxxK_PVotHCya",
    "sCpOPKiPeWod": 19,
    "kZyzMsykMvnp": true
  },
  "notification_sent": true,
  "time_elapsed": 769429377,
  "started_on": "1971-06-13T19:04:30.137Z",
  "completed_on": "1975-05-18T06:57:54.121Z",
  "created_on": "1978-05-31T18:22:22.364Z",
  "last_updated_on": "1985-03-15T09:11:00.490Z",
  "cardholder": {
    "id": 479299771,
    "financial_institution_id": 1573259388,
    "agent_session_id": "XtiK",
    "type": "ephemeral",
    "first_name": "WbQKTiZfV",
    "last_name": "tUlESKNYqmfPXibgpTrETzDehFHyNu",
    "email": "qeLUwEQYNtAU@UNtXHp.Pbm",
    "meta_key": "ClOaAn",
    "cardholder_safe_key": "Uxd3VUHn3/21pTuB468arOWmAKZXa+p6iAYI7ldk/bs=",
    "custom_data": {
      "OeiYydvTIdbK": "bKe1Nl$Vw[5i6rPW",
      "jKhbWrDVUuYa": 28,
      "QDRauZcSZgem": false
    },
    "created_on": "1988-01-28T17:29:06.626Z",
    "last_updated_on": "1972-06-14T07:18:49.090Z"
  },
  "cardsavr_card": {
    "id": 942123050,
    "bin_id": 273369189,
    "cvv": "JqC",
    "expiration_month": "h",
    "expiration_year": "u",
    "name_on_card": "qAZZyhfdTUaMtktAJvFqvrfVVJYdloDNihNonDFkgzsaHmyOXVCTcKtdlOnXocjHIXASewZptqePCkIRvkXGBnVBRhXQCelYvadGATByztcGecbEIMWqiSuwvXakXvfXYcLznZDsUxBoRRyGeLuahKQWZYVnjJYyOUvOVmpGggouurvFDCZeyBSLYBpooAXmJYuqdWAHrgFdKgkEpbhlqIlwybxvjjppCZKeBKwzhnumklRuFsoIVpPzWsdzkv",
    "first_6": "cMqWRNaqplDGAqAmdBygivBHVDfjrfin",
    "first_7": "vqISPEFajGMaMNgbDKZPFrueRlZVDjpC",
    "first_8": "QkszIkRUVEoJGrSNFDvvbgJsoKTTtBub",
    "created_on": "1971-06-26T11:38:03.553Z",
    "last_updated_on": "2004-06-06T14:57:24.507Z"
  },
  "cardsavr_account": {
    "id": 1205726757,
    "last_card_placed_id": 1705832431,
    "username": "fIyYfspqzfLccDIKxassYGyIGNWQeyfWresetzHlIMzqbDkkaUSBDtFHoUw",
    "username_hash": "MBCZJJPzOPmFrzweBdaoWubhCbWRBbUvyVUwToNKpkcYHvGaizhhWOdvdoA",
    "password": "tfjoyMZaMcuVxhJYAMyqNRRSuCaXSRAHHegJWuEWuaYUbBdNtoSpuCSsJuI",
    "last_login": "1977-07-18T23:14:22.295Z",
    "last_password_update": "1975-03-17T21:08:45.579Z",
    "last_saved_card": "2008-02-04T03:38:34.775Z",
    "created_on": "1985-10-16T01:29:27.047Z",
    "last_updated_on": "1995-05-08T02:36:17.377Z"
  }
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/1703229180`

### <a name="response-place_card_on_single_site_job"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number | 
card_id | number (fk) | ID of card associated with this job.
status | string | Current status of job (e.g. pending_tfa).
status_message | string | Human readable representation of the jobs status.
termination_type | string | Final termination status of a job. (BILLABLE, SITE_INTERACTION_FAILURE, USER_DATA_FAILURE, PROCESS FAILURE)
custom_data | object | 
notification_sent | boolean | Indicates if a notification has been sent or posted for this job.
time_elapsed | number | Amount of time elapsed since the creation of the job.
started_on | date | Time when job started.
completed_on | date | Timestamp of job completion.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) | ID of cardholder associated with this job.
account_id | number (fk) | ID of account associated with this job.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

### Filter parameters
- ids / id (in path)
- cardholder_ids
- card_ids
- account_ids
- status
- status_include / status_exclude
- termination_type
- termination_types_include / termaxation_types_exclude
- notification_sent
- time_elapsed_min / time_elapsed_max
- started_on_min / started_on_max
- completed_on_min / completed_on_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

## Create single-site job

```javascript
const singlesitejob = await session.createSingleSiteJob({
  "cardholder_id": 772346502,
  "card_id": 938333785,
  "account_id": 1470936223,
  "status": "ABANDONED_QUICKSTART",
  "custom_data": {
    "okLAHoxrhjNT": "=_q+*s!wxxK_PVotHCya",
    "sCpOPKiPeWod": 19,
    "kZyzMsykMvnp": true
  },
  "notification_sent": true,
  "time_elapsed": 769429377,
  "started_on": "1971-06-13T19:04:30.137Z",
  "completed_on": "1975-05-18T06:57:54.121Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 772346502 },
	{ "card_id", 938333785 },
	{ "account_id", 1470936223 },
	{ "status", "ABANDONED_QUICKSTART" },
	{ "notification_sent", true },
	{ "time_elapsed", 769429377 },
	{ "started_on", "1971-06-13T19:04:30.137Z" },
	{ "completed_on", "1975-05-18T06:57:54.121Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 772346502 )
	.add("card_id", 938333785 )
	.add("account_id", 1470936223 )
	.add("status", "ABANDONED_QUICKSTART" )
	.add("notification_sent", true )
	.add("time_elapsed", 769429377 )
	.add("started_on", "1971-06-13T19:04:30.137Z" )
	.add("completed_on", "1975-05-18T06:57:54.121Z" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":772346502,\"card_id\":938333785,\"account_id\":1470936223,\"status\":\"ABANDONED_QUICKSTART\",\"custom_data\":{\"okLAHoxrhjNT\":\"=_q+*s!wxxK_PVotHCya\",\"sCpOPKiPeWod\":19,\"kZyzMsykMvnp\":true},\"notification_sent\":true,\"time_elapsed\":769429377,\"started_on\":\"1971-06-13T19:04:30.137Z\",\"completed_on\":\"1975-05-18T06:57:54.121Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/
```

[Request hydration](## Request Hydration on POST) can be used on this endpoint. This allows you to create a new a single-site job and all referential entities at the same time.
cardholder_id | number | yes
card_id | number | no
account_id | number | yes
status | [string enum](#post-place_card_on_single_site_job-1)* | no
custom_data | object | no
notification_sent | boolean | no
time_elapsed | number | no
started_on | date | no
completed_on | date | no

See [single-site job response attributes](#response-place_card_on_single_site_job).

#### <a name="post-place_card_on_single_site_job-1"></a>string enum*
- INITIATED
- REQUESTED
- IN_PROGRESS
- AUTH
- LOGIN_SUBMITTED
- PENDING_CREDS
- CREDS_RECEIVED
- PENDING_NEWCREDS
- NEWCREDS_RECEIVED
- PENDING_CARD
- LOGIN_RESUBMITTED
- PENDING_TFA
- TFA_CODE_RECEIVED
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
- ACCOUNT_SETUP_INCOMPLETE
- ACCOUNT_NOT_SUPPORTED
- COUNTRY_NOT_SUPPORTED
- PREPAID_ACCOUNT
- INACTIVE_ACCOUNT
- INVALID_CARD
- INVALID_ADDRESS
- PASSWORD_RESET_REQUIRED
- BUNDLED_SUBSCRIPTION
- FREE_ACCOUNT
- ACCOUNT_LOCKED
- DUPLICATE_CARD
- INVALID_EXPIRATION_DATE
- EXPIRED_CARD
- INVALID_CVV
- INVALID_NETWORK
- MAX_LIMIT_OF_STORED_CARDS
- SUCCESSFUL
- UNSUPPORTED_CAPTCHA
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
const singlesitejob = await session.updateSingleSiteJob(1,{
  "card_id": 2039251792,
  "status": "PASSWORD_RESET_REQUIRED",
  "custom_data": {
    "aeqPYAZxKxWe": ".rvgcB",
    "FIBqRLalSJLR": 59,
    "lVRvCmCsJfEW": true
  },
  "notification_sent": true,
  "time_elapsed": 215387456,
  "started_on": "2001-08-14T16:29:40.101Z",
  "completed_on": "1992-12-31T21:18:49.592Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 2039251792 },
	{ "status", "PASSWORD_RESET_REQUIRED" },
	{ "notification_sent", true },
	{ "time_elapsed", 215387456 },
	{ "started_on", "2001-08-14T16:29:40.101Z" },
	{ "completed_on", "1992-12-31T21:18:49.592Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 2039251792 )
	.add("status", "PASSWORD_RESET_REQUIRED" )
	.add("notification_sent", true )
	.add("time_elapsed", 215387456 )
	.add("started_on", "2001-08-14T16:29:40.101Z" )
	.add("completed_on", "1992-12-31T21:18:49.592Z" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":2039251792,\"status\":\"PASSWORD_RESET_REQUIRED\",\"custom_data\":{\"aeqPYAZxKxWe\":\".rvgcB\",\"FIBqRLalSJLR\":59,\"lVRvCmCsJfEW\":true},\"notification_sent\":true,\"time_elapsed\":215387456,\"started_on\":\"2001-08-14T16:29:40.101Z\",\"completed_on\":\"1992-12-31T21:18:49.592Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1703229180
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
notification_sent | boolean |
time_elapsed | number |
started_on | date |
completed_on | date |

See [single-site job response parameters](#response-place_card_on_single_site_job).

<aside class="notice">Update calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete single-site job

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1703229180
```

```javascript
await session.deleteSingleSiteJob(undefined);
```

```csharp
CardSavrResponse<SingleSiteJob> singlesitejob = await http.DeleteSingleSiteJobAsync(undefined);
```

```java
JsonValue singlesitejob = session.delete("/place_card_on_single_site_jobs", undefined, null);
```

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [single-site job response parameters](#response-place_card_on_single_site_job).

