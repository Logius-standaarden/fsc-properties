# Architecture

This section describes how the property object fits into the existing FSC architecture.

## Grant Properties

Each grant in a Contract can now contain an optional property object. This object is included in the grant's data and is part of the content that is hashed when creating the grant hash and contract content hash.

The property object can contain one or multiple keys, with values of any valid JSON datatype. This flexibility allows for a wide range of use cases and future extensibility.

Example of a ServiceConnectionGrant with a property object:

```json
{
  "data": {
    "type": "GRANT_TYPE_SERVICE_CONNECTION",
    "service": {
      "peer_id": "00000000000000000001",
      "name": "example-service"
    },
    "outway": {
      "peer_id": "00000000000000000002",
      "public_key_thumbprint": "3a56f2e9269ac63f0d4394c46b96539da1625b6a985d38029ff89f34e490960c"
    },
    "properties": {
      "max_requests_per_minute": 100,
      "tags": ["api", "v1", "beta"],
      "custom_metadata": {
        "department": "IT",
        "project": "FSC Integration"
      }
    }
  }
}
```