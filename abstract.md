This document specifies an extension to the Federated Service Connectivity (FSC) Core specification, introducing the ability to include custom properties in grants. The extension defines a flexible mechanism for adding key-value pairs to grants, which are then propagated through access tokens and made available to services.

Key features of this extension include:

1. A `properties` object within grants, allowing for arbitrary JSON key-value pairs.
1. Integration of the `properties` object into the grant hash calculation process.
1. Inclusion of properties in access tokens as a new `prp` claim.
1. Guidelines for Manager, Inway, and Outway behavior when handling properties.
1. Security considerations, including size limitations and sensitive data handling.

This extension maintains backwards compatibility with the FSC Core specification while enabling more detailed and flexible grant definitions. It opens up possibilities for application-specific metadata and configuration options within the FSC ecosystem, enhancing the capabilities of federated service connectivity implementations.