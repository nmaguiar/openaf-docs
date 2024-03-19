---
layout: default
title: oafp to Excel
parent: oafp
grand_parent: Guides
---

# oafp to Excel

### Processes each json file in /some/data creating and updating the data.xlsx file with a sheet for each file 

```bash
find /some/data -name "*.json" | xargs -I '{}' /bin/sh -c 'oafp file={} output=xls xlsfile=data.xlsx xlsopen=false xlssheet=$(echo {} | sed "s/.*\/\(.*\)\.json/\1/g" )'
```