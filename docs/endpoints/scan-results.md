# Collection

## POST
This is actually an RPC-style endpoint. It is used to send raw usage data to the server, so that the statistics can be compiled.

### Request

#### URL
```
/scan-results
```

#### Body
The body must contain all collected data from the client's device.

```json
{
  "device": {
    "model": "Find 5",
    "operating_system": "android",
    "version": "4.4.2",
    "device_id": "5622ce149d42e67c"
  },
  "beaconLogs": [
    {
      "major": 16,
      "UUID": "44c0ffee-988a-49dc-0bad-a55c0de2d1e4",
      "timestamp": 1406804464.128,
      "rssi": -60,
      "id": 1,
      "minor": 0
    }, {
      "major": 16,
      "UUID": "44c0ffee-988a-49dc-0bad-a55c0de2d1e4",
      "timestamp": 1406804474.128,
      "rssi": -60,
      "id": 2,
      "minor": 0
    }
  ]
}
```

### Response
The response is a summary of the received results.

#### Body

```json
{
  "message": "The scan results are successfully processed.",
  "added": 2,
  "skipped": 0
}
```
