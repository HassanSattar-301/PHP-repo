
# Oauth Token

OAuth 2 Authorization endpoint response

## Structure

`OauthToken`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `accessToken` | `string` | Required | Access token | getAccessToken(): string | setAccessToken(string accessToken): void |
| `tokenType` | `string` | Required | Type of access token | getTokenType(): string | setTokenType(string tokenType): void |
| `expiresIn` | `?int` | Optional | Time in seconds before the access token expires | getExpiresIn(): ?int | setExpiresIn(?int expiresIn): void |
| `scope` | `?string` | Optional | List of scopes granted<br>This is a space-delimited list of strings. | getScope(): ?string | setScope(?string scope): void |
| `expiry` | `?int` | Optional | Time of token expiry as unix timestamp (UTC) | getExpiry(): ?int | setExpiry(?int expiry): void |
| `refreshToken` | `?string` | Optional | Refresh token<br>Used to get a new access token when it expires. | getRefreshToken(): ?string | setRefreshToken(?string refreshToken): void |

## Example

```php
use SwaggerPetstoreOpenApi30Lib\Models\Builders\OauthTokenBuilder;

$oauthToken = OauthTokenBuilder::init(
    'access_token8',
    'token_type8'
)
    ->expiresIn(10)
    ->scope('scope2')
    ->expiry(152)
    ->refreshToken('refresh_token0')
    ->build();
```

