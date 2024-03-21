---
layout: default
title: oafp with OpenAF
parent: oafp
grand_parent: Guides
---

# oafp with OpenAF

List of examples of use of oafp using OpenAF functionality:

### Listing all currently accessible oPacks

```bash
oaf -c "sprint(getOPackRemoteDB())" | oafp maptoarray=true opath="[].{name:name,description:description,version:version}" from="sort(name)" out=ctable
```

### Current OS information visible to OpenAF

```bash
oafp -v path=os
```

### List all network addresses returned from the current DNS server for a hostname

```bash
oaf -c "sprint(ow.loadNet().getDNS('yahoo.com'))" | oafp from="sort(Address)" out=ctable
```

Result:
```
   Name   │AdditionalName│        Address         │RRsetType│DClass│Type│TTL
──────────┼──────────────┼────────────────────────┼─────────┼──────┼────┼───
yahoo.com.│null          │yahoo.com./74.6.143.25  │1        │1     │1   │512
yahoo.com.│null          │yahoo.com./74.6.143.26  │1        │1     │1   │512
yahoo.com.│null          │yahoo.com./74.6.231.20  │1        │1     │1   │512
yahoo.com.│null          │yahoo.com./74.6.231.21  │1        │1     │1   │512
yahoo.com.│null          │yahoo.com./98.137.11.163│1        │1     │1   │512
yahoo.com.│null          │yahoo.com./98.137.11.164│1        │1     │1   │512
[#6 rows]
```

### List the TLS certificates of a target host with a sorted alternative names

```bash
oaf -c "sprint(ow.loadNet().getTLSCertificates('yahoo.com',443))" | oafp path="[].{issuer:issuerDN,subject:subjectDN,notBefore:notBefore,notAfter:notAfter,alternatives:join(' | ',sort(map(&[1],nvl(alternatives,\`[]\`))))}" out=ctree
```

Result:
```
╭ [0] ╭ issuer      : CN=DigiCert SHA2 High Assurance Server CA, OU=www.digicert.com, O=DigiCert Inc, C=US
│     ├ subject     : CN=yahoo.com, O=Oath Holdings Inc., L=Sunnyvale, ST=California, C=US
│     ├ notBefore   : 2024-02-20T00:00:00.000Z
│     ├ notAfter    : 2024-08-14T23:59:59.000Z
│     ╰ alternatives: *.amp.yimg.com | *.att.yahoo.com | *.global.vespa.oath.cloud | *.media.yahoo.com | *.www.yahoo.com | *.yahoo.com | add.my.yahoo.com | brb.yahoo.net | ca.my.yahoo.com |
│                     ca.rogers.yahoo.com | ddl.fp.yahoo.com | fr-ca.rogers.yahoo.com | hk.rd.yahoo.com | mbp.yimg.com | s.yimg.com | tw.rd.yahoo.com | yahoo.com
╰ [1] ╭ issuer      : CN=DigiCert High Assurance EV Root CA, OU=www.digicert.com, O=DigiCert Inc, C=US
      ├ subject     : CN=DigiCert SHA2 High Assurance Server CA, OU=www.digicert.com, O=DigiCert Inc, C=US
      ├ notBefore   : 2013-10-22T12:00:00.000Z
      ├ notAfter    : 2028-10-22T12:00:00.000Z
      ╰ alternatives:
```