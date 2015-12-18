# Collection

## POST
This is an RPC-style endpoint. It is used to send raw usage data to the server, so that the statistics can be compiled.

### Request

#### URL
```
/scan-results
```

#### Body
The body must contain all collected data from the client's device.

```json
{
  "instance_ref": "S-44C0FFEE-1",
  "device": {
    "model": "Find 5",
    "operating_system": "android",
    "version": "4.4.2",
    "device_id": "5622ce149d42e67c"
  },
  "beaconLogs": [
    {
      "UUID": "44c0ffee-988a-49dc-0bad-a55c0de2d1e4",
      "major": 16,
      "minor": 0,
      "timestamp": 1406804464.128,
      "timezone": "UTC+01:00",
      "rssi": -60,
      "beacon_id": 16
    }, {
      "UUID": "44c0ffee-988a-49dc-0bad-a55c0de2d1e4",
      "major": 16,
      "minor": 0,
      "timestamp": 1406804474.128,
      "timezone": "UTC+02:00",
      "rssi": -60,
      "beacon_id": 16
    }
  ]
}
```

| Parameter               | Description                                              | Required |
|-------------------------|----------------------------------------------------------|:--------:|
| instance_ref            | The application reference as you get from your dashboard | yes      |
| device.model            | The client's device model                                | yes      |
| device.operating_system | The client's device model                                | yes      |
| device.version          | The client's device OS version                           | yes      |
| device.device_id        | The client's unique device id                            | yes      |
| beaconLogs[].UUID       | The beacon UUID                                          | yes      |
| beaconLogs[].major      | The beacon's major number                                | yes      |
| beaconLogs[].minor      | The beacon's minor number                                | yes      |
| beaconLogs[].timestamp  | Timestamp of result in seconds                           | yes      |
| beaconLogs[].timezone   | The client's timezone in UTC format                      | no       |
| beaconLogs[].rssi       | The result's RSSI value                                  | yes      |
| beaconLogs[].beacon_id  | The beacon's id as defined in Sensimity                  | no       |

### Response
The response is an indication of success. When the request was accepted, you will receive an HTTP-status of"204 No Content".
If the provided `instance_ref` does not exist in the Sensimity database a HTTP-status "400 Bad Request".

#### Status code

If the request was successful:

* 204 No Content

In case of client error:

* 400 Bad Request


#### Body
In case the instance_ref was not recognized:

```json
{
  "errors": [
    "Supplied reference does not exist"
  ]
}
```
