---
layout: default
title: oafp with Windows
parent: oafp
grand_parent: Guides
---

# oafp with Windows

List of examples of use of oafp running in Windows:

### Output a table with the list of network interfaces

In a powershell:
```powershell
Get-NetIPAddress | ConvertTo-Json | .\oafp.bat path="[].{ipAddress:IPAddress,prefixLen:PrefixLength,interface:InterfaceAlias}" sql=select\ *\ order\ by\ interface out=ctable
```

Result:
```
             ipAddress              │prefixLen│         interface
────────────────────────────────────┼─────────┼───────────────────────────
fe80::d925:f470:9e2d:cfde%10        │64       │Ethernet
fdb2:2c26:f4e4:0:b4c8:5841:e9e8:bc1f│128      │Ethernet
fdb2:2c26:f4e4:0:6b6f:8af0:423f:5fad│64       │Ethernet
10.211.55.5                         │24       │Ethernet
::1                                 │128      │Loopback Pseudo-Interface 1
127.0.0.1                           │8        │Loopback Pseudo-Interface 1
[#6 rows]
```

### Output a table with the current route table

In a powershell:
```powershell
Get-NetRoute | ConvertTo-Json | .\oafp.bat path="[].{destination:DestinationPrefix,gateway:NextHop,interface:InterfaceAlias,metric:InterfaceMetric}" sql=select\ *\ order\ by\ interface,destination out=ctable
```

Result:
```
              destination               │       gateway        │         interface         │metric
────────────────────────────────────────┼──────────────────────┼───────────────────────────┼──────
0.0.0.0/0                               │10.211.55.1           │Ethernet                   │15
10.211.55.0/24                          │0.0.0.0               │Ethernet                   │15
10.211.55.255/32                        │0.0.0.0               │Ethernet                   │15
10.211.55.5/32                          │0.0.0.0               │Ethernet                   │15
224.0.0.0/4                             │0.0.0.0               │Ethernet                   │15
255.255.255.255/32                      │0.0.0.0               │Ethernet                   │15
::/0                                    │fe80::21c:42ff:fe00:18│Ethernet                   │15
fdb2:2c26:f4e4:0:6b6f:8af0:423f:5fad/128│::                    │Ethernet                   │15
fdb2:2c26:f4e4:0:b4c8:5841:e9e8:bc1f/128│::                    │Ethernet                   │15
fdb2:2c26:f4e4::/64                     │::                    │Ethernet                   │15
fe80::/64                               │::                    │Ethernet                   │15
fe80::d925:f470:9e2d:cfde/128           │::                    │Ethernet                   │15
ff00::/8                                │::                    │Ethernet                   │15
127.0.0.0/8                             │0.0.0.0               │Loopback Pseudo-Interface 1│75
127.0.0.1/32                            │0.0.0.0               │Loopback Pseudo-Interface 1│75
127.255.255.255/32                      │0.0.0.0               │Loopback Pseudo-Interface 1│75
224.0.0.0/4                             │0.0.0.0               │Loopback Pseudo-Interface 1│75
255.255.255.255/32                      │0.0.0.0               │Loopback Pseudo-Interface 1│75
::1/128                                 │::                    │Loopback Pseudo-Interface 1│75
ff00::/8                                │::                    │Loopback Pseudo-Interface 1│75
[#20 rows]
```

### Output a table with the attached disk information

In a powershell:
```powershell
Get-Disk | ConvertTo-Csv -NoTypeInformation | .\oafp.bat in=csv path="[].{id:trim(UniqueId),name:FriendlyName,isBoot:IsBoot,location:Location,size:to_bytesAbbr(to_number(Size)),allocSize:to_bytesAbbr(to_number(AllocatedSize)),sectorSize:LogicalSectorSize,phySectorSize:PhysicalSectorSize,numPartitions:NumberOfPartitions,partitioning:PartitionStyle,health:HealthStatus,bus:BusType,manufacturer:Manufacturer,model:Model,firmwareVersion:FirmwareVersion,serialNumber:SerialNumber}" out=ctable
```

### Output a table with USB/PnP devices

In a powershell:
```powershell
Get-PnpDevice -PresentOnly | ConvertTo-Csv -NoTypeInformation | .\oafp.bat in=csv path="[].{class:PNPClass,service:Service,name:FriendlyName,id:InstanceId,description:Description,deviceId:DeviceID,status:Status,present:Present}" sql=select\ *\ order\ by\ class,service out=ctable
```