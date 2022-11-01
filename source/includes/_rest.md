
# Accounts
Account objects contain the account information, such as username and password, for a particular cardhoder. They are used to log in to a cardholder's account for placing a payment card.
## Get account

```javascript
const accounts = await session.getAccounts(1831318202,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","merchant_site","cardsavr_card"])});
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
JsonArray response = (JsonArray)session.get(1831318202, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1831318202,
  "last_password_update": "1988-10-30T06:11:45.411Z",
  "last_saved_card": "1990-04-12T10:46:08.611Z",
  "created_on": "1981-03-01T23:06:39.518Z",
  "last_updated_on": "2014-04-20T13:09:39.503Z",
  "cardholder": {
    "id": 1878456135,
    "financial_institution_id": 465592705,
    "agent_session_id": "gzPqhcaLLnDuPg",
    "type": "ephemeral",
    "first_name": "JydaOmvGuiojpALyDpEwMGuPtUaY",
    "last_name": "R",
    "email": "SlRKKbOgrFeR@BpjHZp.EyK",
    "meta_key": "VZl",
    "cardholder_safe_key": "StS2G1TuZP9ubuYoof4eqz1ff1P/HYKCNXAAWmzw4q0=",
    "safe_key_hash": "HidVxMOqmdJBoOEeUlGEzzbZPzGyyIIRXiLAhDZftUYuISyDZzoKcHcybmo",
    "custom_data": {
      "LIPUsDwxvEsC": "b^,Fo=GeTbO)&@%b",
      "WEjcQzHoSrkA": 35,
      "XlKwcEGdVZYh": true
    },
    "created_on": "1997-05-02T23:46:40.192Z",
    "last_updated_on": "2018-09-11T17:20:07.024Z"
  },
  "merchant_site": {
    "id": 1327841525,
    "name": "wvvxZgkaayLtRvRUGZ",
    "host": "XqcBPAoqCqbByDZAoJX",
    "tags": [
      "G+($%}Vnxbdgo!VEbH/9p(kVA",
      41,
      "1ic54Lh47jqC}"
    ],
    "interface_type": "vbs",
    "required_form_fields": [
      "$Iw2%4YYCjPrV7l-Z1",
      97,
      "2pn^}w,D(M"
    ],
    "images": [
      {
        "sbHogFXfQAtB": "fQ1$8N4C%%wX0yjL})8kNhNb",
        "BQDiBOODECPL": 79,
        "KFHMoCoHpfAR": true
      },
      {
        "RqAYhwgmwymC": "CzW=Af.3S{g=t_Ov%aQ,",
        "QQcVVRoaGYHH": 45,
        "tjzDVhwLdOQS": false
      },
      {
        "sJkgkHCgKUes": "GuwDBATt",
        "nxSALnbnqoNk": 67,
        "HjMjUnYbfDwc": false
      }
    ],
    "account_identification": [
      {
        "rXpulXICEjXe": "qN_O+3oV@A~sXL=~7UvfP)Y-rYS}).g",
        "XbbMgmMEddlA": 19,
        "GQIKVxNsccNK": false
      },
      {
        "oOuRrMJjVVjS": "g2IN2BU$4#",
        "yCstIQizeUYQ": 61,
        "zLgcIIStlWLC": true
      },
      {
        "GYctodSpcqyj": "_pcI7T",
        "NrftnwtvCuDs": 68,
        "ApyZmigNNFmQ": false
      }
    ],
    "messages": {
      "oxkqOISolJrj": "]5-BuDT+,)m2K.l@g4",
      "VqFHXeklEgbu": 62,
      "EZIomBLBzLRG": true
    },
    "mfa": true,
    "move_mouse_to_element": false,
    "screenshot": true,
    "proxy_order": [
      "jnQCt.3[f+Y*//u_(ajHFWpOyMz^4u",
      88,
      "_S)U&zQ)}H6"
    ],
    "credit_card_page": "fDlcmbphuaPFE",
    "forgot_password_page": "YIljNKIhDRoGiHOyV",
    "quick_start": false,
    "login_page": "hHot"
  },
  "cardsavr_card": {
    "id": 527912494,
    "bin_id": 934027411,
    "type": "Visa",
    "cvv": "gyN",
    "expiration_month": "1",
    "expiration_year": "z",
    "name_on_card": "nNnFuzgxlDuqwbNhLQMGPdboKXfnpEjafDZXrYTzyoxnVaMOgQhnSEjhMvAduFWBJtqNZAbXPQBtgQHcWJRQDEfKctzPFVQEjAOkaRKNHNGXogWFIXPXpqfdArPNlniwdJaUdlgzlKXQPelqQnTYWZqeEWznSXRhsLaogDwfsXKJpEZwxUyluXHvUqlLpDJxRHsbuHJSVIjvHrjcdHUWpUiOJTBxDjKlEAeDRNhRCKauNjgYLRRlDoITWdXHCJ",
    "first_6": "JQfXDvPTmqZxUnmuqaMUmqUYTJSeBfUe",
    "first_7": "NgGBtvnKjVWiUcmYejRjnjbMIMZlvymO",
    "first_8": "HElduvnnpfpiFcuJqfZzVauMwMPTfhXR",
    "nickname": "siEquHETwymDuShiyziGbaGhdmvGazKbHAoyioNUkuuuIxwyNBNrzHAiZfZhaxv",
    "custom_data": {
      "nPFZLStRQAdB": "qp[1&pO#3[mM!Qw,*@!QWRPm",
      "oBEXcUhgxyxW": 39,
      "mDgvXuDiCLqE": false
    },
    "created_on": "2001-07-12T07:05:53.281Z",
    "last_updated_on": "2021-08-12T18:11:52.502Z"
  },
  "customer_key": "qPsBWpTHPJBnWdXRE"
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

**Example GET request path:**<br>`/cardsavr_accounts/1831318202`

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
  "cardholder_id": 990367172,
  "merchant_site_id": 1358055924,
  "customer_key": "qPsBWpTHPJBnWdXRE",
  "last_card_placed_id": 1445608175,
  "account_identification": {
    "SfJheBvMBOAe": "Q-X.Y]NN5&WQKHZJ+vpaKTJlR$IH=",
    "tKtmaHhCHvwi": 39,
    "vyuIToGDDeON": false
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 990367172 },
	{ "merchant_site_id", 1358055924 },
	{ "customer_key", "qPsBWpTHPJBnWdXRE" },
	{ "last_card_placed_id", 1445608175 }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 990367172 )
	.add("merchant_site_id", 1358055924 )
	.add("customer_key", "qPsBWpTHPJBnWdXRE" )
	.add("last_card_placed_id", 1445608175 )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":990367172,\"merchant_site_id\":1358055924,\"customer_key\":\"qPsBWpTHPJBnWdXRE\",\"last_card_placed_id\":1445608175,\"account_identification\":{\"SfJheBvMBOAe\":\"Q-X.Y]NN5&WQKHZJ+vpaKTJlR$IH=\",\"tKtmaHhCHvwi\":39,\"vyuIToGDDeON\":false}}"
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
  "last_card_placed_id": 823273592,
  "account_identification": {
    "amAOmAzEylyv": "A{ls}8vw!&,AO8[zI.*",
    "DDeCwIJwUCbb": 0,
    "byuonCCrqEeC": true
  }
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 823273592 }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 823273592 )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":823273592,\"account_identification\":{\"amAOmAzEylyv\":\"A{ls}8vw!&,AO8[zI.*\",\"DDeCwIJwUCbb\":0,\"byuonCCrqEeC\":true}}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1831318202
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
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/1831318202
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
const addresses = await session.getAddresses(2109402379,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder"])});
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
JsonArray response = (JsonArray)session.get(2109402379, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2109402379,
  "address1": "DfZlSoRcFVjFSuxoSHefRLMtWqnRgduMMIAnAZvdmdvJFvgYdwNOgqPPClVejDNEyZGGzylxnpknZKONiADmUOZZaXBSYKWwYQN",
  "address2": "BuhQuSAQiMBfFsYBWugBHHbIjkhhSmWpcxyJIVJwCmcEaEpuuglWljHJrSdbnthsldUsaMbNQPqQTytdHBtnCKaagfNHeuZKsPJ",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "ilxJrkzJPnSK@kELIxU.JaN",
  "phone_number": "2065555555",
  "created_on": "2022-10-29T12:02:06.414Z",
  "last_updated_on": "1978-12-01T21:51:33.012Z",
  "cardholder": {
    "id": 1233496883,
    "financial_institution_id": 1971743169,
    "agent_session_id": "tiLLVydjWDiVqG",
    "type": "persistent_creds",
    "first_name": "mpQUVXJyCFNYMcY",
    "last_name": "kW",
    "email": "EJNGALVvEMNF@bBDojO.WnS",
    "meta_key": "OwOuwIooMYZHygqssCPKnWEy",
    "cardholder_safe_key": "i45cbUKCcQTUjFG8WMvjMEyTa9hQ+GjmruAjtZ+KLVw=",
    "safe_key_hash": "BivOMrBbwHiLlFjUBFEWwfvbMiKzdqRzTYyWeHHbvnJheFHBZAGznOsESOG",
    "custom_data": {
      "WiImczpzJAuH": "+A.{Q",
      "ziWujaXvPRYL": 70,
      "BQsEfOFeiuyh": false
    },
    "created_on": "2007-11-06T04:05:36.755Z",
    "last_updated_on": "1984-09-26T14:59:58.333Z"
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

**Example GET request path:**<br>`/cardsavr_addresses/2109402379`

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
  "cardholder_id": 1524932440,
  "address1": "DfZlSoRcFVjFSuxoSHefRLMtWqnRgduMMIAnAZvdmdvJFvgYdwNOgqPPClVejDNEyZGGzylxnpknZKONiADmUOZZaXBSYKWwYQN",
  "address2": "BuhQuSAQiMBfFsYBWugBHHbIjkhhSmWpcxyJIVJwCmcEaEpuuglWljHJrSdbnthsldUsaMbNQPqQTytdHBtnCKaagfNHeuZKsPJ",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "ilxJrkzJPnSK@kELIxU.JaN",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1524932440 },
	{ "address1", "DfZlSoRcFVjFSuxoSHefRLMtWqnRgduMMIAnAZvdmdvJFvgYdwNOgqPPClVejDNEyZGGzylxnpknZKONiADmUOZZaXBSYKWwYQN" },
	{ "address2", "BuhQuSAQiMBfFsYBWugBHHbIjkhhSmWpcxyJIVJwCmcEaEpuuglWljHJrSdbnthsldUsaMbNQPqQTytdHBtnCKaagfNHeuZKsPJ" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "ilxJrkzJPnSK@kELIxU.JaN" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1524932440 )
	.add("address1", "DfZlSoRcFVjFSuxoSHefRLMtWqnRgduMMIAnAZvdmdvJFvgYdwNOgqPPClVejDNEyZGGzylxnpknZKONiADmUOZZaXBSYKWwYQN" )
	.add("address2", "BuhQuSAQiMBfFsYBWugBHHbIjkhhSmWpcxyJIVJwCmcEaEpuuglWljHJrSdbnthsldUsaMbNQPqQTytdHBtnCKaagfNHeuZKsPJ" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "ilxJrkzJPnSK@kELIxU.JaN" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1524932440,\"address1\":\"DfZlSoRcFVjFSuxoSHefRLMtWqnRgduMMIAnAZvdmdvJFvgYdwNOgqPPClVejDNEyZGGzylxnpknZKONiADmUOZZaXBSYKWwYQN\",\"address2\":\"BuhQuSAQiMBfFsYBWugBHHbIjkhhSmWpcxyJIVJwCmcEaEpuuglWljHJrSdbnthsldUsaMbNQPqQTytdHBtnCKaagfNHeuZKsPJ\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"ilxJrkzJPnSK@kELIxU.JaN\",\"phone_number\":\"2065555555\"}"
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
  "address1": "yTkcUnhNXOGMihBSNPLpSwtvtjfdmszlwjbZlRdVFRRinoVDWKoUswbQUCylxDAdTGBgpDZfGIEeYAvltZLFJmvDlCAUzociFZL",
  "address2": "vpsHAPTkpoHdXCuMjtfGVlyZmuTqvKgHuXUPADTDIDkyZSudtMiKrxUBFHrcUemWkkmzhXpgmwHiSOQknyEYgFhOvEkItgEIbeY",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "lqPNHzgAFUJf@MHqaIA.xXv",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "yTkcUnhNXOGMihBSNPLpSwtvtjfdmszlwjbZlRdVFRRinoVDWKoUswbQUCylxDAdTGBgpDZfGIEeYAvltZLFJmvDlCAUzociFZL" },
	{ "address2", "vpsHAPTkpoHdXCuMjtfGVlyZmuTqvKgHuXUPADTDIDkyZSudtMiKrxUBFHrcUemWkkmzhXpgmwHiSOQknyEYgFhOvEkItgEIbeY" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "lqPNHzgAFUJf@MHqaIA.xXv" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "yTkcUnhNXOGMihBSNPLpSwtvtjfdmszlwjbZlRdVFRRinoVDWKoUswbQUCylxDAdTGBgpDZfGIEeYAvltZLFJmvDlCAUzociFZL" )
	.add("address2", "vpsHAPTkpoHdXCuMjtfGVlyZmuTqvKgHuXUPADTDIDkyZSudtMiKrxUBFHrcUemWkkmzhXpgmwHiSOQknyEYgFhOvEkItgEIbeY" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "lqPNHzgAFUJf@MHqaIA.xXv" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"yTkcUnhNXOGMihBSNPLpSwtvtjfdmszlwjbZlRdVFRRinoVDWKoUswbQUCylxDAdTGBgpDZfGIEeYAvltZLFJmvDlCAUzociFZL\",\"address2\":\"vpsHAPTkpoHdXCuMjtfGVlyZmuTqvKgHuXUPADTDIDkyZSudtMiKrxUBFHrcUemWkkmzhXpgmwHiSOQknyEYgFhOvEkItgEIbeY\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"lqPNHzgAFUJf@MHqaIA.xXv\",\"phone_number\":\"2065555555\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/2109402379
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/2109402379
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
const bins = await session.getBins(600818168,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(600818168, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 600818168,
  "custom_data": {
    "eqBgzmSZZrnD": "IIzld5hVide1aLv+(+Wf)S,j2w&",
    "pqenjygjdMwt": 56,
    "uRLNvESvOcEc": false
  },
  "created_on": "1982-07-28T15:57:38.657Z",
  "last_updated_on": "2018-08-06T00:34:14.967Z",
  "financial_institution": {
    "id": 752049487,
    "name": "gjGTXKSWpLNPWsGiSDrORLDxhZlcgWOnfFdmYNTRpIkUqpOvikieYtevgCqvbCp",
    "description": "ysPCYAyBbnXsRTEYfOx",
    "lookup_key": "OfCmrPAtJQWYHyTCVlMZSFglCJKGroiXRluPBwOvopWOqZlRErtYqSgUADBKoke",
    "alternate_lookup_key": "crDqakFEOwzbgsSXjrkifWlipgkdRHyJHXERoLlZgjdMSdQvDvARUjnihPxcCwJ",
    "config": {
      "XxtGieLJhhEG": "VW&UaJz[*d7uv5ZPD3GQ23bja",
      "BaXPloiUrpwk": 68,
      "ZqtLFFdlSGMJ": true
    },
    "last_activity": "2010-03-29T22:05:14.192Z",
    "created_on": "1970-11-12T04:24:29.071Z",
    "last_updated_on": "2006-11-09T20:26:45.678Z"
  },
  "bank_identification_number": "38296884"
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

**Example GET request path:**<br>`/cardsavr_bins/600818168`

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
  "financial_institution_id": 1101130844,
  "bank_identification_number": "38296884",
  "custom_data": {
    "eqBgzmSZZrnD": "IIzld5hVide1aLv+(+Wf)S,j2w&",
    "pqenjygjdMwt": 56,
    "uRLNvESvOcEc": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1101130844 },
	{ "bank_identification_number", "38296884" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1101130844 )
	.add("bank_identification_number", "38296884" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1101130844,\"bank_identification_number\":\"38296884\",\"custom_data\":{\"eqBgzmSZZrnD\":\"IIzld5hVide1aLv+(+Wf)S,j2w&\",\"pqenjygjdMwt\":56,\"uRLNvESvOcEc\":false}}"
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
  "financial_institution_id": 1575509118,
  "custom_data": {
    "lrywUOnhTUcV": "JvADJP=SRIaz",
    "KNTMHKsGgxxD": 89,
    "SWlpvhNXNTKe": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1575509118 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1575509118 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1575509118,\"custom_data\":{\"lrywUOnhTUcV\":\"JvADJP=SRIaz\",\"KNTMHKsGgxxD\":89,\"SWlpvhNXNTKe\":true}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/600818168
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/600818168
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
const cardplacementresults = await session.getCardPlacementResults(58427136,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution","merchant_site","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(58427136, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 58427136,
  "merchant_site_hostname": "LJXCpoTjjrTOLcrazPiXxINSKifUXCnPaOXzuifLqidHrtdbOPlbKvsVFtVUnwgBAurJQZGjprpLZvUpMucvBKrhsgfkAgylgEoywtydkqsWzzTzTPFXQfweiGClxsGwrahSLluULzWwltLtpzHuduchEOrtURbDDOuFdhQmwQMFGopPaDkvUsRYsgsmYNFrKdNioeoSjtATZTkSCGtEWvyjillZZydizKesWQpoWOEKkjsdgBSVpPOUvDZaRd",
  "meta_key": "MB9810411",
  "fi_name": "xKsciaTWVpCVUogtEMqTinRVetlAIiSbuHeKiIPxJThpAOcKmeGrIIcrDJHjSrV",
  "bank_identification_number": "42118518",
  "cuid": "lAnjAJKlwPSrSqfmLjTyiBePxFm",
  "par": "CtSBcyJhdMcUlwJrjeuZyZjWflYJA",
  "card_customer_key": "BkWKjTmejHjSwzNWkOVfpIsFbCkKX",
  "account_customer_key": "XQplQOT",
  "status": "SUCCESSFUL",
  "status_message": "Successful",
  "termination_type": "BILLABLE",
  "custom_data": {
    "FqlMehLUOOsM": "R$",
    "NspxvbTejvFR": 70,
    "yBxqpCoTbZcF": false
  },
  "time_elapsed": 967249220,
  "first_6": "rmHxjFuvsZLWRSsdYLEoLNRSFcsIibBZ",
  "first_7": "FDPgTZGOjIXVGKlWKplQNOxzHnxLWMrE",
  "first_8": "AQTptLxSLwPfihVUUWoJVyfOMwJhPRMg",
  "trace": "I",
  "email_sent": true,
  "completed_on": "1982-04-11T12:35:57.932Z",
  "created_on": "1977-08-08T20:53:58.118Z",
  "last_updated_on": "2009-02-07T06:55:33.386Z",
  "financial_institution": {
    "id": 1534895453,
    "name": "dYvuzaLRFipKOGHAYcTrSswsCLnZzCnqoejALUDYNTXKCXpeblvZzTVfvdHpreQ",
    "description": "wmYxdkiDMqbEsbzBZpQvI",
    "lookup_key": "dEWpLsAmrdeeoHPRiGNjAYhYGccqHmvidAEAAenVlWluchRRbwItUAGoJgrnhQA",
    "alternate_lookup_key": "zedAOoEHrIIgxPIeldJcygMJOKthBTlfRUZgxsUgzeFoopNtcKUfQPFwNOFfVSD",
    "config": {
      "YfYECKPlqdSp": "}j1r-u{-nE4M({]0=hDFd",
      "hJYemdVAMRKa": 28,
      "NhEfMRxBKTDg": false
    },
    "last_activity": "2010-06-03T10:43:30.867Z",
    "created_on": "1976-02-18T00:14:53.785Z",
    "last_updated_on": "1972-06-14T08:14:46.106Z"
  },
  "merchant_site": {
    "id": 2045026534,
    "name": "FNXYek",
    "host": "aastzAzivtrdvSjzsKstKahQxTBpHuw",
    "tags": [
      "g#8_-e/~*R}e/k@jo8]n=iF",
      76,
      "JADlZlz/bYH.Re]Jrt(tzzm9L@&&7"
    ],
    "queue_name": "vbs_queue",
    "interface_type": "vbs",
    "required_form_fields": [
      "4TgSE9_k4eB+XXecNaJ",
      65,
      "y"
    ],
    "images": [
      {
        "DiQDjFBONZJD": "@Jd",
        "AYLGPxcjOHgY": 8,
        "ABuFVAARDrrv": true
      },
      {
        "jJQDcSaljaaR": "m^",
        "OZzYtSeNYeFp": 71,
        "ASgiYPadnvzL": true
      },
      {
        "gDVIAkJVTMNR": "NGG]JHdwF4*[95GNmbli6o9W2{h7C~",
        "VkjqRxGaEHos": 65,
        "BFcrUwSibxnT": false
      }
    ],
    "account_identification": [
      {
        "NSQpLEvAdBRY": "HA*EVhc_-*]HOl#XXX00shUOyM8{P",
        "FEgldFXAmALO": 30,
        "DiHIltdKrRpk": true
      },
      {
        "RfWWKArAmnyz": "}.HaBXyt",
        "gkhxADuOHUMJ": 67,
        "OWWCVaxCbAMS": false
      },
      {
        "RKyYNoTsXdqy": "tC9[PXY_)vyKr5z/!J^s+Q0*k6WJp-Y",
        "HBcHCBTvopAa": 95,
        "QOppMptenaWm": true
      }
    ],
    "messages": {
      "bnMKZELftZDD": "/2DBNaMgK%&lPBYtYS_mE",
      "ygwcIHhFhUJw": 99,
      "femtGxAdGPtz": true
    },
    "mfa": false,
    "move_mouse_to_element": false,
    "screenshot": false,
    "proxy_order": [
      "v,c/DasYU",
      68,
      "S#Oz3P9MKW%TK}$qS54UJ+AYD@I(%"
    ],
    "credit_card_page": "PqteCSZyHgfoMLvgqMrNpafRcKjt",
    "forgot_password_page": "BgFFcmVbMxDrMowTLkJiUIPSpcmJAPg",
    "quick_start": false,
    "login_page": "Jj"
  },
  "cardsavr_bin": {
    "id": 1644157536,
    "financial_institution_id": 1695221415,
    "custom_data": {
      "CnFVoKXIugoC": "sFXloM0EDoS6]PXpzwO.H5%I",
      "GWrgkMiSIDlh": 29,
      "yttmRCGyMqHK": false
    },
    "created_on": "2005-11-26T20:25:53.319Z",
    "last_updated_on": "1989-04-13T04:30:00.660Z"
  },
  "place_card_on_single_site_job_id": 438753826
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

**Example GET request path:**<br>`/card_placement_results/58427136`

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
const cards = await session.getCards(1329190277,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_address","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(1329190277, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1329190277,
  "type": "Mastercard",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "glqcTllWeTVERGkDVSucfnJZrtmYbrpUdAGwgabSOTWRwGLgTonJDQolYOhdQMw",
  "custom_data": {
    "NplxolGEBSNO": "PDFAn*lJzN.",
    "OWKFzAnwKgCx": 42,
    "LZoKXTJWrJmQ": false
  },
  "created_on": "2012-10-15T05:19:23.351Z",
  "last_updated_on": "2003-06-29T21:21:16.815Z",
  "cardholder": {
    "id": 1758459434,
    "financial_institution_id": 849699309,
    "agent_session_id": "DBhPzbEmNOvQvolydGFDeRjQ",
    "type": "ephemeral",
    "first_name": "jVuxc",
    "last_name": "pfUWlLDgbZMbZZiJteMmMrtOMYBpQSB",
    "email": "uWEEXJyzdARc@QkVcgd.CCg",
    "meta_key": "uaXGDznNFJHPNYiZnqvEWSMMHdxyqy",
    "cardholder_safe_key": "vwIij+e7DUubawuOqMJsW+K805r0qPkCFNrKeBvcUy4=",
    "safe_key_hash": "EBVDOcxwZxKeGOgnjxKzkFycHlIZKdVWlOqAHxsLicaQHSLLsjeXSBSnSZv",
    "custom_data": {
      "kNDFfQqOybke": "D5LY-$EbDE^#Xd}m0Zm9C,ubt0a",
      "uGhnbBeFSRdt": 87,
      "DMKUHrSgeNft": true
    },
    "created_on": "2013-05-02T04:48:35.627Z",
    "last_updated_on": "2011-09-08T21:26:59.910Z"
  },
  "cardsavr_address": {
    "id": 147477522,
    "address1": "ZkiZlKbdEDWvJtHGDvVnchyvICzVWmIKcawupbvftSZyHTNGpxTynauSTNNQhbQmPIpRxMMoOMyPZnXkkhNMkQthrNizZrbYZxt",
    "address2": "VwKOigbdGdcgccxgnFBAGozXDLiPfTKDkFDsfeqgneIGQpJNcaPTeMwinXcoQXLLbGZyRdLqjfyWeZojZLXaDgaemmrAkrrszuZ",
    "city": "zdqwmlqqTbcJrfdlrmzAWLzshUAucJuPXDiImQDaqRcRqEUzdBVZJRMXJKFfLlscPPEPLxexIiveIsIakjNPvQnKPqIGaftUSZM",
    "subnational": "CQhqpmxcVXrWbWwAQbIOvmJneYwXTTejvnUVsuAUJcQxgLFZpJVdVywpObhvIeL",
    "postal_code": "WVgnGtqPMsScwybDwxUvzCvwBJuSWPY",
    "postal_other": "lvJRJrOMDLqaLAEpeqfhGgXMcwAhFBt",
    "country": "USA",
    "is_primary": false,
    "first_name": "YuCwobpqdhhMpVzEEYtivvTtU",
    "last_name": "YJbdsZePBFVS",
    "email": "rzLcNdieXuHe@qNkIZj.vPm",
    "phone_number": "njpGQFAcuvB",
    "created_on": "2012-01-03T10:25:57.690Z",
    "last_updated_on": "1971-09-21T18:41:00.480Z"
  },
  "cardsavr_bin": {
    "id": 1194871634,
    "financial_institution_id": 307023019,
    "custom_data": {
      "xaXIhnuZHzXu": "HXe0&&*O4tFfbR$FVtt",
      "PkaacrHZsBfZ": 93,
      "iUfmoTRiZNHT": false
    },
    "created_on": "1972-02-20T14:06:00.921Z",
    "last_updated_on": "1974-06-13T20:07:22.028Z"
  },
  "par": "GmPZaoLzDwKeiPMiGJealcOyMMrdG",
  "customer_key": "pWaHiCbiVniMDBqrr"
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

**Example GET request path:**<br>`/cardsavr_cards/1329190277`

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
  "cardholder_id": 1711202388,
  "address_id": 13898881,
  "bin_id": 565938320,
  "par": "GmPZaoLzDwKeiPMiGJealcOyMMrdG",
  "customer_key": "pWaHiCbiVniMDBqrr",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "glqcTllWeTVERGkDVSucfnJZrtmYbrpUdAGwgabSOTWRwGLgTonJDQolYOhdQMw",
  "custom_data": {
    "NplxolGEBSNO": "PDFAn*lJzN.",
    "OWKFzAnwKgCx": 42,
    "LZoKXTJWrJmQ": false
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1711202388 },
	{ "address_id", 13898881 },
	{ "bin_id", 565938320 },
	{ "par", "GmPZaoLzDwKeiPMiGJealcOyMMrdG" },
	{ "customer_key", "pWaHiCbiVniMDBqrr" },
	{ "pan", "4111111111111111" },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Jane Smith" },
	{ "nickname", "glqcTllWeTVERGkDVSucfnJZrtmYbrpUdAGwgabSOTWRwGLgTonJDQolYOhdQMw" }
};

CardSavrResponse<Card> card = await http.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1711202388 )
	.add("address_id", 13898881 )
	.add("bin_id", 565938320 )
	.add("par", "GmPZaoLzDwKeiPMiGJealcOyMMrdG" )
	.add("customer_key", "pWaHiCbiVniMDBqrr" )
	.add("pan", "4111111111111111" )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Jane Smith" )
	.add("nickname", "glqcTllWeTVERGkDVSucfnJZrtmYbrpUdAGwgabSOTWRwGLgTonJDQolYOhdQMw" )
	.build();
JsonValue card = session.post("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1711202388,\"address_id\":13898881,\"bin_id\":565938320,\"par\":\"GmPZaoLzDwKeiPMiGJealcOyMMrdG\",\"customer_key\":\"pWaHiCbiVniMDBqrr\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"glqcTllWeTVERGkDVSucfnJZrtmYbrpUdAGwgabSOTWRwGLgTonJDQolYOhdQMw\",\"custom_data\":{\"NplxolGEBSNO\":\"PDFAn*lJzN.\",\"OWKFzAnwKgCx\":42,\"LZoKXTJWrJmQ\":false}}"
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
  "bin_id": 1803137767,
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "VPPXzIQFFlLVQXrkBmOULgXFjxAaiklubABUqgttidfXxsSCHkFnkgGJyrErshF",
  "custom_data": {
    "UMsrxOclBecK": "BS0zswJmQ3N6KKL)_4zhG_",
    "zhfkHLDQraTG": 81,
    "hkRKrlweNKui": false
  },
  "pan": "4111111111111111"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "bin_id", 1803137767 },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Jane Smith" },
	{ "nickname", "VPPXzIQFFlLVQXrkBmOULgXFjxAaiklubABUqgttidfXxsSCHkFnkgGJyrErshF" },
	{ "pan", "4111111111111111" }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("bin_id", 1803137767 )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Jane Smith" )
	.add("nickname", "VPPXzIQFFlLVQXrkBmOULgXFjxAaiklubABUqgttidfXxsSCHkFnkgGJyrErshF" )
	.add("pan", "4111111111111111" )
	.build();
JsonValue card = session.put("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"bin_id\":1803137767,\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"VPPXzIQFFlLVQXrkBmOULgXFjxAaiklubABUqgttidfXxsSCHkFnkgGJyrErshF\",\"custom_data\":{\"UMsrxOclBecK\":\"BS0zswJmQ3N6KKL)_4zhG_\",\"zhfkHLDQraTG\":81,\"hkRKrlweNKui\":false},\"pan\":\"4111111111111111\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1329190277
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1329190277
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
const cardholders = await session.getCardholders(50049646,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(50049646, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 50049646,
  "type": "ephemeral",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "ERUrUgAupWhHvgYGDgMvkjKVpafWq",
  "custom_data": {
    "EBUYliGXXOSu": "u9!xcI&/MGvEkC2XumSV4F1kSAvAn=Y",
    "GaaXiXsDkvSI": 12,
    "mePJATFLZoMj": false
  },
  "created_on": "2002-06-03T23:56:02.069Z",
  "last_updated_on": "1970-05-29T00:52:12.767Z",
  "financial_institution": {
    "id": 2049146784,
    "name": "cnbzvmHJiMOClDwxpWrupxkSMqgXBLfQYbTuwBlbaagNSWTPTgNMKKzdTSBRxKS",
    "description": "qNfkFjYMJQPLqnOqJC",
    "lookup_key": "keGTyZeQKkyfoZutZZtCLTjPudWVJTcZuNkNzqpHCJWXLOrFdotbPqXREBuGftM",
    "alternate_lookup_key": "wQSJaXnmwDQkdesIvhpXfDsqXWxZLfSvhRqyqjphSorqeNVoEXeaJTMDXyNceaU",
    "config": {
      "ZxiCadsAaEKd": ".W",
      "NXQEUoCgwiOf": 95,
      "wQtffxZBYkup": true
    },
    "last_activity": "2021-06-29T16:28:07.435Z",
    "created_on": "1996-01-23T08:38:31.613Z",
    "last_updated_on": "1976-06-02T10:04:46.824Z"
  },
  "cuid": "FokMksUailumOYCtsZvXpZ"
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

**Example GET request path:**<br>`/cardholders/50049646`

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
  "cuid": "FokMksUailumOYCtsZvXpZ",
  "type": "ephemeral",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "ERUrUgAupWhHvgYGDgMvkjKVpafWq",
  "custom_data": {
    "EBUYliGXXOSu": "u9!xcI&/MGvEkC2XumSV4F1kSAvAn=Y",
    "GaaXiXsDkvSI": 12,
    "mePJATFLZoMj": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cuid", "FokMksUailumOYCtsZvXpZ" },
	{ "type", "ephemeral" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "ERUrUgAupWhHvgYGDgMvkjKVpafWq" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cuid", "FokMksUailumOYCtsZvXpZ" )
	.add("type", "ephemeral" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "ERUrUgAupWhHvgYGDgMvkjKVpafWq" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"cuid\":\"FokMksUailumOYCtsZvXpZ\",\"type\":\"ephemeral\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"ERUrUgAupWhHvgYGDgMvkjKVpafWq\",\"custom_data\":{\"EBUYliGXXOSu\":\"u9!xcI&/MGvEkC2XumSV4F1kSAvAn=Y\",\"GaaXiXsDkvSI\":12,\"mePJATFLZoMj\":false}}"
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
  "type": "persistent_all",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "wlRNjO",
  "custom_data": {
    "smpsQVbSmhgo": "Hkm&ZO,~F.0[!(v.d+",
    "kykdHmvtDLtZ": 53,
    "qiFZxiSvOjlg": true
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
	{ "meta_key", "wlRNjO" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("type", "persistent_all" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "wlRNjO" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"type\":\"persistent_all\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"wlRNjO\",\"custom_data\":{\"smpsQVbSmhgo\":\"Hkm&ZO,~F.0[!(v.d+\",\"kykdHmvtDLtZ\":53,\"qiFZxiSvOjlg\":true}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/50049646
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
https://api.INSTANCE.cardsavr.io/cardholders/50049646
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
const users = await session.getUsers(945185337,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(945185337, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 945185337,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1976-05-24T22:11:34.334Z",
  "is_locked": false,
  "password_lifetime": 314,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_sso_agent",
  "next_rotation_on": "2010-09-09T10:51:54.674Z",
  "created_on": "1988-05-22T02:59:29.176Z",
  "last_updated_on": "2002-08-27T01:18:40.386Z",
  "username": "jsmith123",
  "financial_institution": {
    "id": 6905612,
    "name": "uaTUOnyhxLQTYHhFtZczogdaHjmDOAFFajPgSvWzhXahElFjbDAwPerpsKJRcZJ",
    "description": "pNZhCDicLsMFVzckyfFMcshGBWlwJqZ",
    "lookup_key": "iAGItVRqbCnWouxzggsyCPKOnbbNSFNfNVGHYFEONqbZYuqbiptSGfKiUOyDyUx",
    "alternate_lookup_key": "bMEsDmLbKWsLbKUQfgZRpYXfQLJJefMSFbUisUPJTJXEdKbgbTTlVPQXRSxWUpG",
    "config": {
      "gTNAbfQAAmpN": "(GN[,RF",
      "hQNCcDZGlaYn": 47,
      "puENVxrTAUGv": true
    },
    "last_activity": "2018-07-15T14:41:59.221Z",
    "created_on": "2017-06-13T10:07:40.105Z",
    "last_updated_on": "2003-04-06T13:50:53.520Z"
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

**Example GET request path:**<br>`/cardsavr_users/945185337`

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
  "financial_institution_id": 664171994,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 314,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_sso_agent",
  "next_rotation_on": "2010-09-09T10:51:54.674Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 664171994 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 314 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "cardholder_sso_agent" },
	{ "next_rotation_on", "2010-09-09T10:51:54.674Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 664171994 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 314 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "cardholder_sso_agent" )
	.add("next_rotation_on", "2010-09-09T10:51:54.674Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":664171994,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":314,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"cardholder_sso_agent\",\"next_rotation_on\":\"2010-09-09T10:51:54.674Z\"}"
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
  "financial_institution_id": 396729165,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 218,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_sso_agent",
  "next_rotation_on": "1996-04-04T04:35:02.401Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 396729165 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 218 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "cardholder_sso_agent" },
	{ "next_rotation_on", "1996-04-04T04:35:02.401Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 396729165 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 218 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "cardholder_sso_agent" )
	.add("next_rotation_on", "1996-04-04T04:35:02.401Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":396729165,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":218,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"cardholder_sso_agent\",\"next_rotation_on\":\"1996-04-04T04:35:02.401Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/945185337
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/945185337
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
const financialinstitutions = await session.getFinancialInstitutions(871761460,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(871761460, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 871761460,
  "name": "bYdqQlCLynQKriWnkGcWYUCAellVLiCpSjvaSNDTrwoHKLAwkpUHnGpttfHgTvI",
  "description": "jPIYvJLhiueXeUWfWRiszsplN",
  "lookup_key": "KFoHkkacOkyvxdUIyMWTKrKzwMYYxDwHfdoQotiXipfKLuVJsfCbxBkfYYndrlU",
  "alternate_lookup_key": "wlgZEtaAmPunofNJiYFSVMGaJAGGHwjvCISKLQSGkmhnsrACqonaUOgBaSwGnxG",
  "last_activity": "1978-06-08T12:10:29.787Z",
  "created_on": "1985-08-13T01:10:06.645Z",
  "last_updated_on": "1979-01-07T06:51:54.003Z"
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

**Example GET request path:**<br>`/financial_institutions/871761460`

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
  "name": "bYdqQlCLynQKriWnkGcWYUCAellVLiCpSjvaSNDTrwoHKLAwkpUHnGpttfHgTvI",
  "description": "jPIYvJLhiueXeUWfWRiszsplN",
  "lookup_key": "KFoHkkacOkyvxdUIyMWTKrKzwMYYxDwHfdoQotiXipfKLuVJsfCbxBkfYYndrlU",
  "alternate_lookup_key": "wlgZEtaAmPunofNJiYFSVMGaJAGGHwjvCISKLQSGkmhnsrACqonaUOgBaSwGnxG"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "bYdqQlCLynQKriWnkGcWYUCAellVLiCpSjvaSNDTrwoHKLAwkpUHnGpttfHgTvI" },
	{ "description", "jPIYvJLhiueXeUWfWRiszsplN" },
	{ "lookup_key", "KFoHkkacOkyvxdUIyMWTKrKzwMYYxDwHfdoQotiXipfKLuVJsfCbxBkfYYndrlU" },
	{ "alternate_lookup_key", "wlgZEtaAmPunofNJiYFSVMGaJAGGHwjvCISKLQSGkmhnsrACqonaUOgBaSwGnxG" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "bYdqQlCLynQKriWnkGcWYUCAellVLiCpSjvaSNDTrwoHKLAwkpUHnGpttfHgTvI" )
	.add("description", "jPIYvJLhiueXeUWfWRiszsplN" )
	.add("lookup_key", "KFoHkkacOkyvxdUIyMWTKrKzwMYYxDwHfdoQotiXipfKLuVJsfCbxBkfYYndrlU" )
	.add("alternate_lookup_key", "wlgZEtaAmPunofNJiYFSVMGaJAGGHwjvCISKLQSGkmhnsrACqonaUOgBaSwGnxG" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"bYdqQlCLynQKriWnkGcWYUCAellVLiCpSjvaSNDTrwoHKLAwkpUHnGpttfHgTvI\",\"description\":\"jPIYvJLhiueXeUWfWRiszsplN\",\"lookup_key\":\"KFoHkkacOkyvxdUIyMWTKrKzwMYYxDwHfdoQotiXipfKLuVJsfCbxBkfYYndrlU\",\"alternate_lookup_key\":\"wlgZEtaAmPunofNJiYFSVMGaJAGGHwjvCISKLQSGkmhnsrACqonaUOgBaSwGnxG\"}"
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
  "name": "ueMGrLMRMQGlGfOByQbDznRUYonjVPnyCfIywZkJyulkUTdrGuWEpmRXJGGEcxe",
  "description": "tR",
  "lookup_key": "VcMBCODujBGJUeiwoABxzAZqYAkWGrKhummqhdKaKhZzpNWnGrOmFYxBTZBbJvX",
  "alternate_lookup_key": "xoTQJufCXHYluuWwKxEebjhYkwWyyQBaBihoXINcmmfqOjCgSBdmsJjIFYjjogt"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "ueMGrLMRMQGlGfOByQbDznRUYonjVPnyCfIywZkJyulkUTdrGuWEpmRXJGGEcxe" },
	{ "description", "tR" },
	{ "lookup_key", "VcMBCODujBGJUeiwoABxzAZqYAkWGrKhummqhdKaKhZzpNWnGrOmFYxBTZBbJvX" },
	{ "alternate_lookup_key", "xoTQJufCXHYluuWwKxEebjhYkwWyyQBaBihoXINcmmfqOjCgSBdmsJjIFYjjogt" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "ueMGrLMRMQGlGfOByQbDznRUYonjVPnyCfIywZkJyulkUTdrGuWEpmRXJGGEcxe" )
	.add("description", "tR" )
	.add("lookup_key", "VcMBCODujBGJUeiwoABxzAZqYAkWGrKhummqhdKaKhZzpNWnGrOmFYxBTZBbJvX" )
	.add("alternate_lookup_key", "xoTQJufCXHYluuWwKxEebjhYkwWyyQBaBihoXINcmmfqOjCgSBdmsJjIFYjjogt" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"ueMGrLMRMQGlGfOByQbDznRUYonjVPnyCfIywZkJyulkUTdrGuWEpmRXJGGEcxe\",\"description\":\"tR\",\"lookup_key\":\"VcMBCODujBGJUeiwoABxzAZqYAkWGrKhummqhdKaKhZzpNWnGrOmFYxBTZBbJvX\",\"alternate_lookup_key\":\"xoTQJufCXHYluuWwKxEebjhYkwWyyQBaBihoXINcmmfqOjCgSBdmsJjIFYjjogt\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/871761460
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
https://api.INSTANCE.cardsavr.io/financial_institutions/871761460
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
const integrators = await session.getIntegrators(226133169,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(226133169, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 226133169,
  "name": "XUeZKfAhkKyIkwdCYHZmDYtMWNwErivPChgjnJsmgsdInDGvd",
  "description": "pXgEBQVfWRxvDqqLOSvDvFKXxaW",
  "current_key": "wVUQ0/egWU5ar/w0bmPVZR0auC+UaEginkQBWDfrkZw=",
  "key_lifetime": 32,
  "next_rotation_on": "2003-01-17T15:49:54.690Z",
  "created_on": "2016-04-06T23:50:34.588Z",
  "last_updated_on": "2005-11-14T14:03:27.137Z"
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

**Example GET request path:**<br>`/integrators/226133169`

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
  "name": "XUeZKfAhkKyIkwdCYHZmDYtMWNwErivPChgjnJsmgsdInDGvd",
  "description": "pXgEBQVfWRxvDqqLOSvDvFKXxaW",
  "current_key": "wVUQ0/egWU5ar/w0bmPVZR0auC+UaEginkQBWDfrkZw=",
  "key_lifetime": 32,
  "next_rotation_on": "2003-01-17T15:49:54.690Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "XUeZKfAhkKyIkwdCYHZmDYtMWNwErivPChgjnJsmgsdInDGvd" },
	{ "description", "pXgEBQVfWRxvDqqLOSvDvFKXxaW" },
	{ "current_key", "wVUQ0/egWU5ar/w0bmPVZR0auC+UaEginkQBWDfrkZw=" },
	{ "key_lifetime", 32 },
	{ "next_rotation_on", "2003-01-17T15:49:54.690Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "XUeZKfAhkKyIkwdCYHZmDYtMWNwErivPChgjnJsmgsdInDGvd" )
	.add("description", "pXgEBQVfWRxvDqqLOSvDvFKXxaW" )
	.add("current_key", "wVUQ0/egWU5ar/w0bmPVZR0auC+UaEginkQBWDfrkZw=" )
	.add("key_lifetime", 32 )
	.add("next_rotation_on", "2003-01-17T15:49:54.690Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"XUeZKfAhkKyIkwdCYHZmDYtMWNwErivPChgjnJsmgsdInDGvd\",\"description\":\"pXgEBQVfWRxvDqqLOSvDvFKXxaW\",\"current_key\":\"wVUQ0/egWU5ar/w0bmPVZR0auC+UaEginkQBWDfrkZw=\",\"key_lifetime\":32,\"next_rotation_on\":\"2003-01-17T15:49:54.690Z\"}"
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
  "name": "BFBDvjSytEAxIzKOrAwgpBVSonBuERLfpXquIWFMpESJOJHUK",
  "description": "wFOGNJuuMyux",
  "current_key": "sOE5+Ry4vfICbjGwM3EFVCMxYmBWX7JKxb7pCsDDUvU=",
  "key_lifetime": 125,
  "next_rotation_on": "2017-06-18T18:34:26.038Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "BFBDvjSytEAxIzKOrAwgpBVSonBuERLfpXquIWFMpESJOJHUK" },
	{ "description", "wFOGNJuuMyux" },
	{ "current_key", "sOE5+Ry4vfICbjGwM3EFVCMxYmBWX7JKxb7pCsDDUvU=" },
	{ "key_lifetime", 125 },
	{ "next_rotation_on", "2017-06-18T18:34:26.038Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "BFBDvjSytEAxIzKOrAwgpBVSonBuERLfpXquIWFMpESJOJHUK" )
	.add("description", "wFOGNJuuMyux" )
	.add("current_key", "sOE5+Ry4vfICbjGwM3EFVCMxYmBWX7JKxb7pCsDDUvU=" )
	.add("key_lifetime", 125 )
	.add("next_rotation_on", "2017-06-18T18:34:26.038Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"BFBDvjSytEAxIzKOrAwgpBVSonBuERLfpXquIWFMpESJOJHUK\",\"description\":\"wFOGNJuuMyux\",\"current_key\":\"sOE5+Ry4vfICbjGwM3EFVCMxYmBWX7JKxb7pCsDDUvU=\",\"key_lifetime\":125,\"next_rotation_on\":\"2017-06-18T18:34:26.038Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/226133169
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
https://api.INSTANCE.cardsavr.io/integrators/226133169
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
const merchantsites = await session.getMerchantSites(559534326,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(559534326, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 559534326,
  "name": "Amazon",
  "host": "amazon.com",
  "tags": [
    "+i,^QP5AZy=RtP",
    93,
    "6R$wq9n*yndm_5azvgt~PvQ&ylnB"
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
  "mfa": true,
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

**Example GET request path:**<br>`/merchant_sites/559534326`

### <a name="response-merchant_site"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this merchant site.
name | string | 
host | string | For interface type 'dcs',  hostname of the DCS broker server for the merchant site; for interface type 'vbs' hostname of the merchant_site. e.g. amazon.com
tags | array | Tags for filtering desired merchant sites.  This could either be site status (e.g. prod, development), countries supported (e.g. usa, canada), or site attributes (e.g. synthetic).  Tags can also be compounded to create combinations: (e.g. ?tags=prod,usa&tags=synthetic means all sites tagged prod and usa as well as sites tagged synthetic)
interface_type | string | Type of interface agent to use with merchant. Set to 'dcs' for a site that has direct connect support; and to 'vbs' for a site using Robotic Process Automation
required_form_fields | array | Indicates the cardholder personal information fields that are required by this site.
images | array | URLs of the images for this merchant site.  Use a filter parameter of 'image_widths', a coomma delimited list of widths (e.g. image_widths=64).  Tile images with these widths will be returned.  The default is 128 and 32 width images.
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
const notifications = await session.getNotifications(257862309,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(257862309, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 257862309,
  "name": "Sample Notification",
  "type": "webhook",
  "event": "merchant_site_updates_all",
  "config": {
    "recipient": "cardholder",
    "url": null,
    "from_email": "CardUpdatr <no-reply@cardupdatr.app>",
    "return_path": "no-reply@cardupdatr.app",
    "send_email_time": null,
    "interval_length": null,
    "interval_type": null
  },
  "html_template": "SNnHddZSU",
  "text_template": "egMiPmliNNrJGcIk",
  "created_on": "2019-09-14T07:07:10.489Z",
  "last_updated_on": "1997-10-02T07:39:01.744Z",
  "financial_institution": {
    "id": 1267874431,
    "name": "CUCBYMBGEKUAVcYoRdqJCDiLOUPmnMUXzHfeSXDMSCPDfbGTDDulBCaYLvvzLhn",
    "description": "VXZR",
    "lookup_key": "SCJctbtQAnHbNZikZuucEeBcTUbSNgpgIRcMlbQdgyQUUBNPxedLXQXOGShqtpH",
    "alternate_lookup_key": "jDVGbtRshzikFAmaPwUaJaxRfBwBXlJFuFLcVfQlfFwupYNQUFYzzpdYRrDecBo",
    "config": {
      "ExuFbdSgmUhb": "Yt_SwULA72fR28jUqRp4I8l",
      "sQsyiWXUytrs": 90,
      "BhIZaBuGlSoA": false
    },
    "last_activity": "1989-03-19T00:54:06.690Z",
    "created_on": "2002-03-16T17:57:44.029Z",
    "last_updated_on": "1976-04-12T12:52:31.156Z"
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

**Example GET request path:**<br>`/notifications/257862309`

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
  "financial_institution_id": 58230126,
  "name": "Sample Notification",
  "type": "webhook",
  "event": "merchant_site_updates_all",
  "config": {
    "recipient": "cardholder",
    "url": null,
    "from_email": "CardUpdatr <no-reply@cardupdatr.app>",
    "return_path": "no-reply@cardupdatr.app",
    "send_email_time": null,
    "interval_length": null,
    "interval_type": null
  },
  "html_template": "SNnHddZSU",
  "text_template": "egMiPmliNNrJGcIk"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 58230126 },
	{ "name", "Sample Notification" },
	{ "type", "webhook" },
	{ "event", "merchant_site_updates_all" },
	{ "html_template", "SNnHddZSU" },
	{ "text_template", "egMiPmliNNrJGcIk" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 58230126 )
	.add("name", "Sample Notification" )
	.add("type", "webhook" )
	.add("event", "merchant_site_updates_all" )
	.add("html_template", "SNnHddZSU" )
	.add("text_template", "egMiPmliNNrJGcIk" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":58230126,\"name\":\"Sample Notification\",\"type\":\"webhook\",\"event\":\"merchant_site_updates_all\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"SNnHddZSU\",\"text_template\":\"egMiPmliNNrJGcIk\"}"
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
  "html_template": "ibSlGHrScqBPNpBoWli",
  "text_template": "kigJVfMicoqrUgUbcOi"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Sample Notification" },
	{ "type", "email" },
	{ "event", "session_complete" },
	{ "html_template", "ibSlGHrScqBPNpBoWli" },
	{ "text_template", "kigJVfMicoqrUgUbcOi" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Sample Notification" )
	.add("type", "email" )
	.add("event", "session_complete" )
	.add("html_template", "ibSlGHrScqBPNpBoWli" )
	.add("text_template", "kigJVfMicoqrUgUbcOi" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"Sample Notification\",\"type\":\"email\",\"event\":\"session_complete\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"ibSlGHrScqBPNpBoWli\",\"text_template\":\"kigJVfMicoqrUgUbcOi\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/257862309
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
https://api.INSTANCE.cardsavr.io/notifications/257862309
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
const notificationresults = await session.getNotificationResults(1523590939,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["notification"])});
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
JsonArray response = (JsonArray)session.get(1523590939, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1523590939,
  "last_attempt_date": "1975-08-02T23:48:23.652Z",
  "fi_lookup_key": "CtQcTNeqzGnuXrtXBazkslfzrdAwmwIWUQvYOeYFViDLFZCUBgEFTjmSVJWGMJZ",
  "cuid": "NaVdPHgoipwErEUFsalmvuEflqkJZgh",
  "status": "success",
  "attempts": 241250022,
  "notification_data": {
    "DMhCbuesMQWy": "1zDrSZBL6[m",
    "rCQwLWCznRaF": 44,
    "JTOjxMkxwoNN": true
  },
  "created_on": "2016-04-20T04:48:46.723Z",
  "last_updated_on": "1982-06-28T07:08:55.492Z",
  "notification": {
    "id": 860955720,
    "name": "LhoIujcorbzLImLXYIxFVucPZiDddGhemNYeTkiERzmrNpSXKJIoMEDiQRzwWLm",
    "type": "webhook",
    "event": "merchant_site_updates_all",
    "config": {
      "PpikwVrNTONY": "l#b#hQvHP^f",
      "SCOgNNukdCMx": 95,
      "PbPzkghzdypo": true
    },
    "html_template": "NbubbgxgTVuHLIwDKRlfO",
    "text_template": "dVizlcRABu",
    "created_on": "2011-01-04T08:37:47.617Z",
    "last_updated_on": "1992-04-12T03:25:53.853Z"
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

**Example GET request path:**<br>`/notification_results/1523590939`

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
  "notification_id": 1903840693,
  "fi_lookup_key": "CtQcTNeqzGnuXrtXBazkslfzrdAwmwIWUQvYOeYFViDLFZCUBgEFTjmSVJWGMJZ",
  "cuid": "NaVdPHgoipwErEUFsalmvuEflqkJZgh",
  "status": "success",
  "attempts": 241250022,
  "notification_data": {
    "DMhCbuesMQWy": "1zDrSZBL6[m",
    "rCQwLWCznRaF": 44,
    "JTOjxMkxwoNN": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 1903840693 },
	{ "fi_lookup_key", "CtQcTNeqzGnuXrtXBazkslfzrdAwmwIWUQvYOeYFViDLFZCUBgEFTjmSVJWGMJZ" },
	{ "cuid", "NaVdPHgoipwErEUFsalmvuEflqkJZgh" },
	{ "status", "success" },
	{ "attempts", 241250022 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 1903840693 )
	.add("fi_lookup_key", "CtQcTNeqzGnuXrtXBazkslfzrdAwmwIWUQvYOeYFViDLFZCUBgEFTjmSVJWGMJZ" )
	.add("cuid", "NaVdPHgoipwErEUFsalmvuEflqkJZgh" )
	.add("status", "success" )
	.add("attempts", 241250022 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":1903840693,\"fi_lookup_key\":\"CtQcTNeqzGnuXrtXBazkslfzrdAwmwIWUQvYOeYFViDLFZCUBgEFTjmSVJWGMJZ\",\"cuid\":\"NaVdPHgoipwErEUFsalmvuEflqkJZgh\",\"status\":\"success\",\"attempts\":241250022,\"notification_data\":{\"DMhCbuesMQWy\":\"1zDrSZBL6[m\",\"rCQwLWCznRaF\":44,\"JTOjxMkxwoNN\":true}}"
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
const singlesitejobs = await session.getSingleSiteJobs(690639735,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_card","cardsavr_account","credential_requests"])});
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
JsonArray response = (JsonArray)session.get(690639735, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 690639735,
  "status": "PROXY_PROBE_FAILED",
  "status_message": "qhlGtMddVkJgXkPeFyKQENpfF",
  "termination_type": "SITE_INTERACTION_FAILURE",
  "custom_data": {
    "RPeVbXsrxBDe": "vnd8*okLoxAYGTVF#J]+b",
    "Soovikhjjcpy": 83,
    "cbDVtDUNfwkT": true
  },
  "notification_sent": true,
  "time_elapsed": 2123559131,
  "started_on": "2010-06-11T01:59:59.934Z",
  "completed_on": "2016-06-17T10:02:00.317Z",
  "created_on": "1977-01-06T15:38:14.440Z",
  "last_updated_on": "1978-07-31T09:31:49.203Z",
  "cardholder": {
    "id": 431961262,
    "financial_institution_id": 1757010156,
    "agent_session_id": "kizPTkhosIYrBVHp",
    "type": "persistent_creds",
    "first_name": "ZxvPNEbZZOdL",
    "last_name": "dsDSCtKvuvAx",
    "email": "SEXVRfEOtTGv@QFUBif.xMS",
    "meta_key": "kbMIMIYjoamVxfDiEGCDSI",
    "cardholder_safe_key": "QM1WFFXDwFEOwM6uBxUfhbWdvt2xmQyScpQy/IzkEd8=",
    "safe_key_hash": "eMHBxmAEugSEELyzKWqIMktCEIFbJqcuQtUwUguYKBqBZHwYuNvQJsRnafB",
    "custom_data": {
      "GosMZZtHZSjp": "GgW5w=fX",
      "ibsBNDxurlxE": 82,
      "DpQieVmrpXFx": false
    },
    "created_on": "1989-04-29T20:50:15.345Z",
    "last_updated_on": "2016-04-08T18:49:33.147Z"
  },
  "cardsavr_card": {
    "id": 334566050,
    "bin_id": 1678255889,
    "type": "Mastercard",
    "cvv": "wUH",
    "expiration_month": "5",
    "expiration_year": "c",
    "name_on_card": "CcgpTNbQcMUkbcFJUlFfXgFNpoePNqrBhLojTtGBUdCIcWRrvbDVyjBvuOcGHqWSEoeshckErLMnluWcWEtyisPlcSvcyRkqsuyqKIkxfRVJhMBRljsvhdScBDzWsARdDWlMrUFqSyQZcQYtmGFCxFNEShiELCHsVjMmvMOSuEubgAIKBnXDzLhUxybxWpemwBUpvXSvaedmbjfRIuaUhTwSIpMehKkXEElPVYFlutzPhtZzgGItqgavWVhFyt",
    "first_6": "ZqoWCVZEMeIrrqWEcXcXnnaKGqnvwQcP",
    "first_7": "TwiktTYkvkyiDyLBFZOkAPFTMWUlPuWa",
    "first_8": "gMcXFmCSXOQKxAGxoZmGaqjepfeLWmyf",
    "nickname": "leSuDuhGvwfjbivaQQbtEeSkfyRcoBgkiaeHeREVIbFGddIUcExsTzJRZmtfSnH",
    "custom_data": {
      "LZJzuTwqIJeM": "A7(EM+)QxYR!UeTV5^jXT",
      "GaaNlLnvAVsC": 96,
      "gMhGPSgPgblq": false
    },
    "created_on": "1976-11-08T02:57:57.866Z",
    "last_updated_on": "2003-02-10T20:54:50.393Z"
  },
  "cardsavr_account": {
    "id": 1460494130,
    "last_card_placed_id": 363227181,
    "primary_account_identifier_hash": "VjcqalUqyPdyPKhwTzqzAPbimTtyQohXqSBJSKCrqUxFTlaAKCueFGWEFwk",
    "account_identification": {
      "ahrafsqPWTDc": "73Ar$J$EP)CecxD+VX_[#jxEi(D4c",
      "KlHYyoLScmiL": 53,
      "jExjZeBAmVyQ": true
    },
    "last_login": "1974-12-22T01:14:40.214Z",
    "last_password_update": "1981-05-22T01:28:01.183Z",
    "last_saved_card": "1972-07-13T01:04:46.858Z",
    "created_on": "2007-03-11T16:29:59.595Z",
    "last_updated_on": "2001-03-24T19:47:19.866Z"
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/690639735`

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
  "cardholder_id": 1415579511,
  "card_id": 1115590933,
  "account_id": 1307567035,
  "status": "PROXY_PROBE_FAILED",
  "custom_data": {
    "RPeVbXsrxBDe": "vnd8*okLoxAYGTVF#J]+b",
    "Soovikhjjcpy": 83,
    "cbDVtDUNfwkT": true
  },
  "notification_sent": true,
  "time_elapsed": 2123559131,
  "started_on": "2010-06-11T01:59:59.934Z",
  "completed_on": "2016-06-17T10:02:00.317Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1415579511 },
	{ "card_id", 1115590933 },
	{ "account_id", 1307567035 },
	{ "status", "PROXY_PROBE_FAILED" },
	{ "notification_sent", true },
	{ "time_elapsed", 2123559131 },
	{ "started_on", "2010-06-11T01:59:59.934Z" },
	{ "completed_on", "2016-06-17T10:02:00.317Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1415579511 )
	.add("card_id", 1115590933 )
	.add("account_id", 1307567035 )
	.add("status", "PROXY_PROBE_FAILED" )
	.add("notification_sent", true )
	.add("time_elapsed", 2123559131 )
	.add("started_on", "2010-06-11T01:59:59.934Z" )
	.add("completed_on", "2016-06-17T10:02:00.317Z" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1415579511,\"card_id\":1115590933,\"account_id\":1307567035,\"status\":\"PROXY_PROBE_FAILED\",\"custom_data\":{\"RPeVbXsrxBDe\":\"vnd8*okLoxAYGTVF#J]+b\",\"Soovikhjjcpy\":83,\"cbDVtDUNfwkT\":true},\"notification_sent\":true,\"time_elapsed\":2123559131,\"started_on\":\"2010-06-11T01:59:59.934Z\",\"completed_on\":\"2016-06-17T10:02:00.317Z\"}"
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
  "card_id": 288764609,
  "status": "QUEUED",
  "custom_data": {
    "cwMwkqeIUrKR": "pH[n+[z3x9n0GbberWkoF29I8Ax7L1",
    "vCuAMJlFkjWS": 24,
    "yWGZIhqLsHAn": true
  },
  "notification_sent": false,
  "time_elapsed": 1123428161,
  "started_on": "2022-03-19T18:55:28.503Z",
  "completed_on": "2002-06-13T07:22:07.559Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 288764609 },
	{ "status", "QUEUED" },
	{ "notification_sent", false },
	{ "time_elapsed", 1123428161 },
	{ "started_on", "2022-03-19T18:55:28.503Z" },
	{ "completed_on", "2002-06-13T07:22:07.559Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 288764609 )
	.add("status", "QUEUED" )
	.add("notification_sent", false )
	.add("time_elapsed", 1123428161 )
	.add("started_on", "2022-03-19T18:55:28.503Z" )
	.add("completed_on", "2002-06-13T07:22:07.559Z" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":288764609,\"status\":\"QUEUED\",\"custom_data\":{\"cwMwkqeIUrKR\":\"pH[n+[z3x9n0GbberWkoF29I8Ax7L1\",\"vCuAMJlFkjWS\":24,\"yWGZIhqLsHAn\":true},\"notification_sent\":false,\"time_elapsed\":1123428161,\"started_on\":\"2022-03-19T18:55:28.503Z\",\"completed_on\":\"2002-06-13T07:22:07.559Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/690639735
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/690639735
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

