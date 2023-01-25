
# Accounts
Account objects contain the account information, such as username and password, for a particular cardhoder. They are used to log in to a cardholder's account for placing a payment card.
## Get account

```javascript
const accounts = await session.getAccounts(1102906164,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","merchant_site","cardsavr_card"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["cardholder","merchant_site","cardsavr_card"])}
JsonArray response = (JsonArray)session.get(1102906164, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1102906164,
  "last_password_update": "1994-01-11T11:15:55.732Z",
  "last_saved_card": "1988-12-02T14:52:48.680Z",
  "created_on": "2017-02-10T04:38:26.668Z",
  "last_updated_on": "1982-05-31T13:46:01.790Z",
  "cardholder": {
    "id": 1339357392,
    "type": "persistent_creds",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "oUoPhKx",
    "custom_data": {
      "VVEAvKobNuOl": "wj9~yi+*{F0kK/yLKstTecH$-56)x1",
      "IaMSIFKwajwL": 6,
      "ciEjGBvsMeaN": false
    },
    "created_on": "1994-02-04T02:15:24.320Z",
    "last_updated_on": "1976-11-25T04:31:08.701Z",
    "cuid": "bYENbVRQUye"
  },
  "merchant_site": {
    "id": 1753013655,
    "name": "Amazon",
    "host": "amazon.com",
    "tags": [
      "()CpkIM_MFa390kF~3!Xm,KP-8)7RD(r",
      15,
      "z(Wlu)ETG8^CJ=^u"
    ],
    "interface_type": "vbs",
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
    "account_link": [
      {
        "key_name": "username",
        "label": "Username",
        "type": "initial_account_link"
      },
      {
        "key_name": "password",
        "label": "Password",
        "type": "initial_account_link",
        "secret": true
      },
      {
        "key_name": "otp",
        "label": "One Time Passcode",
        "type": ""
      }
    ],
    "messages": {
      "mfa_label": "Additional information required, this code may be sent to your phone or email address.",
      "additional_info_message": "",
      "auth_message": "Linking account."
    },
    "credit_card_page": "https://www.merchantsite.com/credit_card",
    "forgot_password_page": "https://www.merchantsite.com/forgot_password",
    "login_page": "https://www.merchantsite.com/login"
  },
  "cardsavr_card": {
    "id": 2125921037,
    "type": "Visa",
    "expiration_month": 12,
    "expiration_year": 24,
    "name_on_card": "Jane Smith",
    "nickname": "Jane's VISA",
    "custom_data": {
      "dilePbNXqmVV": "$1y",
      "XUKGYGTrIZPN": 4,
      "CuWFHYEbjfqS": true
    },
    "created_on": "2010-11-04T11:30:03.794Z",
    "last_updated_on": "1991-10-15T17:19:20.087Z",
    "par": "zxSBQRrSikOneAAbooJjCIWViFzPX",
    "customer_key": "XiHsSCaHjsXZEKCkxuNyWiTzRnzzjr"
  },
  "customer_key": "TD"
}
```

### Path

GET /cardsavr_accounts **(batch)** or GET /cardsavr_accounts/:id **(singular)**

### Description

Returns the account specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable accounts, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


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

**Example batch GET request path:**<br>`/cardsavr_accounts?ids=1,2`

#### Singular GET requests

