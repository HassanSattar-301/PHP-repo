
# Pet

*This model accepts additional fields of type array.*

## Structure

`Pet`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `id` | `?int` | Optional | - | getId(): ?int | setId(?int id): void |
| `name` | `string` | Required | - | getName(): string | setName(string name): void |
| `category` | [`?Category`](../../doc/models/category.md) | Optional | - | getCategory(): ?Category | setCategory(?Category category): void |
| `photoUrls` | `string[]` | Required | - | getPhotoUrls(): array | setPhotoUrls(array photoUrls): void |
| `tags` | [`?(Tag[])`](../../doc/models/tag.md) | Optional | - | getTags(): ?array | setTags(?array tags): void |
| `status` | [`?string(PetStatus)`](../../doc/models/pet-status.md) | Optional | pet status in the store | getStatus(): ?string | setStatus(?string status): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SwaggerPetstoreOpenApi30Lib\Models\Builders\PetBuilder;
use SwaggerPetstoreOpenApi30Lib\Models\Builders\CategoryBuilder;
use SwaggerPetstoreOpenApi30Lib\ApiHelper;
use SwaggerPetstoreOpenApi30Lib\Models\Builders\TagBuilder;
use SwaggerPetstoreOpenApi30Lib\Models\PetStatus;

$pet = PetBuilder::init(
    'name0',
    [
        'photoUrls5',
        'photoUrls6'
    ]
)
    ->id(72)
    ->category(
        CategoryBuilder::init()
            ->id(232)
            ->name('name2')
            ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
            ->build()
    )
    ->tags(
        [
            TagBuilder::init()
                ->id(26)
                ->name('name0')
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build()
        ]
    )
    ->status(PetStatus::AVAILABLE)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

