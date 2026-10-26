# User

Operations about user

```php
$userApi = $client->getUserApi();
```

## Class Name

`UserApi`

## Methods

* [Create User](../../doc/controllers/user.md#create-user)
* [Create Users with List Input](../../doc/controllers/user.md#create-users-with-list-input)
* [Login User](../../doc/controllers/user.md#login-user)
* [Logout User](../../doc/controllers/user.md#logout-user)
* [Get User by Name](../../doc/controllers/user.md#get-user-by-name)
* [Update User](../../doc/controllers/user.md#update-user)
* [Delete User](../../doc/controllers/user.md#delete-user)


# Create User

This can only be done by the logged in user.

:information_source: **Note** This endpoint does not require authentication.

```php
function createUser(
    ?int $id = null,
    ?string $username = null,
    ?string $firstName = null,
    ?string $lastName = null,
    ?string $email = null,
    ?string $password = null,
    ?string $phone = null,
    ?int $userStatus = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `?int` | Form, Optional | - |
| `username` | `?string` | Form, Optional | - |
| `firstName` | `?string` | Form, Optional | - |
| `lastName` | `?string` | Form, Optional | - |
| `email` | `?string` | Form, Optional | - |
| `password` | `?string` | Form, Optional | - |
| `phone` | `?string` | Form, Optional | - |
| `userStatus` | `?int` | Form, Optional | User Status |

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`User`](../../doc/models/user.md).

## Example Usage

```php
$id = 10;

$username = 'theUser';

$firstName = 'John';

$lastName = 'James';

$email = 'john@email.com';

$password = '12345';

$phone = '12345';

$userStatus = 1;

$userApi = $client->getUserApi();
$apiResponse = $userApi->createUser(
    $id,
    $username,
    $firstName,
    $lastName,
    $email,
    $password,
    $phone,
    $userStatus
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'User:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| Default | Unexpected error | `ApiException` |


# Create Users with List Input

Creates list of users with given input array.

:information_source: **Note** This endpoint does not require authentication.

```php
function createUsersWithListInput(?array $body = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`?(User[])`](../../doc/models/user.md) | Body, Optional | - |

## Response Type

**200**: Successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`User`](../../doc/models/user.md).

## Example Usage

```php
$body = [
    UserBuilder::init()->build()
];

$userApi = $client->getUserApi();
$apiResponse = $userApi->createUsersWithListInput($body);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'User:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| Default | Unexpected error | `ApiException` |


# Login User

Log into the system.

:information_source: **Note** This endpoint does not require authentication.

```php
function loginUser(?string $username = null, ?string $password = null): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `username` | `?string` | Query, Optional | The user name for login |
| `password` | `?string` | Query, Optional | The password for login in clear text |

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type `string`.

## Example Usage

```php
$userApi = $client->getUserApi();
$apiResponse = $userApi->loginUser();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'string:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Invalid username/password supplied | `ApiException` |
| Default | Unexpected error | `ApiException` |


# Logout User

Log user out of the system.

:information_source: **Note** This endpoint does not require authentication.

```php
function logoutUser(): ApiResponse
```

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$userApi = $client->getUserApi();
$apiResponse = $userApi->logoutUser();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'void:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| Default | Unexpected error | `ApiException` |


# Get User by Name

Get user detail based on username.

:information_source: **Note** This endpoint does not require authentication.

```php
function getUserByName(string $usersname): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `usersname` | `string` | Template, Required | The username that needs to be processed |

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`User`](../../doc/models/user.md).

## Example Usage

```php
$usersname = 'usersname0';

$userApi = $client->getUserApi();
$apiResponse = $userApi->getUserByName($usersname);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'User:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Invalid username supplied | `ApiException` |
| 404 | User not found | `ApiException` |
| Default | Unexpected error | `ApiException` |


# Update User

This can only be done by the logged in user.

:information_source: **Note** This endpoint does not require authentication.

```php
function updateUser(
    string $usersname,
    ?int $id = null,
    ?string $username = null,
    ?string $firstName = null,
    ?string $lastName = null,
    ?string $email = null,
    ?string $password = null,
    ?string $phone = null,
    ?int $userStatus = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `usersname` | `string` | Template, Required | The username that needs to be processed |
| `id` | `?int` | Form, Optional | - |
| `username` | `?string` | Form, Optional | - |
| `firstName` | `?string` | Form, Optional | - |
| `lastName` | `?string` | Form, Optional | - |
| `email` | `?string` | Form, Optional | - |
| `password` | `?string` | Form, Optional | - |
| `phone` | `?string` | Form, Optional | - |
| `userStatus` | `?int` | Form, Optional | User Status |

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$usersname = 'usersname0';

$id = 10;

$username = 'theUser';

$firstName = 'John';

$lastName = 'James';

$email = 'john@email.com';

$password = '12345';

$phone = '12345';

$userStatus = 1;

$userApi = $client->getUserApi();
$apiResponse = $userApi->updateUser(
    $usersname,
    $id,
    $username,
    $firstName,
    $lastName,
    $email,
    $password,
    $phone,
    $userStatus
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'void:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | bad request | `ApiException` |
| 404 | user not found | `ApiException` |
| Default | Unexpected error | `ApiException` |


# Delete User

This can only be done by the logged in user.

:information_source: **Note** This endpoint does not require authentication.

```php
function deleteUser(string $usersname): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `usersname` | `string` | Template, Required | The username that needs to be processed |

## Response Type

**200**: User deleted

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$usersname = 'usersname0';

$userApi = $client->getUserApi();
$apiResponse = $userApi->deleteUser($usersname);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'void:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Invalid username supplied | `ApiException` |
| 404 | User not found | `ApiException` |
| Default | Unexpected error | `ApiException` |

