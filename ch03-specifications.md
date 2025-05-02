# Specifications

This section provides detailed specifications for implementing the property object extension.

## Property Object

### Structure

The property object must be a valid JSON object. It can contain any number of key-value pairs, where:

1. Keys must be strings
2. Values can be of any valid JSON datatype (string, number, boolean, object, array, or null)

### Grant

The property object MAY be added to a grant object and MUST have the key 'properties'.

### Inclusion in Grant Hash

When calculating the grant hash, the property object must be included in the hashing process. This ensures that the properties are part of the immutable grant definition.

To include the property object in the grant hash:

1. Canonicalize the JSON property object as described in [RFC 8785](https://www.rfc-editor.org/rfc/rfc8785)
1. Hash the canonicalized JSON string using the hash algorithm described in contract.content.algorithm
1. Add the hash to the grantBytes array as described in the FSC Core specification.
1. Continue with the hashing process as described in the FSC Core specification.

### Validation

When validating a grant with properties:

1. The Manager must ensure that the `properties` field, if present, is a valid JSON object.
2. The Manager should not impose any restrictions on the content of the property object beyond it being valid JSON, as the meaning and use of properties are application-specific.

### Security Considerations

1. The size of the `properties` object should be limited to prevent excessive data transfer and storage. It is recommended to implement a size limit of 1MB for the serialized `properties` object.

2. Sensitive information like secrets or other private information should not be stored in the `properties` object, as it may be visible to Services and potentially logged or stored in various systems.

3. Implementers should be aware that the contents of the `properties` object are unsanitized. For example, they should consider sanitizing the data before showing it in user interfaces to prevent XSS injections or other security vulnerabilities.

### Backwards Compatibility

This extension is backwards compatible with the FSC Core specification. Systems that do not implement this extension will ignore the `properties` field in grants and the `prp` claim in access tokens.

### Future Considerations

1. Standard property keys and their meanings could be defined in future versions to promote interoperability between different implementations.