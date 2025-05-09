# AIMA Gateway Shared Protobuf Definitions

## Overview

This repository provides the Protocol Buffer (protobuf) definitions for the AIMA Gateway.

AIMA Gateway is a service designed to facilitate efficient communication between external systems and our AIMA platform using either gRPC or REST.

Its protobuf definitions specify structured data contracts to ensure consistent, reliable, and backward-compatible integrations.

If you are unable to use gRPC, you can also use our REST endpoints, though we recommend using gRPC as it is faster and more efficient.

## Repository Purpose

- Store and manage protobuf definitions used for communication with the AIMA Gateway.
- Ensure consistent data structures and backward compatibility for customer integrations.

## See also

- Protocol Buffers: https://protobuf.dev/
- gRPC: https://grpc.io/
- gRPC Service Protocols: [aima-gateway-protocols-public](https://github.com/team-sigma-ai/dtp-aima-gw-protocols-public)

## Notes

These protocols adhere to the following standards:

- Protocol Version 3 only.
- Timestamp fields always:
  - Use nanosecond Unix Epoch time.
  - Represent UTC.

## Versioning

We use versioning for individual Messages within a namespace to ensure controlled updates and backward compatibility.

### Guidelines:
- The namespace includes the version, e.g., `ai.sigmafinancial.aima.shared.v1`.
- Breaking changes to a messages results in a new version being created for only that message.
- Server Endpoints may use multiple versions of a message simultaneously. For example:
  - `v1.Management.InvokeWorkflow` might use `ai.sigmafinancial.aima.shared.v1.ExampleMetadataMessage`
  - `v2.Generative.ChatStreaming` might use `ai.sigmafinancial.aima.shared.v2.ExampleMetadataMessage`

## Compiling

To use the gRPC service definitions, you will also need the shared models.
Ensure that you have set your `protoc` search path to include the parent folder which includes both sets of gRPC definitions.

Example if your folder structure is like the one below, set your search path to include `aima-gateway-protos`.

```
aima-gateway-protos
|
+---- dtp-aima-gw-protocols-shared
|
\---- dtp-aima-gw-protocols-public
```

