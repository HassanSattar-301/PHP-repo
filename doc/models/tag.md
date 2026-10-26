
# Tag

*This model accepts additional fields of type array.*

## Structure

`Tag`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `id` | `?int` | Optional | - | getId(): ?int | setId(?int id): void |
| `name` | `?string` | Optional | - | getName(): ?string | setName(?string name): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SwaggerPetstoreOpenApi30Lib\Models\Builders\TagBuilder;
use SwaggerPetstoreOpenApi30Lib\ApiHelper;

$tag = TagBuilder::init()
    ->id(168)
    ->name('name6')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

