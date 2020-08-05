# Accounts
An account object contains a CardSavr user's account information for a specific merchant site.
## Get account

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1133161,
  "last_card_placed_id": 1822467,
  "username": "jsmith123",
  "password": null,
  "last_login": "1992-10-27T18:08:46.607Z",
  "last_password_update": "2002-08-11T03:31:56.314Z",
  "last_saved_card": "1993-12-04T13:23:15.988Z",
  "created_on": "1974-04-19T09:48:36.764Z",
  "last_updated_on": "1972-03-11T21:56:49.849Z",
  "cardholder_id": 56338,
  "merchant_site_id": 5374900
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

> Sample request:

```json
{
  "cardholder_id": 56338,
  "merchant_site_id": 5374900,
  "last_card_placed_id": 1822467,
  "username": "jsmith123",
  "password": "Pa$$w0rd"
}
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


## Update account

> Sample request - /cardsavr_accounts/1133161 :

```json
{
  "last_card_placed_id": 9341076,
  "username": "jsmith123",
  "password": "Pa$$w0rd"
}
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


## Delete account

### Path

DELETE /cardsavr_accounts/{id}

### Description

Delete a account and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Addresses
Address objects contain billing address information for a particular user.
## Get address

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 259892,
  "address1": "NkxEtLQpPJuyRTTZqQsPAhaiFZLhoebwZdzQfiNjzKiKFQEGkjkbJMierToOeyllGCDMtYjmKOmnHgPZeMKLzwbaxVCdHhVQomH",
  "address2": "yFdfOxVYQLPwYKtDLqZjcYFDyRsNEjixcFntWEtjGwJoJIEklWeYXdsLZFhbrCsteqjyvOmeYLanaJQvvoKdDdzlbajRgMWUqcM",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true,
  "created_on": "2000-08-21T13:07:23.323Z",
  "last_updated_on": "2019-01-07T04:08:52.421Z",
  "user_id": 7358952,
  "password": null
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

> Sample request:

```json
{
  "user_id": 7358952,
  "address1": "NkxEtLQpPJuyRTTZqQsPAhaiFZLhoebwZdzQfiNjzKiKFQEGkjkbJMierToOeyllGCDMtYjmKOmnHgPZeMKLzwbaxVCdHhVQomH",
  "address2": "yFdfOxVYQLPwYKtDLqZjcYFDyRsNEjixcFntWEtjGwJoJIEklWeYXdsLZFhbrCsteqjyvOmeYLanaJQvvoKdDdzlbajRgMWUqcM",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": true
}
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

> Sample request - /cardsavr_addresses/259892 :

```json
{
  "address1": "PUBnGadDjWLeYRUtdAitvENNGYaxlpaOjuWgrPmioLmFdbqXmWjCEzdPkcAfiKGKskQePNEVEuBkiAZgLuaEcueTuCNkTCdLjVm",
  "address2": "pdjRDDlQsVPpomytiovIwcqSNTSIOodluyKKJQMlpSBfTjPkKCuQxETpYmZDaawEaAiAZjDiZPTiuwVhxIInIdVdEjrpRMXBDBj",
  "city": "Seattle",
  "subnational": "WA",
  "postal_code": "98177",
  "postal_other": "98177-0124",
  "country": "USA",
  "is_primary": false
}
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

### Path

DELETE /cardsavr_addresses/{id}

### Description

Delete a address and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Bins
A cardsavr_bin object
## Get bin

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 7268197,
  "financial_institution_id": 4148297,
  "brand": "ibtdEYMoswZUoRPCTJD",
  "issuer": "HStBmOsPfzDhJFDWjaCZDfuOefGBIRsCIMGRkDbvhmUONJooRTNJTdVtqlzjbfQKKDFXPiKWhNutqLrOZfSsCQiiVSBYxaKgPgp",
  "type": "QQxBWCjEfrWPBi",
  "level": "lhylfLoaCUomZEJhDXHfzGdSYQNRZroxGDpRdfpUGdpeClvpMINGioiUquvWcgzayLLLbwLzjDdHTXdhgXwOwqbTcYnOMJXQJgR",
  "created_on": "1988-09-22T05:46:23.039Z",
  "last_updated_on": "2016-12-08T10:51:57.504Z",
  "bank_identification_number": "40659210",
  "password": null
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

> Sample request:

```json
{
  "financial_institution_id": 4148297,
  "bank_identification_number": "40659210",
  "brand": "ibtdEYMoswZUoRPCTJD",
  "issuer": "HStBmOsPfzDhJFDWjaCZDfuOefGBIRsCIMGRkDbvhmUONJooRTNJTdVtqlzjbfQKKDFXPiKWhNutqLrOZfSsCQiiVSBYxaKgPgp",
  "type": "QQxBWCjEfrWPBi",
  "level": "lhylfLoaCUomZEJhDXHfzGdSYQNRZroxGDpRdfpUGdpeClvpMINGioiUquvWcgzayLLLbwLzjDdHTXdhgXwOwqbTcYnOMJXQJgR"
}
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

> Sample request - /cardsavr_bins/7268197 :

```json
{
  "financial_institution_id": 9476000,
  "brand": "LpXJiSPXQgqJJiFpNZX",
  "issuer": "ZPeJnUyaXAMZMHIFldTOQXoapxempWPigLVzWptbNangrdYoBwluJUmJLSIUeUyrnqDGBXRsYTzvmZMryhtUyMgMSAMsmprUHCy",
  "type": "EvPgHbNfRpLmoH",
  "level": "AuUJYSrVpBpuswEjsVmwEEaSecxcMUibQQbpSBhlJJuCUWwGsjLahSHLTMlUDzaCkzcBTXYyuVkVjeMwiwhjVixBDVVqMmVfERJ"
}
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

### Path

DELETE /cardsavr_bins/{id}

### Description

Delete a bin and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Cards
Card objects contain information about a payment card belonging to a single cardholder. Card objects are used to populate users' payment information on merchant sites.
## Get card

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 5306051,
  "address_id": 3087022,
  "bin_id": 2564497,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "first_6": "obpOEnBDByazIDwnyWiYdTsZsGPtokru",
  "first_7": "tAcEsUdzjhbIhnMTBclACIHCrnPCsnlv",
  "first_8": "WjyjVgHCKLMpuNxBNCOEBxGsazcEvcsj",
  "created_on": "2010-12-02T23:43:18.418Z",
  "last_updated_on": "2005-07-24T02:29:59.595Z",
  "expiration_month": 1,
  "expiration_year": 31,
  "cardholder_id": 533114,
  "par": "pctsGOBKQZqIntSJhdzXikpvQCRFb",
  "pan": "TktEBOUPHWoQZos",
  "cvv": "GXm",
  "password": null
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

> Sample request:

```json
{
  "cardholder_id": 533114,
  "address_id": 3087022,
  "bin_id": 2564497,
  "par": "pctsGOBKQZqIntSJhdzXikpvQCRFb",
  "pan": "TktEBOUPHWoQZos",
  "cvv": "GXm",
  "expiration_month": 1,
  "expiration_year": 31,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith"
}
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


## Update card

> Sample request - /cardsavr_cards/5306051 :

```json
{
  "address_id": 8572843,
  "bin_id": 8737732,
  "name_on_card": "Joe C Smith",
  "first_name": "Joe",
  "last_name": "Smith",
  "expiration_month": 1,
  "expiration_year": 31
}
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

### Path

DELETE /cardsavr_cards/{id}

### Description

Delete a card and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Users
User objects correspond to a single CardSavr user.
## Get user

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 7408104,
  "financial_institution_id": 7821878,
  "last_password": "hVaGwR133rxGXZznBh+XIH8omOypk9/6Wun+eftW6+A=",
  "password": null,
  "next_password": "xPX8PrtCJSewUBrkgD0ntLjutqZZhfgRdjOaeFXqKSw=",
  "expired_password_1": "GpjqtmBG/9BqBq80JuJZM1ggCxgQUF31kGCJSOCH9bY=",
  "expired_password_2": "K7bCPoo1r4HoiFA9/8HCDjzwZfC2K6KKrYc+8xT0G80=",
  "cardholder_safe_key": "cJV6lNovsl+FdU27pUBTsEP9MlVugj1UrGEPuVL0d2I=",
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1993-04-27T13:33:19.594Z",
  "is_locked": true,
  "password_lifetime": 113,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "developer",
  "phone_number": "UtUuwzgUcIrXfJ",
  "custom_data": {
    "oopCMPpaDsWq": "4kYyV(&hd.3(sHTLb=azen0DdZwE",
    "rtBfGOzkxXoo": 44,
    "FKjIWXnwnIeU": true
  },
  "next_rotation_on": "1990-01-12T08:35:49.011Z",
  "created_on": "1977-04-23T08:55:25.724Z",
  "last_updated_on": "1998-12-24T09:48:39.689Z",
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