**Singular requests** only return the account matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_accounts/1102906164`

### <a name="response-cardsavr_account"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this account.
last_card_placed_id | number (fk) [cards](#cards) | ID of the last card placed on this account by the Virtual Browser System (VBS).
last_password_update | date | 
last_saved_card | date | Date of last card saved on this account.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) [cardholders](#cardholders) | ID of the cardholder associated with this account.
merchant_site_id | number (fk) [merchant sites](#merchant-sites) | ID of the merchant site associated with this account.
customer_key | string | An external reference to a merchant site for a specific cardholder.  A key of merchant host and cuid will be used if none provided. The default can potentially violate a constraint with two accounts of the same merchant site.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create account

```javascript
const account = await session.createAccount({
  "cardholder_id": 1868900573,
  "merchant_site_id": 1573458732,
  "customer_key": "TD",
  "last_card_placed_id": 1010043920,
  "account_link": {
    "username": "jsmith123",
    "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1868900573 },
	{ "merchant_site_id", 1573458732 },
	{ "customer_key", "TD" },
	{ "last_card_placed_id", 1010043920 }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1868900573 )
	.add("merchant_site_id", 1573458732 )
	.add("customer_key", "TD" )
	.add("last_card_placed_id", 1010043920 )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1868900573,\"merchant_site_id\":1573458732,\"customer_key\":\"TD\",\"last_card_placed_id\":1010043920,\"account_link\":{\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/
```

### Path

POST /cardsavr_accounts

### Description

Create a account and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.



<aside class="notice"><a href=#request-hydration-on-post>Request hydration</a> can be used on this endpoint. This allows you to create a new account and all referential entities in a single POST request.
</aside>

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cardholder_id | number | yes | ID of the cardholder associated with this account.
merchant_site_id | number | yes | ID of the merchant site associated with this account.
customer_key | string | yes | An external reference to a merchant site for a specific cardholder.  A key of merchant host and cuid will be used if none provided. The default can potentially violate a constraint with two accounts of the same merchant site.
last_card_placed_id | number | no | ID of the last card placed on this account by the Virtual Browser System (VBS).
account_link | object | no | One or more properties with key:value pairs that are required for authenticated a user.  These properties are either included as part of initial account collection, or they are requested as part of a credential_request.  An error will be returned if all properties are not provided for a given credential_request. The set of key:value pairs for a site is specified in the merchant site info returned from GET /merchant_sites as account_link.

See [account response attributes](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the account_link when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Upsert account

```javascript
const account = await session.updateAccount(1,{
  "last_card_placed_id": 660560022,
  "account_link": {
    "username": "jsmith123",
    "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
  }
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 660560022 }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 660560022 )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":660560022,\"account_link\":{\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1102906164
```

### Path

PUT /cardsavr_accounts OR /cardsavr_accounts/{id}

### Description

Upsert can be used to either update a account, create a new account, or return an existing account.  Either an id or customer_key is required for upsert. The id (in path or body), along with an updated body, can be used to update an existing account; the customer_key (in body) can likewise be used to update a account, and can also be used to create a new account, if the customer_key does not match any existing accounts. If the id or customer_key provided corresponds to a pre-existing account and no updated information has been included in the body, the existing account will be returned.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
last_card_placed_id | number | ID of the last card placed on this account by the Virtual Browser System (VBS).
account_link | object | One or more properties with key:value pairs that are required for authenticated a user.  These properties are either included as part of initial account collection, or they are requested as part of a credential_request.  An error will be returned if all properties are not provided for a given credential_request. The set of key:value pairs for a site is specified in the merchant site info returned from GET /merchant_sites as account_link.

See [account response parameters](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the account_link when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete account

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1102906164
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



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [account response parameters](#response-cardsavr_account).


# Addresses
Address objects contain the billing address for a specific cardholder, and are used to populate billing address information on merchant sites. They are linked to cards and cardholders.
## Get address

```javascript
const addresses = await session.getAddresses(1351823695,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["cardholder"])}
JsonArray response = (JsonArray)session.get(1351823695, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1351823695,
  "address1": "VNeogcFFwMOpqoxXWvECUOrqDpDjMXmOaIpoNJgqWdPLwaxKhluRotdXpCBLCGOsmLnDbfrTOnuAQrvIARiyIzsVMFwAwqGloPW",
  "address2": "FOEREbBrkXLDMFijpmBsHvVUglbQiQRkdWhuWRnCDtVtKrSSTVToHxfxtzJZrKAxTtcSniSFXEoqFFBJNvbQeVretgondTpuCfb",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "FYZMhrwzzUwr@ximYLm.ogD",
  "phone_number": "2065555555",
  "created_on": "1977-01-09T00:26:11.038Z",
  "last_updated_on": "1982-11-05T14:30:33.837Z",
  "cardholder": {
    "id": 505812283,
    "type": "ephemeral",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "SLTwUcFxbDnCfgKTopdtjmmOoaQ",
    "custom_data": {
      "VWcwCTQzATOY": "hCE",
      "pUIJMlZpPqiz": 82,
      "hvepSMKlvhfY": false
    },
    "created_on": "2018-01-07T16:04:25.662Z",
    "last_updated_on": "1972-11-13T20:02:39.040Z",
    "cuid": "ddjAkKJLGffAHT"
  }
}
```

### Path

GET /cardsavr_addresses **(batch)** or GET /cardsavr_addresses/:id **(singular)**

### Description

Returns the address specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable addresses, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- cardholder_ids
- is_primary
- first_name
- last_name
- email
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/cardsavr_addresses?ids=1,2`

#### Singular GET requests

**Singular requests** only return the address matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_addresses/1351823695`

### <a name="response-cardsavr_address"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this address.
address1 | string | 
address2 | string | Second line of address, if one exists (e.g. apartment number).
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
cardholder_id | number (fk) [cardholders](#cardholders) | ID of the cardholder associated with this address.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create address

```javascript
const address = await session.createAddress({
  "cardholder_id": 1051791274,
  "address1": "VNeogcFFwMOpqoxXWvECUOrqDpDjMXmOaIpoNJgqWdPLwaxKhluRotdXpCBLCGOsmLnDbfrTOnuAQrvIARiyIzsVMFwAwqGloPW",
  "address2": "FOEREbBrkXLDMFijpmBsHvVUglbQiQRkdWhuWRnCDtVtKrSSTVToHxfxtzJZrKAxTtcSniSFXEoqFFBJNvbQeVretgondTpuCfb",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "FYZMhrwzzUwr@ximYLm.ogD",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1051791274 },
	{ "address1", "VNeogcFFwMOpqoxXWvECUOrqDpDjMXmOaIpoNJgqWdPLwaxKhluRotdXpCBLCGOsmLnDbfrTOnuAQrvIARiyIzsVMFwAwqGloPW" },
	{ "address2", "FOEREbBrkXLDMFijpmBsHvVUglbQiQRkdWhuWRnCDtVtKrSSTVToHxfxtzJZrKAxTtcSniSFXEoqFFBJNvbQeVretgondTpuCfb" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "FYZMhrwzzUwr@ximYLm.ogD" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1051791274 )
	.add("address1", "VNeogcFFwMOpqoxXWvECUOrqDpDjMXmOaIpoNJgqWdPLwaxKhluRotdXpCBLCGOsmLnDbfrTOnuAQrvIARiyIzsVMFwAwqGloPW" )
	.add("address2", "FOEREbBrkXLDMFijpmBsHvVUglbQiQRkdWhuWRnCDtVtKrSSTVToHxfxtzJZrKAxTtcSniSFXEoqFFBJNvbQeVretgondTpuCfb" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "FYZMhrwzzUwr@ximYLm.ogD" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1051791274,\"address1\":\"VNeogcFFwMOpqoxXWvECUOrqDpDjMXmOaIpoNJgqWdPLwaxKhluRotdXpCBLCGOsmLnDbfrTOnuAQrvIARiyIzsVMFwAwqGloPW\",\"address2\":\"FOEREbBrkXLDMFijpmBsHvVUglbQiQRkdWhuWRnCDtVtKrSSTVToHxfxtzJZrKAxTtcSniSFXEoqFFBJNvbQeVretgondTpuCfb\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"FYZMhrwzzUwr@ximYLm.ogD\",\"phone_number\":\"2065555555\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/
```

### Path

POST /cardsavr_addresses

### Description

Create a address and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.



<aside class="notice"><a href=#request-hydration-on-post>Request hydration</a> can be used on this endpoint. This allows you to create an new address and all referential entities in a single POST request.
</aside>

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cardholder_id | number | yes | ID of the cardholder associated with this address.
address1 | string | yes | 
address2 | string | no | Second line of address, if one exists (e.g. apartment number).
city | string | yes | 
subnational | string | yes | Subnational unit (i.e. state or province).
postal_code | string | yes | 
postal_other | string | no | E.g. last four digits in a zip-plus-four.
country | [string enum](#post-cardsavr_address-1)* | no | 
is_primary | boolean | yes | Indicates if this is the primary address of this cardholder, as a cardholder can be linked to multiple addresses.
first_name | string | no | 
last_name | string | no | 
email | string | no | 
phone_number | string | no | 

See [address response attributes](#response-cardsavr_address).

#### <a name="post-cardsavr_address-1"></a>string enum*
- usa
- canada
- Canada
- USA


## Update address

```javascript
const address = await session.updateAddress(1,{
  "address1": "JQYzqfGwmtNdGbhiBqShGUrpgtyfPBZFhiCldwWnLesXQvQyzHMCiPDabbfvkPpAihfpLlnVPgeaJFgAFtcHJqObwznlTIDCisb",
  "address2": "LvHILlVSsJKhyFVCFexWDQlUlfUnycBVyosaJHjHbJNuHCymWVQxVSUQZAKjWhgOGwFXuYrlWWieHkHyfiQWntcABCmFOZLouNJ",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "nCrnWJwsKaeE@nYaUQd.Icx",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "JQYzqfGwmtNdGbhiBqShGUrpgtyfPBZFhiCldwWnLesXQvQyzHMCiPDabbfvkPpAihfpLlnVPgeaJFgAFtcHJqObwznlTIDCisb" },
	{ "address2", "LvHILlVSsJKhyFVCFexWDQlUlfUnycBVyosaJHjHbJNuHCymWVQxVSUQZAKjWhgOGwFXuYrlWWieHkHyfiQWntcABCmFOZLouNJ" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "nCrnWJwsKaeE@nYaUQd.Icx" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "JQYzqfGwmtNdGbhiBqShGUrpgtyfPBZFhiCldwWnLesXQvQyzHMCiPDabbfvkPpAihfpLlnVPgeaJFgAFtcHJqObwznlTIDCisb" )
	.add("address2", "LvHILlVSsJKhyFVCFexWDQlUlfUnycBVyosaJHjHbJNuHCymWVQxVSUQZAKjWhgOGwFXuYrlWWieHkHyfiQWntcABCmFOZLouNJ" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", false )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "nCrnWJwsKaeE@nYaUQd.Icx" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"JQYzqfGwmtNdGbhiBqShGUrpgtyfPBZFhiCldwWnLesXQvQyzHMCiPDabbfvkPpAihfpLlnVPgeaJFgAFtcHJqObwznlTIDCisb\",\"address2\":\"LvHILlVSsJKhyFVCFexWDQlUlfUnycBVyosaJHjHbJNuHCymWVQxVSUQZAKjWhgOGwFXuYrlWWieHkHyfiQWntcABCmFOZLouNJ\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"nCrnWJwsKaeE@nYaUQd.Icx\",\"phone_number\":\"2065555555\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1351823695
```

### Path

PUT /cardsavr_addresses OR /cardsavr_addresses/{id}

### Description

Update a address and return the updated object.  An id is required on every update request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
address1 | string | 
address2 | string | Second line of address, if one exists (e.g. apartment number).
city | string | 
subnational | string | Subnational unit (i.e. state or province).
postal_code | string | 
postal_other | string | E.g. last four digits in a zip-plus-four.
country | [string enum](#post-cardsavr_address-1)* | 
is_primary | boolean | Indicates if this is the primary address of this cardholder, as a cardholder can be linked to multiple addresses.
first_name | string | 
last_name | string | 
email | string | 
phone_number | string | 

See [address response parameters](#response-cardsavr_address).


## Delete address

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1351823695
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



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [address response parameters](#response-cardsavr_address).


# Bins
A Bank Identification Number (BIN) object represents a BIN used by a financial institution in the CardSavr API. They are linked to cards and FIs and used for reporting purposes.
## Get bin

```javascript
const bins = await session.getBins(2135942559,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Bins> bins = await session.GetBinsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["financial_institution"])}
JsonArray response = (JsonArray)session.get(2135942559, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2135942559,
  "custom_data": {
    "KxnKwmNexwor": "[f~",
    "ADNcFlMuJWUx": 95,
    "ZvpJOxnxonuN": false
  },
  "created_on": "2014-01-07T06:42:39.243Z",
  "last_updated_on": "1991-06-22T03:59:13.343Z",
  "financial_institution": {
    "id": 1461190003,
    "name": "LcGIsXwYxjvTeSVQXIgxPzbCwbcDhujGwMkyDKYohKNCUoJnrWhaRbXuJNOMrgW",
    "description": "gVojhVDGFGCoBZffUp",
    "lookup_key": "bxcTgLNePIahLhuRJeDHjIUzJdRYKnwbEvFKmyElkUDiABPDmJfNaMrAgziyQDb",
    "alternate_lookup_key": "HUAHKWbADOBjWtrldlzLMmMvkmvYnLrPdEDVgmmvzvOYsyNhjqxUiPQCxHIAYsC",
    "last_activity": "2005-06-25T14:51:07.270Z",
    "created_on": "2014-12-12T22:15:26.522Z",
    "last_updated_on": "2008-05-11T00:16:46.594Z"
  },
  "bank_identification_number": "6563168"
}
```

### Path

GET /cardsavr_bins **(batch)** or GET /cardsavr_bins/:id **(singular)**

### Description

Returns the bin specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable bins, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- financial_institution_ids
- bank_identification_numbers
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/cardsavr_bins?ids=1,2`

#### Singular GET requests

**Singular requests** only return the bin matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_bins/2135942559`

### <a name="response-cardsavr_bin"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this BIN.
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | ID of financial institution that this Bank Identification Number belongs to.
custom_data | object | Custom data (e.g. brand, type) that can be added according to FI need.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
bank_identification_number | string | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create bin

```javascript
const bin = await session.createBin({
  "financial_institution_id": 433002039,
  "bank_identification_number": "6563168",
  "custom_data": {
    "KxnKwmNexwor": "[f~",
    "ADNcFlMuJWUx": 95,
    "ZvpJOxnxonuN": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 433002039 },
	{ "bank_identification_number", "6563168" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 433002039 )
	.add("bank_identification_number", "6563168" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":433002039,\"bank_identification_number\":\"6563168\",\"custom_data\":{\"KxnKwmNexwor\":\"[f~\",\"ADNcFlMuJWUx\":95,\"ZvpJOxnxonuN\":false}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/
```

### Path

POST /cardsavr_bins

### Description

Create a bin and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
financial_institution_id | number | yes | ID of financial institution that this Bank Identification Number belongs to.
bank_identification_number | string | yes | 
custom_data | object | no | Custom data (e.g. brand, type) that can be added according to FI need.

See [bin response attributes](#response-cardsavr_bin).


## Update bin

```javascript
const bin = await session.updateBin(1,{
  "financial_institution_id": 1056618359,
  "custom_data": {
    "cJMHmfPKddQf": "R+Hv+aYM$vGw]hWR}XQxguLmF43f3",
    "jNBMBFJuWbjI": 40,
    "wDwUDJcuiBWe": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1056618359 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1056618359 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1056618359,\"custom_data\":{\"cJMHmfPKddQf\":\"R+Hv+aYM$vGw]hWR}XQxguLmF43f3\",\"jNBMBFJuWbjI\":40,\"wDwUDJcuiBWe\":true}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/2135942559
```

### Path

PUT /cardsavr_bins OR /cardsavr_bins/{id}

### Description

Update a bin and return the updated object.  An id is required on every update request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
financial_institution_id | number | ID of financial institution that this Bank Identification Number belongs to.
custom_data | object | Custom data (e.g. brand, type) that can be added according to FI need.

See [bin response parameters](#response-cardsavr_bin).


## Delete bin

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/2135942559
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



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [bin response parameters](#response-cardsavr_bin).


# Card Placement Results
Card Placement results are a flatted version of the jobs and its publily available meta data. Although sensitive data like the PAN and account creds are not available, all the details of the job are captured here for future reference after the corresponding entities may have been deleted.
## Get card placement result

```javascript
const cardplacementresults = await session.getCardPlacementResults(923380121,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution","merchant_site","cardsavr_bin"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<CardPlacementResults> cardplacementresults = await session.GetCardPlacementResultsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["financial_institution","merchant_site","cardsavr_bin"])}
JsonArray response = (JsonArray)session.get(923380121, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 923380121,
  "merchant_site_hostname": "seJLSFidnMqGNvzcrxWJhRMBVoUvfJrvVfTHPzLgZQWiFqQuienNIlwaXOUJuoOdodcRJwPrXmtksChboTKVjUnbWCRJBjSbyrDmxyXuGrZnHtxipEJLacZhIrvvJLIRMEqRyciQqqoWhlkvcWErVtuZUYgndfXDDVslGBGahbQuKPVKHTnUHXSzOhKQMbXsjgBdzTgUQXGOFBfzoLKxLQgGFlqjLAqPCfpaHNrIWbkPFkOwHILajWBEpeNlFW",
  "meta_key": "MB9810411",
  "fi_name": "ijSWeaaKFrlBZAiQwrKchAHedLZqvnpexgdDUFhnRXIzACZGAZcbbixJyPBXeVq",
  "bank_identification_number": "81857474",
  "cuid": "JrXfIyqFQpxOvkiXvVYeZHPvkuPCXFHD",
  "par": "MMcSozVqxuoySVxpgaLJXWYSCaYEc",
  "card_customer_key": "CFbWsiEzSvWBroGXJahiLTv",
  "account_customer_key": "IqLkxks",
  "status": "SUCCESSFUL",
  "status_message": "Successful",
  "termination_type": "BILLABLE",
  "custom_data": {
    "wevNMgNjpnHT": "P]&+/$E7(vF6jaDRf6KDH__Epr_,)P",
    "ALSEDMgYwuoM": 86,
    "OYKfevJWpCDk": true
  },
  "time_elapsed": 1503475174,
  "first_6": "ksNRRMdZwtsIjDvdVvSHDwFvJvXpTwsE",
  "first_7": "JFcXRuFinVTAXFZVaiEyUhuStpvcRwZm",
  "first_8": "hDyaYybrRDYGQwmrUxPZVYuyrPbWGrrV",
  "trace": "QSNwdaWVJsyGRsRaisQsqhswP",
  "email_sent": false,
  "completed_on": "1985-07-07T00:23:38.388Z",
  "created_on": "1993-03-08T15:59:49.451Z",
  "last_updated_on": "1976-08-24T23:12:13.646Z",
  "financial_institution": {
    "id": 1703562757,
    "name": "OczLtIbiUGpTuIthFskaLZqVtSkvGRbQsJmaqYSDUNxigZggqpAMfOvgsoyXuRJ",
    "description": "V",
    "lookup_key": "uSyrJxPNxbbJDtbCTnrjdaYbsRbERizxNzaOcxziFaEifKhzRyrrujMPDOsIxOO",
    "alternate_lookup_key": "GaySvzcvLpRMorpijJqSXMuVxAizyXVNZqzvKfYQrPhBBgFkUZKSPPKWvlgJwLL",
    "last_activity": "1984-06-14T04:04:55.065Z",
    "created_on": "2019-08-20T10:01:47.189Z",
    "last_updated_on": "2009-04-19T05:48:40.748Z"
  },
  "merchant_site": {
    "id": 75229485,
    "name": "Amazon",
    "host": "amazon.com",
    "tags": [
      "gH6*sNAedj_*qm(TV+EpOdo*[IV+Z",
      64,
      "R4Ml_@9~,^s"
    ],
    "interface_type": "dcs",
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
    "account_link": [
      {
        "key_name": "username",
        "label": "Username",
        "type": "initial_account_link"
      },
      {
        "key_name": "password",
        "label": "Password",
        "type": "initial_account_link",
        "secret": true
      },
      {
        "key_name": "otp",
        "label": "One Time Passcode",
        "type": ""
      }
    ],
    "messages": {
      "mfa_label": "Additional information required, this code may be sent to your phone or email address.",
      "additional_info_message": "",
      "auth_message": "Linking account."
    },
    "credit_card_page": "https://www.merchantsite.com/credit_card",
    "forgot_password_page": "https://www.merchantsite.com/forgot_password",
    "login_page": "https://www.merchantsite.com/login"
  },
  "cardsavr_bin": {
    "id": 1118756532,
    "custom_data": {
      "VvEvriRMHgxr": "44o@ZU",
      "HcQSUbAMKluS": 87,
      "bpEXVXBYKAgJ": false
    },
    "created_on": "1988-06-12T05:29:22.765Z",
    "last_updated_on": "2003-10-10T07:01:51.873Z",
    "bank_identification_number": "84999390"
  },
  "place_card_on_single_site_job_id": 1585151006
}
```

### Path

GET /card_placement_results **(batch)** or GET /card_placement_results/:id **(singular)**

### Description

Returns the card placement result specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable card placement results, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


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
- statuses
- status
- termination_type
- termination_types_include / termination_types_exclude
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

**Example batch GET request path:**<br>`/card_placement_results?ids=1,2`

#### Singular GET requests

**Singular requests** only return the card placement result matching the id provided in the path.

**Example GET request path:**<br>`/card_placement_results/923380121`

### <a name="response-card_placement_result"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this card placement result.
merchant_site_hostname | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
fi_name | string | 
bank_identification_number | string | 
cuid | string | External unique ID for cardholder--can be account_id, email address, phone number, etc.  A random number will be gnenerated if not provided.
par | string | 
card_customer_key | string | Unique customer reference for this card. A random number will be generated and returned if not provided
account_customer_key | string | An external reference to a merchant site for a specific cardholder.  A key of merchant host and cuid will be used if none provided. The default can potentially violate a constraint with two accounts of the same merchant site.
status | string | Status of job (when it terminated).
status_message | string | Human readable representation of the job's status.
termination_type | string | Final termination status of a job. (BILLABLE, SITE_INTERACTION_FAILURE, USER_DATA_FAILURE, PROCESS FAILURE)
custom_data | object | 
time_elapsed | number | 
first_6 | string | First six digits of card number.
first_7 | string | First seven digits of card number.
first_8 | string | First eight digits of card number.
trace | string | The trace key follows jobs as they are processed from beginning to end.  This helps with debugging the logs.
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | 
merchant_site_id | number (fk) [merchant sites](#merchant-sites) | 
email_sent | boolean | 
completed_on | date | 
created_on | date | Date this job result was created on
last_updated_on | date | Date this job result was last updated on
place_card_on_single_site_job_id | number | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

# Cards
A card object contains information about a payment card for a specific cardholder. Card objects are used to populate payment information on merchant sites.
## Get card

```javascript
const cards = await session.getCards(641501920,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_address","cardsavr_bin"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Cards> cards = await session.GetCardsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_address","cardsavr_bin"])}
JsonArray response = (JsonArray)session.get(641501920, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 641501920,
  "type": "Visa",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "PfpuvEokMEnD": "5=U*0myoslP^yPbq[NWv@",
    "licqAMJLcbsK": 2,
    "VIwysfCuPNeS": true
  },
  "created_on": "2023-01-19T00:39:05.239Z",
  "last_updated_on": "2005-10-13T06:11:51.477Z",
  "cardholder": {
    "id": 1441009875,
    "type": "persistent_all",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "MgjJDnGMqTudqO",
    "custom_data": {
      "AsfDczvLDwdY": "N@,%T+}",
      "IufsYpVMQKVZ": 4,
      "GiynVnFWHVUN": false
    },
    "created_on": "2013-12-04T19:22:35.155Z",
    "last_updated_on": "2019-01-10T11:09:55.387Z",
    "cuid": "NaQUGPHYjmNTZVXIT"
  },
  "cardsavr_address": {
    "id": 813567540,
    "address1": "HTTRmdTwTQMGuPaWfCOpSCYtiTgqHrfcOrHGPklBRBWzmmxLbjIIXAfduHoopdNkKjwlKhzglxECJFUMCCRhZzUSguPqESxjRzE",
    "address2": "zGgfpOaWltMLwcEgoudKnOVCthQPflKXxZnkeFvLStaPSQzOnKdgwZSAKMeqFxbuDxBXlJFcNveOTsBoeaQNyhqBGCGgWXJPTQQ",
    "city": "Seattle",
    "subnational": "WA",
    "postal_code": "98177",
    "postal_other": "98177-0124",
    "country": "USA",
    "is_primary": true,
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "mhZZRTsrVeJL@iUfMgi.jAa",
    "phone_number": "2065555555",
    "created_on": "2004-12-22T22:24:55.520Z",
    "last_updated_on": "2008-06-07T00:16:14.376Z"
  },
  "cardsavr_bin": {
    "id": 156404704,
    "custom_data": {
      "GJxYNcLmWpZg": "uQ+4UN(%dWy_#HwG2=oHzdss",
      "ReLWUsCAZfDu": 87,
      "jCLajpsGNrOz": false
    },
    "created_on": "1975-06-26T00:43:49.912Z",
    "last_updated_on": "1999-10-03T14:29:56.890Z",
    "bank_identification_number": "52946352"
  },
  "par": "CzLooZYxggmiljZNXUuSjCGaknedH",
  "customer_key": "oSzaZamWsFw"
}
```

### Path

GET /cardsavr_cards **(batch)** or GET /cardsavr_cards/:id **(singular)**

### Description

Returns the card specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable cards, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- cardholder_ids
- address_ids
- bin_ids
- pars
- customer_keys
- types
- type
- nickname
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/cardsavr_cards?ids=1,2`

#### Singular GET requests

**Singular requests** only return the card matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_cards/641501920`

### <a name="response-cardsavr_card"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this card.
bin_id | number (fk) [bins](#bins) | ID of BIN associated with this card.
type | string | Type of card (e.g. Visa), automatically filled in by CardSavr.
expiration_month | string | 
expiration_year | string | 
name_on_card | string | 
nickname | string | 
custom_data | object | Meta-data that can be added to the card if needed.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) [cardholders](#cardholders) | ID of cardholder associated with this card.
address_id | number (fk) [addresses](#addresses) | ID of address associated with this card.
par | string | Unique Personal Account Reference number for this card, to be used for card lookup. Generated automatically from PAN, expiration date, and username if using the SDK.
customer_key | string | Unique customer reference for this card. A random number will be generated and returned if not provided

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create card

```javascript
const card = await session.createCard({
  "cardholder_id": 254413658,
  "address_id": 1712872948,
  "bin_id": 639356581,
  "par": "CzLooZYxggmiljZNXUuSjCGaknedH",
  "customer_key": "oSzaZamWsFw",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "PfpuvEokMEnD": "5=U*0myoslP^yPbq[NWv@",
    "licqAMJLcbsK": 2,
    "VIwysfCuPNeS": true
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 254413658 },
	{ "address_id", 1712872948 },
	{ "bin_id", 639356581 },
	{ "par", "CzLooZYxggmiljZNXUuSjCGaknedH" },
	{ "customer_key", "oSzaZamWsFw" },
	{ "pan", "4111111111111111" },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Jane Smith" },
	{ "nickname", "Jane's VISA" }
};

CardSavrResponse<Card> card = await http.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 254413658 )
	.add("address_id", 1712872948 )
	.add("bin_id", 639356581 )
	.add("par", "CzLooZYxggmiljZNXUuSjCGaknedH" )
	.add("customer_key", "oSzaZamWsFw" )
	.add("pan", "4111111111111111" )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Jane Smith" )
	.add("nickname", "Jane's VISA" )
	.build();
JsonValue card = session.post("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":254413658,\"address_id\":1712872948,\"bin_id\":639356581,\"par\":\"CzLooZYxggmiljZNXUuSjCGaknedH\",\"customer_key\":\"oSzaZamWsFw\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"Jane's VISA\",\"custom_data\":{\"PfpuvEokMEnD\":\"5=U*0myoslP^yPbq[NWv@\",\"licqAMJLcbsK\":2,\"VIwysfCuPNeS\":true}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/
```

### Path

POST /cardsavr_cards

### Description

Create a card and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.



<aside class="notice"><a href=#request-hydration-on-post>Request hydration</a> can be used on this endpoint. This allows you to create a new card and all referential entities in a single POST request.
</aside>

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cardholder_id | number | yes | ID of cardholder associated with this card.
address_id | number | no | ID of address associated with this card.
bin_id | number | no | ID of BIN associated with this card.
par | string | no | Unique Personal Account Reference number for this card, to be used for card lookup. Generated automatically from PAN, expiration date, and username if using the SDK.
customer_key | string | yes | Unique customer reference for this card. A random number will be generated and returned if not provided
pan | string | yes | Personal Account Number (PAN) of this card.
cvv | string | yes | 
expiration_month | string | yes | 
expiration_year | string | yes | 
name_on_card | string | yes | 
nickname | string | no | 
custom_data | object | no | Meta-data that can be added to the card if needed.

See [card response attributes](#response-cardsavr_card).

#### <a name="post-cardsavr_card-1"></a>string enum*
- Visa
- Mastercard
- American Express
- Unknown Type

<aside class="notice">Update calls to /cardsavr_cards require the cardholder's personal cardholder_safe_key header to encrypt and save the pan and cvv when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Upsert card

```javascript
const card = await session.updateCard(1,{
  "bin_id": 1040607155,
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "YzYuvpjOoIQH": "$FG7gUD_PMB{vWb=OY.",
    "iGSeaBoQQAmU": 92,
    "MNnHHdpoLpSD": true
  },
  "pan": "4111111111111111"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "bin_id", 1040607155 },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Jane Smith" },
	{ "nickname", "Jane's VISA" },
	{ "pan", "4111111111111111" }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("bin_id", 1040607155 )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Jane Smith" )
	.add("nickname", "Jane's VISA" )
	.add("pan", "4111111111111111" )
	.build();
JsonValue card = session.put("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"bin_id\":1040607155,\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"Jane's VISA\",\"custom_data\":{\"YzYuvpjOoIQH\":\"$FG7gUD_PMB{vWb=OY.\",\"iGSeaBoQQAmU\":92,\"MNnHHdpoLpSD\":true},\"pan\":\"4111111111111111\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/641501920
```

### Path

PUT /cardsavr_cards OR /cardsavr_cards/{id}

### Description

Upsert can be used to either update a card, create a new card, or return an existing card.  Either an id or customer_key is required for upsert. The id (in path or body), along with an updated body, can be used to update an existing card; the customer_key (in body) can likewise be used to update a card, and can also be used to create a new card, if the customer_key does not match any existing cards. If the id or customer_key provided corresponds to a pre-existing card and no updated information has been included in the body, the existing card will be returned.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
bin_id | number | ID of BIN associated with this card.
cvv | string | 
expiration_month | string | 
expiration_year | string | 
name_on_card | string | 
nickname | string | 
custom_data | object | Meta-data that can be added to the card if needed.

See [card response parameters](#response-cardsavr_card).


## Delete card

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/641501920
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



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [card response parameters](#response-cardsavr_card).


# Cardholders
Cardholders are the end-users of the CardSavr API, who can have their their payment information updated on merchant site(s). Cardholders can be linked to cards, accounts, and addresses.
## Get cardholder

```javascript
const cardholders = await session.getCardholders(444033905,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Cardholders> cardholders = await session.GetCardholdersAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["financial_institution"])}
JsonArray response = (JsonArray)session.get(444033905, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 444033905,
  "type": "ephemeral",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "cORaudLXQQtBsBwoeMWFT",
  "custom_data": {
    "JCAAXMmDTqyn": "gyC,3_m=LP@%4(wfyj8q6Tq-",
    "SPVgZQjQtVvB": 15,
    "VOLCogEpRsuG": true
  },
  "created_on": "1977-03-17T08:44:09.539Z",
  "last_updated_on": "2012-01-17T06:27:02.336Z",
  "financial_institution": {
    "id": 254337771,
    "name": "CVzPiCTZqMDgmaLbKtzLYxUayuxvxwVIODLEKMTreSWTKnYZmJlDAXeHyZZMnJR",
    "description": "AMjsDmoLQvBkdw",
    "lookup_key": "HKLhzCimzoLhlyhOLsNMIGqxkchDBUsMmpDxbQquUltjpqrswdBgqVIVFhKHTYX",
    "alternate_lookup_key": "LtAMarvfLSqOajzMkrjqAovZYVEjaqyxaCVJVzFBWXKIJOjHFjUqOBNiKtceaaN",
    "last_activity": "2011-10-12T19:40:19.244Z",
    "created_on": "2022-08-24T22:12:35.845Z",
    "last_updated_on": "2003-04-02T22:14:58.892Z"
  },
  "cuid": "BBzpeYViHbkxXRTyUCOZOmS"
}
```

### Path

GET /cardholders **(batch)** or GET /cardholders/:id **(singular)**

### Description

Returns the cardholder specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable cardholders, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- financial_institution_ids
- financial_institution_id
- cuid
- type
- first_name
- last_name
- email
- meta_key
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/cardholders?ids=1,2`

#### Singular GET requests

**Singular requests** only return the cardholder matching the id provided in the path.

**Example GET request path:**<br>`/cardholders/444033905`

### <a name="response-cardholder"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this cardholder.
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | 
type | string | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities.
 If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
first_name | string | 
last_name | string | 
email | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
custom_data | object | Additional data that can be added to the cardholder if needed.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cuid | string | External unique ID for cardholder--can be account_id, email address, phone number, etc.  A random number will be gnenerated if not provided.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create cardholder

```javascript
const cardholder = await session.createCardholder({
  "cuid": "BBzpeYViHbkxXRTyUCOZOmS",
  "type": "ephemeral",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "cORaudLXQQtBsBwoeMWFT",
  "custom_data": {
    "JCAAXMmDTqyn": "gyC,3_m=LP@%4(wfyj8q6Tq-",
    "SPVgZQjQtVvB": 15,
    "VOLCogEpRsuG": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cuid", "BBzpeYViHbkxXRTyUCOZOmS" },
	{ "type", "ephemeral" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "cORaudLXQQtBsBwoeMWFT" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cuid", "BBzpeYViHbkxXRTyUCOZOmS" )
	.add("type", "ephemeral" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "cORaudLXQQtBsBwoeMWFT" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"cuid\":\"BBzpeYViHbkxXRTyUCOZOmS\",\"type\":\"ephemeral\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"cORaudLXQQtBsBwoeMWFT\",\"custom_data\":{\"JCAAXMmDTqyn\":\"gyC,3_m=LP@%4(wfyj8q6Tq-\",\"SPVgZQjQtVvB\":15,\"VOLCogEpRsuG\":true}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/
```

### Path

POST /cardholders

### Description

Create a cardholder and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cuid | string | yes | External unique ID for cardholder--can be account_id, email address, phone number, etc.  A random number will be gnenerated if not provided.
type | [string enum](#post-cardholder-1)* | no | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities.
 If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
first_name | string | no | 
last_name | string | no | 
email | string | no | 
meta_key | string | no | Key used for billing record identification; automatically generated during card creation.
custom_data | object | no | Additional data that can be added to the cardholder if needed.

See [cardholder response attributes](#response-cardholder).

#### <a name="post-cardholder-1"></a>string enum*
- ephemeral
- persistent_creds
- persistent_all


## Upsert cardholder

```javascript
const cardholder = await session.updateCardholder(1,{
  "type": "ephemeral",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "ldEusOxu",
  "custom_data": {
    "HYjKHRMLpKJp": "=)G[0LZ4iYuO3/V@5(sbbO9q=2,^",
    "RmWQKdliWcNK": 83,
    "fYJbfLSfOYnh": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "type", "ephemeral" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "ldEusOxu" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("type", "ephemeral" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "ldEusOxu" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"type\":\"ephemeral\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"ldEusOxu\",\"custom_data\":{\"HYjKHRMLpKJp\":\"=)G[0LZ4iYuO3/V@5(sbbO9q=2,^\",\"RmWQKdliWcNK\":83,\"fYJbfLSfOYnh\":true}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/444033905
```

### Path

PUT /cardholders OR /cardholders/{id}

### Description

Upsert can be used to either update a cardholder, create a new cardholder, or return an existing cardholder.  Either an id or cuid is required for upsert. The id (in path or body), along with an updated body, can be used to update an existing cardholder; the cuid (in body) can likewise be used to update a cardholder, and can also be used to create a new cardholder, if the cuid does not match any existing cardholders. If the id or cuid provided corresponds to a pre-existing cardholder and no updated information has been included in the body, the existing cardholder will be returned.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
type | [string enum](#post-cardholder-1)* | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities.
 If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
first_name | string | 
last_name | string | 
email | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
custom_data | object | Additional data that can be added to the cardholder if needed.

See [cardholder response parameters](#response-cardholder).


## Delete cardholder

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/444033905
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



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [cardholder response parameters](#response-cardholder).


# Users
Users are internal entities, such as agents or admins, that can perform such functions as creating and deleting cardholders, fetching merchant sites, creating jobs, etc.
## Get user

```javascript
const users = await session.getUsers(34994353,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Users> users = await session.GetUsersAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["financial_institution"])}
JsonArray response = (JsonArray)session.get(34994353, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 34994353,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1979-02-07T09:11:56.574Z",
  "is_locked": true,
  "password_lifetime": 317,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_sso_agent",
  "next_rotation_on": "1975-11-05T20:30:32.553Z",
  "created_on": "1972-03-19T17:02:23.276Z",
  "last_updated_on": "1997-08-05T13:45:49.982Z",
  "username": "jsmith123",
  "financial_institution": {
    "id": 1488101669,
    "name": "FhjyjxYmjUQNkaQmuUnZAzzKctqQUdnOFNwoljBPttetVDTbaGhDaVHbnsegtLt",
    "description": "eJXKcMEpkBimKbnfinwJ",
    "lookup_key": "rwcuXOGLsVHFLsewbenscHeqftxvigoSWBSrkXYrGukdCDvHpaGGUpzIywANoeQ",
    "alternate_lookup_key": "MLniABoXyQvDsnUkXPIjKVnmZLmZZlCfsSwgrJlfpBExTdzHMtmTcbHKYcKUccv",
    "last_activity": "1971-08-19T10:14:28.644Z",
    "created_on": "2008-02-26T22:45:44.487Z",
    "last_updated_on": "1975-09-24T21:13:10.121Z"
  }
}
```

### Path

GET /cardsavr_users **(batch)** or GET /cardsavr_users/:id **(singular)**

### Description

Returns the user specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable users, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


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

**Example batch GET request path:**<br>`/cardsavr_users?ids=1,2`

#### Singular GET requests

**Singular requests** only return the user matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_users/34994353`

### <a name="response-cardsavr_user"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this user.
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | 
first_name | string | 
last_name | string | 
last_login_time | date | 
is_locked | boolean | 
password_lifetime | number | Length of time that password will remain valid.
email | string | 
is_password_update_required | boolean | 
role | string | <p>User role (cardholder_agent, cardholder_sso_agent or customer_agent) determines the user's ability to access certain endpoints and perform certain operations within the CardSavr API.</p><p>cardholder_agents can create cardholders, create card's addresses for those cardholders, create accounts for those cardholders, and post jobs for those cardholders. cardholder_sso_agents are like cardholder_agent, but cannot create cardholder or cards.</p>customer_agents can peform all actions on cardholders/accounts/, but are limited to acting on cardholders/jobs/accounts/cards within their FI (unless they are assigned to the admin FI)
next_rotation_on | date | Date of next password rotation for this user.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
username | string | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create user

```javascript
const user = await session.createUser({
  "financial_institution_id": 2107273747,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 317,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_sso_agent",
  "next_rotation_on": "1975-11-05T20:30:32.553Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 2107273747 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 317 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "cardholder_sso_agent" },
	{ "next_rotation_on", "1975-11-05T20:30:32.553Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 2107273747 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 317 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "cardholder_sso_agent" )
	.add("next_rotation_on", "1975-11-05T20:30:32.553Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":2107273747,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":317,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"cardholder_sso_agent\",\"next_rotation_on\":\"1975-11-05T20:30:32.553Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/
```

### Path

POST /cardsavr_users

### Description

Create a user and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
financial_institution_id | number | no | 
username | string | yes | 
password | string | yes | 
first_name | string | no | 
last_name | string | no | 
password_lifetime | number | no | Length of time that password will remain valid.
email | string | no | 
is_password_update_required | boolean | no | 
role | [string enum](#post-cardsavr_user-1)* | yes | <p>User role (cardholder_agent, cardholder_sso_agent or customer_agent) determines the user's ability to access certain endpoints and perform certain operations within the CardSavr API.</p><p>cardholder_agents can create cardholders, create card's addresses for those cardholders, create accounts for those cardholders, and post jobs for those cardholders. cardholder_sso_agents are like cardholder_agent, but cannot create cardholder or cards.</p>customer_agents can peform all actions on cardholders/accounts/, but are limited to acting on cardholders/jobs/accounts/cards within their FI (unless they are assigned to the admin FI)
next_rotation_on | date | no | Date of next password rotation for this user.

See [user response attributes](#response-cardsavr_user).

#### <a name="post-cardsavr_user-1"></a>string enum*
- admin
- cardholder_sso_agent
- cardholder_agent
- customer_agent
- swch_agent


## Update user

```javascript
const user = await session.updateUser(1,{
  "financial_institution_id": 1188979470,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 24,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "cardholder_sso_agent",
  "next_rotation_on": "2005-10-22T23:56:32.531Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1188979470 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 24 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "cardholder_sso_agent" },
	{ "next_rotation_on", "2005-10-22T23:56:32.531Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1188979470 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 24 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "cardholder_sso_agent" )
	.add("next_rotation_on", "2005-10-22T23:56:32.531Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1188979470,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":24,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"cardholder_sso_agent\",\"next_rotation_on\":\"2005-10-22T23:56:32.531Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/34994353
```

### Path

PUT /cardsavr_users OR /cardsavr_users/{id}

### Description

Update a user and return the updated object.  An id is required on every update request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
financial_institution_id | number | 
first_name | string | 
last_name | string | 
password_lifetime | number | Length of time that password will remain valid.
email | string | 
is_password_update_required | boolean | 
role | [string enum](#post-cardsavr_user-1)* | <p>User role (cardholder_agent, cardholder_sso_agent or customer_agent) determines the user's ability to access certain endpoints and perform certain operations within the CardSavr API.</p><p>cardholder_agents can create cardholders, create card's addresses for those cardholders, create accounts for those cardholders, and post jobs for those cardholders. cardholder_sso_agents are like cardholder_agent, but cannot create cardholder or cards.</p>customer_agents can peform all actions on cardholders/accounts/, but are limited to acting on cardholders/jobs/accounts/cards within their FI (unless they are assigned to the admin FI)
next_rotation_on | date | Date of next password rotation for this user.

See [user response parameters](#response-cardsavr_user).


## Delete user

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/34994353
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



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [user response parameters](#response-cardsavr_user).


# Financial Institutions
Financial Institution (FI) objects represent individual FIs and can be linked to users and cardholders. They also contain the configuration information that can be used to customize an FI's CardUpdatr instance, if one exists.
## Get financial institution

```javascript
const financialinstitutions = await session.getFinancialInstitutions(930427057,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = 
JsonArray response = (JsonArray)session.get(930427057, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 930427057,
  "name": "TfngUjpsCbGDYLzSFIQHjWUiRmOSaABVhnGIKAbxYoqxGFKBnsVfRRNHjFsXaQi",
  "description": "D",
  "lookup_key": "VprvMXbyFMbPFEgkgZhgtKepeQKgjfwDlswKPTfCrhCnMwuNCHIIkQkPecYdrFY",
  "alternate_lookup_key": "PaJsVFNhbklIsjqOAdbDqGxrowRawCwTYnVzBmqsHnwilkxKwauFdItbLbxwQWs",
  "last_activity": "1978-02-07T05:24:04.552Z",
  "created_on": "2000-05-03T23:11:36.988Z",
  "last_updated_on": "1979-06-15T17:00:57.518Z"
}
```

### Path

GET /financial_institutions **(batch)** or GET /financial_institutions/:id **(singular)**

### Description

Returns the financial institution specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable financial institutions, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- id
- names
- lookup_key
- exclude_lookup_keys
- alternate_lookup_key
- last_activity_min / last_activity_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/financial_institutions?ids=1,2`

#### Singular GET requests

**Singular requests** only return the financial institution matching the id provided in the path.

**Example GET request path:**<br>`/financial_institutions/930427057`

### <a name="response-financial_institution"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this financial institution.
name | string | 
description | string | 
lookup_key | string | Unique key used to identify financial institution.
alternate_lookup_key | string | Alternate lookup key; can be used in case of FI name change that does not match original lookup_key, in order to maintain backwards compatibility.
last_activity | date | Date of last cardholder creation for this financial institution
created_on | date | Date this financial institution was created on
last_updated_on | date | Date this financial institution was last updated on

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create financial institution

```javascript
const financialinstitution = await session.createFinancialInstitution({
  "name": "TfngUjpsCbGDYLzSFIQHjWUiRmOSaABVhnGIKAbxYoqxGFKBnsVfRRNHjFsXaQi",
  "description": "D",
  "lookup_key": "VprvMXbyFMbPFEgkgZhgtKepeQKgjfwDlswKPTfCrhCnMwuNCHIIkQkPecYdrFY",
  "alternate_lookup_key": "PaJsVFNhbklIsjqOAdbDqGxrowRawCwTYnVzBmqsHnwilkxKwauFdItbLbxwQWs"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "TfngUjpsCbGDYLzSFIQHjWUiRmOSaABVhnGIKAbxYoqxGFKBnsVfRRNHjFsXaQi" },
	{ "description", "D" },
	{ "lookup_key", "VprvMXbyFMbPFEgkgZhgtKepeQKgjfwDlswKPTfCrhCnMwuNCHIIkQkPecYdrFY" },
	{ "alternate_lookup_key", "PaJsVFNhbklIsjqOAdbDqGxrowRawCwTYnVzBmqsHnwilkxKwauFdItbLbxwQWs" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "TfngUjpsCbGDYLzSFIQHjWUiRmOSaABVhnGIKAbxYoqxGFKBnsVfRRNHjFsXaQi" )
	.add("description", "D" )
	.add("lookup_key", "VprvMXbyFMbPFEgkgZhgtKepeQKgjfwDlswKPTfCrhCnMwuNCHIIkQkPecYdrFY" )
	.add("alternate_lookup_key", "PaJsVFNhbklIsjqOAdbDqGxrowRawCwTYnVzBmqsHnwilkxKwauFdItbLbxwQWs" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"TfngUjpsCbGDYLzSFIQHjWUiRmOSaABVhnGIKAbxYoqxGFKBnsVfRRNHjFsXaQi\",\"description\":\"D\",\"lookup_key\":\"VprvMXbyFMbPFEgkgZhgtKepeQKgjfwDlswKPTfCrhCnMwuNCHIIkQkPecYdrFY\",\"alternate_lookup_key\":\"PaJsVFNhbklIsjqOAdbDqGxrowRawCwTYnVzBmqsHnwilkxKwauFdItbLbxwQWs\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/
```

### Path

POST /financial_institutions

### Description

Create a financial institution and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
name | string | yes | 
description | string | no | 
lookup_key | string | yes | Unique key used to identify financial institution.
alternate_lookup_key | string | no | Alternate lookup key; can be used in case of FI name change that does not match original lookup_key, in order to maintain backwards compatibility.

See [financial institution response attributes](#response-financial_institution).


## Update financial institution

```javascript
const financialinstitution = await session.updateFinancialInstitution(1,{
  "name": "RRVjwyZiedxAKBZMKRGakkrGZvqSvwcjCXYxMtzlYAFDXDfSuhrFhHKVndzVrWt",
  "description": "odXIOtkJQ",
  "lookup_key": "aMIvpPmfSjCfyLOEsudcrebFXYhotUSfqVsaMhCACRtoHbOZmbxIHhqVyVBVJeA",
  "alternate_lookup_key": "eghLafJpjhQTmodSjvFbnZjpulYqbGKgrgdkmmknSpIinfYdfrdfOsLeEEkvMgE"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "RRVjwyZiedxAKBZMKRGakkrGZvqSvwcjCXYxMtzlYAFDXDfSuhrFhHKVndzVrWt" },
	{ "description", "odXIOtkJQ" },
	{ "lookup_key", "aMIvpPmfSjCfyLOEsudcrebFXYhotUSfqVsaMhCACRtoHbOZmbxIHhqVyVBVJeA" },
	{ "alternate_lookup_key", "eghLafJpjhQTmodSjvFbnZjpulYqbGKgrgdkmmknSpIinfYdfrdfOsLeEEkvMgE" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "RRVjwyZiedxAKBZMKRGakkrGZvqSvwcjCXYxMtzlYAFDXDfSuhrFhHKVndzVrWt" )
	.add("description", "odXIOtkJQ" )
	.add("lookup_key", "aMIvpPmfSjCfyLOEsudcrebFXYhotUSfqVsaMhCACRtoHbOZmbxIHhqVyVBVJeA" )
	.add("alternate_lookup_key", "eghLafJpjhQTmodSjvFbnZjpulYqbGKgrgdkmmknSpIinfYdfrdfOsLeEEkvMgE" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"RRVjwyZiedxAKBZMKRGakkrGZvqSvwcjCXYxMtzlYAFDXDfSuhrFhHKVndzVrWt\",\"description\":\"odXIOtkJQ\",\"lookup_key\":\"aMIvpPmfSjCfyLOEsudcrebFXYhotUSfqVsaMhCACRtoHbOZmbxIHhqVyVBVJeA\",\"alternate_lookup_key\":\"eghLafJpjhQTmodSjvFbnZjpulYqbGKgrgdkmmknSpIinfYdfrdfOsLeEEkvMgE\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/930427057
```

### Path

PUT /financial_institutions OR /financial_institutions/{id}

### Description

Update a financial institution and return the updated object.  An id is required on every update request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
name | string | 
description | string | 
lookup_key | string | Unique key used to identify financial institution.
alternate_lookup_key | string | Alternate lookup key; can be used in case of FI name change that does not match original lookup_key, in order to maintain backwards compatibility.

See [financial institution response parameters](#response-financial_institution).


## Delete financial institution

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/930427057
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



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [financial institution response parameters](#response-financial_institution).


# Integrators
Integrators are applications that integrate the CardSavr API, using their own unique integrator key. An integrator name and key are required for all calls to the CardSavr API. An integrator can be associated with multiple users.
## Get integrator

```javascript
const integrators = await session.getIntegrators(1897111286,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = 
JsonArray response = (JsonArray)session.get(1897111286, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1897111286,
  "name": "qBQXGfyjNNXJMwXNDhZjkUudKgBAqJLyoISVVVRPkFsjUdZfq",
  "description": "wy",
  "current_key": "UJkVRQO5jMhfrjKptBgOPK2NyRc2Oq4AIiq7MsFFf2o=",
  "key_lifetime": 130,
  "next_rotation_on": "1971-11-28T16:57:12.086Z",
  "created_on": "1972-04-05T02:40:59.135Z",
  "last_updated_on": "1999-08-16T12:54:56.754Z"
}
```

### Path

GET /integrators **(batch)** or GET /integrators/:id **(singular)**

### Description

Returns the integrator specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable integrators, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- names
- name
- next_rotation_on_min / next_rotation_on_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/integrators?ids=1,2`

#### Singular GET requests

**Singular requests** only return the integrator matching the id provided in the path.

**Example GET request path:**<br>`/integrators/1897111286`

### <a name="response-integrator"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this integrator.
name | string | Name of integrator.
description | string | 
current_key | string | Current key for this integrator.
key_lifetime | number | Sets the duration of validity for integrator key.
next_rotation_on | date | Date of next key rotation for this integrator.
created_on | date | Date this integrator was created on
last_updated_on | date | Date this integrator was last updated on

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create integrator

```javascript
const integrator = await session.createIntegrator({
  "name": "qBQXGfyjNNXJMwXNDhZjkUudKgBAqJLyoISVVVRPkFsjUdZfq",
  "description": "wy",
  "current_key": "UJkVRQO5jMhfrjKptBgOPK2NyRc2Oq4AIiq7MsFFf2o=",
  "key_lifetime": 130,
  "next_rotation_on": "1971-11-28T16:57:12.086Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "qBQXGfyjNNXJMwXNDhZjkUudKgBAqJLyoISVVVRPkFsjUdZfq" },
	{ "description", "wy" },
	{ "current_key", "UJkVRQO5jMhfrjKptBgOPK2NyRc2Oq4AIiq7MsFFf2o=" },
	{ "key_lifetime", 130 },
	{ "next_rotation_on", "1971-11-28T16:57:12.086Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "qBQXGfyjNNXJMwXNDhZjkUudKgBAqJLyoISVVVRPkFsjUdZfq" )
	.add("description", "wy" )
	.add("current_key", "UJkVRQO5jMhfrjKptBgOPK2NyRc2Oq4AIiq7MsFFf2o=" )
	.add("key_lifetime", 130 )
	.add("next_rotation_on", "1971-11-28T16:57:12.086Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"qBQXGfyjNNXJMwXNDhZjkUudKgBAqJLyoISVVVRPkFsjUdZfq\",\"description\":\"wy\",\"current_key\":\"UJkVRQO5jMhfrjKptBgOPK2NyRc2Oq4AIiq7MsFFf2o=\",\"key_lifetime\":130,\"next_rotation_on\":\"1971-11-28T16:57:12.086Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/
```

### Path

POST /integrators

### Description

Create a integrator and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
name | string | yes | Name of integrator.
description | string | no | 
current_key | string | no | Current key for this integrator.
key_lifetime | number | no | Sets the duration of validity for integrator key.
next_rotation_on | date | no | Date of next key rotation for this integrator.

See [integrator response attributes](#response-integrator).


## Update integrator

```javascript
const integrator = await session.updateIntegrator(1,{
  "name": "lxKPsDVgPySAovHRRAAgAcpMOAEadWNPRakRwMOmHleZSmWdt",
  "description": "dGLPxCROsb",
  "current_key": "afHJ6l2d52VSLbKRohYpfNn+SuGqwo7aoPBYojH22UE=",
  "key_lifetime": 217,
  "next_rotation_on": "1999-09-29T16:31:09.620Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "lxKPsDVgPySAovHRRAAgAcpMOAEadWNPRakRwMOmHleZSmWdt" },
	{ "description", "dGLPxCROsb" },
	{ "current_key", "afHJ6l2d52VSLbKRohYpfNn+SuGqwo7aoPBYojH22UE=" },
	{ "key_lifetime", 217 },
	{ "next_rotation_on", "1999-09-29T16:31:09.620Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "lxKPsDVgPySAovHRRAAgAcpMOAEadWNPRakRwMOmHleZSmWdt" )
	.add("description", "dGLPxCROsb" )
	.add("current_key", "afHJ6l2d52VSLbKRohYpfNn+SuGqwo7aoPBYojH22UE=" )
	.add("key_lifetime", 217 )
	.add("next_rotation_on", "1999-09-29T16:31:09.620Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"lxKPsDVgPySAovHRRAAgAcpMOAEadWNPRakRwMOmHleZSmWdt\",\"description\":\"dGLPxCROsb\",\"current_key\":\"afHJ6l2d52VSLbKRohYpfNn+SuGqwo7aoPBYojH22UE=\",\"key_lifetime\":217,\"next_rotation_on\":\"1999-09-29T16:31:09.620Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/1897111286
```

### Path

PUT /integrators OR /integrators/{id}

### Description

Update a integrator and return the updated object.  An id is required on every update request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
name | string | Name of integrator.
description | string | 
current_key | string | Current key for this integrator.
key_lifetime | number | Sets the duration of validity for integrator key.
next_rotation_on | date | Date of next key rotation for this integrator.

See [integrator response parameters](#response-integrator).


## Delete integrator

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/1897111286
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



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [integrator response parameters](#response-integrator).


# Merchant sites
A merchant site object contains information, such as images URLs and hostname, for a CardSavr-supported merchant site.
## Get merchant site

```javascript
const merchantsites = await session.getMerchantSites(383508603,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = 
JsonArray response = (JsonArray)session.get(383508603, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 383508603,
  "name": "Amazon",
  "host": "amazon.com",
  "tags": [
    "Grs/DlaIr5h(-35WZaX,*/_",
    68,
    "4[uBgHKC{),JQk**ti{lWZ#SU~Z%JH"
  ],
  "interface_type": "vbs",
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
  "account_link": [
    {
      "key_name": "username",
      "label": "Username",
      "type": "initial_account_link"
    },
    {
      "key_name": "password",
      "label": "Password",
      "type": "initial_account_link",
      "secret": true
    },
    {
      "key_name": "otp",
      "label": "One Time Passcode",
      "type": ""
    }
  ],
  "messages": {
    "mfa_label": "Additional information required, this code may be sent to your phone or email address.",
    "additional_info_message": "",
    "auth_message": "Linking account."
  },
  "credit_card_page": "https://www.merchantsite.com/credit_card",
  "forgot_password_page": "https://www.merchantsite.com/forgot_password",
  "login_page": "https://www.merchantsite.com/login"
}
```

### Path

GET /merchant_sites **(batch)** or GET /merchant_sites/:id **(singular)**

### Description

Returns the merchant site specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable merchant sites, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- id
- exclude_ids
- top_ids
- name_starts_with
- hosts
- host
- exclude_hosts
- top_hosts
- host_starts_with
- tags
- image_widths

**Example batch GET request path:**<br>`/merchant_sites?ids=1,2`

#### Singular GET requests

**Singular requests** only return the merchant site matching the id provided in the path.

**Example GET request path:**<br>`/merchant_sites/383508603`

### <a name="response-merchant_site"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this merchant site.
name | string | 
host | string | For interface type 'dcs',  hostname of the DCS broker server for the merchant site; for interface type 'vbs' hostname of the merchant_site. e.g. amazon.com
tags | array | Tags for filtering desired merchant sites.  This could either be site status (e.g. prod, development), countries supported (e.g. usa, canada), or site attributes (e.g. synthetic).  Tags can also be compounded to create combinations: (e.g. ?tags=prod,usa&tags=synthetic means all sites tagged prod and usa as well as sites tagged synthetic)
interface_type | string | Type of interface agent to use with merchant. Set to 'dcs' for a site that has direct connect support; and to 'vbs' for a site using Robotic Process Automation
required_form_fields | array | Indicates the cardholder personal information fields that are required by this site.
images | array | URLs of the images for this merchant site.  Use a filter parameter of 'image_widths', a comma delimited list of widths (e.g. image_widths=64).  Tile images with these widths will be returned.  The default is 128 and 32 width images.
account_link | array | One or more property sets with key names to populated on POST/PUT /cardsavr_accounts requests, and labels to display to the end user for the type of information being requested for this site ( e.g. Username, Password, Account Number, Email, ... ) Each property contains its 'key_name', a 'label' that defines the property, a 'secret' flag (property should be masked on input like a password), and a type.  Only properties with a type of 'initial_account_link' should be presented upon initial credential collection.  For example, an input field for 'tfa' is not displayed on initial collection.  All other non-'initial_account_link' properties will be requested while the transactiion progresses and they are only listed here for informational purposes.
messages | object | Message properties to display to end users.  Supercedes the deprecated loging properties. The message properties are mfa_label: additional informaton required for mfs challenges such as a code sent to users phone or email, additional_info_message: some contextual info sent from CardSavr to aid the user interaction, auth_message: a label to display during during the authentication phase
credit_card_page | string | Merchant's credit card entry page.
forgot_password_page | string | Merchant's forgotten password page.
login_page | string | URL of login page.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

# Notifications
Notification objects define a set of actions to be triggered by certain CardSavr events, such as session completion.
## Get notification

```javascript
const notifications = await session.getNotifications(1382967771,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["financial_institution"])}
JsonArray response = (JsonArray)session.get(1382967771, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1382967771,
  "name": "Sample Notification",
  "type": "email",
  "event": "merchant_site_updates_top",
  "config": {
    "recipient": "cardholder",
    "url": null,
    "from_email": "CardUpdatr <no-reply@cardupdatr.app>",
    "return_path": "no-reply@cardupdatr.app",
    "send_email_time": null,
    "interval_length": null,
    "interval_type": null
  },
  "html_template": "dQKBHFPYlakJmkXHDhMlgR",
  "text_template": "gtHkKFoZePtqUqJtyxiPG",
  "created_on": "2009-02-28T08:16:02.142Z",
  "last_updated_on": "1984-12-12T17:55:18.475Z",
  "financial_institution": {
    "id": 601487644,
    "name": "dhbSMoboBPXFxtMlVLOgbjAPeZIBiyQWcCeLDyaAHItzXavObpRgcNRZrQMSnfr",
    "description": "zTSYatZv",
    "lookup_key": "WyKTAOQUgRKCMZIAspQDQuSOhYUtgRpADYKxLDOkkQjpNQzuvWxPtbrRgUZJhwr",
    "alternate_lookup_key": "GqmlqnSyMJgqcsCSlkrmsFtcDGXSawxAcTFgiloojCxBexGQvlEqcAZXTnGZkEP",
    "last_activity": "1989-11-27T14:28:27.729Z",
    "created_on": "2021-06-26T21:31:30.651Z",
    "last_updated_on": "1998-11-11T15:29:45.883Z"
  }
}
```

### Path

GET /notifications **(batch)** or GET /notifications/:id **(singular)**

### Description

Returns the notification specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable notifications, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- financial_institution_ids
- names
- type
- events
- event
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/notifications?ids=1,2`

#### Singular GET requests

**Singular requests** only return the notification matching the id provided in the path.

**Example GET request path:**<br>`/notifications/1382967771`

### <a name="response-notification"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this notification.
name | string | Name of this notification.
type | string | Notification type (e.g. webhook or email).
event | string | Event that will triger the notification (e.g. session complete).
config | object | 
html_template | string | Overrides the default CardUpdatr html email template (for email notifications).
text_template | string | Overrides the default CardUpdatr text email template (for email notifications).
created_on | date | Date this notification was created on
last_updated_on | date | Date this notification was last updated on
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | ID of the financial institution associated with this notification.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create notification

```javascript
const notification = await session.createNotification({
  "financial_institution_id": 260143700,
  "name": "Sample Notification",
  "type": "email",
  "event": "merchant_site_updates_top",
  "config": {
    "recipient": "cardholder",
    "url": null,
    "from_email": "CardUpdatr <no-reply@cardupdatr.app>",
    "return_path": "no-reply@cardupdatr.app",
    "send_email_time": null,
    "interval_length": null,
    "interval_type": null
  },
  "html_template": "dQKBHFPYlakJmkXHDhMlgR",
  "text_template": "gtHkKFoZePtqUqJtyxiPG"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 260143700 },
	{ "name", "Sample Notification" },
	{ "type", "email" },
	{ "event", "merchant_site_updates_top" },
	{ "html_template", "dQKBHFPYlakJmkXHDhMlgR" },
	{ "text_template", "gtHkKFoZePtqUqJtyxiPG" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 260143700 )
	.add("name", "Sample Notification" )
	.add("type", "email" )
	.add("event", "merchant_site_updates_top" )
	.add("html_template", "dQKBHFPYlakJmkXHDhMlgR" )
	.add("text_template", "gtHkKFoZePtqUqJtyxiPG" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":260143700,\"name\":\"Sample Notification\",\"type\":\"email\",\"event\":\"merchant_site_updates_top\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"dQKBHFPYlakJmkXHDhMlgR\",\"text_template\":\"gtHkKFoZePtqUqJtyxiPG\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/
```

### Path

POST /notifications

### Description

Create a notification and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
financial_institution_id | number | yes | ID of the financial institution associated with this notification.
name | string | yes | Name of this notification.
type | [string enum](#post-notification-1)* | yes | Notification type (e.g. webhook or email).
event | [string enum](#post-notification-2)** | yes | Event that will triger the notification (e.g. session complete).
config | object | no | 
html_template | string | no | Overrides the default CardUpdatr html email template (for email notifications).
text_template | string | no | Overrides the default CardUpdatr text email template (for email notifications).

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
  "event": "session_complete",
  "config": {
    "recipient": "cardholder",
    "url": null,
    "from_email": "CardUpdatr <no-reply@cardupdatr.app>",
    "return_path": "no-reply@cardupdatr.app",
    "send_email_time": null,
    "interval_length": null,
    "interval_type": null
  },
  "html_template": "ESErPGtLNeaQykGHcSVgTixKM",
  "text_template": "SVdZSNtSbNDKwKvJgnUqnlw"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Sample Notification" },
	{ "type", "webhook" },
	{ "event", "session_complete" },
	{ "html_template", "ESErPGtLNeaQykGHcSVgTixKM" },
	{ "text_template", "SVdZSNtSbNDKwKvJgnUqnlw" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Sample Notification" )
	.add("type", "webhook" )
	.add("event", "session_complete" )
	.add("html_template", "ESErPGtLNeaQykGHcSVgTixKM" )
	.add("text_template", "SVdZSNtSbNDKwKvJgnUqnlw" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"Sample Notification\",\"type\":\"webhook\",\"event\":\"session_complete\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"ESErPGtLNeaQykGHcSVgTixKM\",\"text_template\":\"SVdZSNtSbNDKwKvJgnUqnlw\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/1382967771
```

### Path

PUT /notifications OR /notifications/{id}

### Description

Update a notification and return the updated object.  An id is required on every update request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
name | string | Name of this notification.
type | [string enum](#post-notification-1)* | Notification type (e.g. webhook or email).
event | [string enum](#post-notification-2)** | Event that will triger the notification (e.g. session complete).
config | object | 
html_template | string | Overrides the default CardUpdatr html email template (for email notifications).
text_template | string | Overrides the default CardUpdatr text email template (for email notifications).

See [notification response parameters](#response-notification).


## Delete notification

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/1382967771
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



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [notification response parameters](#response-notification).


# Notification results
Notification result objects are records of an attempt/attempts to send a notification, indicating success/failure and additional relevant information.
## Get notification result

```javascript
const notificationresults = await session.getNotificationResults(630250387,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["notification"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<NotificationResults> notificationresults = await session.GetNotificationResultsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["notification"])}
JsonArray response = (JsonArray)session.get(630250387, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 630250387,
  "last_attempt_date": "1994-05-28T00:36:06.786Z",
  "fi_lookup_key": "WUnlfDJdhBgKaHfuYKTuSLKyvycWzFTLiXQnSTRGgTxiSClcZTSenLKhBvPHmVa",
  "cuid": "yKFbGvfGenvyXhYtLvfLbeXOCAIcplW",
  "status": "failure",
  "attempts": 1922247943,
  "notification_data": {
    "SAZEHYGgzIjz": "[_,",
    "nfMahAyFPtTk": 23,
    "tBJKFbwdQyVV": true
  },
  "created_on": "2001-07-13T13:35:54.742Z",
  "last_updated_on": "1999-01-28T23:45:57.222Z",
  "notification": {
    "id": 174309715,
    "name": "Sample Notification",
    "type": "webhook",
    "event": "merchant_site_updates_top",
    "config": {
      "recipient": "cardholder",
      "url": null,
      "from_email": "CardUpdatr <no-reply@cardupdatr.app>",
      "return_path": "no-reply@cardupdatr.app",
      "send_email_time": null,
      "interval_length": null,
      "interval_type": null
    },
    "html_template": "MHKDNXgpzLGzajonbpmcITnTUAFpz",
    "text_template": "KKRAfGEIqc",
    "created_on": "2014-12-21T20:54:36.495Z",
    "last_updated_on": "1976-07-25T03:57:49.265Z"
  }
}
```

### Path

GET /notification_results **(batch)** or GET /notification_results/:id **(singular)**

### Description

Returns the notification result specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable notification results, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


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

**Example batch GET request path:**<br>`/notification_results?ids=1,2`

#### Singular GET requests

**Singular requests** only return the notification result matching the id provided in the path.

**Example GET request path:**<br>`/notification_results/630250387`

### <a name="response-notification_result"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this notification.
last_attempt_date | date | Date of last attempt to post this notification.
fi_lookup_key | string | FI lookup key associated with the attempted notification.
cuid | string | External unique ID for cardholder--can be account_id, email address, phone number, etc.  A random number will be gnenerated if not provided.
status | string | Status of the notification attempt.
attempts | number | Number of attempts made to send or post notification.
notification_data | object | Data sent with the notification.
created_on | date | Date this notification result was created on
last_updated_on | date | Date this notification result was last updated on
notification_id | number (fk) [notifications](#notifications) | ID of the attempted notification.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create notification result

```javascript
const notificationresult = await session.createNotificationResult({
  "notification_id": 1838285361,
  "fi_lookup_key": "WUnlfDJdhBgKaHfuYKTuSLKyvycWzFTLiXQnSTRGgTxiSClcZTSenLKhBvPHmVa",
  "cuid": "yKFbGvfGenvyXhYtLvfLbeXOCAIcplW",
  "status": "failure",
  "attempts": 1922247943,
  "notification_data": {
    "SAZEHYGgzIjz": "[_,",
    "nfMahAyFPtTk": 23,
    "tBJKFbwdQyVV": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 1838285361 },
	{ "fi_lookup_key", "WUnlfDJdhBgKaHfuYKTuSLKyvycWzFTLiXQnSTRGgTxiSClcZTSenLKhBvPHmVa" },
	{ "cuid", "yKFbGvfGenvyXhYtLvfLbeXOCAIcplW" },
	{ "status", "failure" },
	{ "attempts", 1922247943 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 1838285361 )
	.add("fi_lookup_key", "WUnlfDJdhBgKaHfuYKTuSLKyvycWzFTLiXQnSTRGgTxiSClcZTSenLKhBvPHmVa" )
	.add("cuid", "yKFbGvfGenvyXhYtLvfLbeXOCAIcplW" )
	.add("status", "failure" )
	.add("attempts", 1922247943 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":1838285361,\"fi_lookup_key\":\"WUnlfDJdhBgKaHfuYKTuSLKyvycWzFTLiXQnSTRGgTxiSClcZTSenLKhBvPHmVa\",\"cuid\":\"yKFbGvfGenvyXhYtLvfLbeXOCAIcplW\",\"status\":\"failure\",\"attempts\":1922247943,\"notification_data\":{\"SAZEHYGgzIjz\":\"[_,\",\"nfMahAyFPtTk\":23,\"tBJKFbwdQyVV\":true}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notification_results/
```

### Path

POST /notification_results

### Description

Create a notification result and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
notification_id | number | yes | ID of the attempted notification.
fi_lookup_key | string | yes | FI lookup key associated with the attempted notification.
cuid | string | yes | External unique ID for cardholder--can be account_id, email address, phone number, etc.  A random number will be gnenerated if not provided.
status | [string enum](#post-notification_result-1)* | yes | Status of the notification attempt.
attempts | number | yes | Number of attempts made to send or post notification.
notification_data | object | no | Data sent with the notification.

See [notification result response attributes](#response-notification_result).

#### <a name="post-notification_result-1"></a>string enum*
- success
- failure

# Single-site jobs
Single-site job objects contain the information necessary to place a payment card on a merchant site, as well as status information about the card placement attempt. They are linked to a single cardholder, account, card, and merchant site.
## Get single-site job

```javascript
const singlesitejobs = await session.getSingleSiteJobs(165886079,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_card","cardsavr_account","credential_requests"])});
```

```csharp
Paging paging = new Paging() { PageLength = 100, IsDescending = true, Page = 1, Sort = "id" };
HttpRequestHeaders headers = new HttpRequestMessage().Headers;
string[] array = { "cardholder","merchant_site","cardsavr_card" };
var json = JsonConvert.SerializeObject(array);
headers.Add("x-cardsavr-hydration", json);
var query = new {ids = 1};
QueryDef qd = new QueryDef(query);
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(qd,paging,headers);
```

```java
Headers headers = session.createHeaders();
headers.paging = Json.createObjectBuilder().add("page", 1).add("page_length", 5).add("is_descending", true).add("sort", "id").build();
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_card","cardsavr_account","credential_requests"])}
JsonArray response = (JsonArray)session.get(165886079, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 165886079,
  "status": "INITIATED",
  "status_message": "r",
  "termination_type": "PROCESS_FAILURE",
  "custom_data": {
    "ibMaPssnjacC": "1{XU^EPKf(I!ru!43i",
    "gqlBtHkRHaYi": 85,
    "BYBVMihkmHNV": false
  },
  "notification_sent": false,
  "time_elapsed": 94010780,
  "started_on": "2017-02-20T17:10:51.270Z",
  "completed_on": "2005-03-22T19:46:41.501Z",
  "created_on": "1971-01-21T16:56:30.249Z",
  "last_updated_on": "2007-04-28T04:31:09.618Z",
  "cardholder": {
    "id": 849825572,
    "type": "persistent_all",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "yxrMTTOdeDZivjwsFGFNK",
    "custom_data": {
      "ZegHIsBHiwco": ")$728Iv3Q+X@jiby-wQ3",
      "nyVKRhmiEdww": 77,
      "ACkPffJEGYIH": false
    },
    "created_on": "1981-05-04T09:42:20.630Z",
    "last_updated_on": "2020-05-28T09:56:20.728Z",
    "cuid": "RUuG"
  },
  "cardsavr_card": {
    "id": 1941014294,
    "type": "Visa",
    "expiration_month": 12,
    "expiration_year": 24,
    "name_on_card": "Jane Smith",
    "nickname": "Jane's VISA",
    "custom_data": {
      "ezRFwLvWRQiR": "]buiD{o00YN_=PJ",
      "TvgVZHezwbPH": 56,
      "NjXGwFRBOloS": true
    },
    "created_on": "2021-02-23T22:47:50.251Z",
    "last_updated_on": "2006-01-23T11:35:32.410Z",
    "par": "cjVbhKKkOAXaqtCfpvSefgewktJcM",
    "customer_key": "tcqqqlJxLhAfLVMpZlRLeDW"
  },
  "cardsavr_account": {
    "id": 1442204739,
    "last_password_update": "2016-05-19T11:34:31.173Z",
    "last_saved_card": "1998-09-22T03:30:44.840Z",
    "created_on": "2004-01-29T09:59:46.642Z",
    "last_updated_on": "2010-03-06T07:03:49.726Z",
    "customer_key": "TCKLILKd"
  }
}
```

### Path

GET /place_card_on_single_site_jobs **(batch)** or GET /place_card_on_single_site_jobs/:id **(singular)**

### Description

Returns the single-site job specified by the provided ID

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable single-site jobs, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


### Filter parameters
- ids / id (in path)
- cardholder_ids
- card_ids
- account_ids
- status
- status_include / status_exclude
- termination_type
- termination_types_include / termination_types_exclude
- notification_sent
- time_elapsed_min / time_elapsed_max
- started_on_min / started_on_max
- completed_on_min / completed_on_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/place_card_on_single_site_jobs?ids=1,2`

#### Singular GET requests

**Singular requests** only return the single-site job matching the id provided in the path.

**Example GET request path:**<br>`/place_card_on_single_site_jobs/165886079`

To hydrate all credential requests currently associated with a job, include credential_requests in the hydration header (see example at right).`

### <a name="response-place_card_on_single_site_job"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this job.
card_id | number (fk) [cards](#cards) | ID of card associated with this job.
status | string | Current status of job (e.g. pending_tfa). These names are dynamic and change frequently, so it is best to use status_message to communicate with cardholders.
status_message | string | Human readable representation of the jobs status.
termination_type | string | Final termination status of a job. (BILLABLE, SITE_INTERACTION_FAILURE, USER_DATA_FAILURE, PROCESS FAILURE)
custom_data | object | 
notification_sent | boolean | Indicates if a notification has been sent or posted for this job.
time_elapsed | number | Amount of time elapsed since the creation of the job.
started_on | date | Time when job started.
completed_on | date | Timestamp of job completion.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) [cardholders](#cardholders) | ID of cardholder associated with this job.
account_id | number (fk) [accounts](#accounts) | ID of account associated with this job.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create single-site job

```javascript
const singlesitejob = await session.createSingleSiteJob({
  "cardholder_id": 1765906120,
  "card_id": 1066085670,
  "account_id": 925681353,
  "status": "INITIATED",
  "custom_data": {
    "ibMaPssnjacC": "1{XU^EPKf(I!ru!43i",
    "gqlBtHkRHaYi": 85,
    "BYBVMihkmHNV": false
  },
  "notification_sent": false,
  "time_elapsed": 94010780,
  "started_on": "2017-02-20T17:10:51.270Z",
  "completed_on": "2005-03-22T19:46:41.501Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1765906120 },
	{ "card_id", 1066085670 },
	{ "account_id", 925681353 },
	{ "status", "INITIATED" },
	{ "notification_sent", false },
	{ "time_elapsed", 94010780 },
	{ "started_on", "2017-02-20T17:10:51.270Z" },
	{ "completed_on", "2005-03-22T19:46:41.501Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1765906120 )
	.add("card_id", 1066085670 )
	.add("account_id", 925681353 )
	.add("status", "INITIATED" )
	.add("notification_sent", false )
	.add("time_elapsed", 94010780 )
	.add("started_on", "2017-02-20T17:10:51.270Z" )
	.add("completed_on", "2005-03-22T19:46:41.501Z" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1765906120,\"card_id\":1066085670,\"account_id\":925681353,\"status\":\"INITIATED\",\"custom_data\":{\"ibMaPssnjacC\":\"1{XU^EPKf(I!ru!43i\",\"gqlBtHkRHaYi\":85,\"BYBVMihkmHNV\":false},\"notification_sent\":false,\"time_elapsed\":94010780,\"started_on\":\"2017-02-20T17:10:51.270Z\",\"completed_on\":\"2005-03-22T19:46:41.501Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/
```

### Path

POST /place_card_on_single_site_jobs

### Description

Create a single-site job and return the created object.

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.



<aside class="notice"><a href=#request-hydration-on-post>Request hydration</a> can be used on this endpoint. This allows you to create a new single-site job and all referential entities in a single POST request.
</aside>

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
cardholder_id | number | yes | ID of cardholder associated with this job.
card_id | number | no | ID of card associated with this job.
account_id | number | yes | ID of account associated with this job.
status | [string enum](#post-place_card_on_single_site_job-1)* | no | Current status of job (e.g. pending_tfa). These names are dynamic and change frequently, so it is best to use status_message to communicate with cardholders.
custom_data | object | no | 
notification_sent | boolean | no | Indicates if a notification has been sent or posted for this job.
time_elapsed | number | no | Amount of time elapsed since the creation of the job.
started_on | date | no | Time when job started.
completed_on | date | no | Timestamp of job completion.

See [single-site job response attributes](#response-place_card_on_single_site_job).

#### <a name="post-place_card_on_single_site_job-1"></a>string enum*
- INITIATED
- REQUESTED
- IN_PROGRESS
- AUTH
- CREDS_RECEIVED
- TFA_CODE_RECEIVED
- TFA_SUBMITTED
- LOGIN_SUBMITTED
- SUBMITTED
- PENDING_NEWCREDS
- PENDING_TFA
- PENDING
- UPDATING
- QUEUED
- SITE_BLOCKED
- CANCEL_REQUESTED
- CANCELLED
- CANCELLED_QUICKSTART
- ABANDONED
- ABANDONED_QUICKSTART
- KILLED
- ACCOUNT_SETUP_INCOMPLETE
- ACCOUNT_NOT_SUPPORTED
- TFA_NOT_SUPPORTED
- PREPAID_ACCOUNT
- INACTIVE_ACCOUNT
- MISSING_CARD_DATA
- card_form_failed
- INVALID_CARD
- MULTI_ACCOUNT_CARD_NOT_ALLOWED
- INVALID_ADDRESS
- PASSWORD_RESET_REQUIRED
- BUNDLED_SUBSCRIPTION
- FREE_ACCOUNT
- ACCOUNT_LOCKED
- INVALID_EXPIRATION_DATE
- EXPIRED_CARD
- INVALID_CVV
- INVALID_NETWORK
- MAX_LIMIT_OF_STORED_CARDS
- PAYMENT_PROCESSOR_DOWN
- DUPLICATE_CARD
- SUCCESSFUL
- UNSUPPORTED_CAPTCHA
- TIMEOUT_CAPTCHA
- TIMEOUT_CREDENTIALS
- TIMEOUT_TFA
- TOO_MANY_LOGIN_FAILURES
- TOO_MANY_TFA_FAILURES
- INVALID_SECURITY_ANSWERS
- INVALID_CREDENTIAL_REQUEST_TYPE
- UNSUCCESSFUL
- PROXY_PROBE_FAILED
- VBS_TIMEOUT
- VBS_ERROR
- UNKNOWN_INTERFACE_TYPE
- UNIMPLEMENTED_JOB_TYPE
- UNKNOWN_JOB_TYPE
- INCOMPLETE_JOB_DATA

#### <a name="post-place_card_on_single_site_job-2"></a>string enum**
- USER_DATA_FAILURE
- PROCESS_FAILURE
- SITE_INTERACTION_FAILURE
- BILLABLE
- NEVER_STARTED

<aside class="notice">Update calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Update single-site job

```javascript
const singlesitejob = await session.updateSingleSiteJob(1,{
  "card_id": 1433620101,
  "status": "PASSWORD_RESET_REQUIRED",
  "custom_data": {
    "CFhZWiLVuvhY": "Wzu(51MdJzTv*^O$,bdw",
    "nuALXhdTdvAi": 23,
    "xocUjEPXtiUe": true
  },
  "notification_sent": true,
  "time_elapsed": 1949006917,
  "started_on": "2000-10-24T16:19:54.470Z",
  "completed_on": "1981-05-05T04:06:30.215Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 1433620101 },
	{ "status", "PASSWORD_RESET_REQUIRED" },
	{ "notification_sent", true },
	{ "time_elapsed", 1949006917 },
	{ "started_on", "2000-10-24T16:19:54.470Z" },
	{ "completed_on", "1981-05-05T04:06:30.215Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 1433620101 )
	.add("status", "PASSWORD_RESET_REQUIRED" )
	.add("notification_sent", true )
	.add("time_elapsed", 1949006917 )
	.add("started_on", "2000-10-24T16:19:54.470Z" )
	.add("completed_on", "1981-05-05T04:06:30.215Z" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":1433620101,\"status\":\"PASSWORD_RESET_REQUIRED\",\"custom_data\":{\"CFhZWiLVuvhY\":\"Wzu(51MdJzTv*^O$,bdw\",\"nuALXhdTdvAi\":23,\"xocUjEPXtiUe\":true},\"notification_sent\":true,\"time_elapsed\":1949006917,\"started_on\":\"2000-10-24T16:19:54.470Z\",\"completed_on\":\"1981-05-05T04:06:30.215Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/165886079
```

### Path

PUT /place_card_on_single_site_jobs OR /place_card_on_single_site_jobs/{id}

### Description

Update a single-site job and return the updated object.  An id is required on every update request.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

### Body parameters

Parameter | Type | Description 
-------- | ---- | ---------
card_id | number | ID of card associated with this job.
status | [string enum](#post-place_card_on_single_site_job-1)* | Current status of job (e.g. pending_tfa). These names are dynamic and change frequently, so it is best to use status_message to communicate with cardholders.
custom_data | object | 
notification_sent | boolean | Indicates if a notification has been sent or posted for this job.
time_elapsed | number | Amount of time elapsed since the creation of the job.
started_on | date | Time when job started.
completed_on | date | Timestamp of job completion.

See [single-site job response parameters](#response-place_card_on_single_site_job).

<aside class="notice">Update calls to /place_card_on_single_site_jobs require the cardholder's personal cardholder_safe_key header to encrypt and save the safe when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete single-site job

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/165886079
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



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.


See [single-site job response parameters](#response-place_card_on_single_site_job).

