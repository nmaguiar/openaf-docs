---
layout: default
title: Check current Java TLS
parent: oJobIO
grand_parent: Guides
---

# Check current Java TLS

Java controls the cipher suites and TLS protocol used to perform network connections. You can check which a particular JRE (Java Runtime Environment) by executing:

```
ojob ojob.io/java/checkTLS
```

resulting in a map equivalent to:

```yaml
╭ given_cipher_suites                  ╭ [0] : TLS_AES_256_GCM_SHA384
│                                      ├ [1] : TLS_AES_128_GCM_SHA256
│                                      ├ [2] : TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384
│                                      ├ [3] : TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
│                                      ├ [4] : TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
│                                      ├ [5] : TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
│                                      ├ [6] : TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
│                                      ├ [7] : TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
│                                      ├ [8] : TLS_RSA_WITH_AES_256_GCM_SHA384
│                                      ├ [9] : TLS_RSA_WITH_AES_128_GCM_SHA256
│                                      ├ [10]: TLS_RSA_WITH_AES_256_CBC_SHA
│                                      ╰ [11]: TLS_RSA_WITH_AES_128_CBC_SHA
├ ephemeral_keys_supported            : true
├ session_ticket_supported            : false
├ tls_compression_supported           : false
├ unknown_cipher_suite_supported      : false
├ beast_vuln                          : false
├ able_to_detect_n_minus_one_splitting: false
├ insecure_cipher_suites
├ tls_version                         : TLS 1.3
╰ rating                              : Probably Okay
```

## Forcing a different TLS

You can for a specific TLS adding a Java system property:

```
export OAF_JARGS="-Djdk.tls.client.protocols=TLSv1.2"
ojob ojob.io/java/checkTLS
```

resulting in a map equivalent to:

```yaml
╭ given_cipher_suites                  ╭ [0]: TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384
│                                      ├ [1]: TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
│                                      ├ [2]: TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
│                                      ├ [3]: TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
│                                      ├ [4]: TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
│                                      ├ [5]: TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
│                                      ├ [6]: TLS_RSA_WITH_AES_256_GCM_SHA384
│                                      ├ [7]: TLS_RSA_WITH_AES_128_GCM_SHA256
│                                      ├ [8]: TLS_RSA_WITH_AES_256_CBC_SHA
│                                      ╰ [9]: TLS_RSA_WITH_AES_128_CBC_SHA
├ ephemeral_keys_supported            : true
├ session_ticket_supported            : false
├ tls_compression_supported           : false
├ unknown_cipher_suite_supported      : false
├ beast_vuln                          : false
├ able_to_detect_n_minus_one_splitting: false
├ insecure_cipher_suites
├ tls_version                         : TLS 1.2
╰ rating                              : Probably Okay
```