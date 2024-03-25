---
layout: default
title: oafp to Excel
parent: oafp
grand_parent: Guides
---

# oafp to Excel

List of examples of use of oafp to parse data to Excel:

### Processes each json file in /some/data creating and updating the data.xlsx file with a sheet for each file 

```bash
find /some/data -name "*.json" | xargs -I '{}' /bin/sh -c 'oafp file={} output=xls xlsfile=data.xlsx xlsopen=false xlssheet=$(echo {} | sed "s/.*\/\(.*\)\.json/\1/g" )'
```

### Building an Excel file with the AWS IPv4 and IPv6 ranges

```bash
curl https://ip-ranges.amazonaws.com/ip-ranges.json > ip-ranges.json

oafp ip-ranges.json path=prefixes out=xls xlsfile=aws-ip-ranges.xlsx xlssheet=ipv4

oafp ip-ranges.json path=ipv6_prefixes out=xls xlsfile=aws-ip-ranges.xlsx xlssheet=ipv6
```

This will create the _aws-ip-ranges.xlsx_ file with an ipv4 and an ipv6 sheet.