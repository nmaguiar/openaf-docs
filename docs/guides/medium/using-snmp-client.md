---
layout: default
title: Using the SNMP plugin
parent: Medium
grand_parent: Guides
---

# Using the SNMP plugin

In OpenAF there are two main SNMP plugins: SNMP and SNMP server. In this article we are going to focus on the SNMP plugin that provide SNMP client functionality. 

SNMP has different versions (e.g. 1, 2, 3) that require different settings. Starting with version 1 and 2 all you need is the SNMP connection details and, optinionally, a community:

````javascript
plugin("SNMP");
var snmp = new SNMP("udp:demo.snmplabs.com/161", "public");  // version 1/2
````
## Checking an OID value

To get the value associated with an OID:

````javascript
snmp.get("1.3.6.1.2.1.1.3.0");
// {
//  "1.3.6.1.2.1.1.3.0": "36 days, 12:34:56.51"
//}
````

## Sending a trap/inform

To send a trap simply:

````javascript
snmp.trap("1.3.6.1.4.1.20408.4.1.1.2", [
    { OID: "1.2.3.4.5.6.7.8", type: "s", value: "My error message." }
])
````

You just need to provide the trap OID and an array of OID based values. Each value can have a different type. The supported types are:

| Type | Description |
|------|-------------|
| i    | Integer     |
| u    | Unsigned    |
| c    | Counter32   |
| s    | String      |
| x    | Hex String  |
| d    | Decimal String |
| n    | A null object |
| o    | An object id |
| t    | Timeticks |
| a    | An ip address |

To inform it's exactly the same but it will return you a Java response object:

````javascript
var response = snmp.inform("1.3.6.1.4.1.20408.4.1.1.2", [
    { OID: "1.2.3.4.5.6.7.8", type: "s", value: "My error message." }
])
````

In contrast sending a trap will return immediately and there won't be any acknowledgement.  

## Version 3

On version 3 you need to provide a little more information:

````javascript
plugin("SNMP");
var aTimeout = 3000, aNumberOfRetries = 3;
var snmp = new SNMP("udp:demo.snmplabs.com/161", "public", aTimeout, aNumberOfRetries, 3, {
    engineId      : "8000000001020304",
    authPassphrase: "authKey1",
    privPassphrase: "privKey1",
    authProtocol  : "MD5",
    privProtocol  : "DES",
    securityName  : "usr-md5-des"
})
````

But all the rest is same as shown previously.