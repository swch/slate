
# Card Placement Results
Card Placement results are a flatted version of the jobs and its publily available meta data. Although sensitive data like the PAN and account creds are not available, all the details of the job are captured here for future reference after the corresponding entities may have been deleted.
## Get card placement result

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/card_placement_results/931320305
```

```javascript
const cardplacementresults = await session.getCardPlacementResults(931320305);
```

```csharp
CardSavrResponse<CardPlacementResults> cardplacementresults = await session.GetCardPlacementResultsAsync(undefined);
```

```java
JsonValue cardplacementresults = session.get("/card_placement_results", 931320305, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 931320305,
  "merchant_site_hostname": "amazon.com",
  "meta_key": "MB9810411",
  "fi_name": "ACME Bank",
  "bank_identification_number": "60529289",
  "cuid": "abcd1234",
  "par": "MoNeosrGpuSdImbnoKODPUqXUpPrn",
  "card_customer_key": "NA",
  "account_customer_key": "1$abcd1234",
  "status": "SUCCESSFUL",
  "status_message": "WgdkLENVXZlvHVt",
  "termination_type": "BIILLABLE",
  "custom_data": {
    "gqjYNJzzBwlm": "^Wb>-{bk(L6>rlcKS)i9_-i+*Dn*}G",
    "HRxeDaWuSwob": 40,
    "JlBxCLklIyvY": true
  },
  "time_elapsed": 1770508573,
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "trace": "xSEwRHSzQUHpljFrJlremGRXoaqTekKDDSqfkzWIKwOYWlwZXsvfuJhPzMRCYZjotSozsYoAkpbYjpuLQnVcvmmoDgDOxrnSYymLWATryspHTarLpNieIxQBjHFyczwtRqYtmgIlKTNuTOBRhelFjZULTemyYnFnbKciokdQBOZWrtXiaKRypbDugdRxxFbrZWkhWPSUlIPHckqpfFwUwAXeHZluCpesuZAPoGiYvVIFenuKXqwdbcLmPVLplj",
  "email_sent": true,
  "completed_on": "1981-11-21T10:30:12.133Z",
  "created_on": "1983-10-05T09:12:16.577Z",
  "last_updated_on": "2001-05-24T08:36:23.863Z",
  "financial_institution": {
    "id": 1964561665,
    "name": "NVLCpODaHQbZyBnLGmaVpqXYOTfHjnqIPpJUOQLcnZhGGKazGVbYHBmyBNcpSlW",
    "description": "kMPfmmvRT",
    "lookup_key": "jaLOrCapGzUggGlyQhKDTNCEuAjQgjsEpEwcGPdSEPbbtnEoMniVprSDcmWIDjU",
    "alternate_lookup_key": "daZRoVnbVhvbSeRAZzmXDWhgueudazLIwBIHphJjrLaXkLMUAVMRAqKqPPAYszA",
    "config": {
      "WyVDeFzQKpyA": "TWuGAw",
      "OCJYJZNLxKLv": 5,
      "EmBJzmsSuNAE": false
    },
    "created_on": "2018-06-22T10:23:32.041Z",
    "last_updated_on": "1999-05-06T23:14:47.601Z"
  },
  "merchant_site": {
    "id": 2033715086,
    "name": "nlqKQNiVMrw",
    "host": "XQgznGbnVfABbceOtioNFHlfQxJdsI",
    "tags": [
      ">$)%s{DzB50gB9lR{.Qbu6n)/4uy",
      77,
      "17[%J816Z6^"
    ],
    "queue_name": "vbs_queue",
    "required_form_fields": [
      ")wD#^96kJo]>ZYVLlbSsT]n^#-+w_",
      42,
      "6"
    ],
    "images": [
      {
        "vGmdfJHDdywm": "o4Miji,>a=xyEX#CNFDD",
        "kWeqcayqLsfv": 90,
        "yIlvqFgQrIvL": false
      },
      {
        "UzBBoDRdoSLK": "JVauAD(rn}wY[V%4c5FylYGA",
        "LvBiqFskvVXs": 96,
        "MSNiUIXoHfpO": true
      },
      {
        "vTwTixvwvlIb": "Mza2-+FJ9Z+aL",
        "BAEKdiKTjhym": 21,
        "eQKdYUfozsXm": true
      }
    ],
    "account_identification": {
      "aLragIskvdxb": "Ipn%1Fb{}",
      "tBdKOAmjfFbX": 77,
      "pnILCAWdCoCv": false
    },
    "messages": {
      "mpOzKwtiMprS": "A0~6.",
      "LMQaDMRgfPGw": 45,
      "eZTMEKezQsIv": false
    },
    "mfa": true,
    "move_mouse_to_element": true,
    "proxy_order": [
      "ebOS#G",
      90,
      "bO5RL~7GP[kB7P9%>W~uDPxV%lgm"
    ],
    "credit_card_page": "ObrRjXYBslwBXOerER",
    "forgot_password_page": "hzpwTNyxG",
    "quick_start": false,
    "login_page": "lHkEAQMKmBCXPaKa",
    "login": {
      "OlwRsEbaHDVu": "kF9o~4b4%flkRs$",
      "JRzirKuVQVej": 83,
      "OQgETTMpJQMR": false
    }
  },
  "cardsavr_bin": {
    "id": 1839596029,
    "financial_institution_id": 1649407600,
    "custom_data": {
      "NCGCmKaAoJvo": "CM,MS#0Ug.VmAe[Wn@<EcIzlf.WP]",
      "kdcfRmGsPOzt": 8,
      "yJVJGKGPTJTc": false
    },
    "created_on": "1984-09-20T20:17:19.799Z",
    "last_updated_on": "2011-07-17T06:26:13.532Z"
  },
  "place_card_on_single_site_job_id": 1605373370
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

**Example GET request path:**<br>`/card_placement_results/931320305`

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
  "bank_identification_number": "60529289",
  "cuid": "abcd1234",
  "par": "MoNeosrGpuSdImbnoKODPUqXUpPrn",
  "card_customer_key": "NA",
  "account_customer_key": "1$abcd1234",
  "status": "SUCCESSFUL",
  "status_message": "WgdkLENVXZlvHVt",
  "termination_type": "BIILLABLE",
  "custom_data": {
    "gqjYNJzzBwlm": "^Wb>-{bk(L6>rlcKS)i9_-i+*Dn*}G",
    "HRxeDaWuSwob": 40,
    "JlBxCLklIyvY": true
  },
  "time_elapsed": 1770508573,
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "trace": "xSEwRHSzQUHpljFrJlremGRXoaqTekKDDSqfkzWIKwOYWlwZXsvfuJhPzMRCYZjotSozsYoAkpbYjpuLQnVcvmmoDgDOxrnSYymLWATryspHTarLpNieIxQBjHFyczwtRqYtmgIlKTNuTOBRhelFjZULTemyYnFnbKciokdQBOZWrtXiaKRypbDugdRxxFbrZWkhWPSUlIPHckqpfFwUwAXeHZluCpesuZAPoGiYvVIFenuKXqwdbcLmPVLplj",
  "place_card_on_single_site_job_id": 1605373370,
  "financial_institution_id": 832491634,
  "merchant_site_id": 1879337533,
  "email_sent": true,
  "completed_on": "1981-11-21T10:30:12.133Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "merchant_site_hostname", "amazon.com" },
	{ "meta_key", "MB9810411" },
	{ "fi_name", "ACME Bank" },
	{ "bank_identification_number", "60529289" },
	{ "cuid", "abcd1234" },
	{ "par", "MoNeosrGpuSdImbnoKODPUqXUpPrn" },
	{ "card_customer_key", "NA" },
	{ "account_customer_key", "1$abcd1234" },
	{ "status", "SUCCESSFUL" },
	{ "status_message", "WgdkLENVXZlvHVt" },
	{ "termination_type", "BIILLABLE" },
	{ "time_elapsed", 1770508573 },
	{ "first_6", "000000" },
	{ "first_7", "0000000" },
	{ "first_8", "00000000" },
	{ "trace", "xSEwRHSzQUHpljFrJlremGRXoaqTekKDDSqfkzWIKwOYWlwZXsvfuJhPzMRCYZjotSozsYoAkpbYjpuLQnVcvmmoDgDOxrnSYymLWATryspHTarLpNieIxQBjHFyczwtRqYtmgIlKTNuTOBRhelFjZULTemyYnFnbKciokdQBOZWrtXiaKRypbDugdRxxFbrZWkhWPSUlIPHckqpfFwUwAXeHZluCpesuZAPoGiYvVIFenuKXqwdbcLmPVLplj" },
	{ "place_card_on_single_site_job_id", 1605373370 },
	{ "financial_institution_id", 832491634 },
	{ "merchant_site_id", 1879337533 },
	{ "email_sent", true },
	{ "completed_on", "1981-11-21T10:30:12.133Z" }
};

