# Store

Access to Petstore orders

Find out more about our store: [https://swagger.io](https://swagger.io)

```php
$storeApi = $client->getStoreApi();
```

## Class Name

`StoreApi`

## Methods

* [Get Inventory](../../doc/controllers/store.md#get-inventory)
* [Place Order](../../doc/controllers/store.md#place-order)
* [Get Order by Id](../../doc/controllers/store.md#get-order-by-id)
* [Delete Order](../../doc/controllers/store.md#delete-order)


# Get Inventory

Returns a map of status codes to quantities.

```php
function getInventory(): ApiResponse
```

## Authentication

This endpoint requires [api_key](../../doc/auth/custom-header-signature.md)

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type `array<string,int>`.

## Example Usage

```php
$storeApi = $client->getStoreApi();
$apiResponse = $storeApi->getInventory();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'array<string,int>:';
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


# Place Order

Place a new order in the store.

:information_source: **Note** This endpoint does not require authentication.

```php
function placeOrder(
    ?int $id = null,
    ?int $petId = null,
    ?int $quantity = null,
    ?\DateTime $shipDate = null,
    ?string $status = null,
    ?bool $complete = null
): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `id` | `?int` | Form, Optional | - |
| `petId` | `?int` | Form, Optional | - |
| `quantity` | `?int` | Form, Optional | - |
| `shipDate` | `?DateTime` | Form, Optional | - |
| `status` | [`?string(OrderStatus)`](../../doc/models/order-status.md) | Form, Optional | Order Status |
| `complete` | `?bool` | Form, Optional | - |

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Order`](../../doc/models/order.md).

## Example Usage

```php
$id = 10;

$petId = 198772;

$quantity = 7;

$storeApi = $client->getStoreApi();
$apiResponse = $storeApi->placeOrder(
    $id,
    $petId,
    $quantity
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Order:';
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


# Get Order by Id

For valid response try integer IDs with value <= 5 or > 10. Other values will generate exceptions.

:information_source: **Note** This endpoint does not require authentication.

```php
function getOrderById(int $orderId): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `orderId` | `int` | Template, Required | ID of order that needs to be fetched |

## Response Type

**200**: successful operation

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Order`](../../doc/models/order.md).

## Example Usage

```php
$orderId = 62;

$storeApi = $client->getStoreApi();
$apiResponse = $storeApi->getOrderById($orderId);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Order:';
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
| 404 | Order not found | `ApiException` |
| Default | Unexpected error | `ApiException` |


# Delete Order

For valid response try integer IDs with value < 1000. Anything above 1000 or non-integers will generate API errors.

:information_source: **Note** This endpoint does not require authentication.

```php
function deleteOrder(int $orderId): ApiResponse
```

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `orderId` | `int` | Template, Required | ID of the order that needs to be deleted |

## Response Type

**200**: order deleted

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$orderId = 62;

$storeApi = $client->getStoreApi();
$apiResponse = $storeApi->deleteOrder($orderId);

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
| 400 | Invalid ID supplied | `ApiException` |
| 404 | Order not found | `ApiException` |
| Default | Unexpected error | `ApiException` |