> Sample request:

```json
{
  "financial_institution_id": 7821878,
  "username": "jsmith123",
  "password": "Pa$$w0rd",
  "next_password": "xPX8PrtCJSewUBrkgD0ntLjutqZZhfgRdjOaeFXqKSw=",
  "cardholder_safe_key": "cJV6lNovsl+FdU27pUBTsEP9MlVugj1UrGEPuVL0d2I=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 113,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "developer",
  "phone_number": "UtUuwzgUcIrXfJ",
  "custom_data": {
    "oopCMPpaDsWq": "4kYyV(&hd.3(sHTLb=azen0DdZwE",
    "rtBfGOzkxXoo": 44,
    "FKjIWXnwnIeU": true
  },
  "next_rotation_on": "1990-01-12T08:35:49.011Z"
}
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


## Update user

> Sample request - /cardsavr_users/7408104 :

```json
{
  "financial_institution_id": 387589,
  "password": "Pa$$w0rd",
  "next_password": "lmIm2764SjObr/Q1PmWEyjAwzPY/mZnrdtiURJe9spY=",
  "cardholder_safe_key": "n/gsdoGyMbubsUtmpc6glhue23fSqOyAEJD6fqaYHjg=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 345,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "analyst",
  "phone_number": "LEHBncxSEirviu",
  "custom_data": {
    "ujaDjAYzySfs": "L!F3h%Lb*Rs@XzO}K",
    "DzsUeWlGRpNW": 55,
    "LOIiqdqkmODN": false
  },
  "next_rotation_on": "2015-04-03T14:17:41.653Z",
  "username": "jsmith123"
}
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


## Delete user

### Path

DELETE /cardsavr_users/{id}

### Description

Delete a user and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Financial Institutions
A CardSavr Financial Institution that can be associated with jobs and users.
## Get financial institution

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 948153,
  "name": "sUJzLqMGspQAVsGaIfnEhiTnENbnLdXtjdazAYoBMwNpOIRRkeAKTuevcnSAfVS",
  "description": "pnmzFPwBhegdFEAoyzuNVbHxdBWhX",
  "lookup_key": "POlCIJvMMPSweDGMvhPDVdelNGZqlBFUyLUifjQAUIbXQedCtrAyQPKCeGGzvZg",
  "alternate_lookup_key": "MCfAALULVJLReCROQANTVxsYNvzVOQRXBtlmypPElRfIlWxkRrwCHjyiGXtyLev",
  "created_on": "2004-06-13T18:18:33.830Z",
  "last_updated_on": "2020-06-10T14:00:56.824Z",
  "password": null
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

> Sample request:

```json
{
  "name": "sUJzLqMGspQAVsGaIfnEhiTnENbnLdXtjdazAYoBMwNpOIRRkeAKTuevcnSAfVS",
  "description": "pnmzFPwBhegdFEAoyzuNVbHxdBWhX",
  "lookup_key": "POlCIJvMMPSweDGMvhPDVdelNGZqlBFUyLUifjQAUIbXQedCtrAyQPKCeGGzvZg",
  "alternate_lookup_key": "MCfAALULVJLReCROQANTVxsYNvzVOQRXBtlmypPElRfIlWxkRrwCHjyiGXtyLev"
}
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

> Sample request - /financial_institutions/948153 :

```json
{
  "name": "MJDLEeaMeLrDALAORhypsiVFYOVfXhfIxLwJVwizbGKnxVApDEhceebNpMbLAwP",
  "description": "cSCHmRBoJUMjgrtUVlGnoooSaUhuU",
  "lookup_key": "ckXXWGOGcyfRWdqaeHGWViKEtwxYVyqKKvvdMrEdmbvenMmZeBFGGQjeIlIqYlH",
  "alternate_lookup_key": "LLfZGLBvDPNYlBCOzOOrGfPHxfMFchmagGhTMTalkSwXRqABlJpkTRXVLcHBeLn"
}
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

### Path

DELETE /financial_institutions/{id}

### Description