CardSavrResponse<CardPlacementResult> cardplacementresult = await http.CreateCardPlacementResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("merchant_site_hostname", "amazon.com" )
	.add("meta_key", "MB9810411" )
	.add("fi_name", "ACME Bank" )
	.add("bank_identification_number", "60529289" )
	.add("cuid", "abcd1234" )
	.add("par", "MoNeosrGpuSdImbnoKODPUqXUpPrn" )
	.add("card_customer_key", "NA" )
	.add("account_customer_key", "1$abcd1234" )
	.add("status", "SUCCESSFUL" )
	.add("status_message", "WgdkLENVXZlvHVt" )
	.add("termination_type", "BIILLABLE" )
	.add("time_elapsed", 1770508573 )
	.add("first_6", "000000" )
	.add("first_7", "0000000" )
	.add("first_8", "00000000" )
	.add("trace", "xSEwRHSzQUHpljFrJlremGRXoaqTekKDDSqfkzWIKwOYWlwZXsvfuJhPzMRCYZjotSozsYoAkpbYjpuLQnVcvmmoDgDOxrnSYymLWATryspHTarLpNieIxQBjHFyczwtRqYtmgIlKTNuTOBRhelFjZULTemyYnFnbKciokdQBOZWrtXiaKRypbDugdRxxFbrZWkhWPSUlIPHckqpfFwUwAXeHZluCpesuZAPoGiYvVIFenuKXqwdbcLmPVLplj" )
	.add("place_card_on_single_site_job_id", 1605373370 )
	.add("financial_institution_id", 832491634 )
	.add("merchant_site_id", 1879337533 )
	.add("email_sent", true )
	.add("completed_on", "1981-11-21T10:30:12.133Z" )
	.build();
JsonValue cardplacementresult = session.post("/card_placement_results", body, null, null);
```

```shell
curl -d "{\"merchant_site_hostname\":\"amazon.com\",\"meta_key\":\"MB9810411\",\"fi_name\":\"ACME Bank\",\"bank_identification_number\":\"60529289\",\"cuid\":\"abcd1234\",\"par\":\"MoNeosrGpuSdImbnoKODPUqXUpPrn\",\"card_customer_key\":\"NA\",\"account_customer_key\":\"1$abcd1234\",\"status\":\"SUCCESSFUL\",\"status_message\":\"WgdkLENVXZlvHVt\",\"termination_type\":\"BIILLABLE\",\"custom_data\":{\"gqjYNJzzBwlm\":\"^Wb>-{bk(L6>rlcKS)i9_-i+*Dn*}G\",\"HRxeDaWuSwob\":40,\"JlBxCLklIyvY\":true},\"time_elapsed\":1770508573,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\",\"trace\":\"xSEwRHSzQUHpljFrJlremGRXoaqTekKDDSqfkzWIKwOYWlwZXsvfuJhPzMRCYZjotSozsYoAkpbYjpuLQnVcvmmoDgDOxrnSYymLWATryspHTarLpNieIxQBjHFyczwtRqYtmgIlKTNuTOBRhelFjZULTemyYnFnbKciokdQBOZWrtXiaKRypbDugdRxxFbrZWkhWPSUlIPHckqpfFwUwAXeHZluCpesuZAPoGiYvVIFenuKXqwdbcLmPVLplj\",\"place_card_on_single_site_job_id\":1605373370,\"financial_institution_id\":832491634,\"merchant_site_id\":1879337533,\"email_sent\":true,\"completed_on\":\"1981-11-21T10:30:12.133Z\"}"
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
  "bank_identification_number": "20977118",
  "cuid": "abcd1234",
  "par": "CzrINibRLezAeRsmfDxZRYzkcvFyL",
  "card_customer_key": "NA",
  "account_customer_key": "1$abcd1234",
  "status": "SUCCESSFUL",
  "status_message": "toYmRoSgSdvL",
  "termination_type": "BIILLABLE",
  "custom_data": {
    "dWENYnhiOAzV": ">jQ@$!uhAtiy=oO&",
    "RjTtsueYtHGN": 14,
    "NvaTozmnhhjH": false
  },
  "time_elapsed": 89006902,
  "first_6": "000000",
  "first_7": "0000000",
  "first_8": "00000000",
  "trace": "laLxSnzOlbDbWYmPjKMQyzAQcpiQsXaIBhNfAfCPkaalNnQPkzBhBYYixuWlrmCUvnucaILKEHqaSkRnfKeKCBKdwFaUakFrOawTJRHhrAudGDrCLywCBBFGHhHJcSADKfwyCovzwmJToIOngvexyDzfaNAzufwlIZILXHqXFEsJytHipMQpkKpnGxFvAoTWwkvrcerIHAQMSEFfLTTbyJgYIQrDFxCjhWoNpUCRpoiyUlvPinZjTvIszXhYWx",
  "financial_institution_id": 357194176,
  "merchant_site_id": 570183842,
  "email_sent": false,
  "completed_on": "1998-12-17T07:30:06.215Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "merchant_site_hostname", "amazon.com" },
	{ "meta_key", "MB9810411" },
	{ "fi_name", "ACME Bank" },
	{ "bank_identification_number", "20977118" },
	{ "cuid", "abcd1234" },
	{ "par", "CzrINibRLezAeRsmfDxZRYzkcvFyL" },
	{ "card_customer_key", "NA" },
	{ "account_customer_key", "1$abcd1234" },
	{ "status", "SUCCESSFUL" },
	{ "status_message", "toYmRoSgSdvL" },
	{ "termination_type", "BIILLABLE" },
	{ "time_elapsed", 89006902 },
	{ "first_6", "000000" },
	{ "first_7", "0000000" },
	{ "first_8", "00000000" },
	{ "trace", "laLxSnzOlbDbWYmPjKMQyzAQcpiQsXaIBhNfAfCPkaalNnQPkzBhBYYixuWlrmCUvnucaILKEHqaSkRnfKeKCBKdwFaUakFrOawTJRHhrAudGDrCLywCBBFGHhHJcSADKfwyCovzwmJToIOngvexyDzfaNAzufwlIZILXHqXFEsJytHipMQpkKpnGxFvAoTWwkvrcerIHAQMSEFfLTTbyJgYIQrDFxCjhWoNpUCRpoiyUlvPinZjTvIszXhYWx" },
	{ "financial_institution_id", 357194176 },
	{ "merchant_site_id", 570183842 },
	{ "email_sent", false },
	{ "completed_on", "1998-12-17T07:30:06.215Z" }
};

CardSavrResponse<CardPlacementResult> cardplacementresult = await http.UpdateCardPlacementResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("merchant_site_hostname", "amazon.com" )
	.add("meta_key", "MB9810411" )
	.add("fi_name", "ACME Bank" )
	.add("bank_identification_number", "20977118" )
	.add("cuid", "abcd1234" )
	.add("par", "CzrINibRLezAeRsmfDxZRYzkcvFyL" )
	.add("card_customer_key", "NA" )
	.add("account_customer_key", "1$abcd1234" )
	.add("status", "SUCCESSFUL" )
	.add("status_message", "toYmRoSgSdvL" )
	.add("termination_type", "BIILLABLE" )
	.add("time_elapsed", 89006902 )
	.add("first_6", "000000" )
	.add("first_7", "0000000" )
	.add("first_8", "00000000" )
	.add("trace", "laLxSnzOlbDbWYmPjKMQyzAQcpiQsXaIBhNfAfCPkaalNnQPkzBhBYYixuWlrmCUvnucaILKEHqaSkRnfKeKCBKdwFaUakFrOawTJRHhrAudGDrCLywCBBFGHhHJcSADKfwyCovzwmJToIOngvexyDzfaNAzufwlIZILXHqXFEsJytHipMQpkKpnGxFvAoTWwkvrcerIHAQMSEFfLTTbyJgYIQrDFxCjhWoNpUCRpoiyUlvPinZjTvIszXhYWx" )
	.add("financial_institution_id", 357194176 )
	.add("merchant_site_id", 570183842 )
	.add("email_sent", false )
	.add("completed_on", "1998-12-17T07:30:06.215Z" )
	.build();
JsonValue cardplacementresult = session.put("/card_placement_results", body, null, null);
```

```shell
curl -d "{\"merchant_site_hostname\":\"amazon.com\",\"meta_key\":\"MB9810411\",\"fi_name\":\"ACME Bank\",\"bank_identification_number\":\"20977118\",\"cuid\":\"abcd1234\",\"par\":\"CzrINibRLezAeRsmfDxZRYzkcvFyL\",\"card_customer_key\":\"NA\",\"account_customer_key\":\"1$abcd1234\",\"status\":\"SUCCESSFUL\",\"status_message\":\"toYmRoSgSdvL\",\"termination_type\":\"BIILLABLE\",\"custom_data\":{\"dWENYnhiOAzV\":\">jQ@$!uhAtiy=oO&\",\"RjTtsueYtHGN\":14,\"NvaTozmnhhjH\":false},\"time_elapsed\":89006902,\"first_6\":\"000000\",\"first_7\":\"0000000\",\"first_8\":\"00000000\",\"trace\":\"laLxSnzOlbDbWYmPjKMQyzAQcpiQsXaIBhNfAfCPkaalNnQPkzBhBYYixuWlrmCUvnucaILKEHqaSkRnfKeKCBKdwFaUakFrOawTJRHhrAudGDrCLywCBBFGHhHJcSADKfwyCovzwmJToIOngvexyDzfaNAzufwlIZILXHqXFEsJytHipMQpkKpnGxFvAoTWwkvrcerIHAQMSEFfLTTbyJgYIQrDFxCjhWoNpUCRpoiyUlvPinZjTvIszXhYWx\",\"financial_institution_id\":357194176,\"merchant_site_id\":570183842,\"email_sent\":false,\"completed_on\":\"1998-12-17T07:30:06.215Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/card_placement_results/931320305
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


