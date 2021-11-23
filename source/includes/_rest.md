
# Accounts
Account objects contain the account information, such as username and password, for a particular cardhoder. They are used to log in to a cardholder's account for placing a payment card.
## Get account

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/723893950
```

```javascript
const accounts = await session.getAccounts(723893950);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(undefined);
```

```java
JsonValue accounts = session.get("/cardsavr_accounts", 723893950, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 723893950,
  "last_password_update": "2014-03-25T04:13:10.999Z",
  "last_saved_card": "1994-11-16T23:18:23.498Z",
  "created_on": "1985-12-19T12:44:40.461Z",
  "last_updated_on": "1982-05-14T17:27:11.832Z",
  "cardholder": {
    "id": 2131815677,
    "financial_institution_id": 1644369060,
    "agent_session_id": "eYryQtamqEFHJgGGNTAHnc",
    "type": "persistent",
    "first_name": "znhcnJIKhwaqtfqMKlGbxAxziyEhuklQ",
    "last_name": "RMLBgx",
    "email": "OJyFzAIOiJra@ZBJiXb.KnO",
    "meta_key": "PNFKyBuJLja",
    "cardholder_safe_key": "xhlIvbQxmywVBkzvujblp1v3gg7A1dTSeZDE7sdn48k=",
    "custom_data": {
      "IEFRzVKHZrRs": "w9B_FSl711kI&f[=DPhKp!P[",
      "UgCvcJWmCZFs": 97,
      "bibYxuFmMMHH": false
    },
    "created_on": "2005-09-21T09:00:39.447Z",
    "last_updated_on": "2018-12-09T11:01:42.176Z"
  },
  "merchant_site": {
    "id": 1327455459,
    "name": "aZslOJnd",
    "host": "HMyymlWcJ",
    "tags": [
      "uT6}9o#<0])DP",
      57,
      "Q,VtoX-Un#"
    ],
    "required_form_fields": [
      "lG*lP05fQ$-=^C,wU*e(3-[+jew",
      67,
      "oQTlc)7H<tMxJWx5BA~4Yw(jK).t"
    ],
    "images": [
      {
        "BjZjooQNZjcZ": "!GNP,j>oCQKr.=gW@Fw=Q7a6Ch#}6zF^",
        "fBXEGuVbCchR": 50,
        "qYtRtyudgFRg": true
      },
      {
        "jjHuzSYgpAPa": "]FA%tjNy",
        "rkXCBkkKYAoA": 4,
        "tiDjJLIBVMkz": false
      },
      {
        "QkvHWpXLzzvs": "lr#0PQ</a&",
        "VXZObdqjkMga": 39,
        "cFcJstEOJggA": true
      }
    ],
    "account_identification": {
      "fPeXzAnewves": "o",
      "tPsxBTBdnfam": 95,
      "TVbZZCTwuvkv": true
    },
    "messages": {
      "OvvvxUYTHDFA": "j}6b9i*kTqg,QpI9/u#3qzG",
      "pfoxnLIpFGGn": 2,
      "oZLMiayCYOTK": true
    },
    "mfa": true,
    "move_mouse_to_element": false,
    "proxy_order": [
      "q6GDtT5[_",
      12,
      "8CIGQ0UZu%"
    ],
    "credit_card_page": "mbMNnFf",
    "forgot_password_page": "CeTSXQVarLxlIFpimvirVTThHWbXLgv",
    "quick_start": true,
    "login_page": "GbDidcteh",
    "login": {
      "uACJvFFTOvRY": "FdVS1Ldt{bXUu2tfjl!&r7yx~}Gv>jqk",
      "bFvnIEgMtzpY": 79,
      "kMWzjQiTnMke": false
    }
  },
  "cardsavr_card": {
    "id": 1612686406,
    "bin_id": 156660939,
    "cvv": "hsG",
    "expiration_month": "q",
    "expiration_year": "T",
    "name_on_card": "bKHPnEcyMYIsNWQukbVbJwrAMcpxvnKizIPNsKIOJZnUjwrwpyQtYhouqyfnOKkpszgcsInEqSUHvczZxOhuTXnpiEsrVKevXTQcEVBmPaTKVZwxZEdpBvXFrObnKMzECEGTiHQXCEmxruBNTizkJlpeOjVqEPsXCYkhODQsCJaQeXywIIOtVFgiwWlGagnGLbtyaqVHNuBoDtnndBYECgpKeExtkorXGrTSikpeBvRQbvAxCpKCvcbABZGCnF",
    "first_6": "HsJIkNVVnqQMxACfcAzyxozngQRqFfWk",
    "first_7": "gGdpjyPyzrkXyLyVHSoVJuMEkXsgXowg",
    "first_8": "DaLjireiRLwHquTEQJTwBPErymcJZbKu",
    "created_on": "1988-07-21T03:40:04.429Z",
    "last_updated_on": "2006-10-18T18:33:55.424Z"
  },
  "customer_key": "eLROHMAxucKqgjDxbr"
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

**Example GET request path:**<br>`/cardsavr_accounts/723893950`

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
  "cardholder_id": 1824365548,
  "merchant_site_id": 1921565691,
  "customer_key": "eLROHMAxucKqgjDxbr",
  "last_card_placed_id": 2029771937,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1824365548 },
	{ "merchant_site_id", 1921565691 },
	{ "customer_key", "eLROHMAxucKqgjDxbr" },
	{ "last_card_placed_id", 2029771937 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1824365548 )
	.add("merchant_site_id", 1921565691 )
	.add("customer_key", "eLROHMAxucKqgjDxbr" )
	.add("last_card_placed_id", 2029771937 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1824365548,\"merchant_site_id\":1921565691,\"customer_key\":\"eLROHMAxucKqgjDxbr\",\"last_card_placed_id\":2029771937,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/
```

### Path

POST /cardsavr_accounts

### Description

Create a account and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
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
  "last_card_placed_id": 1402341968,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 1402341968 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 1402341968 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":1402341968,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/723893950
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
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/723893950
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1476768325
```

```javascript
const addresses = await session.getAddresses(1476768325);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(undefined);
```

```java
JsonValue addresses = session.get("/cardsavr_addresses", 1476768325, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1476768325,
  "address1": "123 Main St.",
  "address2": "Unit A",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "2065555555",
  "created_on": "2008-07-07T20:41:37.882Z",
  "last_updated_on": "1975-10-11T14:00:48.505Z",
  "cardholder": {
    "id": 1832929922,
    "financial_institution_id": 936555399,
    "agent_session_id": "Ju",
    "type": "persistent",
    "first_name": "osswoOREHfUX",
    "last_name": "ZOenIsPLNGlR",
    "email": "aGksYDJfWXiA@RGnLUw.MFm",
    "meta_key": "fjlCrraueZgs",
    "cardholder_safe_key": "JsiCjeVR5xmn95flyb10wPbZ4SvHVtiDxVtW21KaH1I=",
    "custom_data": {
      "jZJhhOwQrjiN": "RuPI{B{q_@YNv(hM19xEpaA/{mS",
      "CuxhpZcQxVJt": 18,
      "PKGtPZyxgjfh": false
    },
    "created_on": "1979-01-05T23:18:19.179Z",
    "last_updated_on": "2015-02-25T14:42:01.371Z"
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

**Example GET request path:**<br>`/cardsavr_addresses/1476768325`

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
  "cardholder_id": 1141628160,
  "address1": "123 Main St.",
  "address2": "Unit A",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1141628160 },
	{ "address1", "123 Main St." },
	{ "address2", "Unit A" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.CreateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1141628160 )
	.add("address1", "123 Main St." )
	.add("address2", "Unit A" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.post("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1141628160,\"address1\":\"123 Main St.\",\"address2\":\"Unit A\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"phone_number\":\"2065555555\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/
```

### Path

POST /cardsavr_addresses

### Description

Create a address and return the created object.

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
  "address1": "123 Main St.",
  "address2": "Unit A",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "phone_number": "2065555555"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "address1", "123 Main St." },
	{ "address2", "Unit A" },
	{ "city", "Seattle" },
	{ "subnational", "WA" },
	{ "postal_code", "98177" },
	{ "postal_other", "98177-0124" },
	{ "country", "USA" },
	{ "is_primary", true },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "phone_number", "2065555555" }
};

CardSavrResponse<Address> address = await http.UpdateAddressAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("address1", "123 Main St." )
	.add("address2", "Unit A" )
	.add("city", "Seattle" )
	.add("subnational", "WA" )
	.add("postal_code", "98177" )
	.add("postal_other", "98177-0124" )
	.add("country", "USA" )
	.add("is_primary", true )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("phone_number", "2065555555" )
	.build();
