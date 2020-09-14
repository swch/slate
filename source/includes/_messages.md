# Client Messages

## Subscribe to Status Updaates

> Before you can listen to a channel, you must first subscribe.  Unlike credential requests, multiple clients can listen to messages for the same job.

```javascript
const session = this.getSession(username);
const subscription = await session.registerForJobStatusUpdates(job_id);
//this key is necessary for all future requests
const key = subscription.body.access_key;
```

```csharp
//not implemented
```

```shell
#session must first be started, and must have permissions
curl -iv 
  -H "Content-Type: application/json" "https://api.INSTANCE.cardsavr.io/messages/place_card_on_single_site_jobs/123/broadcasts/registrations" 
  -H "trace: {\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
```

> access_key is required for all future requests for status updates.  Messages are returned as an array.  status is always job_status

```json
{
    "access_key": "erz5nk219FPZNWGv3AbHdA=="
}
```

### Path
GET /messages/place_card_on_single_site_jobs/job_id:/broadcasts/registrations

### Description
Registers a client to a broadcast message channel.  Messages are saved for an hour waiting for the client to poll.  Generally clients poll every 5 seconds.  Multiple clients can poll for messages for the same job, so each client has its own access key.  

<aside class="notice">
See the <a href="https://developers.strivve.com/resources/messaging">Messaging system document</a> for more details on how the messaging system is architected.
</aside>

## Get Status Updates

> The unique access key is returned for every broadcast message poll request

```javascript
const broadcast_probe = setInterval(async () => { 
    const update = await session.getJobStatusUpdate(job_id, subscription.body.access_key);
    if (update.status_code == 401) {
        clearInterval(broadcast_probe);
    } else if (update.body) {
        update.body.map((item: any) => {
            callback(item);   //process message "item"
            if (item.type === "job_status") {
                if (item.message.termination_type || item.message.percent_complete == 100) { //job is completed, stop probing
                    clearInterval(broadcast_probe);
                }
            }
        });
    }
}, 5000);
```

```csharp
Not implemented yet
```

```shell
#old_pass is not required for privileged admins.  Users must provide their old password
curl -iv -H "Content-Type: application/json" 
  "https://api.INSTANCE.cardsavr.io/messages/place_card_on_single_site_jobs/123/broadcasts/" 
  -H "cardsavr-messaging-access-key: erz5nk219FPZNWGv3AbHdA=="
  -H "trace: {\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
```

> Response is an array, as mutliple messages may be generated between polls.

```json
[
    {
        "type": "job_status",
        "message": {
            "job_timeout": 856058,
            "percent_complete": 30,
            "status": "AUTH"            
        },
        "job_id": 123
    },
    {
        "type": "job_status",
        "message": {
            "job_timeout": 855737,
            "percent_complete": 54,
            "status": "UPDATING"            
        },
        "job_id": 123
    }
]
```

### Path
GET /messages/place_card_on_single_site_jobs/job_id:/credential_requests

### Description
Grabs the status messages for this job.  If there are no messages, none are returned.  Since multiple messages may be returned, the body is an array of messages.  When jobs complete, the final message will have a "termination_type" with values:

Termination type | Description
---------------- | -----------
BILLABLE | Job completed successfully
USER_DATA_FAILURE | There was an issue with data supplied by the user like a TFA code or password
SITE_INTERACTION_FAILURE | Strivve's robot was unable to crawl the site
PROCESS_FAILURE | There was an internal system failure - these happen very rarely and should be escallated immediately

## Get Credential Requests

> Credential requests must be polled for using the job_id.  Permissions are established based on the role and the owner of the job.

```javascript
const request_probe = setInterval(async () => { 
    const request = await session.getJobInformationRequest(job_id);
    if (request.body) {
        callback(request.body); //callback is a function that processes the message.
    }
}, 5000);
```

```csharp
//not implemented
```

```shell
# With a shell, you must first establish a session, followed by 
# a login command.  Note that the cookies from the session call 
# must be passed into the login call. This ONLY works 
# with a development server that supports unsigned body requests. 
curl "https://api.INSTANCE.cardsavr.io/messages/place_card_on_single_site_jobs/123/broadcasts" 
  -H 
  -H "trace: {\"key\": \"my_trace\"}" -c ~/_cookies  
```

> The response contains a unique request envelope id which must be returned with the response.

```json
{
  "type": "tfa_request",
  "job_id": 101,
  "envelope_id": "uHsa6mI3GYO2ZwOf82SuaA=="
}
```

### Path

GET /messages/place_card_on_single_site_jobs/job_id:/credential_requests

### Description

Polls the server for requests from the virtual browser session.  This might be new credentials or a TFA code.  You must use the envelope_id that was returned with the initial request message.

## Post Credential Response

> Jobs wiill wait until a credential response is posted.

```javascript
const session = this.getSession(username); //session should already be loaded
session.sendJobInformation(job_id, envelope_id, "tfa_response", "1234");
```

```csharp
//not implemented
```

```shell
#session must first be started
curl -iv -X POST -d "{\"envelope_id\": \"uHsa6mI3GYO2ZwOf82SuaA==\", \"type\": \"tfa_request\", \"message\": \"1234\"}" 
  -H "Content-Type: application/json" "https://api.INSTANCE.cardsavr.io/messages/place_card_on_single_site_jobs/123/credential_responses" 
  -H "trace: {\"key\": \"my_trace\"}" -b ~/_cookies -c ~/_cookies
```

> The login call returns the user, along with a public key to be used to encrypt future requests

```json
{
  "type": "credential_response",
  "job_id": 101,
  "envelope_id": "uHsa6mI3GYO2ZwOf82SuaA==",
  "message": "submitted"
}
```

### Path

POST /messages/place_card_on_single_site_jobs/job_id:/credential_responses

### Description

Post the response to a TFA request or a bad credential request

<aside class="notice">
Credential resubmission messages notify the virtual browser session that credentials have been updated. The client application still needs to save the new credentials in the job safe by updating the account.
</aside>

### Body parameters

Parameter | Type | Required | Desription
-------- | ---- | --------- | ----------
envelope_id | string | yes | unique key associated with the original request
type | string | yes | credential_request or tfa_request
message | string | yes | "success" for credential resubmissions, and the tfa code entered by the user for TFA responses