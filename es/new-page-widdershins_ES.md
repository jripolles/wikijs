---
title: Vota-MD-widdershins_ES
description: 
published: true
date: 2022-08-10T09:25:54.252Z
tags: 
editor: markdown
dateCreated: 2022-08-10T09:25:54.252Z
---

<!-- Generator: Widdershins v4.0.1 -->

<h1 id="vora-rest-api">VORA Rest API v0.2 ES</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

VORA Telephony API Platform.

Base URLs:

* <a href="https://localhost:18443/vora">https://localhost:18443/vora</a>

* <a href="https://172.24.46.60:8443/vora">https://172.24.46.60:8443/vora</a>

* <a href="https://172.24.46.61:8443/vora">https://172.24.46.61:8443/vora</a>

* <a href="http://localhost:18085/vora">http://localhost:18085/vora</a>

* <a href="http://172.24.46.60:8085/vora">http://172.24.46.60:8085/vora</a>

* <a href="http://172.24.46.61:8085/vora">http://172.24.46.61:8085/vora</a>

* <a href="https://localhost:8443/vora">https://localhost:8443/vora</a>

# Authentication

- oAuth2 authentication. 

    - Flow: authorizationCode
    - Authorization URL = [http://172.24.61.14:9090/authorization/oauth2/authorize](http://172.24.61.14:9090/authorization/oauth2/authorize)
    - Token URL = [http://172.24.61.14:9090/authorization/oauth2/token](http://172.24.61.14:9090/authorization/oauth2/token)

|Scope|Scope Description|
|---|---|
|scope.vora.identities|Identities|
|scope.vora.calls|Call|
|scope.vora.presence|Presence|
|scope.vora.recording|Recording|

<h1 id="vora-rest-api-session">Session</h1>

VORA API session operations

## logout

<a id="opIdlogout"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://localhost:18443/vora/logout/{identity} \
  -H 'Accept: */*' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://localhost:18443/vora/logout/{identity} HTTP/1.1
Host: localhost:18443
Accept: */*

```

```javascript

const headers = {
  'Accept':'*/*',
  'Authorization':'Bearer {access-token}'
};

fetch('https://localhost:18443/vora/logout/{identity}',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => '*/*',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://localhost:18443/vora/logout/{identity}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://localhost:18443/vora/logout/{identity}', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => '*/*',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://localhost:18443/vora/logout/{identity}', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost:18443/vora/logout/{identity}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"*/*"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://localhost:18443/vora/logout/{identity}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /logout/{identity}`

*User Log Out*

The action will be used to clean up the existing REST and WS connections after the user log out.

<h3 id="logout-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|identity|path|string|true|User Identity|

> Example responses

> 400 Response

<h3 id="logout-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful operation|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|The access token is expired, revoked, malformed, or invalid for other reasons|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|The access token has insufficient scope|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not found|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Conflict|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
security_auth ( Scopes: scope.vora.identities )
</aside>

## events

<a id="opIdevents"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://localhost:18443/vora/identity/{identity}/eventSubscription \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://localhost:18443/vora/identity/{identity}/eventSubscription HTTP/1.1
Host: localhost:18443
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "subscribeAll": true,
  "events": [
    "callRinging",
    "presence",
    "callHeld"
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://localhost:18443/vora/identity/{identity}/eventSubscription',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://localhost:18443/vora/identity/{identity}/eventSubscription',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://localhost:18443/vora/identity/{identity}/eventSubscription', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://localhost:18443/vora/identity/{identity}/eventSubscription', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost:18443/vora/identity/{identity}/eventSubscription");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://localhost:18443/vora/identity/{identity}/eventSubscription", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /identity/{identity}/eventSubscription`

*Events Subscription*

It will be executed also right after the registration by default and the application will be subscribe the required events that it will be informed throughout its registered session. Although it is triggerred automatically in the registration, the application user can sent is anytime to update the subscription state. It is enabled for both user and manager modes..

> Body parameter

```json
{
  "subscribeAll": true,
  "events": [
    "callRinging",
    "presence",
    "callHeld"
  ]
}
```

<h3 id="events-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|identity|path|string|true|User Identity|
|body|body|[EventsIn](#schemaeventsin)|true|none|

> Example responses

> 400 Response

```json
{
  "timestamp": "2019-08-24T14:15:22Z",
  "status": "500",
  "error": "string",
  "message": "string"
}
```

<h3 id="events-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful operation|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|The access token is expired, revoked, malformed, or invalid for other reasons|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|The access token has insufficient scope|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not found|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Conflict|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
security_auth ( Scopes: scope.vora.identities )
</aside>

## setup

<a id="opIdsetup"></a>

> Code samples

```shell
# You can also use wget
curl -X POST https://localhost:18443/vora/identity/setup \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
POST https://localhost:18443/vora/identity/setup HTTP/1.1
Host: localhost:18443
Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "connectionType": "WebSocket",
  "identity": "910111000",
  "holdUpMode": false
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://localhost:18443/vora/identity/setup',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.post 'https://localhost:18443/vora/identity/setup',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.post('https://localhost:18443/vora/identity/setup', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Content-Type' => 'application/json',
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('POST','https://localhost:18443/vora/identity/setup', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost:18443/vora/identity/setup");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "https://localhost:18443/vora/identity/setup", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /identity/setup`

*User Initial Setup*

The action will be used to get the session setup right after the registration process by default. The application is required to provide the connectionType and it will be informed the subscriber phone number details for further usage.

> Body parameter

```json
{
  "connectionType": "WebSocket",
  "identity": "910111000",
  "holdUpMode": false
}
```

<h3 id="setup-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[SetupIn](#schemasetupin)|true|none|

> Example responses

> 200 Response

```json
{
  "webSocketToken": "<todo>"
}
```

<h3 id="setup-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful operation|[SetupOut](#schemasetupout)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|The access token is expired, revoked, malformed, or invalid for other reasons|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|The access token has insufficient scope|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not found|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Conflict|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
security_auth ( Scopes: scope.vora.identities )
</aside>

## identities

<a id="opIdidentities"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost:18443/vora/identity \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer {access-token}'

```

```http
GET https://localhost:18443/vora/identity HTTP/1.1
Host: localhost:18443
Accept: application/json

```

```javascript

const headers = {
  'Accept':'application/json',
  'Authorization':'Bearer {access-token}'
};

fetch('https://localhost:18443/vora/identity',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'Bearer {access-token}'
}

result = RestClient.get 'https://localhost:18443/vora/identity',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer {access-token}'
}

r = requests.get('https://localhost:18443/vora/identity', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => 'application/json',
    'Authorization' => 'Bearer {access-token}',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost:18443/vora/identity', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost:18443/vora/identity");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"Bearer {access-token}"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost:18443/vora/identity", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /identity`

*Get Identity*

VORA user can register with the defined username and password on the application but the selection for the preferred identity that it wants to use during the VORA session can change.

> Example responses

> 200 Response

```json
{
  "identities": [
    "602128708",
    "942788701",
    "915510577"
  ]
}
```

<h3 id="identities-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Successful operation|[IdentityOut](#schemaidentityout)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Bad Request|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|The access token is expired, revoked, malformed, or invalid for other reasons|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|The access token has insufficient scope|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not found|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|Conflict|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|
|500|[Internal Server Error](https://tools.ietf.org/html/rfc7231#section-6.6.1)|Internal Server Error|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
security_auth ( Scopes: scope.vora.identities )
</aside>

## identitiesOptions

<a id="opIdidentitiesOptions"></a>

> Code samples

```shell
# You can also use wget
curl -X OPTIONS https://localhost:18443/vora/identity \
  -H 'Accept: */*'

```

```http
OPTIONS https://localhost:18443/vora/identity HTTP/1.1
Host: localhost:18443
Accept: */*

```

```javascript

const headers = {
  'Accept':'*/*'
};

fetch('https://localhost:18443/vora/identity',
{
  method: 'OPTIONS',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => '*/*'
}

result = RestClient.options 'https://localhost:18443/vora/identity',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*'
}

r = requests.options('https://localhost:18443/vora/identity', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => '*/*',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('OPTIONS','https://localhost:18443/vora/identity', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost:18443/vora/identity");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("OPTIONS");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"*/*"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("OPTIONS", "https://localhost:18443/vora/identity", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`OPTIONS /identity`

> Example responses

> 200 Response

<h3 id="identitiesoptions-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|[IdentityOut](#schemaidentityout)|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="vora-rest-api-health">Health</h1>

VORA API Health operations

## readiness

<a id="opIdreadiness"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost:18443/vora/health/readiness \
  -H 'Accept: */*'

```

```http
GET https://localhost:18443/vora/health/readiness HTTP/1.1
Host: localhost:18443
Accept: */*

```

```javascript

const headers = {
  'Accept':'*/*'
};

fetch('https://localhost:18443/vora/health/readiness',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => '*/*'
}

result = RestClient.get 'https://localhost:18443/vora/health/readiness',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*'
}

r = requests.get('https://localhost:18443/vora/health/readiness', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => '*/*',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost:18443/vora/health/readiness', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost:18443/vora/health/readiness");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"*/*"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost:18443/vora/health/readiness", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /health/readiness`

*Readiness*

Check readiness status of the service.

> Example responses

> 204 Response

<h3 id="readiness-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|string|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|

<aside class="success">
This operation does not require authentication
</aside>

## liveness

<a id="opIdliveness"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://localhost:18443/vora/health/liveness \
  -H 'Accept: */*'

```

```http
GET https://localhost:18443/vora/health/liveness HTTP/1.1
Host: localhost:18443
Accept: */*

```

```javascript

const headers = {
  'Accept':'*/*'
};

fetch('https://localhost:18443/vora/health/liveness',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => '*/*'
}

result = RestClient.get 'https://localhost:18443/vora/health/liveness',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*'
}

r = requests.get('https://localhost:18443/vora/health/liveness', headers = headers)

print(r.json())

```

```php
<?php

require 'vendor/autoload.php';

$headers = array(
    'Accept' => '*/*',
);

$client = new \GuzzleHttp\Client();

// Define array of request body.
$request_body = array();

try {
    $response = $client->request('GET','https://localhost:18443/vora/health/liveness', array(
        'headers' => $headers,
        'json' => $request_body,
       )
    );
    print_r($response->getBody()->getContents());
 }
 catch (\GuzzleHttp\Exception\BadResponseException $e) {
    // handle exception or api errors.
    print_r($e->getMessage());
 }

 // ...

```

```java
URL obj = new URL("https://localhost:18443/vora/health/liveness");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"*/*"},
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "https://localhost:18443/vora/health/liveness", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /health/liveness`

*Liveness*

Check liveness status of the service.

> Example responses

> 503 Response

<h3 id="liveness-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No Content|None|
|503|[Service Unavailable](https://tools.ietf.org/html/rfc7231#section-6.6.4)|Service Unavailable|[ResponseStatusVoraError](#schemaresponsestatusvoraerror)|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocS_ResponseStatusVoraError">ResponseStatusVoraError</h2>
<!-- backwards compatibility -->
<a id="schemaresponsestatusvoraerror"></a>
<a id="schema_ResponseStatusVoraError"></a>
<a id="tocSresponsestatusvoraerror"></a>
<a id="tocsresponsestatusvoraerror"></a>

```json
{
  "timestamp": "2019-08-24T14:15:22Z",
  "status": "500",
  "error": "string",
  "message": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|timestamp|string(date-time)|true|none|none|
|status|string|true|none|none|
|error|string|true|none|none|
|message|string|true|none|none|

<h2 id="tocS_EventsIn">EventsIn</h2>
<!-- backwards compatibility -->
<a id="schemaeventsin"></a>
<a id="schema_EventsIn"></a>
<a id="tocSeventsin"></a>
<a id="tocseventsin"></a>

```json
{
  "subscribeAll": true,
  "events": [
    "callRinging",
    "presence",
    "callHeld"
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|subscribeAll|boolean|true|none|By default, for the all allowed events.|
|events|[string]|false|none|Optional, the list of the events that application is allowed to receive.<br>If the events parameter is empty and subscribeAll is false, then the user will unsubscribe from the events action and will not receive any informative events during the deregistration process.|

<h2 id="tocS_SetupIn">SetupIn</h2>
<!-- backwards compatibility -->
<a id="schemasetupin"></a>
<a id="schema_SetupIn"></a>
<a id="tocSsetupin"></a>
<a id="tocssetupin"></a>

```json
{
  "connectionType": "WebSocket",
  "identity": "910111000",
  "holdUpMode": false
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|connectionType|string|true|none|This parameter will provide the information about the connection type for the application.|
|identity|string|true|none|The VORA user will provide one of its identities to use the VORA session. For the User and Manager mode, it should be the phone number with the VORA service to be able to use the call control features. For the OTT users, only the fixed number will be allowed as the OneNet defined number. In the administrator mode, the user identity will be the username since there is no phone number assigned to the user.|
|holdUpMode|boolean|false|none|It is allowed only for the soft clients running on the mobile phones, where the web application should initiate a push notification for the terminating calls to get the readiness of the client.|

<h2 id="tocS_SetupOut">SetupOut</h2>
<!-- backwards compatibility -->
<a id="schemasetupout"></a>
<a id="schema_SetupOut"></a>
<a id="tocSsetupout"></a>
<a id="tocssetupout"></a>

```json
{
  "webSocketToken": "<todo>"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|webSocketToken|string|true|none|This will be used to authenticate the WebSocket connection which is different than the access token and will be created by the VORA Gateway. Hence this connection will be independent from the oAuth server.|

<h2 id="tocS_IdentityOut">IdentityOut</h2>
<!-- backwards compatibility -->
<a id="schemaidentityout"></a>
<a id="schema_IdentityOut"></a>
<a id="tocSidentityout"></a>
<a id="tocsidentityout"></a>

```json
{
  "identities": [
    "602128708",
    "942788701",
    "915510577"
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|identities|[string]|true|none|The list of the identities assigned the VORA service.|

