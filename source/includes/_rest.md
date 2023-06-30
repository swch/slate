
# Accounts
Account objects contain the account information, such as username and password, for a particular cardhoder. They are used to log in to a cardholder's account for placing a payment card.
## Get account

```javascript
const accounts = await session.getAccounts(748803509,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","merchant_site","cardsavr_card"])});
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
JsonArray response = (JsonArray)session.get(748803509, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 748803509,
  "last_password_update": "2018-09-27T18:19:28.697Z",
  "last_saved_card": "2008-05-04T14:47:45.502Z",
  "created_on": "1989-02-14T20:40:50.575Z",
  "last_updated_on": "1993-06-15T00:08:30.063Z",
  "cardholder": {
    "id": 168082380,
    "type": "ephemeral",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "hGPFAvCTrev",
    "webhook_url": "https://mywebhooks.com/this",
    "custom_data": {
      "pQZHjntqCBhX": "#^5,-Q[fe{K.jxuL_7v}M(.m#Je~Z(kD",
      "YRDRbDljLduc": 19,
      "BrrBfyaAjgkF": true
    },
    "created_on": "1978-05-22T15:35:56.905Z",
    "last_updated_on": "1980-05-07T08:05:17.066Z",
    "cuid": "MktECziPFamDXXRlAlPdRhlUiOOj"
  },
  "merchant_site": {
    "id": 616172289,
    "name": "Amazon",
    "note": "Bd",
    "host": "amazon.com",
    "tags": [
      "-%",
      67,
      "x9DXkQ~KKH.H"
    ],
    "interface_type": "dcs",
    "job_type": "BILL_PAY",
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
    "script_directory": "tuorWuXnrXbKkj",
    "record_final_site_artifacts": false,
    "puppeteer_screenshot": false,
    "login_page": "https://www.merchantsite.com/login",
    "forgot_password_page": "https://www.merchantsite.com/forgot_password",
    "credit_card_page": "https://www.merchantsite.com/credit_card",
    "wallet_page": "xqwmHuKzNKtQyHfZGuET",
    "merchant_sso_group": "EEkTPjHalHspKYCzcXEc",
    "tier": 477116587
  },
  "cardsavr_card": {
    "id": 595496327,
    "type": "Visa",
    "expiration_month": 12,
    "expiration_year": 24,
    "name_on_card": "Jane Smith",
    "nickname": "Jane's VISA",
    "custom_data": {
      "HiwGmTSZsRbc": "+UQZ${~dinm,",
      "uuIppPeAiUEM": 76,
      "lbZnlUCgWXKs": false
    },
    "created_on": "2008-09-27T18:26:16.079Z",
    "last_updated_on": "1986-07-11T06:24:03.555Z",
    "par": "PDqYNkmabwCFpicNOGlyjpDiWjLJA",
    "customer_key": "ldYC"
  },
  "customer_key": "JX"
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

**Example GET request path:**<br>`/cardsavr_accounts/748803509`

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
  "cardholder_id": 931747943,
  "merchant_site_id": 755020082,
  "customer_key": "JX",
  "last_card_placed_id": 392267388,
  "account_link": {
    "username": "jsmith123",
    "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 931747943 },
	{ "merchant_site_id", 755020082 },
	{ "customer_key", "JX" },
	{ "last_card_placed_id", 392267388 }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 931747943 )
	.add("merchant_site_id", 755020082 )
	.add("customer_key", "JX" )
	.add("last_card_placed_id", 392267388 )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":931747943,\"merchant_site_id\":755020082,\"customer_key\":\"JX\",\"last_card_placed_id\":392267388,\"account_link\":{\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}}"
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
account_link | object | no | One or more properties with key:value pairs that are required for authenticated a user.  These properties are either included as part of initial account collection, or they are requested as part of a credential_request.  An error will be returned if all properties are not provided for a given credential_request. The set of key:value pairs for a site are specified in the merchant site info returned from GET /merchant_sites as 'account_link'.  If credentials are being saved as part of a credential_response, the corresponding envelope_id must be supplied as a header.

See [account response attributes](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the account_link when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Upsert account

```javascript
const account = await session.updateAccount(1,{
  "last_card_placed_id": 1706948797,
  "account_link": {
    "username": "jsmith123",
    "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
  }
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 1706948797 }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 1706948797 )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":1706948797,\"account_link\":{\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/748803509
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
account_link | object | One or more properties with key:value pairs that are required for authenticated a user.  These properties are either included as part of initial account collection, or they are requested as part of a credential_request.  An error will be returned if all properties are not provided for a given credential_request. The set of key:value pairs for a site are specified in the merchant site info returned from GET /merchant_sites as 'account_link'.  If credentials are being saved as part of a credential_response, the corresponding envelope_id must be supplied as a header.

