
# Accounts
Account objects contain the account information, such as username and password, for a particular cardhoder. They are used to log in to a cardholder's account for placing a payment card.
## Get account

```javascript
const accounts = await session.getAccounts(214733092,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","merchant_site","cardsavr_card"])});
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
JsonArray response = (JsonArray)session.get(214733092, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 214733092,
  "last_password_update": "1982-06-11T07:03:07.271Z",
  "last_saved_card": "2003-05-29T16:25:59.803Z",
  "created_on": "1984-05-17T20:44:06.799Z",
  "last_updated_on": "1974-12-19T03:22:48.177Z",
  "cardholder": {
    "id": 1948052807,
    "financial_institution_id": 762014807,
    "agent_session_id": "qHQWgjSokfjlYbVKf",
    "type": "persistent_creds",
    "first_name": "RS",
    "last_name": "TTKWXNNAf",
    "email": "vHCyxQmWICfL@rrsMex.UPu",
    "meta_key": "IV",
    "cardholder_safe_key": "qtTlY+0KIPQ4usO1YnXiVyryPMD0bBMfku//c7xyzmk=",
    "safe_key_hash": "EalYJtExyAXcYOJvIonoCPyBGopsSBwHmNXOfiTSYLCkXCzbjWpPkRLzbTs",
    "custom_data": {
      "PFQiLGQxqJef": "rcmgiXs}fe2$t&.U",
      "oKGfIpmIsxwV": 75,
      "DKUsAIltwboy": true
    },
    "created_on": "2020-06-26T14:13:49.361Z",
    "last_updated_on": "1984-12-04T14:32:59.375Z"
  },
  "merchant_site": {
    "id": 265277356,
    "name": "uCZyd",
    "host": "EUHvkEuoErFcHDR",
    "tags": [
      "B3r^*Y&N!JtUDgKD1k/Brq4Yv",
      42,
      "H2Dd3=Y,+~Fb-K}pd/7w+LP[W~zd"
    ],
    "queue_name": "vbs_queue",
    "interface_type": "vbs",
    "required_form_fields": [
      "ZE)9&azxM[R",
      14,
      "*MZ-k210dA6v%)4"
    ],
    "images": [
      {
        "lHZeXAvzrIqE": "Yd84B.%iETpoA!7",
        "knCMLElgnMZU": 0,
        "fmEIVWfXntRL": false
      },
      {
        "PFuMhdLmKLck": "*79$2X)a)",
        "sTlOPkxQXwsV": 86,
        "IEWfLUYeJgzh": true
      },
      {
        "DnrJizdXkhsy": "y",
        "gVCfBLCgFCEQ": 87,
        "svcOlXrJgKsV": true
      }
    ],
    "account_identification": [
      {
        "AVBFBZCuvGQl": "c~7J-]y[5Pii~)uKGzf-75+v8",
        "RxPoozJOPFce": 84,
        "VWUMEmVMfpID": true
      },
      {
        "lXsJSifFhDDb": "AjoB(,Rpj7c9",
        "tqsJHBWJodhN": 48,
        "XudvRypgFENG": false
      },
      {
        "eeosLTNYaqhq": "}Xjz3&(hABBP6t_",
        "IBfewJYxTnzw": 21,
        "nxXwDzsmluFw": true
      }
    ],
    "messages": {
      "kZTxvZpOwMrk": "~f}SNQ{WjWR}q*W6MoG.s8pCB[rq",
      "yKutjERMnWVA": 98,
      "zXkeosIImAeU": true
    },
    "mfa": true,
    "move_mouse_to_element": false,
    "screenshot": false,
    "proxy_order": [
      "I.Y=Cvubq1@Zz3ERNt1*Zu",
      75,
      "!z)TyYFTjdu2dt"
    ],
    "credit_card_page": "rZlUscVP",
    "forgot_password_page": "ReY",
    "quick_start": false,
    "login_page": "DcMMmdUYKtHUjoDXKLDItFJOCeZ"
  },
  "cardsavr_card": {
    "id": 1323656569,
    "bin_id": 858864522,
    "type": "American Express",
    "cvv": "yTx",
    "expiration_month": "12",
    "expiration_year": "N",
    "name_on_card": "zVxQryURyAanbwxpnBCFyHEiuejTdAtTKmaZKfTqEhTIWlKIWYNAIlxNwXZUBkFtrPFUVnPwAXTcbZzzEywBJdpRGTmEDGNqSjUQCzwUVHTeguTCjCoKEzgwTgtdBZtJWRPpsZgrOvOGFMnFFeIZPxZULgQwqozOhPTgbiDBeYhwREKplTGLBvsLieLwsXDeHEklFiFNbAtWjuEdVgWWHgkDOjpDCcyCFnUGqsqnUKuAmkxXdlQTeCeheQSTNk",
    "first_6": "jnxlwGbpehRVieeyPgosOUUUMsjrkYzj",
    "first_7": "omOkVJDALXAxMatAbNjYzBSGaAzZryTt",
    "first_8": "YJdyWAoODgsyxgGanoYdhNbnbYcOnkTV",
    "nickname": "FCSguMdubQBMlGwxTwKogaVFbwSiqzWjqcXyLHzvFeYDpikCYVvculkiyjmTTDq",
    "custom_data": {
      "cNwHbpqsiPVt": "7uyvGC1~r@i/[[^n&slkuA6TiESHul6P",
      "QWWOnYlYHlYm": 51,
      "aEwwZSJvrOhX": false
    },
    "created_on": "1973-06-12T01:26:51.268Z",
    "last_updated_on": "1973-10-24T18:10:35.296Z"
  },
  "customer_key": "QSqXIZd"
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

**Example GET request path:**<br>`/cardsavr_accounts/214733092`

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
  "cardholder_id": 508332500,
  "merchant_site_id": 491889397,
  "customer_key": "QSqXIZd",
  "last_card_placed_id": 1482148448,
  "account_identification": {
    "xAeKEdcSJfdB": "Ciq8^M~e}mH)L{^q8Y,q!Ne+W4jqp(xT",
    "IrPkEzYgbWmI": 5,
    "uwOcnleEEEcn": true
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 508332500 },
	{ "merchant_site_id", 491889397 },
	{ "customer_key", "QSqXIZd" },
	{ "last_card_placed_id", 1482148448 }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 508332500 )
	.add("merchant_site_id", 491889397 )
	.add("customer_key", "QSqXIZd" )
	.add("last_card_placed_id", 1482148448 )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":508332500,\"merchant_site_id\":491889397,\"customer_key\":\"QSqXIZd\",\"last_card_placed_id\":1482148448,\"account_identification\":{\"xAeKEdcSJfdB\":\"Ciq8^M~e}mH)L{^q8Y,q!Ne+W4jqp(xT\",\"IrPkEzYgbWmI\":5,\"uwOcnleEEEcn\":true}}"
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
account_identification | object | no | One or more properties with key:value pairs for identifying a user and if necessary credentials such as a password. The set of key:value pairs for a site is specified in the merchant site info returned from GET /merchant_sites.

See [account response attributes](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the account_identification when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Upsert account

```javascript
const account = await session.updateAccount(1,{
  "last_card_placed_id": 1174326503,
  "account_identification": {
    "ZBcZdmTHKbHQ": "K=dE}",
    "iclmtOrZGLOc": 62,
    "GTMRdcCGMkTl": false
  }
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 1174326503 }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 1174326503 )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":1174326503,\"account_identification\":{\"ZBcZdmTHKbHQ\":\"K=dE}\",\"iclmtOrZGLOc\":62,\"GTMRdcCGMkTl\":false}}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/214733092
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
account_identification | object | One or more properties with key:value pairs for identifying a user and if necessary credentials such as a password. The set of key:value pairs for a site is specified in the merchant site info returned from GET /merchant_sites.