## Delete card placement result

```shell
curl -X DELETE
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/card_placement_results/931320305
```

```javascript
await session.deleteCardPlacementResult(undefined);
```

```csharp
CardSavrResponse<CardPlacementResult> cardplacementresult = await http.DeleteCardPlacementResultAsync(undefined);
```

```java
JsonValue cardplacementresult = session.delete("/card_placement_results", undefined, null);
```

### Path

DELETE /card_placement_results/{id}

### Description

Delete a card placement result and purge its [related items](#cascading-delete).  An id is required on every delete request.

See [card placement result response parameters](#response-card_placement_result).


# Accounts
Account objects contain the account information, such as username and password, for a particular cardhoder. They are used to log in to a cardholder's account for placing a payment card.
## Get account

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/2043199056
```

```javascript
const accounts = await session.getAccounts(2043199056);
```

```csharp
CardSavrResponse<Accounts> accounts = await session.GetAccountsAsync(undefined);
```

```java
JsonValue accounts = session.get("/cardsavr_accounts", 2043199056, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2043199056,
  "last_password_update": "1998-10-08T22:13:32.960Z",
  "last_saved_card": "1981-09-21T00:45:12.134Z",
  "created_on": "1995-10-22T23:27:14.418Z",
  "last_updated_on": "1991-06-24T05:53:11.946Z",
  "cardholder": {
    "id": 692246450,
    "financial_institution_id": 180443075,
    "agent_session_id": "tC",
    "type": "persistent",
    "first_name": "GxhwdGcNiYEvnqq",
    "last_name": "ywKnFyI",
    "email": "uZxIFZZEBxmI@FWjJay.zhx",
    "meta_key": "lehWtPnlxVLLRmwkjUvxH",
    "cardholder_safe_key": "OU9p2WtW6HQQtU++YL8smjZr/MLSv3j/1iX6iFgMHg4=",
    "custom_data": {
      "yLQKQayyBXBD": "9]p&",
      "AxuuvulpnEeJ": 47,
      "lGcBrznltCXi": true
    },
    "created_on": "1990-04-21T20:27:48.682Z",
    "last_updated_on": "2010-01-23T10:48:24.135Z"
  },
  "merchant_site": {
    "id": 1017753822,
    "name": "QEprIyR",
    "host": "T",
    "tags": [
      "67Av+%p/#1",
      12,
      "St=*<@M8H"
    ],
    "queue_name": "vbs_queue",
    "required_form_fields": [
      "@9cQ5MHF6h*ge4z",
      93,
      "5Y2>,Fg%sRixvu+a"
    ],
    "images": [
      {
        "TtMVheurIjLa": "<IG.2ew4X@g0",
        "GkmSFucLnQpU": 52,
        "NTmyMlFOZrZl": false
      },
      {
        "lymsoVFMkLJp": "lPRdh%a9S>{oR3rl7Njky.xJTQQ0fT1",
        "jAHpQEAUBAbI": 0,
        "aKUUQQCkHaFu": true
      },
      {
        "ljaVZBtRgQGK": "G#O%{Y@azuh!",
        "OeXjJDQEIRzZ": 27,
        "GSfXfxTbVvHv": false
      }
    ],
    "account_identification": {
      "EnxuhGqzymXG": "G",
      "sNPdoLwvrDVK": 27,
      "srAEbVBwNphD": false
    },
    "messages": {
      "HVOWtZogKlxx": "]*<tB2%Qmy3U$X",
      "XgaydeZtFeWm": 26,
      "wBmnfjllejTq": false
    },
    "mfa": true,
    "move_mouse_to_element": false,
    "proxy_order": [
      "OxB2s-wc3k7Gys_Sv~Nccj!z)Ns",
      9,
      "3FnCg-80gn*0}_yvEorDdz,6%=r>s"
    ],
    "credit_card_page": "gLUlWZ",
    "forgot_password_page": "MtbeEmMdGBTXIbsplAJp",
    "quick_start": false,
    "login_page": "JjFjxj",
    "login": {
      "NAdUcOkRrDeg": "K<fp9P0F*m%gXW<{Qp)onWZg0",
      "anzkhFYkkrpx": 75,
      "GPOTFfdVVsZY": true
    }
  },
  "cardsavr_card": {
    "id": 439355090,
    "bin_id": 103804870,
    "cvv": "QHX",
    "expiration_month": "i",
    "expiration_year": "Z",
    "name_on_card": "PTOPOgOYVUyFQbiLiAGLygnpDgNWXeogvcMOuuZzNiXnUPtMTWAYvvrqFJudBtHZXqCYBQKkLsUzlQqmcKjcddgmZvgvbcaPHXcYUMXmOjqgLarNdhOIuKMkXSPJPrmzewtijVEnTcNBEmEWYKmJdsZeCjbqWvUcnGUIMGCkNUnWozrrEslBdSiRfrFeFIsKgxfHOioXVhmEKJjSsVNuhwEKyfgqurliISmJMwLkamvsGLUyMaBQFDmrZvtFXS",
    "first_6": "hXVudHtKfAKwPbwpjscpSouMITXsgnIf",
    "first_7": "NJlTBYTriXFBfatpnQpZxAMpYqZPHCHJ",
    "first_8": "gROWttwnsgmNQMVfFAGJGjvrazXjiPwE",
    "created_on": "2011-10-27T06:18:18.508Z",
    "last_updated_on": "1993-02-10T16:15:05.223Z"
  },
  "customer_key": "X"
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

**Example GET request path:**<br>`/cardsavr_accounts/2043199056`

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
  "cardholder_id": 1650567456,
  "merchant_site_id": 1492303091,
  "customer_key": "X",
  "last_card_placed_id": 672743464,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1650567456 },
	{ "merchant_site_id", 1492303091 },
	{ "customer_key", "X" },
	{ "last_card_placed_id", 672743464 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.CreateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1650567456 )
	.add("merchant_site_id", 1492303091 )
	.add("customer_key", "X" )
	.add("last_card_placed_id", 672743464 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.post("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1650567456,\"merchant_site_id\":1492303091,\"customer_key\":\"X\",\"last_card_placed_id\":672743464,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
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
  "last_card_placed_id": 942902131,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, null, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "last_card_placed_id", 942902131 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<Account> account = await http.UpdateAccountAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("last_card_placed_id", 942902131 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue account = session.put("/cardsavr_accounts", body, null, null);
```

```shell
curl -d "{\"last_card_placed_id\":942902131,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/2043199056
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
https://api.INSTANCE.cardsavr.io/cardsavr_accounts/2043199056
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
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1874078100
```

```javascript
const addresses = await session.getAddresses(1874078100);
```

```csharp
CardSavrResponse<Addresses> addresses = await session.GetAddressesAsync(undefined);
```

```java
JsonValue addresses = session.get("/cardsavr_addresses", 1874078100, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1874078100,
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
  "created_on": "1997-03-17T16:09:44.881Z",
  "last_updated_on": "2002-12-31T14:19:11.948Z",
  "cardholder": {
    "id": 1679204159,
    "financial_institution_id": 1774413590,
    "agent_session_id": "aoaPzObzqJPvMDFjPaCsgADtABxIvkB",
    "type": "ephemeral",
    "first_name": "RcU",
    "last_name": "pErbunMSHISEsmHvvXFCdXxw",
    "email": "sosUVOVObDiy@SHIFtP.zIG",
    "meta_key": "ZlgatywnEriUu",
    "cardholder_safe_key": "/B12df0DoxD1owZ+FR/75NipZSWUus0B3+EYdEAq/Bg=",
    "custom_data": {
      "uvYVoschSFnr": "6XMm",
      "rhKjaLXumvpr": 83,
      "IutokGMVKbEA": false
    },
    "created_on": "2001-06-12T07:23:24.377Z",
    "last_updated_on": "2013-08-10T11:10:57.305Z"
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

**Example GET request path:**<br>`/cardsavr_addresses/1874078100`

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
  "cardholder_id": 1414343873,
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
	{ "cardholder_id", 1414343873 },
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
	.add("cardholder_id", 1414343873 )
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
curl -d "{\"cardholder_id\":1414343873,\"address1\":\"123 Main St.\",\"address2\":\"Unit A\",\"city\":\"Seattle\",\"subnational\":\"WA\",\"postal_code\":\"98177\",\"postal_other\":\"98177-0124\",\"country\":\"USA\",\"is_primary\":true,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"phone_number\":\"2065555555\"}"
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1874078100
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
https://api.INSTANCE.cardsavr.io/cardsavr_addresses/1874078100
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
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/cardsavr_bins/181470582
```

```javascript
const bins = await session.getBins(181470582);
```

```csharp
CardSavrResponse<Bins> bins = await session.GetBinsAsync(undefined);
```

```java
JsonValue bins = session.get("/cardsavr_bins", 181470582, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 181470582,
  "custom_data": {
    "rWcGSEEsMNAn": "oTv,skWjT_L*PU~S}SHoXO<Pl9lKp~r",
    "uMKfZBMFQTmj": 16,
    "dcIryjPiayhx": true
  },
  "created_on": "2013-01-20T20:34:02.149Z",
  "last_updated_on": "2002-10-18T00:32:45.788Z",
  "financial_institution": {
    "id": 190152926,
    "name": "zLslYlheonkVGvuxXJmncnZjsgFrLjtfMJybBvrdzrilXoAUyGHYGcTnSgxBYxx",
    "description": "XeblRShghmoUu",
    "lookup_key": "TkPxVrgTsGudotjuEUXbVCplEZjOnEHCoybmqQCbpwwbnTjsXCGVWpTggMaOtag",
    "alternate_lookup_key": "lnHZIzUOUzrTWnxBaJmMTAmpKsteALoHMfgCrxuccqNxvGjAGAqtGmFoubAuxaF",
    "config": {
      "NEQaGsvkIoQH": "pSr0T=r}9WmH3A&cOx!-=O=6",
      "OvgKAxsnKlvv": 27,
      "DLXhudCYLJtM": true
    },
    "created_on": "1995-04-06T22:02:54.691Z",
    "last_updated_on": "1970-11-28T00:22:15.155Z"
  },
  "bank_identification_number": "68357559"
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

**Example GET request path:**<br>`/cardsavr_bins/181470582`

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
  "financial_institution_id": 372366096,
  "bank_identification_number": "68357559",
  "custom_data": {
    "rWcGSEEsMNAn": "oTv,skWjT_L*PU~S}SHoXO<Pl9lKp~r",
    "uMKfZBMFQTmj": 16,
    "dcIryjPiayhx": true
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 372366096 },
	{ "bank_identification_number", "68357559" }
};

CardSavrResponse<Bin> bin = await http.CreateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 372366096 )
	.add("bank_identification_number", "68357559" )
	.build();
JsonValue bin = session.post("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":372366096,\"bank_identification_number\":\"68357559\",\"custom_data\":{\"rWcGSEEsMNAn\":\"oTv,skWjT_L*PU~S}SHoXO<Pl9lKp~r\",\"uMKfZBMFQTmj\":16,\"dcIryjPiayhx\":true}}"
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
  "financial_institution_id": 605690727,
  "custom_data": {
    "GJLRJAVfGBZh": "FK6n",
    "noIwSCcRpcLj": 31,
    "UwArJpKrKBak": false
  }
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 605690727 }
};

CardSavrResponse<Bin> bin = await http.UpdateBinAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 605690727 )
	.build();
JsonValue bin = session.put("/cardsavr_bins", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":605690727,\"custom_data\":{\"GJLRJAVfGBZh\":\"FK6n\",\"noIwSCcRpcLj\":31,\"UwArJpKrKBak\":false}}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_bins/181470582
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
https://api.INSTANCE.cardsavr.io/cardsavr_bins/181470582
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


# Cards
A card object contains information about a payment card for a specific cardholder. Card objects are used to populate payment information on merchant sites.
## Get card

```shell
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/cardsavr_cards/987080611
```

```javascript
const cards = await session.getCards(987080611);
```

```csharp
CardSavrResponse<Cards> cards = await session.GetCardsAsync(undefined);
```

```java
JsonValue cards = session.get("/cardsavr_cards", 987080611, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 987080611,
  "expiration_month": 12,
  "expiration_year": 24,
  "name_on_card": "Joe C Smith",
  "created_on": "2013-05-12T16:14:15.240Z",
  "last_updated_on": "1975-04-16T04:33:20.043Z",
  "cardholder": {
    "id": 1524697332,
    "financial_institution_id": 1111638316,
    "agent_session_id": "EGpQUzvYMAPRuiJvSxAcwfZQw",
    "type": "persistent",
    "first_name": "fscjSbO",
    "last_name": "GlMqJ",
    "email": "zDcClvDtqgEV@ShvaFp.bQQ",
    "meta_key": "peUkHIobZFvpSKCORxXIIU",
    "cardholder_safe_key": "k3EMLuwnuagIdjqGKGZkK8y7iZ9S139VNHtzd5p68Qc=",
    "custom_data": {
      "BCAJAkyEmzNt": "S4$K)m}WFVebeE6/",
      "GleXNEEsomXZ": 94,
      "qteLiFxIZZbJ": false
    },
    "created_on": "1980-05-09T15:27:58.018Z",
    "last_updated_on": "1982-09-26T19:26:50.658Z"
  },
  "cardsavr_bin": {
    "id": 1043395702,
    "financial_institution_id": 1398077415,
    "custom_data": {
      "hzyjJRzNXzFC": "Jov%YHNB8sw*",
      "USucDqgCWJKe": 12,
      "edvTDxikGEjJ": true
    },
    "created_on": "1972-11-08T04:05:51.157Z",
    "last_updated_on": "2016-08-25T07:23:57.858Z"
  },
  "address_id": 1638238840,
  "par": "CIjXfbRNobnjwRTuCoAJMzWSDNpSM"
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

**Example GET request path:**<br>`/cardsavr_cards/987080611`

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
  "cardholder_id": 168528234,
  "address_id": 1638238840,
  "bin_id": 1566252144,
  "par": "CIjXfbRNobnjwRTuCoAJMzWSDNpSM",
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
	{ "cardholder_id", 168528234 },
	{ "address_id", 1638238840 },
	{ "bin_id", 1566252144 },
	{ "par", "CIjXfbRNobnjwRTuCoAJMzWSDNpSM" },
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
	.add("cardholder_id", 168528234 )
	.add("address_id", 1638238840 )
	.add("bin_id", 1566252144 )
	.add("par", "CIjXfbRNobnjwRTuCoAJMzWSDNpSM" )
	.add("pan", "4111111111111111" )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Joe C Smith" )
	.build();
JsonValue card = session.post("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":168528234,\"address_id\":1638238840,\"bin_id\":1566252144,\"par\":\"CIjXfbRNobnjwRTuCoAJMzWSDNpSM\",\"pan\":\"4111111111111111\",\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\"}"
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
  "bin_id": 1432440398,
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
	{ "bin_id", 1432440398 },
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
	.add("bin_id", 1432440398 )
	.add("cvv", "111" )
	.add("expiration_month", 12 )
	.add("expiration_year", 24 )
	.add("name_on_card", "Joe C Smith" )
	.add("pan", "4111111111111111" )
	.build();
JsonValue card = session.put("/cardsavr_cards", body, null, null);
```

```shell
curl -d "{\"bin_id\":1432440398,\"cvv\":\"111\",\"expiration_month\":12,\"expiration_year\":24,\"name_on_card\":\"Joe C Smith\",\"pan\":\"4111111111111111\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_cards/987080611
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
https://api.INSTANCE.cardsavr.io/cardsavr_cards/987080611
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
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/cardholders/475197014
```

```javascript
const cardholders = await session.getCardholders(475197014);
```

```csharp
CardSavrResponse<Cardholders> cardholders = await session.GetCardholdersAsync(undefined);
```

```java
JsonValue cardholders = session.get("/cardholders", 475197014, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 475197014,
  "first_name": "Joe",
  "last_name": "Smith",
  "email": "test_email@strivve.com",
  "meta_key": "MB9810411",
  "custom_data": {
    "MfNPOuNucLhp": "KcpF~v$ipNB5v=bAxIO",
    "RJgSaoDgcHKK": 43,
    "EowYaYxUSJJu": false
  },
  "created_on": "1997-01-15T21:37:28.186Z",
  "last_updated_on": "1983-08-19T02:11:05.463Z",
  "cuid": "abcd1234",
  "financial_institution": {
    "id": 852132396,
    "name": "kHCJzqqTdpdedVeGPGdmdIrZgmlyscgEkeecfWeGPCjQvRDIZneHVFjSuHVKjRi",
    "description": "boQOohrfyEE",
    "lookup_key": "UXzcjbUknGnwVUzNlMHbDlCTWXPlIOKUKconoHuqocjmZHvkMlVTJyOUjdpeWyu",
    "alternate_lookup_key": "wdKwjfofqtFENjzgJVCOWziUvofibEGRmOVggKBaGEheMXQjyRrTdtzBVCykQrl",
    "config": {
      "TSskyNKEbFpQ": "yxxO-mM,<S%>",
      "FPkHBFwkuRnn": 88,
      "oErHbxOVXovh": true
    },
    "created_on": "1991-06-08T21:47:49.317Z",
    "last_updated_on": "1976-06-16T10:29:22.640Z"
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

**Example GET request path:**<br>`/cardholders/475197014`

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
    "MfNPOuNucLhp": "KcpF~v$ipNB5v=bAxIO",
    "RJgSaoDgcHKK": 43,
    "EowYaYxUSJJu": false
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
curl -d "{\"cuid\":\"abcd1234\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"MB9810411\",\"custom_data\":{\"MfNPOuNucLhp\":\"KcpF~v$ipNB5v=bAxIO\",\"RJgSaoDgcHKK\":43,\"EowYaYxUSJJu\":false}}"
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
    "IIjXJEurgcDU": "@qjFr^ylT8j+%}Y",
    "VCHgWnPRXNXs": 32,
    "byKaDbJYWFBU": false
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
curl -d "{\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"email\":\"test_email@strivve.com\",\"meta_key\":\"MB9810411\",\"custom_data\":{\"IIjXJEurgcDU\":\"@qjFr^ylT8j+%}Y\",\"VCHgWnPRXNXs\":32,\"byKaDbJYWFBU\":false},\"cuid\":\"abcd1234\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardholders/475197014
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
https://api.INSTANCE.cardsavr.io/cardholders/475197014
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
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/cardsavr_users/1895110496
```

```javascript
const users = await session.getUsers(1895110496);
```

```csharp
CardSavrResponse<Users> users = await session.GetUsersAsync(undefined);
```

```java
JsonValue users = session.get("/cardsavr_users", 1895110496, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1895110496,
  "first_name": "Joe",
  "last_name": "Smith",
  "last_login_time": "1999-07-07T12:36:29.018Z",
  "is_locked": true,
  "password_lifetime": 40,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "swch_agent",
  "next_rotation_on": "1990-04-30T21:50:10.324Z",
  "created_on": "2000-12-15T08:25:53.356Z",
  "last_updated_on": "1990-02-06T18:29:48.925Z",
  "username": "jsmith123",
  "financial_institution": {
    "id": 1484069702,
    "name": "wduuDlMhihODqlqxujIvHmyNWEZPGGciUNHrPoMRtdNytwjOKxNZnViaWIsaGKw",
    "description": "tsHRrwUomRSWJZGAdpAP",
    "lookup_key": "UACmXJbsvpUFSfICNzaIApMxJqLBnLlApwyEnwWWMMGWutSSFSyMESlhRIJChWN",
    "alternate_lookup_key": "UgRHrAnUAHoTZOnbZzwEvRtZJdBWMbavUBZxldurrJWLacFjJkUREnhupFSawsD",
    "config": {
      "FxocqjXOXqst": "hyDnz~g[qF9wM=TKYHO9}Ng<Qv[{",
      "IaDNVUmGsOUE": 30,
      "GhXYzSaGGcMq": true
    },
    "created_on": "1991-09-21T05:28:18.324Z",
    "last_updated_on": "2013-03-29T00:42:47.951Z"
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

**Example GET request path:**<br>`/cardsavr_users/1895110496`

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
  "financial_institution_id": 1475559788,
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=",
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 40,
  "email": "test_email@strivve.com",
  "is_password_update_required": true,
  "role": "swch_agent",
  "next_rotation_on": "1990-04-30T21:50:10.324Z"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 1475559788 },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 40 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", true },
	{ "role", "swch_agent" },
	{ "next_rotation_on", "1990-04-30T21:50:10.324Z" }
};

CardSavrResponse<User> user = await http.CreateUserAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 1475559788 )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 40 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", true )
	.add("role", "swch_agent" )
	.add("next_rotation_on", "1990-04-30T21:50:10.324Z" )
	.build();
JsonValue user = session.post("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":1475559788,\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\",\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":40,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":true,\"role\":\"swch_agent\",\"next_rotation_on\":\"1990-04-30T21:50:10.324Z\"}"
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
  "financial_institution_id": 861912846,
  "first_name": "Joe",
  "last_name": "Smith",
  "password_lifetime": 331,
  "email": "test_email@strivve.com",
  "is_password_update_required": false,
  "role": "swch_agent",
  "next_rotation_on": "1977-12-28T17:13:38.283Z",
  "username": "jsmith123",
  "password": "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI="
}, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 861912846 },
	{ "first_name", "Joe" },
	{ "last_name", "Smith" },
	{ "password_lifetime", 331 },
	{ "email", "test_email@strivve.com" },
	{ "is_password_update_required", false },
	{ "role", "swch_agent" },
	{ "next_rotation_on", "1977-12-28T17:13:38.283Z" },
	{ "username", "jsmith123" },
	{ "password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" }
};

CardSavrResponse<User> user = await http.UpdateUserAsync(body, NEW_CARDHODLER_SAFE_KEY, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 861912846 )
	.add("first_name", "Joe" )
	.add("last_name", "Smith" )
	.add("password_lifetime", 331 )
	.add("email", "test_email@strivve.com" )
	.add("is_password_update_required", false )
	.add("role", "swch_agent" )
	.add("next_rotation_on", "1977-12-28T17:13:38.283Z" )
	.add("username", "jsmith123" )
	.add("password", "BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=" )
	.build();
JsonValue user = session.put("/cardsavr_users", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":861912846,\"first_name\":\"Joe\",\"last_name\":\"Smith\",\"password_lifetime\":331,\"email\":\"test_email@strivve.com\",\"is_password_update_required\":false,\"role\":\"swch_agent\",\"next_rotation_on\":\"1977-12-28T17:13:38.283Z\",\"username\":\"jsmith123\",\"password\":\"BSN6W6IF72W6EVWwbwgqYIo51ad/ZCZ74vxa3rzyQqI=\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-new-cardholder-safe-key: NEW_CARDHODLER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/cardsavr_users/1895110496
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
https://api.INSTANCE.cardsavr.io/cardsavr_users/1895110496
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
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/financial_institutions/162639034
```

```javascript
const financialinstitutions = await session.getFinancialInstitutions(162639034);
```

```csharp
CardSavrResponse<FinancialInstitutions> financialinstitutions = await session.GetFinancialInstitutionsAsync(undefined);
```

```java
JsonValue financialinstitutions = session.get("/financial_institutions", 162639034, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 162639034,
  "name": "QIoOXqHcuLGZccgfUfqycWgkiPBqoQpEZHVlZVyWVnhLetJWLLZKHTTSIzVVvQb",
  "description": "xhQKxbzepvSzEqWkPi",
  "lookup_key": "bKwrqHwIMkPNXBEjgZFYHLOjvfeBAoaMMGbQGYAqxwlwmyMLIApHWbXcYYLIXzV",
  "alternate_lookup_key": "nnuldWaBBlOTiENzggkQBZHNlGtSFTLQQyWFqYDsOhNXMmbgFpUUyNhxdmaSINb",
  "created_on": "1989-07-31T20:58:03.762Z",
  "last_updated_on": "2005-01-06T11:46:23.997Z"
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

**Example GET request path:**<br>`/financial_institutions/162639034`

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
  "name": "QIoOXqHcuLGZccgfUfqycWgkiPBqoQpEZHVlZVyWVnhLetJWLLZKHTTSIzVVvQb",
  "description": "xhQKxbzepvSzEqWkPi",
  "lookup_key": "bKwrqHwIMkPNXBEjgZFYHLOjvfeBAoaMMGbQGYAqxwlwmyMLIApHWbXcYYLIXzV",
  "alternate_lookup_key": "nnuldWaBBlOTiENzggkQBZHNlGtSFTLQQyWFqYDsOhNXMmbgFpUUyNhxdmaSINb"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "QIoOXqHcuLGZccgfUfqycWgkiPBqoQpEZHVlZVyWVnhLetJWLLZKHTTSIzVVvQb" },
	{ "description", "xhQKxbzepvSzEqWkPi" },
	{ "lookup_key", "bKwrqHwIMkPNXBEjgZFYHLOjvfeBAoaMMGbQGYAqxwlwmyMLIApHWbXcYYLIXzV" },
	{ "alternate_lookup_key", "nnuldWaBBlOTiENzggkQBZHNlGtSFTLQQyWFqYDsOhNXMmbgFpUUyNhxdmaSINb" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.CreateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "QIoOXqHcuLGZccgfUfqycWgkiPBqoQpEZHVlZVyWVnhLetJWLLZKHTTSIzVVvQb" )
	.add("description", "xhQKxbzepvSzEqWkPi" )
	.add("lookup_key", "bKwrqHwIMkPNXBEjgZFYHLOjvfeBAoaMMGbQGYAqxwlwmyMLIApHWbXcYYLIXzV" )
	.add("alternate_lookup_key", "nnuldWaBBlOTiENzggkQBZHNlGtSFTLQQyWFqYDsOhNXMmbgFpUUyNhxdmaSINb" )
	.build();
JsonValue financialinstitution = session.post("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"QIoOXqHcuLGZccgfUfqycWgkiPBqoQpEZHVlZVyWVnhLetJWLLZKHTTSIzVVvQb\",\"description\":\"xhQKxbzepvSzEqWkPi\",\"lookup_key\":\"bKwrqHwIMkPNXBEjgZFYHLOjvfeBAoaMMGbQGYAqxwlwmyMLIApHWbXcYYLIXzV\",\"alternate_lookup_key\":\"nnuldWaBBlOTiENzggkQBZHNlGtSFTLQQyWFqYDsOhNXMmbgFpUUyNhxdmaSINb\"}"
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
  "name": "GcaIKEkNvvDfwEnLxlPPqBRJHSxzfMpsyFbFPtxWCsILsHVUfvzFdfmUDZRFeFN",
  "description": "QOnRVvyqDWnwqPYGERdDuwLe",
  "lookup_key": "dhjDfhIPMRADymVMCnVGswrfrmNrAHlnbVVasrtZNdqBssqktonqMmmGkQVWrGl",
  "alternate_lookup_key": "niVtHkIWDBJsJPRUoCQLFTfBwJQskLzCcwUKwOsiLsohlXmIKUdJIThKlnszPuK"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "GcaIKEkNvvDfwEnLxlPPqBRJHSxzfMpsyFbFPtxWCsILsHVUfvzFdfmUDZRFeFN" },
	{ "description", "QOnRVvyqDWnwqPYGERdDuwLe" },
	{ "lookup_key", "dhjDfhIPMRADymVMCnVGswrfrmNrAHlnbVVasrtZNdqBssqktonqMmmGkQVWrGl" },
	{ "alternate_lookup_key", "niVtHkIWDBJsJPRUoCQLFTfBwJQskLzCcwUKwOsiLsohlXmIKUdJIThKlnszPuK" }
};

CardSavrResponse<FinancialInstitution> financialinstitution = await http.UpdateFinancialInstitutionAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "GcaIKEkNvvDfwEnLxlPPqBRJHSxzfMpsyFbFPtxWCsILsHVUfvzFdfmUDZRFeFN" )
	.add("description", "QOnRVvyqDWnwqPYGERdDuwLe" )
	.add("lookup_key", "dhjDfhIPMRADymVMCnVGswrfrmNrAHlnbVVasrtZNdqBssqktonqMmmGkQVWrGl" )
	.add("alternate_lookup_key", "niVtHkIWDBJsJPRUoCQLFTfBwJQskLzCcwUKwOsiLsohlXmIKUdJIThKlnszPuK" )
	.build();
JsonValue financialinstitution = session.put("/financial_institutions", body, null, null);
```

```shell
curl -d "{\"name\":\"GcaIKEkNvvDfwEnLxlPPqBRJHSxzfMpsyFbFPtxWCsILsHVUfvzFdfmUDZRFeFN\",\"description\":\"QOnRVvyqDWnwqPYGERdDuwLe\",\"lookup_key\":\"dhjDfhIPMRADymVMCnVGswrfrmNrAHlnbVVasrtZNdqBssqktonqMmmGkQVWrGl\",\"alternate_lookup_key\":\"niVtHkIWDBJsJPRUoCQLFTfBwJQskLzCcwUKwOsiLsohlXmIKUdJIThKlnszPuK\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/financial_institutions/162639034
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
https://api.INSTANCE.cardsavr.io/financial_institutions/162639034
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
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/integrators/1678328018
```

```javascript
const integrators = await session.getIntegrators(1678328018);
```

```csharp
CardSavrResponse<Integrators> integrators = await session.GetIntegratorsAsync(undefined);
```

```java
JsonValue integrators = session.get("/integrators", 1678328018, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 1678328018,
  "name": "KEYOPxiKUhlZFtXYTVtyWSDxzqYsKzPRIdzkorlSDVUhUPSbf",
  "description": "XAGmhrRdLDcMBZTNxvbwuwiVHdPtn",
  "current_key": "J49pxoazjQ+hrnEkrHnLTXjbZ5yIu4E4wA9Pzfyw8dw=",
  "key_lifetime": 279,
  "next_rotation_on": "1977-03-02T13:22:21.737Z",
  "created_on": "2020-03-15T08:51:26.940Z",
  "last_updated_on": "2018-07-27T01:37:12.421Z"
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

**Example GET request path:**<br>`/integrators/1678328018`

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
  "name": "KEYOPxiKUhlZFtXYTVtyWSDxzqYsKzPRIdzkorlSDVUhUPSbf",
  "description": "XAGmhrRdLDcMBZTNxvbwuwiVHdPtn",
  "current_key": "J49pxoazjQ+hrnEkrHnLTXjbZ5yIu4E4wA9Pzfyw8dw=",
  "key_lifetime": 279,
  "next_rotation_on": "1977-03-02T13:22:21.737Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "KEYOPxiKUhlZFtXYTVtyWSDxzqYsKzPRIdzkorlSDVUhUPSbf" },
	{ "description", "XAGmhrRdLDcMBZTNxvbwuwiVHdPtn" },
	{ "current_key", "J49pxoazjQ+hrnEkrHnLTXjbZ5yIu4E4wA9Pzfyw8dw=" },
	{ "key_lifetime", 279 },
	{ "next_rotation_on", "1977-03-02T13:22:21.737Z" }
};

CardSavrResponse<Integrator> integrator = await http.CreateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "KEYOPxiKUhlZFtXYTVtyWSDxzqYsKzPRIdzkorlSDVUhUPSbf" )
	.add("description", "XAGmhrRdLDcMBZTNxvbwuwiVHdPtn" )
	.add("current_key", "J49pxoazjQ+hrnEkrHnLTXjbZ5yIu4E4wA9Pzfyw8dw=" )
	.add("key_lifetime", 279 )
	.add("next_rotation_on", "1977-03-02T13:22:21.737Z" )
	.build();
JsonValue integrator = session.post("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"KEYOPxiKUhlZFtXYTVtyWSDxzqYsKzPRIdzkorlSDVUhUPSbf\",\"description\":\"XAGmhrRdLDcMBZTNxvbwuwiVHdPtn\",\"current_key\":\"J49pxoazjQ+hrnEkrHnLTXjbZ5yIu4E4wA9Pzfyw8dw=\",\"key_lifetime\":279,\"next_rotation_on\":\"1977-03-02T13:22:21.737Z\"}"
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
  "name": "ZgzMcmLImtrzWdMJuwORwPDiFavToXBfLKMdewBohyBVytyjD",
  "description": "xqRXcRXlBzoChmgvJcTkHEZwwSNcJplV",
  "current_key": "TG9J41Hoq0cO/lauvkEX7EQs7ZAu2N6PXrJBQdZIy14=",
  "key_lifetime": 123,
  "next_rotation_on": "1985-11-17T09:33:32.431Z"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "ZgzMcmLImtrzWdMJuwORwPDiFavToXBfLKMdewBohyBVytyjD" },
	{ "description", "xqRXcRXlBzoChmgvJcTkHEZwwSNcJplV" },
	{ "current_key", "TG9J41Hoq0cO/lauvkEX7EQs7ZAu2N6PXrJBQdZIy14=" },
	{ "key_lifetime", 123 },
	{ "next_rotation_on", "1985-11-17T09:33:32.431Z" }
};

CardSavrResponse<Integrator> integrator = await http.UpdateIntegratorAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "ZgzMcmLImtrzWdMJuwORwPDiFavToXBfLKMdewBohyBVytyjD" )
	.add("description", "xqRXcRXlBzoChmgvJcTkHEZwwSNcJplV" )
	.add("current_key", "TG9J41Hoq0cO/lauvkEX7EQs7ZAu2N6PXrJBQdZIy14=" )
	.add("key_lifetime", 123 )
	.add("next_rotation_on", "1985-11-17T09:33:32.431Z" )
	.build();
JsonValue integrator = session.put("/integrators", body, null, null);
```

```shell
curl -d "{\"name\":\"ZgzMcmLImtrzWdMJuwORwPDiFavToXBfLKMdewBohyBVytyjD\",\"description\":\"xqRXcRXlBzoChmgvJcTkHEZwwSNcJplV\",\"current_key\":\"TG9J41Hoq0cO/lauvkEX7EQs7ZAu2N6PXrJBQdZIy14=\",\"key_lifetime\":123,\"next_rotation_on\":\"1985-11-17T09:33:32.431Z\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/integrators/1678328018
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
https://api.INSTANCE.cardsavr.io/integrators/1678328018
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
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/merchant_sites/256016662
```

```javascript
const merchantsites = await session.getMerchantSites(256016662);
```

```csharp
CardSavrResponse<MerchantSites> merchantsites = await session.GetMerchantSitesAsync(undefined);
```

```java
JsonValue merchantsites = session.get("/merchant_sites", 256016662, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 256016662,
  "name": "nOhXXaPpBhTNGffXxUX",
  "host": "JKNVvLEJtxpxfCoRqzkVA",
  "tags": [
    "8GEqiyz^C2IWPtilc]b",
    4,
    "w@{.hjE#{BWVVo)JNUg[3>m#/10d/18D"
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
    "GzLCWCQOtMKi": "2k%_0]~EsF-",
    "JABhCyeJIpZy": 41,
    "tNovhxDqVqCR": false
  },
  "mfa": false,
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

**Example GET request path:**<br>`/merchant_sites/256016662`

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
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/notifications/656286862
```

```javascript
const notifications = await session.getNotifications(656286862);
```

```csharp
CardSavrResponse<Notifications> notifications = await session.GetNotificationsAsync(undefined);
```

```java
JsonValue notifications = session.get("/notifications", 656286862, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 656286862,
  "name": "VNcdOWuLxolhsYpYYjPshgBqmKVGvUdKfPmDjmDDwLskxkaLoTwTXKQMfWLCfVX",
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
  "html_template": "ksANWnyOghfqRehLimOgKjFWJ",
  "text_template": "JplUUTB",
  "created_on": "1974-01-03T04:35:05.434Z",
  "last_updated_on": "2007-03-28T10:08:13.843Z",
  "financial_institution": {
    "id": 274600094,
    "name": "WoahYLqeKbXDQtuldaGioZwrmizgbZwbklvQgUHFmSmYJygGCyEKaGIHdGSCApj",
    "description": "EglBpAHmRpNR",
    "lookup_key": "hJNqtPEBcHdAvehsFTuTJSRjOAJZrFaxQFGYokxvgzkDDcZihvANDCIqMcjDmKY",
    "alternate_lookup_key": "KUYrNewvcghmLAMfmEQnUsiYuwHhcwhxrLDgqjWZTOOBXqktsTxedvDEGrLNdvB",
    "config": {
      "OQKXyqeSzNiO": "u./B}}~(oW8==x]__q#",
      "gpNsjhbQnIhA": 64,
      "bURIYoWGoyZp": true
    },
    "created_on": "1989-01-30T06:04:06.942Z",
    "last_updated_on": "2000-09-05T07:17:12.293Z"
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

**Example GET request path:**<br>`/notifications/656286862`

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
  "financial_institution_id": 601856888,
  "name": "VNcdOWuLxolhsYpYYjPshgBqmKVGvUdKfPmDjmDDwLskxkaLoTwTXKQMfWLCfVX",
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
  "html_template": "ksANWnyOghfqRehLimOgKjFWJ",
  "text_template": "JplUUTB"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "financial_institution_id", 601856888 },
	{ "name", "VNcdOWuLxolhsYpYYjPshgBqmKVGvUdKfPmDjmDDwLskxkaLoTwTXKQMfWLCfVX" },
	{ "type", "webhook" },
	{ "event", "session_complete" },
	{ "html_template", "ksANWnyOghfqRehLimOgKjFWJ" },
	{ "text_template", "JplUUTB" }
};

CardSavrResponse<Notification> notification = await http.CreateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("financial_institution_id", 601856888 )
	.add("name", "VNcdOWuLxolhsYpYYjPshgBqmKVGvUdKfPmDjmDDwLskxkaLoTwTXKQMfWLCfVX" )
	.add("type", "webhook" )
	.add("event", "session_complete" )
	.add("html_template", "ksANWnyOghfqRehLimOgKjFWJ" )
	.add("text_template", "JplUUTB" )
	.build();
JsonValue notification = session.post("/notifications", body, null, null);
```

```shell
curl -d "{\"financial_institution_id\":601856888,\"name\":\"VNcdOWuLxolhsYpYYjPshgBqmKVGvUdKfPmDjmDDwLskxkaLoTwTXKQMfWLCfVX\",\"type\":\"webhook\",\"event\":\"session_complete\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"ksANWnyOghfqRehLimOgKjFWJ\",\"text_template\":\"JplUUTB\"}"
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
  "name": "kTvulIqYVdsQZGrkzAEPfkxpBhTfgudPDayULyUMJTQJGZkqdIjTZmjqHuDtiHA",
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
  "html_template": "eQiQjTzMxyglrOlMxkaNLReA",
  "text_template": "zOzGzlrUDPXEtpZAJPjsJwOkA"
});
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "name", "kTvulIqYVdsQZGrkzAEPfkxpBhTfgudPDayULyUMJTQJGZkqdIjTZmjqHuDtiHA" },
	{ "type", "webhook" },
	{ "event", "merchant_site_updates_top" },
	{ "html_template", "eQiQjTzMxyglrOlMxkaNLReA" },
	{ "text_template", "zOzGzlrUDPXEtpZAJPjsJwOkA" }
};

CardSavrResponse<Notification> notification = await http.UpdateNotificationAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("name", "kTvulIqYVdsQZGrkzAEPfkxpBhTfgudPDayULyUMJTQJGZkqdIjTZmjqHuDtiHA" )
	.add("type", "webhook" )
	.add("event", "merchant_site_updates_top" )
	.add("html_template", "eQiQjTzMxyglrOlMxkaNLReA" )
	.add("text_template", "zOzGzlrUDPXEtpZAJPjsJwOkA" )
	.build();
JsonValue notification = session.put("/notifications", body, null, null);
```

```shell
curl -d "{\"name\":\"kTvulIqYVdsQZGrkzAEPfkxpBhTfgudPDayULyUMJTQJGZkqdIjTZmjqHuDtiHA\",\"type\":\"webhook\",\"event\":\"merchant_site_updates_top\",\"config\":{\"recipient\":\"cardholder\",\"url\":null,\"from_email\":\"CardUpdatr <no-reply@cardupdatr.app>\",\"return_path\":\"no-reply@cardupdatr.app\",\"send_email_time\":null,\"interval_length\":null,\"interval_type\":null},\"html_template\":\"eQiQjTzMxyglrOlMxkaNLReA\",\"text_template\":\"zOzGzlrUDPXEtpZAJPjsJwOkA\"}"
-X PUT -H "Content-Type: application/json"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/notifications/656286862
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
https://api.INSTANCE.cardsavr.io/notifications/656286862
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
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/notification_results/705439843
```

```javascript
const notificationresults = await session.getNotificationResults(705439843);
```

```csharp
CardSavrResponse<NotificationResults> notificationresults = await session.GetNotificationResultsAsync(undefined);
```

```java
JsonValue notificationresults = session.get("/notification_results", 705439843, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 705439843,
  "last_attempt_date": "1983-08-26T08:36:48.048Z",
  "fi_lookup_key": "fOOqGZgqHyZYdTlrDzNfPtLsJUTqZWUVWPlhzLqMSZqSjJstYSfmiQzZnIwkYqA",
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
  "created_on": "2017-10-06T07:34:18.033Z",
  "last_updated_on": "2007-04-20T05:21:48.152Z",
  "notification": {
    "id": 2041459405,
    "name": "aCevdtGJDSSxWQVcItWbsFVjCMvmkkCqSceLduSTqshweFNlKyKjeBIiYVxZnDT",
    "type": "email",
    "event": "session_complete",
    "config": {
      "WfcTiFWqUqEG": "QvhZV{#<jmx.=FWi6%ynhYwVAk.8nwg>",
      "GLvhvmyqhIkZ": 14,
      "AUTtEDkGpcGN": true
    },
    "html_template": "owSOyL",
    "text_template": "tbWdQAIMXmpZP",
    "created_on": "1982-12-24T08:18:22.760Z",
    "last_updated_on": "1984-10-04T01:00:16.398Z"
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

**Example GET request path:**<br>`/notification_results/705439843`

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
  "notification_id": 1625642344,
  "fi_lookup_key": "fOOqGZgqHyZYdTlrDzNfPtLsJUTqZWUVWPlhzLqMSZqSjJstYSfmiQzZnIwkYqA",
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
	{ "notification_id", 1625642344 },
	{ "fi_lookup_key", "fOOqGZgqHyZYdTlrDzNfPtLsJUTqZWUVWPlhzLqMSZqSjJstYSfmiQzZnIwkYqA" },
	{ "cuid", "abcd1234" },
	{ "status", "SUCCESSFUL" },
	{ "attempts", 3 }
};

CardSavrResponse<NotificationResult> notificationresult = await http.CreateNotificationResultAsync(body);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("notification_id", 1625642344 )
	.add("fi_lookup_key", "fOOqGZgqHyZYdTlrDzNfPtLsJUTqZWUVWPlhzLqMSZqSjJstYSfmiQzZnIwkYqA" )
	.add("cuid", "abcd1234" )
	.add("status", "SUCCESSFUL" )
	.add("attempts", 3 )
	.build();
JsonValue notificationresult = session.post("/notification_results", body, null, null);
```

```shell
curl -d "{\"notification_id\":1625642344,\"fi_lookup_key\":\"fOOqGZgqHyZYdTlrDzNfPtLsJUTqZWUVWPlhzLqMSZqSjJstYSfmiQzZnIwkYqA\",\"cuid\":\"abcd1234\",\"status\":\"SUCCESSFUL\",\"attempts\":3,\"notification_data\":{\"status_code\":200,\"webhook_request\":{\"request_data\":123},\"webhook_response\":\"OK\"}}"
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
curl -H "x-cardsavr-trace:{\"key\": \"my_trace\"}"
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/2115559668
```

```javascript
const singlesitejobs = await session.getSingleSiteJobs(2115559668);
```

```csharp
CardSavrResponse<SingleSiteJobs> singlesitejobs = await session.GetSingleSiteJobsAsync(undefined);
```

```java
JsonValue singlesitejobs = session.get("/place_card_on_single_site_jobs", 2115559668, null, null);
```

> Sample response - not all properties are available to all roles (200 OK):

```json
{
  "id": 2115559668,
  "status": "SUCCESSFUL",
  "status_message": "KmipZhWQhLavgxgEzuBeXUN",
  "termination_type": "BIILLABLE",
  "custom_data": {
    "pYLFcUXruMPG": "w*et~jkQEsN}io+G(>FCRZ",
    "fKqttdKTVHPD": 57,
    "vVcwhxkVIyKO": true
  },
  "notification_sent": false,
  "time_elapsed": 958841692,
  "started_on": "2015-10-21T15:34:11.623Z",
  "completed_on": "2007-07-10T02:50:07.569Z",
  "created_on": "1992-12-03T03:09:06.264Z",
  "last_updated_on": "1979-06-21T11:58:43.927Z",
  "cardholder": {
    "id": 1512671220,
    "financial_institution_id": 773381133,
    "agent_session_id": "UaTzmuirJyheNke",
    "type": "ephemeral",
    "first_name": "bIDwcxYlXqMHzUlYnwGnp",
    "last_name": "FbjhMWkumOzdWnHlYX",
    "email": "pYUlDwJAekEH@xMvXou.nIm",
    "meta_key": "qiqmdEwcEFMxknfU",
    "cardholder_safe_key": "EQTNbuuTTQfhUUX2w1Hz6ipR8pYRb+3hn99PinUaSng=",
    "custom_data": {
      "DZDyQMKcFoQk": "8NS78@_QpMF1((L",
      "EvDfNSiIwDHc": 25,
      "XlLEKQtKJUdV": true
    },
    "created_on": "1979-02-11T09:28:49.609Z",
    "last_updated_on": "2006-01-09T00:38:12.244Z"
  },
  "cardsavr_card": {
    "id": 1895134333,
    "bin_id": 520761461,
    "cvv": "MJm",
    "expiration_month": "v",
    "expiration_year": "v",
    "name_on_card": "aXvDnlRhVKUNVTQXJVfcBozTgOSDJGOlkwbojRryVtljJYNWfTfFKzUkuNCIxziJCXuomwhTPVQkbeawzkfkyknVFrRFswDHsnMSKoseMcwzOWwfRzRUKXjwcfIokZAIpaofCmVFHBuPIdmIbAKCNCGVqCgazSafogREKjtkWcvCETeiyfjoBDJPjqRynMOGguxiyvlduBQiaHsOZYztfkmMDLnDcGcZJwbbNCVZcYQfCrCSJzPQTDVaXWpnov",
    "first_6": "liOUGzWLmsIQBvqZMwiWSOmPSIchPmSV",
    "first_7": "DydAsggmYEGtyjsHMugXhalCOhAEehoA",
    "first_8": "FMYwuxXNpfZbyibjCziFNqJdmsHDNVvv",
    "created_on": "2014-03-01T04:57:11.173Z",
    "last_updated_on": "1982-12-17T16:31:36.799Z"
  },
  "cardsavr_account": {
    "id": 1945812226,
    "last_card_placed_id": 1179273305,
    "username": "nzOeKZzcVmXbnkSQZnXuzFagPAHmzpfzsWRgsLnuAaZVXNFAGzBksLAHiMv",
    "username_hash": "jzxgtIoMGzyKlpywnMohMNxrkBpeiPfsvCmXvHPYNYWnJPeNfNwLZUjGpQU",
    "password": "KJoEteKxIRSiqhzgFDhWSCgOWLvUigAksmCxjqIKzcXoyTVsrRRZtdNThGm",
    "last_login": "2008-06-09T23:26:09.756Z",
    "last_password_update": "1990-09-23T05:59:34.874Z",
    "last_saved_card": "2015-05-19T21:25:40.019Z",
    "created_on": "1997-01-06T08:03:50.524Z",
    "last_updated_on": "1998-01-29T12:40:30.750Z"
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

**Example GET request path:**<br>`/place_card_on_single_site_jobs/2115559668`

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
  "cardholder_id": 1285707721,
  "card_id": 1082206388,
  "account_id": 382073662,
  "status": "SUCCESSFUL",
  "custom_data": {
    "pYLFcUXruMPG": "w*et~jkQEsN}io+G(>FCRZ",
    "fKqttdKTVHPD": 57,
    "vVcwhxkVIyKO": true
  },
  "notification_sent": false,
  "time_elapsed": 958841692,
  "started_on": "2015-10-21T15:34:11.623Z",
  "completed_on": "2007-07-10T02:50:07.569Z",
  "termination_type": "BIILLABLE"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "cardholder_id", 1285707721 },
	{ "card_id", 1082206388 },
	{ "account_id", 382073662 },
	{ "status", "SUCCESSFUL" },
	{ "notification_sent", false },
	{ "time_elapsed", 958841692 },
	{ "started_on", "2015-10-21T15:34:11.623Z" },
	{ "completed_on", "2007-07-10T02:50:07.569Z" },
	{ "termination_type", "BIILLABLE" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.CreateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("cardholder_id", 1285707721 )
	.add("card_id", 1082206388 )
	.add("account_id", 382073662 )
	.add("status", "SUCCESSFUL" )
	.add("notification_sent", false )
	.add("time_elapsed", 958841692 )
	.add("started_on", "2015-10-21T15:34:11.623Z" )
	.add("completed_on", "2007-07-10T02:50:07.569Z" )
	.add("termination_type", "BIILLABLE" )
	.build();
JsonValue singlesitejob = session.post("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"cardholder_id\":1285707721,\"card_id\":1082206388,\"account_id\":382073662,\"status\":\"SUCCESSFUL\",\"custom_data\":{\"pYLFcUXruMPG\":\"w*et~jkQEsN}io+G(>FCRZ\",\"fKqttdKTVHPD\":57,\"vVcwhxkVIyKO\":true},\"notification_sent\":false,\"time_elapsed\":958841692,\"started_on\":\"2015-10-21T15:34:11.623Z\",\"completed_on\":\"2007-07-10T02:50:07.569Z\",\"termination_type\":\"BIILLABLE\"}"
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
  "card_id": 2048202722,
  "status": "SUCCESSFUL",
  "custom_data": {
    "LUQUTiQwqQWk": "B*t9nLdwb~e[.4/uRjOJPtETKASx#($y",
    "qFBNQtOLveAJ": 62,
    "stGZusacXxsa": true
  },
  "notification_sent": true,
  "time_elapsed": 59465448,
  "started_on": "2004-04-12T02:58:57.509Z",
  "completed_on": "2004-10-09T15:51:02.772Z",
  "termination_type": "BIILLABLE"
}, CARDHOLDER_SAFE_KEY);
```

```csharp
PropertyBag body = new PropertyBag()
{
	{ "card_id", 2048202722 },
	{ "status", "SUCCESSFUL" },
	{ "notification_sent", true },
	{ "time_elapsed", 59465448 },
	{ "started_on", "2004-04-12T02:58:57.509Z" },
	{ "completed_on", "2004-10-09T15:51:02.772Z" },
	{ "termination_type", "BIILLABLE" }
};

CardSavrResponse<SingleSiteJob> singlesitejob = await http.UpdateSingleSiteJobAsync(body, CARDHOLDER_SAFE_KEY);
```

```java
JsonObject body = Json.createObjectBuilder()
	.add("card_id", 2048202722 )
	.add("status", "SUCCESSFUL" )
	.add("notification_sent", true )
	.add("time_elapsed", 59465448 )
	.add("started_on", "2004-04-12T02:58:57.509Z" )
	.add("completed_on", "2004-10-09T15:51:02.772Z" )
	.add("termination_type", "BIILLABLE" )
	.build();
JsonValue singlesitejob = session.put("/place_card_on_single_site_jobs", body, null, null);
```

```shell
curl -d "{\"card_id\":2048202722,\"status\":\"SUCCESSFUL\",\"custom_data\":{\"LUQUTiQwqQWk\":\"B*t9nLdwb~e[.4/uRjOJPtETKASx#($y\",\"qFBNQtOLveAJ\":62,\"stGZusacXxsa\":true},\"notification_sent\":true,\"time_elapsed\":59465448,\"started_on\":\"2004-04-12T02:58:57.509Z\",\"completed_on\":\"2004-10-09T15:51:02.772Z\",\"termination_type\":\"BIILLABLE\"}"
-X PUT -H "Content-Type: application/json"
-H "cardholder-safe-key: CARDHOLDER_SAFE_KEY"
-H "x-cardsavr-trace:{\"key\": \"my_trace\"}" 
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/2115559668
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
https://api.INSTANCE.cardsavr.io/place_card_on_single_site_jobs/2115559668
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

