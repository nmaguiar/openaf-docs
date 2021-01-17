---
layout: default
title: csv
parent: Reference
grand_parent: OpenAF docs
---


## csv

### CSV.clear

__CSV.clear()__

````
Clears all internal structures. This will clear all data stored previously in this instance.
````
### CSV.clear

__CSV.clear()__

````
Clears all internal structures. This will clear all data stored previously in this instance.
````
### CSV.csv

__CSV.csv() : Array__

````
Returns a javascript array of maps with the current internal CSV representation.
````
### CSV.CSV

__CSV.CSV(aCsvString)__

````
Creates a new instance of the CSV object. Optionally you can provide a string that contains a CSV.
````
### CSV.CSV

__CSV.CSV(aCsvString)__

````
Creates a new instance of the CSV object. Optionally you can provide a string that contains a CSV.
````
### CSV.csv

__CSV.csv() : Array__

````
Returns a javascript array of maps with the current internal CSV representation.
````
### CSV.fromCSV

__CSV.fromCSV(aCSVString)__

````
Tries to convert aCSVString into an internal csv format.
````
### CSV.fromCSV

__CSV.fromCSV(aCSVString)__

````
Tries to convert aCSVString into an internal csv format.
````
### CSV.readFile

__CSV.readFile(aFilename) : Number__

````
Tries to read aFilename into the internal CSV representation. If successful the number of read lines will be returned. Otherwise an exception will be raised.
````
### CSV.readFile

__CSV.readFile(aFilename) : Number__

````
Tries to read aFilename into the internal CSV representation. If successful the number of read lines will be returned. Otherwise an exception will be raised.
````
### CSV.setSeparator

__CSV.setSeparator(aSeparator)__

````
Sets the default separator to use when building a CSV output (default is ;)
````
### CSV.setSeparator

__CSV.setSeparator(aSeparator)__

````
Sets the default separator to use when building a CSV output (default is ;)
````
### CSV.setStringDelimiter

__CSV.setStringDelimiter(aDelimiter)__

````
Sets the default string delimited to use when building a CSV output (default is ")
````
### CSV.setStringDelimiter

__CSV.setStringDelimiter(aDelimiter)__

````
Sets the default string delimited to use when building a CSV output (default is ")
````
### CSV.toCsv

__CSV.toCsv(anArrayOfMaps, anArrayOfKeys)__

````
Tries to convert a javascript anArrayOfMaps into an internal csv format. The array should be composed of maps whose elements must have the same keys (example: [ { "F1": 1, "F2": abc}, { "F1": 2, "F2": xyz } ]). Optionally anArrayOfKeys can be provided to restrict the keys used and to force their order.
````
### CSV.toCsv

__CSV.toCsv(anArrayOfMaps, anArrayOfKeys)__

````
Tries to convert a javascript anArrayOfMaps into an internal csv format. The array should be composed of maps whose elements must have the same keys (example: [ { "F1": 1, "F2": abc}, { "F1": 2, "F2": xyz } ]). Optionally anArrayOfKeys can be provided to restrict the keys used and to force their order.
````
### CSV.w

__CSV.w() : String__

````
Returns the current CSV internal representation in the form of a string.
````
### CSV.w

__CSV.w() : String__

````
Returns the current CSV internal representation in the form of a string.
````
### CSV.writeFile

__CSV.writeFile(aFilename) : Number__

````
Tries to write the internal CSV representation into aFilename. If successful it will return the number of lines written, otherwise an exception will be raised.
````
### CSV.writeFile

__CSV.writeFile(aFilename) : Number__

````
Tries to write the internal CSV representation into aFilename. If successful it will return the number of lines written, otherwise an exception will be raised.
````
