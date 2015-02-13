# Collection

## POST

Create a new user.

### Request

#### URL
```
/user
```

#### Body
The body is a json format of a user.

```json
{
  "email": "user@example.org",
  "password": "qwerty123",
  "name": "John Doe"
}
```

### Response
The response is the user object.

#### Body
```json
{
  "email": "user@example.org",
  "name": "John Doe",
  "created_at": "2015-02-13 16:33:31.347069",
  "updated_at": "2015-02-13 16:33:31.347069",
  "superadmin": false,
  "deleted": false,
  "networks": [ ],
  "user_id": 22,
  "_links": {
    "self": {
      "href": "http:\/\/api.sensimity.com\/user\/22"
    }
  }
}
```

# Resource

## GET

### Request

#### URL
```
/user/:user_id
```

#### Parameters

| Name    | Type    | Description    |
|---------|---------|----------------|
| user_id | integer | ID of the User |

### Response
The response is single user.

#### Body
```json
{
  "email": "user@example.org",
  "name": "John Doe",
  "created_at": "2015-02-13 16:33:31.347069",
  "updated_at": "2015-02-13 16:33:31.347069",
  "superadmin": false,
  "deleted": false,
  "networks": [ ],
  "user_id": 22,
  "_links": {
    "self": {
      "href": "http:\/\/api.sensimity.com\/user\/22"
    }
  }
}
```

## PATCH

### Request

#### URL
```
/user/:user_id
```

#### Parameters

| Name    | Type    | Description    |
|---------|---------|----------------|
| user_id | integer | ID of the User |

#### Body
```json
{
  "name": "John Deer"
}
```

### Response
The response is a single user.

#### Body
```json
{
  "email": "user@example.org",
  "name": "John Deer",
  "created_at": "2015-02-13 16:33:31.347069",
  "updated_at": "2015-02-13 16:33:31.347069",
  "superadmin": false,
  "deleted": false,
  "networks": [ ],
  "user_id": 22,
  "_links": {
    "self": {
      "href": "http:\/\/api.sensimity.com\/user\/22"
    }
  }
}
```

## DELETE
Delete a user.

### Request

#### URL
```
/user/:user_id
```

#### Parameters
| Name    | Type    | Description    |
|---------|---------|----------------|
| user_id | integer | ID of the User |

### Response

#### Status code
204 No Content