JsonValue address = session.put("/cardsavr_addresses", body, null, null);
```

```shell
curl -d "{\"address1\":\"123 Main St.\",\"address2\":\"Unit A\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"phone_number\":\"2065555555\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1476768325
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1476768325
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/477044742
```

```javascript
const bins = await session.getBins(477044742);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(undefined);
```

```java
JsonValue bins = session.get("/cardsavr_bins", 477044742, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 477044742,
  "custom_data": {
    "qXHpJpZJvlyT": "})RScqttXp+KUb}D]FI_*I-^C",
    "uyRMONYKprGp": 10,
    "bMNQvjgHHvbg": false
  },
  "created_on": "2014-03-01T11:46:34.710Z",
  "last_updated_on": "2018-02-13T05:40:43.936Z",
  "financial_institution": {
    "id": 468671733,
    "name": "yYrNohxuOqlWYiKdzmrwrjIJVBnqQoZemWpgunmFTqpQQckigUMFtVaJtqeZYQP",
    "description": "aHzGUgOnsSUidNLZFSWWmFkUpN",
    "lookup_key": "VLzDSiMQduHijJczIszKSMzlCkrPICynCRJHNhQmMBbySYGbNzuMpTcnyUEKKns",
    "alternate_lookup_key": "qlUifQkFMMwRwLYYTbEYEkSopuOZSHfNhqftELnFoJnxhZnUeQOUpoQsXdnmsOb",
    "config": {
      "acYOCfBrzaMO": "Ou1f!u",
      "OjhtUgeOkRMc": 88,
      "IuyAZeJtyiRt": false
    },
    "created_on": "1995-04-28T22:23:19.366Z",
    "last_updated_on": "2007-10-26T08:38:46.359Z"
  },
  "bank_identification_number": "15224386"
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

**Example GET request path:**<br>`/cardsavr_bins/477044742`

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
  "financial_institution_id": 1619322979,
  "bank_identification_number": "15224386",
  "custom_data": {
    "qXHpJpZJvlyT": "})RScqttXp+KUb}D]FI_*I-^C",
    "uyRMONYKprGp": 10,
    "bMNQvjgHHvbg": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1619322979 },
	{ "bank_identification_number", "15224386" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1619322979 )
	.add("bank_identification_number", "15224386" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1619322979,\"bank_identification_number\":\"15224386\",\"custom_data\":{\"qXHpJpZJvlyT\":\"})RScqttXp+KUb}D]FI_*I-^C\",\"uyRMONYKprGp\":10,\"bMNQvjgHHvbg\":false}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/
```

### Path

POST /cardsavr_bins

### Description

Create a bin and return the created object.

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
  "financial_institution_id": 1441301552,
  "custom_data": {
    "rtipsvfFShTc": "PLLraMc]!1sv^9GvRK)B>)U(fJISe",
    "OaksbphzjncV": 29,
    "mAxTrWIZEPgK": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1441301552 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1441301552 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1441301552,\"custom_data\":{\"rtipsvfFShTc\":\"PLLraMc]!1sv^9GvRK)B>)U(fJISe\",\"OaksbphzjncV\":29,\"mAxTrWIZEPgK\":true}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/477044742
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/477044742
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
https://api.INSTANCE.cardsavr.io/card_placement_results/1102990271
```

```javascript
const cardplacementresults = await session.getCardPlacementResults(1102990271);
```

```csharp
CardSavrResponse<CardPlacementResults> cardplacementresults = await session.GetCardPlacementResultsAsync(undefined);
```

```java
JsonValue cardplacementresults = session.get("/card_placement_results", 1102990271, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1102990271,
  "merchant_site_hostname": "amazon.com",
  "meta_key": "MB9810411",
  "fi_name": "ACME Bank",
  "bank_identification_number": "38600997",
  "cuid": "abcd1234",
  "par": "ouFkEdkjIbOuaGjQvoPCTZgOclcOI",
  "card_customer_key": "NA",
  "account_customer_key": "1$abcd1234",
  "status": "SUCCESSFUL",
  "status_message": "uZfjLkgtLzuhbsbWKUhkX",
  "termination_type": "BIILLABLE",
  "custom_data": {
    "TQYFjZOLaCPE": "6/SiHd>45",
    "qhRJIRPLOrzi": 90,
    "RQxbIItdXfqX": true
  },
  "time_elapsed": 1412547964,
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "trace": "noGXiCFuUAszzCkdEhkACRcliVOwxbpYdNrccYVsmMzYBNhxZrmyJXRHzWGjTdaroDKnXXLnSQlqsrPdeudIozvmChCjJFNCBYJwCsdcMbUHgzOzflkHfeyTtoeBxcXIUJbUFWQSKnbaXLQdGObOimlVnzmJlkhmDcYlFDDiqcCkgVuTFdOYAyLDxVdXvbBtvSsrtGpxYBOYntMUkEwMGLaDDOqBCgYaDMOwBRDosJdQWORpxLEIqopoVllEta",
  "email_sent": false,
  "completed_on": "1998-04-24T19:51:35.111Z",
  "created_on": "2021-09-03T07:51:02.325Z",
  "last_updated_on": "1972-05-10T18:57:41.033Z",
  "financial_institution": {
    "id": 1991248087,
    "name": "esydboQcyVrxYuZVybuTrfqKkkyJRGYevCHPsivoYaWPjgfxbhhlouTwPpAbmQA",
    "description": "MDvrflWJCeuQUTjavv",
    "lookup_key": "sbRYStJFuIqzPEkoPLYorWUKQfjJCxUgpXKoQcFsgxQBdJOgRZdfovKKcXytOeQ",
    "alternate_lookup_key": "pRNSCmqvdNRHvZhcJDtTxtrVtUZtOkAVXlRtUqChrfIuvfngMQUsDyujYQyrFTb",
    "config": {
      "SsoEPydItAbF": "WBM",
      "VPCjmttGjrlM": 47,
      "rRbpdylDSCgP": true
    },
    "created_on": "2011-06-18T02:01:24.092Z",
    "last_updated_on": "1977-07-13T03:41:13.171Z"
  },
  "merchant_site": {
    "id": 395027150,
    "name": "Az",
    "host": "nXcYvCgNTyOQbDPtaqxXemAXqDI",
    "tags": [
      "Co-*x16QAtNU<Oa-B",
      30,
      "k3Zcx"
    ],
    "queue_name": "vbs_lambda_queue",
    "required_form_fields": [
      "+A",
      7,
      "afolSNQ.jVYg^pA[K7&$t$Jz/2D!"
    ],
    "images": [
      {
        "OYzAvrVskSDt": "p9kF{89u.GK>i]0j3SD,%1@A<nzqS_",
        "xJUKzEHfagBV": 57,
        "WVhEVMygvSCD": false
      },
      {
        "LCngsFRxaQSx": "yJJGDK!=tK]4fq<u",
        "EvRGiUapgSQJ": 43,
        "SEscxEwCskEH": false
      },
      {
        "dJkOgjghGqLB": "gCLkx0*h[[fe",
        "MgdLvkNClgiG": 84,
        "kFJbCEXDXuvm": false
      }
    ],
    "account_identification": {
      "rjbmOcvjnRNj": ".2(%@qY=]/vN_+m9<Uqwya=",
      "EkOCvSqZLBPz": 33,
      "rZtWceSTEKMb": false
    },
    "messages": {
      "xwMqQDRURACU": "zHAt0l*2VZ]{S0sLR,R65KNWb",
      "AHCyBJIFtCyO": 77,
      "SFbbiVqgJqHI": true
    },
    "mfa": true,
    "move_mouse_to_element": true,
    "proxy_order": [
      "X5JpGDWZe<g8,H2GW",
      1,
      "(q,ak4b#[/F"
    ],
    "credit_card_page": "oUuXBjAtfjICqAgzOPOpKvDvt",
    "forgot_password_page": "NIZ",
    "quick_start": false,
    "login_page": "veQSoOGQvhbxjBwkKRniUMX",
    "login": {
      "ckbXbCYdIiqe": "YQ76.+d)OMH_3sp$>0j)y,",
      "nBZUzUyRgdvO": 88,
      "DghnyysCrfoC": true
    }
  },
  "cardsavr_bin": {
    "id": 1451045911,
    "financial_institution_id": 444055346,
    "custom_data": {
      "oShIQHDoHfhk": "}dYgA2>MzOl)Bz-u=68Vx3).]xk",
      "qwLyNptvvUPA": 37,
      "xZaSqhlowbYp": true
    },
    "created_on": "1989-09-10T08:02:01.448Z",
    "last_updated_on": "1987-12-04T13:54:40.203Z"
  },
  "place_card_on_single_site_job_id": 774339397
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

**Example GET request path:**<br>`/card_placement_results/1102990271`

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
  "merchant_site_hostname": "amazon.com",
  "meta_key": "MB9810411",
  "fi_name": "ACME Bank",
  "bank_identification_number": "38600997",
  "cuid": "abcd1234",
  "par": "ouFkEdkjIbOuaGjQvoPCTZgOclcOI",
  "card_customer_key": "NA",
  "account_customer_key": "1$abcd1234",
  "status": "SUCCESSFUL",
  "status_message": "uZfjLkgtLzuhbsbWKUhkX",
  "termination_type": "BIILLABLE",
  "custom_data": {
    "TQYFjZOLaCPE": "6/SiHd>45",
    "qhRJIRPLOrzi": 90,
    "RQxbIItdXfqX": true
  },
  "time_elapsed": 1412547964,
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "trace": "noGXiCFuUAszzCkdEhkACRcliVOwxbpYdNrccYVsmMzYBNhxZrmyJXRHzWGjTdaroDKnXXLnSQlqsrPdeudIozvmChCjJFNCBYJwCsdcMbUHgzOzflkHfeyTtoeBxcXIUJbUFWQSKnbaXLQdGObOimlVnzmJlkhmDcYlFDDiqcCkgVuTFdOYAyLDxVdXvbBtvSsrtGpxYBOYntMUkEwMGLaDDOqBCgYaDMOwBRDosJdQWORpxLEIqopoVllEta",
  "place_card_on_single_site_job_id": 774339397,
  "financial_institution_id": 1216798291,
  "merchant_site_id": 1683244040,
  "email_sent": false,
  "completed_on": "1998-04-24T19:51:35.111Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "merchant_site_hostname", "amazon.com" },
	{ "meta_key", "MB9810411" },
	{ "fi_name", "ACME Bank" },
	{ "bank_identification_number", "38600997" },
	{ "cuid", "abcd1234" },
	{ "par", "ouFkEdkjIbOuaGjQvoPCTZgOclcOI" },
	{ "card_customer_key", "NA" },
	{ "account_customer_key", "1$abcd1234" },
	{ "status", "SUCCESSFUL" },
	{ "status_message", "uZfjLkgtLzuhbsbWKUhkX" },
	{ "termination_type", "BIILLABLE" },
	{ "time_elapsed", 1412547964 },
	{ "first_6", "000000" },
	{ "first_7", "0000000" },
	{ "first_8", "00000000" },
	{ "trace", "noGXiCFuUAszzCkdEhkACRcliVOwxbpYdNrccYVsmMzYBNhxZrmyJXRHzWGjTdaroDKnXXLnSQlqsrPdeudIozvmChCjJFNCBYJwCsdcMbUHgzOzflkHfeyTtoeBxcXIUJbUFWQSKnbaXLQdGObOimlVnzmJlkhmDcYlFDDiqcCkgVuTFdOYAyLDxVdXvbBtvSsrtGpxYBOYntMUkEwMGLaDDOqBCgYaDMOwBRDosJdQWORpxLEIqopoVllEta" },
	{ "place_card_on_single_site_job_id", 774339397 },
	{ "financial_institution_id", 1216798291 },
	{ "merchant_site_id", 1683244040 },
	{ "email_sent", false },
	{ "completed_on", "1998-04-24T19:51:35.111Z" }
};

CardSavrResponse<CardPlacementResult> cardplacementresult = await http.CreateCardPlacementResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("merchant_site_hostname", "amazon.com" )
	.add("meta_key", "MB9810411" )
	.add("fi_name", "ACME Bank" )
	.add("bank_identification_number", "38600997" )
	.add("cuid", "abcd1234" )
	.add("par", "ouFkEdkjIbOuaGjQvoPCTZgOclcOI" )
	.add("card_customer_key", "NA" )
	.add("account_customer_key", "1$abcd1234" )
	.add("status", "SUCCESSFUL" )
	.add("status_message", "uZfjLkgtLzuhbsbWKUhkX" )
	.add("termination_type", "BIILLABLE" )
	.add("time_elapsed", 1412547964 )
	.add("first_6", "000000" )
	.add("first_7", "0000000" )
	.add("first_8", "00000000" )
	.add("trace", "noGXiCFuUAszzCkdEhkACRcliVOwxbpYdNrccYVsmMzYBNhxZrmyJXRHzWGjTdaroDKnXXLnSQlqsrPdeudIozvmChCjJFNCBYJwCsdcMbUHgzOzflkHfeyTtoeBxcXIUJbUFWQSKnbaXLQdGObOimlVnzmJlkhmDcYlFDDiqcCkgVuTFdOYAyLDxVdXvbBtvSsrtGpxYBOYntMUkEwMGLaDDOqBCgYaDMOwBRDosJdQWORpxLEIqopoVllEta" )
	.add("place_card_on_single_site_job_id", 774339397 )
	.add("financial_institution_id", 1216798291 )
	.add("merchant_site_id", 1683244040 )
	.add("email_sent", false )
	.add("completed_on", "1998-04-24T19:51:35.111Z" )
	.build();
JsonValue cardplacementresult = session.post("/card_placement_results", body, null, null);
```

```shell
curl -d "{\"merchant_site_hostname\":\"amazon.com\",\"meta_key\":\"MB9810411\",\"fi_name\":\"ACME Bank\",\"bank_identification_number\":\"38600997\",\"cuid\":\"abcd1234\",\"par\":\"ouFkEdkjIbOuaGjQvoPCTZgOclcOI\",\"card_customer_key\":\"NA\",\"account_customer_key\":\"1$abcd1234\",\"status\":\"SUCCESSFUL\",\"status_message\":\"uZfjLkgtLzuhbsbWKUhkX\",\"termination_type\":\"BIILLABLE\",\"custom_data\":{\"TQYFjZOLaCPE\":\"6/SiHd>45\",\"qhRJIRPLOrzi\":90,\"RQxbIItdXfqX\":true},\"time_elapsed\":1412547964,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\",\"trace\":\"noGXiCFuUAszzCkdEhkACRcliVOwxbpYdNrccYVsmMzYBNhxZrmyJXRHzWGjTdaroDKnXXLnSQlqsrPdeudIozvmChCjJFNCBYJwCsdcMbUHgzOzflkHfeyTtoeBxcXIUJbUFWQSKnbaXLQdGObOimlVnzmJlkhmDcYlFDDiqcCkgVuTFdOYAyLDxVdXvbBtvSsrtGpxYBOYntMUkEwMGLaDDOqBCgYaDMOwBRDosJdQWORpxLEIqopoVllEta\",\"place_card_on_single_site_job_id\":774339397,\"financial_institution_id\":1216798291,\"merchant_site_id\":1683244040,\"email_sent\":false,\"completed_on\":\"1998-04-24T19:51:35.111Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/card_placement_results/
```

### Path

POST /card_placement_results

### Description

Create a card placement result and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
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
  "merchant_site_hostname": "amazon.com",
  "meta_key": "MB9810411",
  "fi_name": "ACME Bank",
  "bank_identification_number": "3099510",
  "cuid": "abcd1234",
  "par": "NXIFnLpGddJtmjgxParXkTQuILeJY",
  "card_customer_key": "NA",
  "account_customer_key": "1$abcd1234",
  "status": "SUCCESSFUL",
  "status_message": "rImaHgWTLFXuuiIjjLtnHpHYotjbCpAN",
  "termination_type": "BIILLABLE",
  "custom_data": {
    "HAXuNbwydiYy": "Y]B9Jzd>QcbxueFXXK(%TCLh(b]",
    "RpwKvXeovQOv": 46,
    "XdWfqBWmmFem": false
  },
  "time_elapsed": 194007233,
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "trace": "YYHFNKnIokBXdyibOlxqmFiJWDtuWwcjPcTUPSPOkgehGTVikPQUWjeTzMVlThAHzbdXPuiwTRShYryRKymBMhtQyZtZCdxOeHBcLCyTzKDCqbjrLjYbAMgwrXVTDJgAKrEuGSAZWFtLjbvFaiGdVVfIblJTAEvEmErJMGduupPPMzaMTSjmdclPWIeOJfGAyCQdearukkvDIVBwwpSrhYxnpJGjJkvdDguGkiQNpqHbTcMJDsazSrymHWBBCk",
  "financial_institution_id": 1495745042,
  "merchant_site_id": 248232743,
  "email_sent": false,
  "completed_on": "1990-02-27T17:15:29.017Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "merchant_site_hostname", "amazon.com" },
	{ "meta_key", "MB9810411" },
	{ "fi_name", "ACME Bank" },
	{ "bank_identification_number", "3099510" },
	{ "cuid", "abcd1234" },
	{ "par", "NXIFnLpGddJtmjgxParXkTQuILeJY" },
	{ "card_customer_key", "NA" },
	{ "account_customer_key", "1$abcd1234" },
	{ "status", "SUCCESSFUL" },
	{ "status_message", "rImaHgWTLFXuuiIjjLtnHpHYotjbCpAN" },
	{ "termination_type", "BIILLABLE" },
	{ "time_elapsed", 194007233 },
	{ "first_6", "000000" },
	{ "first_7", "0000000" },
	{ "first_8", "00000000" },
	{ "trace", "YYHFNKnIokBXdyibOlxqmFiJWDtuWwcjPcTUPSPOkgehGTVikPQUWjeTzMVlThAHzbdXPuiwTRShYryRKymBMhtQyZtZCdxOeHBcLCyTzKDCqbjrLjYbAMgwrXVTDJgAKrEuGSAZWFtLjbvFaiGdVVfIblJTAEvEmErJMGduupPPMzaMTSjmdclPWIeOJfGAyCQdearukkvDIVBwwpSrhYxnpJGjJkvdDguGkiQNpqHbTcMJDsazSrymHWBBCk" },
	{ "financial_institution_id", 1495745042 },
	{ "merchant_site_id", 248232743 },
	{ "email_sent", false },
	{ "completed_on", "1990-02-27T17:15:29.017Z" }
};

CardSavrResponse<CardPlacementResult> cardplacementresult = await http.UpdateCardPlacementResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("merchant_site_hostname", "amazon.com" )
	.add("meta_key", "MB9810411" )
	.add("fi_name", "ACME Bank" )
	.add("bank_identification_number", "3099510" )
	.add("cuid", "abcd1234" )
	.add("par", "NXIFnLpGddJtmjgxParXkTQuILeJY" )
	.add("card_customer_key", "NA" )
	.add("account_customer_key", "1$abcd1234" )
	.add("status", "SUCCESSFUL" )
	.add("status_message", "rImaHgWTLFXuuiIjjLtnHpHYotjbCpAN" )
	.add("termination_type", "BIILLABLE" )
	.add("time_elapsed", 194007233 )
	.add("first_6", "000000" )
	.add("first_7", "0000000" )
	.add("first_8", "00000000" )
	.add("trace", "YYHFNKnIokBXdyibOlxqmFiJWDtuWwcjPcTUPSPOkgehGTVikPQUWjeTzMVlThAHzbdXPuiwTRShYryRKymBMhtQyZtZCdxOeHBcLCyTzKDCqbjrLjYbAMgwrXVTDJgAKrEuGSAZWFtLjbvFaiGdVVfIblJTAEvEmErJMGduupPPMzaMTSjmdclPWIeOJfGAyCQdearukkvDIVBwwpSrhYxnpJGjJkvdDguGkiQNpqHbTcMJDsazSrymHWBBCk" )
	.add("financial_institution_id", 1495745042 )
	.add("merchant_site_id", 248232743 )
	.add("email_sent", false )
	.add("completed_on", "1990-02-27T17:15:29.017Z" )
	.build();
JsonValue cardplacementresult = session.put("/card_placement_results", body, null, null);
```

```shell
curl -d "{\"merchant_site_hostname\":\"amazon.com\",\"meta_key\":\"MB9810411\",\"fi_name\":\"ACME Bank\",\"bank_identification_number\":\"3099510\",\"cuid\":\"abcd1234\",\"par\":\"NXIFnLpGddJtmjgxParXkTQuILeJY\",\"card_customer_key\":\"NA\",\"account_customer_key\":\"1$abcd1234\",\"status\":\"SUCCESSFUL\",\"status_message\":\"rImaHgWTLFXuuiIjjLtnHpHYotjbCpAN\",\"termination_type\":\"BIILLABLE\",\"custom_data\":{\"HAXuNbwydiYy\":\"Y]B9Jzd>QcbxueFXXK(%TCLh(b]\",\"RpwKvXeovQOv\":46,\"XdWfqBWmmFem\":false},\"time_elapsed\":194007233,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\",\"trace\":\"YYHFNKnIokBXdyibOlxqmFiJWDtuWwcjPcTUPSPOkgehGTVikPQUWjeTzMVlThAHzbdXPuiwTRShYryRKymBMhtQyZtZCdxOeHBcLCyTzKDCqbjrLjYbAMgwrXVTDJgAKrEuGSAZWFtLjbvFaiGdVVfIblJTAEvEmErJMGduupPPMzaMTSjmdclPWIeOJfGAyCQdearukkvDIVBwwpSrhYxnpJGjJkvdDguGkiQNpqHbTcMJDsazSrymHWBBCk\",\"financial_institution_id\":1495745042,\"merchant_site_id\":248232743,\"email_sent\":false,\"completed_on\":\"1990-02-27T17:15:29.017Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/card_placement_results/1102990271
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/757497013
```

```javascript
const cards = await session.getCards(757497013);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(undefined);
```

```java
JsonValue cards = session.get("/cardsavr_cards", 757497013, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 757497013,
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Joe C Smith",
  "created_on": "1999-08-27T03:16:30.022Z",
  "last_updated_on": "2016-12-23T17:19:13.036Z",
  "cardholder": {
    "id": 1240198549,
    "financial_institution_id": 1032620687,
    "agent_session_id": "xWXTIMyaLHsFYh",
    "type": "persistent",
    "first_name": "dGVEsIQNiwLXBJAoUWhdNAFKWFIg",
    "last_name": "LYO",
    "email": "AIwXpHRxAEeY@uVpvlc.gkF",
    "meta_key": "SSYywmmnCwpxLevAV",
    "cardholder_safe_key": "4OH2eweZx7cCthrUFRvESm5u8lGwuRX3q7Nv82cUkNU=",
    "custom_data": {
      "yrLzyGgttWEP": "1LYbW}JlBsTPBkL>p.hZ^Cp%visF",
      "GJLvPFBeAsKe": 54,
      "XuhvSQyDMNww": true
    },
    "created_on": "1990-12-12T13:13:16.468Z",
    "last_updated_on": "1981-04-30T02:33:54.590Z"
  },
  "cardsavr_bin": {
    "id": 671524679,
    "financial_institution_id": 315360586,
    "custom_data": {
      "rORYfvGQdpIs": "%CX^Q/{+SQgSWUo&pyx3AvhECqhg",
      "OjzplEtRNpMh": 83,
      "tUWReFBbDQXB": true
    },
    "created_on": "2016-03-24T18:06:00.794Z",
    "last_updated_on": "1973-05-21T05:50:34.425Z"
  },
  "address_id": 496467031,
  "par": "diIybmoGlTaNIgZnpDTuBExNooSHz"
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

**Example GET request path:**<br>`/cardsavr_cards/757497013`

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
address_id | number | ID of address associated with this card.
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
  "cardholder_id": 1073424271,
  "address_id": 496467031,
  "bin_id": 1176621005,
  "par": "diIybmoGlTaNIgZnpDTuBExNooSHz",
  "pan": "4111111111111111",
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Joe C Smith"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1073424271 },
	{ "address_id", 496467031 },
	{ "bin_id", 1176621005 },
	{ "par", "diIybmoGlTaNIgZnpDTuBExNooSHz" },
	{ "pan", "4111111111111111" },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Joe C Smith" }
};

CardSavrResponse<Card> card = await http.CreateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1073424271 )
	.add("address_id", 496467031 )
	.add("bin_id", 1176621005 )
	.add("par", "diIybmoGlTaNIgZnpDTuBExNooSHz" )
	.add("pan", "4111111111111111" )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Joe C Smith" )
	.build();
