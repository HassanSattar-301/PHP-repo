
# Order

*This model accepts additional fields of type array.*

## Structure

`Order`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `id` | `?int` | Optional | - | getId(): ?int | setId(?int id): void |
| `petId` | `?int` | Optional | - | getPetId(): ?int | setPetId(?int petId): void |
| `quantity` | `?int` | Optional | - | getQuantity(): ?int | setQuantity(?int quantity): void |
| `shipDate` | `?DateTime` | Optional | - | getShipDate(): ?\DateTime | setShipDate(?\DateTime shipDate): void |
| `status` | [`?string(OrderStatus)`](../../doc/models/order-status.md) | Optional | Order Status | getStatus(): ?string | setStatus(?string status): void |
| `complete` | `?bool` | Optional | - | getComplete(): ?bool | setComplete(?bool complete): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SwaggerPetstoreOpenApi30Lib\Models\Builders\OrderBuilder;
use SwaggerPetstoreOpenApi30Lib\Utils\DateTimeHelper;
use SwaggerPetstoreOpenApi30Lib\Models\OrderStatus;
use SwaggerPetstoreOpenApi30Lib\ApiHelper;

$order = OrderBuilder::init()
    ->id(144)
    ->petId(184)
    ->quantity(100)
    ->shipDate(DateTimeHelper::fromRfc3339DateTime('2016-03-13T12:52:32.123Z'))
    ->status(OrderStatus::PLACED)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

