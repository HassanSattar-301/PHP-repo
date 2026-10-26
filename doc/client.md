
# Client Class Documentation

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](../README.md#environments) | The API environment. <br> **Default: `Environment.PRODUCTION`** |
| timeout | `int` | Timeout for API calls in seconds.<br>*Default*: `30` |
| enableRetries | `bool` | Whether to enable retries and backoff feature.<br>*Default*: `false` |
| numberOfRetries | `int` | The number of retries to make.<br>*Default*: `0` |
| retryInterval | `float` | The retry time interval between the endpoint calls.<br>*Default*: `1` |
| backOffFactor | `float` | Exponential backoff factor to increase interval between retries.<br>*Default*: `2` |
| maximumRetryWaitTime | `int` | The maximum wait time in seconds for overall retrying requests.<br>*Default*: `0` |
| retryOnTimeout | `bool` | Whether to retry on request timeout.<br>*Default*: `true` |
| httpStatusCodesToRetry | `array` | Http status codes to retry against.<br>*Default*: `408, 413, 429, 500, 502, 503, 504, 521, 522, 524, 408, 413, 429, 500, 502, 503, 504, 521, 522, 524` |
| httpMethodsToRetry | `array` | Http methods to retry against.<br>*Default*: `'GET', 'PUT', 'GET', 'PUT'` |
| loggingConfiguration | [`LoggingConfigurationBuilder`](../doc/logging-configuration-builder.md) | Represents the logging configurations for API calls |
| proxyConfiguration | [`ProxyConfigurationBuilder`](../doc/proxy-configuration-builder.md) | Represents the proxy configurations for API calls |
| petstoreAuthCredentials | [`PetstoreAuthCredentials`](auth/oauth-2-implicit-grant.md) | The Credentials Setter for OAuth 2 Implicit Grant |
| apiKeyCredentials | [`ApiKeyCredentials`](auth/custom-header-signature.md) | The Credentials Setter for Custom Header Signature |

The API client can be initialized as follows:

```php
use SwaggerPetstoreOpenApi30Lib\Logging\LoggingConfigurationBuilder;
use SwaggerPetstoreOpenApi30Lib\Logging\RequestLoggingConfigurationBuilder;
use SwaggerPetstoreOpenApi30Lib\Logging\ResponseLoggingConfigurationBuilder;
use Psr\Log\LogLevel;
use SwaggerPetstoreOpenApi30Lib\Environment;
use SwaggerPetstoreOpenApi30Lib\Authentication\PetstoreAuthCredentialsBuilder;
use SwaggerPetstoreOpenApi30Lib\Models\OauthScopePetstoreAuth;
use SwaggerPetstoreOpenApi30Lib\Authentication\ApiKeyCredentialsBuilder;
use SwaggerPetstoreOpenApi30Lib\SwaggerPetstoreOpenApi30ClientBuilder;

$client = SwaggerPetstoreOpenApi30ClientBuilder::init()
    ->petstoreAuthCredentials(
        PetstoreAuthCredentialsBuilder::init(
            'OAuthClientId',
            'OAuthRedirectUri'
        )
            ->oauthScopes(
                [
                    OauthScopePetstoreAuth::WRITEPETS,
                    OauthScopePetstoreAuth::READPETS
                ]
            )
    )
    ->apiKeyCredentials(
        ApiKeyCredentialsBuilder::init(
            'api_key'
        )
    )
    ->environment(Environment::PRODUCTION)
    ->loggingConfiguration(
        LoggingConfigurationBuilder::init()
            ->level(LogLevel::INFO)
            ->requestConfiguration(RequestLoggingConfigurationBuilder::init()->body(true))
            ->responseConfiguration(ResponseLoggingConfigurationBuilder::init()->headers(true))
    )
    ->build();
```

## Swagger Petstore - OpenAPI 3.0 Client

The gateway for the SDK. This class acts as a factory for the Apis and also holds the configuration of the SDK.

## Apis

| Name | Description |
|  --- | --- |
| getPetApi() | Gets PetApi |
| getStoreApi() | Gets StoreApi |
| getUserApi() | Gets UserApi |

