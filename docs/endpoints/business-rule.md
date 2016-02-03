# Collection

## GET

Retrieve collection of business rules for a specific beacon within a network

### Request

#### URL
```
/network/:network_id/business-rule?beacon=:beacon_id
```

#### Parameters
| Name       | Type    | Description       |
|------------|---------|-------------------|
| network_id | integer | ID of the network |


#### Query parameters
| Name       | Type    | Description       |
|------------|---------|-------------------|
| beacon_id  | integer | ID of the beacon  |


### Response
The response is a list of all business rules for the specific beacon.

#### Body
```json
{
    "_links": {
        "self": {
            "href": "https:\/\/api.sensimity.com\/v1\/business-rule?beacon=6\u0026page=1"
        },
        "first": {
            "href": "https:\/\/api.sensimity.com\/v1\/business-rule?beacon=6"
        },
        "last": {
            "href": "https:\/\/api.sensimity.com\/v1\/business-rule?beacon=6\u0026page=1"
        }
    },
    "_embedded": {
        "business_rule": [{
            "business_rule_id": 2,
            "business_rule_type": "far",
            "beacon_id": 6,
            "interaction_id": 1,
            "_links": {
                "self": {
                    "href": "https:\/\/api.sensimity.com\/v1\/business-rule\/2"
                }
            }
        }, {
            "business_rule_id": 3,
            "business_rule_type": "moving_towards",
            "beacon_id": 6,
            "interaction_id": 1,
            "_links": {
                "self": {
                    "href": "https:\/\/api.sensimity.com\/v1\/business-rule\/3"
                }
            }
        }]
    },
    "page_count": 1,
    "page_size": 25,
    "total_items": 2
}
```

## POST
Create a new business rule in the collection.

### Request

#### URL
```
/network/:network_id/business-rule
```

#### Parameters
| Name       | Type    | Description       |
|------------|---------|-------------------|
| network_id | integer | ID of the network |

#### Body
The body is a json format of a business rule.

```json
{
    "business_rule_type": "moving_towards",
    "beacon_id": 1,
    "interaction_type": "url",
    "content": "http://www.sensimity.com"
}
```

### Response
The response is the created business rule resource representation.

#### Status code
201 Created

#### Body

```json
{
    "business_rule_id": 1,
    "business_rule_type": "moving_towards",
    "beacon_id": 1,
    "interaction_id": 1,
    "interaction_type": "url",
    "content": "http:\/\/www.sensimity.com",
    "_links": {
        "self": {
            "href": "https:\/\/api.sensimity.com\/v1\/business-rule\/1"
        }
    }
}
```

# Resource

## GET
Get details about the specified business rule

### Request

#### URL
```
/network/:network_id/business-rule/:business_rule_id
```

#### Parameters
| Name              | Type    | Description              |
|-------------------|---------|--------------------------|
| network_id        | integer | ID of the network        |
| business_rule_id  | integer | ID of the business rule  |

### Response
The response contains the specified business rule resource

#### Body
```json
{
    "business_rule_id": 1,
    "business_rule_type": "moving_towards",
    "beacon_id": 1,
    "interaction_id": 1,
    "interaction_type": "url",
    "content": "http:\/\/www.sensimity.com",
    "_links": {
        "self": {
            "href": "https:\/\/api.sensimity.com\/v1\/business-rule\/1"
        }
    }
}
```

## PATCH
Update the specified business rule.

### Request

#### URL
```
/network/:network_id/business-rule/:business_rule_id
```

#### Parameters
| Name              | Type    | Description              |
|-------------------|---------|--------------------------|
| network_id        | integer | ID of the network        |
| business_rule_id  | integer | ID of the business rule  |

#### Body
```json
{
  "content": "http://www.enrise.com",
  "beacon_id": 2,
  "interaction_id": 2
}
```

> **Important:** beacon_id and interaction_id are required fields in the json body.

### Response
The response is the updated business rule resource.

#### Body
```json
{
    "business_rule_id": 1,
    "business_rule_type": "moving_towards",
    "beacon_id": 1,
    "interaction_id": 1,
    "interaction_type": "url",
    "content": "http:\/\/www.enrise.com",
    "_links": {
        "self": {
            "href": "https:\/\/api.sensimity.com\/v1\/business-rule\/1"
        }
    }
}
```

## DELETE
Delete a business rule.

### Request

#### URL
```
/network/:network_id/business-rule/:busines_rule_id
```

#### Parameters
| Name              | Type    | Description              |
|-------------------|---------|--------------------------|
| network_id        | integer | ID of the network        |
| business_rule_id  | integer | ID of the business rule  |

### Response

#### Status code
204 No Content
