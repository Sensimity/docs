# Authentication

## Protocol
Sensimity uses the [OAuth2](http://tools.ietf.org/html/rfc6749) protocol to handle authentication.
There are many libraries available in multiple language which you can use.

## Credentials
To use the Sensimity API you need the following credentials which you have received when creating an account:
* Client ID
* Client Secret
* Username
* Password

If you do not have these credentials please [contact us](mailto:info@sensimity.com).

## Obtaining a token
To obtain a token you must make a request to the Sensimity API using the credentials described in the [previous chapter](authentication.md#credentials).
Here's an example of the request:

```bash
curl -X POST \
    -H "Authorization: Basic Y2xpZW50X2lkOmNsaWVudF9zZWNyZXQ=" \
    -H "Accept: application/vnd.sensimity.v1+json" \
    -H "Content-Type: application/vnd.sensimity.v1+json" \
    -d '{"username":"user@example.org","password":"your_password","grant_type":"password"}' \
    http://api.sensimity.com/oauth
```

The response will contain a access token that you need for subsequent requests:
```json
{
    "access_token": "b5f4b74cd0204bd5cc2b315a6e15b19a3211de2a",
    "expires_in": 3600,
    "token_type": "Bearer",
    "scope": null,
    "refresh_token": "d454a2e53636153f21607e5817378bd6c059dd5c"
}
```

More details about this endpoint can be found in the [OAuth endpoint documentation](http://google.com).

## Calling protected API resources
To make requests to endpoints that require authentication you must provide the access token in the `Authorization` header.
The header looks as follows:

```
Authorization: Bearer b5f4b74cd0204bd5cc2b315a6e15b19a3211de2a
```

For example, a request to list all beacons in a network will look like this:
```bash
curl -X GET \
    -H "Authorization: Bearer b5f4b74cd0204bd5cc2b315a6e15b19a3211de2a" \
    -H "Accept: application/vnd.sensimity.v1+json" \
    http://api.sensimity.com/v1/network/1/beacon/1
```

## Refresh token
An obtained access token will expire after some time and you will have to obtain a new one.
To do this you need the `refresh_token` (see [Obtaining a token](authentication.md#obtaining-a-token)).
Here's an example of the request:

```bash
curl -X POST \
    -H "Authorization: Basic Y2xpZW50X2lkOmNsaWVudF9zZWNyZXQ=" \
    -H "Accept: application/vnd.sensimity.v1+json" \
    -H "Content-Type: application/vnd.sensimity.v1+json" \
    -d '{"username":"user@example.org","refresh_token":"d454a2e53636153f21607e5817378bd6c059dd5c","grant_type":"refresh_token"}' \
    http://api.sensimity.com/oauth
```

The response will contain a new access token that you need for subsequent requests:
```json
{
    "access_token": "0d9cc8ee2b04ceeabd591e1d8e208a14b956e9c4",
    "expires_in": 3600,
    "token_type": "Bearer",
    "scope": null
}
```