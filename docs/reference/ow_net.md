---
layout: default
title: ow.net
parent: Reference
grand_parent: OpenAF docs
---


## ow.net

### ow.net.getActualTime

__ow.net.getActualTime(useAlternative) : Date__

````
Retrieves the current actual time from worldtimeapi.org (through https). The current actual time will be returned in a Date. If useAlternative = true it will use worldclockapi.com (through http)
````
### ow.net.getAddressType

__ow.net.getAddressType(aAddress) : Map__

````
Given aAddress tries to return a map with the following flags: isValidAddress, hostname, ipv4, ipv6 and privateAddress
````
### ow.net.getDoH

__ow.net.getDoH(aAddr, aType, aProvider) : Array__

````
Performs a DNS over HTTPs query with aAddr. Optionally you can provide the aType of record (defaults to 'a') and the DNS over HTTPs aProvider between 'google' and 'cloudflare'.
````
### ow.net.getHost2IP

__ow.net.getHost2IP(aHost) : String__

````
Tries to resolve aHost to an IP address using the default DNS.
````
### ow.net.getHostAddress

__ow.net.getHostAddress() : String__

````
Returns the current host ip address.
````
### ow.net.getHostName

__ow.net.getHostName() : String__

````
Returns the current hostname.
````
### ow.net.getIP2Host

__ow.net.getIP2Host(aIP) : String__

````
Tries to reverse DNS aIP to a host address using the default DNS.
````
### ow.net.getPublicIP

__ow.net.getPublicIP(aIPAddress) : Map__

````
Uses the functionality provided by https://ifconfig.co to return a map with the apparent current public ip address, public hostname and a guess of country and city. Please be aware of the request limits of the service (around 1 request per minute).
If aIPAddress is provided it will use the functionality provided by http://ip-api.com (if aIPAddress is a empty string it will use the current public IP address). Please be also aware of non-commercial and request limits of the service (around 45 requests per minute). The details provided by each service might differ depending on how update is each of the services' databases.
````
### ow.net.getReverseDoH

__ow.net.getReverseDoH(aIP, aProvider) : Array__

````
Tries to retrieve the reverse DNS of aIP using DNS over HTTPs. Optionally you can choose the aProvider between 'google' and 'cloudflare'.
````
### ow.net.getSSLPublicCertificates

__ow.net.getSSLPublicCertificates(aHost, aPort) : Array__

````
Given aHost and aPort for a HTTPs connection it will retrieve the array of peer certificates available. You can retrieve the specific public key by using the method .getPublicKey for each array element. Usually you be interested on the first certificate of the returned array.
````
### ow.net.getTLSCertificates

__ow.net.getTLSCertificates(aHost, aPort, withJava, aPath, aPass, aSoTimeout) : Array__

````
Tries to retreive the TLS certificates from aHost, aPort (defaults to 443). Optionally if withJava=true the original certificate Java object will also be included. If the CA certificates is in a different location you can provide aPath and the corresponding aPass. Additionally you can specificy aSoTimeout (socket timeout in ms) which defaults to 10s.
````
### ow.net.getWhoIs

__ow.net.getWhoIs(aQuery, aInitServer) : Map__

````
Tries to perform a whois aQuery for a domain or an ip address. Optionally you can provide aInitServer (defaults to whois.iana.org)
````
### ow.net.testHost

__ow.net.testHost(aAddress, aTimeout) : Map__

````
Uses the java implementation (e.g. usually ICMP ping) for testing reachability to an aAddress. It timeouts after aTimeout (defaults to 4000ms). Returns a map with the "time" spent trying to get an answer from aAddress and a boolean "reachable" with the result.
````
### ow.net.testPort

__ow.net.testPort(aAddress, aPort, aCustomTimeout) : boolean__

````
Tries to connect to aPort (e.g. 1234) on aAddress (e.g. 1.2.3.4). If the connection is successfull it will disconnect and return true, otherwise it will return false. If aCustomTimeout (in ms) is defined, it will use that value as the timeout instead of the 1,5 seconds by default.
````
### ow.net.testPortLatency

__ow.net.testPortLatency(aHost, aPort, aCustomTimeout) : Number__

````
Test establishing a TCP socket connection with aHost on aPort. Optionally aCustomTimeout can be provided (defaults to 60000 ms). The test will be timed and the time in ms will be returned. If returned a time < 0 then an error occurred or the  host:port couldn't be reached.
````
### ow.net.testPublicPort

__ow.net.testPublicPort(aPort) : Map__

````
Uses the functionality provided by http://ifconfig.co to return a map with the result of testing if aPort is within public  reach from your apparent current public ip address. Please be aware of the request limits of the service (around 1 request per minute).
````
### ow.net.testURLLatency

__ow.net.testURLLatency(aURL, aCustomTimeout) : Number__

````
Test sending a HTTP(s) GET to aURL. Optionally aCustomTimeout can be provided. The test will be timed and the time in ms will be returned. If returned a time < 0 then an error occurred or the host:port couldn't be reached.
````