JsonValue card = session.post("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1073424271,\"address_id\":496467031,\"bin_id\":1176621005,\"par\":\"diIybmoGlTaNIgZnpDTuBExNooSHz\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/
```

### Path

POST /cardsavr_cards

### Description

Create a card and return the created object.

### Body parameters

Parameter | Type | Required | Description
-------- | ---- | --------- | ----------
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
  "bin_id": 78310085,
  "cvv": "111",
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Joe C Smith",
  "pan": "4111111111111111"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "bin_id", 78310085 },
	{ "cvv", "111" },
	{ "expiration_month", 12 },
	{ "expiration_year", 24 },
	{ "name_on_card", "Joe C Smith" },
	{ "pan", "4111111111111111" }
};

CardSavrResponse<Card> card = await http.UpdateCardAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("bin_id", 78310085 )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Joe C Smith" )
	.add("pan", "4111111111111111" )
	.build();
JsonValue card = session.put("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"bin_id\":78310085,\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\",\"pan\":\"4111111111111111\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/757497013
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/757497013
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
https://api.INSTANCE.cardsavr.io/cardholders/1785960076
```

```javascript
const cardholders = await session.getCardholders(1785960076);
```

```csharp
CardSavrResponse<Cardholders> cardholders = await session.GetCardholdersAsync(undefined);
```

```java
JsonValue cardholders = session.get("/cardholders", 1785960076, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1785960076,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "MB9810411",
  "custom_data": {
    "ETGiNtREaVaK": "i&4wCS,JJ_p.dUi^m-i9i",
    "hFohwKdjKFsx": 45,
    "mxkzNyCAYjTF": false
  },
  "created_on": "1976-12-13T23:11:25.590Z",
  "last_updated_on": "1976-10-19T05:06:20.632Z",
  "cuid": "abcd1234",
  "financial_institution": {
    "id": 613591216,
    "name": "VHzCFbvRInPXbwYERQBFZOJclSfHScwUzdWwhepoBEtzYZSsmsHwTscEGabHyZC",
    "description": "TGokcSzFJSpVzUbOEgfpbHBnufw",
    "lookup_key": "zWPCYbFADsuPTCQdWHBaOmEcwLrKNnbomrXHNzcCOFLOfAheWytwJNHZCvXNlyp",
    "alternate_lookup_key": "hTUmldLxoHMQWatSjLLqDqzIYQLNSOrcabzOxhLZblgCTaViDjdIhQTXqjWcWcF",
    "config": {
      "hQCniKjbuhQL": ".i+qb2F1~PpO.tOmBp(x",
      "krtEnIKEPxCh": 67,
      "wJNneoqHgcwM": false
    },
    "created_on": "1977-07-09T13:52:48.965Z",
    "last_updated_on": "1994-12-07T22:55:25.486Z"
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

**Example GET request path:**<br>`/cardholders/1785960076`

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
  "cuid": "abcd1234",
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "MB9810411",
  "custom_data": {
    "ETGiNtREaVaK": "i&4wCS,JJ_p.dUi^m-i9i",
    "hFohwKdjKFsx": 45,
    "mxkzNyCAYjTF": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cuid", "abcd1234" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "MB9810411" }
};

CardSavrResponse<Cardholder> cardholder = await http.CreateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cuid", "abcd1234" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "MB9810411" )
	.build();
JsonValue cardholder = session.post("/cardholders", body, null, null);
```

```shell
curl -d "{\"cuid\":\"abcd1234\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"MB9810411\",\"custom_data\":{\"ETGiNtREaVaK\":\"i&4wCS,JJ_p.dUi^m-i9i\",\"hFohwKdjKFsx\":45,\"mxkzNyCAYjTF\":false}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/
```

### Path

POST /cardholders

### Description

Create a cardholder and return the created object.

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
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "MB9810411",
  "custom_data": {
    "dQahXMJBazVE": "c64&RbBu3ttb_f_1Sp",
    "ZyEVwGVZYsoP": 55,
    "CrVlvXtsDmxJ": true
  },
  "cuid": "abcd1234"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "email", "test_email@strivve.com" },
	{ "meta_key", "MB9810411" },
	{ "cuid", "abcd1234" }
};

