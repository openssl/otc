- QUIC
  - [#8797](https://github.com/openssl/openssl/issues/8797)
  The standard has now been published and this has become more timely.

- constant time bignum
  - [#6640](https://github.com/openssl/openssl/issues/6640)
  Significant rework is involved to make BNs constant time pervasively and
  by default.

- safe integer operations wrappers
  Like the constant time ones but avoiding overflow etc.
  We're constantly reinventing these in a variety of places and they are tricky.

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

- Multithreading improvements
  Make CRYPTO_RWLOCK and atomic counters opaque structures.
  - Atomics could only carry the lock on platforms where atomics aren't defined.
    current usage is to have the lock even if it isn't used (some exceptions).
  - We could add thread debugging / tracing.

- better XOF mode
  - [#7894](https://github.com/openssl/openssl/issues/7894)
  Allowing XOF final to be called repeatedly to generate more output.
  Require diving into assembly implementations

- additional KDFs (3 from passwd command)
  The KDFs in the passwd command are aging but potentially useful elsewhere.
  PVK

- Argon2 KDF and thread support
  - [#4091](https://github.com/openssl/openssl/issues/4091)
  - [#12256](https://github.com/openssl/openssl/issues/12256)

- yescrypt KDF

- Secret sharing
  Shamir's secret sharing or a different scheme or several?
  Command line application plus a C API

- create EVP_PRF (hybrid between KDF, MAC and RAND)
  - [#14543](https://github.com/openssl/openssl/issues/14543)
  Our PRFs are part of KDF, however MACs are also used in this role and the
  DRBGs are too.  In terms of complexity, RAND >> MAC > KDF.  An EVP_PRF would
  sit between RAND and KDF.

- create EVP_AEAD_CIPHER
  This should have been done when they were invented.  Is it too late to do
  it now?

- AEAD for enc
  Introduce a different command for this?
  We'd need to define a file format for this.
  Should be limited to decryptions that fit into memory.

- fetchable signature algorithms
  - [#10512](https://github.com/openssl/openssl/issues/10512)
  - [#14467](https://github.com/openssl/openssl/issues/14467)
  - [#15624](https://github.com/openssl/openssl/issues/15624)
  Both for X509 and TLS

- fetchable any AlgorithmIdentifier.algorithm
  (signature algorithms aren't the only "composite" algorithms.  See EVP_PBE)

- mechanism to pass AlgorithmIdentifier.parameters to providers
  (we have that mechanism for ciphers, see EVP_CIPHER_asn1_to_params())

- CNG provider
  - [#3481](https://github.com/openssl/openssl/issues/3481)
  - [#6338](https://github.com/openssl/openssl/issues/6338)

- PVK

- PKCS #11 provider
  How much of the standard?
  There are at least 2 companies that would assist in this effort.

- ESNI
  - [#7482](https://github.com/openssl/openssl/issues/7482)

- Windows cert & key store

- FIPS 140-3

- EVP_SKEY (or equivalent)

- algorithm state serialisation
  - [#14222](https://github.com/openssl/openssl/issues/14222)
  - [#14223](https://github.com/openssl/openssl/issues/14223)

- HPKE (Hybrid Public Key Encryption)
  - [#14748](https://github.com/openssl/openssl/issues/14748)

- Attribute Certificate RFC-5755
  - [#14648](https://github.com/openssl/openssl/issues/14648)

- EVP SRP API

- support more store URIs
  - [#14001](https://github.com/openssl/openssl/issues/14001)

- blake 3
  - [#11613](https://github.com/openssl/openssl/issues/11613)

- CBOR (Compact Binary Object Representation)
  - [#13925](https://github.com/openssl/openssl/issues/13925)

- remove engine and legacy completely

- finish documenting everything

- finish deprecations

- more demos
  - [#14134](https://github.com/openssl/openssl/issues/14134)

- DTLS 1.3
  - [#13900](https://github.com/openssl/openssl/issues/13900)

- Certificate Compression RFC 8879
  - [#13597](https://github.com/openssl/openssl/issues/13597)

- More encoders/decoders, e.g. JWK support

- Review all "Post 3.0" items for possible inclusion

- Better configurability of TLS sigalgs

- Better run-time configurability of algorithm support
  API and run-time configuration file support for enabling/disabling
  algorithms in general (filtering on fetch level basis)

- Makefile dependencies
  Current generated Makefile gets things wrong and this requires cleaning
  (both clean and distclean) too frequently.

- Type sanity
  Replace long long with int64 and similar

- Internal platform library with clearly defined internal headers.
  (e_os.h is a mess, and all kinds of platform specific compensation
  code all over our source is a mess)
  
- Internal path building library (perhaps inspired from perl's File::Spec)
  (we currently handle the difference between VMS and unix-ish paths
  in an ad-hoc, and not very consistent manner)

- Better autoconfiguration of builds - automatically checking whether we can
  enable things like ec_nistp_64_gcc_128 or not

- Post-Quantum Cryptography - subject to standardization of finalists.
  See https://csrc.nist.gov/Projects/post-quantum-cryptography/round-3-submissions
  (Possibly integrating 3rd party providers/implementations if permission was granted).

- Installation verification tests - testing that the installed libraries
  headers, configuration and documentation are installed properly