See [account response parameters](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the account_link when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete account

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/748803509
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
const addresses = await session.getAddresses(1608094256,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder"])});
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
JsonArray response = (JsonArray)session.get(1608094256, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1608094256,
  "address1": "UEsDqOXDPKrrPMCIILOGaBuXECDWpkaSsahywLOBDItKFJjkyQhXuBqRXtBvBlHuMcKSNhiGOWdDeKMZZToIceJklLepkEmCuks",
  "address2": "fBFzTiEPZPRqKxzYAbNaDZwXAjRhnipCEoniZoXzBtDsHlVNqjBvYtjVsjOnTicAKWBaTuYblGnQqDrSSsVacVpVFenorTydNwX",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "vxNaprANzBUq@ZrGsvR.gYc",
  "phone_number": "2065555555",
  "created_on": "1998-03-15T05:54:09.463Z",
  "last_updated_on": "2019-12-10T22:12:22.564Z",
  "cardholder": {
    "id": 6105303,
    "type": "persistent_all",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "CnZHXNnwVOyJBrUCwdGiWBSc",
    "webhook_url": "https://mywebhooks.com/this",
    "custom_data": {
      "TPTMWAcPhdyV": "u)yItZ/U9)rp2NPiE",
      "qAnxajhOtpAD": 69,
      "plQKzMBjRVVK": true
    },
    "created_on": "1987-12-21T04:23:33.489Z",
    "last_updated_on": "2011-01-07T02:25:45.018Z",
    "cuid": "QQvggBCWStPhQyOUUGrHJLjfz"
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

**Example GET request path:**<br>`/cardsavr_addresses/1608094256`

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
  "cardholder_id": 1580504474,
  "address1": "UEsDqOXDPKrrPMCIILOGaBuXECDWpkaSsahywLOBDItKFJjkyQhXuBqRXtBvBlHuMcKSNhiGOWdDeKMZZToIceJklLepkEmCuks",
  "address2": "fBFzTiEPZPRqKxzYAbNaDZwXAjRhnipCEoniZoXzBtDsHlVNqjBvYtjVsjOnTicAKWBaTuYblGnQqDrSSsVacVpVFenorTydNwX",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "vxNaprANzBUq@ZrGsvR.gYc",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1580504474 },
	{ "address1", "UEsDqOXDPKrrPMCIILOGaBuXECDWpkaSsahywLOBDItKFJjkyQhXuBqRXtBvBlHuMcKSNhiGOWdDeKMZZToIceJklLepkEmCuks" },
	{ "address2", "fBFzTiEPZPRqKxzYAbNaDZwXAjRhnipCEoniZoXzBtDsHlVNqjBvYtjVsjOnTicAKWBaTuYblGnQqDrSSsVacVpVFenorTydNwX" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "vxNaprANzBUq@ZrGsvR.gYc" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1580504474 )
	.add("address1", "UEsDqOXDPKrrPMCIILOGaBuXECDWpkaSsahywLOBDItKFJjkyQhXuBqRXtBvBlHuMcKSNhiGOWdDeKMZZToIceJklLepkEmCuks" )
	.add("address2", "fBFzTiEPZPRqKxzYAbNaDZwXAjRhnipCEoniZoXzBtDsHlVNqjBvYtjVsjOnTicAKWBaTuYblGnQqDrSSsVacVpVFenorTydNwX" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "vxNaprANzBUq@ZrGsvR.gYc" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1580504474,\"address1\":\"UEsDqOXDPKrrPMCIILOGaBuXECDWpkaSsahywLOBDItKFJjkyQhXuBqRXtBvBlHuMcKSNhiGOWdDeKMZZToIceJklLepkEmCuks\",\"address2\":\"fBFzTiEPZPRqKxzYAbNaDZwXAjRhnipCEoniZoXzBtDsHlVNqjBvYtjVsjOnTicAKWBaTuYblGnQqDrSSsVacVpVFenorTydNwX\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"vxNaprANzBUq@ZrGsvR.gYc\",\"phone_number\":\"2065555555\"}"
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
  "address1": "FEJcFBhITmEhjqqvtpnQbpUgaXGnjpupgRiGFYwQNFRDzvLNrWNnJcXIORMSxBaoCWyZeDorUvOJdpZHiFkjBJXpFElmFCxeWTa",
  "address2": "nFfQUbiVjcBwYfbMaBzZNKtlaohvbxMbbOylvlNjZBlTemaazGhsLxChCTSpjRqvusWSBxFtdpKykcuUThSSEATTpwEankBVIVj",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "OldCJapmnArR@AMazJr.ZAd",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "FEJcFBhITmEhjqqvtpnQbpUgaXGnjpupgRiGFYwQNFRDzvLNrWNnJcXIORMSxBaoCWyZeDorUvOJdpZHiFkjBJXpFElmFCxeWTa" },
	{ "address2", "nFfQUbiVjcBwYfbMaBzZNKtlaohvbxMbbOylvlNjZBlTemaazGhsLxChCTSpjRqvusWSBxFtdpKykcuUThSSEATTpwEankBVIVj" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "OldCJapmnArR@AMazJr.ZAd" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "FEJcFBhITmEhjqqvtpnQbpUgaXGnjpupgRiGFYwQNFRDzvLNrWNnJcXIORMSxBaoCWyZeDorUvOJdpZHiFkjBJXpFElmFCxeWTa" )
	.add("address2", "nFfQUbiVjcBwYfbMaBzZNKtlaohvbxMbbOylvlNjZBlTemaazGhsLxChCTSpjRqvusWSBxFtdpKykcuUThSSEATTpwEankBVIVj" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "OldCJapmnArR@AMazJr.ZAd" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"FEJcFBhITmEhjqqvtpnQbpUgaXGnjpupgRiGFYwQNFRDzvLNrWNnJcXIORMSxBaoCWyZeDorUvOJdpZHiFkjBJXpFElmFCxeWTa\",\"address2\":\"nFfQUbiVjcBwYfbMaBzZNKtlaohvbxMbbOylvlNjZBlTemaazGhsLxChCTSpjRqvusWSBxFtdpKykcuUThSSEATTpwEankBVIVj\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"OldCJapmnArR@AMazJr.ZAd\",\"phone_number\":\"2065555555\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1608094256
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1608094256
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
const bins = await session.getBins(564156928,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(564156928, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 564156928,
  "custom_data": {
    "UORQhHOIEQrA": "UvD)40$G2s1pgQ",
    "vbWLIwILcFWM": 26,
    "XkmNvTZMhmrJ": false
  },
  "created_on": "2016-01-01T22:53:14.254Z",
  "last_updated_on": "1972-07-30T19:01:00.963Z",
  "financial_institution": {
    "id": 1084876263,
    "name": "YAcIqsquLPVULYWwyMSCAFEvZWvyHykDmpdaRCrBZhdAFKreIfdwcNMOiqZwlzs",
    "description": "lfvUnOcyhcfyzvouAluBbnO",
    "lookup_key": "FbPQwetmxUYQohcEBIwySrYJlnxmSijkaopmfFyJVKdJdAJncNsfHhdmvwWNjFa",
    "alternate_lookup_key": "YwvbEMqWDAKkEZTCrsMDElRjnqObLmhGAiYpKInrKxhvFglkOWrWZMYOfkXdspZ",
    "last_activity": "2009-06-01T23:36:36.662Z",
    "created_on": "1974-11-15T10:24:58.878Z",
    "last_updated_on": "2006-03-01T20:18:07.654Z"
  },
  "bank_identification_number": "84826548"
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

**Example GET request path:**<br>`/cardsavr_bins/564156928`

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
  "financial_institution_id": 1850202805,
  "bank_identification_number": "84826548",
  "custom_data": {
    "UORQhHOIEQrA": "UvD)40$G2s1pgQ",
    "vbWLIwILcFWM": 26,
    "XkmNvTZMhmrJ": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1850202805 },
	{ "bank_identification_number", "84826548" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1850202805 )
	.add("bank_identification_number", "84826548" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1850202805,\"bank_identification_number\":\"84826548\",\"custom_data\":{\"UORQhHOIEQrA\":\"UvD)40$G2s1pgQ\",\"vbWLIwILcFWM\":26,\"XkmNvTZMhmrJ\":false}}"
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
  "financial_institution_id": 1738517175,
  "custom_data": {
    "ecZlCYQbgHgM": "67[/AJk(D",
    "VSGUtVberNtn": 42,
    "dcbzPiHpeOcT": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1738517175 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1738517175 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1738517175,\"custom_data\":{\"ecZlCYQbgHgM\":\"67[/AJk(D\",\"VSGUtVberNtn\":42,\"dcbzPiHpeOcT\":true}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/564156928
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/564156928
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
const cardplacementresults = await session.getCardPlacementResults(926177931,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution","merchant_site","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(926177931, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 926177931,
  "merchant_site_hostname": "qaUYGLVAcxbObcYyACTlZJCyJVrycEFlASQjQEmVoJETZTQawoWoANXvufkeEBmdqcYhYxQTnhqxtxeCOjYAWefwbaiTHXfqshqHnkCXQzmTKSWonnJltUJdAxtIFsnbISIrXdkDKXBpUgpMfWNJjVysoufXwAHtKQHyplfLTlMYqtlvhEaVbJhqfHhRNDThgwPzeDwxsLzoMyiAWSWRwMPkyWQfaxWOIjCkItPFzudSvLgMlWProjOrBqHPqG",
  "meta_key": "MB9810411",
  "fi_name": "DKTlAjplVxNLtAOfXBcXTnzeFaWHXvRuQgJHLVvcmcKMvXhkWgbRRxDQPJZwNYX",
  "bank_identification_number": "83402535",
  "cuid": "umtdUcrjgvweVucTcmKURWFHEbIMHSW",
  "par": "PnUejrVDPdSLzJTXrOeECXMRenlpU",
  "card_customer_key": "YYWEQPuww",
  "account_customer_key": "lIqiKs",
  "status": "SUCCESSFUL",
  "status_message": "Successful",
  "termination_type": "BILLABLE",
  "custom_data": {
    "qWkHnEWfvnlI": "hRaDBu-kucPL&y=h=7uC(PA[r9xF,h9n",
    "fkjRIOUTgZNy": 62,
    "LvNOaqgZUWXq": true
  },
  "time_elapsed": 992997918,
  "first_6": "wCiwfwhjPPvrLphHxapxvvoIDExUDKJL",
  "first_7": "xreJdKRlNuKmrYFqZdrmqnxZvJDPKfRs",
  "first_8": "jSHbkzHjwUSuZeLWWLbLCxSCRujKsLjO",
  "trace": "QHlTnAnKjLTORZEbRfCNxDCWovVVv",
  "email_sent": true,
  "completed_on": "1976-11-06T01:25:25.270Z",
  "created_on": "2007-11-20T13:02:35.064Z",
  "last_updated_on": "1998-01-11T20:06:02.604Z",
  "financial_institution": {
    "id": 197394753,
    "name": "HvAqqgPoirKBkDSNjyqCbvYoOGoUKByYeaRBQxApTUImQeIpAQXfEUbWbWEIQkk",
    "description": "sbCeDaBMSKADwCmeFfOqOIJbmucwxG",
    "lookup_key": "OcpfNXhyjzjQUAPjbJqftyUzTBsObqbwyUDbTBKrACtrpUUEdGKXvLKPnqqXbWA",
    "alternate_lookup_key": "VdGTMsaIFRpQLxCFZAeIMRzwDvSFIrzxgFjaOERjtpxEEFRDLizREFwaoCCIXmr",
    "last_activity": "2004-03-18T19:16:22.134Z",
    "created_on": "2006-06-25T09:52:01.718Z",
    "last_updated_on": "1993-07-08T13:44:33.496Z"
  },
  "merchant_site": {
    "id": 1394668862,
    "name": "Amazon",
    "note": "DRliAWmlZUWCezmQDnukgabchZlr",
    "host": "amazon.com",
    "tags": [
      ")XFs[XU",
      73,
      "z4~S7"
    ],
    "interface_type": "rpa_loopback",
    "job_type": "CARD_PLACEMENT",
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
    "script_directory": "QcHrEiilUVziLymQgW",
    "record_final_site_artifacts": true,
    "puppeteer_screenshot": false,
    "login_page": "https://www.merchantsite.com/login",
    "forgot_password_page": "https://www.merchantsite.com/forgot_password",
    "credit_card_page": "https://www.merchantsite.com/credit_card",
    "wallet_page": "TxwjDJFDQtRGeLseMidfSqIUjobVi",
    "merchant_sso_group": "EFTxLdzZcXhatjT",
    "tier": 1643017266
  },
  "cardsavr_bin": {
    "id": 992219166,
    "custom_data": {
      "ILsdEHCLVoKP": "M)X@p,aK@_GH{E@xX9^It^",
      "wBNtKljQmkUI": 53,
      "npDWFprJqBev": true
    },
    "created_on": "1986-05-22T12:26:06.407Z",
    "last_updated_on": "2004-09-14T01:49:14.475Z",
    "bank_identification_number": "61344038"
  },
  "place_card_on_single_site_job_id": 1009071360
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

**Example GET request path:**<br>`/card_placement_results/926177931`

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

# Cardholder sessions
A record of information associated with the session of a carholder -- it terminates after explicit completion or 15 minutes of inactivity.
## Get cardholder session


# Cards
A card object contains information about a payment card for a specific cardholder. Card objects are used to populate payment information on merchant sites.
## Get card

```javascript
const cards = await session.getCards(167073021,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_address","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(167073021, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 167073021,
  "type": "Visa",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "SnKfHaaBcARU": "X6WRkYXm@p=91XHT5b9F8f.RwP5",
    "mEqSVeLFCUoa": 19,
    "LEtdvYFZDmJk": false
  },
  "created_on": "1994-10-01T16:07:34.715Z",
  "last_updated_on": "1993-11-26T12:52:21.801Z",
  "cardholder": {
    "id": 1032583526,
    "type": "persistent_creds",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "tQTPbLxsaLMyTRhnBcWYsPfTHRb",
    "webhook_url": "https://mywebhooks.com/this",
    "custom_data": {
      "TzCkDIjGPndD": "Z",
      "TYOkJtxLlhBh": 33,
      "mVuROkBEkZZr": true
    },
    "created_on": "1986-10-04T23:37:12.833Z",
    "last_updated_on": "1996-06-02T19:37:23.909Z",
    "cuid": "tUTOTUNRXLthusJmks"
  },
  "cardsavr_address": {
    "id": 1900306420,
    "address1": "cXvdfTQZBmgOtBZNVUfJSsqqWWNNlqAHmARvsUOsEdkgFfroKBUuYVJbpIBSTHjnsgfoHtxffmkUTwiMxgcuaaLNVNxehWDbZTd",
    "address2": "neMfIOHMzpHYxPqGZkigWUfWoLRUgrYKDxXJpUEKdCAeZnBkJVzEDkmWfOHXVwoWcWaRgfbMTFDbCWbVCtJCgFWxgNBHmFxDDZN",
    "city": "Seattle",
    "subnational": "WA",
    "postal_code": "98177",
    "postal_other": "98177-0124",
    "country": "USA",
    "is_primary": false,
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "lzqtQeDnPwOc@eYbxvo.TfP",
    "phone_number": "2065555555",
    "created_on": "1997-05-22T20:43:50.383Z",
    "last_updated_on": "1998-05-24T00:45:44.209Z"
  },
  "cardsavr_bin": {
    "id": 1569286641,
    "custom_data": {
      "dRAnOhPvEvzb": "ppB$-#i9/#e~wVK",
      "fLgBkwpYodxl": 3,
      "FiAkKmymBsrT": false
    },
    "created_on": "1977-07-20T20:08:24.089Z",
    "last_updated_on": "2010-11-14T13:02:47.783Z",
    "bank_identification_number": "76236048"
  },
  "par": "zmwXzaYkrCxbedjfMmBACnByTfpga",
  "customer_key": "twZyoRauOxouSjFPmwNzUqgRsW"
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

**Example GET request path:**<br>`/cardsavr_cards/167073021`

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
  "cardholder_id": 1375903879,
  "address_id": 403471264,
  "bin_id": 312650169,
  "par": "zmwXzaYkrCxbedjfMmBACnByTfpga",
  "customer_key": "twZyoRauOxouSjFPmwNzUqgRsW",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "SnKfHaaBcARU": "X6WRkYXm@p=91XHT5b9F8f.RwP5",
    "mEqSVeLFCUoa": 19,
    "LEtdvYFZDmJk": false
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1375903879 },
	{ "address_id", 403471264 },
	{ "bin_id", 312650169 },
	{ "par", "zmwXzaYkrCxbedjfMmBACnByTfpga" },
	{ "customer_key", "twZyoRauOxouSjFPmwNzUqgRsW" },
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
	.add("cardholder_id", 1375903879 )
	.add("address_id", 403471264 )
	.add("bin_id", 312650169 )
	.add("par", "zmwXzaYkrCxbedjfMmBACnByTfpga" )
	.add("customer_key", "twZyoRauOxouSjFPmwNzUqgRsW" )
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
curl -d "{\"cardholder_id\":1375903879,\"address_id\":403471264,\"bin_id\":312650169,\"par\":\"zmwXzaYkrCxbedjfMmBACnByTfpga\",\"customer_key\":\"twZyoRauOxouSjFPmwNzUqgRsW\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"Jane's VISA\",\"custom_data\":{\"SnKfHaaBcARU\":\"X6WRkYXm@p=91XHT5b9F8f.RwP5\",\"mEqSVeLFCUoa\":19,\"LEtdvYFZDmJk\":false}}"
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
cvv | string | no | 
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
  "bin_id": 600277668,
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "Jane's VISA",
  "custom_data": {
    "WKZWvWpXRDqG": "pjfhP{6&W11%o91$B(",
    "JSmPXaNPNKpU": 0,
    "TrxqmJiAqBqt": true
  },
  "pan": "4111111111111111"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "bin_id", 600277668 },
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
	.add("bin_id", 600277668 )
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
curl -d "{\"bin_id\":600277668,\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"Jane's VISA\",\"custom_data\":{\"WKZWvWpXRDqG\":\"pjfhP{6&W11%o91$B(\",\"JSmPXaNPNKpU\":0,\"TrxqmJiAqBqt\":true},\"pan\":\"4111111111111111\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/167073021
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/167073021
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
const cardholders = await session.getCardholders(2052053876,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution","integrator"])});
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
headers.hydration = {'x-cardsavr-hydration':JSON.stringify(["financial_institution","integrator"])}
JsonArray response = (JsonArray)session.get(2052053876, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2052053876,
  "type": "persistent_creds",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "ajWgfWqAjWcYmmpKcAAsaPyuJrkKtCn",
  "webhook_url": "https://mywebhooks.com/this",
  "custom_data": {
    "VwyDguSUQUmG": "EIi-*kIZ0Ib1Eo[D~=w",
    "GWMsFYUOSxHb": 50,
    "uhZtZYcwVQge": false
  },
  "created_on": "2010-02-09T16:33:38.704Z",
  "last_updated_on": "1981-11-07T15:22:01.256Z",
  "financial_institution": {
    "id": 2115173949,
    "name": "srpGIoucLgMuUfmEUatnxhXqCzNbgriKkdRJLEcprIednzKGUMZvEGuJusoZNUb",
    "description": "A",
    "lookup_key": "jmiXyZPzonFPeYLmYcZBWOeMsoAigSKrllNjfAWHmETxSppYaGPqHWasVuGiOYb",
    "alternate_lookup_key": "xyFQwVfLAuQpCzKmTVegXHzqGBxIhapsnPyCjJYLVfXBjLWlPZXqpHcEllXOhhC",
    "last_activity": "2020-10-07T22:20:31.946Z",
    "created_on": "1972-02-02T12:07:45.232Z",
    "last_updated_on": "2006-04-06T20:36:25.467Z"
  },
  "integrator": {
    "id": 2097282712,
    "name": "GXeXEdMYtyruNalIDKpwquNiXYzaFrjyTBTymcSYnPQGtDXMF",
    "description": "uzBmXGFwDtVQI",
    "current_key": "a19dWTuTyD3Zh38GN+plPV+aOxzZleLOeAT/J6EPJ8k=",
    "key_lifetime": 18,
    "next_rotation_on": "1993-01-29T07:43:58.247Z",
    "created_on": "2005-05-03T09:32:58.059Z",
    "last_updated_on": "1979-08-20T19:55:40.463Z"
  },
  "cuid": "WBtFPRGnrrweGyznIlyqgwftEdUHcWZ"
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

**Example GET request path:**<br>`/cardholders/2052053876`

### <a name="response-cardholder"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this cardholder.
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | 
type | string | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities. If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
first_name | string | 
last_name | string | 
email | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
webhook_url | string | A cardholder specific url for posting job reults following the end of a session.  This overrides the FI global settiings in the portal.
custom_data | object | Additional data that can be added to the cardholder if needed.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cuid | string | External unique ID for cardholder--can be account_id, email address, phone number, etc.  A random number will be gnenerated if not provided.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create cardholder

```javascript
const cardholder = await session.createCardholder({
  "cuid": "WBtFPRGnrrweGyznIlyqgwftEdUHcWZ",
  "type": "persistent_creds",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "ajWgfWqAjWcYmmpKcAAsaPyuJrkKtCn",
  "webhook_url": "https://mywebhooks.com/this",
  "custom_data": {
    "VwyDguSUQUmG": "EIi-*kIZ0Ib1Eo[D~=w",
    "GWMsFYUOSxHb": 50,
    "uhZtZYcwVQge": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cuid", "WBtFPRGnrrweGyznIlyqgwftEdUHcWZ" },
	{ "type", "persistent_creds" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "ajWgfWqAjWcYmmpKcAAsaPyuJrkKtCn" },
	{ "webhook_url", "https://mywebhooks.com/this" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cuid", "WBtFPRGnrrweGyznIlyqgwftEdUHcWZ" )
	.add("type", "persistent_creds" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "ajWgfWqAjWcYmmpKcAAsaPyuJrkKtCn" )
	.add("webhook_url", "https://mywebhooks.com/this" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"cuid\":\"WBtFPRGnrrweGyznIlyqgwftEdUHcWZ\",\"type\":\"persistent_creds\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"ajWgfWqAjWcYmmpKcAAsaPyuJrkKtCn\",\"webhook_url\":\"https://mywebhooks.com/this\",\"custom_data\":{\"VwyDguSUQUmG\":\"EIi-*kIZ0Ib1Eo[D~=w\",\"GWMsFYUOSxHb\":50,\"uhZtZYcwVQge\":false}}"
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
type | [string enum](#post-cardholder-1)* | no | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities. If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
first_name | string | no | 
last_name | string | no | 
email | string | no | 
meta_key | string | no | Key used for billing record identification; automatically generated during card creation.
webhook_url | string | no | A cardholder specific url for posting job reults following the end of a session.  This overrides the FI global settiings in the portal.
custom_data | object | no | Additional data that can be added to the cardholder if needed.

See [cardholder response attributes](#response-cardholder).

#### <a name="post-cardholder-1"></a>string enum*
- ephemeral
- persistent_creds
- persistent_all


## Upsert cardholder

```javascript
const cardholder = await session.updateCardholder(1,{
  "type": "persistent_all",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "RoQkMmmjfddDyOWsuY",
  "webhook_url": "https://mywebhooks.com/this",
  "custom_data": {
    "ZgwzxjzsNuZA": "^WmHy~vTM7M04EvUuhxF",
    "pSENczytTjyr": 100,
    "qUkwNPrLEBLc": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "type", "persistent_all" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "RoQkMmmjfddDyOWsuY" },
	{ "webhook_url", "https://mywebhooks.com/this" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("type", "persistent_all" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "RoQkMmmjfddDyOWsuY" )
	.add("webhook_url", "https://mywebhooks.com/this" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"type\":\"persistent_all\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"RoQkMmmjfddDyOWsuY\",\"webhook_url\":\"https://mywebhooks.com/this\",\"custom_data\":{\"ZgwzxjzsNuZA\":\"^WmHy~vTM7M04EvUuhxF\",\"pSENczytTjyr\":100,\"qUkwNPrLEBLc\":true}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/2052053876
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
type | [string enum](#post-cardholder-1)* | It is critical to understand the behavior associated with each cardholder type.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities. If not storing CardSavr ids within your application, you can look up cards and accounts using the corresponding customer_key. 
first_name | string | 
last_name | string | 
email | string | 
meta_key | string | Key used for billing record identification; automatically generated during card creation.
webhook_url | string | A cardholder specific url for posting job reults following the end of a session.  This overrides the FI global settiings in the portal.
custom_data | object | Additional data that can be added to the cardholder if needed.

See [cardholder response parameters](#response-cardholder).


## Delete cardholder

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/2052053876
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
const users = await session.getUsers(504966318,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(504966318, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 504966318,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "2004-03-21T04:15:14.445Z",
  "is_locked": false,
  "password_lifetime": 352,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_sso_agent",
  "next_rotation_on": "2014-09-09T20:11:25.423Z",
  "created_on": "2006-05-27T11:23:53.933Z",
  "last_updated_on": "2020-03-28T23:06:30.626Z",
  "username": "jsmith123",
  "financial_institution": {
    "id": 1984027226,
    "name": "AHpmyNyJqtrRKNtcVzQPzTdyKVLIspkHqughvfTGoyvMFHmmiIwfzKGximxTaXO",
    "description": "PkobKR",
    "lookup_key": "JDZUZGdjWXXorYEhOMgsTvzDQtwghIgqJRvEiajvCShxmFSWFirpnsGDZRHKYkI",
    "alternate_lookup_key": "zExcrLcbJLbntJvdGxNzgRkPHFwQUaQHqnUgkWHRQeoLEgYlZFZLpaLCsXobeGl",
    "last_activity": "2009-01-24T17:41:52.764Z",
    "created_on": "2017-09-30T06:32:50.604Z",
    "last_updated_on": "1996-07-04T12:14:00.413Z"
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

**Example GET request path:**<br>`/cardsavr_users/504966318`

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
  "financial_institution_id": 1443022894,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 352,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_sso_agent",
  "next_rotation_on": "2014-09-09T20:11:25.423Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1443022894 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 352 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "cardholder_sso_agent" },
	{ "next_rotation_on", "2014-09-09T20:11:25.423Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1443022894 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 352 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "cardholder_sso_agent" )
	.add("next_rotation_on", "2014-09-09T20:11:25.423Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1443022894,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":352,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"cardholder_sso_agent\",\"next_rotation_on\":\"2014-09-09T20:11:25.423Z\"}"
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
  "financial_institution_id": 1014116873,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 153,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "cardholder_sso_agent",
  "next_rotation_on": "1983-03-09T04:30:57.049Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1014116873 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 153 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "cardholder_sso_agent" },
	{ "next_rotation_on", "1983-03-09T04:30:57.049Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1014116873 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 153 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "cardholder_sso_agent" )
	.add("next_rotation_on", "1983-03-09T04:30:57.049Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1014116873,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":153,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"cardholder_sso_agent\",\"next_rotation_on\":\"1983-03-09T04:30:57.049Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/504966318
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/504966318
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
const financialinstitutions = await session.getFinancialInstitutions(1820083481,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(1820083481, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1820083481,
  "name": "pocAWBzubbxvFWhtvUFWjbSBzQsNVubCoUZCZssSISHkoDzBDguOEgijxEnOITi",
  "description": "NVJ",
  "lookup_key": "AAppomItrjyGgwKboLhULNRkaCIvhZWohtJxVWdSAqejLPVlbsssftYlosWVueO",
  "alternate_lookup_key": "AMgpvgDCgSXcUTnNSkqCfaJaIDPMFrGXVMqtbAZVumOAfOGNqsrhiMRgDSuKXiQ",
  "last_activity": "2001-06-10T14:45:27.680Z",
  "created_on": "1970-03-28T12:15:06.574Z",
  "last_updated_on": "1984-03-22T21:05:21.924Z"
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

**Example GET request path:**<br>`/financial_institutions/1820083481`

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
  "name": "pocAWBzubbxvFWhtvUFWjbSBzQsNVubCoUZCZssSISHkoDzBDguOEgijxEnOITi",
  "description": "NVJ",
  "lookup_key": "AAppomItrjyGgwKboLhULNRkaCIvhZWohtJxVWdSAqejLPVlbsssftYlosWVueO",
  "alternate_lookup_key": "AMgpvgDCgSXcUTnNSkqCfaJaIDPMFrGXVMqtbAZVumOAfOGNqsrhiMRgDSuKXiQ"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "pocAWBzubbxvFWhtvUFWjbSBzQsNVubCoUZCZssSISHkoDzBDguOEgijxEnOITi" },
	{ "description", "NVJ" },
	{ "lookup_key", "AAppomItrjyGgwKboLhULNRkaCIvhZWohtJxVWdSAqejLPVlbsssftYlosWVueO" },
	{ "alternate_lookup_key", "AMgpvgDCgSXcUTnNSkqCfaJaIDPMFrGXVMqtbAZVumOAfOGNqsrhiMRgDSuKXiQ" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "pocAWBzubbxvFWhtvUFWjbSBzQsNVubCoUZCZssSISHkoDzBDguOEgijxEnOITi" )
	.add("description", "NVJ" )
	.add("lookup_key", "AAppomItrjyGgwKboLhULNRkaCIvhZWohtJxVWdSAqejLPVlbsssftYlosWVueO" )
	.add("alternate_lookup_key", "AMgpvgDCgSXcUTnNSkqCfaJaIDPMFrGXVMqtbAZVumOAfOGNqsrhiMRgDSuKXiQ" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"pocAWBzubbxvFWhtvUFWjbSBzQsNVubCoUZCZssSISHkoDzBDguOEgijxEnOITi\",\"description\":\"NVJ\",\"lookup_key\":\"AAppomItrjyGgwKboLhULNRkaCIvhZWohtJxVWdSAqejLPVlbsssftYlosWVueO\",\"alternate_lookup_key\":\"AMgpvgDCgSXcUTnNSkqCfaJaIDPMFrGXVMqtbAZVumOAfOGNqsrhiMRgDSuKXiQ\"}"
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
  "name": "sLzHgPiwxkPcPErGHAmWzkHLSRKaafnPDQEDgepJmEMZFfjfxloNDUmIKsaqyRb",
  "description": "VIMxkViaaBPXlFHWcMrXAYie",
  "lookup_key": "DCEFFYsXoUCrKSqXNaKJPWxEbCjkBwUHYIlqctAzvvNjsFQzLWfKVKmkEdqdUVT",
  "alternate_lookup_key": "kLrwOfAaBFjPhyiqlbAPBKgeOzYBlQnusuKvIOZfYuWZbLuLCvGaDHjlElPUyfz"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "sLzHgPiwxkPcPErGHAmWzkHLSRKaafnPDQEDgepJmEMZFfjfxloNDUmIKsaqyRb" },
	{ "description", "VIMxkViaaBPXlFHWcMrXAYie" },
	{ "lookup_key", "DCEFFYsXoUCrKSqXNaKJPWxEbCjkBwUHYIlqctAzvvNjsFQzLWfKVKmkEdqdUVT" },
	{ "alternate_lookup_key", "kLrwOfAaBFjPhyiqlbAPBKgeOzYBlQnusuKvIOZfYuWZbLuLCvGaDHjlElPUyfz" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "sLzHgPiwxkPcPErGHAmWzkHLSRKaafnPDQEDgepJmEMZFfjfxloNDUmIKsaqyRb" )
	.add("description", "VIMxkViaaBPXlFHWcMrXAYie" )
	.add("lookup_key", "DCEFFYsXoUCrKSqXNaKJPWxEbCjkBwUHYIlqctAzvvNjsFQzLWfKVKmkEdqdUVT" )
	.add("alternate_lookup_key", "kLrwOfAaBFjPhyiqlbAPBKgeOzYBlQnusuKvIOZfYuWZbLuLCvGaDHjlElPUyfz" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"sLzHgPiwxkPcPErGHAmWzkHLSRKaafnPDQEDgepJmEMZFfjfxloNDUmIKsaqyRb\",\"description\":\"VIMxkViaaBPXlFHWcMrXAYie\",\"lookup_key\":\"DCEFFYsXoUCrKSqXNaKJPWxEbCjkBwUHYIlqctAzvvNjsFQzLWfKVKmkEdqdUVT\",\"alternate_lookup_key\":\"kLrwOfAaBFjPhyiqlbAPBKgeOzYBlQnusuKvIOZfYuWZbLuLCvGaDHjlElPUyfz\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/1820083481
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
https://api.INSTANCE.cardsavr.io/financial_institutions/1820083481
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
const integrators = await session.getIntegrators(31246125,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(31246125, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 31246125,
  "name": "yxtpVaoiDFguuxRlAqnsmdxUJrDyArQVwrOsOdgFGDRXJxpSj",
  "description": "cjVfmSmsAPzLuGxp",
  "current_key": "aLE3Gs6Kuy0+Lqrn1A2qJs64R3nY/c1Zbb7k9p2V4AE=",
  "key_lifetime": 16,
  "next_rotation_on": "2005-08-18T04:17:35.218Z",
  "created_on": "2005-10-24T11:24:06.930Z",
  "last_updated_on": "1981-02-02T06:31:48.711Z"
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

**Example GET request path:**<br>`/integrators/31246125`

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
  "name": "yxtpVaoiDFguuxRlAqnsmdxUJrDyArQVwrOsOdgFGDRXJxpSj",
  "description": "cjVfmSmsAPzLuGxp",
  "current_key": "aLE3Gs6Kuy0+Lqrn1A2qJs64R3nY/c1Zbb7k9p2V4AE=",
  "key_lifetime": 16,
  "next_rotation_on": "2005-08-18T04:17:35.218Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "yxtpVaoiDFguuxRlAqnsmdxUJrDyArQVwrOsOdgFGDRXJxpSj" },
	{ "description", "cjVfmSmsAPzLuGxp" },
	{ "current_key", "aLE3Gs6Kuy0+Lqrn1A2qJs64R3nY/c1Zbb7k9p2V4AE=" },
	{ "key_lifetime", 16 },
	{ "next_rotation_on", "2005-08-18T04:17:35.218Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "yxtpVaoiDFguuxRlAqnsmdxUJrDyArQVwrOsOdgFGDRXJxpSj" )
	.add("description", "cjVfmSmsAPzLuGxp" )
	.add("current_key", "aLE3Gs6Kuy0+Lqrn1A2qJs64R3nY/c1Zbb7k9p2V4AE=" )
	.add("key_lifetime", 16 )
	.add("next_rotation_on", "2005-08-18T04:17:35.218Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"yxtpVaoiDFguuxRlAqnsmdxUJrDyArQVwrOsOdgFGDRXJxpSj\",\"description\":\"cjVfmSmsAPzLuGxp\",\"current_key\":\"aLE3Gs6Kuy0+Lqrn1A2qJs64R3nY/c1Zbb7k9p2V4AE=\",\"key_lifetime\":16,\"next_rotation_on\":\"2005-08-18T04:17:35.218Z\"}"
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
  "name": "YVqKFhrkYitMwXGJiLODjKpBKzlACEFyHdAJsGqiwlwSbYBFp",
  "description": "ZpENpHnSxktcAJJaDtRggsChxFKfkT",
  "current_key": "yVnk0zoep+vaUWx+DmU5HOSDtmyw9IWznmzVyMXB5bY=",
  "key_lifetime": 309,
  "next_rotation_on": "2021-11-08T06:49:10.597Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "YVqKFhrkYitMwXGJiLODjKpBKzlACEFyHdAJsGqiwlwSbYBFp" },
	{ "description", "ZpENpHnSxktcAJJaDtRggsChxFKfkT" },
	{ "current_key", "yVnk0zoep+vaUWx+DmU5HOSDtmyw9IWznmzVyMXB5bY=" },
	{ "key_lifetime", 309 },
	{ "next_rotation_on", "2021-11-08T06:49:10.597Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "YVqKFhrkYitMwXGJiLODjKpBKzlACEFyHdAJsGqiwlwSbYBFp" )
	.add("description", "ZpENpHnSxktcAJJaDtRggsChxFKfkT" )
	.add("current_key", "yVnk0zoep+vaUWx+DmU5HOSDtmyw9IWznmzVyMXB5bY=" )
	.add("key_lifetime", 309 )
	.add("next_rotation_on", "2021-11-08T06:49:10.597Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"YVqKFhrkYitMwXGJiLODjKpBKzlACEFyHdAJsGqiwlwSbYBFp\",\"description\":\"ZpENpHnSxktcAJJaDtRggsChxFKfkT\",\"current_key\":\"yVnk0zoep+vaUWx+DmU5HOSDtmyw9IWznmzVyMXB5bY=\",\"key_lifetime\":309,\"next_rotation_on\":\"2021-11-08T06:49:10.597Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/31246125
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
https://api.INSTANCE.cardsavr.io/integrators/31246125
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
const merchantsites = await session.getMerchantSites(2135566514,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(2135566514, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2135566514,
  "name": "Amazon",
  "note": "QbAxaWyDpzvvcBL",
  "host": "amazon.com",
  "tags": [
    "jQ.xF#,B",
    64,
    "ZfmmDt6^"
  ],
  "interface_type": "rpa",
  "job_type": "BILL_PAY",
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
  "script_directory": "GqXdbaCkhLYYoLeJ",
  "record_final_site_artifacts": false,
  "puppeteer_screenshot": false,
  "login_page": "https://www.merchantsite.com/login",
  "forgot_password_page": "https://www.merchantsite.com/forgot_password",
  "credit_card_page": "https://www.merchantsite.com/credit_card",
  "wallet_page": "QAWVo",
  "merchant_sso_group": "YXemchHGsdxz",
  "tier": 2116748016
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

**Example GET request path:**<br>`/merchant_sites/2135566514`

### <a name="response-merchant_site"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this merchant site.
name | string | 
note | string | Human-readable note about the site for developers
host | string | For interface type 'dcs',  hostname of the DCS broker server for the merchant site; for interface type 'vbs' hostname of the merchant_site. e.g. amazon.com
tags | array | Tags for filtering desired merchant sites.  This could either be site status (e.g. prod, development), countries supported (e.g. usa, canada), or site attributes (e.g. synthetic).  Tags can also be compounded to create combinations: (e.g. ?tags=prod,usa&tags=synthetic means all sites tagged prod and usa as well as sites tagged synthetic)
interface_type | string | Type of interface agent to use with merchant. Set to 'dcs' for a site that has direct connect support; and to 'vbs' for a site using Robotic Process Automation
job_type | string | Type of job this site supports. Card placement or bill payment
required_form_fields | array | Indicates the cardholder personal information fields that are required by this site.
images | array | URLs of the images for this merchant site.  Use a filter parameter of 'image_widths', a comma delimited list of widths (e.g. image_widths=64).  Tile images with these widths will be returned.  The default is 128 and 32 width images.
account_link | array | One or more property sets with key names to populated on POST/PUT /cardsavr_accounts requests, and labels to display to the end user for the type of information being requested for this site ( e.g. Username, Password, Account Number, Email, ... ) Each property contains its 'key_name', a 'label' that defines the property, a 'secret' flag (property should be masked on input like a password), and a type.  Only properties with a type of 'initial_account_link' should be presented upon initial credential collection.  For example, an input field for 'tfa' is not displayed on initial collection.  All other non-'initial_account_link' properties will be requested while the transactiion progresses and they are only listed here for informational purposes.
messages | object | Message properties to display to end users.  Supercedes the deprecated loging properties. The message properties are mfa_label: additional informaton required for mfs challenges such as a code sent to users phone or email, additional_info_message: some contextual info sent from CardSavr to aid the user interaction, auth_message: a label to display during during the authentication phase
script_directory | string | Optional override for the name of the directory to lookup scripts in (default is host)
record_final_site_artifacts | boolean | Take a snapshot of html and a screenshot of the final merchant site. Disabling this can speed up task cleanup.
puppeteer_screenshot | boolean | Use puppeteer to take a screenshot of site for debugging.
login_page | string | URL of login page.
forgot_password_page | string | Merchant's forgotten password page.
credit_card_page | string | Merchant's credit card entry page.
wallet_page | string | URL of the site's wallet page, where the is a list of last 4 card numbers.
merchant_sso_group | string | Default group a site rolls up to. Jobs for the same user account should not run simultaneously.
tier | number | Site's tier based on perceived card usage on that site.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

# Notifications
Notification objects define a set of actions to be triggered by certain CardSavr events, such as session completion.
## Get notification

```javascript
const notifications = await session.getNotifications(1578105573,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(1578105573, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1578105573,
  "name": "Sample Notification",
  "type": "email",
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
  "html_template": "LprDUX",
  "text_template": "KzQKAvIQKurch",
  "created_on": "2014-04-15T10:07:37.066Z",
  "last_updated_on": "2021-10-10T06:32:47.166Z",
  "financial_institution": {
    "id": 1439708486,
    "name": "XkkhRackccztxaSiOcDszdNclxGwtoAanODieSqEOcbnxYdpZfIlENvTPLOpcOT",
    "description": "TCTpUSdLiMzuCdGDyXqKlZEZkhmVsOd",
    "lookup_key": "QbtYOQYtgVGMSAupafaxOzCBkHxEdcfsLYiTWZkgeNXhpToRBLOlaDcXMGecrSZ",
    "alternate_lookup_key": "nLngICuJnqpFlhHhyfnzSbnlPUGbvlkXdSLQhcfspVbCakpiXGJpLrBOgBNdziy",
    "last_activity": "1999-06-25T16:39:44.003Z",
    "created_on": "1996-06-27T16:22:08.324Z",
    "last_updated_on": "1976-09-25T03:41:21.056Z"
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

**Example GET request path:**<br>`/notifications/1578105573`

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
  "financial_institution_id": 1522322712,
  "name": "Sample Notification",
  "type": "email",
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
  "html_template": "LprDUX",
  "text_template": "KzQKAvIQKurch"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1522322712 },
	{ "name", "Sample Notification" },
	{ "type", "email" },
	{ "event", "session_complete" },
	{ "html_template", "LprDUX" },
	{ "text_template", "KzQKAvIQKurch" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1522322712 )
	.add("name", "Sample Notification" )
	.add("type", "email" )
	.add("event", "session_complete" )
	.add("html_template", "LprDUX" )
	.add("text_template", "KzQKAvIQKurch" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1522322712,\"name\":\"Sample Notification\",\"type\":\"email\",\"event\":\"session_complete\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"LprDUX\",\"text_template\":\"KzQKAvIQKurch\"}"
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
  "type": "email",
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
  "html_template": "lCcEES",
  "text_template": "RnqWnLVtywjLkDUkMawzUyuH"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Sample Notification" },
	{ "type", "email" },
	{ "event", "session_complete" },
	{ "html_template", "lCcEES" },
	{ "text_template", "RnqWnLVtywjLkDUkMawzUyuH" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Sample Notification" )
	.add("type", "email" )
	.add("event", "session_complete" )
	.add("html_template", "lCcEES" )
	.add("text_template", "RnqWnLVtywjLkDUkMawzUyuH" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"Sample Notification\",\"type\":\"email\",\"event\":\"session_complete\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"lCcEES\",\"text_template\":\"RnqWnLVtywjLkDUkMawzUyuH\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/1578105573
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
https://api.INSTANCE.cardsavr.io/notifications/1578105573
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
const notificationresults = await session.getNotificationResults(40663104,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["notification"])});
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
JsonArray response = (JsonArray)session.get(40663104, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 40663104,
  "last_attempt_date": "1976-11-09T14:33:16.978Z",
  "fi_lookup_key": "slIuTcmBJfmjYizzPVcqjTYBCjMGLzmpsasdkaDOKoayDlhNHtkwausXlGGRRbN",
  "cuid": "E",
  "status": "failure",
  "attempts": 1933477389,
  "notification_data": {
    "okTsjGAxpjsk": "._)$ttfA",
    "yhipWQUjZBmH": 49,
    "hAjlStWTkQLJ": false
  },
  "created_on": "2022-02-10T04:31:12.096Z",
  "last_updated_on": "2023-02-23T11:47:15.677Z",
  "notification": {
    "id": 830044788,
    "name": "Sample Notification",
    "type": "email",
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
    "html_template": "EXeTUgt",
    "text_template": "LmPyUGcGBSxtVsAkMON",
    "created_on": "1973-12-15T20:07:28.991Z",
    "last_updated_on": "1976-11-04T09:02:58.567Z"
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

**Example GET request path:**<br>`/notification_results/40663104`

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
  "notification_id": 2068170707,
  "fi_lookup_key": "slIuTcmBJfmjYizzPVcqjTYBCjMGLzmpsasdkaDOKoayDlhNHtkwausXlGGRRbN",
  "cuid": "E",
  "status": "failure",
  "attempts": 1933477389,
  "notification_data": {
    "okTsjGAxpjsk": "._)$ttfA",
    "yhipWQUjZBmH": 49,
    "hAjlStWTkQLJ": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 2068170707 },
	{ "fi_lookup_key", "slIuTcmBJfmjYizzPVcqjTYBCjMGLzmpsasdkaDOKoayDlhNHtkwausXlGGRRbN" },
	{ "cuid", "E" },
	{ "status", "failure" },
	{ "attempts", 1933477389 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 2068170707 )
	.add("fi_lookup_key", "slIuTcmBJfmjYizzPVcqjTYBCjMGLzmpsasdkaDOKoayDlhNHtkwausXlGGRRbN" )
	.add("cuid", "E" )
	.add("status", "failure" )
	.add("attempts", 1933477389 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":2068170707,\"fi_lookup_key\":\"slIuTcmBJfmjYizzPVcqjTYBCjMGLzmpsasdkaDOKoayDlhNHtkwausXlGGRRbN\",\"cuid\":\"E\",\"status\":\"failure\",\"attempts\":1933477389,\"notification_data\":{\"okTsjGAxpjsk\":\"._)$ttfA\",\"yhipWQUjZBmH\":49,\"hAjlStWTkQLJ\":false}}"
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
const singlesitejobs = await session.getSingleSiteJobs(1188178555,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_card","cardsavr_account","credential_requests"])});
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
JsonArray response = (JsonArray)session.get(1188178555, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1188178555,
  "status": "TIMEOUT_TFA",
  "status_message": "ZM",
  "termination_type": "SITE_INTERACTION_FAILURE",
  "custom_data": {
    "IDsdnxGiGgrL": "-@0KEze*GlWICP-4o9wl",
    "bSkeeBaLDMai": 92,
    "qlTCUHWJDnUh": true
  },
  "notification_sent": true,
  "time_elapsed": 2009520478,
  "auth_percent_complete": 1367075172,
  "percent_complete": 1104696897,
  "started_on": "2005-06-23T00:51:45.730Z",
  "completed_on": "1998-07-24T03:15:05.327Z",
  "created_on": "2004-05-19T13:29:06.896Z",
  "last_updated_on": "1970-03-30T03:22:33.836Z",
  "cardholder": {
    "id": 119249958,
    "type": "ephemeral",
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "test_email@strivve.com",
    "meta_key": "WjLYNsDKmpgy",
    "webhook_url": "https://mywebhooks.com/this",
    "custom_data": {
      "WrDGXsREhmGB": "}^J3+xV(yS)T[I+Uu!&]iNb",
      "uOrzGrowBtBW": 43,
      "udXGIBuJwpud": true
    },
    "created_on": "1976-03-09T23:59:38.087Z",
    "last_updated_on": "1974-01-06T01:34:42.716Z",
    "cuid": "eYuWkfVtPRjnsVqdnAuhgaJiYLOO"
  },
  "cardsavr_card": {
    "id": 1955446888,
    "type": "Visa",
    "expiration_month": 12,
    "expiration_year": 24,
    "name_on_card": "Jane Smith",
    "nickname": "Jane's VISA",
    "custom_data": {
      "axoRTMvbbVLb": "3c%HA0[.#{7kLR2TK#q][-Bws",
      "zPeWseoTZsqt": 68,
      "cchUStKHFlqs": false
    },
    "created_on": "1996-07-02T12:21:57.681Z",
    "last_updated_on": "2016-12-09T00:16:25.109Z",
    "par": "aufPFeSTuoAXQrRfjGuXWSpleBazL",
    "customer_key": "MIkYDnDqcfVAMKCwtOtFgwLFhtdguny"
  },
  "cardsavr_account": {
    "id": 56779520,
    "last_password_update": "1983-10-15T04:49:34.022Z",
    "last_saved_card": "2021-10-04T08:16:45.533Z",
    "created_on": "1985-12-29T17:34:18.708Z",
    "last_updated_on": "1973-02-01T02:26:04.322Z",
    "customer_key": "wrhSPzgZVGknCrrJqZOWrjnipGidtxHb"
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/1188178555`

To hydrate all credential requests currently associated with a job, include credential_requests in the hydration header (see example at right).`

### <a name="response-place_card_on_single_site_job"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this job.
card_id | number (fk) [cards](#cards) | ID of card associated with this job.
status | string | Current status of job (e.g. pending_tfa). These names are dynamic and change frequently, so it is best to use status_message to communicate with cardholders.
status_message | string | Human readable representation of the job's status.
termination_type | string | Final termination status of a job. (BILLABLE, SITE_INTERACTION_FAILURE, USER_DATA_FAILURE, PROCESS FAILURE)
custom_data | object | 
notification_sent | boolean | Indicates if a notification has been sent or posted for this job.
time_elapsed | number | Amount of time elapsed since the creation of the job.
auth_percent_complete | number | 
percent_complete | number | 
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
  "cardholder_id": 180417819,
  "card_id": 340797899,
  "account_id": 564031877,
  "status": "TIMEOUT_TFA",
  "custom_data": {
    "IDsdnxGiGgrL": "-@0KEze*GlWICP-4o9wl",
    "bSkeeBaLDMai": 92,
    "qlTCUHWJDnUh": true
  },
  "notification_sent": true,
  "time_elapsed": 2009520478,
  "started_on": "2005-06-23T00:51:45.730Z",
  "completed_on": "1998-07-24T03:15:05.327Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 180417819 },
	{ "card_id", 340797899 },
	{ "account_id", 564031877 },
	{ "status", "TIMEOUT_TFA" },
	{ "notification_sent", true },
	{ "time_elapsed", 2009520478 },
	{ "started_on", "2005-06-23T00:51:45.730Z" },
	{ "completed_on", "1998-07-24T03:15:05.327Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 180417819 )
	.add("card_id", 340797899 )
	.add("account_id", 564031877 )
	.add("status", "TIMEOUT_TFA" )
	.add("notification_sent", true )
	.add("time_elapsed", 2009520478 )
	.add("started_on", "2005-06-23T00:51:45.730Z" )
	.add("completed_on", "1998-07-24T03:15:05.327Z" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":180417819,\"card_id\":340797899,\"account_id\":564031877,\"status\":\"TIMEOUT_TFA\",\"custom_data\":{\"IDsdnxGiGgrL\":\"-@0KEze*GlWICP-4o9wl\",\"bSkeeBaLDMai\":92,\"qlTCUHWJDnUh\":true},\"notification_sent\":true,\"time_elapsed\":2009520478,\"started_on\":\"2005-06-23T00:51:45.730Z\",\"completed_on\":\"1998-07-24T03:15:05.327Z\"}"
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
card_id | number | yes | ID of card associated with this job.
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
- LOGIN_SUBMITTED
- CREDS_RECEIVED
- TFA_CODE_RECEIVED
- TFA_SUBMITTED
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
- JOB_RECORD_DELETED
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
- TEST_COMPLETE_SUCCESS
- SUCCESSFUL
- UNSUPPORTED_CAPTCHA
- TIMEOUT_CAPTCHA
- TIMEOUT_CREDENTIALS
- TIMEOUT_TFA
- TOO_MANY_LOGIN_FAILURES
- TOO_MANY_TFA_FAILURES
- TOO_MANY_OTP_FAILURES
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
  "card_id": 500212131,
  "status": "INVALID_CARD",
  "custom_data": {
    "OWILyZaDrXty": "Kv.",
    "mJpINiKyGMIP": 58,
    "rhfABuiWtvIk": true
  },
  "notification_sent": false,
  "time_elapsed": 1627228275,
  "started_on": "1982-01-10T02:35:18.867Z",
  "completed_on": "1995-12-09T07:07:37.761Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 500212131 },
	{ "status", "INVALID_CARD" },
	{ "notification_sent", false },
	{ "time_elapsed", 1627228275 },
	{ "started_on", "1982-01-10T02:35:18.867Z" },
	{ "completed_on", "1995-12-09T07:07:37.761Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 500212131 )
	.add("status", "INVALID_CARD" )
	.add("notification_sent", false )
	.add("time_elapsed", 1627228275 )
	.add("started_on", "1982-01-10T02:35:18.867Z" )
	.add("completed_on", "1995-12-09T07:07:37.761Z" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":500212131,\"status\":\"INVALID_CARD\",\"custom_data\":{\"OWILyZaDrXty\":\"Kv.\",\"mJpINiKyGMIP\":58,\"rhfABuiWtvIk\":true},\"notification_sent\":false,\"time_elapsed\":1627228275,\"started_on\":\"1982-01-10T02:35:18.867Z\",\"completed_on\":\"1995-12-09T07:07:37.761Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1188178555
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1188178555
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

