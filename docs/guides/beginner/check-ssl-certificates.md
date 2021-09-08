---
layout: default
title: Check SSL certificates
parent: Beginner
grand_parent: Guides
---

# Check SSL certificates

OpenAF can retrieve the SSL public certificates from an external site and check their corresponding properties. This can be useful, for example, to alert on the certificate validity approaching end.

_(version >= 20210721)_

## How to get the SSL public certificates

Simply use the ___ow.net.getSSLPublicCertificates__ function:

````javascript
ow.loadNet();
var certificates = ow.net.getSSLPublicCertificates("github.com", 443);
````

This function requires you to provide the external site hostname (for example, github.com) and the corresponding port (for example, 443 (https default port)).

Keep in mind that HTTPS SSL certificates can be a collection of certificates. For that reason the variable _certificates_ will be an array.

> Each array element is a certificate java object extending java.security.cert.X509Certificate 

## How to retrieve properties

You can check the available properties in the openaf console with the auto-complete feature or by executing:

````javascript
> desc certificates[0]
````

The following example retrieves the subject and the validity period of each certificate:

````javascript
sprint( certificates.map(cert => ({
    subject  : cert.subjectDN,
    notBefore: cert.notBefore,
    notAfter : cert.notAfter
})) );

// [
//   {
//     "subject": "CN=github.com, O=\"GitHub, Inc.\", L=San Francisco, ST=California, C=US",
//     "notBefore": "Thu Mar 25 00:00:00 GMT 2021",
//     "notAfter": "Wed Mar 30 23:59:59 GMT 2022"
//   },
//   {
//     "subject": "CN=DigiCert High Assurance TLS Hybrid ECC SHA256 2020 CA1, O=\"DigiCert, Inc.\", C=US",
//     "notBefore": "Thu Dec 17 00:00:00 GMT 2020",
//     "notAfter": "Mon Dec 16 23:59:59 GMT 2030"
//   }
// ]
````