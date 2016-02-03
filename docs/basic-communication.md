# Talking to the Sensimity API

## API server
The Sensimity API can be reached at `https://api.sensimity.com/`.

## Accept and Content-Type headers
For all requests to the Sensimity API please use the following Accept header:
```
Accept: application/vnd.sensimity.v1+json
```

And the following Content-Type header:
```
Content-Type: application/vnd.sensimity.v1+json
```

## Authenticating
Most endpoints require the client to be authenticated with the API. You can read more on this in [the chapter on authentication](authentication.md).

## Making a request to the API
For example:
```sh
curl -X GET -H "Authorization: Bearer 932840e6079d85f5a4a9954916f04e37c8223cac" -H "Accept: application/vnd.sensimity.v1+json" -H "Content-Type: application/vnd.sensimity.v1+json" https://api.sensimity.com/v1/network/1/beacon
```

## Response status codes
Based on HTTP the SensimityAPI uses HTTP-status codes. Here's a list of the statuses and their meaning:

| Code | Status                 | Explanation |
|------|------------------------|-------------|
| 200  | OK                     |             |
| 201  | Created                |             |
| 204  | No Content             |             |
| 400  | Bad Request            |             |
| 401  | Unauthorized           |             |
| 403  | Forbidden              |             |
| 404  | Not Found              |             |
| 406  | Not Acceptable         |             |
| 415  | Unsupported Media Type |             |
| 422  | Unprocessable Entity   |             |

## Error response
When a response was not successful, in many cases the problem will be reported in the response body.


For example, when a required property is missing.
```json
{
  "validation_messages": {
    "title": {
      "isEmpty": "Value is required and can't be empty"
    }
  },
  "type": "http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html",
  "title": "Unprocessable Entity",
  "status": 422,
  "detail": "Failed Validation"
}
```