CardSavrResponse<Cardholder> cardholder = await http.UpdateCardholderAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("email", "test_email@strivve.com" )
	.add("meta_key", "MB9810411" )
	.add("cuid", "abcd1234" )
	.build();
JsonValue cardholder = session.put("/cardholders", body, null, null);
```

```shell
curl -d "{\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"MB9810411\",\"custom_data\":{\"dQahXMJBazVE\":\"c64&RbBu3ttb_f_1Sp\",\"ZyEVwGVZYsoP\":55,\"CrVlvXtsDmxJ\":true},\"cuid\":\"abcd1234\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/1785960076
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
https://api.INSTANCE.cardsavr.io/cardholders/1785960076
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/895977695
```

```javascript
const users = await session.getUsers(895977695);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(undefined);
```

```java
JsonValue users = session.get("/cardsavr_users", 895977695, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 895977695,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "2012-05-01T06:21:39.849Z",
  "is_locked": true,
  "password_lifetime": 290,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "admin",
  "next_rotation_on": "2001-04-13T17:11:47.188Z",
  "created_on": "1993-02-05T05:25:01.353Z",
  "last_updated_on": "1980-01-03T09:22:31.318Z",
  "username": "jsmith123",
  "financial_institution": {
    "id": 1518935965,
    "name": "OpOGtgAUOUEaejXNQbIqxujFDsXqzgjwOpxBWlyQDyeKHVEiXVlfSJumGMLSaeU",
    "description": "pxCNVJRtNiUgXJqjiRPtfa",
    "lookup_key": "SaiLTWIAoLmKUqiGYjZazDjAwUGGHmSuzSNmKgxignSmUOZdtKaYxAcenOEMAsn",
    "alternate_lookup_key": "PZUCEoJRPAYZuyjhXPqiQBKPezeCoNJHnAkSAktNcXqBJFGwqHrnGISDoZUErcI",
    "config": {
      "kSQsWENENcni": "g~q7fg9I4*",
      "sbWPKzQicCGd": 90,
      "BsSkFlraEEYD": false
    },
    "created_on": "1978-03-22T04:04:17.142Z",
    "last_updated_on": "2001-07-30T17:50:43.037Z"
  }
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

**Example GET request path:**<br>`/cardsavr_users/895977695`

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
  "financial_institution_id": 1788016856,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 290,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "admin",
  "next_rotation_on": "2001-04-13T17:11:47.188Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1788016856 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 290 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "admin" },
	{ "next_rotation_on", "2001-04-13T17:11:47.188Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1788016856 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 290 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "admin" )
	.add("next_rotation_on", "2001-04-13T17:11:47.188Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1788016856,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":290,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"admin\",\"next_rotation_on\":\"2001-04-13T17:11:47.188Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/
```

### Path

POST /cardsavr_users

### Description

Create a user and return the created object.

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
  "financial_institution_id": 1041082603,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 365,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "cardholder_agent",
  "next_rotation_on": "1989-05-19T03:55:30.484Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1041082603 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 365 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "cardholder_agent" },
	{ "next_rotation_on", "1989-05-19T03:55:30.484Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1041082603 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 365 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "cardholder_agent" )
	.add("next_rotation_on", "1989-05-19T03:55:30.484Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1041082603,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":365,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"cardholder_agent\",\"next_rotation_on\":\"1989-05-19T03:55:30.484Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/895977695
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/895977695
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
https://api.INSTANCE.cardsavr.io/financial_institutions/227948117
```

```javascript
const financialinstitutions = await session.getFinancialInstitutions(227948117);
```

```csharp
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(undefined);
```

```java
JsonValue financialinstitutions = session.get("/financial_institutions", 227948117, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 227948117,
  "name": "JvpnoVcPgQvARlPvNqEkHNDLegzHbfCsBRKMDsPnYQuunelptAEDXvbdgfFRKOW",
  "description": "HT",
  "lookup_key": "NNjLsHzDTqNKDhzPOTpHqFNFjVMQfdittCPZtDALJvMrHhWnqiCtCHBySgmmduk",
  "alternate_lookup_key": "ieUHDhMCyqllwHNweIaYhxIDnWziAvpgOZTSMjVxEyyXDsEGWZvBQSMLEGrQNoj",
  "created_on": "1995-06-23T03:30:50.237Z",
  "last_updated_on": "1973-07-09T03:06:12.494Z"
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

**Example GET request path:**<br>`/financial_institutions/227948117`

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
  "name": "JvpnoVcPgQvARlPvNqEkHNDLegzHbfCsBRKMDsPnYQuunelptAEDXvbdgfFRKOW",
  "description": "HT",
  "lookup_key": "NNjLsHzDTqNKDhzPOTpHqFNFjVMQfdittCPZtDALJvMrHhWnqiCtCHBySgmmduk",
  "alternate_lookup_key": "ieUHDhMCyqllwHNweIaYhxIDnWziAvpgOZTSMjVxEyyXDsEGWZvBQSMLEGrQNoj"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "JvpnoVcPgQvARlPvNqEkHNDLegzHbfCsBRKMDsPnYQuunelptAEDXvbdgfFRKOW" },
	{ "description", "HT" },
	{ "lookup_key", "NNjLsHzDTqNKDhzPOTpHqFNFjVMQfdittCPZtDALJvMrHhWnqiCtCHBySgmmduk" },
	{ "alternate_lookup_key", "ieUHDhMCyqllwHNweIaYhxIDnWziAvpgOZTSMjVxEyyXDsEGWZvBQSMLEGrQNoj" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "JvpnoVcPgQvARlPvNqEkHNDLegzHbfCsBRKMDsPnYQuunelptAEDXvbdgfFRKOW" )
	.add("description", "HT" )
	.add("lookup_key", "NNjLsHzDTqNKDhzPOTpHqFNFjVMQfdittCPZtDALJvMrHhWnqiCtCHBySgmmduk" )
	.add("alternate_lookup_key", "ieUHDhMCyqllwHNweIaYhxIDnWziAvpgOZTSMjVxEyyXDsEGWZvBQSMLEGrQNoj" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"JvpnoVcPgQvARlPvNqEkHNDLegzHbfCsBRKMDsPnYQuunelptAEDXvbdgfFRKOW\",\"description\":\"HT\",\"lookup_key\":\"NNjLsHzDTqNKDhzPOTpHqFNFjVMQfdittCPZtDALJvMrHhWnqiCtCHBySgmmduk\",\"alternate_lookup_key\":\"ieUHDhMCyqllwHNweIaYhxIDnWziAvpgOZTSMjVxEyyXDsEGWZvBQSMLEGrQNoj\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
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

See [financial institution response attributes](#response-financial_institution).


## Update financial institution

```javascript
const financialinstitution = await session.updateFinancialInstitution(1,{
  "name": "KWwdBietWJCbtDjMYqbZnBTYOfZiIBRkFWrBLSMtofmDzBXgVmVsFkPAHSJSgHZ",
  "description": "apOnqye",
  "lookup_key": "lukNXuQsISBAWVpHaaWJWMPHNQKoTGTgrxyUaokJccpgoONXPcdJDCNTNRoSNoG",
  "alternate_lookup_key": "ayQvdarDIIPknCBuWgHeyxZeippnqmquBkwHFmNOvcPfPkkLdYhhYSPcOPXnbSs"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "KWwdBietWJCbtDjMYqbZnBTYOfZiIBRkFWrBLSMtofmDzBXgVmVsFkPAHSJSgHZ" },
	{ "description", "apOnqye" },
	{ "lookup_key", "lukNXuQsISBAWVpHaaWJWMPHNQKoTGTgrxyUaokJccpgoONXPcdJDCNTNRoSNoG" },
	{ "alternate_lookup_key", "ayQvdarDIIPknCBuWgHeyxZeippnqmquBkwHFmNOvcPfPkkLdYhhYSPcOPXnbSs" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "KWwdBietWJCbtDjMYqbZnBTYOfZiIBRkFWrBLSMtofmDzBXgVmVsFkPAHSJSgHZ" )
	.add("description", "apOnqye" )
	.add("lookup_key", "lukNXuQsISBAWVpHaaWJWMPHNQKoTGTgrxyUaokJccpgoONXPcdJDCNTNRoSNoG" )
	.add("alternate_lookup_key", "ayQvdarDIIPknCBuWgHeyxZeippnqmquBkwHFmNOvcPfPkkLdYhhYSPcOPXnbSs" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"KWwdBietWJCbtDjMYqbZnBTYOfZiIBRkFWrBLSMtofmDzBXgVmVsFkPAHSJSgHZ\",\"description\":\"apOnqye\",\"lookup_key\":\"lukNXuQsISBAWVpHaaWJWMPHNQKoTGTgrxyUaokJccpgoONXPcdJDCNTNRoSNoG\",\"alternate_lookup_key\":\"ayQvdarDIIPknCBuWgHeyxZeippnqmquBkwHFmNOvcPfPkkLdYhhYSPcOPXnbSs\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/227948117
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
https://api.INSTANCE.cardsavr.io/financial_institutions/227948117
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
https://api.INSTANCE.cardsavr.io/integrators/160487274
```

```javascript
const integrators = await session.getIntegrators(160487274);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(undefined);
```

```java
JsonValue integrators = session.get("/integrators", 160487274, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 160487274,
  "name": "MxqYuBBHtiercVrACZlmMwvkJBwmqhaujdWpxVwtvdjplhrwf",
  "description": "VWGYUAMbiqAYxskpBKlICmfxPFOWUYL",
  "current_key": "9eCy8EWp9NxPFYdsn8/ufVeF9TBO7kzVGmW0olrny4s=",
  "key_lifetime": 203,
  "next_rotation_on": "2015-04-05T14:53:46.762Z",
  "created_on": "1972-12-31T23:23:00.444Z",
  "last_updated_on": "1970-06-23T19:06:39.427Z"
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

**Example GET request path:**<br>`/integrators/160487274`

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
  "name": "MxqYuBBHtiercVrACZlmMwvkJBwmqhaujdWpxVwtvdjplhrwf",
  "description": "VWGYUAMbiqAYxskpBKlICmfxPFOWUYL",
  "current_key": "9eCy8EWp9NxPFYdsn8/ufVeF9TBO7kzVGmW0olrny4s=",
  "key_lifetime": 203,
  "next_rotation_on": "2015-04-05T14:53:46.762Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "MxqYuBBHtiercVrACZlmMwvkJBwmqhaujdWpxVwtvdjplhrwf" },
	{ "description", "VWGYUAMbiqAYxskpBKlICmfxPFOWUYL" },
	{ "current_key", "9eCy8EWp9NxPFYdsn8/ufVeF9TBO7kzVGmW0olrny4s=" },
	{ "key_lifetime", 203 },
	{ "next_rotation_on", "2015-04-05T14:53:46.762Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "MxqYuBBHtiercVrACZlmMwvkJBwmqhaujdWpxVwtvdjplhrwf" )
	.add("description", "VWGYUAMbiqAYxskpBKlICmfxPFOWUYL" )
	.add("current_key", "9eCy8EWp9NxPFYdsn8/ufVeF9TBO7kzVGmW0olrny4s=" )
	.add("key_lifetime", 203 )
	.add("next_rotation_on", "2015-04-05T14:53:46.762Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"MxqYuBBHtiercVrACZlmMwvkJBwmqhaujdWpxVwtvdjplhrwf\",\"description\":\"VWGYUAMbiqAYxskpBKlICmfxPFOWUYL\",\"current_key\":\"9eCy8EWp9NxPFYdsn8/ufVeF9TBO7kzVGmW0olrny4s=\",\"key_lifetime\":203,\"next_rotation_on\":\"2015-04-05T14:53:46.762Z\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
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
description | string | no
current_key | string | no
key_lifetime | number | no
next_rotation_on | date | no

See [integrator response attributes](#response-integrator).


## Update integrator

```javascript
const integrator = await session.updateIntegrator(1,{
  "name": "bdYqBVNcgvvTemkhbtBdZnutDciFEkxXenHAeZXDwiDwABgJR",
  "description": "ebPTniFFhgIDiGB",
  "current_key": "uBNVn3WVoBTWSM1Rdif5CaYJYt2d6mVNDiI5Y4S69fU=",
  "key_lifetime": 200,
  "next_rotation_on": "2021-08-05T17:50:07.060Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "bdYqBVNcgvvTemkhbtBdZnutDciFEkxXenHAeZXDwiDwABgJR" },
	{ "description", "ebPTniFFhgIDiGB" },
	{ "current_key", "uBNVn3WVoBTWSM1Rdif5CaYJYt2d6mVNDiI5Y4S69fU=" },
	{ "key_lifetime", 200 },
	{ "next_rotation_on", "2021-08-05T17:50:07.060Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "bdYqBVNcgvvTemkhbtBdZnutDciFEkxXenHAeZXDwiDwABgJR" )
	.add("description", "ebPTniFFhgIDiGB" )
	.add("current_key", "uBNVn3WVoBTWSM1Rdif5CaYJYt2d6mVNDiI5Y4S69fU=" )
	.add("key_lifetime", 200 )
	.add("next_rotation_on", "2021-08-05T17:50:07.060Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"bdYqBVNcgvvTemkhbtBdZnutDciFEkxXenHAeZXDwiDwABgJR\",\"description\":\"ebPTniFFhgIDiGB\",\"current_key\":\"uBNVn3WVoBTWSM1Rdif5CaYJYt2d6mVNDiI5Y4S69fU=\",\"key_lifetime\":200,\"next_rotation_on\":\"2021-08-05T17:50:07.060Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/160487274
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
https://api.INSTANCE.cardsavr.io/integrators/160487274
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
https://api.INSTANCE.cardsavr.io/merchant_sites/2112293263
```

```javascript
const merchantsites = await session.getMerchantSites(2112293263);
```

```csharp
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(undefined);
```

```java
JsonValue merchantsites = session.get("/merchant_sites", 2112293263, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2112293263,
  "name": "GsEkYPkotCySMFBZh",
  "host": "LYEkf",
  "tags": [
    "Z-",
    66,
    "d_sC~.uP*"
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
    "PHjVtCPMTuDe": "QlyL0",
    "UxXgRUglTpRN": 83,
    "mjuTmgQqnjHR": false
  },
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

#### Batch GET requests

**Batch requests** return the first page of all viewable merchant sites, filtered by any [query filters](#get-filters) listed in the path.

**Example batch GET request path:**<br>`/merchant_sites?ids=1,2`

#### Singular GET requests

**Singular requests** only return the merchant site matching the id provided in the path.

**Example GET request path:**<br>`/merchant_sites/2112293263`

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
https://api.INSTANCE.cardsavr.io/notifications/23188739
```

```javascript
const notifications = await session.getNotifications(23188739);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(undefined);
```

```java
JsonValue notifications = session.get("/notifications", 23188739, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 23188739,
  "name": "eEIHHYTUEAEpZOZhiNxKSbfRZTuZtehUkigkYtiTjYDNPjrxhWSTjbIFvVCCfXQ",
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
  "html_template": "FisPTUSJb",
  "text_template": "QjJZCZYLncxpiYHSkdzNi",
  "created_on": "2020-10-12T07:06:19.710Z",
  "last_updated_on": "2015-07-11T21:51:17.531Z",
  "financial_institution": {
    "id": 1554179967,
    "name": "FAydWuVbXlMlVWsdszjmwKKbzLeGyzYFlAAANqgpYXJCikfFSHrsQcrZoaaTABu",
    "description": "PGbjzlQBCeqIUDp",
    "lookup_key": "teLhoBJEHDIhDhsIemqsznyWSYpiyktZRycmQwdSdKqesVgCbAWGEnJpXYgUpqG",
    "alternate_lookup_key": "BJdhcbfFIlWtnEADxjPOKDxvGbYIHOdeTWilcvbBEvEgooxISaiTDKGfbSMDxoQ",
    "config": {
      "YVDzhxwiOLDe": "9h#y/!3lTtaOJV6[_MiE",
      "CshYrVhKaMeF": 42,
      "eqLbzFGquyKd": false
    },
    "created_on": "2012-05-06T12:34:19.512Z",
    "last_updated_on": "1978-09-21T20:49:53.855Z"
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

**Example GET request path:**<br>`/notifications/23188739`

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
  "financial_institution_id": 872000622,
  "name": "eEIHHYTUEAEpZOZhiNxKSbfRZTuZtehUkigkYtiTjYDNPjrxhWSTjbIFvVCCfXQ",
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
  "html_template": "FisPTUSJb",
  "text_template": "QjJZCZYLncxpiYHSkdzNi"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 872000622 },
	{ "name", "eEIHHYTUEAEpZOZhiNxKSbfRZTuZtehUkigkYtiTjYDNPjrxhWSTjbIFvVCCfXQ" },
	{ "type", "email" },
	{ "event", "merchant_site_updates_top" },
	{ "html_template", "FisPTUSJb" },
	{ "text_template", "QjJZCZYLncxpiYHSkdzNi" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 872000622 )
	.add("name", "eEIHHYTUEAEpZOZhiNxKSbfRZTuZtehUkigkYtiTjYDNPjrxhWSTjbIFvVCCfXQ" )
	.add("type", "email" )
	.add("event", "merchant_site_updates_top" )
	.add("html_template", "FisPTUSJb" )
	.add("text_template", "QjJZCZYLncxpiYHSkdzNi" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":872000622,\"name\":\"eEIHHYTUEAEpZOZhiNxKSbfRZTuZtehUkigkYtiTjYDNPjrxhWSTjbIFvVCCfXQ\",\"type\":\"email\",\"event\":\"merchant_site_updates_top\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"FisPTUSJb\",\"text_template\":\"QjJZCZYLncxpiYHSkdzNi\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/
```

### Path

POST /notifications

### Description

Create a notification and return the created object.

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
  "name": "fGHnCWtHpcloRwroflFzPGIbHDoxecaTrNdvCDBRaeaFtzXksStfmUHBgiTRKBl",
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
  "html_template": "tSHtUJcJBaFvbVjSpygGQJcIymCuEo",
  "text_template": "KYrLLWbColqKUtZvJ"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "fGHnCWtHpcloRwroflFzPGIbHDoxecaTrNdvCDBRaeaFtzXksStfmUHBgiTRKBl" },
	{ "type", "email" },
	{ "event", "session_complete" },
	{ "html_template", "tSHtUJcJBaFvbVjSpygGQJcIymCuEo" },
	{ "text_template", "KYrLLWbColqKUtZvJ" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "fGHnCWtHpcloRwroflFzPGIbHDoxecaTrNdvCDBRaeaFtzXksStfmUHBgiTRKBl" )
	.add("type", "email" )
	.add("event", "session_complete" )
	.add("html_template", "tSHtUJcJBaFvbVjSpygGQJcIymCuEo" )
	.add("text_template", "KYrLLWbColqKUtZvJ" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"fGHnCWtHpcloRwroflFzPGIbHDoxecaTrNdvCDBRaeaFtzXksStfmUHBgiTRKBl\",\"type\":\"email\",\"event\":\"session_complete\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"tSHtUJcJBaFvbVjSpygGQJcIymCuEo\",\"text_template\":\"KYrLLWbColqKUtZvJ\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/23188739
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
https://api.INSTANCE.cardsavr.io/notifications/23188739
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
https://api.INSTANCE.cardsavr.io/notification_results/119675834
```

```javascript
const notificationresults = await session.getNotificationResults(119675834);
```

```csharp
CardSavrResponse<NotificationResults> notificationresults = await session.GetNotificationResultsAsync(undefined);
```

```java
JsonValue notificationresults = session.get("/notification_results", 119675834, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 119675834,
  "last_attempt_date": "2009-02-10T23:40:46.215Z",
  "fi_lookup_key": "byBIrAASatTCsUFFJQaKGUkXvOQUNzjSTziZtKgQvTfQcgARfvIwlVpxSudnyFM",
  "cuid": "abcd1234",
  "status": "SUCCESSFUL",
  "attempts": 3,
  "notification_data": {
    "status_code": 200,
    "webhook_request": {
      "request_data": 123
    },
    "webhook_response": "OK"
  },
  "created_on": "1986-08-31T04:05:02.686Z",
  "last_updated_on": "1975-01-22T16:13:33.798Z",
  "notification": {
    "id": 617546682,
    "name": "SCTrhPBEsHpwFpWIAJpjLCnvIYKiqxwkNcEfyUUsSACXNNKhVGKHlToWgHAzeNO",
    "type": "webhook",
    "event": "session_complete",
    "config": {
      "GwgZncMpumIi": "l",
      "drNiPdAILzKm": 29,
      "avQGEYPqxPnp": true
    },
    "html_template": "bcWqTtlhGIPgDqE",
    "text_template": "UIQtQ",
    "created_on": "1994-01-21T12:21:18.614Z",
    "last_updated_on": "2010-08-21T13:08:31.792Z"
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

**Example GET request path:**<br>`/notification_results/119675834`

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
  "notification_id": 1521788594,
  "fi_lookup_key": "byBIrAASatTCsUFFJQaKGUkXvOQUNzjSTziZtKgQvTfQcgARfvIwlVpxSudnyFM",
  "cuid": "abcd1234",
  "status": "SUCCESSFUL",
  "attempts": 3,
  "notification_data": {
    "status_code": 200,
    "webhook_request": {
      "request_data": 123
    },
    "webhook_response": "OK"
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "notification_id", 1521788594 },
	{ "fi_lookup_key", "byBIrAASatTCsUFFJQaKGUkXvOQUNzjSTziZtKgQvTfQcgARfvIwlVpxSudnyFM" },
	{ "cuid", "abcd1234" },
	{ "status", "SUCCESSFUL" },
	{ "attempts", 3 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 1521788594 )
	.add("fi_lookup_key", "byBIrAASatTCsUFFJQaKGUkXvOQUNzjSTziZtKgQvTfQcgARfvIwlVpxSudnyFM" )
	.add("cuid", "abcd1234" )
	.add("status", "SUCCESSFUL" )
	.add("attempts", 3 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":1521788594,\"fi_lookup_key\":\"byBIrAASatTCsUFFJQaKGUkXvOQUNzjSTziZtKgQvTfQcgARfvIwlVpxSudnyFM\",\"cuid\":\"abcd1234\",\"status\":\"SUCCESSFUL\",\"attempts\":3,\"notification_data\":{\"status_code\":200,\"webhook_request\":{\"request_data\":123},\"webhook_response\":\"OK\"}}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notification_results/
```

### Path

POST /notification_results

### Description

Create a notification result and return the created object.

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

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}" -H "x-cardsavr-session-jwt: [JWT]"
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/965257869
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(965257869);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(undefined);
```

```java
JsonValue singlesitejobs = session.get("/place_card_on_single_site_jobs", 965257869, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 965257869,
  "status": "SUCCESSFUL",
  "status_message": "wTgsJErEegNCGTdgay",
  "termination_type": "BIILLABLE",
  "custom_data": {
    "JFGBIprzgxdL": ">YUdn.XaDChk@j*>O*13w<J",
    "XzhxrqUVMfbC": 15,
    "uudynUjHxpxl": false
  },
  "notification_sent": false,
  "time_elapsed": 1170360294,
  "started_on": "1988-07-14T08:46:22.267Z",
  "completed_on": "1987-08-22T04:06:38.314Z",
  "created_on": "1995-11-25T05:57:48.543Z",
  "last_updated_on": "2015-11-20T20:58:23.820Z",
  "cardholder": {
    "id": 1826188260,
    "financial_institution_id": 693803056,
    "agent_session_id": "ZRorbCjDaPKlDgbB",
    "type": "ephemeral",
    "first_name": "pvBBtBKtUUFUogYMV",
    "last_name": "mCvtG",
    "email": "rBLMSSWEqkUN@zVNFOH.pkP",
    "meta_key": "JII",
    "cardholder_safe_key": "A8etytahAnGXakuan4iujLbTZhQ7U89vfGC+AJ9DGmg=",
    "custom_data": {
      "ywVvAQvwXeqx": "pn(MvQ46~v^",
      "WzBcVdZvviYi": 1,
      "maTKqwzYSpYX": true
    },
    "created_on": "1973-09-11T11:39:20.602Z",
    "last_updated_on": "2010-03-12T00:58:36.103Z"
  },
  "cardsavr_card": {
    "id": 1813834253,
    "bin_id": 1308491145,
    "cvv": "lHZ",
    "expiration_month": "v",
    "expiration_year": "b",
    "name_on_card": "zOtGEOjAmrrinnuJBPZEAoSDMOZldlGarRmhNxqWtUKXhPKRugxMeAFNUdSgrOiLRoxMzGjHKbhpeStCByLueQulxYctBiscNxHcLtfgxYcYbTJMiZsMCRVVQVsJsZiDzSthXDurpADGAgpQiUlbhJaWDMKaVCHDxXcRYMOAolFgTZRIMugrszRjNtTUBqYXcfjlIOnYEPfmIOglBxHkALfhzvOiqMSgElmazEIxfNmVAiVRVpnMOzjVnyUpWE",
    "first_6": "vbDLmeLDukrQgCqbGTeMRZmrdfGGPVTV",
    "first_7": "yQiLyvSZgpFcyjxiHDfBKFxSzFpKmbZC",
    "first_8": "WajhTipQfNQdeSjhaQhQRnqJrFWzFlRx",
    "created_on": "1993-11-21T01:50:26.058Z",
    "last_updated_on": "2014-11-03T20:13:05.205Z"
  },
  "cardsavr_account": {
    "id": 1130681138,
    "last_card_placed_id": 660269852,
    "username": "zsKFuzwsFZpAjNPxoBipEgEGUdkjeaeANqTNUjfBpNlttcoqOBeXIAipKoZ",
    "username_hash": "ZvsyMjCBPtbOedjMMntnEfPJmvJRWIBJgPYXLUHtLvqtFVehQvAnQFYFJBX",
    "password": "FZkPGhBgVBsyFjMyvZRGlDfwHlAcSkjuimPWAzXngJFUIPtaTVzubrBduEo",
    "last_login": "2013-04-24T10:29:49.434Z",
    "last_password_update": "2004-08-05T17:22:00.835Z",
    "last_saved_card": "1993-06-08T06:13:57.079Z",
    "created_on": "2012-02-14T14:30:57.557Z",
    "last_updated_on": "1980-09-17T04:00:08.553Z"
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/965257869`

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
  "cardholder_id": 194593639,
  "card_id": 322578548,
  "account_id": 2142244906,
  "status": "SUCCESSFUL",
  "custom_data": {
    "JFGBIprzgxdL": ">YUdn.XaDChk@j*>O*13w<J",
    "XzhxrqUVMfbC": 15,
    "uudynUjHxpxl": false
  },
  "notification_sent": false,
  "time_elapsed": 1170360294,
  "started_on": "1988-07-14T08:46:22.267Z",
  "completed_on": "1987-08-22T04:06:38.314Z",
  "termination_type": "BIILLABLE"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 194593639 },
	{ "card_id", 322578548 },
	{ "account_id", 2142244906 },
	{ "status", "SUCCESSFUL" },
	{ "notification_sent", false },
	{ "time_elapsed", 1170360294 },
	{ "started_on", "1988-07-14T08:46:22.267Z" },
	{ "completed_on", "1987-08-22T04:06:38.314Z" },
	{ "termination_type", "BIILLABLE" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 194593639 )
	.add("card_id", 322578548 )
	.add("account_id", 2142244906 )
	.add("status", "SUCCESSFUL" )
	.add("notification_sent", false )
	.add("time_elapsed", 1170360294 )
	.add("started_on", "1988-07-14T08:46:22.267Z" )
	.add("completed_on", "1987-08-22T04:06:38.314Z" )
	.add("termination_type", "BIILLABLE" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":194593639,\"card_id\":322578548,\"account_id\":2142244906,\"status\":\"SUCCESSFUL\",\"custom_data\":{\"JFGBIprzgxdL\":\">YUdn.XaDChk@j*>O*13w<J\",\"XzhxrqUVMfbC\":15,\"uudynUjHxpxl\":false},\"notification_sent\":false,\"time_elapsed\":1170360294,\"started_on\":\"1988-07-14T08:46:22.267Z\",\"completed_on\":\"1987-08-22T04:06:38.314Z\",\"termination_type\":\"BIILLABLE\"}"
-X POST -H "Content-Type: application/json"
-H "x-cardsavr-cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/
```

### Path

POST /place_card_on_single_site_jobs

### Description

Create a single-site job and return the created object.

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
  "card_id": 2047620380,
  "status": "SUCCESSFUL",
  "custom_data": {
    "JwPOLjYZlRxd": "s_QB{mK",
    "yXkNQhbqnQmY": 62,
    "YbLbXApkdqQc": true
  },
  "notification_sent": true,
  "time_elapsed": 1708648182,
  "started_on": "2000-07-05T19:14:26.928Z",
  "completed_on": "2000-12-19T04:16:24.123Z",
  "termination_type": "BIILLABLE"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 2047620380 },
	{ "status", "SUCCESSFUL" },
	{ "notification_sent", true },
	{ "time_elapsed", 1708648182 },
	{ "started_on", "2000-07-05T19:14:26.928Z" },
	{ "completed_on", "2000-12-19T04:16:24.123Z" },
	{ "termination_type", "BIILLABLE" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 2047620380 )
	.add("status", "SUCCESSFUL" )
	.add("notification_sent", true )
	.add("time_elapsed", 1708648182 )
	.add("started_on", "2000-07-05T19:14:26.928Z" )
	.add("completed_on", "2000-12-19T04:16:24.123Z" )
	.add("termination_type", "BIILLABLE" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":2047620380,\"status\":\"SUCCESSFUL\",\"custom_data\":{\"JwPOLjYZlRxd\":\"s_QB{mK\",\"yXkNQhbqnQmY\":62,\"YbLbXApkdqQc\":true},\"notification_sent\":true,\"time_elapsed\":1708648182,\"started_on\":\"2000-07-05T19:14:26.928Z\",\"completed_on\":\"2000-12-19T04:16:24.123Z\",\"termination_type\":\"BIILLABLE\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/965257869
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/965257869
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