Delete a financial institution and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Integrators
An integrator object represents an integrator that implements CardSavr.
## Get integrator

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 7302814,
  "name": "wDrWZimjVFoTyzxxzdENIkhXORuFhOQIeqRpaMvNLjhCaWiKC",
  "integrator_type": "cust_internal",
  "description": "SwVbEij",
  "last_key": "BdUl/G65xxOoMmwO4ZHiDK2HXQXjMWcG4bn7pXX5iRA=",
  "current_key": "JUWo10x4IBGbdAiYCRc0YXZ7Wzo2MPtGJoz1+1EdDX0=",
  "next_key": "3irQfmwKax9A1hmYHZh51wuZnqxepmu2VGEcHh+rKz0=",
  "key_lifetime": 139,
  "next_rotation_on": "1992-09-14T08:57:34.772Z",
  "created_on": "2002-07-04T01:02:15.102Z",
  "last_updated_on": "2011-05-28T08:58:15.499Z",
  "password": null
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

> Sample request:

```json
{
  "name": "wDrWZimjVFoTyzxxzdENIkhXORuFhOQIeqRpaMvNLjhCaWiKC",
  "integrator_type": "cust_internal",
  "description": "SwVbEij",
  "last_key": "BdUl/G65xxOoMmwO4ZHiDK2HXQXjMWcG4bn7pXX5iRA=",
  "current_key": "JUWo10x4IBGbdAiYCRc0YXZ7Wzo2MPtGJoz1+1EdDX0=",
  "next_key": "3irQfmwKax9A1hmYHZh51wuZnqxepmu2VGEcHh+rKz0=",
  "key_lifetime": 139,
  "next_rotation_on": "1992-09-14T08:57:34.772Z"
}
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

> Sample request - /integrators/7302814 :

```json
{
  "name": "QwLWzaBpkBQAwdbOaqVtiTBBSYRhFPSzZfAYDnOHMrvhzPhEi",
  "integrator_type": "application",
  "description": "jdUaAsuVQLOJKinMwECwwjn",
  "last_key": "0BHEuKy0yBc4G099agJbRXnHZ26nHw6x/ieTHeBerfc=",
  "current_key": "hE6YlglNNrHNdJZmeDVrCMlHD04Zmi4YHVzit2jZpPA=",
  "next_key": "LLkYTTIPnjjf3ymr26k4SkP4Uj1LHUhadlpaQqynuro=",
  "key_lifetime": 353,
  "next_rotation_on": "2009-09-09T09:43:35.536Z"
}
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

### Path

DELETE /integrators/{id}

### Description

Delete a integrator and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Merchant Sites
Merchant site objects contain information about CardSavr-supported merchant sites.
## Get merchant site

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 9984429,
  "name": "XmaxjlVUaOCMpMdcjUTRCHDNq",
  "host": "zWHETLuyDWRVvEWbuMCozDPD",
  "image_lookup_key": "dJnwzGuNKhYwlNoIPp",
  "images": [
    {
      "vpGljWqgZeIQ": "]b^4X/EqPP{u#Ez5QH8v-{H^AykEII",
      "zrDyFIqriKhX": 84,
      "tvvHkgXUNFXN": false
    },
    {
      "wqyAaAuonlCF": "&y>6[ZHvHff41{%]scUv),ID)[8",
      "lipwrVRRVQTK": 56,
      "vTmhcOwCMrDe": false
    },
    {
      "ugBGiosgPGRO": "6wS5zIL8/eEns=u!",
      "RYEbEihbepbn": 43,
      "AGDmfaRxEdoD": true
    }
  ],
  "mfa": false,
  "tags": "rUNwUpkjDGPPH",
  "login": {
    "TxbboHcbFQSl": "]s)2",
    "RyOxYbEsKZRf": 83,
    "FycnKKdXBpbm": false
  },
  "password": null
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

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 4170112,
  "name": "UqQuHMVGSwmzjGepFdiczpcBZLuaDUHrjUueZNFdxNGvUzcOdPOCKXUDUcVPVoJ",
  "type": "webhook",
  "config": {
    "OJiARJSKnfed": "TIf,qZ7N=1Cs,X^sBL~#3^N,8{(",
    "mHjTGTgBPwyZ": 54,
    "daAMrDuSmEce": false
  },
  "created_on": "1989-12-29T01:28:28.755Z",
  "last_updated_on": "1989-08-03T01:16:22.468Z",
  "financial_institution_id": 1616096,
  "password": null
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

> Sample request:

