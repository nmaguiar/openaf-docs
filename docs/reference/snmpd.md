---
layout: default
title: snmpd
parent: Reference
grand_parent: OpenAF docs
---


## snmpd

### SNMPD.addOID

__SNMPD.addOID(aOID, aFunction)__

````
Adds a callback when the specified OID (should end in .0) gets look up. The call back aFunction receives the aOID as a parameter. See more: http://www.jitendrazaa.com/blog/java/snmp/creating-snmp-agent-server-in-java-using-snmp4j/
````
### SNMPD.addOID

__SNMPD.addOID(aOID, aFunction)__

````
Adds a callback when the specified OID (should end in .0) gets look up. The call back aFunction receives the aOID as a parameter. See more: http://www.jitendrazaa.com/blog/java/snmp/creating-snmp-agent-server-in-java-using-snmp4j/
````
### SNMPd.setOID

__SNMPd.setOID(aOID, aFunction)__

````
Changes the callback for a specific OID (should end in .0). The call back aFunction receives the aOID as a parameter.
````
### SNMPd.setOID

__SNMPd.setOID(aOID, aFunction)__

````
Changes the callback for a specific OID (should end in .0). The call back aFunction receives the aOID as a parameter.
````
### SNMPd.SNMPd

__SNMPd.SNMPd(anAddress, aSysDesc) : SNMPd__

````
Prepares a SNMP server listening on the given anAddress (e.g. udp:1.2.3.4/161). Optionally you can also provide a system description (aSysDesc).
````
### SNMPd.SNMPd

__SNMPd.SNMPd(anAddress, aSysDesc) : SNMPd__

````
Prepares a SNMP server listening on the given anAddress (e.g. udp:1.2.3.4/161). Optionally you can also provide a system description (aSysDesc).
````
### SNMPd.start

__SNMPd.start(aCommunity)__

````
Starts the SNMP server given a community name. If no community is provided, public is assumed.
````
### SNMPd.start

__SNMPd.start(aCommunity)__

````
Starts the SNMP server given a community name. If no community is provided, public is assumed.
````
### SNMPd.stop

__SNMPd.stop()__

````
Stops the SNMP server.
````
### SNMPd.stop

__SNMPd.stop()__

````
Stops the SNMP server.
````
