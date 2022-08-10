---
title: Pet-MD
description: 
published: true
date: 2022-08-10T06:44:59.790Z
tags: 
editor: markdown
dateCreated: 2022-08-10T06:44:59.790Z
---

# Swagger Petstore - OpenAPI 3.0

> Version 1.0.11

This is a sample Pet Store Server based on the OpenAPI 3.0 specification.  You can find out more about
Swagger at [https://swagger.io](https://swagger.io). In the third iteration of the pet store, we've switched to the design first approach!
You can now help us improve the API whether it's by making changes to the definition itself or to the code.
That way, with time, we can improve the API in general, and expose some of the new features in OAS3.

_If you're looking for the Swagger 2.0/OAS 2.0 version of Petstore, then click [here](https://editor.swagger.io/?url=https://petstore.swagger.io/v2/swagger.yaml). Alternatively, you can load via the `Edit > Load Petstore OAS 2.0` menu option!_

Some useful links:
- [The Pet Store repository](https://github.com/swagger-api/swagger-petstore)
- [The source API definition for the Pet Store](https://github.com/swagger-api/swagger-petstore/blob/master/src/main/resources/openapi.yaml)

## Path Table

| Method | Path | Description |
| --- | --- | --- |
| PUT | [/pet](#putpet) | Update an existing pet |
| POST | [/pet](#postpet) | Add a new pet to the store |
| GET | [/pet/findByStatus](#getpetfindbystatus) | Finds Pets by status |
| GET | [/pet/findByTags](#getpetfindbytags) | Finds Pets by tags |
| GET | [/pet/{petId}](#getpetpetid) | Find pet by ID |
| POST | [/pet/{petId}](#postpetpetid) | Updates a pet in the store with form data |
| DELETE | [/pet/{petId}](#deletepetpetid) | Deletes a pet |
| POST | [/pet/{petId}/uploadImage](#postpetpetiduploadimage) | uploads an image |
| GET | [/store/inventory](#getstoreinventory) | Returns pet inventories by status |
| POST | [/store/order](#poststoreorder) | Place an order for a pet |
| GET | [/store/order/{orderId}](#getstoreorderorderid) | Find purchase order by ID |
| DELETE | [/store/order/{orderId}](#deletestoreorderorderid) | Delete purchase order by ID |
| POST | [/user](#postuser) | Create user |
| POST | [/user/createWithList](#postusercreatewithlist) | Creates list of users with given input array |
| GET | [/user/login](#getuserlogin) | Logs user into the system |
| GET | [/user/logout](#getuserlogout) | Logs out current logged in user session |
| GET | [/user/{username}](#getuserusername) | Get user by user name |
| PUT | [/user/{username}](#putuserusername) | Update user |
| DELETE | [/user/{username}](#deleteuserusername) | Delete user |

## Reference Table

| Name | Path | Description |
| --- | --- | --- |
| Order | [#/components/schemas/Order](#componentsschemasorder) |  |
| Customer | [#/components/schemas/Customer](#componentsschemascustomer) |  |
| Address | [#/components/schemas/Address](#componentsschemasaddress) |  |
| Category | [#/components/schemas/Category](#componentsschemascategory) |  |
| User | [#/components/schemas/User](#componentsschemasuser) |  |
| Tag | [#/components/schemas/Tag](#componentsschemastag) |  |
| Pet | [#/components/schemas/Pet](#componentsschemaspet) |  |
| ApiResponse | [#/components/schemas/ApiResponse](#componentsschemasapiresponse) |  |
| Pet | [#/components/requestBodies/Pet](#componentsrequestbodiespet) | Pet object that needs to be added to the store |
| UserArray | [#/components/requestBodies/UserArray](#componentsrequestbodiesuserarray) | List of user object |
| petstore_auth | [#/components/securitySchemes/petstore_auth](#componentssecurityschemespetstore_auth) |  |
| api_key | [#/components/securitySchemes/api_key](#componentssecurityschemesapi_key) |  |

## Path Details

***

### [PUT]/pet

- Summary  
Update an existing pet

- Description  
Update an existing pet by Id

- Security  
petstore_auth  

#### RequestBody

- application/json

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

- application/xml

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

- application/x-www-form-urlencoded

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

#### Responses

- 200 Successful operation

`application/json`

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

`application/xml`

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

- 400 Invalid ID supplied

- 404 Pet not found

- 405 Validation exception

***

### [POST]/pet

- Summary  
Add a new pet to the store

- Description  
Add a new pet to the store

- Security  
petstore_auth  

#### RequestBody

- application/json

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

- application/xml

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

- application/x-www-form-urlencoded

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

#### Responses

- 200 Successful operation

`application/json`

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

`application/xml`

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

- 405 Invalid input

***

### [GET]/pet/findByStatus

- Summary  
Finds Pets by status

- Description  
Multiple status values can be provided with comma separated strings

- Security  
petstore_auth  

#### Parameters(Query)

```ts
status?: string
```

#### Responses

- 200 successful operation

`application/json`

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}[]
```

`application/xml`

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}[]
```

- 400 Invalid status value

***

### [GET]/pet/findByTags

- Summary  
Finds Pets by tags

- Description  
Multiple tags can be provided with comma separated strings. Use tag1, tag2, tag3 for testing.

- Security  
petstore_auth  

#### Parameters(Query)

```ts
tags?: string[]
```

#### Responses

- 200 successful operation

`application/json`

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}[]
```

`application/xml`

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}[]
```

- 400 Invalid tag value

***

### [GET]/pet/{petId}

- Summary  
Find pet by ID

- Description  
Returns a single pet

- Security  
api_key  
petstore_auth  

#### Responses

- 200 successful operation

`application/json`

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

`application/xml`

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

- 400 Invalid ID supplied

- 404 Pet not found

***

### [POST]/pet/{petId}

- Summary  
Updates a pet in the store with form data

- Security  
petstore_auth  

#### Parameters(Query)

```ts
name?: string
```

```ts
status?: string
```

#### Responses

- 405 Invalid input

***

### [DELETE]/pet/{petId}

- Summary  
Deletes a pet

- Description  
delete a pet

- Security  
petstore_auth  

#### Headers

```ts
api_key?: string
```

#### Responses

- 400 Invalid pet value

***

### [POST]/pet/{petId}/uploadImage

- Summary  
uploads an image

- Security  
petstore_auth  

#### Parameters(Query)

```ts
additionalMetadata?: string
```

#### RequestBody

- application/octet-stream

```ts
{
  "type": "string",
  "format": "binary"
}
```

#### Responses

- 200 successful operation

`application/json`

```ts
{
  code?: integer
  type?: string
  message?: string
}
```

***

### [GET]/store/inventory

- Summary  
Returns pet inventories by status

- Description  
Returns a map of status codes to quantities

- Security  
api_key  

#### Responses

- 200 successful operation

`application/json`

```ts
{
}
```

***

### [POST]/store/order

- Summary  
Place an order for a pet

- Description  
Place a new order in the store

#### RequestBody

- application/json

```ts
{
  id?: integer
  petId?: integer
  quantity?: integer
  shipDate?: string
  // Order Status
  status?: string
  complete?: boolean
}
```

- application/xml

```ts
{
  id?: integer
  petId?: integer
  quantity?: integer
  shipDate?: string
  // Order Status
  status?: string
  complete?: boolean
}
```

- application/x-www-form-urlencoded

```ts
{
  id?: integer
  petId?: integer
  quantity?: integer
  shipDate?: string
  // Order Status
  status?: string
  complete?: boolean
}
```

#### Responses

- 200 successful operation

`application/json`

```ts
{
  id?: integer
  petId?: integer
  quantity?: integer
  shipDate?: string
  // Order Status
  status?: string
  complete?: boolean
}
```

- 405 Invalid input

***

### [GET]/store/order/{orderId}

- Summary  
Find purchase order by ID

- Description  
For valid response try integer IDs with value <= 5 or > 10. Other values will generate exceptions.

#### Responses

- 200 successful operation

`application/json`

```ts
{
  id?: integer
  petId?: integer
  quantity?: integer
  shipDate?: string
  // Order Status
  status?: string
  complete?: boolean
}
```

`application/xml`

```ts
{
  id?: integer
  petId?: integer
  quantity?: integer
  shipDate?: string
  // Order Status
  status?: string
  complete?: boolean
}
```

- 400 Invalid ID supplied

- 404 Order not found

***

### [DELETE]/store/order/{orderId}

- Summary  
Delete purchase order by ID

- Description  
For valid response try integer IDs with value < 1000. Anything above 1000 or nonintegers will generate API errors

#### Responses

- 400 Invalid ID supplied

- 404 Order not found

***

### [POST]/user

- Summary  
Create user

- Description  
This can only be done by the logged in user.

#### RequestBody

- application/json

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}
```

- application/xml

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}
```

- application/x-www-form-urlencoded

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}
```

#### Responses

- default successful operation

`application/json`

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}
```

`application/xml`

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}
```

***

### [POST]/user/createWithList

- Summary  
Creates list of users with given input array

- Description  
Creates list of users with given input array

#### RequestBody

- application/json

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}[]
```

#### Responses

- 200 Successful operation

`application/json`

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}
```

`application/xml`

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}
```

- default successful operation

***

### [GET]/user/login

- Summary  
Logs user into the system

#### Parameters(Query)

```ts
username?: string
```

```ts
password?: string
```

#### Responses

- 200 successful operation

`application/xml`

```ts
{
  "type": "string"
}
```

`application/json`

```ts
{
  "type": "string"
}
```

- 400 Invalid username/password supplied

***

### [GET]/user/logout

- Summary  
Logs out current logged in user session

#### Responses

- default successful operation

***

### [GET]/user/{username}

- Summary  
Get user by user name

#### Responses

- 200 successful operation

`application/json`

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}
```

`application/xml`

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}
```

- 400 Invalid username supplied

- 404 User not found

***

### [PUT]/user/{username}

- Summary  
Update user

- Description  
This can only be done by the logged in user.

#### RequestBody

- application/json

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}
```

- application/xml

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}
```

- application/x-www-form-urlencoded

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}
```

#### Responses

- default successful operation

***

### [DELETE]/user/{username}

- Summary  
Delete user

- Description  
This can only be done by the logged in user.

#### Responses

- 400 Invalid username supplied

- 404 User not found

## References

### #/components/schemas/Order

```ts
{
  id?: integer
  petId?: integer
  quantity?: integer
  shipDate?: string
  // Order Status
  status?: string
  complete?: boolean
}
```

### #/components/schemas/Customer

```ts
{
  id?: integer
  username?: string
  address: {
    street?: string
    city?: string
    state?: string
    zip?: string
  }[]
}
```

### #/components/schemas/Address

```ts
{
  street?: string
  city?: string
  state?: string
  zip?: string
}
```

### #/components/schemas/Category

```ts
{
  id?: integer
  name?: string
}
```

### #/components/schemas/User

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}
```

### #/components/schemas/Tag

```ts
{
  id?: integer
  name?: string
}
```

### #/components/schemas/Pet

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

### #/components/schemas/ApiResponse

```ts
{
  code?: integer
  type?: string
  message?: string
}
```

### #/components/requestBodies/Pet

- application/json

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

- application/xml

```ts
{
  id?: integer
  name: string
  category: {
    id?: integer
    name?: string
  }
  photoUrls?: string[]
  tags: {
    id?: integer
    name?: string
  }[]
  // pet status in the store
  status?: string
}
```

### #/components/requestBodies/UserArray

- application/json

```ts
{
  id?: integer
  username?: string
  firstName?: string
  lastName?: string
  email?: string
  password?: string
  phone?: string
  // User Status
  userStatus?: integer
}[]
```

### #/components/securitySchemes/petstore_auth

```ts
{
  "type": "oauth2",
  "flows": {
    "implicit": {
      "authorizationUrl": "https://petstore3.swagger.io/oauth/authorize",
      "scopes": {
        "write:pets": "modify pets in your account",
        "read:pets": "read your pets"
      }
    }
  }
}
```

### #/components/securitySchemes/api_key

```ts
```