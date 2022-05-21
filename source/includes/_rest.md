
# Accounts
Account objects contain the account information, such as username and password, for a particular cardhoder. They are used to log in to a cardholder's account for placing a payment card.
## Get account

```javascript
const accounts = await session.getAccounts(973837131,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","merchant_site","cardsavr_card"])});
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
JsonArray response = (JsonArray)session.get(973837131, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 973837131,
  "last_password_update": "1994-04-19T12:51:51.917Z",
  "last_saved_card": "1975-10-29T07:00:45.862Z",
  "created_on": "2006-01-06T17:59:09.729Z",
  "last_updated_on": "1995-09-08T00:31:15.262Z",
  "cardholder": {
    "id": 1512629588,
    "financial_institution_id": 1187820181,
    "agent_session_id": "GmnNMHtNbbvImawVT",
    "type": "ephemeral",
    "first_name": "hmks",
    "last_name": "AhbASQVSJgOYH",
    "email": "vMglxlaqPigL@JvNJtP.tVU",
    "meta_key": "zRLhVDDjRfHIbmBJzbHAUQTJ",
    "cardholder_safe_key": "rJdzanjyNv5KAE32ibVlVnvKsTAGU9T2v0BLP/8bfaA=",
    "safe_key_hash": "gsiCkeIHmNNONmAuqotvWsrYCtpYienvfccTCkGMPRExrHujnPvsdupAjQP",
    "custom_data": {
      "KEeRWxxQiwTQ": "5yw3XF.Y",
      "ZxroHNHfeZnf": 66,
      "VtEvsNoECRYz": false
    },
    "created_on": "2010-12-30T15:48:15.137Z",
    "last_updated_on": "2018-04-15T04:10:05.927Z"
  },
  "merchant_site": {
    "id": 198629437,
    "name": "zVGQToBNxJijBgclwIghCIA",
    "host": "xVBiYTOTOAkrtgKSOtdrvZzxBN",
    "tags": [
      "/B++bQnho2H)STaQ",
      60,
      "I-,@44#,vd%T*w9#{&&"
    ],
    "interface_type": "vbs",
    "required_form_fields": [
      "P66",
      39,
      "Ehg&-"
    ],
    "images": [
      {
        "cWCZgEOZgZDG": "4Sj~{q$(MRmigw@Xby&GSd{-]&*(s",
        "BkxzHFRPoYXo": 20,
        "XhDOqDNOmYKP": false
      },
      {
        "heuhhuaFlvUh": "K#lFp~wjvS_p.JIvA",
        "iqnbwfPUkqWX": 88,
        "UGfulbydOfOX": true
      },
      {
        "PIJidmOIsgkS": "2y+moC,dI",
        "tNPtsZLNhIlr": 77,
        "CrRjIIYfozhk": true
      }
    ],
    "account_identification": [
      {
        "kwCTNEqbpREU": "9=O8,Bbn@m",
        "OhPdaQFxexiA": 97,
        "eBIEPsXuuvFL": true
      },
      {
        "ftjwOdKWmnWL": "j{z{.cp9D.@",
        "bYBkXlgzzIPN": 12,
        "BUMCWFXaCnih": true
      },
      {
        "MmzAMDaDkLtf": "}3%Bggv#ZZ",
        "oViPmaYixTXQ": 78,
        "FXRqwaYBqKWN": false
      }
    ],
    "messages": {
      "UKpQBecXdELO": "lfq",
      "EsfzlCohluuC": 2,
      "MQYOpSKFQBPL": true
    },
    "mfa": true,
    "move_mouse_to_element": false,
    "proxy_order": [
      "ePD)/fjykb}",
      83,
      "EwQ(~n."
    ],
    "credit_card_page": "uWe",
    "forgot_password_page": "qL",
    "quick_start": false,
    "login_page": "PAdXnKHNvzKSBkgvMN"
  },
  "cardsavr_card": {
    "id": 1206330868,
    "bin_id": 1789801757,
    "cvv": "GuB",
    "expiration_month": "7",
    "expiration_year": "h",
    "name_on_card": "kZxDVwcxPzNEAenhmZNKGYfXgQsVqvSmPoNmiGuBmiROKvUmMoPHMKLwugCHpaojDlsFbpitjorDEJvYkfqJENIcwZEMktWCKIskdweiIgUlctPGAYbfCVbLDcXAEGGmzuhuWuZSiMhvBrWTFwbVnZsRMeGchsGtAThkBZXtILhGykkipRUXmnHGgSMcBZldTUthelMOPNGCFQJAanHWNZrUrtfbgmMgeYPQyDOBLBmcFsXOFEYGGaHeFKqMSP",
    "first_6": "UWIudXxkribPxQssYBfbpfvnPyBovoKd",
    "first_7": "oGfmNvQakGOvOTvNKLHGZVpMyvhxITpK",
    "first_8": "vnYLMJYDZmQNhbvHVbcpBIphNjAiNCxw",
    "nickname": "BSJsCgrqZrUisZfHLmKyeqOMfUfmcGAglIGPKcOSdgBFXVhulYDxWDgmMiVTZnQ",
    "created_on": "1984-03-25T15:40:20.365Z",
    "last_updated_on": "1993-10-17T04:56:39.500Z"
  },
  "customer_key": "pVtWdpIzbbKAMFyqFI"
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

**Example GET request path:**<br>`/cardsavr_accounts/973837131`

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
  "cardholder_id": 1923923045,
  "merchant_site_id": 703964414,
  "customer_key": "pVtWdpIzbbKAMFyqFI",
  "last_card_placed_id": 2080135110,
  "account_identification": {
    "MrgjVUMmYnCK": "8h_Q.Vp",
    "VNfQGFIvuYBQ": 41,
    "nlzEiYTrRSDW": false
  }
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1923923045 },
	{ "merchant_site_id", 703964414 },
	{ "customer_key", "pVtWdpIzbbKAMFyqFI" },
	{ "last_card_placed_id", 2080135110 }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1923923045 )
	.add("merchant_site_id", 703964414 )
	.add("customer_key", "pVtWdpIzbbKAMFyqFI" )
	.add("last_card_placed_id", 2080135110 )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1923923045,\"merchant_site_id\":703964414,\"customer_key\":\"pVtWdpIzbbKAMFyqFI\",\"last_card_placed_id\":2080135110,\"account_identification\":{\"MrgjVUMmYnCK\":\"8h_Q.Vp\",\"VNfQGFIvuYBQ\":41,\"nlzEiYTrRSDW\":false}}"
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
account_identification | object | no | One or more properties with key:value pairs for identifying a user and if necessary credentials such as a password. The set of key:value pairs for a site is specified in the merchant site info returned from GET /merchant_sites. Supercedes deprecated username and password properties. E.g. account_identification:{'username':'someuser','password':'thierpassword'} or account_identification:{'phone_number':'206-123-4567','pin':'1234'} or account_identification:{'account_number':'1234567890'} based on examples from GET /merchant_sites documentation

See [account response attributes](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the account_identification when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Upsert account

```javascript
const account = await session.updateAccount(1,{
  "last_card_placed_id": 1496523202,
  "account_identification": {
    "etzUOFBVKyIx": "j-xtR.X@pSX@6",
    "zXSCSThAcjXN": 18,
    "zUmpUWyDaTVP": true
  }
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 1496523202 }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 1496523202 )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":1496523202,\"account_identification\":{\"etzUOFBVKyIx\":\"j-xtR.X@pSX@6\",\"zXSCSThAcjXN\":18,\"zUmpUWyDaTVP\":true}}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/973837131
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
account_identification | object | One or more properties with key:value pairs for identifying a user and if necessary credentials such as a password. The set of key:value pairs for a site is specified in the merchant site info returned from GET /merchant_sites. Supercedes deprecated username and password properties. E.g. account_identification:{'username':'someuser','password':'thierpassword'} or account_identification:{'phone_number':'206-123-4567','pin':'1234'} or account_identification:{'account_number':'1234567890'} based on examples from GET /merchant_sites documentation

