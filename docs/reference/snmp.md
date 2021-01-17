---
layout: default
title: snmp
parent: Reference
grand_parent: OpenAF docs
---


## snmp

### SNMP.get

__SNMP.get(aOID) : Object__

````
Gets a value for the provided aOID (expects value to be string or convertible to string).
````
### SNMP.get

__SNMP.get(aOID) : Object__

````
Gets a value for the provided aOID (expects value to be string or convertible to string).
````
### SNMP.inform

__SNMP.inform(aOID, aDataArray)__

````
Tries to send an inform based on aOID and using aDataArray where each element should be a map with oid, type (i - integer, u - unsigned, c - counter32, s - string, x - hex string, d - decimal string, n - nullobj, o - objid, t - timeticks, a - ipaddress,) and value.
````
### SNMP.inform

__SNMP.inform(aOID, aDataArray)__

````
Tries to send an inform based on aOID and using aDataArray where each element should be a map with oid, type (i - integer, u - unsigned, c - counter32, s - string, x - hex string, d - decimal string, n - nullobj, o - objid, t - timeticks, a - ipaddress,) and value.
````
### SNMP.SNMP

__SNMP.SNMP(anAddress, aCommunity, aTimeout, retries, version, securityMap)__

````
Tries to establish a SNMP connection to the given address (anAddress in the form of udp:x.x.x.x/port) of a specific community (aCommunity (e.g public)) with a provided timeout (aTimeout) and number of retries. You can also specify the version (2 or 3). For version 3 you can also provide a securityMap with the following entries:

   securityName   (String)
   authProtocol   (String) HMAC128SHA224, HMAC192SHA256, HMAC256SHA384, HMAC384SHA512, MD5, SHA
   privProtocol   (String) 3DES, AES128, AES192, AES256, DES
   authPassphrase (String)
   privPassphrase (String)
   engineId       (String)


````
### SNMP.SNMP

__SNMP.SNMP(anAddress, aCommunity, aTimeout, retries, version, securityMap)__

````
Tries to establish a SNMP connection to the given address (anAddress in the form of udp:x.x.x.x/port) of a specific community (aCommunity (e.g public)) with a provided timeout (aTimeout) and number of retries. You can also specify the version (2 or 3). For version 3 you can also provide a securityMap with the following entries:

   securityName   (String)
   authProtocol   (String) HMAC128SHA224, HMAC192SHA256, HMAC256SHA384, HMAC384SHA512, MD5, SHA
   privProtocol   (String) 3DES, AES128, AES192, AES256, DES
   authPassphrase (String)
   privPassphrase (String)
   engineId       (String)


````
### SNMP.start

__SNMP.start()__

````
Starts the client connection (usually already invoked by the SNMP constructor, so there shouldn't be a need to invoke it).
````
### SNMP.start

__SNMP.start()__

````
Starts the client connection (usually already invoked by the SNMP constructor, so there shouldn't be a need to invoke it).
````
### SNMP.trap

__SNMP.trap(aOID, aDataArray, shouldInform)__

````
Tries to send a trap based on aOID and using aDataArray where each element should be a map with oid, type (i - integer, u - unsigned, c - counter32, s - string, x - hex string, d - decimal string, n - nullobj, o - objid, t - timeticks, a - ipaddress,) and value. Optionally you can determine if shouldInform instead of sending the trap.
````
### SNMP.trap

__SNMP.trap(aOID, aDataArray, shouldInform)__

````
Tries to send a trap based on aOID and using aDataArray where each element should be a map with oid, type (i - integer, u - unsigned, c - counter32, s - string, x - hex string, d - decimal string, n - nullobj, o - objid, t - timeticks, a - ipaddress,) and value. Optionally you can determine if shouldInform instead of sending the trap.
````
