# API Proof of Concept

The current QUIC API Design PR ([https://github.com/openssl/openssl/pull/17184](https://github.com/openssl/openssl/pull/17184)) presents a number of different options for the style of API that we might implement. In summary these are:

* Just use the existing SSL API
* A generic comms API with SSL compat layer
* A completely new QUIC API with SSL compat layer

This Proof of Concept (PoC) will attempt to address the second option (a generic comms API). By implementing a simple generic comms API we hope to discover the types of problems that we will encounter if we were to take this approach and highlight any areas of difficulty or concern. This will confirm or deny the viability of the generic comms API.

## Scope

The PoC will implement 4 applications:

* A simple client using the generic comms API to send and receive data to/from a TLS server
* A simple server using the generic comms API to send and receive data to/from a TLS client
* A simple client using the generic comms API to send and receive data to/from a server using a “toy” multi-stream protocol
* A simple server using the generic comms API to send and receive data to/from a server using a “toy” multi-stream protocol

All of the above will be based on non-blocking IO.

The “toy” protocol will have the following characteristics:

* UDP based
* Ability to send/receive data over more than one stream
* Ability for the server to support multiple connections over a single socket

The PoC will implement enough of a generic comms API to support the above 4 applications.

The PoC API will support setting arbitrary protocol metadata required for the connection on both client and server side such as authentication credentials, SNI, etc.

The PoC must also address the SSL compatibility layer. Existing demo client and server code should be demonstrated to work with the SSL compatibility layer.

## Output

The output of the PoC will be a branch in a copy of the main OpenSSL source repository. The code will be held in a "poc" repository under the OpenSSL organisation in Github. It will contain running code for each of the 4 applications described above.

It will not:

* Be merged into the main source repository.
* Have accompanying design documentation.
* Contain tests.
* Have undergone review through the pull request code review process. This is not intended to be production quality code.

All of the above will be timeboxed to 2 people for 4 calendar weeks work (2 sprints). The PoC team will attempt to implement the complete scope as outlined above. If this turns out not to be possible they will implement as much of a subset as possible.