See [account response parameters](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the account_identification when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete account

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/973837131
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
const addresses = await session.getAddresses(1672492402,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder"])});
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
JsonArray response = (JsonArray)session.get(1672492402, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1672492402,
  "address1": "ERSoyVqrIcxNOKMBrhgDopNdKmuAEuedGpLJuhiXiXWDwJLbJHSMOfbPLBGnucZFRLKkLakSghrsjTyHVKBhPfhLlQnGqHiqErG",
  "address2": "OsyIPssUhGFbVwUpalkLEzNWLwJmYWDiwCcInCxfywPVTGsQtFrxGdFanawJwpwYsJRLNVQlHZLVSKIKpNyVpseedLbQNaciECo",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "mumAWcltdNxV@EeIsSS.sez",
  "phone_number": "2065555555",
  "created_on": "2007-03-22T14:10:22.696Z",
  "last_updated_on": "1988-06-22T05:45:44.955Z",
  "cardholder": {
    "id": 407827611,
    "financial_institution_id": 1863417942,
    "agent_session_id": "rAYenomSCwiGhbSIOMyMNsEhThenpdr",
    "type": "persistent",
    "first_name": "Wml",
    "last_name": "etBZQtvbpcvsupTxJDch",
    "email": "MCEmxaHodxIz@QbmGMd.TPY",
    "meta_key": "hdCzOijXLnBEbsAP",
    "cardholder_safe_key": "+A4qkPPUFinVgwqH0lc0fAw3v3Dk0IjxZeEupEx/otI=",
    "safe_key_hash": "ubEZsmLLzIcTpmbJQiPhGlvaYjAydDhmUcoTPbeqAhaZWVpPVGZjqxIcvnN",
    "custom_data": {
      "otaxdfbfBClZ": "2nE1Hkn*TQ{us1$",
      "wROWSehaAOfy": 68,
      "uQVJwktqlXfi": true
    },
    "created_on": "2008-08-15T14:17:51.711Z",
    "last_updated_on": "1972-05-11T01:48:22.894Z"
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

**Example GET request path:**<br>`/cardsavr_addresses/1672492402`

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
  "cardholder_id": 1938777643,
  "address1": "ERSoyVqrIcxNOKMBrhgDopNdKmuAEuedGpLJuhiXiXWDwJLbJHSMOfbPLBGnucZFRLKkLakSghrsjTyHVKBhPfhLlQnGqHiqErG",
  "address2": "OsyIPssUhGFbVwUpalkLEzNWLwJmYWDiwCcInCxfywPVTGsQtFrxGdFanawJwpwYsJRLNVQlHZLVSKIKpNyVpseedLbQNaciECo",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "mumAWcltdNxV@EeIsSS.sez",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1938777643 },
	{ "address1", "ERSoyVqrIcxNOKMBrhgDopNdKmuAEuedGpLJuhiXiXWDwJLbJHSMOfbPLBGnucZFRLKkLakSghrsjTyHVKBhPfhLlQnGqHiqErG" },
	{ "address2", "OsyIPssUhGFbVwUpalkLEzNWLwJmYWDiwCcInCxfywPVTGsQtFrxGdFanawJwpwYsJRLNVQlHZLVSKIKpNyVpseedLbQNaciECo" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "mumAWcltdNxV@EeIsSS.sez" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1938777643 )
	.add("address1", "ERSoyVqrIcxNOKMBrhgDopNdKmuAEuedGpLJuhiXiXWDwJLbJHSMOfbPLBGnucZFRLKkLakSghrsjTyHVKBhPfhLlQnGqHiqErG" )
	.add("address2", "OsyIPssUhGFbVwUpalkLEzNWLwJmYWDiwCcInCxfywPVTGsQtFrxGdFanawJwpwYsJRLNVQlHZLVSKIKpNyVpseedLbQNaciECo" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "mumAWcltdNxV@EeIsSS.sez" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1938777643,\"address1\":\"ERSoyVqrIcxNOKMBrhgDopNdKmuAEuedGpLJuhiXiXWDwJLbJHSMOfbPLBGnucZFRLKkLakSghrsjTyHVKBhPfhLlQnGqHiqErG\",\"address2\":\"OsyIPssUhGFbVwUpalkLEzNWLwJmYWDiwCcInCxfywPVTGsQtFrxGdFanawJwpwYsJRLNVQlHZLVSKIKpNyVpseedLbQNaciECo\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"mumAWcltdNxV@EeIsSS.sez\",\"phone_number\":\"2065555555\"}"
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
  "address1": "NoTXPskSjblqEMIkoMacdIVbeyPkHUgkbKpsgZtwebgeAsrCPyoWNudJmtoOpEAClnxBhKabiFsIsqgrtJRrhURIjBDgrEhSZwG",
  "address2": "cOTcKBBcaSllKUugTvHxjRSxnyzNkIwNhwSPKCdptjzHHnoAPZpYrOyTvsPMYHXvQFiLNPUzbanudowBTylxFOGnJKGwEmqDeRG",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "xzUGMeXWEhIG@QVIbJa.ySk",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "NoTXPskSjblqEMIkoMacdIVbeyPkHUgkbKpsgZtwebgeAsrCPyoWNudJmtoOpEAClnxBhKabiFsIsqgrtJRrhURIjBDgrEhSZwG" },
	{ "address2", "cOTcKBBcaSllKUugTvHxjRSxnyzNkIwNhwSPKCdptjzHHnoAPZpYrOyTvsPMYHXvQFiLNPUzbanudowBTylxFOGnJKGwEmqDeRG" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "xzUGMeXWEhIG@QVIbJa.ySk" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "NoTXPskSjblqEMIkoMacdIVbeyPkHUgkbKpsgZtwebgeAsrCPyoWNudJmtoOpEAClnxBhKabiFsIsqgrtJRrhURIjBDgrEhSZwG" )
	.add("address2", "cOTcKBBcaSllKUugTvHxjRSxnyzNkIwNhwSPKCdptjzHHnoAPZpYrOyTvsPMYHXvQFiLNPUzbanudowBTylxFOGnJKGwEmqDeRG" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "xzUGMeXWEhIG@QVIbJa.ySk" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"NoTXPskSjblqEMIkoMacdIVbeyPkHUgkbKpsgZtwebgeAsrCPyoWNudJmtoOpEAClnxBhKabiFsIsqgrtJRrhURIjBDgrEhSZwG\",\"address2\":\"cOTcKBBcaSllKUugTvHxjRSxnyzNkIwNhwSPKCdptjzHHnoAPZpYrOyTvsPMYHXvQFiLNPUzbanudowBTylxFOGnJKGwEmqDeRG\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"xzUGMeXWEhIG@QVIbJa.ySk\",\"phone_number\":\"2065555555\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1672492402
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1672492402
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
const bins = await session.getBins(270200887,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(270200887, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 270200887,
  "custom_data": {
    "BuWlrxQlObTg": "B6",
    "LPnpcLLFMzGP": 49,
    "WiRatHkIvWsx": false
  },
  "created_on": "1989-11-22T22:26:11.468Z",
  "last_updated_on": "2011-03-26T09:53:56.055Z",
  "financial_institution": {
    "id": 2068472368,
    "name": "kluozuWCNJHWkgXBEMtgbMJXdnzgyTSgcTCLavOdpxRmshJCOMthsvFkSabcpjc",
    "description": "Vp",
    "lookup_key": "eVLOOpOePGNwUzxcmogYmGgvgLZyobvGMCLGCcNGVxhvDguUUkeVbefGmgtCjcT",
    "alternate_lookup_key": "ILrjNrQgqebKTsGXCosehHBXoQMRkEtSxCdNAUtyQPVtBdoZHqFEEToiuOViVgc",
    "config": {
      "jaPvUdxnLbNn": "(7W%UiVwG}O[qw~q]M)L2,,6p!kXT",
      "BIvyJwZwEAYA": 74,
      "tKhmJFPhPnou": true
    },
    "last_activity": "1973-05-17T00:50:43.337Z",
    "created_on": "2014-06-03T15:04:52.593Z",
    "last_updated_on": "2014-02-21T08:16:22.123Z"
  },
  "bank_identification_number": "68921077"
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

**Example GET request path:**<br>`/cardsavr_bins/270200887`

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
  "financial_institution_id": 28748790,
  "bank_identification_number": "68921077",
  "custom_data": {
    "BuWlrxQlObTg": "B6",
    "LPnpcLLFMzGP": 49,
    "WiRatHkIvWsx": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 28748790 },
	{ "bank_identification_number", "68921077" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 28748790 )
	.add("bank_identification_number", "68921077" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":28748790,\"bank_identification_number\":\"68921077\",\"custom_data\":{\"BuWlrxQlObTg\":\"B6\",\"LPnpcLLFMzGP\":49,\"WiRatHkIvWsx\":false}}"
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
  "financial_institution_id": 1469742860,
  "custom_data": {
    "CjIHUaucxXob": "Gk^H@A48K8Ldy9.rn-P&m",
    "WrngRbTAXOTT": 19,
    "QkgHjNMmbwAL": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1469742860 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1469742860 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1469742860,\"custom_data\":{\"CjIHUaucxXob\":\"Gk^H@A48K8Ldy9.rn-P&m\",\"WrngRbTAXOTT\":19,\"QkgHjNMmbwAL\":true}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/270200887
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/270200887
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
const cardplacementresults = await session.getCardPlacementResults(377965738,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution","merchant_site","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(377965738, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 377965738,
  "merchant_site_hostname": "QigoDBxceMZTfLaHWgjNCFCICwCbIxjurxnJMcNnpTSjOBrodttAGAWZBokvKHEIVwkaFGahYrgSaZhEpyYrpWjDZJFUYLRwFxefXQCucNuQLwQmOsvMnQTCBFJDQFWqCrjRawkvxRVPIJQahRqctNmcWWFWVHzZTMLRIqWTpcHvmMSZTBkZUzQUivZYNWDzXZoAnxhDvxJiUINxPwkEIvVAUomlbeQzsnqNOQnafYjYfBQEfdpjfeXDzPHwDt",
  "meta_key": "MB9810411",
  "fi_name": "kCdqMVZzFLEbxyFLQjKZXwaLvQSMXEEKUbgGbGJMpWKUVdsCFlphsMdHrXrDvxf",
  "bank_identification_number": "98757822",
  "cuid": "gqqDu",
  "par": "PkkmZwiwWckeZawgJgvvylpFUzQqm",
  "card_customer_key": "sWyKvKZjcuviAwzgG",
  "account_customer_key": "jDwlcLAuL",
  "status": "SUCCESSFUL",
  "status_message": "Successful",
  "termination_type": "BILLABLE",
  "custom_data": {
    "EefdIorxjkuy": "_/K8F]+Dv*hFyNL1]9lzE~J&w",
    "thoOZzGoTZSD": 49,
    "CSNSNebNGjIh": false
  },
  "time_elapsed": 1919682853,
  "first_6": "ZYcApZnYeQidkhzGGFcqswSKimDVHwFA",
  "first_7": "etlGCUTxBXkWhkquqIoLuJDtSYvhZwWA",
  "first_8": "ggUfPaHrQlKTLZiEuSJUtegjIrlmDeol",
  "trace": "LGmtafDXQVEsWUluCOtaKngvC",
  "email_sent": true,
  "completed_on": "2006-03-20T15:49:04.570Z",
  "created_on": "1975-10-25T14:14:28.279Z",
  "last_updated_on": "1990-04-04T05:37:06.797Z",
  "financial_institution": {
    "id": 210350194,
    "name": "sUeQIPnjdGazWIbuxcWOgmDXdJslDKmrRfsDpHNUHreUvgNSwjOdWmLaIKuGzqg",
    "description": "VJUemiAPvJGGNKtQuIyWLTyrQJd",
    "lookup_key": "ddfbnZWUVGGTijrDyUwNfxyHGOjkyluxscTyvblOuCsZRnotdXDgRgLjWVUJTxn",
    "alternate_lookup_key": "PINnecjPkHsavkqYtCMcXRYgpxDDjnjUiKCTLWsbQHiVFEyPguSJiASTQeduspA",
    "config": {
      "IaBcqblKrsfp": "U6EF9BD=MCwO,",
      "HeXraWZRlcLk": 95,
      "erkadCuTMFxx": true
    },
    "last_activity": "2015-08-31T08:13:52.381Z",
    "created_on": "1975-02-03T08:47:59.237Z",
    "last_updated_on": "2003-10-16T03:03:19.632Z"
  },
  "merchant_site": {
    "id": 2004202323,
    "name": "mzfmWnROAxoFsHAcRSFCQaDUgRuZSaxP",
    "host": "MVjPgHByhvxmSmagrgrxFapXndLOYO",
    "tags": [
      "(",
      80,
      "k+S3n@bk8#@hU"
    ],
    "queue_name": "vbs_queue",
    "interface_type": "dcs",
    "required_form_fields": [
      ")L5C74,n3d",
      49,
      "Gj4GGDRNK@AS2(c!l"
    ],
    "images": [
      {
        "OqpNeWTTBVaO": "07~]bdj+",
        "uSoYXMBHBVQd": 37,
        "psvFiaXcZdjR": false
      },
      {
        "ExGSsImNENFJ": "VVz=Vas_tJeM~#LtKbyr]xy(vwJx[[BZ",
        "UxpqkUFPBiZi": 2,
        "gJxAyzQFlNOe": false
      },
      {
        "OlGHZuAsLWqP": "I7",
        "nKPrexHAIcQK": 35,
        "haqvFGHpTGNB": true
      }
    ],
    "account_identification": [
      {
        "LBSjaJVHBDFS": "9w&h.q_}RIGG1l).p+=R@wI",
        "lKGPavDcPujt": 100,
        "cbKbVSyueiCP": false
      },
      {
        "pwZoaWlTLxdF": "$0ztWDwXzg3oK#GNl[a}[49/A_",
        "oFGTTkqpCaRQ": 47,
        "eeRJfrOCQEMg": false
      },
      {
        "AtfzoCvyqFpR": "DlFisK,Bf8#VyyFktv&X}n}D5$d{",
        "CWuddRIgmrlE": 13,
        "hxMliTLqjQJw": false
      }
    ],
    "messages": {
      "vmAVJzAYEGZA": "gT(GD-v*Q_h2M[fUu2zYX+T@#d[.V89",
      "lqkfBxYPyKKh": 64,
      "iChvkUwsftnp": false
    },
    "mfa": false,
    "move_mouse_to_element": false,
    "proxy_order": [
      "(U7Y!r*}quks[c]HiMob",
      87,
      "^QPo{Bs9k"
    ],
    "credit_card_page": "lkCciColg",
    "forgot_password_page": "uaJuAcngQzvyyGZjxLjTdruSJklmuwx",
    "quick_start": false,
    "login_page": "tXSEkebBaVrIMkX"
  },
  "cardsavr_bin": {
    "id": 1254769237,
    "financial_institution_id": 554867625,
    "custom_data": {
      "PmonxiKTiBEX": "i7q1wKUH",
      "XNwSposvYRxz": 49,
      "ADhqVYOzAFuM": false
    },
    "created_on": "1992-02-28T09:08:23.835Z",
    "last_updated_on": "2015-12-28T03:12:19.281Z"
  },
  "place_card_on_single_site_job_id": 844537994
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

**Example GET request path:**<br>`/card_placement_results/377965738`

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
const cards = await session.getCards(1801259276,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_address","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(1801259276, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1801259276,
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "HgRVsvqoARcLmsAwdBMHBpSZvHfZMonJQiksDIrQQEEHrYLJzXegGHeZnSKnnzQ",
  "created_on": "2000-06-15T12:05:17.481Z",
  "last_updated_on": "1997-11-25T10:25:35.138Z",
  "cardholder": {
    "id": 2047402945,
    "financial_institution_id": 1237902969,
    "agent_session_id": "sC",
    "type": "persistent",
    "first_name": "DcoGSnUUFMt",
    "last_name": "hlXctSJkBuyLvlnjMMFBymv",
    "email": "bHSavzIMfyUu@bvhOOC.XHV",
    "meta_key": "HutfRirByk",
    "cardholder_safe_key": "DVhOBELXaF2snzYIp52ZBEhPghRvj7+3uihnoEFYp74=",
    "safe_key_hash": "ZjTvVAKjyUimfwIwbryMjFUilquZfUJdXdsSpdojjRmkwuCNAPchbGyHUHr",
    "custom_data": {
      "wqkYjzhfvJgO": "j[I2MV9W3TKVu)5c",
      "FTgVMMEtoYKb": 43,
      "iqcRBVbdohFA": false
    },
    "created_on": "1973-10-14T07:48:31.201Z",
    "last_updated_on": "1978-09-29T18:54:54.764Z"
  },
  "cardsavr_address": {
    "id": 103879742,
    "address1": "XknzyhKEMlKmrMjNYrBdOoDMVbHJDkOKJnkUNzdmlXzbAjxRWmCuihOaOpsiPUUYXVTTNfVhHxFvVrmRmRXTblLwCjFLGpFLKkD",
    "address2": "nfKBycfCncPWhBwgYAbkrFxWCwoNAUWVEGFwblqoxuetOXbpQAdfvfXClkomFjkOfpqHCtoHVGoEvIdpRshWQOAmdHwPzLBhTra",
    "city": "xvRZMBVvuLXjORwtvUynUjxoUkqCeqjCZaYINdPhHpagBgBDoviVMTADfKHPnbIBIskiWqgcCJYKypvJOQHXXFARskhNNGVOJKJ",
    "subnational": "lknRoKJZFDCpCXjBMqaieOicCcGPdKGaYzISbGyiSFucCrecnGhhZWhpNJNDxQN",
    "postal_code": "xPAQAwdBRMaccWpDEeBvYHlTIfMwwRD",
    "postal_other": "fKEzLMILEODDSGRmvJlXyKVARAjqASB",
    "country": "canada",
    "is_primary": false,
    "first_name": "XXvQwElO",
    "last_name": "DHNrlbGHS",
    "email": "NsPvIidjbNOd@cCXHGk.ZNd",
    "phone_number": "IRDkbMXFCRVsZATb",
    "created_on": "1984-04-03T03:04:38.173Z",
    "last_updated_on": "1985-07-23T06:09:11.403Z"
  },
  "cardsavr_bin": {
    "id": 669304141,
    "financial_institution_id": 860551531,
    "custom_data": {
      "GNlRryqvFmys": ")W}fO",
      "IcmMhdReJJlJ": 60,
      "TWAgrgQMpOVN": true
    },
    "created_on": "1971-06-01T17:20:42.535Z",
    "last_updated_on": "2014-10-23T01:42:56.343Z"
  },
  "par": "semztMoKYthmkmDAbOIFoAqhXhUry",
  "customer_key": "xjbzQMgRblaOeQOxlZjsldVe"
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
- nickname
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/cardsavr_cards?ids=1,2`

#### Singular GET requests

**Singular requests** only return the card matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_cards/1801259276`

### <a name="response-cardsavr_card"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this card.
bin_id | number (fk) [bins](#bins) | ID of BIN associated with this card.
expiration_month | string | 
expiration_year | string | 
name_on_card | string | 
nickname | string | 
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
  "cardholder_id": 872323359,
  "address_id": 843731815,
  "bin_id": 1397653929,
  "par": "semztMoKYthmkmDAbOIFoAqhXhUry",
  "customer_key": "xjbzQMgRblaOeQOxlZjsldVe",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "HgRVsvqoARcLmsAwdBMHBpSZvHfZMonJQiksDIrQQEEHrYLJzXegGHeZnSKnnzQ"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 872323359 },
	{ "address_id", 843731815 },
	{ "bin_id", 1397653929 },
	{ "par", "semztMoKYthmkmDAbOIFoAqhXhUry" },
	{ "customer_key", "xjbzQMgRblaOeQOxlZjsldVe" },
	{ "pan", "4111111111111111" },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Jane Smith" },
	{ "nickname", "HgRVsvqoARcLmsAwdBMHBpSZvHfZMonJQiksDIrQQEEHrYLJzXegGHeZnSKnnzQ" }
};

CardSavrResponse<Card> card = await http.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 872323359 )
	.add("address_id", 843731815 )
	.add("bin_id", 1397653929 )
	.add("par", "semztMoKYthmkmDAbOIFoAqhXhUry" )
	.add("customer_key", "xjbzQMgRblaOeQOxlZjsldVe" )
	.add("pan", "4111111111111111" )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Jane Smith" )
	.add("nickname", "HgRVsvqoARcLmsAwdBMHBpSZvHfZMonJQiksDIrQQEEHrYLJzXegGHeZnSKnnzQ" )
	.build();
JsonValue card = session.post("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":872323359,\"address_id\":843731815,\"bin_id\":1397653929,\"par\":\"semztMoKYthmkmDAbOIFoAqhXhUry\",\"customer_key\":\"xjbzQMgRblaOeQOxlZjsldVe\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"HgRVsvqoARcLmsAwdBMHBpSZvHfZMonJQiksDIrQQEEHrYLJzXegGHeZnSKnnzQ\"}"
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

See [card response attributes](#response-cardsavr_card).

<aside class="notice">Update calls to /cardsavr_cards require the cardholder's personal cardholder_safe_key header to encrypt and save the pan and cvv when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Upsert card

```javascript
const card = await session.updateCard(1,{
  "bin_id": 290942103,
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "nickname": "OwztvxWgFtdDYbaKwoxjGqWFsVDqhaKFEefNmKykshZwfvZlatDMYRZPSZeQaHD",
  "pan": "4111111111111111"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "bin_id", 290942103 },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Jane Smith" },
	{ "nickname", "OwztvxWgFtdDYbaKwoxjGqWFsVDqhaKFEefNmKykshZwfvZlatDMYRZPSZeQaHD" },
	{ "pan", "4111111111111111" }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("bin_id", 290942103 )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Jane Smith" )
	.add("nickname", "OwztvxWgFtdDYbaKwoxjGqWFsVDqhaKFEefNmKykshZwfvZlatDMYRZPSZeQaHD" )
	.add("pan", "4111111111111111" )
	.build();
JsonValue card = session.put("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"bin_id\":290942103,\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"nickname\":\"OwztvxWgFtdDYbaKwoxjGqWFsVDqhaKFEefNmKykshZwfvZlatDMYRZPSZeQaHD\",\"pan\":\"4111111111111111\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1801259276
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

See [card response parameters](#response-cardsavr_card).


## Delete card

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1801259276
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
const cardholders = await session.getCardholders(164082682,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(164082682, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 164082682,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "OURG",
  "custom_data": {
    "yhSIxMUzbOUJ": "R",
    "jmphyPLWWCOO": 57,
    "yUvNfdhitATX": false
  },
  "created_on": "2007-02-09T23:48:16.563Z",
  "last_updated_on": "1976-01-02T19:00:45.593Z",
  "financial_institution": {
    "id": 1865608186,
    "name": "xoMuCISUbxWILZwfMBpSlimyYjqemMZwbKLVipCusBoseeeMFQpcLkAOayypeak",
    "description": "JuT",
    "lookup_key": "UiIGacSRkKiVGufEUbwkDTIMFHkyMwaaWQeXlYBVSyFBGImoEumtsQCeSSlBgIq",
    "alternate_lookup_key": "VPVNBeZMFnwHISYykJgalHBMzzrMxOKxHgefCdySbEUSujibyuHeSvshbGVWYxd",
    "config": {
      "qMcOJmDdKqJg": "w60)6Ur}X0#-uprjE2&YkWu33-}",
      "FssvgMoeFtcl": 19,
      "zLvWdmfiszLs": true
    },
    "last_activity": "1994-08-15T12:35:32.135Z",
    "created_on": "1972-07-12T01:34:31.876Z",
    "last_updated_on": "2018-10-04T16:23:14.752Z"
  },
  "cuid": "dUVKaRwKlHJFcRAMdTXak"
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
- first_name
- last_name
- email
- meta_key
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/cardholders?ids=1,2`

#### Singular GET requests

**Singular requests** only return the cardholder matching the id provided in the path.

**Example GET request path:**<br>`/cardholders/164082682`

### <a name="response-cardholder"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this cardholder.
financial_institution_id | number (fk) [financial institutions](#financial-institutions) | 
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
  "cuid": "dUVKaRwKlHJFcRAMdTXak",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "OURG",
  "custom_data": {
    "yhSIxMUzbOUJ": "R",
    "jmphyPLWWCOO": 57,
    "yUvNfdhitATX": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cuid", "dUVKaRwKlHJFcRAMdTXak" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "OURG" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cuid", "dUVKaRwKlHJFcRAMdTXak" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "OURG" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"cuid\":\"dUVKaRwKlHJFcRAMdTXak\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"OURG\",\"custom_data\":{\"yhSIxMUzbOUJ\":\"R\",\"jmphyPLWWCOO\":57,\"yUvNfdhitATX\":false}}"
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
first_name | string | no | 
last_name | string | no | 
email | string | no | 
meta_key | string | no | Key used for billing record identification; automatically generated during card creation.
custom_data | object | no | Additional data that can be added to the cardholder if needed.

See [cardholder response attributes](#response-cardholder).


## Upsert cardholder

```javascript
const cardholder = await session.updateCardholder(1,{
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "UTuWTPI",
  "custom_data": {
    "civafTcGLaqe": "l&_(PXS",
    "GUKtKIYkqCuD": 93,
    "miIolAIPqUjF": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "UTuWTPI" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "UTuWTPI" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"UTuWTPI\",\"custom_data\":{\"civafTcGLaqe\":\"l&_(PXS\",\"GUKtKIYkqCuD\":93,\"miIolAIPqUjF\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/164082682
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
https://api.INSTANCE.cardsavr.io/cardholders/164082682
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
const users = await session.getUsers(1803710972,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(1803710972, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1803710972,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "2015-02-15T10:22:45.867Z",
  "is_locked": false,
  "password_lifetime": 336,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "customer_agent",
  "next_rotation_on": "1974-05-07T10:53:38.658Z",
  "created_on": "1995-06-12T20:13:33.315Z",
  "last_updated_on": "1975-01-31T20:19:24.317Z",
  "username": "jsmith123",
  "financial_institution": {
    "id": 987801565,
    "name": "PXsFRncNXVAHdbTvdDEbDYNlcGCvXBudbxUCbZETxmJSeBUHqAfpsQQluqAqRku",
    "description": "jgXQisuyWOpSIZkkrVXjqrQYXCSX",
    "lookup_key": "kWKBToyCGJmSUGYVgnDRzsBTIlHfklBiqgRhjsBjElRNTCfYcdptRaUWLTUCSIg",
    "alternate_lookup_key": "AbjBCtZSjslPqxzFFRvWbkdpIsFTKNudUDmmVmgCDQKUyxjNewTtqgTnGFrFaXS",
    "config": {
      "AslYjcZndVjb": "YBc",
      "UfujRuwelpne": 13,
      "ZfZorEbOUPBx": true
    },
    "last_activity": "2022-01-29T02:24:05.928Z",
    "created_on": "2003-07-19T20:52:46.521Z",
    "last_updated_on": "1999-01-31T00:05:34.472Z"
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

**Example GET request path:**<br>`/cardsavr_users/1803710972`

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
  "financial_institution_id": 517849245,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 336,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "customer_agent",
  "next_rotation_on": "1974-05-07T10:53:38.658Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 517849245 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 336 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "customer_agent" },
	{ "next_rotation_on", "1974-05-07T10:53:38.658Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 517849245 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 336 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "customer_agent" )
	.add("next_rotation_on", "1974-05-07T10:53:38.658Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":517849245,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":336,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"customer_agent\",\"next_rotation_on\":\"1974-05-07T10:53:38.658Z\"}"
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
  "financial_institution_id": 1334572794,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 36,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "admin",
  "next_rotation_on": "1984-05-21T08:33:27.790Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1334572794 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 36 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "admin" },
	{ "next_rotation_on", "1984-05-21T08:33:27.790Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1334572794 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 36 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "admin" )
	.add("next_rotation_on", "1984-05-21T08:33:27.790Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1334572794,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":36,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"admin\",\"next_rotation_on\":\"1984-05-21T08:33:27.790Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/1803710972
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/1803710972
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
const financialinstitutions = await session.getFinancialInstitutions(1294310812,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(1294310812, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1294310812,
  "name": "ZyHMZAjlLiMHackArARRjNdDmlcRlrANgHhBgIlwsYKVqamXhTyYQxancikLkHu",
  "description": "mJmTqOXYAUoNCyxIzmStDVszOtdwgQF",
  "lookup_key": "rQfwTAiVFznmeQHsYHGtrxSQrCMDCxygvQWwAYUZoKuFdQZlegzLuVyhkmlVZDE",
  "alternate_lookup_key": "AhrtwmiicATRYdKtYslytYCxkuqTEkwGlNTmNqTeYUNVBmvRdJhXxzQJSBFxPvc",
  "last_activity": "2022-03-09T21:45:22.607Z",
  "created_on": "2007-06-02T16:02:44.317Z",
  "last_updated_on": "1970-07-18T07:48:46.027Z"
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

**Example GET request path:**<br>`/financial_institutions/1294310812`

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
  "name": "ZyHMZAjlLiMHackArARRjNdDmlcRlrANgHhBgIlwsYKVqamXhTyYQxancikLkHu",
  "description": "mJmTqOXYAUoNCyxIzmStDVszOtdwgQF",
  "lookup_key": "rQfwTAiVFznmeQHsYHGtrxSQrCMDCxygvQWwAYUZoKuFdQZlegzLuVyhkmlVZDE",
  "alternate_lookup_key": "AhrtwmiicATRYdKtYslytYCxkuqTEkwGlNTmNqTeYUNVBmvRdJhXxzQJSBFxPvc"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "ZyHMZAjlLiMHackArARRjNdDmlcRlrANgHhBgIlwsYKVqamXhTyYQxancikLkHu" },
	{ "description", "mJmTqOXYAUoNCyxIzmStDVszOtdwgQF" },
	{ "lookup_key", "rQfwTAiVFznmeQHsYHGtrxSQrCMDCxygvQWwAYUZoKuFdQZlegzLuVyhkmlVZDE" },
	{ "alternate_lookup_key", "AhrtwmiicATRYdKtYslytYCxkuqTEkwGlNTmNqTeYUNVBmvRdJhXxzQJSBFxPvc" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "ZyHMZAjlLiMHackArARRjNdDmlcRlrANgHhBgIlwsYKVqamXhTyYQxancikLkHu" )
	.add("description", "mJmTqOXYAUoNCyxIzmStDVszOtdwgQF" )
	.add("lookup_key", "rQfwTAiVFznmeQHsYHGtrxSQrCMDCxygvQWwAYUZoKuFdQZlegzLuVyhkmlVZDE" )
	.add("alternate_lookup_key", "AhrtwmiicATRYdKtYslytYCxkuqTEkwGlNTmNqTeYUNVBmvRdJhXxzQJSBFxPvc" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"ZyHMZAjlLiMHackArARRjNdDmlcRlrANgHhBgIlwsYKVqamXhTyYQxancikLkHu\",\"description\":\"mJmTqOXYAUoNCyxIzmStDVszOtdwgQF\",\"lookup_key\":\"rQfwTAiVFznmeQHsYHGtrxSQrCMDCxygvQWwAYUZoKuFdQZlegzLuVyhkmlVZDE\",\"alternate_lookup_key\":\"AhrtwmiicATRYdKtYslytYCxkuqTEkwGlNTmNqTeYUNVBmvRdJhXxzQJSBFxPvc\"}"
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
  "name": "CbxSWUrQFPLBJRGCHTHALyOJLIkwoYERGPnmaNxrdzqPYeEgoNshRSNhIxsVQXl",
  "description": "CYSzSGBNAexsdWHBmVsyqykwJiuT",
  "lookup_key": "QjDxiueyWtCKEQfaTGZHIhgFAWVyOIGGZXJtZmXLORVXIiIrKjDLSQMWjloeWGD",
  "alternate_lookup_key": "sDOMOWBfYQXvrItOWnKnBTxgbCSDLcIVxwHZlUGuZPkVSuANzKquwOztNNHeJSB"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "CbxSWUrQFPLBJRGCHTHALyOJLIkwoYERGPnmaNxrdzqPYeEgoNshRSNhIxsVQXl" },
	{ "description", "CYSzSGBNAexsdWHBmVsyqykwJiuT" },
	{ "lookup_key", "QjDxiueyWtCKEQfaTGZHIhgFAWVyOIGGZXJtZmXLORVXIiIrKjDLSQMWjloeWGD" },
	{ "alternate_lookup_key", "sDOMOWBfYQXvrItOWnKnBTxgbCSDLcIVxwHZlUGuZPkVSuANzKquwOztNNHeJSB" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "CbxSWUrQFPLBJRGCHTHALyOJLIkwoYERGPnmaNxrdzqPYeEgoNshRSNhIxsVQXl" )
	.add("description", "CYSzSGBNAexsdWHBmVsyqykwJiuT" )
	.add("lookup_key", "QjDxiueyWtCKEQfaTGZHIhgFAWVyOIGGZXJtZmXLORVXIiIrKjDLSQMWjloeWGD" )
	.add("alternate_lookup_key", "sDOMOWBfYQXvrItOWnKnBTxgbCSDLcIVxwHZlUGuZPkVSuANzKquwOztNNHeJSB" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"CbxSWUrQFPLBJRGCHTHALyOJLIkwoYERGPnmaNxrdzqPYeEgoNshRSNhIxsVQXl\",\"description\":\"CYSzSGBNAexsdWHBmVsyqykwJiuT\",\"lookup_key\":\"QjDxiueyWtCKEQfaTGZHIhgFAWVyOIGGZXJtZmXLORVXIiIrKjDLSQMWjloeWGD\",\"alternate_lookup_key\":\"sDOMOWBfYQXvrItOWnKnBTxgbCSDLcIVxwHZlUGuZPkVSuANzKquwOztNNHeJSB\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/1294310812
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
https://api.INSTANCE.cardsavr.io/financial_institutions/1294310812
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
const integrators = await session.getIntegrators(613966821,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(613966821, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 613966821,
  "name": "xmFbAFtVPZJHolShWXBknlDDXtpzNGzyxKUlecfZhEDBFdkaM",
  "description": "HgZCWusxgwxndOESEyxSTVms",
  "current_key": "Jttw+GteZ0eNOvsZx4Rt5RFUE1Dq+VB5jf5v+evriJk=",
  "key_lifetime": 236,
  "next_rotation_on": "2018-11-18T10:17:24.902Z",
  "created_on": "1984-05-12T00:09:25.679Z",
  "last_updated_on": "2017-09-30T19:55:59.873Z"
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

**Example GET request path:**<br>`/integrators/613966821`

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
  "name": "xmFbAFtVPZJHolShWXBknlDDXtpzNGzyxKUlecfZhEDBFdkaM",
  "description": "HgZCWusxgwxndOESEyxSTVms",
  "current_key": "Jttw+GteZ0eNOvsZx4Rt5RFUE1Dq+VB5jf5v+evriJk=",
  "key_lifetime": 236,
  "next_rotation_on": "2018-11-18T10:17:24.902Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "xmFbAFtVPZJHolShWXBknlDDXtpzNGzyxKUlecfZhEDBFdkaM" },
	{ "description", "HgZCWusxgwxndOESEyxSTVms" },
	{ "current_key", "Jttw+GteZ0eNOvsZx4Rt5RFUE1Dq+VB5jf5v+evriJk=" },
	{ "key_lifetime", 236 },
	{ "next_rotation_on", "2018-11-18T10:17:24.902Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "xmFbAFtVPZJHolShWXBknlDDXtpzNGzyxKUlecfZhEDBFdkaM" )
	.add("description", "HgZCWusxgwxndOESEyxSTVms" )
	.add("current_key", "Jttw+GteZ0eNOvsZx4Rt5RFUE1Dq+VB5jf5v+evriJk=" )
	.add("key_lifetime", 236 )
	.add("next_rotation_on", "2018-11-18T10:17:24.902Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"xmFbAFtVPZJHolShWXBknlDDXtpzNGzyxKUlecfZhEDBFdkaM\",\"description\":\"HgZCWusxgwxndOESEyxSTVms\",\"current_key\":\"Jttw+GteZ0eNOvsZx4Rt5RFUE1Dq+VB5jf5v+evriJk=\",\"key_lifetime\":236,\"next_rotation_on\":\"2018-11-18T10:17:24.902Z\"}"
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
  "name": "pSPVPuNmpAPJQLZrGcikAfHpRDOUilWDtrhWhtKjMwZjlhLNQ",
  "description": "ypZKyyctvjHkpUhGnuKW",
  "current_key": "LZhWI/Qg6kVOUBLvxuH6401+3Zd+5JqraFUbFFuH55g=",
  "key_lifetime": 42,
  "next_rotation_on": "1998-05-19T22:57:28.227Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "pSPVPuNmpAPJQLZrGcikAfHpRDOUilWDtrhWhtKjMwZjlhLNQ" },
	{ "description", "ypZKyyctvjHkpUhGnuKW" },
	{ "current_key", "LZhWI/Qg6kVOUBLvxuH6401+3Zd+5JqraFUbFFuH55g=" },
	{ "key_lifetime", 42 },
	{ "next_rotation_on", "1998-05-19T22:57:28.227Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "pSPVPuNmpAPJQLZrGcikAfHpRDOUilWDtrhWhtKjMwZjlhLNQ" )
	.add("description", "ypZKyyctvjHkpUhGnuKW" )
	.add("current_key", "LZhWI/Qg6kVOUBLvxuH6401+3Zd+5JqraFUbFFuH55g=" )
	.add("key_lifetime", 42 )
	.add("next_rotation_on", "1998-05-19T22:57:28.227Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"pSPVPuNmpAPJQLZrGcikAfHpRDOUilWDtrhWhtKjMwZjlhLNQ\",\"description\":\"ypZKyyctvjHkpUhGnuKW\",\"current_key\":\"LZhWI/Qg6kVOUBLvxuH6401+3Zd+5JqraFUbFFuH55g=\",\"key_lifetime\":42,\"next_rotation_on\":\"1998-05-19T22:57:28.227Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/613966821
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
https://api.INSTANCE.cardsavr.io/integrators/613966821
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
const merchantsites = await session.getMerchantSites(1384152912,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(1384152912, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1384152912,
  "name": "Amazon",
  "host": "amazon.com",
  "tags": [
    "#AP]7{l9v9yNu",
    97,
    "hL/W4cbJ=84#YD3K8%TirB)A5h"
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

**Example batch GET request path:**<br>`/merchant_sites?ids=1,2`

#### Singular GET requests

**Singular requests** only return the merchant site matching the id provided in the path.

**Example GET request path:**<br>`/merchant_sites/1384152912`

### <a name="response-merchant_site"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this merchant site.
name | string | 
host | string | For interface type 'dcs',  hostname of the DCS broker server for the merchant site; for interface type 'vbs' hostname of the merchant_site. e.g. amazon.com
tags | array | Tags for filtering desired merchant sites.  This could either be site status (e.g. prod, development), countries supported (e.g. usa, canada), or site attributes (e.g. synthetic).  Tags can also be compounded to create combinations: (e.g. ?tags=prod,usa&tags=synthetic means all sites tagged prod and usa as well as sites tagged synthetic)
interface_type | string | Type of interface agent to use with merchant. Set to 'dcs' for a site that has direct connect support; and to 'vbs' for a site using Robotic Process Automation
required_form_fields | array | Indicates the cardholder personal information fields that are required by this site.
images | array | URLs of the images for this merchant site.
account_identification | array | One or more property sets with key names to populated on POST/PUT /cardsavr_accounts requests, and labels to display to the end user for the type of information being requested for this site ( e.g. Username, Password, Account Number, Email, ... )
messages | object | Message properties to display to end users.  Supercedes the deprecated loging properties. The message properties are mfa_label: additional informaton required for mfs challenges such as a code sent to users phone or email, additional_info_message: some contextual info sent from CardSavr to aid the user interaction, auth_message: a label to display during during the authentication phase
mfa | boolean | Indicates if this site is MFA-enabled.
credit_card_page | string | Merchant's credit card entry page.
forgot_password_page | string | Merchant's forgotten password page.
login_page | string | URL of login page.

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

# Notifications
Notification objects define a set of actions to be triggered by certain CardSavr events, such as session completion.
## Get notification

```javascript
const notifications = await session.getNotifications(1845472776,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(1845472776, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1845472776,
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
  "html_template": "ksc",
  "text_template": "kSnQbGnwoAuLbpSVCMubGzAyGHl",
  "created_on": "1981-04-04T07:35:03.797Z",
  "last_updated_on": "2011-05-07T16:35:54.597Z",
  "financial_institution": {
    "id": 1628464123,
    "name": "TXLWlbleUONQcTFChoGJCYtaEfeQsherrkxzyaXgraxcJtjclcDvlYItCvgGAKf",
    "description": "FrQCkbceMIbnhvTbeWUa",
    "lookup_key": "HHmqBUJYjvjiJPpayFviJgPqFjzynWegBrZNAlfwczzNkduLkwSdujbCQAhxqGx",
    "alternate_lookup_key": "FhvmFIOILuQdZocLjKmJTqwJLAKvPTtEHEONWbdTJYlBMssvRzhBhhVIifiGVIr",
    "config": {
      "bvoUPFYkCEHs": ",]!o+FXIr5",
      "GzbJThJIepHP": 95,
      "LYuXOdmJrdeb": true
    },
    "last_activity": "2017-01-26T12:43:35.511Z",
    "created_on": "2006-03-30T18:08:54.687Z",
    "last_updated_on": "1992-06-07T22:10:02.540Z"
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

**Example GET request path:**<br>`/notifications/1845472776`

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
  "financial_institution_id": 1875010046,
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
  "html_template": "ksc",
  "text_template": "kSnQbGnwoAuLbpSVCMubGzAyGHl"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1875010046 },
	{ "name", "Sample Notification" },
	{ "type", "webhook" },
	{ "event", "merchant_site_updates_top" },
	{ "html_template", "ksc" },
	{ "text_template", "kSnQbGnwoAuLbpSVCMubGzAyGHl" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1875010046 )
	.add("name", "Sample Notification" )
	.add("type", "webhook" )
	.add("event", "merchant_site_updates_top" )
	.add("html_template", "ksc" )
	.add("text_template", "kSnQbGnwoAuLbpSVCMubGzAyGHl" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1875010046,\"name\":\"Sample Notification\",\"type\":\"webhook\",\"event\":\"merchant_site_updates_top\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"ksc\",\"text_template\":\"kSnQbGnwoAuLbpSVCMubGzAyGHl\"}"
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
  "html_template": "aJDkNmQIpAyG",
  "text_template": "IJjHbCqMMFCLbLUexSHFSrAbm"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Sample Notification" },
	{ "type", "email" },
	{ "event", "merchant_site_updates_all" },
	{ "html_template", "aJDkNmQIpAyG" },
	{ "text_template", "IJjHbCqMMFCLbLUexSHFSrAbm" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Sample Notification" )
	.add("type", "email" )
	.add("event", "merchant_site_updates_all" )
	.add("html_template", "aJDkNmQIpAyG" )
	.add("text_template", "IJjHbCqMMFCLbLUexSHFSrAbm" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"Sample Notification\",\"type\":\"email\",\"event\":\"merchant_site_updates_all\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"aJDkNmQIpAyG\",\"text_template\":\"IJjHbCqMMFCLbLUexSHFSrAbm\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/1845472776
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
https://api.INSTANCE.cardsavr.io/notifications/1845472776
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
const notificationresults = await session.getNotificationResults(1198888614,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["notification"])});
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
JsonArray response = (JsonArray)session.get(1198888614, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1198888614,
  "last_attempt_date": "2015-04-10T08:44:15.725Z",
  "fi_lookup_key": "PXOcBVhQQuuRTGcukWSyxTcMhLTRKFzAtfOxOmbCiDBbtpSCMXktyvExjOuwDmF",
  "cuid": "bekxR",
  "status": "failure",
  "attempts": 475900061,
  "notification_data": {
    "LtsfXsHBbBaJ": "t(._zf-fw#FM3+FHv,S",
    "CuvvWwwUFfHZ": 100,
    "leinEdnCozbp": true
  },
  "created_on": "1990-11-18T13:12:23.374Z",
  "last_updated_on": "1990-05-31T10:42:05.485Z",
  "notification": {
    "id": 1666193340,
    "name": "ZInsUvDBGTrvaNotbTfwLiNzexEsoLTSjYbISMUWsEfrzZbhDNoOQymfOGPpcnL",
    "type": "email",
    "event": "merchant_site_updates_top",
    "config": {
      "VfUYUKIbCdAz": "OPD_VJ*x!@Di+fwtNBd",
      "nrRsaMLMKDOx": 43,
      "GJnbVWMGzUZX": false
    },
    "html_template": "mtgSMi",
    "text_template": "aLPeaocNgDEaruntFpJbK",
    "created_on": "1982-03-11T13:36:09.863Z",
    "last_updated_on": "1974-10-08T04:39:53.969Z"
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

**Example GET request path:**<br>`/notification_results/1198888614`

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
  "notification_id": 16946184,
  "fi_lookup_key": "PXOcBVhQQuuRTGcukWSyxTcMhLTRKFzAtfOxOmbCiDBbtpSCMXktyvExjOuwDmF",
  "cuid": "bekxR",
  "status": "failure",
  "attempts": 475900061,
  "notification_data": {
    "LtsfXsHBbBaJ": "t(._zf-fw#FM3+FHv,S",
    "CuvvWwwUFfHZ": 100,
    "leinEdnCozbp": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 16946184 },
	{ "fi_lookup_key", "PXOcBVhQQuuRTGcukWSyxTcMhLTRKFzAtfOxOmbCiDBbtpSCMXktyvExjOuwDmF" },
	{ "cuid", "bekxR" },
	{ "status", "failure" },
	{ "attempts", 475900061 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 16946184 )
	.add("fi_lookup_key", "PXOcBVhQQuuRTGcukWSyxTcMhLTRKFzAtfOxOmbCiDBbtpSCMXktyvExjOuwDmF" )
	.add("cuid", "bekxR" )
	.add("status", "failure" )
	.add("attempts", 475900061 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":16946184,\"fi_lookup_key\":\"PXOcBVhQQuuRTGcukWSyxTcMhLTRKFzAtfOxOmbCiDBbtpSCMXktyvExjOuwDmF\",\"cuid\":\"bekxR\",\"status\":\"failure\",\"attempts\":475900061,\"notification_data\":{\"LtsfXsHBbBaJ\":\"t(._zf-fw#FM3+FHv,S\",\"CuvvWwwUFfHZ\":100,\"leinEdnCozbp\":true}}"
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
const singlesitejobs = await session.getSingleSiteJobs(1391070587,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_card","cardsavr_account","credential_requests"])});
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
JsonArray response = (JsonArray)session.get(1391070587, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1391070587,
  "status": "TOO_MANY_LOGIN_FAILURES",
  "status_message": "jvMRsbnHtRkCcTmhzmVGWmv",
  "termination_type": "NEVER_STARTED",
  "custom_data": {
    "wAQfMJYZrwcb": "L",
    "SZwJJNyvbiAD": 41,
    "QlJlZmpTsJND": false
  },
  "notification_sent": false,
  "time_elapsed": 635688588,
  "started_on": "1984-05-29T05:29:30.852Z",
  "completed_on": "1992-10-31T11:42:46.423Z",
  "created_on": "2009-07-18T08:27:50.639Z",
  "last_updated_on": "1978-01-28T12:06:07.505Z",
  "cardholder": {
    "id": 1321081152,
    "financial_institution_id": 165341638,
    "agent_session_id": "KcGhtFCZWSDp",
    "type": "persistent",
    "first_name": "kn",
    "last_name": "TSJgMyKteJHdNkkCrdKTmJUl",
    "email": "pLXvihaZrlzr@DZXxFh.yTY",
    "meta_key": "Fr",
    "cardholder_safe_key": "izgAvgfuVMD9JJ+h4eVZ2lc2QLnOZ6XQL25b1zJp+P8=",
    "safe_key_hash": "RUpBTzEkwAhUviPofOLKbhEcfsQCyAlmiFGtqJdsKLeFbElGaGmDqrMPPIw",
    "custom_data": {
      "dDmOORntaEum": "7]so.6=Vc733yLh)$",
      "louBIsqtnVGr": 25,
      "kVHucbtwMfcP": true
    },
    "created_on": "1982-11-18T22:24:49.856Z",
    "last_updated_on": "1975-02-22T15:35:44.796Z"
  },
  "cardsavr_card": {
    "id": 616130165,
    "bin_id": 523823477,
    "cvv": "DwV",
    "expiration_month": "3",
    "expiration_year": "r",
    "name_on_card": "EqzFNUSXrXGvVfOsuOUVpYsRbooglclRAorgkeqOdYJOwTBOtnmYfeQbnDUTtjGQoQcjzkKrNijmKZbUuYeBytYTPzdCFmsEYOJXFInGLeMZAhJGRAuxnJSvVvarFQDtnwQlUALvtOjXAMcuOEQEgOAvGzAORjELJKxYiRrJIDoITCAtfkvrDPwxVeyIggpTGtfFDlKGOkgJkTSyMwmqwKHlzSlklYugkiPaOWPJXIKNQmrjnTfqLwaijoQBjA",
    "first_6": "kbpIUPAQIZWuCeeWIooKgYXPPoMTtVVd",
    "first_7": "YGfpXDFpZZryYasqdDzurVjecIXXyYzc",
    "first_8": "AYdIaERdsoFYTawzdRUMRObjoviGyhZD",
    "nickname": "lJEYMeighnfhoQxkFYxTutnmsEelfcvViiSsJzRtQZdXZJzMuPSqkgSjSoylDHq",
    "created_on": "2003-03-09T13:47:03.132Z",
    "last_updated_on": "2005-07-06T11:41:59.996Z"
  },
  "cardsavr_account": {
    "id": 493859645,
    "last_card_placed_id": 800683982,
    "primary_account_identifier_hash": "nozlJnQkoWUuYdrIYKENsuzbRovVKkuJLbQYUPEXvaRbEfwpVbXaZfoVDJU",
    "account_identification": {
      "HKAvvwtUYhfq": "O40a(sXw#lt56JOk~pVWcMQ{Sf-hb2z",
      "azfTtOdVBvMV": 26,
      "XlINmtgBwUTj": true
    },
    "last_login": "1992-11-14T12:45:55.785Z",
    "last_password_update": "1972-09-08T23:35:24.982Z",
    "last_saved_card": "2017-03-08T13:46:25.806Z",
    "created_on": "2016-03-20T19:35:47.555Z",
    "last_updated_on": "1982-05-13T03:07:26.889Z"
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/1391070587`

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
  "cardholder_id": 1507173817,
  "card_id": 45509086,
  "account_id": 1793988964,
  "status": "TOO_MANY_LOGIN_FAILURES",
  "custom_data": {
    "wAQfMJYZrwcb": "L",
    "SZwJJNyvbiAD": 41,
    "QlJlZmpTsJND": false
  },
  "notification_sent": false,
  "time_elapsed": 635688588,
  "started_on": "1984-05-29T05:29:30.852Z",
  "completed_on": "1992-10-31T11:42:46.423Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1507173817 },
	{ "card_id", 45509086 },
	{ "account_id", 1793988964 },
	{ "status", "TOO_MANY_LOGIN_FAILURES" },
	{ "notification_sent", false },
	{ "time_elapsed", 635688588 },
	{ "started_on", "1984-05-29T05:29:30.852Z" },
	{ "completed_on", "1992-10-31T11:42:46.423Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1507173817 )
	.add("card_id", 45509086 )
	.add("account_id", 1793988964 )
	.add("status", "TOO_MANY_LOGIN_FAILURES" )
	.add("notification_sent", false )
	.add("time_elapsed", 635688588 )
	.add("started_on", "1984-05-29T05:29:30.852Z" )
	.add("completed_on", "1992-10-31T11:42:46.423Z" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1507173817,\"card_id\":45509086,\"account_id\":1793988964,\"status\":\"TOO_MANY_LOGIN_FAILURES\",\"custom_data\":{\"wAQfMJYZrwcb\":\"L\",\"SZwJJNyvbiAD\":41,\"QlJlZmpTsJND\":false},\"notification_sent\":false,\"time_elapsed\":635688588,\"started_on\":\"1984-05-29T05:29:30.852Z\",\"completed_on\":\"1992-10-31T11:42:46.423Z\"}"
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
  "card_id": 1679793623,
  "status": "INVALID_EXPIRATION_DATE",
  "custom_data": {
    "QJaetGuiqjKJ": "6WU](3lEz4RRP&avU3gBmNs6N",
    "UflIruVHYPCJ": 2,
    "aNEKzjuEHAoG": false
  },
  "notification_sent": false,
  "time_elapsed": 1400051416,
  "started_on": "2017-04-19T11:06:47.766Z",
  "completed_on": "2000-03-26T17:34:20.515Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 1679793623 },
	{ "status", "INVALID_EXPIRATION_DATE" },
	{ "notification_sent", false },
	{ "time_elapsed", 1400051416 },
	{ "started_on", "2017-04-19T11:06:47.766Z" },
	{ "completed_on", "2000-03-26T17:34:20.515Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 1679793623 )
	.add("status", "INVALID_EXPIRATION_DATE" )
	.add("notification_sent", false )
	.add("time_elapsed", 1400051416 )
	.add("started_on", "2017-04-19T11:06:47.766Z" )
	.add("completed_on", "2000-03-26T17:34:20.515Z" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":1679793623,\"status\":\"INVALID_EXPIRATION_DATE\",\"custom_data\":{\"QJaetGuiqjKJ\":\"6WU](3lEz4RRP&avU3gBmNs6N\",\"UflIruVHYPCJ\":2,\"aNEKzjuEHAoG\":false},\"notification_sent\":false,\"time_elapsed\":1400051416,\"started_on\":\"2017-04-19T11:06:47.766Z\",\"completed_on\":\"2000-03-26T17:34:20.515Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1391070587
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/1391070587
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

