# Collection

## POST

Create a new user.

A user must at all times be linked to an account.

### Request

#### URL
```
/user
```

#### Body
The body is a json format of a user, with an embedded reference to the Account the user will be linked to.
Optionally, the Account (and underlying Network and Instance) can be created in one request.

```json
{
  "name": "John Doe",
  "email": "user@example.org",
  "password": "qwerty123",
  "_embedded": {
    "account": {
      "name": "JohnDoe",
      "ref": "S-JOHNDOE"
    }
  }
}
```

Or, you can link a new User to an existing account like this:

```json
{
  "name": "John Doe",
  "email": "user@example.org",
  "password": "qwerty123",
  "_embedded": {
    "account": {
      "_links": {
        "self": {
          "href": "https://api.sensimity.com/account/1"
        }
      }
    }
  }
}
```

### Response
The response is the created User object.

#### Body
```json
{
  "user_id": 1,
  "name": "John Doe",
  "email": "user@example.org",
  "password": null,
  "superadmin": false,
  "_embedded": {
    "account": {
      "account_id": 1,
      "ref": "S-JOHNDOE",
      "name": "JohnDoe",
      "_embedded": {
        "default_network": {
          "network_id": 1018,
          "_links": {
            "self": {
              "href": "https:\\/\\/api.sensimity.com\\/network\\/1"
            }
          }
        },
        "instance": [
          {
            "instance_id": 1,
            "ref": "S-JOHNDOE-1",
            "name": "JohnDoe",
            "_embedded": {
              "account": {
                "account_id": 1,
                "_links": {
                  "self": {
                    "href": "https:\\/\\/api.sensimity.com\\/account\\/1"
                  }
                }
              }
            },
            "_links": {
              "self": {
                "href": "https:\\/\\/api.sensimity.com\\/instance\\/1"
              }
            }
          }
        ]
      },
      "_links": {
        "self": {
          "href": "https:\\/\\/api.sensimity.com\\/account\\/1"
        }
      }
    }
  },
  "_links": {
    "self": {
      "href": "https:\\/\\/api.sensimity.com\\/user\\/1"
    }
  }
}
```

# Resource

## GET
Get a specific user.

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
  "user_id": 1,
  "name": "John Doe",
  "email": "user@example.org",
  "password": null,
  "superadmin": false,
  "_embedded": {
    "account": {
      "account_id": 1,
      "ref": "S-JOHNDOE",
      "name": "JohnDoe",
      "_embedded": {
        "default_network": {
          "network_id": 1,
          "_links": {
            "self": {
              "href": "https:\\/\\/api.sensimity.com\\/network\\/1"
            }
          }
        },
        "instance": [
          {
            "instance_id": 1,
            "ref": "S-JOHNDOE-1",
            "name": "JohnDoe",
            "_embedded": {
              "account": {
                "account_id": 1,
                "_links": {
                  "self": {
                    "href": "https:\\/\\/api.sensimity.com\\/account\\/1"
                  }
                }
              }
            },
            "_links": {
              "self": {
                "href": "https:\\/\\/api.sensimity.com\\/instance\\/1"
              }
            }
          }
        ]
      },
      "_links": {
        "self": {
          "href": "https:\\/\\/api.sensimity.com\\/account\\/1"
        }
      }
    }
  },
  "_links": {
    "self": {
      "href": "https:\\/\\/api.sensimity.com\\/user\\/1"
    }
  }
}
```

## PATCH
Update a specific user.

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
  "user_id": 1,
  "name": "John Deer",
  "email": "user@example.org",
  "password": null,
  "superadmin": false,
  "_embedded": {
    "account": {
      "account_id": 1,
      "ref": "S-JOHNDOE",
      "name": "JohnDoe",
      "_embedded": {
        "default_network": {
          "network_id": 1,
          "_links": {
            "self": {
              "href": "https:\\/\\/api.sensimity.com\\/network\\/1"
            }
          }
        },
        "instance": [
          {
            "instance_id": 1,
            "ref": "S-JOHNDOE-1",
            "name": "JohnDoe",
            "_embedded": {
              "account": {
                "account_id": 1,
                "_links": {
                  "self": {
                    "href": "https:\\/\\/api.sensimity.com\\/account\\/1"
                  }
                }
              }
            },
            "_links": {
              "self": {
                "href": "https:\\/\\/api.sensimity.com\\/instance\\/1"
              }
            }
          }
        ]
      },
      "_links": {
        "self": {
          "href": "https:\\/\\/api.sensimity.com\\/account\\/1"
        }
      }
    }
  },
  "_links": {
    "self": {
      "href": "https:\\/\\/api.sensimity.com\\/user\\/1"
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
