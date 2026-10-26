
# User

*This model accepts additional fields of type array.*

## Structure

`User`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `id` | `?int` | Optional | - | getId(): ?int | setId(?int id): void |
| `username` | `?string` | Optional | - | getUsername(): ?string | setUsername(?string username): void |
| `firstName` | `?string` | Optional | - | getFirstName(): ?string | setFirstName(?string firstName): void |
| `lastName` | `?string` | Optional | - | getLastName(): ?string | setLastName(?string lastName): void |
| `email` | `?string` | Optional | - | getEmail(): ?string | setEmail(?string email): void |
| `password` | `?string` | Optional | - | getPassword(): ?string | setPassword(?string password): void |
| `phone` | `?string` | Optional | - | getPhone(): ?string | setPhone(?string phone): void |
| `userStatus` | `?int` | Optional | User Status | getUserStatus(): ?int | setUserStatus(?int userStatus): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use SwaggerPetstoreOpenApi30Lib\Models\Builders\UserBuilder;
use SwaggerPetstoreOpenApi30Lib\ApiHelper;

$user = UserBuilder::init()
    ->id(76)
    ->username('username0')
    ->firstName('firstName4')
    ->lastName('lastName4')
    ->email('email6')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

