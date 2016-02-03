# Collection

## GET

Retrieve collection of networks that the logged in user has access to.

> **Important:** This endpoint can only be accessed when you are [logged in](../authentication.md) via oAuth

### Request

#### URL
```
/network
```

### Response
The response is a paginated list of all networks that the user has access to.

#### Body
```json
{
    "_links": {
        "self": {
            "href": "https:\/\/api.sensimity.com\/v1\/network?page=1"
        },
        "first": {
            "href": "https:\/\/api.sensimity.com\/v1\/network"
        },
        "last": {
            "href": "https:\/\/api.sensimity.com\/v1\/network?page=1"
        }
    },
    "_embedded": {
        "network": [{
            "network_id": 3,
            "name": "Enrise Office",
            "url_name": "enrise-office",
            "parent_network_id": null,
            "_links": {
                "self": {
                    "href": "https:\/\/api.sensimity.com\/v1\/network\/3"
                }
            }
        }, {
            "network_id": 4,
            "name": "Sensimity Office",
            "url_name": "sensimity-office",
            "parent_network_id": null,
            "_links": {
                "self": {
                    "href": "https:\/\/api.sensimity.com\/v1\/network\/4"
                }
            }
        }]
    },
    "page_count": 1,
    "page_size": 25,
    "total_items": 2
}
```

# Resource

## GET
Get details about the specified network

### Request

#### URL
```
/network/:network_id
```

#### Parameters
| Name              | Type    | Description              |
|-------------------|---------|--------------------------|
| network_id        | integer | ID of the network        |

### Response
The response is a single network resource representation

#### Body
```json
{
    "network_id": 5,
    "name": "Demo network",
    "url_name": "demo-network",
    "parent_network_id": null,
    "users": [],
    "_links": {
        "self": {
            "href": "https:\/\/api.sensimity.com\/v1\/network\/5"
        }
    }
}
```

## PATCH
Update the specified network.

### Request

#### URL
```
/network/:network_id
```

#### Parameters
| Name              | Type    | Description              |
|-------------------|---------|--------------------------|
| network_id        | integer | ID of the network        |

#### Body
```json
{
    "name": "Other network name"
}
```

### Response
The response is the updated network resource.

#### Body
```json
{
    "network_id": 5,
    "name": "Other network name",
    "url_name": "demo-network",
    "parent_network_id": null,
    "users": [],
    "_links": {
        "self": {
            "href": "https:\/\/api.sensimity.com\/v1\/network\/5"
        }
    }
}
```

## DELETE
Delete a network.

### Request

#### URL
```
/network/:network_id
```

#### Parameters
| Name              | Type    | Description              |
|-------------------|---------|--------------------------|
| network_id        | integer | ID of the network        |

### Response

#### Status code
204 No Content
