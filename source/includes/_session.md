# Grants and Passwords

## Get user credential grant

> Credential grants are very important for handing off responbility to a downstream client.  The grants must be provisioned by a user that caan create grants (like a cardholder_agent), and the grant is one time use for 3 minutes.

```javascript
const { CardsavrSession } = require() "@strivve/strivve-sdk/lib/cardsavr/CardsavrJSLibrary-2.0";

//agent_session is the session of a cardholder agent.  Cardholder agents are lower 
//privileged agents that can issue grants for cardholder accounts.
const grant_response_login = await agent_session.getCredentialGrant(cardholder_id);
const grant = grant_response_login.body.user_credential_grant;
```

```csharp
using Switch.CardSavr.Http;

CardSavrResponse<CredentialGrant> grantCardholder = await agentSession.client.CreateUserGrantAsync(cardholderId);
string grant = grantCardholder.Body.user_credential_grant;
```

```shell
#session must first be started, and must have permissions to create grants
curl -iv 
  -H "Content-Type: application/json" "https://api.INSTANCE.cardsavr.io/cardsavr_users/:id/credential_grant" 
  -H "trace: {\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
```

> Grants are always 38 characters, are one time use, and expire after 3 minutes.

```json
{
    "user_credential_grant": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9ey"
}
```

### Path
GET /cardsavr_users/:id/credential_grant

### Description
Returns a credential grant for specified user. This grant can be included with a login call ONCE within three minutes of being created.

## Update user password

> Password updates for non-agents must supply the old_password

```javascript
const { CardsavrSession } = require() "@strivve/strivve-sdk/lib/cardsavr/CardsavrJSLibrary-2.0";

await session.updatePassword(user_id, { password : new_password, password_copy : new_password});
```

```csharp
using Switch.CardSavr.Http;

PropertyBag bag = new PropertyBag();
bag["old_password"] = old_password;
bag["password"] = new_password;
bag["password_copy"] = new_password;

CardSavrResponse<PropertyBag> result = await http.UpdateUserPasswordAsync(user_id, bag);
```

```shell
#old_pass is not required for privileged admins.  Users must provide their old password
curl -iv  -d "{\"password\": \"3ysXPhntmPDU7xUFYKbc/4Aq=WVrhExdjHQsx5FgV2pZ\", 
  \"password_copy\": \"3ysXPhntmPDU7xUFYKbc/4Aq=WVrhExdjHQsx5FgV2pZ\"}" 
  -H "Content-Type: application/json" "https://api.INSTANCE.cardsavr.io/cardsavr_users/:id/credential_grant" 
  -H "trace: {\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
```

> Grants are always 38 characters, are one time use, and expire after 3 minutes.

```json
{
    "successs": true
}
```

### Path
PUT /cardsavr_users/:id/update_password

### Description
Updates CardSavr user password key. Partners are responsible for rotating their agent role password keys every 90 days. Cardholder roles cannot have passwords and must log in using credential grants.

<aside class="notice">
Most password updates can be done via the [Partner Portal](https://developers.strivve.com/resources/partner-portal/), however customer_agent and cardholder_agent password are the responsibility of the partner to rotate.
</aside>

### Body parameters

Parameter | Type | Required | Desription
--------- | ---- | -------- | ----------
password | string | yes | New password key
password_copy | string | yes | copy of new password key
old_password | string | not always | Privileged accounts can reset users' passwords without the old key

# Session

Session endpoints are used for session initiation, login, and termination.

> All sessions must first be started to initialize with the salt:

```javascript
const { CardsavrSession } = require() "@strivve/strivve-sdk/lib/cardsavr/CardsavrJSLibrary-2.0";

const session = new CardsavrSession(cardsavr_server, 
    app_key, app_name, username, password);
//session.init() calls both start AND login
const login_data = await session.init();
```

```csharp
using Switch.CardSavr.Http;

CardSavrHttpClient session = new CardSavrHttpClient(_cardsavrServer, 
  _appKey, _appName, userName, password);
//session.Init() calls both start AND login
CardSavrResponse<LoginResult> login = await session.Init();
```

```shell
# With a shell, you must first establish a session, followed by 
# a login command.  Note that the cookies from the session call 
# must be passed into the login call. This ONLY works 
# with a development server that supports unsigned body requests. 
curl "https://api.INSTANCE.cardsavr.io/session/start" 
  -H "trace: {\"key\": \"my_trace\"}" -c ~/_cookies  
```

> The SDK calls save the sessionSalt for future use

```json
{
  "sessionSalt": "kz2R3qexAkZqhoCalnNX9+6CLAMZ+"
}
```

## Start a CardSavr session

### Path
GET /session/start/

### Description

Starts new CardSavr session. Returns a session salt to be used for [user-login](#login).

## User login

> To authorize, a session initialization followed by a login call is required:

```javascript
const { CardsavrSession } = require() "@strivve/strivve-sdk/lib/cardsavr/CardsavrJSLibrary-2.0";

const session = new CardsavrSession(cardsavr_server, 
    app_key, app_name, username, password);
const login_data = await session.init();
```

```csharp
using Switch.CardSavr.Http;

CardSavrHttpClient session = new CardSavrHttpClient(_cardsavrServer, 
  _appKey, _appName, userName, password);
CardSavrResponse<LoginResult> login = await session.Init();
```

```shell
#session must first be started
curl -iv -d "{\"password\": \"PASSWORD\", \"userName\": \"USERNAME\"}" 
  -H "Content-Type: application/json" "https://api.INSTANCE.cardsavr.io/session/login" 
  -H "trace: {\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
```

> The login call returns the user, along with a public key to be used to encrypt future requests

```json
{
  "serverPublicKey": "sample_public_key",
  "status": "valid_password",
  "success": true,
  "user_id": 123,
  "user": 
  {
    "id": 123,
    "username": "john_smith_123",
    "first_name": "John",
    "last_name": "Smith",
    "email": "jsmith@email.com",
    "is_locked": true,
    "role": "dev",
    "created_on": "2018-04-19T23:10:36.657Z",
    "last_updated_on": null
  }
}
```

### Path
POST /session/login

### Description

Login user into a CardSavr session

### Body parameters

Parameter | Type | Required | Desription
-------- | ---- | --------- | ----------
clientPublicKey | string | yes | The public key issued by Strivve
userName | string | yes | user name for this user
signedSalt | string | yes | Salt returned from the [session start](#start-a-cardsavr-session) call
password | string | no | User's password -- this is required unless uisng a credential grant
userCredentialGrant | string | no | Grant issued by agent -- this is required unless using a password

## End session

```javascript
const { CardsavrSession } = require() "@strivve/strivve-sdk/lib/cardsavr/CardsavrJSLibrary-2.0";

await session.end();
//or if using the CardsavrHelper, the cache must be cleaned up
//await helper.endSession(username);
```

```csharp
using Switch.CardSavr.Http;

await client.EndAsync();
//or if using CardSavrHelper, you need to release the session from the cache
//await helper.CloseSession(userName);
```

```shell
#session must first be started
curl -iv -d -H "Content-Type: application/json" "https://api.INSTANCE.cardsavr.io/session/end" 
  -H "trace: {\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
```

> Session end returns a 200 with no body

### Path

GET /session/end/

### Description

Ends the current user session.



