
# Getting Started with Swagger Petstore - OpenAPI 3.0

## Introduction

This is a sample Pet Store Server based on the OpenAPI 3.0 specification.  You can find out more about
Swagger at [https://swagger.io](https://swagger.io). In the third iteration of the pet store, we've switched to the design first approach!
You can now help us improve the API whether it's by making changes to the definition itself or to the code.
That way, with time, we can improve the API in general, and expose some of the new features in OAS3.

Some useful links:

- [The Pet Store repository](https://github.com/swagger-api/swagger-petstore)
- [The source API definition for the Pet Store](https://github.com/swagger-api/swagger-petstore/blob/master/src/main/resources/openapi.yaml)

Find out more about Swagger: [https://swagger.io](https://swagger.io)

## Install the Package

Run the following command to install the package and automatically add the dependency to your composer.json file:

```bash
composer require "vender-demo/first-project:1.5.0"
```

Or add it to the composer.json file manually as given below:

```json
"require": {
    "vender-demo/first-project": "1.5.0"
}
```

You can also view the package at:
https://packagist.org/packages/vender-demo/first-project#1.5.0

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](README.md#environments) | The API environment. <br> **Default: `Environment.PRODUCTION`** |
| timeout | `int` | Timeout for API calls in seconds.<br>*Default*: `30` |
| enableRetries | `bool` | Whether to enable retries and backoff feature.<br>*Default*: `false` |
| numberOfRetries | `int` | The number of retries to make.<br>*Default*: `0` |
| retryInterval | `float` | The retry time interval between the endpoint calls.<br>*Default*: `1` |
| backOffFactor | `float` | Exponential backoff factor to increase interval between retries.<br>*Default*: `2` |
| maximumRetryWaitTime | `int` | The maximum wait time in seconds for overall retrying requests.<br>*Default*: `0` |
| retryOnTimeout | `bool` | Whether to retry on request timeout.<br>*Default*: `true` |
| httpStatusCodesToRetry | `array` | Http status codes to retry against.<br>*Default*: `408, 413, 429, 500, 502, 503, 504, 521, 522, 524, 408, 413, 429, 500, 502, 503, 504, 521, 522, 524` |
| httpMethodsToRetry | `array` | Http methods to retry against.<br>*Default*: `'GET', 'PUT', 'GET', 'PUT'` |
| loggingConfiguration | [`LoggingConfigurationBuilder`](doc/logging-configuration-builder.md) | Represents the logging configurations for API calls |
| proxyConfiguration | [`ProxyConfigurationBuilder`](doc/proxy-configuration-builder.md) | Represents the proxy configurations for API calls |
| petstoreAuthCredentials | [`PetstoreAuthCredentials`](doc/auth/oauth-2-implicit-grant.md) | The Credentials Setter for OAuth 2 Implicit Grant |
| apiKeyCredentials | [`ApiKeyCredentials`](doc/auth/custom-header-signature.md) | The Credentials Setter for Custom Header Signature |

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

## Environments

The SDK can be configured to use a different environment for making API calls. Available environments are:

### Fields

| Name | Description |
|  --- | --- |
| PRODUCTION | **Default** |

## Authorization

This API uses the following authentication schemes.

* [`petstore_auth (OAuth 2 Implicit Grant)`](doc/auth/oauth-2-implicit-grant.md)
* [`api_key (Custom Header Signature)`](doc/auth/custom-header-signature.md)

## List of APIs

* [Pet](doc/controllers/pet.md)
* [Store](doc/controllers/store.md)
* [User](doc/controllers/user.md)

## SDK Infrastructure

### Configuration

* [ProxyConfigurationBuilder](doc/proxy-configuration-builder.md)
* [LoggingConfigurationBuilder](doc/logging-configuration-builder.md)
* [RequestLoggingConfigurationBuilder](doc/request-logging-configuration-builder.md)
* [ResponseLoggingConfigurationBuilder](doc/response-logging-configuration-builder.md)

### HTTP

* [HttpRequest](doc/http-request.md)

### Utilities

* [FileWrapper](doc/file-wrapper.md)
* [ApiResponse](doc/api-response.md)