```json
{
  "financial_institution_id": 1616096,
  "name": "UqQuHMVGSwmzjGepFdiczpcBZLuaDUHrjUueZNFdxNGvUzcOdPOCKXUDUcVPVoJ",
  "type": "webhook",
  "config": {
    "OJiARJSKnfed": "TIf,qZ7N=1Cs,X^sBL~#3^N,8{(",
    "mHjTGTgBPwyZ": 54,
    "daAMrDuSmEce": false
  }
}
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

> Sample request - /notifications/4170112 :

```json
{
  "name": "BgyDKEnNaTTNSYYAPQLEzYkqRZOIEzYpIGoMSqsThJSXHjqBiAZoJTnnwMUFjzP",
  "type": "webhook",
  "config": {
    "nlRlbHaasfgV": "nKSMQN3xx,nZ*~dC$B<oWK[l,,f",
    "SsSGXbeCxDql": 89,
    "yjINyVXyXSwe": false
  }
}
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

### Path

DELETE /notifications/{id}

### Description

Delete a notification and purge its [related items](#cascading-delete).  An id is required on every delete request.

# Single-site jobs
A place_card_on_single_site_job object
## Get single-site job

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2433487,
  "card_placement_result_id": "wztaQGCcdS",
  "status": "TOO_MANY_LOGIN_FAILURES",
  "safe_blob": "ZjNEEJJwD",
  "safe_nonce": "SmsWZvWuhlHZX",
  "custom_data": {
    "wYdOOXCkCTfw": "s+v9[p-Fd}KquapCnBVY^n.PY[u8[*",
    "WKEwqBMUTqra": 35,
    "WlsLHBQYlUwN": false
  },
  "failure_reason": "GPwuRZipEAAAQ",
  "messaging_addresses": "lu",
  "current_state": "BlbjLanEZvKzjxDrHjQjIpvIdJogoBvxnLOgVJkvEvgmhPLkXWRSoFnvKgKLfcU",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 4725768,
  "job_ready_on": "1979-12-13T14:40:18.589Z",
  "started_on": "1992-04-21T17:09:00.468Z",
  "completed_on": "2012-09-02T09:08:45.440Z",
  "expiration_date": "2020-02-09T08:16:23.707Z",
  "created_on": "2016-10-12T02:32:39.255Z",
  "last_updated_on": "1971-05-14T04:41:50.612Z",
  "place_card_on_multiple_sites_job_id": 1455640,
  "user_id": 6784662,
  "card_id": 966112,
  "account_id": 7781302,
  "password": null
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

> Sample request:

```json
{
  "place_card_on_multiple_sites_job_id": 1455640,
  "user_id": 6784662,
  "card_id": 966112,
  "account_id": 7781302,
  "status": "TOO_MANY_LOGIN_FAILURES",
  "custom_data": {
    "wYdOOXCkCTfw": "s+v9[p-Fd}KquapCnBVY^n.PY[u8[*",
    "WKEwqBMUTqra": 35,
    "WlsLHBQYlUwN": false
  },
  "failure_reason": "GPwuRZipEAAAQ",
  "current_state": "BlbjLanEZvKzjxDrHjQjIpvIdJogoBvxnLOgVJkvEvgmhPLkXWRSoFnvKgKLfcU",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 4725768,
  "started_on": "1992-04-21T17:09:00.468Z",
  "completed_on": "2012-09-02T09:08:45.440Z",
  "expiration_date": "2020-02-09T08:16:23.707Z"
}
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

> Sample request - /place_card_on_single_site_jobs/2433487 :

```json
{
  "status": "UNSUCCESSFUL",
  "custom_data": {
    "BKddZUfjItJj": "q6vHJ7QRi8L@oXk(",
    "nmbUDWmhFfgW": 95,
    "BKcJzGRYmNNd": false
  },
  "failure_reason": "NCdaAonmGXqrQHHqQopYRCEOBNKRQKrH",
  "current_state": "yLpWOPYomkqkkTspVVkuiPxNUoyBYurIdcTIowfsGyvZqRFoUgUVxiWIVPsFjww",
  "do_not_queue": true,
  "user_is_present": false,
  "time_elapsed": 4077803,
  "started_on": "1971-08-12T12:12:22.921Z",
  "completed_on": "2001-03-12T02:20:29.216Z",
  "expiration_date": "1993-09-02T23:48:56.134Z"
}
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

### Path

DELETE /place_card_on_single_site_jobs/{id}

### Description

Delete a single-site job and purge its [related items](#cascading-delete).  An id is required on every delete request.

