# Collection

## GET

Retrieve collection of beacons.

### Request

#### URL
```
/network/:network_id/beacon
```

#### Parameters
| Name       | Type    | Description       |
|------------|---------|-------------------|
| network_id | integer | ID of the network |

### Response
The response is a list of all beacons belonging to this network.

#### Body
```json
{
  "_links": {
    "self": {
      "href": "http:\/\/api.sensimity.com\/v1\/network\/1\/beacon?page=1"
    },
    "first": {
      "href": "http:\/\/api.sensimity.com\/v1\/network\/1\/beacon"
    },
    "last": {
      "href": "http:\/\/api.sensimity.com\/v1\/network\/1\/beacon?page=1"
    }
  },
  "_embedded": {
    "beacon": [
      {
        "beacon_id": 1,
        "uuid_beacon": "44c0ffee-988a-49dc-0bad-a55c0de2d1e4",
        "major": 16,
        "minor": 1,
        "created_at": "2014-08-04 22:10:12.313",
        "updated_at": "2014-08-04 22:10:36.823678",
        "network_id": 1,
        "title": "beacon_1",
        "description": "This is the first beacon",
        "_links": {
          "self": {
            "href": "http:\/\/api.sensimity.com\/v1\/network\/1\/beacon\/1"
          },
          "area": {
            "href": "http:\/\/api.sensimity.com\/v1\/area\/4"
          }
        }
      },
      {
        "beacon_id": 2,
        "uuid_beacon": "44c0ffee-988a-49dc-0bad-a55c0de2d1e4",
        "major": 2,
        "minor": 2,
        "created_at": "2015-02-06 15:57:54.058238",
        "updated_at": "2015-02-06 15:57:54.058238",
        "network_id": 1,
        "title": "beacon_2",
        "description": "This is the second beacon",
        "_links": {
          "self": {
            "href": "http:\/\/api.sensimity.com\/v1\/network\/1\/beacon\/2"
          },
          "area": {
            "href": "http:\/\/api.sensimity.com\/v1\/area\/2"
          }
        }
      }
    ]
  },
  "page_count": 1,
  "page_size": 100,
  "total_items": 2
}
```

## POST
Create a new beacon in the collection.

### Request

#### URL
```
/network/:network_id/beacon
```

#### Parameters
| Name       | Type    | Description       |
|------------|---------|-------------------|
| network_id | integer | ID of the network |

#### Body
The body is a json format of a beacon.

```json
{
  "uuid_beacon": "44c0ffee-988a-49dc-0bad-a55c0de2d1e4",
  "major": 2,
  "minor": 2,
  "network_id": 1,
  "title": "beacon_2",
  "description": "This is the second beacon"
}
```

### Response
The response is a list of all beacons belonging to this network.

#### Status code
201 Created

#### Body

```json
{
  "beacon_id": 6,
  "area_id": null,
  "uuid_beacon": "44c0ffee-988a-49dc-0bad-a55c0de2d1e4",
  "major": 2,
  "minor": 2,
  "created_at": "2015-02-13 13:50:23.466588",
  "updated_at": "2015-02-13 13:50:23.466588",
  "network_id": 1,
  "title": "beacon_2",
  "description": "This is the second beacon",
  "_links": {
    "self": {
      "href": "http:\/\/api.sensimity.com\/v1\/network\/1\/beacon\/6"
    }
  }
}
```

# Resource

## GET
Get a specific beacon from the specified network.

### Request

#### URL
```
/network/:network_id/beacon/:beacon_id
```

#### Parameters
| Name       | Type    | Description       |
|------------|---------|-------------------|
| network_id | integer | ID of the network |
| beacon_id  | integer | ID of the beacon  |

### Response
The response is a single beacon resource from the network.

#### Body
```json
{
  "beacon_id": 6,
  "area_id": null,
  "uuid_beacon": "44c0ffee-988a-49dc-0bad-a55c0de2d1e4",
  "major": 2,
  "minor": 2,
  "created_at": "2015-02-13 13:50:23.466588",
  "updated_at": "2015-02-13 13:50:23.466588",
  "network_id": 1,
  "title": "beacon_2",
  "description": "This is the second beacon",
  "_links": {
    "self": {
      "href": "http:\/\/api.sensimity.com\/v1\/network\/1\/beacon\/6"
    }
  }
}
```

## PATCH
Update a specific beacon from the specified network.

### Request

#### URL
```
/network/:network_id/beacon/:beacon_id
```

#### Parameters
| Name       | Type    | Description       |
|------------|---------|-------------------|
| network_id | integer | ID of the network |
| beacon_id  | integer | ID of the beacon  |

#### Body
```json
{
  "title": "my_beacon"
}
```

### Response
The response is the updated beacon resource from the network.

#### Body
```json
{
  "beacon_id": 6,
  "area_id": null,
  "uuid_beacon": "44c0ffee-988a-49dc-0bad-a55c0de2d1e4",
  "major": 2,
  "minor": 2,
  "created_at": "2015-02-13 13:50:23.466588",
  "updated_at": "2015-02-13 13:50:23.466588",
  "network_id": 1,
  "title": "my_beacon",
  "description": "This is the second beacon",
  "_links": {
    "self": {
      "href": "http:\/\/api.sensimity.com\/v1\/network\/1\/beacon\/6"
    }
  }
}
```

## DELETE
Delete a beacon.

### Request

#### URL
```
/network/:network_id/beacon/:beacon_id
```

#### Parameters
| Name       | Type    | Description       |
|------------|---------|-------------------|
| network_id | integer | ID of the network |
| beacon_id  | integer | ID of the beacon  |

### Response

#### Status code
204 No Content