---
title: Vota-MD
description: 
published: true
date: 2022-08-02T14:36:45.780Z
tags: 
editor: markdown
dateCreated: 2022-08-02T14:36:45.780Z
---

# VORA Rest API

> Version 0.2

VORA Telephony API Platform.

## Path Table

| Method | Path | Description |
| --- | --- | --- |
| POST | [/logout/{identity}](#postlogoutidentity) | User Log Out |
| POST | [/identity/{identity}/eventSubscription](#postidentityidentityeventsubscription) | Events Subscription |
| POST | [/identity/setup](#postidentitysetup) | User Initial Setup |
| GET | [/identity](#getidentity) | Get Identity |
| OPTIONS | [/identity](#optionsidentity) |  |
| GET | [/health/readiness](#gethealthreadiness) | Readiness |
| GET | [/health/liveness](#gethealthliveness) | Liveness |

## Reference Table

| Name | Path | Description |
| --- | --- | --- |
| ResponseStatusVoraError | [#/components/schemas/ResponseStatusVoraError](#componentsschemasresponsestatusvoraerror) |  |
| EventsIn | [#/components/schemas/EventsIn](#componentsschemaseventsin) |  |
| SetupIn | [#/components/schemas/SetupIn](#componentsschemassetupin) |  |
| SetupOut | [#/components/schemas/SetupOut](#componentsschemassetupout) |  |
| IdentityOut | [#/components/schemas/IdentityOut](#componentsschemasidentityout) |  |
| security_auth | [#/components/securitySchemes/security_auth](#componentssecurityschemessecurity_auth) |  |

## Path Details

***

### [POST]/logout/{identity}

- Summary  
User Log Out

- Description  
The action will be used to clean up the existing REST and WS connections after the user log out.

- Security  
security_auth  

#### Responses

- 200 Successful operation

- 400 Bad Request

`*/*`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 401 The access token is expired, revoked, malformed, or invalid for other reasons

`*/*`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 403 The access token has insufficient scope

`*/*`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 404 Not found

`*/*`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 409 Conflict

`*/*`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 500 Internal Server Error

`*/*`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

***

### [POST]/identity/{identity}/eventSubscription

- Summary  
Events Subscription

- Description  
It will be executed also right after the registration by default and the application will be subscribe the required events that it will be informed throughout its registered session. Although it is triggerred automatically in the registration, the application user can sent is anytime to update the subscription state. It is enabled for both user and manager modes..

- Security  
security_auth  

#### RequestBody

- application/json

```ts
{
  // By default, for the all allowed events.
  subscribeAll: boolean
  events?: string[]
}
```

#### Responses

- 200 Successful operation

- 400 Bad Request

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 401 The access token is expired, revoked, malformed, or invalid for other reasons

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 403 The access token has insufficient scope

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 404 Not found

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 409 Conflict

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 500 Internal Server Error

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

***

### [POST]/identity/setup

- Summary  
User Initial Setup

- Description  
The action will be used to get the session setup right after the registration process by default. The application is required to provide the connectionType and it will be informed the subscriber phone number details for further usage.

- Security  
security_auth  

#### RequestBody

- application/json

```ts
{
  // This parameter will provide the information about the connection type for the application.
  connectionType: string
  // The VORA user will provide one of its identities to use the VORA session. For the User and Manager mode, it should be the phone number with the VORA service to be able to use the call control features. For the OTT users, only the fixed number will be allowed as the OneNet defined number. In the administrator mode, the user identity will be the username since there is no phone number assigned to the user.
  identity: string
  // It is allowed only for the soft clients running on the mobile phones, where the web application should initiate a push notification for the terminating calls to get the readiness of the client.
  holdUpMode?: boolean
}
```

#### Responses

- 200 Successful operation

`application/json`

```ts
{
  // This will be used to authenticate the WebSocket connection which is different than the access token and will be created by the VORA Gateway. Hence this connection will be independent from the oAuth server.
  webSocketToken: string
}
```

- 400 Bad Request

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 401 The access token is expired, revoked, malformed, or invalid for other reasons

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 403 The access token has insufficient scope

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 404 Not found

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 409 Conflict

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 500 Internal Server Error

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

***

### [GET]/identity

- Summary  
Get Identity

- Description  
VORA user can register with the defined username and password on the application but the selection for the preferred identity that it wants to use during the VORA session can change.

- Security  
security_auth  

#### Responses

- 200 Successful operation

`application/json`

```ts
{
  identities?: string[]
}
```

- 400 Bad Request

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 401 The access token is expired, revoked, malformed, or invalid for other reasons

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 403 The access token has insufficient scope

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 404 Not found

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 409 Conflict

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

- 500 Internal Server Error

`application/json`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

***

### [OPTIONS]/identity

#### Responses

- 200 OK

`*/*`

```ts
{
  identities?: string[]
}
```

***

### [GET]/health/readiness

- Summary  
Readiness

- Description  
Check readiness status of the service.

#### Responses

- 204 No Content

`*/*`

```ts
{
  "type": "string"
}
```

- 503 Service Unavailable

`*/*`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

***

### [GET]/health/liveness

- Summary  
Liveness

- Description  
Check liveness status of the service.

#### Responses

- 204 No Content

- 503 Service Unavailable

`*/*`

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

## References

### #/components/schemas/ResponseStatusVoraError

```ts
{
  timestamp: string
  status: string
  error: string
  message: string
}
```

### #/components/schemas/EventsIn

```ts
{
  // By default, for the all allowed events.
  subscribeAll: boolean
  events?: string[]
}
```

### #/components/schemas/SetupIn

```ts
{
  // This parameter will provide the information about the connection type for the application.
  connectionType: string
  // The VORA user will provide one of its identities to use the VORA session. For the User and Manager mode, it should be the phone number with the VORA service to be able to use the call control features. For the OTT users, only the fixed number will be allowed as the OneNet defined number. In the administrator mode, the user identity will be the username since there is no phone number assigned to the user.
  identity: string
  // It is allowed only for the soft clients running on the mobile phones, where the web application should initiate a push notification for the terminating calls to get the readiness of the client.
  holdUpMode?: boolean
}
```

### #/components/schemas/SetupOut

```ts
{
  // This will be used to authenticate the WebSocket connection which is different than the access token and will be created by the VORA Gateway. Hence this connection will be independent from the oAuth server.
  webSocketToken: string
}
```

### #/components/schemas/IdentityOut

```ts
{
  identities?: string[]
}
```

### #/components/securitySchemes/security_auth

```ts
```