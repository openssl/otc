- QUIC
  The standard has now been published and this has become more timely.

- constant time bignum
  Significant rework is involved to make BNs constant time pervasively and
  by default.

- better EC
  - EC kiila?
  - not using BN?
  - whatever?

- RNG strengths as a limiting factor
  - Limit key generation to the strength of the RNG.
  - Anternatively, implement SP 800-90C 10.1.2 to increase RNG strength.

- algorithm strength passed around pervasively
  Extension of the above where strength is spread more pervasively.

- better RNG instantiation (flexible architecture)
  The current RNG layout is hard wired.  It would be good to allow applications
  more flexibility in this setup.

- property expressions (add "or" operation, parenthesis, ...)
  Adding an "or" operatin to property queries has been mentioned repeatedly.
  Having "or" implies parenthesis and potentially operator precedence.

- algorithm priority
  To allow different implementations of one algorithm to be chosen based on
  a desirability.

- More fine grained fetchable selection, e.g. ability to provide implementations
  for EC for just some curves but not all

- LTS+
  When do we do this?

- better XOF mode
  Allowing XOF final to be called repeatedly to generate more output.

- additional KDFs (3 from passwd command)
  The KDFs in the passwd command are aging but potentially useful elsewhere.
  PVK

- create EVP_PRF (hybrid between KDF, MAC and RAND)
  Our PRFs are part of KDF, however MACs are also used in this role and the
  DRBGs are too.  In terms of complexity, RAND >> MAC > KDF.  An EVP_PRF would
  sit between RAND and KDF.

- create EVP_AEAD_CIPHER
  This should have been done when they were invented.  Is it too late to do
  it now?

- fetchable signature algorithms
  Both for X509 and TLS

- CNG provider

- PVK

- PKCS #11 provider
  How much of the standard?

- ESNI

- Windows cert & key store

- FIPS 140-3

- EVP_SKEY (or equivalent)

- algorithm state serialisation

- HPKE (Hybrid Public Key Encryption)

- Attribute Certificate RFC-5755

- EVP SRP API

- support more store URIs

- blake 3

- CBOR (Compact Binary Object Representation)

- remove engine and legacy completely

- finish documenting everything

- finish deprecations

- more demos

- DTLS 1.3

- Certificate Compression

- More encoders/decoders, e.g. JWK support
