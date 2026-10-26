
# Api Response

*This model accepts additional fields of type array.*

## Structure

`ApiResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `code` | `?int` | Optional | - | getCode(): ?int | setCode(?int code): void |
| `type` | `?string` | Optional | - | getType(): ?string | setType(?string type): void |
| `message` | `?string` | Optional | - | getMessage(): ?string | setMessage(?string message): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SwaggerPetstoreOpenApi30Lib\Models\Builders\ApiResponseBuilder;
use SwaggerPetstoreOpenApi30Lib\ApiHelper;

$apiResponse = ApiResponseBuilder::init()
    ->code(146)
    ->type('type4')
    ->message('message4')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

