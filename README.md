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

- Protocol Buffers: <https://protobuf.dev/>
- gRPC: <https://grpc.io/>
- gRPC Service Protocols: [aima-gateway-protocols-public](https://github.com/team-sigma-ai/dtp-aima-gw-protocols-public)

## Contents

The definitions are grouped by API version. Each version is an independent
namespace under `ai.sigmafinancial.aima.<version>.<service>`.

The order for repeated fields on the wire carries no meaning and must not be relied upon.

e.g. if there is a `repeated <type> field = ...` you should not assume that the order of
the elements in the array will be consistent between calls or
that they reflect the order of the elements in the input.

## Notes

These protocols adhere to the following standards:

- `proto3` syntax throughout.
- Timestamp fields always:
  - Use nanosecond Unix Epoch time except where explicitly stated.
  - Represent UTC.

## Versioning

We use versioning per namespace to ensure controlled updates and backward
compatibility.

### Guidelines

- The namespace includes the version immediately after `aima`, followed by the
  domain, e.g., `ai.sigmafinancial.aima.v1.common`,
  `ai.sigmafinancial.aima.v3.generative.services`.
- A breaking change to a message results in a new version of that message's
  namespace, leaving the existing version intact.
- Server endpoints may use multiple versions of a message simultaneously. For
  example, the public v1 and v3 Generative services consume the `v1` and `v3`
  shared messages respectively.
- Fields starting with `internal_` are reserved for internal use and should not be relied upon as they can change without notice.


## Compiling

To use the gRPC service definitions, you will also need the shared models.
Ensure that you have set your `protoc` search path to include the parent folder which includes both sets of gRPC definitions.

Example if your folder structure is like the one below, set your search path to include `aima-gateway-protos`.

```text
aima-gateway-protos
|
+---- dtp-aima-gw-protocols-shared
|
\---- dtp-aima-gw-protocols-public
```
