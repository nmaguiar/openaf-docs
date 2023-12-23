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
### CSV.fromCSV

__CSV.fromCSV(aCSVString)__

````
Tries to convert aCSVString into an internal csv format.
````
### CSV.fromStream

__CSV.fromStream(aStream, aFunction)__

````
Tries to read a CSV from aStream a calls aFunction with a map representing the fields of each line. The format is determined by CSV.setStreamFormat and each map entry will have either the number of the field or the corresponding name depending on the header options.
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
### CSV.setStreamFormat

__CSV.setStreamFormat(aMap)__

````
Set the options that will be used with CSV.fromStream. Available options are:

format: String
  You can choose between DEFAULT, EXCEL, INFORMIX_UNLOAD, INFORMIX_UNLOAD_CSV, MYSQL, RFC4180, ORACLE, POSTGRESQL_CSV, POSTGRESQL_TEXT and TDF (please check http://commons.apache.org/proper/commons-csv/user-guide.html)
withHeader: Boolean
  Tries to automatically use the available header
withHeaders: Array
  An array of header strings in the order that data lines will appear.
quoteMode: String
  You can choose between ALL, ALL_NON_NULL, MINIMAL, NON_NUMERIC and NONE.
withDelimiter: String
  A single character as a custom delimiter
withEscape: String
  A single character as a custom escape
withNullString: String


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
### CSV.toStream

__CSV.toStream(aStream, aFunction)__

````
Tries to write a CSV to aStream calling aFunction and expecting it to return a map with the fields previously set with CSV.setStreamFormat and corresponding values for each line (each call will represent a line). The fields need to be specificed in withHeaders map property in CSV.setStreamFormat. The aFunction will be called continuosly until a different output from a map is returned. Note: aStream won't be closed.
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
