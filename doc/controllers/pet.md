# Pet

Everything about your Pets

Find out more: [https://swagger.io](https://swagger.io)

```php
$petApi = $client->getPetApi();
```

## Class Name

`PetApi`

## Methods

* [Update Pet](../../doc/controllers/pet.md#update-pet)
* [Add Pet](../../doc/controllers/pet.md#add-pet)
* [Find Pets by Status](../../doc/controllers/pet.md#find-pets-by-status)
* [Find Pets by Tags](../../doc/controllers/pet.md#find-pets-by-tags)
* [Get Pet by Id](../../doc/controllers/pet.md#get-pet-by-id)
* [Update Pet with Form](../../doc/controllers/pet.md#update-pet-with-form)
* [Delete Pet](../../doc/controllers/pet.md#delete-pet)
* [Upload File](../../doc/controllers/pet.md#upload-file)


# Update Pet

Update an existing pet by Id.

```php
function updatePet(
    string $name,
    array $photoUrls,
    ?int $id = null,
    ?Category $category = null,
    ?array $tags = null,
    ?string $status = null
): ApiResponse
```

## Authentication

This endpoint requires [petstore_auth](../../doc/auth/oauth-2-implicit-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `name` | `string` | Form, Required | - |
| `photoUrls` | `string[]` | Form, Required | - |
| `id` | `?int` | Form, Optional | - |
| `category` | [`?Category`](../../doc/models/category.md) | Form, Optional | - |
| `tags` | [`?(Tag[])`](../../doc/models/tag.md) | Form, Optional | - |
| `status` | [`?string(PetStatus)`](../../doc/models/pet-status.md) | Form, Optional | pet status in the store |

## Requires scope

### petstore_auth

`read:pets`, `write:pets`

## Response Type

**200**: Successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Pet`](../../doc/models/pet.md).

## Example Usage

```php
$name = 'doggie';

$photoUrls = [
    'photoUrls5',
    'photoUrls6',
    'photoUrls7'
];

$id = 10;

$tags = [
    TagBuilder::init()->build()
];

$petApi = $client->getPetApi();
$apiResponse = $petApi->updatePet(
    $name,
    $photoUrls,
    $id,
    null,
    $tags
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Pet:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Invalid ID supplied | `ApiException` |
| 404 | Pet not found | `ApiException` |
| 422 | Validation exception | `ApiException` |
| Default | Unexpected error | `ApiException` |


# Add Pet

Add a new pet to the store.

```php
function addPet(
    string $name,
    array $photoUrls,
    ?int $id = null,
    ?Category $category = null,
    ?array $tags = null,
    ?string $status = null
): ApiResponse
```

## Authentication

This endpoint requires [petstore_auth](../../doc/auth/oauth-2-implicit-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `name` | `string` | Form, Required | - |
| `photoUrls` | `string[]` | Form, Required | - |
| `id` | `?int` | Form, Optional | - |
| `category` | [`?Category`](../../doc/models/category.md) | Form, Optional | - |
| `tags` | [`?(Tag[])`](../../doc/models/tag.md) | Form, Optional | - |
| `status` | [`?string(PetStatus)`](../../doc/models/pet-status.md) | Form, Optional | pet status in the store |

## Requires scope

### petstore_auth

`read:pets`, `write:pets`

## Response Type

**200**: Successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Pet`](../../doc/models/pet.md).

## Example Usage

```php
$name = 'doggie';

$photoUrls = [
    'photoUrls5',
    'photoUrls6',
    'photoUrls7'
];

$id = 10;

$tags = [
    TagBuilder::init()->build()
];

$petApi = $client->getPetApi();
$apiResponse = $petApi->addPet(
    $name,
    $photoUrls,
    $id,
    null,
    $tags
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Pet:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Invalid input | `ApiException` |
| 422 | Validation exception | `ApiException` |
| Default | Unexpected error | `ApiException` |


# Find Pets by Status

Multiple status values can be provided with comma separated strings.

```php
function findPetsByStatus(?string $status = null): ApiResponse
```

## Authentication

This endpoint requires [petstore_auth](../../doc/auth/oauth-2-implicit-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `status` | [`?string(PetStatus)`](../../doc/models/pet-status.md) | Query, Optional | Status values that need to be considered for filter |

## Requires scope

### petstore_auth

`read:pets`, `write:pets`

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Pet[]`](../../doc/models/pet.md).

## Example Usage

```php
$petApi = $client->getPetApi();
$apiResponse = $petApi->findPetsByStatus();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Pet[]:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Invalid status value | `ApiException` |
| Default | Unexpected error | `ApiException` |


# Find Pets by Tags

Multiple tags can be provided with comma separated strings. Use tag1, tag2, tag3 for testing.

```php
function findPetsByTags(?array $tags = null): ApiResponse
```

## Authentication

This endpoint requires [petstore_auth](../../doc/auth/oauth-2-implicit-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `tags` | `?(string[])` | Query, Optional | Tags to filter by |

## Requires scope

### petstore_auth

`read:pets`, `write:pets`

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Pet[]`](../../doc/models/pet.md).

## Example Usage

```php
$petApi = $client->getPetApi();
$apiResponse = $petApi->findPetsByTags();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Pet[]:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Invalid tag value | `ApiException` |
| Default | Unexpected error | `ApiException` |


# Get Pet by Id

Returns a single pet.

```php
function getPetById(int $petId): ApiResponse
```

## Authentication

This endpoint requires [api_key](../../doc/auth/custom-header-signature.md) **OR** [petstore_auth](../../doc/auth/oauth-2-implicit-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `petId` | `int` | Template, Required | ID of pet to return |

## Requires scope

### petstore_auth

`read:pets`, `write:pets`

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Pet`](../../doc/models/pet.md).

## Example Usage

```php
$petId = 10;

$petApi = $client->getPetApi();
$apiResponse = $petApi->getPetById($petId);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Pet:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Invalid ID supplied | `ApiException` |
| 404 | Pet not found | `ApiException` |
| Default | Unexpected error | `ApiException` |


# Update Pet with Form

Updates a pet resource based on the form data.

```php
function updatePetWithForm(int $petId, ?string $name = null, ?string $status = null): ApiResponse
```

## Authentication

This endpoint requires [petstore_auth](../../doc/auth/oauth-2-implicit-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `petId` | `int` | Template, Required | ID of pet that needs to be updated |
| `name` | `?string` | Query, Optional | Name of pet that needs to be updated |
| `status` | `?string` | Query, Optional | Status of pet that needs to be updated |

## Requires scope

### petstore_auth

`read:pets`, `write:pets`

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Pet`](../../doc/models/pet.md).

## Example Usage

```php
$petId = 10;

$petApi = $client->getPetApi();
$apiResponse = $petApi->updatePetWithForm($petId);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Pet:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | Invalid input | `ApiException` |
| Default | Unexpected error | `ApiException` |


# Delete Pet

Delete a pet.

```php
function deletePet(int $petId, ?string $apiKey = null): ApiResponse
```

## Authentication

This endpoint requires [petstore_auth](../../doc/auth/oauth-2-implicit-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `petId` | `int` | Template, Required | Pet id to delete |
| `apiKey` | `?string` | Header, Optional | - |

## Requires scope

### petstore_auth

`read:pets`, `write:pets`

## Response Type

**200**: Pet deleted

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$petId = 10;

$petApi = $client->getPetApi();
$apiResponse = $petApi->deletePet($petId);

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
| 400 | Invalid pet value | `ApiException` |
| Default | Unexpected error | `ApiException` |


# Upload File

Upload image of the pet.

```php
function uploadFile(int $petId, ?string $additionalMetadata = null, ?FileWrapper $body = null): ApiResponse
```

## Authentication

This endpoint requires [petstore_auth](../../doc/auth/oauth-2-implicit-grant.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `petId` | `int` | Template, Required | ID of pet to update |
| `additionalMetadata` | `?string` | Query, Optional | Additional Metadata |
| `body` | `?FileWrapper` | Form, Optional | - |

## Requires scope

### petstore_auth

`read:pets`, `write:pets`

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`ApiResponse`](../../doc/models/api-response.md).

## Example Usage

```php
$petId = 10;

$petApi = $client->getPetApi();
$apiResponse = $petApi->uploadFile($petId);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'ApiResponse:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 400 | No file uploaded | `ApiException` |
| 404 | Pet not found | `ApiException` |
| Default | Unexpected error | `ApiException` |

