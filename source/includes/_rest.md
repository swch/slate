
# Accounts
Account objects contain the account information, such as username and password, for a particular cardhoder. They are used to log in to a cardholder's account for placing a payment card.
## Get account

```javascript
const accounts = await session.getAccounts(130346413,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","merchant_site","cardsavr_card"])});
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
JsonArray response = (JsonArray)session.get(130346413, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 130346413,
  "last_password_update": "1975-11-19T15:01:36.949Z",
  "last_saved_card": "2002-12-05T03:01:56.484Z",
  "created_on": "1979-11-24T06:13:26.238Z",
  "last_updated_on": "2003-08-28T04:45:14.289Z",
  "cardholder": {
    "id": 1176439776,
    "financial_institution_id": 243752557,
    "agent_session_id": "kPEwEry",
    "type": "ephemeral",
    "first_name": "bhUqzvSlBydYSmcgOfNPrtMVTlTlw",
    "last_name": "LltVlYjsIDXGX",
    "email": "TmKnvxwBeEAB@JvzRRc.PLN",
    "meta_key": "dgpwOjQKWPGlgBtCaxwUgPQtO",
    "cardholder_safe_key": "j487AqEyzG/1Yg17il0Fa8FSH7B6NPE7Cm2UPP1ewhQ=",
    "custom_data": {
      "GJsvKGbarplO": "gHWF1",
      "iXRIMLYwSoaX": 98,
      "QcqpCQIBCxYe": false
    },
    "created_on": "2012-01-19T05:25:27.757Z",
    "last_updated_on": "1973-05-30T15:50:14.193Z"
  },
  "merchant_site": {
    "id": 1958759735,
    "name": "QgOEmEJylFNUXUhPKkixD",
    "host": "fZLhZalTIZjyJOJFwtrcMVolascbHuu",
    "tags": [
      "BpGy]-MJN_rTYX!GUh8f+VE}1",
      43,
      "xNLs.W"
    ],
    "queue_name": "vbs_queue",
    "interface_type": "dcs",
    "required_form_fields": [
      "tR0RKC{J(I{iil^Wh+L",
      29,
      "sA"
    ],
    "images": [
      {
        "xcMQaAhAWRqX": "ViNM5HzY^bZC)S/oi",
        "sAeRZuyPWtAz": 68,
        "byoSWoAcTsOV": true
      },
      {
        "GvzQarPSiczG": "ieNB/RKnzo.,P39Bj-.eOmTEQ5%(6u",
        "JyMYmvjYrypu": 84,
        "FAoFkmoMqDHK": false
      },
      {
        "RqJLMpOnXnMX": "DW[6Z1jL2.!Ov}CGzJVunxU7(nE",
        "FgYUSWWyTpGa": 73,
        "zQEgMSGARubd": true
      }
    ],
    "messages": {
      "ZeYHqOHSthgH": "EDLMf*",
      "NHjEpspgqvhA": 69,
      "ombuXGfUIzru": false
    },
    "mfa": false,
    "move_mouse_to_element": false,
    "proxy_order": [
      "=3d*eOif++n8XJWo+p]s@",
      79,
      ",@{%/CKvo$fT"
    ],
    "credit_card_page": "XImlfqbNKNjnJyDrWxMaUzF",
    "forgot_password_page": "lhaXSFfV",
    "quick_start": false,
    "login_page": "XYPOqMlmjngKkVbg",
    "login": {
      "efgToicwxAdg": "*22yTg98-Y",
      "FyKKXKCbejYJ": 60,
      "fYsfdpOlfPLo": false
    }
  },
  "cardsavr_card": {
    "id": 1411661435,
    "bin_id": 1387223582,
    "cvv": "nBa",
    "expiration_month": "6",
    "expiration_year": "m",
    "name_on_card": "PMdnxwnhiaQfKEjBDIwveUFAMhJvcyvnQJxpLvwrhDGzPmdTsLviltFhdCYlhSlAoxpKrbETQrKNlNKOFcCUbFbWMagJcnZuVMhjpHVDRpVTrfnsUcoGRnSeXUUlGPQJLnPcVWOxTsCxWBZzjQWKjofslpzFfSTQgYlILhuIUwNJphuGUiYdjlEyhaPNealHzUBxnvaNBmDHoiMFRKSCRlDbEmzdAOeqqHZxwtHokOwJSXhgdVJKPpJxJQhAtb",
    "first_6": "yNzPAzYHhRmGduVtEdHHBslQOhxxAzil",
    "first_7": "SqsKomfPVtnmZCwZkXqsmonYmXZUyqqe",
    "first_8": "qBElhaRdzCCvFIHiHInSYvnVQmhQlhsE",
    "created_on": "1983-11-17T10:48:44.546Z",
    "last_updated_on": "2018-11-17T07:06:34.071Z"
  },
  "customer_key": "oINYaWXySPOLnABc"
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

**Example GET request path:**<br>`/cardsavr_accounts/130346413`

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
  "cardholder_id": 618159578,
  "merchant_site_id": 504302124,
  "customer_key": "oINYaWXySPOLnABc",
  "last_card_placed_id": 1771768402,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 618159578 },
	{ "merchant_site_id", 504302124 },
	{ "customer_key", "oINYaWXySPOLnABc" },
	{ "last_card_placed_id", 1771768402 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 618159578 )
	.add("merchant_site_id", 504302124 )
	.add("customer_key", "oINYaWXySPOLnABc" )
	.add("last_card_placed_id", 1771768402 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":618159578,\"merchant_site_id\":504302124,\"customer_key\":\"oINYaWXySPOLnABc\",\"last_card_placed_id\":1771768402,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
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
cardholder_id | number | yes
merchant_site_id | number | yes
customer_key | string | yes
last_card_placed_id | number | no
username | string | no
password | string | no
account_identification | object | no

See [account response attributes](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username, password and account_identification when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe user properties.</aside>

## Upsert account

```javascript
const account = await session.updateAccount(1,{
  "last_card_placed_id": 830848591,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 830848591 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 830848591 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":830848591,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/130346413
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
last_card_placed_id | number |
username | string |
password | string |
account_identification | object |

See [account response parameters](#response-cardsavr_account).

<aside class="notice">Update calls to /cardsavr_accounts require the cardholder's personal cardholder_safe_key header to encrypt and save the username, password and account_identification when Strivve does not manage keys for a customer (this is an environment setting). The safe keys are also not required if updating non-safe properties.</aside>

## Delete account

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/130346413
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
const addresses = await session.getAddresses(1092514608,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder"])});
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
JsonArray response = (JsonArray)session.get(1092514608, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1092514608,
  "address1": "SaeCwehgMWaftqEqeCXIEftzjFsjOZWhxyoBICSoHMSdFfLPQLLTHLZqmuAykZLsZsgfeLFmEyUsFiqFhDheuXlfaUlaZqRsMJf",
  "address2": "KbrNoQnGrVvMIUASogPCvWEeSWXmYgDgWLcgLRgHuYtIkseQEIBLssokIcFnWBozIoqoczaKYDWRhrYdFYTJVvGmsDTGwjaVaRg",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "sSIwYLXSnsKb@YjdBal.leT",
  "phone_number": "2065555555",
  "created_on": "1999-03-12T23:05:20.672Z",
  "last_updated_on": "1976-02-14T02:22:29.684Z",
  "cardholder": {
    "id": 1319301224,
    "financial_institution_id": 137076179,
    "agent_session_id": "GyWcwoMFQFjEWEhDmQMPvdSGvb",
    "type": "ephemeral",
    "first_name": "Yogy",
    "last_name": "KVHOEOuccEwasPdYQEzeuU",
    "email": "qjTTGExmawdP@RajKLM.KUe",
    "meta_key": "CkCLH",
    "cardholder_safe_key": "5ofTQvE5nMA+ecktI2LVPe1EqUg/d5imJfB2pob8kZc=",
    "custom_data": {
      "oGaPdRKrmvlG": ".vTzM",
      "cqsScvVYHmti": 64,
      "PTHVvaQDZYMg": false
    },
    "created_on": "1998-05-25T09:14:17.836Z",
    "last_updated_on": "1977-01-02T18:00:52.904Z"
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

**Example GET request path:**<br>`/cardsavr_addresses/1092514608`

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
  "cardholder_id": 1889033846,
  "address1": "SaeCwehgMWaftqEqeCXIEftzjFsjOZWhxyoBICSoHMSdFfLPQLLTHLZqmuAykZLsZsgfeLFmEyUsFiqFhDheuXlfaUlaZqRsMJf",
  "address2": "KbrNoQnGrVvMIUASogPCvWEeSWXmYgDgWLcgLRgHuYtIkseQEIBLssokIcFnWBozIoqoczaKYDWRhrYdFYTJVvGmsDTGwjaVaRg",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "sSIwYLXSnsKb@YjdBal.leT",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1889033846 },
	{ "address1", "SaeCwehgMWaftqEqeCXIEftzjFsjOZWhxyoBICSoHMSdFfLPQLLTHLZqmuAykZLsZsgfeLFmEyUsFiqFhDheuXlfaUlaZqRsMJf" },
	{ "address2", "KbrNoQnGrVvMIUASogPCvWEeSWXmYgDgWLcgLRgHuYtIkseQEIBLssokIcFnWBozIoqoczaKYDWRhrYdFYTJVvGmsDTGwjaVaRg" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "sSIwYLXSnsKb@YjdBal.leT" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1889033846 )
	.add("address1", "SaeCwehgMWaftqEqeCXIEftzjFsjOZWhxyoBICSoHMSdFfLPQLLTHLZqmuAykZLsZsgfeLFmEyUsFiqFhDheuXlfaUlaZqRsMJf" )
	.add("address2", "KbrNoQnGrVvMIUASogPCvWEeSWXmYgDgWLcgLRgHuYtIkseQEIBLssokIcFnWBozIoqoczaKYDWRhrYdFYTJVvGmsDTGwjaVaRg" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "sSIwYLXSnsKb@YjdBal.leT" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1889033846,\"address1\":\"SaeCwehgMWaftqEqeCXIEftzjFsjOZWhxyoBICSoHMSdFfLPQLLTHLZqmuAykZLsZsgfeLFmEyUsFiqFhDheuXlfaUlaZqRsMJf\",\"address2\":\"KbrNoQnGrVvMIUASogPCvWEeSWXmYgDgWLcgLRgHuYtIkseQEIBLssokIcFnWBozIoqoczaKYDWRhrYdFYTJVvGmsDTGwjaVaRg\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"sSIwYLXSnsKb@YjdBal.leT\",\"phone_number\":\"2065555555\"}"
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
cardholder_id | number | yes
address1 | string | yes
address2 | string | no
city | string | yes
subnational | string | yes
postal_code | string | yes
postal_other | string | no
country | [string enum](#post-cardsavr_address-1)* | no
is_primary | boolean | yes
first_name | string | no
last_name | string | no
email | string | no
phone_number | string | no

See [address response attributes](#response-cardsavr_address).

#### <a name="post-cardsavr_address-1"></a>string enum*
- usa
- canada
- Canada
- USA


## Update address

```javascript
const address = await session.updateAddress(1,{
  "address1": "lDrNWjQStPNMdNPAyFMeIxsQKeDrEbaUNRqveVwGipwMsttVukiXBqJJUXcFJfhboxPIQFIBlYKCpXMLLykpVOHRbjYqeodSfny",
  "address2": "wdCxbqfmPwAyWYtcNxRIhuihrMWzSHHgXxILMxYzkisMsfVkcTBCdtaNtiZCthdwiQCcAExnozUmqTgMtDibiPRzOuvJIctJWaW",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "izoKfHSlPLaY@dODtTE.ibm",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "lDrNWjQStPNMdNPAyFMeIxsQKeDrEbaUNRqveVwGipwMsttVukiXBqJJUXcFJfhboxPIQFIBlYKCpXMLLykpVOHRbjYqeodSfny" },
	{ "address2", "wdCxbqfmPwAyWYtcNxRIhuihrMWzSHHgXxILMxYzkisMsfVkcTBCdtaNtiZCthdwiQCcAExnozUmqTgMtDibiPRzOuvJIctJWaW" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "izoKfHSlPLaY@dODtTE.ibm" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "lDrNWjQStPNMdNPAyFMeIxsQKeDrEbaUNRqveVwGipwMsttVukiXBqJJUXcFJfhboxPIQFIBlYKCpXMLLykpVOHRbjYqeodSfny" )
	.add("address2", "wdCxbqfmPwAyWYtcNxRIhuihrMWzSHHgXxILMxYzkisMsfVkcTBCdtaNtiZCthdwiQCcAExnozUmqTgMtDibiPRzOuvJIctJWaW" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "izoKfHSlPLaY@dODtTE.ibm" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"lDrNWjQStPNMdNPAyFMeIxsQKeDrEbaUNRqveVwGipwMsttVukiXBqJJUXcFJfhboxPIQFIBlYKCpXMLLykpVOHRbjYqeodSfny\",\"address2\":\"wdCxbqfmPwAyWYtcNxRIhuihrMWzSHHgXxILMxYzkisMsfVkcTBCdtaNtiZCthdwiQCcAExnozUmqTgMtDibiPRzOuvJIctJWaW\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"izoKfHSlPLaY@dODtTE.ibm\",\"phone_number\":\"2065555555\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1092514608
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
address2 | string |
city | string |
subnational | string |
postal_code | string |
postal_other | string |
country | [string enum](#post-cardsavr_address-1)* |
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1092514608
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
const bins = await session.getBins(909268133,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(909268133, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 909268133,
  "custom_data": {
    "SbxnpUSePsWh": "I*&U}YE)(9!",
    "ijZWMZNbtwVF": 37,
    "ofvOjyUfPRUS": false
  },
  "created_on": "1973-07-09T04:03:50.547Z",
  "last_updated_on": "2007-07-20T01:04:28.112Z",
  "financial_institution": {
    "id": 1829643690,
    "name": "bWbElmjjXdgJxbCnBBUFmeIrpMJpecIiukpJWwCyHKwEcHTazOmKUiQLMKtxiQA",
    "description": "DBc",
    "lookup_key": "awhhnTEYBtPmqNiKBRETALOEaoZDqGdohEzGHuTOPuENPEVxUjDBLoONjLGZcHZ",
    "alternate_lookup_key": "fdwxOZlRoQkSinDBnFDBtMXiWeOyIGpGsGhgPzRwyRVcDeJnwaIYuDGomElmMie",
    "config": {
      "eYifAoNXaArM": "E+QWaUJ!X&E3n6y$/",
      "vjjXpMKhjqSR": 2,
      "ZdinkfgrJSum": false
    },
    "last_activity": "1994-12-31T04:25:52.729Z",
    "created_on": "1975-03-05T03:04:10.524Z",
    "last_updated_on": "2017-11-25T12:20:37.902Z"
  },
  "bank_identification_number": "49420817"
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

**Example GET request path:**<br>`/cardsavr_bins/909268133`

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
  "financial_institution_id": 677688318,
  "bank_identification_number": "49420817",
  "custom_data": {
    "SbxnpUSePsWh": "I*&U}YE)(9!",
    "ijZWMZNbtwVF": 37,
    "ofvOjyUfPRUS": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 677688318 },
	{ "bank_identification_number", "49420817" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 677688318 )
	.add("bank_identification_number", "49420817" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":677688318,\"bank_identification_number\":\"49420817\",\"custom_data\":{\"SbxnpUSePsWh\":\"I*&U}YE)(9!\",\"ijZWMZNbtwVF\":37,\"ofvOjyUfPRUS\":false}}"
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
financial_institution_id | number | yes
bank_identification_number | string | yes
custom_data | object | no

See [bin response attributes](#response-cardsavr_bin).


## Update bin

```javascript
const bin = await session.updateBin(1,{
  "financial_institution_id": 3712013,
  "custom_data": {
    "DLjdHhBzwdEf": "@~^h6I_E{Y_y/X^FHm0V#~W/7iczL",
    "JpjYsDpJWOgQ": 41,
    "itVmFooWFPYK": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 3712013 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 3712013 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":3712013,\"custom_data\":{\"DLjdHhBzwdEf\":\"@~^h6I_E{Y_y/X^FHm0V#~W/7iczL\",\"JpjYsDpJWOgQ\":41,\"itVmFooWFPYK\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/909268133
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
financial_institution_id | number |
custom_data | object |

See [bin response parameters](#response-cardsavr_bin).


## Delete bin

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/909268133
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
const cardplacementresults = await session.getCardPlacementResults(1035380131,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution","merchant_site","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(1035380131, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1035380131,
  "merchant_site_hostname": "sbKhckxZxHCPTFqxnGIDvNUnVQAwzikjKDdbFNcxKderJzWWOpnubNdyXVuxEeIzORbDdKhyvnTDrsodWNFFmgxiqRFCdZBGPtObFvvAgPzRQajNpJUcBDlzDSerInwEUGAnRPSemRbfqprVAzXdtRDNUHLTMjEGTbdodjxQJwbHOHPluwWHHwiRtjiWdNiWJhttUELCBlRIKLeqjlpsFsoMIPwhBMLCDOsQXALqdSHZPYEKEOZQbXvlJubfhQ",
  "meta_key": "MB9810411",
  "fi_name": "MAlaOcpeRarGUrCtBdIzxwGsSXBWoQRdPOeTRLuRJjxSbyppsmlNUdWxaTovQzu",
  "bank_identification_number": "38469792",
  "cuid": "AxqaveaTRYqKIyFhZJrezgxVwDfOcXPBEQkGZhcblkjyyhHWKwwdZYdUSJHZinsrrfHGVQyKXxlMojdmbyDJovKfQLiDIjKPfgMIGYwwIXNoOgpomcSlycBHUerpTRqFAdQVAVVdtFcePbVgPJEvacgfkhzwbcbrOkixVxyISeuxAyZluLJkBRWwNYaniRArHMPUXAnleRQTGUYkhmWweYmHciFYXCqVjtrSxlvyhQJMJJZMDCteBjPvoRczdu",
  "par": "LdhTnNjuqcIYIrqVFxrgNRZEgqzkb",
  "card_customer_key": "jaSExdkCSaWQ",
  "account_customer_key": "CoLfwQFqloRBwOofKAQ",
  "status": "SUCCESSFUL",
  "status_message": "Successful",
  "termination_type": "BILLABLE",
  "custom_data": {
    "MHJTJKbYEWvt": "3_^m(70Xcq#fmK&~v",
    "zomoESINdvid": 24,
    "hwnjQzDLYJMK": true
  },
  "time_elapsed": 1044440771,
  "first_6": "bWyILrXhtgRQfeLRKijEpKQtXggBoMcU",
  "first_7": "GVHWcPSVVtmMQusDlPikVppdZrczeOOl",
  "first_8": "voHHsgNniFylrYQgFLwVZYGHWKWnNzdN",
  "trace": "lCxtgtZytaqEXuQljGCWQQViNWKiXuIcikuRuQIdcKLvzIXdkAJqSdYBkCFhKOAEuGptkDIAcWxPqhwzEkgqGgGiKABaNTsSarIfNYlioDewqeJuEHfshzuiMyLxkocOHuEYacLFTvdQQJFDsrHaiuMJAYgCcgSfzmnmqbvnNOKNVUhyqZElxSwBcBcyhULgLHIxEhaLrcNfwhYcxlmmRAFeSiQLOeDSBHyAHtZcAsZcDkddFRtkLFAMFiRmOb",
  "email_sent": false,
  "completed_on": "1990-11-25T20:57:00.591Z",
  "created_on": "2013-06-27T12:36:58.055Z",
  "last_updated_on": "1970-04-19T03:23:26.219Z",
  "financial_institution": {
    "id": 1341630146,
    "name": "XPuGrwSutqDqHUGDPaVgShFgUIHugfXPSmVupTDRIIoimEQvJFxbXusdtziaFaU",
    "description": "hnwmVDkdzBUuoRywcJPsUZPNoUEp",
    "lookup_key": "rLwuyQEmGXHESVpytzfcAlKImNXgnrYHKmWgNxOHhaoGxbrsBpmuWrhlFeabPSt",
    "alternate_lookup_key": "eqXdfwDKpEZOcQpqXtXOCmaDBccOExCQsYWqAxLOgOEsMLyFShBDvtxTvCwTetm",
    "config": {
      "ZXdlWIXPbnYm": "#8Ge*",
      "CqQODVeCivQx": 10,
      "MshbriXLnGEr": true
    },
    "last_activity": "1983-01-23T21:24:43.759Z",
    "created_on": "1993-11-12T16:05:34.668Z",
    "last_updated_on": "2014-01-25T12:20:27.072Z"
  },
  "merchant_site": {
    "id": 1541370142,
    "name": "kRcOhSPnYbbTUZSS",
    "host": "KNMQVJlhMcpmNgqGaIXA",
    "tags": [
      "#=qG.q.&d/p$1Yko+ZXEAc-WY!LVo",
      24,
      "ZDn$jOhhyShdX,!5JKM%XoKa/L5{"
    ],
    "queue_name": "vbs_queue",
    "interface_type": "dcs",
    "required_form_fields": [
      "s0X(!VJ3wMH67evM}*iG",
      74,
      "N"
    ],
    "images": [
      {
        "oyLCSWqgNsGB": "0D68T",
        "nDcDXlxhTYaL": 9,
        "dzPLnrtFtovM": false
      },
      {
        "beOBrLpqpnFa": "(N{6O7Ia}oq5#r",
        "suFjsTdoZAnX": 13,
        "YArKgmgcZrHS": false
      },
      {
        "RnUowsmbQUtb": "Ir",
        "XezJHtLfrmhQ": 59,
        "adNHinrFxCvl": false
      }
    ],
    "messages": {
      "XgMejFIwEEWJ": "1gkPt8OS&U[88q59-z]fry=L",
      "keqhthOUEnkV": 7,
      "xOcdqpGhhPSH": false
    },
    "mfa": true,
    "move_mouse_to_element": false,
    "proxy_order": [
      "M049k7em1Pg",
      22,
      "tfyvD[}qy}dJG*mcQSs#xkR.rS8"
    ],
    "credit_card_page": "WwGBRPGyGbLgnVoxXqzxCzkqbi",
    "forgot_password_page": "GthCNLZbVfoL",
    "quick_start": false,
    "login_page": "ibcZzClOsblqLpjmAUATMiewhxyNCpO",
    "login": {
      "MMFtChCXMUiN": "NPe_7Z@)",
      "yIQuKPXyIwIe": 18,
      "tgIBjYUHlvAG": true
    }
  },
  "cardsavr_bin": {
    "id": 918972391,
    "financial_institution_id": 1890259231,
    "custom_data": {
      "FavSLznmDGNy": "MOj}+&@V4N!z+",
      "ZbuiQwNUujTC": 86,
      "XtWQpPnOgzBI": false
    },
    "created_on": "1977-10-05T15:17:22.349Z",
    "last_updated_on": "2009-12-14T03:49:46.588Z"
  },
  "place_card_on_single_site_job_id": 992580795
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

**Example GET request path:**<br>`/card_placement_results/1035380131`

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
card_customer_key | string | Unique customer reference for this card. A randome numberr will be generated and returned if not provided
account_customer_key | string | An external reference to a merchant site for a specific cardholder.  A key of merchant host and cuid will be used if none provided. The default can potentially violate a constraint with two accounts of the same merchant site.
status | string | Status of job (when it terminated).
status_message | string | Human readable representation of the job's status.
termination_type | string | Final termination status of a job. (BILLABLE, SITE_INTERACTION_FAILURE, USER_DATA_FAILURE, PROCESS FAILURE)
custom_data | object | 
time_elapsed | number | 
first_6 | string | First six digits of card number.
first_7 | string | First seven digits of card number.
first_8 | string | First eight digits of card number.
trace | string | 
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
const cards = await session.getCards(1129687899,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_address","cardsavr_bin"])});
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
JsonArray response = (JsonArray)session.get(1129687899, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1129687899,
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "created_on": "1978-08-17T13:05:09.379Z",
  "last_updated_on": "1991-03-30T09:50:06.060Z",
  "cardholder": {
    "id": 405998952,
    "financial_institution_id": 990004972,
    "agent_session_id": "iWnUWaZupcmZsgHuGTC",
    "type": "persistent",
    "first_name": "wxVPiTvlcVnhfhwtOdDeScjud",
    "last_name": "ddLaq",
    "email": "GIwkFeHkqhES@ggchzE.zKb",
    "meta_key": "MKxSwivGivHHCYfqSzGGOBW",
    "cardholder_safe_key": "x6gvm3BjPNs91ZYruLnDAvo9cUBHnvA6Rx5ffMG3vs8=",
    "custom_data": {
      "tgdqgiWUHJBt": "8qoMb$3bH@$Vm{uO@=JBD{Qu1@MWluO",
      "cNNMUCgnwgCA": 68,
      "aaGwBrScNXVe": true
    },
    "created_on": "2017-08-31T03:07:25.840Z",
    "last_updated_on": "1986-01-08T07:34:38.765Z"
  },
  "cardsavr_address": {
    "id": 108197813,
    "address1": "SCSLPpBsyajEjegqyxzERtwRZGGbqCRbMKZoaNtiEoXHlXZeDpxWVIexWidYiqRmgRQTnWoCQIolOBwquPrbBxPhKhLwmiiBCEV",
    "address2": "FMqGkToqySouiKAxqSbtGnxNssSACnSxqtDUkvSgvmCiOsnWuQemZukYozCtKsncaZzYKOFtbyQanUBJyIgnruGBxZYJPbqVBfB",
    "city": "wEBUMYNkSssOzKJKZBclpdZoREUYGCMEBCOjbPAPcfTmMOHCBlbTRNTlWykZDYwYAQToRYDhsMqClzDUaqwbnmrmVNBGKZZHgZx",
    "subnational": "GdAralREOQKCUFFYyHppPDQipmtrwMbLNBtRlokrOEpKZBUPlnkUaLGGhsPPses",
    "postal_code": "PEKRlxglthZWRTsArnZqNysjgqEfOGj",
    "postal_other": "FyMlemyNjJbGvElSHrmlCwJqCvjwTAh",
    "country": "USA",
    "is_primary": true,
    "first_name": "AVOYpRSPXWKABjVQfdUfskWFtjLcklio",
    "last_name": "BeNjsQn",
    "email": "XODHlrEogsKj@cALkXA.Hid",
    "phone_number": "fQIPWHGrnBn",
    "created_on": "1978-05-22T04:28:03.357Z",
    "last_updated_on": "1990-06-02T07:59:46.832Z"
  },
  "cardsavr_bin": {
    "id": 593297938,
    "financial_institution_id": 2145535709,
    "custom_data": {
      "dUlrMeSSnrzw": "E-[1@PE#}80M",
      "IoYVuOafpZUo": 84,
      "rzhqTrtlJMCH": false
    },
    "created_on": "2014-10-15T02:50:34.886Z",
    "last_updated_on": "1972-05-20T09:02:17.144Z"
  },
  "par": "joSgBuncwyjIPcAeRdNbpFnyWVUoM",
  "customer_key": "sCneWAXhcacrsE"
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
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/cardsavr_cards?ids=1,2`

#### Singular GET requests

**Singular requests** only return the card matching the id provided in the path.

**Example GET request path:**<br>`/cardsavr_cards/1129687899`

### <a name="response-cardsavr_card"></a>Response attributes

Attribute | Type | Description
------ | ---- | -----------
id | number (pk) | Unique ID of this card.
bin_id | number (fk) [bins](#bins) | ID of BIN associated with this card.
expiration_month | string | 
expiration_year | string | 
name_on_card | string | 
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
cardholder_id | number (fk) [cardholders](#cardholders) | ID of cardholder associated with this card.
address_id | number (fk) [addresses](#addresses) | ID of address associated with this card.
par | string | Unique Personal Account Reference number for this card, to be used for card lookup. Generated automatically from PAN, expiration date, and username if using the SDK.
customer_key | string | Unique customer reference for this card. A randome numberr will be generated and returned if not provided

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create card

```javascript
const card = await session.createCard({
  "cardholder_id": 1975082559,
  "address_id": 662784683,
  "bin_id": 552110061,
  "par": "joSgBuncwyjIPcAeRdNbpFnyWVUoM",
  "customer_key": "sCneWAXhcacrsE",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1975082559 },
	{ "address_id", 662784683 },
	{ "bin_id", 552110061 },
	{ "par", "joSgBuncwyjIPcAeRdNbpFnyWVUoM" },
	{ "customer_key", "sCneWAXhcacrsE" },
	{ "pan", "4111111111111111" },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Jane Smith" }
};

CardSavrResponse<Card> card = await http.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1975082559 )
	.add("address_id", 662784683 )
	.add("bin_id", 552110061 )
	.add("par", "joSgBuncwyjIPcAeRdNbpFnyWVUoM" )
	.add("customer_key", "sCneWAXhcacrsE" )
	.add("pan", "4111111111111111" )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Jane Smith" )
	.build();
JsonValue card = session.post("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1975082559,\"address_id\":662784683,\"bin_id\":552110061,\"par\":\"joSgBuncwyjIPcAeRdNbpFnyWVUoM\",\"customer_key\":\"sCneWAXhcacrsE\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\"}"
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
cardholder_id | number | yes
address_id | number | no
bin_id | number | no
par | string | no
customer_key | string | yes
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
  "bin_id": 742926834,
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Jane Smith",
  "pan": "4111111111111111"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "bin_id", 742926834 },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Jane Smith" },
	{ "pan", "4111111111111111" }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("bin_id", 742926834 )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Jane Smith" )
	.add("pan", "4111111111111111" )
	.build();
JsonValue card = session.put("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"bin_id\":742926834,\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Jane Smith\",\"pan\":\"4111111111111111\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1129687899
```

### Path

PUT /cardsavr_cards OR /cardsavr_cards/{id}

### Description

Upsert can be used to either update a card, create a new card, or return an existing card.  Either an id or PAR is required for upsert. The id (in path or body), along with an updated body, can be used to update an existing card; the PAR (in body) can likewise be used to update a card, and can also be used to create a new card, if the PAR does not match any existing cards. If the id or PAR provided corresponds to a pre-existing card and no updated information has been included in the body, the existing card will be returned.



### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/1129687899
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
const cardholders = await session.getCardholders(521369311,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(521369311, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 521369311,
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "jDu",
  "custom_data": {
    "fNanymSKkXLJ": "l=pMY{wqQPPV,AmfkMKPv.25/Rpq&-",
    "SOWFTjrRUzcv": 55,
    "hVXzaPGSnAnc": false
  },
  "created_on": "2017-10-10T11:26:26.045Z",
  "last_updated_on": "2011-01-06T15:05:35.122Z",
  "cuid": "OShPgZfsJIXOazh",
  "financial_institution": {
    "id": 2034135370,
    "name": "CzwFDwXRMopWhKIgAUDKozDfsgUOywtduBTQtNhQSResEzzCsUVroZkyYyQQYFQ",
    "description": "lmfcEUDXJDgXwqLRJCgHxSvMOkq",
    "lookup_key": "dsCXATQAFpXYBGyNRlAjHwwSBzdFmGlFtBeMIrBPpGTNnzfvRYIQeYFxuAuaqCN",
    "alternate_lookup_key": "SKiScUpwkFEtUDlBpBbOIeATSFkKYiHNSGxWyAdfnWtuidMDRNogvLUVGDZWLFL",
    "config": {
      "yojOzlxoDAEK": "]9ek{nl8Atd!Wl~=__7Qry3VW0nV+Pj4",
      "mEXrjHTvmoss": 31,
      "SNImACtDqbKi": true
    },
    "last_activity": "2008-08-18T05:07:25.664Z",
    "created_on": "1977-06-01T17:47:06.048Z",
    "last_updated_on": "2009-08-29T23:19:54.412Z"
  }
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

**Example GET request path:**<br>`/cardholders/521369311`

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
  "cuid": "OShPgZfsJIXOazh",
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "jDu",
  "custom_data": {
    "fNanymSKkXLJ": "l=pMY{wqQPPV,AmfkMKPv.25/Rpq&-",
    "SOWFTjrRUzcv": 55,
    "hVXzaPGSnAnc": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cuid", "OShPgZfsJIXOazh" },
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "jDu" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cuid", "OShPgZfsJIXOazh" )
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "jDu" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"cuid\":\"OShPgZfsJIXOazh\",\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"jDu\",\"custom_data\":{\"fNanymSKkXLJ\":\"l=pMY{wqQPPV,AmfkMKPv.25/Rpq&-\",\"SOWFTjrRUzcv\":55,\"hVXzaPGSnAnc\":false}}"
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
  "first_name": "Jane",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "IvPeEuClPwiNLhuao",
  "custom_data": {
    "JfqEwFNbNnHb": ")t),L#YmKXjhq@hr)*b^iQl_a",
    "dgRVWGLhVDMb": 19,
    "LxbNdUmRPDnG": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "first_name", "Jane" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "IvPeEuClPwiNLhuao" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("first_name", "Jane" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "IvPeEuClPwiNLhuao" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"first_name\":\"Jane\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"IvPeEuClPwiNLhuao\",\"custom_data\":{\"JfqEwFNbNnHb\":\")t),L#YmKXjhq@hr)*b^iQl_a\",\"dgRVWGLhVDMb\":19,\"LxbNdUmRPDnG\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/521369311
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
meta_key | string |
custom_data | object |

See [cardholder response parameters](#response-cardholder).


## Delete cardholder

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/521369311
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
const users = await session.getUsers(2074811648,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(2074811648, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2074811648,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1987-01-28T14:37:58.532Z",
  "is_locked": true,
  "password_lifetime": 21,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "swch_agent",
  "next_rotation_on": "1999-05-19T20:12:20.987Z",
  "created_on": "1997-08-12T22:33:23.683Z",
  "last_updated_on": "1983-12-09T03:49:31.639Z",
  "financial_institution": {
    "id": 1572852238,
    "name": "xUYzeUKoWPkhAbuVFTyOzyUsUSmfWTQqeOTlBcxtezFfdfUxwfLYdmpSUtZvXyU",
    "description": "zbNbuskRZT",
    "lookup_key": "QfGJCPuTAQSibtOBGofzNvFKnnCEWWwnqbVGGJbohLXlPPXazVymGHzAFiPCPsS",
    "alternate_lookup_key": "JniogFZveBDxmlLwMeOvmQMuEVWevTJMLHuaQsaPNRcWAkcOpmPwQOrnYxhwIdo",
    "config": {
      "sgZpgYQmuIOs": "O",
      "rqhSmXoFrnly": 30,
      "GOyTHeInMskC": false
    },
    "last_activity": "2014-09-01T21:53:00.984Z",
    "created_on": "1990-04-07T14:59:37.371Z",
    "last_updated_on": "2000-04-14T12:39:11.151Z"
  },
  "username": "jsmith123"
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

**Example GET request path:**<br>`/cardsavr_users/2074811648`

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
role | string | <p>User role (cardholder_agent or customer_agent) determines the user's ability to access certain endpoints and perform certain operations within the CardSavr API.</p><p>cardholder_agents can create cardholders, create cards addresses for those cardholders, create accounts for those cardholders, and post jobs for those cardholders.</p>customer_agents can peform all actions on cardholders/accounts/, but are limited to acting on cardholders/jobs/accounts/cards within their FI (unless they are assigned to the admin FI)
next_rotation_on | date | Date of next password rotation for this user.
created_on | date | Date this site was created on
last_updated_on | date | Date this site was last updated on
username | string | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

## Create user

```javascript
const user = await session.createUser({
  "financial_institution_id": 75424711,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 21,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "swch_agent",
  "next_rotation_on": "1999-05-19T20:12:20.987Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 75424711 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 21 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "swch_agent" },
	{ "next_rotation_on", "1999-05-19T20:12:20.987Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 75424711 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 21 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "swch_agent" )
	.add("next_rotation_on", "1999-05-19T20:12:20.987Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":75424711,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":21,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"swch_agent\",\"next_rotation_on\":\"1999-05-19T20:12:20.987Z\"}"
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
  "financial_institution_id": 1745390704,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 15,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "cardholder_agent",
  "next_rotation_on": "2019-09-25T17:18:18.834Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1745390704 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 15 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "cardholder_agent" },
	{ "next_rotation_on", "2019-09-25T17:18:18.834Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1745390704 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 15 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "cardholder_agent" )
	.add("next_rotation_on", "2019-09-25T17:18:18.834Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1745390704,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":15,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"cardholder_agent\",\"next_rotation_on\":\"2019-09-25T17:18:18.834Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/2074811648
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/2074811648
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
const financialinstitutions = await session.getFinancialInstitutions(2010472115,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(2010472115, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2010472115,
  "name": "CwJbBpAHobjniMYIpzqfXgyBJcoDoOvWEyTYCqPXlIshmRsAWwqaREAcXrwtocp",
  "description": "OF",
  "lookup_key": "zSFkjBEmNgpiWomQlCuxCSWuKiEAcMeEgEFZGUKhdOswsmYbkWRgNlvploLylfw",
  "alternate_lookup_key": "tvnvSmySLzdfMNhnSlciwqVGTbJBIEmjfizzwrdKwGeBDJXVCiTEhbYMKsIbEET",
  "last_activity": "1977-03-23T01:07:49.021Z",
  "created_on": "2013-07-19T19:54:25.902Z",
  "last_updated_on": "2019-12-14T00:08:45.874Z"
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
- names
- lookup_key
- alternate_lookup_key
- last_activity_min / last_activity_max
- created_on_min / created_on_max
- last_updated_on_min / last_updated_on_max

**Example batch GET request path:**<br>`/financial_institutions?ids=1,2`

#### Singular GET requests

**Singular requests** only return the financial institution matching the id provided in the path.

**Example GET request path:**<br>`/financial_institutions/2010472115`

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
  "name": "CwJbBpAHobjniMYIpzqfXgyBJcoDoOvWEyTYCqPXlIshmRsAWwqaREAcXrwtocp",
  "description": "OF",
  "lookup_key": "zSFkjBEmNgpiWomQlCuxCSWuKiEAcMeEgEFZGUKhdOswsmYbkWRgNlvploLylfw",
  "alternate_lookup_key": "tvnvSmySLzdfMNhnSlciwqVGTbJBIEmjfizzwrdKwGeBDJXVCiTEhbYMKsIbEET"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "CwJbBpAHobjniMYIpzqfXgyBJcoDoOvWEyTYCqPXlIshmRsAWwqaREAcXrwtocp" },
	{ "description", "OF" },
	{ "lookup_key", "zSFkjBEmNgpiWomQlCuxCSWuKiEAcMeEgEFZGUKhdOswsmYbkWRgNlvploLylfw" },
	{ "alternate_lookup_key", "tvnvSmySLzdfMNhnSlciwqVGTbJBIEmjfizzwrdKwGeBDJXVCiTEhbYMKsIbEET" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "CwJbBpAHobjniMYIpzqfXgyBJcoDoOvWEyTYCqPXlIshmRsAWwqaREAcXrwtocp" )
	.add("description", "OF" )
	.add("lookup_key", "zSFkjBEmNgpiWomQlCuxCSWuKiEAcMeEgEFZGUKhdOswsmYbkWRgNlvploLylfw" )
	.add("alternate_lookup_key", "tvnvSmySLzdfMNhnSlciwqVGTbJBIEmjfizzwrdKwGeBDJXVCiTEhbYMKsIbEET" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"CwJbBpAHobjniMYIpzqfXgyBJcoDoOvWEyTYCqPXlIshmRsAWwqaREAcXrwtocp\",\"description\":\"OF\",\"lookup_key\":\"zSFkjBEmNgpiWomQlCuxCSWuKiEAcMeEgEFZGUKhdOswsmYbkWRgNlvploLylfw\",\"alternate_lookup_key\":\"tvnvSmySLzdfMNhnSlciwqVGTbJBIEmjfizzwrdKwGeBDJXVCiTEhbYMKsIbEET\"}"
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
name | string | yes
description | string | no
lookup_key | string | yes
alternate_lookup_key | string | no

See [financial institution response attributes](#response-financial_institution).


## Update financial institution

```javascript
const financialinstitution = await session.updateFinancialInstitution(1,{
  "name": "YWiEAVFhqzeLvgIFtJsSkmPDlUUjPsxfoVNJLJvqZYofHJzNZJawLcMrIpMyyRD",
  "description": "RbDaQjmspzGuSxrhU",
  "lookup_key": "gPFgmEqwnCasnhDyizIUWEiGdaCKFWDoAaOKyBkBjfeVlUdVCUqerXpondnKbMe",
  "alternate_lookup_key": "qwIWpntkVixysvuvbLVfGmLWsdvnXPvZIuychDdJqwfjHdeLxBupSbAemJzYrJu"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "YWiEAVFhqzeLvgIFtJsSkmPDlUUjPsxfoVNJLJvqZYofHJzNZJawLcMrIpMyyRD" },
	{ "description", "RbDaQjmspzGuSxrhU" },
	{ "lookup_key", "gPFgmEqwnCasnhDyizIUWEiGdaCKFWDoAaOKyBkBjfeVlUdVCUqerXpondnKbMe" },
	{ "alternate_lookup_key", "qwIWpntkVixysvuvbLVfGmLWsdvnXPvZIuychDdJqwfjHdeLxBupSbAemJzYrJu" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "YWiEAVFhqzeLvgIFtJsSkmPDlUUjPsxfoVNJLJvqZYofHJzNZJawLcMrIpMyyRD" )
	.add("description", "RbDaQjmspzGuSxrhU" )
	.add("lookup_key", "gPFgmEqwnCasnhDyizIUWEiGdaCKFWDoAaOKyBkBjfeVlUdVCUqerXpondnKbMe" )
	.add("alternate_lookup_key", "qwIWpntkVixysvuvbLVfGmLWsdvnXPvZIuychDdJqwfjHdeLxBupSbAemJzYrJu" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"YWiEAVFhqzeLvgIFtJsSkmPDlUUjPsxfoVNJLJvqZYofHJzNZJawLcMrIpMyyRD\",\"description\":\"RbDaQjmspzGuSxrhU\",\"lookup_key\":\"gPFgmEqwnCasnhDyizIUWEiGdaCKFWDoAaOKyBkBjfeVlUdVCUqerXpondnKbMe\",\"alternate_lookup_key\":\"qwIWpntkVixysvuvbLVfGmLWsdvnXPvZIuychDdJqwfjHdeLxBupSbAemJzYrJu\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/2010472115
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
lookup_key | string |
alternate_lookup_key | string |

See [financial institution response parameters](#response-financial_institution).


## Delete financial institution

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/2010472115
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
const integrators = await session.getIntegrators(1122980868,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(1122980868, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1122980868,
  "name": "YCbfRiBFIhRPtsVujQdmVmuoGswjdDSBZfGRfKgjjtSOiqZXb",
  "description": "nagQAFghdudHWgZuTOCIrUBG",
  "current_key": "szU6qZMjPMBu0FTBYJVc9+6RcnAcLrWsj355y+blZQs=",
  "key_lifetime": 336,
  "next_rotation_on": "2001-11-17T01:48:46.001Z",
  "created_on": "2007-09-27T17:00:27.018Z",
  "last_updated_on": "1995-10-08T14:20:46.522Z"
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

**Example GET request path:**<br>`/integrators/1122980868`

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
  "name": "YCbfRiBFIhRPtsVujQdmVmuoGswjdDSBZfGRfKgjjtSOiqZXb",
  "description": "nagQAFghdudHWgZuTOCIrUBG",
  "current_key": "szU6qZMjPMBu0FTBYJVc9+6RcnAcLrWsj355y+blZQs=",
  "key_lifetime": 336,
  "next_rotation_on": "2001-11-17T01:48:46.001Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "YCbfRiBFIhRPtsVujQdmVmuoGswjdDSBZfGRfKgjjtSOiqZXb" },
	{ "description", "nagQAFghdudHWgZuTOCIrUBG" },
	{ "current_key", "szU6qZMjPMBu0FTBYJVc9+6RcnAcLrWsj355y+blZQs=" },
	{ "key_lifetime", 336 },
	{ "next_rotation_on", "2001-11-17T01:48:46.001Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "YCbfRiBFIhRPtsVujQdmVmuoGswjdDSBZfGRfKgjjtSOiqZXb" )
	.add("description", "nagQAFghdudHWgZuTOCIrUBG" )
	.add("current_key", "szU6qZMjPMBu0FTBYJVc9+6RcnAcLrWsj355y+blZQs=" )
	.add("key_lifetime", 336 )
	.add("next_rotation_on", "2001-11-17T01:48:46.001Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"YCbfRiBFIhRPtsVujQdmVmuoGswjdDSBZfGRfKgjjtSOiqZXb\",\"description\":\"nagQAFghdudHWgZuTOCIrUBG\",\"current_key\":\"szU6qZMjPMBu0FTBYJVc9+6RcnAcLrWsj355y+blZQs=\",\"key_lifetime\":336,\"next_rotation_on\":\"2001-11-17T01:48:46.001Z\"}"
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
name | string | yes
description | string | no
current_key | string | no
key_lifetime | number | no
next_rotation_on | date | no

See [integrator response attributes](#response-integrator).


## Update integrator

```javascript
const integrator = await session.updateIntegrator(1,{
  "name": "hVGzSPmKJVKyKNlpyZGQBczyzvlANInyoAaOcpPXZjVbjRFBL",
  "description": "PQvZbaJyUClcAfZfDKJwlGqQC",
  "current_key": "lXdIzSdkaYt+D/Qt4nQWY5BWE7ZaWthxkMee/4aorrc=",
  "key_lifetime": 100,
  "next_rotation_on": "1976-09-16T07:27:35.662Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "hVGzSPmKJVKyKNlpyZGQBczyzvlANInyoAaOcpPXZjVbjRFBL" },
	{ "description", "PQvZbaJyUClcAfZfDKJwlGqQC" },
	{ "current_key", "lXdIzSdkaYt+D/Qt4nQWY5BWE7ZaWthxkMee/4aorrc=" },
	{ "key_lifetime", 100 },
	{ "next_rotation_on", "1976-09-16T07:27:35.662Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "hVGzSPmKJVKyKNlpyZGQBczyzvlANInyoAaOcpPXZjVbjRFBL" )
	.add("description", "PQvZbaJyUClcAfZfDKJwlGqQC" )
	.add("current_key", "lXdIzSdkaYt+D/Qt4nQWY5BWE7ZaWthxkMee/4aorrc=" )
	.add("key_lifetime", 100 )
	.add("next_rotation_on", "1976-09-16T07:27:35.662Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"hVGzSPmKJVKyKNlpyZGQBczyzvlANInyoAaOcpPXZjVbjRFBL\",\"description\":\"PQvZbaJyUClcAfZfDKJwlGqQC\",\"current_key\":\"lXdIzSdkaYt+D/Qt4nQWY5BWE7ZaWthxkMee/4aorrc=\",\"key_lifetime\":100,\"next_rotation_on\":\"1976-09-16T07:27:35.662Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/1122980868
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
https://api.INSTANCE.cardsavr.io/integrators/1122980868
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
const merchantsites = await session.getMerchantSites(809469392,{"sort":"id","is_descending":true,"page":1, "page_length":25,);
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
JsonArray response = (JsonArray)session.get(809469392, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 809469392,
  "name": "Amazon",
  "host": "amazon.com",
  "tags": [
    "^",
    49,
    "1wk_0snx4%Ejoln}D!$9%VD9z=ocr42"
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
  "mfa": true,
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

### SDK Usage
 Please visit the <a href="https://github.com/swch/Strivve-SDK">javascript</a>, <a href="https://github.com/swch/metro_sdk_c_sharp">c sharp</a>, and <a href="https://github.com/swch/strivve-sdk-java">java</a> SDKs for further examples and information on SDK usage.

#### Batch GET requests

**Batch requests** return the first page of all viewable merchant sites, filtered by any [query filters](#get-filters) (see list of possible parameters below) listed in the path.


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

**Example batch GET request path:**<br>`/merchant_sites?ids=1,2`

#### Singular GET requests

**Singular requests** only return the merchant site matching the id provided in the path.

**Example GET request path:**<br>`/merchant_sites/809469392`

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
mfa | boolean | Indicates if this site is MFA-enabled.
credit_card_page | string | Merchant's credit card entry page.
forgot_password_page | string | Merchant's forgotten password page.
login_page | string | URL of login page.
login | object | 

NOTE: All foreign key parameters (fk) can be [hydrated](#hydration) and support [cascading delete](#cascading-delete).

# Notifications
Notification objects define a set of actions to be triggered by certain CardSavr events, such as session completion.
## Get notification

```javascript
const notifications = await session.getNotifications(313477366,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["financial_institution"])});
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
JsonArray response = (JsonArray)session.get(313477366, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 313477366,
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
  "html_template": "o",
  "text_template": "qc",
  "created_on": "2001-04-01T22:05:35.358Z",
  "last_updated_on": "2003-01-31T02:59:40.109Z",
  "financial_institution": {
    "id": 496572043,
    "name": "dagzEiHVEqxCsSSgFxSIfEFSQurjqOPfGjXFQrWpzWwMWoaBPhwNiiPjwLGEtKy",
    "description": "QPqmGjskRblJnSMskqMCZnF",
    "lookup_key": "QDcZkuVtdUKQkkmFVVgOMdstwoqjNOFIahxhSGHFskrFaOCQDmrjdCedQXlwcPE",
    "alternate_lookup_key": "isfVPndPJlsAllivgdIvunwRmIUlvkAeQMgUopDJoUyrmltetuicMLUzDVlkVKq",
    "config": {
      "evIbFRfOXIVu": "/",
      "ExHwzSNfjqIr": 73,
      "gYeGVgENMTIp": true
    },
    "last_activity": "1971-06-15T07:12:47.958Z",
    "created_on": "1971-08-17T14:20:14.709Z",
    "last_updated_on": "2012-04-02T15:27:59.757Z"
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

**Example GET request path:**<br>`/notifications/313477366`

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
  "financial_institution_id": 802627531,
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
  "html_template": "o",
  "text_template": "qc"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 802627531 },
	{ "name", "Sample Notification" },
	{ "type", "email" },
	{ "event", "webhook_error_summary" },
	{ "html_template", "o" },
	{ "text_template", "qc" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 802627531 )
	.add("name", "Sample Notification" )
	.add("type", "email" )
	.add("event", "webhook_error_summary" )
	.add("html_template", "o" )
	.add("text_template", "qc" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":802627531,\"name\":\"Sample Notification\",\"type\":\"email\",\"event\":\"webhook_error_summary\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"o\",\"text_template\":\"qc\"}"
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
  "html_template": "WkWhyLZRaIkBcxcfqBsnrytbchEhwSZi",
  "text_template": "HfOHsEunIqFxSOkxMa"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "Sample Notification" },
	{ "type", "webhook" },
	{ "event", "session_complete" },
	{ "html_template", "WkWhyLZRaIkBcxcfqBsnrytbchEhwSZi" },
	{ "text_template", "HfOHsEunIqFxSOkxMa" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "Sample Notification" )
	.add("type", "webhook" )
	.add("event", "session_complete" )
	.add("html_template", "WkWhyLZRaIkBcxcfqBsnrytbchEhwSZi" )
	.add("text_template", "HfOHsEunIqFxSOkxMa" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"Sample Notification\",\"type\":\"webhook\",\"event\":\"session_complete\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"WkWhyLZRaIkBcxcfqBsnrytbchEhwSZi\",\"text_template\":\"HfOHsEunIqFxSOkxMa\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/313477366
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
https://api.INSTANCE.cardsavr.io/notifications/313477366
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
const notificationresults = await session.getNotificationResults(2018643232,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["notification"])});
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
JsonArray response = (JsonArray)session.get(2018643232, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2018643232,
  "last_attempt_date": "1984-07-22T05:09:55.501Z",
  "fi_lookup_key": "mQHQWrMOmytkoYpCCFuqkUNVXAqowWaTTwojeUHtrmhPmtlFGDnuBRhJqXsdCJU",
  "cuid": "QzM",
  "status": "success",
  "attempts": 2138816492,
  "notification_data": {
    "vQpmYFKGqeuG": "crY9@h4UTxL3L",
    "shqtsRBwsjRz": 27,
    "KNuWYQOAuqoW": false
  },
  "created_on": "1986-04-23T08:10:05.215Z",
  "last_updated_on": "2017-06-07T17:24:48.820Z",
  "notification": {
    "id": 777780747,
    "name": "GDmkQMKaZaJMLetUOqaWEFWqxrtyeVXznaceKguUUqPMEzVQXgYROtydkqRqHRe",
    "type": "webhook",
    "event": "merchant_site_updates_all",
    "config": {
      "LCzinXZLzDor": "J0D&din,F]q87p%l)Eow",
      "dqdHqGNPemOa": 28,
      "jSXJyBFVDmcv": false
    },
    "html_template": "CMXcUONUTUGgYYGOn",
    "text_template": "NfsGRrgbfNY",
    "created_on": "2011-02-19T18:31:59.854Z",
    "last_updated_on": "1975-02-24T03:09:47.424Z"
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

**Example GET request path:**<br>`/notification_results/2018643232`

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
  "notification_id": 702597743,
  "fi_lookup_key": "mQHQWrMOmytkoYpCCFuqkUNVXAqowWaTTwojeUHtrmhPmtlFGDnuBRhJqXsdCJU",
  "cuid": "QzM",
  "status": "success",
  "attempts": 2138816492,
  "notification_data": {
    "vQpmYFKGqeuG": "crY9@h4UTxL3L",
    "shqtsRBwsjRz": 27,
    "KNuWYQOAuqoW": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 702597743 },
	{ "fi_lookup_key", "mQHQWrMOmytkoYpCCFuqkUNVXAqowWaTTwojeUHtrmhPmtlFGDnuBRhJqXsdCJU" },
	{ "cuid", "QzM" },
	{ "status", "success" },
	{ "attempts", 2138816492 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 702597743 )
	.add("fi_lookup_key", "mQHQWrMOmytkoYpCCFuqkUNVXAqowWaTTwojeUHtrmhPmtlFGDnuBRhJqXsdCJU" )
	.add("cuid", "QzM" )
	.add("status", "success" )
	.add("attempts", 2138816492 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":702597743,\"fi_lookup_key\":\"mQHQWrMOmytkoYpCCFuqkUNVXAqowWaTTwojeUHtrmhPmtlFGDnuBRhJqXsdCJU\",\"cuid\":\"QzM\",\"status\":\"success\",\"attempts\":2138816492,\"notification_data\":{\"vQpmYFKGqeuG\":\"crY9@h4UTxL3L\",\"shqtsRBwsjRz\":27,\"KNuWYQOAuqoW\":false}}"
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

```javascript
const singlesitejobs = await session.getSingleSiteJobs(900535953,{"sort":"id","is_descending":true,"page":1, "page_length":25,{'x-cardsavr-hydration':JSON.stringify(["cardholder","cardsavr_card","cardsavr_account","credential_requests"])});
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
JsonArray response = (JsonArray)session.get(900535953, null, headers);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 900535953,
  "status": "IN_PROGRESS",
  "status_message": "O",
  "termination_type": "BIILLABLE",
  "custom_data": {
    "gqCnLQAdzgUy": "p*5*Nt0wC^Y#XXR2fD",
    "JwGJbJtGzdnM": 61,
    "CAqKalIIEpFC": true
  },
  "notification_sent": true,
  "time_elapsed": 101025524,
  "started_on": "1972-11-03T16:19:40.730Z",
  "completed_on": "1984-10-01T08:23:08.950Z",
  "created_on": "2010-07-21T20:20:05.630Z",
  "last_updated_on": "1999-11-06T03:23:24.494Z",
  "cardholder": {
    "id": 1592736849,
    "financial_institution_id": 2062877064,
    "agent_session_id": "NxewPpJlgOxYbYvzJgQcpFUkWGJ",
    "type": "persistent",
    "first_name": "OZdjB",
    "last_name": "qRfbWSxGGvpNgmt",
    "email": "HSqbUPiIKrZT@vtFYkj.vzZ",
    "meta_key": "CYitBxwtqMCXOirY",
    "cardholder_safe_key": "XZH5D71cEV+25yjDczsakH0TuM1RsjyBnJoEsWL3PjY=",
    "custom_data": {
      "QQxDolGaqnal": "@QJqddw_M!/!U7oOegBH!Xw!o(hx",
      "CHYQeLwfaPXM": 41,
      "gLzwIodsIFNU": false
    },
    "created_on": "1986-01-12T20:47:00.285Z",
    "last_updated_on": "1997-02-11T02:27:52.592Z"
  },
  "cardsavr_card": {
    "id": 1821865492,
    "bin_id": 1213272017,
    "cvv": "cgu",
    "expiration_month": "4",
    "expiration_year": "v",
    "name_on_card": "RuzRDajZcyLFyceHdSgeyWgMXrdYdxoAfltDZEBQbskbtAahKSCGNnvPEUPVwlTqvcJdIicALayMqxyVgzzhlzlWPoOpSLHawXeVtjzBhEwPZuvmMKuJRAisZhGvQleqOzUyainVNOxNbIdwjfqiIvBRYkMJATHeNirmKsQYqqawdXJdqvbmULHOncPjFRPBhOhcJBArkdXraTcVwRrkIiYZfxLwKpqaCdWbPzObdBhmmqxCpIgxTHvwbTiIoo",
    "first_6": "ZcAJKtJVfXOHVQbhMhxLJnnkakKgqdMT",
    "first_7": "uhUUssDLFpWMBUQgeKkshGxQKZzhdZWx",
    "first_8": "LICOSUjAHHMGfoyIKLnolFXXrrKjWMIw",
    "created_on": "1998-11-06T14:08:12.778Z",
    "last_updated_on": "2015-04-20T21:54:26.656Z"
  },
  "cardsavr_account": {
    "id": 394184581,
    "last_card_placed_id": 1452404321,
    "username": "zSjqfnjQpPOTAfguuiirOjLPRTpsCmCAHWaIsiIuaUtsHCqWjXcbabgfViD",
    "username_hash": "zCzCapEBaNYHPcvWaUSJTQgINteTKlQKXSbxdxfqOOuHZGBhEIKwZnZudUK",
    "password": "APgqtINLFxUjiZLVMNIZXeHEktJpaiDLQsIULqZnQFvoPVmVaWypRAhRApy",
    "last_login": "1981-01-26T06:43:44.170Z",
    "last_password_update": "2017-04-11T20:21:21.100Z",
    "last_saved_card": "2009-10-14T23:19:43.543Z",
    "created_on": "1974-07-13T17:01:46.661Z",
    "last_updated_on": "2020-05-01T22:54:01.764Z"
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/900535953`

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
  "cardholder_id": 1230908474,
  "card_id": 332984677,
  "account_id": 1033441235,
  "status": "IN_PROGRESS",
  "custom_data": {
    "gqCnLQAdzgUy": "p*5*Nt0wC^Y#XXR2fD",
    "JwGJbJtGzdnM": 61,
    "CAqKalIIEpFC": true
  },
  "notification_sent": true,
  "time_elapsed": 101025524,
  "started_on": "1972-11-03T16:19:40.730Z",
  "completed_on": "1984-10-01T08:23:08.950Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1230908474 },
	{ "card_id", 332984677 },
	{ "account_id", 1033441235 },
	{ "status", "IN_PROGRESS" },
	{ "notification_sent", true },
	{ "time_elapsed", 101025524 },
	{ "started_on", "1972-11-03T16:19:40.730Z" },
	{ "completed_on", "1984-10-01T08:23:08.950Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1230908474 )
	.add("card_id", 332984677 )
	.add("account_id", 1033441235 )
	.add("status", "IN_PROGRESS" )
	.add("notification_sent", true )
	.add("time_elapsed", 101025524 )
	.add("started_on", "1972-11-03T16:19:40.730Z" )
	.add("completed_on", "1984-10-01T08:23:08.950Z" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1230908474,\"card_id\":332984677,\"account_id\":1033441235,\"status\":\"IN_PROGRESS\",\"custom_data\":{\"gqCnLQAdzgUy\":\"p*5*Nt0wC^Y#XXR2fD\",\"JwGJbJtGzdnM\":61,\"CAqKalIIEpFC\":true},\"notification_sent\":true,\"time_elapsed\":101025524,\"started_on\":\"1972-11-03T16:19:40.730Z\",\"completed_on\":\"1984-10-01T08:23:08.950Z\"}"
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
- SITE_BLOCKED
- CANCEL_REQUESTED
- CANCELLED
- CANCELLED_QUICKSTART
- ABANDONED
- ABANDONED_QUICKSTART
- KILLED
- ACCOUNT_SETUP_INCOMPLETE
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
  "card_id": 863327615,
  "status": "UNKNOWN_JOB_TYPE",
  "custom_data": {
    "pqIskDDxzOPZ": "!pT,P",
    "cXeOuWWmrLTg": 42,
    "mTQgGcchFQTW": false
  },
  "notification_sent": false,
  "time_elapsed": 2074510750,
  "started_on": "1980-01-21T13:37:42.796Z",
  "completed_on": "1980-05-02T15:27:19.643Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 863327615 },
	{ "status", "UNKNOWN_JOB_TYPE" },
	{ "notification_sent", false },
	{ "time_elapsed", 2074510750 },
	{ "started_on", "1980-01-21T13:37:42.796Z" },
	{ "completed_on", "1980-05-02T15:27:19.643Z" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 863327615 )
	.add("status", "UNKNOWN_JOB_TYPE" )
	.add("notification_sent", false )
	.add("time_elapsed", 2074510750 )
	.add("started_on", "1980-01-21T13:37:42.796Z" )
	.add("completed_on", "1980-05-02T15:27:19.643Z" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":863327615,\"status\":\"UNKNOWN_JOB_TYPE\",\"custom_data\":{\"pqIskDDxzOPZ\":\"!pT,P\",\"cXeOuWWmrLTg\":42,\"mTQgGcchFQTW\":false},\"notification_sent\":false,\"time_elapsed\":2074510750,\"started_on\":\"1980-01-21T13:37:42.796Z\",\"completed_on\":\"1980-05-02T15:27:19.643Z\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/900535953
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/900535953
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