See [account response parameters](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the account_identification when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete account

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/214733092
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
const addresses = await session.getAddresses(848559770,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder"])});
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
JsonArray response = (JsonArray)session.get(848559770, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 848559770,
  "address1": "AXuXocPOJSHLDywRvsdpklCBUspJXULyDprojxFakXRhOzKVsDlnttuAIqNxLztMKyDLejCNgasszbcdmubGIIPpIetuYApnysy",
  "address2": "ElLjCkBDHXWgDKLjUyPBmvGVxuNyNwtvqqXdJjyUIPITchsMnsYoHynBBTQMgedJxwPetnblMKDCILbhsrrUPilVvbYIXHQBwHg",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "LIFMcEjmggQW@pYESrG.YnH",
  "phone_number": "2065555555",
  "created_on": "2020-03-26T09:55:09.738Z",
  "last_updated_on": "2013-10-30T15:38:00.507Z",
  "cardholder": {
    "id": 596172100,
    "financial_institution_id": 131172772,
    "agent_session_id": "mvB",
    "type": "persistent_creds",
    "first_name": "bVYvuITZpELCnOnKF",
    "last_name": "mhELQkmbmVeZxvN",
    "email": "eCPTcIbJtCiY@dEzzqL.vSP",
    "meta_key": "ZpZiqddmaTVldkqjjyLbvzaYhiBJiUco",
    "cardholder_safe_key": "uQ8gKHpqWHMd8aAgCLqIw5DEsHfK/oFUu6MvY2/XgYY=",
    "safe_key_hash": "pvWdiklmEzVZaDvsoNJvejlFNuMWdjamkkFBFsOgvKeaqwcdIQSpUuizVdo",
    "custom_data": {
      "wNPEWqRivZre": "&2Ws9o=4%Ws=$pJFJhY8@)IL,U^ZWN&a",
      "dXSACgZDrobO": 81,
      "ofdgoxSwEQvo": false
    },
    "created_on": "1992-01-25T23:51:29.796Z",
    "last_updated_on": "2002-02-15T18:08:11.481Z"
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

**Example GET request path:**<br>`/cardsavr_addresses/848559770`

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
  "cardholder_id": 938586679,
  "address1": "AXuXocPOJSHLDywRvsdpklCBUspJXULyDprojxFakXRhOzKVsDlnttuAIqNxLztMKyDLejCNgasszbcdmubGIIPpIetuYApnysy",
  "address2": "ElLjCkBDHXWgDKLjUyPBmvGVxuNyNwtvqqXdJjyUIPITchsMnsYoHynBBTQMgedJxwPetnblMKDCILbhsrrUPilVvbYIXHQBwHg",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "LIFMcEjmggQW@pYESrG.YnH",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 938586679 },
	{ "address1", "AXuXocPOJSHLDywRvsdpklCBUspJXULyDprojxFakXRhOzKVsDlnttuAIqNxLztMKyDLejCNgasszbcdmubGIIPpIetuYApnysy" },
	{ "address2", "ElLjCkBDHXWgDKLjUyPBmvGVxuNyNwtvqqXdJjyUIPITchsMnsYoHynBBTQMgedJxwPetnblMKDCILbhsrrUPilVvbYIXHQBwHg" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "LIFMcEjmggQW@pYESrG.YnH" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 938586679 )
	.add("address1", "AXuXocPOJSHLDywRvsdpklCBUspJXULyDprojxFakXRhOzKVsDlnttuAIqNxLztMKyDLejCNgasszbcdmubGIIPpIetuYApnysy" )
	.add("address2", "ElLjCkBDHXWgDKLjUyPBmvGVxuNyNwtvqqXdJjyUIPITchsMnsYoHynBBTQMgedJxwPetnblMKDCILbhsrrUPilVvbYIXHQBwHg" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "LIFMcEjmggQW@pYESrG.YnH" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":938586679,\"address1\":\"AXuXocPOJSHLDywRvsdpklCBUspJXULyDprojxFakXRhOzKVsDlnttuAIqNxLztMKyDLejCNgasszbcdmubGIIPpIetuYApnysy\",\"address2\":\"ElLjCkBDHXWgDKLjUyPBmvGVxuNyNwtvqqXdJjyUIPITchsMnsYoHynBBTQMgedJxwPetnblMKDCILbhsrrUPilVvbYIXHQBwHg\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"LIFMcEjmggQW@pYESrG.YnH\",\"phone_number\":\"2065555555\"}"
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
  "address1": "zdvAnqoOyGUuncFrcYQqSJQHdreGVTBrtCeYDbVgNbTkkIpxzXfIdEkHXkviASDstBIoyxtzkamLPyVAznpPAGyOjFkoDMIsDBj",
  "address2": "aMtsRFUduUGdBqyeqIOOjSSceghGzKkbisqvyZRVBbSZDjyRJIMDeRpwBACfrOVFuMHbWlqLVcLTIJktlslJMTZCcUAQhbuiyBE",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "NMdPepGZhSJi@wInXOf.DbQ",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "zdvAnqoOyGUuncFrcYQqSJQHdreGVTBrtCeYDbVgNbTkkIpxzXfIdEkHXkviASDstBIoyxtzkamLPyVAznpPAGyOjFkoDMIsDBj" },
	{ "address2", "aMtsRFUduUGdBqyeqIOOjSSceghGzKkbisqvyZRVBbSZDjyRJIMDeRpwBACfrOVFuMHbWlqLVcLTIJktlslJMTZCcUAQhbuiyBE" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", false },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "NMdPepGZhSJi@wInXOf.DbQ" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "zdvAnqoOyGUuncFrcYQqSJQHdreGVTBrtCeYDbVgNbTkkIpxzXfIdEkHXkviASDstBIoyxtzkamLPyVAznpPAGyOjFkoDMIsDBj" )
	.add("address2", "aMtsRFUduUGdBqyeqIOOjSSceghGzKkbisqvyZRVBbSZDjyRJIMDeRpwBACfrOVFuMHbWlqLVcLTIJktlslJMTZCcUAQhbuiyBE" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", false )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "NMdPepGZhSJi@wInXOf.DbQ" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"zdvAnqoOyGUuncFrcYQqSJQHdreGVTBrtCeYDbVgNbTkkIpxzXfIdEkHXkviASDstBIoyxtzkamLPyVAznpPAGyOjFkoDMIsDBj\",\"address2\":\"aMtsRFUduUGdBqyeqIOOjSSceghGzKkbisqvyZRVBbSZDjyRJIMDeRpwBACfrOVFuMHbWlqLVcLTIJktlslJMTZCcUAQhbuiyBE\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":false,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"NMdPepGZhSJi@wInXOf.DbQ\",\"phone_number\":\"2065555555\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/848559770
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/848559770
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
const bins = await session.getBins(138903610,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(138903610, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 138903610,
  "custom_data": {
    "zXqgsngiDGAs": "(n,${d",
    "mEBJClQZDvIr": 40,
    "gCWxvqRTRrAA": false
  },
  "created_on": "2016-07-26T19:15:54.415Z",
  "last_updated_on": "1972-10-12T06:27:00.954Z",
  "financial_institution": {
    "id": 2102164617,
    "name": "CJJCDRZHazlMGoKNUjsvgQhhtnXkywfItoJVZHOVnMPTJtWFADXDxWivWCfyuQd",
    "description": "ZSvgFIgFdubmpNbJViQB",
    "lookup_key": "mlxJPSPjsrMnUaJPvrNoLVDaCmbQDwAfgHUeZTasTUTBmYutsdufBOgWjCvQMCe",
    "alternate_lookup_key": "LQVAPMIJbAUpjDiOXlEqtJJMekjtkkohyTAEPIOFjTqSWKsKUQOpwkbQjQVCbEH",
    "config": {
      "FkpogyXXFOJi": "IC{)FF!",
      "tJMvcqpAPUqi": 69,
      "abLmmUMCfMPd": true
    },
    "last_activity": "2000-08-13T04:19:26.688Z",
    "created_on": "1995-09-16T18:49:10.030Z",
    "last_updated_on": "1989-04-07T17:08:10.587Z"
  },
  "bank_identification_number": "51288912"
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

**Example GET request path:**<br>`/cardsavr_bins/138903610`

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
  "financial_institution_id": 1389486726,
  "bank_identification_number": "51288912",
  "custom_data": {
    "zXqgsngiDGAs": "(n,${d",
    "mEBJClQZDvIr": 40,
    "gCWxvqRTRrAA": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1389486726 },
	{ "bank_identification_number", "51288912" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1389486726 )
	.add("bank_identification_number", "51288912" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1389486726,\"bank_identification_number\":\"51288912\",\"custom_data\":{\"zXqgsngiDGAs\":\"(n,${d\",\"mEBJClQZDvIr\":40,\"gCWxvqRTRrAA\":false}}"
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
  "financial_institution_id": 558367102,
  "custom_data": {
    "yBqqgZjAowCh": "-f](%WJ&40TjjdQw6,~jF,Nh.-guN",
    "pqERCfkrfyfa": 9,
    "HDXDnVhUavZv": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 558367102 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 558367102 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":558367102,\"custom_data\":{\"yBqqgZjAowCh\":\"-f](%WJ&40TjjdQw6,~jF,Nh.-guN\",\"pqERCfkrfyfa\":9,\"HDXDnVhUavZv\":true}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/138903610
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/138903610
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
const cardplacementresults = await session.getCardPlacementResults(1731954097,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution","merchant_site","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(1731954097, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1731954097,
  "merchant_site_hostname": "VsbnTiJqvLlELraTzAxLpLpcZIibuxMhpdvJwwzEbsudtRFFWcnVUVAtNJduDxYsYkxSagRqRzHGTyUcxieoXAeJWCXHvRDsxoUEvTVaILlTxlobwmPtQBOYUsMKMOAbjWbakCZSVfdNbbxlxCNPPvZcPALvcKDBdIqjPkPCiPFUNpVZWvOowRXTBauBCIzATdiAXPiXWBRreetrIytOQIpNjibpqhPAinEeEifrGxpaIpEeqXraFsntiddpeG",
  "meta_key": "MB9810411",
  "fi_name": "zNIrpwfPWqRnbLulSPUuXHzhHDRdmRZryutclXwUozowAtqjRUXbrOtCSkUKfeN",
  "bank_identification_number": "63141624",
  "cuid": "zFtLEHQH",
  "par": "OkWJPAocVJwPbSLttfQNMYvuzwUib",
  "card_customer_key": "GdBvRJbqkmNdqxTQKlClPTgtWkhQA",
  "account_customer_key": "qapAwizJujoPUePJNVCKbTqfxhyfgln",
  "status": "SUCCESSFUL",
  "status_message": "Successful",
  "termination_type": "BILLABLE",
  "custom_data": {
    "BDbxdKNTvhPy": "U$N*L/Kic-1a($N#2!c](Ia+-SLvjY",
    "gIMhXNgQbHLs": 55,
    "UYeYdpZxbOtw": false
  },
  "time_elapsed": 1310131270,
  "first_6": "vtpbAktvcVSaiqOhRaJdfieJjppgmHRn",
  "first_7": "XjVejUNuEsYiAhuIquzwYfItKiXGiRqW",
  "first_8": "nnvxRvxWbahzvHoBeGpbVGHkAAFhIBId",
  "trace": "XXkbJdInHkokWYhFtOGS",
  "email_sent": false,
  "completed_on": "2016-05-02T19:01:13.506Z",
  "created_on": "2010-05-29T18:15:30.741Z",
  "last_updated_on": "1982-08-22T18:21:05.742Z",
  "financial_institution": {
    "id": 1473482954,
    "name": "oyUrlZQqWEWjapWguXwEoxTNOLoJXtkYQDdnjgrCSbJLirArWUFxTbGrqpCzDNX",
    "description": "ykGkNLT",
    "lookup_key": "VTZylKYclQefZkrrNqtrniFTQquCYzfPrMlWbnHAxseGoPOtbeAPMnimWjufpuj",
    "alternate_lookup_key": "gVsgxeYANvwZzDQnyZGPCDlimrRogMeizLTfbpPnUhHcorRBDGcRBNVMLiYMVLn",
    "config": {
      "HzCtsqHLBSbr": "}F[l&_NuRpy${7[gx[*8EG-[Xgjsi",
      "hxZaQhRpZyUS": 41,
      "stxhwYqnhJAj": false
    },
    "last_activity": "1998-06-23T00:42:23.664Z",
    "created_on": "2000-03-25T18:27:57.377Z",
    "last_updated_on": "2015-08-08T22:43:26.879Z"
  },
  "merchant_site": {
    "id": 558091795,
    "name": "SwPyWbwmvIjohuNhzkllfoiF",
    "host": "EZdIsT",
    "tags": [
      "Z@f1Numv5N&obQtEjeW)",
      65,
      "QqT~twq7"
    ],
    "interface_type": "dcs",
    "required_form_fields": [
      "7",
      32,
      "1&"
    ],
    "images": [
      {
        "KVPvVwTQXuTA": "QZ5c8eLqD(GL]K=k/yb)@d6Lva.+s&@",
        "FFkHCBndqnfL": 13,
        "skJeJUgvKDZL": false
      },
      {
        "OrFRbaUGmJeT": "uJb&6h%U53z)Q3,kx(EfcG}33c!bW",
        "qOpMmMyjJJJq": 45,
        "tdHWnduMTlzq": false
      },
      {
        "zfViBUSIepXg": "2z46_43,p",
        "pNulvVbNpTcr": 84,
        "SCyfwJsOoFxn": true
      }
    ],
    "account_identification": [
      {
        "wtdvxggnAJQD": "5[D^lEa5Crjpe5NeOqu[HJk",
        "PxiddvftWSoO": 42,
        "YCKkLJcbtNFv": false
      },
      {
        "mxiRFDugrQeN": "r[f3I7Re4X{xQ",
        "hKWVFhWKgAsC": 36,
        "ixVAfAaCNMos": true
      },
      {
        "wHauZCONWUuY": "y&,.#z!vD4E",
        "APCumQuIPZHf": 3,
        "XkeccrDFkkcw": false
      }
    ],
    "messages": {
      "CfdwZTCezQVw": "0wzRYRZV(z(/Ml(NW&-",
      "SFpsGCYgArcg": 26,
      "aJZtWYDzcldH": false
    },
    "mfa": true,
    "move_mouse_to_element": false,
    "screenshot": false,
    "proxy_order": [
      "oyd34",
      99,
      "tr4"
    ],
    "credit_card_page": "lgHElUriDFvfSZnOOmGemYITypTzS",
    "forgot_password_page": "wmKAz",
    "quick_start": false,
    "login_page": "CpdNYrPJIHe"
  },
  "cardsavr_bin": {
    "id": 1532213768,
    "financial_institution_id": 1500739476,
    "custom_data": {
      "QvOWJTBCgBQZ": "(icRYVSFIZ@{GOwc",
      "WjbVgitYRAZK": 53,
      "PryEIzLXLlYD": true
    },
    "created_on": "1991-02-14T14:56:08.722Z",
    "last_updated_on": "1971-08-16T01:47:17.004Z"
  },
  "place_card_on_single_site_job_id": 798934306
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

**Example GET request path:**<br>`/card_placement_results/1731954097`

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
const cards = await session.getCards(964183092,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_address","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(964183092, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 964183092,
  "type": "Mastercard",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "XzTTGIWYkjvKaWvTUMqTwCCDcqmlXqyBZSwfCiFuCrsRxQzlCOFBjYyCmMgMtfA",
  "custom_data": {
    "bBgkCBAdbvXi": "Q[}SZs*MhK).XIZ88T3z^mm+)p.kwM~P",
    "gfRroCWKUoTh": 46,
    "mGAbPUzjKJgS": false
  },
  "created_on": "1991-04-26T20:45:40.628Z",
  "last_updated_on": "1970-07-28T06:21:31.360Z",
  "cardholder": {
    "id": 1576193515,
    "financial_institution_id": 881782162,
    "agent_session_id": "BoDwtzmu",
    "type": "persistent_all",
    "first_name": "MHUYLRj",
    "last_name": "ZTTHeisWPBfL",
    "email": "xzgMdgHkbgLi@wkhzaB.eHZ",
    "meta_key": "PoVUKnsRHmeYvLvDeYBdWoYBPdu",
    "cardholder_safe_key": "JsKDwoSPBHwf47JJ/63gUrRC10UaNsWfKsUqpq4Zqv8=",
    "safe_key_hash": "LSCPoDPNDYnjJoBfelcWfYXXEolXvVuZCYjyuCqMkUxIIlJVgQjaabYzAoN",
    "custom_data": {
      "TywifdQXzxHF": "6+/p7pdQ+Cu96P*l%rh$jel#3O@",
      "WiPtjgPFjyxZ": 75,
      "KzHokFSPyOrj": true
    },
    "created_on": "2012-12-29T15:03:15.124Z",
    "last_updated_on": "2018-02-17T12:15:17.471Z"
  },
  "cardsavr_address": {
    "id": 896091225,
    "address1": "ZpuHzuqJKElqaaluOkRhfIcCAsFkpqUTfGvFXLsrNhPYbYqxXJdXgtSNNRLDKPFRYWPEoLfsmkOvZlXdZDyJuBCkmjTUHLcELXy",
    "address2": "EwdaGSTGHcfvPLDLZxogbWmeTJSiZvYKzJEwKLcaAVElNRLbSwocNCLgNdQisQrJWWzBeQSNaIhAHDezVBdmWcHYGXTyOeMxTVG",
    "city": "pSmQKhIykQflLTYQzUEzmvSSYEVzKYCCWsSFZYrcoMbbBatRdNUjzrPbpDAlDbQyzIkcqhRjmNHNBUeajpAyzVYCqfggKXFwRkZ",
    "subnational": "XqpjKJxKpxigsxJfmfPBeiFVOtxBGqWpnwmvemMvLErTBfBryZZMPBTCGwHujqc",
    "postal_code": "ZomMoAsKKVTFWfWcCcozCzhwLZllkhy",
    "postal_other": "dncHdSLyneHmEiJWMalykxVrHpxEMPj",
    "country": "Canada",
    "is_primary": true,
    "first_name": "EZYCCQjTAZqWljwhwcvqwaGt",
    "last_name": "DIGP",
    "email": "qAwgwyhkTany@OObMxh.buS",
    "phone_number": "x",
    "created_on": "1975-11-22T21:01:36.289Z",
    "last_updated_on": "2009-02-15T03:20:32.856Z"
  },
  "cardsavr_bin": {
    "id": 2117180253,
    "financial_institution_id": 197494623,
    "custom_data": {
      "boiuqaGvlBpA": "ChAX9K",
      "bykSTtnPjSxz": 81,
      "oJMerAbZEXkQ": false
    },
    "created_on": "1975-03-18T03:01:10.640Z",
    "last_updated_on": "1984-05-05T16:08:04.943Z"
  },
  "par": "LsnNpvBTWaZfIFuXNmsYVFFnorYfV",
  "customer_key": "VK"
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

**Example GET request path:**<br>`/cardsavr_cards/964183092`

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
  "cardholder_id": 1978416917,
  "address_id": 1222704203,
  "bin_id": 247998832,
  "par": "LsnNpvBTWaZfIFuXNmsYVFFnorYfV",
  "customer_key": "VK",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "XzTTGIWYkjvKaWvTUMqTwCCDcqmlXqyBZSwfCiFuCrsRxQzlCOFBjYyCmMgMtfA",
  "custom_data": {
    "bBgkCBAdbvXi": "Q[}SZs*MhK).XIZ88T3z^mm+)p.kwM~P",
    "gfRroCWKUoTh": 46,
    "mGAbPUzjKJgS": false
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1978416917 },
	{ "address_id", 1222704203 },
	{ "bin_id", 247998832 },
	{ "par", "LsnNpvBTWaZfIFuXNmsYVFFnorYfV" },
	{ "customer_key", "VK" },
	{ "pan", "4111111111111111" },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Jane Smith" },
	{ "nickname", "XzTTGIWYkjvKaWvTUMqTwCCDcqmlXqyBZSwfCiFuCrsRxQzlCOFBjYyCmMgMtfA" }
};

CardSavrResponse<Card> card = await http.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1978416917 )
	.add("address_id", 1222704203 )
	.add("bin_id", 247998832 )
	.add("par", "LsnNpvBTWaZfIFuXNmsYVFFnorYfV" )
	.add("customer_key", "VK" )
	.add("pan", "4111111111111111" )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Jane Smith" )
	.add("nickname", "XzTTGIWYkjvKaWvTUMqTwCCDcqmlXqyBZSwfCiFuCrsRxQzlCOFBjYyCmMgMtfA" )
	.build();
JsonValue card = session.post("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1978416917,\"address_id\":1222704203,\"bin_id\":247998832,\"par\":\"LsnNpvBTWaZfIFuXNmsYVFFnorYfV\",\"customer_key\":\"VK\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"XzTTGIWYkjvKaWvTUMqTwCCDcqmlXqyBZSwfCiFuCrsRxQzlCOFBjYyCmMgMtfA\",\"custom_data\":{\"bBgkCBAdbvXi\":\"Q[}SZs*MhK).XIZ88T3z^mm+)p.kwM~P\",\"gfRroCWKUoTh\":46,\"mGAbPUzjKJgS\":false}}"
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
  "bin_id": 162559610,
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "QOKimpQsJERNleEeTxvofxbFymVFXdcFmjWvuIGCwkuxTrVEwraPZFGBnooOwTB",
  "custom_data": {
    "tyKwriSLydSU": "J$%~IQcwF}Efw,x10QMI-1K-#Z&T",
    "HdNbwplDYTQL": 47,
    "OpagWJViyOGC": false
  },
  "pan": "4111111111111111"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "bin_id", 162559610 },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Jane Smith" },
	{ "nickname", "QOKimpQsJERNleEeTxvofxbFymVFXdcFmjWvuIGCwkuxTrVEwraPZFGBnooOwTB" },
	{ "pan", "4111111111111111" }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("bin_id", 162559610 )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Jane Smith" )
	.add("nickname", "QOKimpQsJERNleEeTxvofxbFymVFXdcFmjWvuIGCwkuxTrVEwraPZFGBnooOwTB" )
	.add("pan", "4111111111111111" )
	.build();
JsonValue card = session.put("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"bin_id\":162559610,\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"QOKimpQsJERNleEeTxvofxbFymVFXdcFmjWvuIGCwkuxTrVEwraPZFGBnooOwTB\",\"custom_data\":{\"tyKwriSLydSU\":\"J$%~IQcwF}Efw,x10QMI-1K-#Z&T\",\"HdNbwplDYTQL\":47,\"OpagWJViyOGC\":false},\"pan\":\"4111111111111111\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/964183092
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/964183092
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
const cardholders = await session.getCardholders(1420500775,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(1420500775, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1420500775,
  "type": "ephemeral",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "rYSMWOaDdtPetEQyx",
  "custom_data": {
    "QkhQMDLomJxW": "g^N[@lQJn%vRnp+!",
    "uavZTcOZKSZf": 76,
    "zAzuQBrwUSiP": true
  },
  "created_on": "1987-12-06T07:26:04.162Z",
  "last_updated_on": "1981-12-02T04:29:18.327Z",
  "financial_institution": {
    "id": 137956831,
    "name": "CGzMqPxabRxrdvlCnMnxeEYBgnEGhVaQggYYeLsIHuJcGzipYPVrNzxFpBLSVyJ",
    "description": "eEDVaHEdLxKmfX",
    "lookup_key": "jqhafTpiwkmywnunthVFTZLurxbQwQAdyqoFGSZMWwpWKTlPAIBLdKaHtktWVej",
    "alternate_lookup_key": "pFxTQdXDitMUKAfZMrDctJntKPpcCyfpGqfppKQHMwklFWhHWQMCvhAuqTunSvT",
    "config": {
      "TPZQwJxqiZDs": "+]q!K04/gX5wkdq.}C3H/}kElX",
      "tLkCldnRqkow": 29,
      "BJYylJATLLBL": false
    },
    "last_activity": "2016-11-03T16:25:21.882Z",
    "created_on": "2000-09-27T13:56:29.366Z",
    "last_updated_on": "1975-04-19T00:19:11.469Z"
  },
  "cuid": "VIgOIiLSfZvygQHElyNxWKeeQZGsluOI"
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

**Example GET request path:**<br>`/cardholders/1420500775`

### <a name="response-cardholder"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this cardholder.
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | 
type | string | It is critical to understand the behavior associated with each cardholder.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities.
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
  "cuid": "VIgOIiLSfZvygQHElyNxWKeeQZGsluOI",
  "type": "ephemeral",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "rYSMWOaDdtPetEQyx",
  "custom_data": {
    "QkhQMDLomJxW": "g^N[@lQJn%vRnp+!",
    "uavZTcOZKSZf": 76,
    "zAzuQBrwUSiP": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cuid", "VIgOIiLSfZvygQHElyNxWKeeQZGsluOI" },
	{ "type", "ephemeral" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "rYSMWOaDdtPetEQyx" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cuid", "VIgOIiLSfZvygQHElyNxWKeeQZGsluOI" )
	.add("type", "ephemeral" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "rYSMWOaDdtPetEQyx" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"cuid\":\"VIgOIiLSfZvygQHElyNxWKeeQZGsluOI\",\"type\":\"ephemeral\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"rYSMWOaDdtPetEQyx\",\"custom_data\":{\"QkhQMDLomJxW\":\"g^N[@lQJn%vRnp+!\",\"uavZTcOZKSZf\":76,\"zAzuQBrwUSiP\":true}}"
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
type | [string enum](#post-cardholder-1)* | no | It is critical to understand the behavior associated with each cardholder.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities.
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
  "meta_key": "XPLqhCXtTncr",
  "custom_data": {
    "ktJEjYoxYwBY": "14d+r+/p",
    "VmCgZCCvtjVD": 25,
    "bcgLJEMjWUqV": true
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
	{ "meta_key", "XPLqhCXtTncr" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("type", "ephemeral" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "XPLqhCXtTncr" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"type\":\"ephemeral\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"XPLqhCXtTncr\",\"custom_data\":{\"ktJEjYoxYwBY\":\"14d+r+/p\",\"VmCgZCCvtjVD\":25,\"bcgLJEMjWUqV\":true}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/1420500775
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
type | [string enum](#post-cardholder-1)* | It is critical to understand the behavior associated with each cardholder.  The default, 'ephemeral', cardholder is deleted along with all its associated entities upon session termination.  'persistent_credentials' cardholders are not removed automatically, but their associated cards are.  'persistent_all' cardholders are not removed and neither are any of their associated entities.
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
https://api.INSTANCE.cardsavr.io/cardholders/1420500775
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
const users = await session.getUsers(677488325,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(677488325, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 677488325,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "2020-09-29T15:42:55.766Z",
  "is_locked": false,
  "password_lifetime": 308,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_agent",
  "next_rotation_on": "1973-09-16T09:28:06.622Z",
  "created_on": "1992-04-09T10:05:34.914Z",
  "last_updated_on": "2012-06-30T05:55:41.267Z",
  "username": "jsmith123",
  "financial_institution": {
    "id": 2099442628,
    "name": "FGOLrkRXDMeQhxuZGAaEMFDJhgefKTBbwqpBmLSMOCDlfZolKqlXfLkPCoaVPZN",
    "description": "ULSDmnLVU",
    "lookup_key": "HyOQZRcTUzBxXGJlOIlLxvzdgOgwvRVmSlwEJaSbmGRwWEyRyoBguaRyRekEmkB",
    "alternate_lookup_key": "CvqQuzMgnMjZuEUEOmFlBIEptqNzaXerCkwaxgQiNCNnJDfVfSHVFbgbprLktqH",
    "config": {
      "oWArmNrgSOHM": "t#./!NzpuxDV$a{",
      "pZTbWPCLFNud": 2,
      "MYVICSKfylZK": true
    },
    "last_activity": "1970-11-03T14:52:35.923Z",
    "created_on": "1972-09-27T10:11:05.221Z",
    "last_updated_on": "2016-10-02T19:42:15.909Z"
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

**Example GET request path:**<br>`/cardsavr_users/677488325`

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
  "financial_institution_id": 594936624,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 308,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_agent",
  "next_rotation_on": "1973-09-16T09:28:06.622Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 594936624 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 308 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "swch_agent" },
	{ "next_rotation_on", "1973-09-16T09:28:06.622Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 594936624 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 308 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "swch_agent" )
	.add("next_rotation_on", "1973-09-16T09:28:06.622Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":594936624,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":308,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"swch_agent\",\"next_rotation_on\":\"1973-09-16T09:28:06.622Z\"}"
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
  "financial_institution_id": 1491912100,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 341,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_agent",
  "next_rotation_on": "1983-04-28T14:56:26.462Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1491912100 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 341 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "cardholder_agent" },
	{ "next_rotation_on", "1983-04-28T14:56:26.462Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1491912100 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 341 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "cardholder_agent" )
	.add("next_rotation_on", "1983-04-28T14:56:26.462Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1491912100,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":341,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"cardholder_agent\",\"next_rotation_on\":\"1983-04-28T14:56:26.462Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/677488325
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/677488325
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
const financialinstitutions = await session.getFinancialInstitutions(1737547938,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(1737547938, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1737547938,
  "name": "giNfOCbixLdJfRtmEIDuazLPEIznqGsTRVlyjZPxeJBWIQjTWdvnIsDSWmmmbPG",
  "description": "LkEJdiuOgrjeVhqsFaSjL",
  "lookup_key": "LyGVKBXtUgulDmrBEnsqYybDXBgxccQWmVaDVCBxlMGhOcUZYaiQteMkQfDbezu",
  "alternate_lookup_key": "kjDNlCtSJDjHWOpVfITVmLddGcuGzSBwJMXCWxTWgiWubDdeoRsgIyTEQyPpPlA",
  "last_activity": "2018-06-13T05:56:45.276Z",
  "created_on": "2000-09-02T22:21:03.140Z",
  "last_updated_on": "1979-01-09T22:25:46.707Z"
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
- alternate_lookup_key
- last_activity_min / last_activity_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/financial_institutions?ids=1,2`

#### Singular GET requests

**Singular requests** only return the financial institution matching the id provided in the path.

**Example GET request path:**<br>`/financial_institutions/1737547938`

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
  "name": "giNfOCbixLdJfRtmEIDuazLPEIznqGsTRVlyjZPxeJBWIQjTWdvnIsDSWmmmbPG",
  "description": "LkEJdiuOgrjeVhqsFaSjL",
  "lookup_key": "LyGVKBXtUgulDmrBEnsqYybDXBgxccQWmVaDVCBxlMGhOcUZYaiQteMkQfDbezu",
  "alternate_lookup_key": "kjDNlCtSJDjHWOpVfITVmLddGcuGzSBwJMXCWxTWgiWubDdeoRsgIyTEQyPpPlA"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "giNfOCbixLdJfRtmEIDuazLPEIznqGsTRVlyjZPxeJBWIQjTWdvnIsDSWmmmbPG" },
	{ "description", "LkEJdiuOgrjeVhqsFaSjL" },
	{ "lookup_key", "LyGVKBXtUgulDmrBEnsqYybDXBgxccQWmVaDVCBxlMGhOcUZYaiQteMkQfDbezu" },
	{ "alternate_lookup_key", "kjDNlCtSJDjHWOpVfITVmLddGcuGzSBwJMXCWxTWgiWubDdeoRsgIyTEQyPpPlA" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "giNfOCbixLdJfRtmEIDuazLPEIznqGsTRVlyjZPxeJBWIQjTWdvnIsDSWmmmbPG" )
	.add("description", "LkEJdiuOgrjeVhqsFaSjL" )
	.add("lookup_key", "LyGVKBXtUgulDmrBEnsqYybDXBgxccQWmVaDVCBxlMGhOcUZYaiQteMkQfDbezu" )
	.add("alternate_lookup_key", "kjDNlCtSJDjHWOpVfITVmLddGcuGzSBwJMXCWxTWgiWubDdeoRsgIyTEQyPpPlA" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"giNfOCbixLdJfRtmEIDuazLPEIznqGsTRVlyjZPxeJBWIQjTWdvnIsDSWmmmbPG\",\"description\":\"LkEJdiuOgrjeVhqsFaSjL\",\"lookup_key\":\"LyGVKBXtUgulDmrBEnsqYybDXBgxccQWmVaDVCBxlMGhOcUZYaiQteMkQfDbezu\",\"alternate_lookup_key\":\"kjDNlCtSJDjHWOpVfITVmLddGcuGzSBwJMXCWxTWgiWubDdeoRsgIyTEQyPpPlA\"}"
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
  "name": "YWgxhjzLLMDKNPJALIhYqOqEsYdLEWdgFipLukxHoQLsLDmoeRFpvzHErlRfBAZ",
  "description": "ijuJxKoQvILlIvEPGRjJChGXH",
  "lookup_key": "WtjuKGhzlRsjQZdbOAmBAZUYvzdBQIwQrHcPPrgFvkXSxCuBKRcLzTqjOQnrRss",
  "alternate_lookup_key": "rMgEolpjABpRQyGJIIhwUPZqpnSGCiqxoNCYNapNEjNIjjYOoHaYfuKFfiBjTBw"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "YWgxhjzLLMDKNPJALIhYqOqEsYdLEWdgFipLukxHoQLsLDmoeRFpvzHErlRfBAZ" },
	{ "description", "ijuJxKoQvILlIvEPGRjJChGXH" },
	{ "lookup_key", "WtjuKGhzlRsjQZdbOAmBAZUYvzdBQIwQrHcPPrgFvkXSxCuBKRcLzTqjOQnrRss" },
	{ "alternate_lookup_key", "rMgEolpjABpRQyGJIIhwUPZqpnSGCiqxoNCYNapNEjNIjjYOoHaYfuKFfiBjTBw" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "YWgxhjzLLMDKNPJALIhYqOqEsYdLEWdgFipLukxHoQLsLDmoeRFpvzHErlRfBAZ" )
	.add("description", "ijuJxKoQvILlIvEPGRjJChGXH" )
	.add("lookup_key", "WtjuKGhzlRsjQZdbOAmBAZUYvzdBQIwQrHcPPrgFvkXSxCuBKRcLzTqjOQnrRss" )
	.add("alternate_lookup_key", "rMgEolpjABpRQyGJIIhwUPZqpnSGCiqxoNCYNapNEjNIjjYOoHaYfuKFfiBjTBw" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"YWgxhjzLLMDKNPJALIhYqOqEsYdLEWdgFipLukxHoQLsLDmoeRFpvzHErlRfBAZ\",\"description\":\"ijuJxKoQvILlIvEPGRjJChGXH\",\"lookup_key\":\"WtjuKGhzlRsjQZdbOAmBAZUYvzdBQIwQrHcPPrgFvkXSxCuBKRcLzTqjOQnrRss\",\"alternate_lookup_key\":\"rMgEolpjABpRQyGJIIhwUPZqpnSGCiqxoNCYNapNEjNIjjYOoHaYfuKFfiBjTBw\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/1737547938
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
https://api.INSTANCE.cardsavr.io/financial_institutions/1737547938
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
const integrators = await session.getIntegrators(371788882,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(371788882, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 371788882,
  "name": "UAmhXRFkmYHZhGjlbUoizwfvsGqnTGtOlZOlbXWfGSqNVcKsP",
  "description": "enMGXJNoPh",
  "current_key": "o+oUZu8GsAqp/MiCir1tj8qcs2CtLMdB/8icKp5eqKc=",
  "key_lifetime": 198,
  "next_rotation_on": "2019-08-17T20:47:43.249Z",
  "created_on": "1997-11-29T14:17:42.429Z",
  "last_updated_on": "2022-08-31T04:42:24.502Z"
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

**Example GET request path:**<br>`/integrators/371788882`

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
  "name": "UAmhXRFkmYHZhGjlbUoizwfvsGqnTGtOlZOlbXWfGSqNVcKsP",
  "description": "enMGXJNoPh",
  "current_key": "o+oUZu8GsAqp/MiCir1tj8qcs2CtLMdB/8icKp5eqKc=",
  "key_lifetime": 198,
  "next_rotation_on": "2019-08-17T20:47:43.249Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "UAmhXRFkmYHZhGjlbUoizwfvsGqnTGtOlZOlbXWfGSqNVcKsP" },
	{ "description", "enMGXJNoPh" },
	{ "current_key", "o+oUZu8GsAqp/MiCir1tj8qcs2CtLMdB/8icKp5eqKc=" },
	{ "key_lifetime", 198 },
	{ "next_rotation_on", "2019-08-17T20:47:43.249Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "UAmhXRFkmYHZhGjlbUoizwfvsGqnTGtOlZOlbXWfGSqNVcKsP" )
	.add("description", "enMGXJNoPh" )
	.add("current_key", "o+oUZu8GsAqp/MiCir1tj8qcs2CtLMdB/8icKp5eqKc=" )
	.add("key_lifetime", 198 )
	.add("next_rotation_on", "2019-08-17T20:47:43.249Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"UAmhXRFkmYHZhGjlbUoizwfvsGqnTGtOlZOlbXWfGSqNVcKsP\",\"description\":\"enMGXJNoPh\",\"current_key\":\"o+oUZu8GsAqp/MiCir1tj8qcs2CtLMdB/8icKp5eqKc=\",\"key_lifetime\":198,\"next_rotation_on\":\"2019-08-17T20:47:43.249Z\"}"
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
  "name": "OwQGzaczZvrLVsNeFyFHFLuxMyHFllWkZomHCVbvdgSggHFUi",
  "description": "AohDloGlyeUtfOW",
  "current_key": "J1w4QC+GtDEOkzZqB9Db6RaNTPklOmHQXgwcItkMmr8=",
  "key_lifetime": 9,
  "next_rotation_on": "1989-11-12T19:58:49.411Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "OwQGzaczZvrLVsNeFyFHFLuxMyHFllWkZomHCVbvdgSggHFUi" },
	{ "description", "AohDloGlyeUtfOW" },
	{ "current_key", "J1w4QC+GtDEOkzZqB9Db6RaNTPklOmHQXgwcItkMmr8=" },
	{ "key_lifetime", 9 },
	{ "next_rotation_on", "1989-11-12T19:58:49.411Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "OwQGzaczZvrLVsNeFyFHFLuxMyHFllWkZomHCVbvdgSggHFUi" )
	.add("description", "AohDloGlyeUtfOW" )
	.add("current_key", "J1w4QC+GtDEOkzZqB9Db6RaNTPklOmHQXgwcItkMmr8=" )
	.add("key_lifetime", 9 )
	.add("next_rotation_on", "1989-11-12T19:58:49.411Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"OwQGzaczZvrLVsNeFyFHFLuxMyHFllWkZomHCVbvdgSggHFUi\",\"description\":\"AohDloGlyeUtfOW\",\"current_key\":\"J1w4QC+GtDEOkzZqB9Db6RaNTPklOmHQXgwcItkMmr8=\",\"key_lifetime\":9,\"next_rotation_on\":\"1989-11-12T19:58:49.411Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/371788882
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
https://api.INSTANCE.cardsavr.io/integrators/371788882
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
const merchantsites = await session.getMerchantSites(1800094325,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(1800094325, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1800094325,
  "name": "Amazon",
  "host": "amazon.com",
  "tags": [
    "DA.)Yy[gdy",
    82,
    "G$z/uZgi="
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
  "account_identification": [
    {
      "key": "username",
      "label": "Username",
      "primary_identifier": true
    },
    {
      "key": "password",
      "label": "Password"
    }
  ],
  "messages": {
    "mfa_label": "Additional information required, this code may be sent to your phone or email address.",
    "additional_info_message": "",
    "auth_message": "Linking account."
  },
  "mfa": false,
  "screenshot": true,
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

**Example GET request path:**<br>`/merchant_sites/1800094325`

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
account_identification | array | One or more property sets with key names to populated on POST/PUT /cardsavr_accounts requests, and labels to display to the end user for the type of information being requested for this site ( e.g. Username, Password, Account Number, Email, ... )
messages | object | Message properties to display to end users.  Supercedes the deprecated loging properties. The message properties are mfa_label: additional informaton required for mfs challenges such as a code sent to users phone or email, additional_info_message: some contextual info sent from CardSavr to aid the user interaction, auth_message: a label to display during during the authentication phase
mfa | boolean | Indicates if this site is MFA-enabled.
screenshot | boolean | Screenshot site for debuging.
credit_card_page | string | Merchant's credit card entry page.
forgot_password_page | string | Merchant's forgotten password page.
login_page | string | URL of login page.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

# Notifications
Notification objects define a set of actions to be triggered by certain CardSavr events, such as session completion.
## Get notification

```javascript
const notifications = await session.getNotifications(845287938,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(845287938, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 845287938,
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
  "html_template": "GTyHGxxjBTPYrwkkjvSgiXEeM",
  "text_template": "kVJeaVJaA",
  "created_on": "2011-04-02T14:07:08.586Z",
  "last_updated_on": "1983-10-27T17:46:14.992Z",
  "financial_institution": {
    "id": 19439550,
    "name": "dnihfflSdRnthBmiNucGETXNkqHosDMZstBgeVFIsGORCOlMyAvnVcNmKVIIOVq",
    "description": "HWAQsUCxcnYXdZuwxTcpvhxKS",
    "lookup_key": "UqgXppMkuVlZvwcrUEXUQWWTyYFEwnbTWutYZYAwpIuvWGrRDMerlWyMjFANlbL",
    "alternate_lookup_key": "OqquPOADEMOuywZidgxsJAkobBzpAjyuktDlduPLgNEXNhfpMPFOpeTIeiPaoKL",
    "config": {
      "spDCLbFFNQoH": "Xe[)syv,Dd)(_^",
      "ZpGtxEJMEILp": 35,
      "NLJDRxXaJjsz": false
    },
    "last_activity": "2008-04-10T18:56:45.498Z",
    "created_on": "1992-07-23T01:14:39.134Z",
    "last_updated_on": "2020-07-29T02:40:19.262Z"
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

**Example GET request path:**<br>`/notifications/845287938`

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
  "financial_institution_id": 979130542,
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
  "html_template": "GTyHGxxjBTPYrwkkjvSgiXEeM",
  "text_template": "kVJeaVJaA"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 979130542 },
	{ "name", "Sample Notification" },
	{ "type", "email" },
	{ "event", "merchant_site_updates_top" },
	{ "html_template", "GTyHGxxjBTPYrwkkjvSgiXEeM" },
	{ "text_template", "kVJeaVJaA" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 979130542 )
	.add("name", "Sample Notification" )
	.add("type", "email" )
	.add("event", "merchant_site_updates_top" )
	.add("html_template", "GTyHGxxjBTPYrwkkjvSgiXEeM" )
	.add("text_template", "kVJeaVJaA" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":979130542,\"name\":\"Sample Notification\",\"type\":\"email\",\"event\":\"merchant_site_updates_top\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"GTyHGxxjBTPYrwkkjvSgiXEeM\",\"text_template\":\"kVJeaVJaA\"}"
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
  "html_template": "oFX",
  "text_template": "ZjoIOENgbZHd"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Sample Notification" },
	{ "type", "email" },
	{ "event", "webhook_error_summary" },
	{ "html_template", "oFX" },
	{ "text_template", "ZjoIOENgbZHd" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Sample Notification" )
	.add("type", "email" )
	.add("event", "webhook_error_summary" )
	.add("html_template", "oFX" )
	.add("text_template", "ZjoIOENgbZHd" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"Sample Notification\",\"type\":\"email\",\"event\":\"webhook_error_summary\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"oFX\",\"text_template\":\"ZjoIOENgbZHd\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/845287938
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
https://api.INSTANCE.cardsavr.io/notifications/845287938
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
const notificationresults = await session.getNotificationResults(575629982,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["notification"])});
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
JsonArray response = (JsonArray)session.get(575629982, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 575629982,
  "last_attempt_date": "2001-09-29T15:08:46.271Z",
  "fi_lookup_key": "gMPKNHSMZBQqPmjNiLnYtqDOQpBARGtghlAWEYxlHESXVNHWDcWaFOizAjvofbw",
  "cuid": "cuWEJsYfzLGXUVXPClNUMHoQscEavTP",
  "status": "success",
  "attempts": 1382195373,
  "notification_data": {
    "bYdFWYWOnVEQ": "3L#Q=+KJ6=pPMS=XCshMzZsZ5RuctY",
    "oCaRCGFsMJVR": 80,
    "EuWrlYZhYRtp": false
  },
  "created_on": "2015-03-27T14:53:56.297Z",
  "last_updated_on": "1997-07-15T02:17:47.950Z",
  "notification": {
    "id": 62462956,
    "name": "CNFDJDUDjZzxMxPPTOgahjESBoHkKMQrHvYETWWPqOLVWLQvvOcGJEYHBWmBrpM",
    "type": "email",
    "event": "session_complete",
    "config": {
      "LRKXAqiLGZky": "P*b&D9CQ&#C8kEU6aYQHznQ",
      "JHtPevrgYIuS": 72,
      "XcvvZFZkXTcG": false
    },
    "html_template": "TBbagjHmHvdqlbXTB",
    "text_template": "o",
    "created_on": "1986-05-27T13:39:09.968Z",
    "last_updated_on": "2002-05-09T13:45:45.235Z"
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

**Example GET request path:**<br>`/notification_results/575629982`

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
  "notification_id": 1190943501,
  "fi_lookup_key": "gMPKNHSMZBQqPmjNiLnYtqDOQpBARGtghlAWEYxlHESXVNHWDcWaFOizAjvofbw",
  "cuid": "cuWEJsYfzLGXUVXPClNUMHoQscEavTP",
  "status": "success",
  "attempts": 1382195373,
  "notification_data": {
    "bYdFWYWOnVEQ": "3L#Q=+KJ6=pPMS=XCshMzZsZ5RuctY",
    "oCaRCGFsMJVR": 80,
    "EuWrlYZhYRtp": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 1190943501 },
	{ "fi_lookup_key", "gMPKNHSMZBQqPmjNiLnYtqDOQpBARGtghlAWEYxlHESXVNHWDcWaFOizAjvofbw" },
	{ "cuid", "cuWEJsYfzLGXUVXPClNUMHoQscEavTP" },
	{ "status", "success" },
	{ "attempts", 1382195373 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 1190943501 )
	.add("fi_lookup_key", "gMPKNHSMZBQqPmjNiLnYtqDOQpBARGtghlAWEYxlHESXVNHWDcWaFOizAjvofbw" )
	.add("cuid", "cuWEJsYfzLGXUVXPClNUMHoQscEavTP" )
	.add("status", "success" )
	.add("attempts", 1382195373 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":1190943501,\"fi_lookup_key\":\"gMPKNHSMZBQqPmjNiLnYtqDOQpBARGtghlAWEYxlHESXVNHWDcWaFOizAjvofbw\",\"cuid\":\"cuWEJsYfzLGXUVXPClNUMHoQscEavTP\",\"status\":\"success\",\"attempts\":1382195373,\"notification_data\":{\"bYdFWYWOnVEQ\":\"3L#Q=+KJ6=pPMS=XCshMzZsZ5RuctY\",\"oCaRCGFsMJVR\":80,\"EuWrlYZhYRtp\":false}}"
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
const singlesitejobs = await session.getSingleSiteJobs(1064873931,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_card","cardsavr_account","credential_requests"])});
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
JsonArray response = (JsonArray)session.get(1064873931, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1064873931,
  "status": "TIMEOUT_CREDENTIALS",
  "status_message": "TMnSFSMlOxlOtitddCppjYamZTQvgiwU",
  "termination_type": "BILLABLE",
  "custom_data": {
    "JgokyRvBOIXX": "gxDyfu]PAD49MjHhn1",
    "qbRyfWYqdBhV": 31,
    "NjGLTHQIXmJK": true
  },
  "notification_sent": false,
  "time_elapsed": 725467991,
  "started_on": "1985-11-03T19:11:28.066Z",
  "completed_on": "1981-01-23T22:47:48.634Z",
  "created_on": "1988-08-12T23:54:53.847Z",
  "last_updated_on": "1985-02-13T16:42:16.106Z",
  "cardholder": {
    "id": 1825254239,
    "financial_institution_id": 387934610,
    "agent_session_id": "TjbpPUPBOjzVeZrOSMWf",
    "type": "persistent_creds",
    "first_name": "iZEDGXDORCHTU",
    "last_name": "WlIIDjAjkKiLotqTJnHmeU",
    "email": "TpiLMwFXhmaU@TDKYkT.Qlp",
    "meta_key": "FRDaRjbDtNzdKSyLPsNCfMWxe",
    "cardholder_safe_key": "riQvU1aBAdN4T6FglHGKkQXTmGkeD+TIlk7NnFvqm3k=",
    "safe_key_hash": "YQoHkffexDqDyfrythYBxwBUPscyHgYkaSolVzeWgoLQFHXAstjbIUsGfiO",
    "custom_data": {
      "QdddGGBhcrlp": "2XU_S}iX@h*",
      "rEfraZaqMupo": 94,
      "ffScCGaRocom": false
    },
    "created_on": "2017-11-01T01:53:46.412Z",
    "last_updated_on": "1972-04-29T03:45:16.802Z"
  },
  "cardsavr_card": {
    "id": 640452263,
    "bin_id": 1850631836,
    "type": "Mastercard",
    "cvv": "aBA",
    "expiration_month": "10",
    "expiration_year": "F",
    "name_on_card": "ZZNFVwiWtjqVHrUorQXnfGTzucYWvAsXVpFtWsNoLBCZEyQFMfQXdUQnuTckZeegifcPEXnOrBwvzNteUZcMsAEORwuHnlAgpMHaSDEUYmtQlTNGPFoQNXtMRTJHWOTncAQYfaCWWivPWaZwpPvzCRINpLaRxRrxhyOBjVvvGSQALDrPwZbppLsSSjLHEtkhXHNVJtvqDvmtTssEwZuuwcwdjjnfdbHRJjverEfcAGJtCuUWcNExcwzoVqPZRx",
    "first_6": "pqmcwUALkyNCWtuljXpfxvhSdIiAMlnG",
    "first_7": "iHkGvvXOJeJGxGXRtATyuVdOoMnjcHoY",
    "first_8": "WYXEdunnotPukRSWmQfUniCXYMlaQmhI",
    "nickname": "hBfeBNLVYbGJhaXiIKuguBLRNUcMoXsUOcYsNNpnYZzafGgSCCleTUjQCUmVMeq",
    "custom_data": {
      "gRcDOsiMOrPk": "L.{MZc^NA#dIi6Z",
      "xzFosRZlocVv": 18,
      "TuiuBaxTafeV": true
    },
    "created_on": "1981-09-17T19:48:44.469Z",
    "last_updated_on": "1983-08-14T15:42:07.795Z"
  },
  "cardsavr_account": {
    "id": 311315300,
    "last_card_placed_id": 2103381406,
    "primary_account_identifier_hash": "ZMDVnuARgIxSLjTyNZrAqZKNvefvpHgevvKaAaBkgPpbniKoIbxAHGBzcKV",
    "account_identification": {
      "xDTgnAYjpcqp": "C956EFS0#,fIn-Z[/p(p",
      "JmWMTYxEakBG": 92,
      "HtBjiVuqQMVp": false
    },
    "last_login": "2010-08-18T01:52:37.991Z",
    "last_password_update": "2006-10-25T10:27:25.937Z",
    "last_saved_card": "2011-07-24T16:36:10.079Z",
    "created_on": "1996-12-23T03:41:38.200Z",
    "last_updated_on": "1985-11-01T17:27:42.262Z"
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/1064873931`

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
  "cardholder_id": 727185679,
  "card_id": 57770974,
  "account_id": 1967456699,
  "status": "TIMEOUT_CREDENTIALS",
  "custom_data": {
    "JgokyRvBOIXX": "gxDyfu]PAD49MjHhn1",
    "qbRyfWYqdBhV": 31,
    "NjGLTHQIXmJK": true
  },
  "notification_sent": false,
  "time_elapsed": 725467991,
  "started_on": "1985-11-03T19:11:28.066Z",
  "completed_on": "1981-01-23T22:47:48.634Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 727185679 },
	{ "card_id", 57770974 },
	{ "account_id", 1967456699 },
	{ "status", "TIMEOUT_CREDENTIALS" },
	{ "notification_sent", false },
	{ "time_elapsed", 725467991 },
	{ "started_on", "1985-11-03T19:11:28.066Z" },
	{ "completed_on", "1981-01-23T22:47:48.634Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 727185679 )
	.add("card_id", 57770974 )
	.add("account_id", 1967456699 )
	.add("status", "TIMEOUT_CREDENTIALS" )
	.add("notification_sent", false )
	.add("time_elapsed", 725467991 )
	.add("started_on", "1985-11-03T19:11:28.066Z" )
	.add("completed_on", "1981-01-23T22:47:48.634Z" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":727185679,\"card_id\":57770974,\"account_id\":1967456699,\"status\":\"TIMEOUT_CREDENTIALS\",\"custom_data\":{\"JgokyRvBOIXX\":\"gxDyfu]PAD49MjHhn1\",\"qbRyfWYqdBhV\":31,\"NjGLTHQIXmJK\":true},\"notification_sent\":false,\"time_elapsed\":725467991,\"started_on\":\"1985-11-03T19:11:28.066Z\",\"completed_on\":\"1981-01-23T22:47:48.634Z\"}"
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
- card_form_failed
- INVALID_CARD
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
  "card_id": 1522083180,
  "status": "ABANDONED_QUICKSTART",
  "custom_data": {
    "vFQPPPUyNXwm": "oJ,HEe,MB)=",
    "QTEPEBOsYaep": 84,
    "YPCDxJviglti": false
  },
  "notification_sent": false,
  "time_elapsed": 293418359,
  "started_on": "1982-08-13T17:12:21.890Z",
  "completed_on": "2021-09-03T23:58:23.933Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 1522083180 },
	{ "status", "ABANDONED_QUICKSTART" },
	{ "notification_sent", false },
	{ "time_elapsed", 293418359 },
	{ "started_on", "1982-08-13T17:12:21.890Z" },
	{ "completed_on", "2021-09-03T23:58:23.933Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 1522083180 )
	.add("status", "ABANDONED_QUICKSTART" )
	.add("notification_sent", false )
	.add("time_elapsed", 293418359 )
	.add("started_on", "1982-08-13T17:12:21.890Z" )
	.add("completed_on", "2021-09-03T23:58:23.933Z" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":1522083180,\"status\":\"ABANDONED_QUICKSTART\",\"custom_data\":{\"vFQPPPUyNXwm\":\"oJ,HEe,MB)=\",\"QTEPEBOsYaep\":84,\"YPCDxJviglti\":false},\"notification_sent\":false,\"time_elapsed\":293418359,\"started_on\":\"1982-08-13T17:12:21.890Z\",\"completed_on\":\"2021-09-03T23:58:23.933Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1064873931
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1064873931
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


# Transaction Record
Credit Card Transaction Record
## Get transaction record

