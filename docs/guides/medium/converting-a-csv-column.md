---
layout: default
title: Converting a CSV column
parent: Medium
grand_parent: Guides
---

# Converting a CSV column

If you have a CSV file and you need to convert a specific column you can use OpenAF to make the necessary conversions using javascript code and any of the available OpenAF's conversion functions.

## The sample CSV

Let's start with a sample CSV file:

```csv
id,file,size,flag
1,fileA.bin,12 KB,true
2,fileB.bin,5.5 MB,false
3,fileC.bin,1.2 MB,false
```

In this CSV file we would need to convert the column size from the string representation to a numeric absolute bytes representation.

## The conversion function

To do it we can use the function _ow.format.fromBytesAbbreviation_. This function will convert the string representation to the number absolute bytes representation that we need:

```javascript
ow.loadFormat()
ow.format.fromBytesAbbreviation("5.5 MB")
// 5767168
```

> If you need to distinguish between MiB and MB you can use a second boolean argument to allow for the base 10 (decimal) interpretation: ```ow.format.fromBytesAbbreviation("5.5 MB", true) // 5500000```

## Changing the CSV column

We have the conversion function but now we need to apply it to all values of the CSV's size column. The [_$csv_ shortcut](../cheat-sheet/csv-shortcuts.md) provide the functionality to do this:

```javascript
// Load the ow.format library
ow.loadFormat()

// On the first call of the function output to stdout the CSV header
var printHeader = true

// Go through each line of the csv file and make the conversions
$csv().fromInFile("input.csv").toOutFn(lineData => {
    // lineData is a javascript map representing the data parsed from each CSV file line

    // If this is the first call print the CSV header
    if (printHeader) {
        // Printing the lineData keys which are actually the headers
        print(Object.keys(lineData).join(","))
        printHeader = false
    }

    // Converting the field 'size' using the function ow.format.fromBytesAbbreviation
    lineData.size = ow.format.fromBytesAbbreviation(lineData.size)
    // Output the lineData values in CSV format
    print(Object.values(lineData).join(","))
})
```

Placing this code in a _convert.js_ file you can execute it and check the converted output:

```
$ oaf -f convert.js > output.csv

$ cat output.csv
id,file,size,flag
1,fileA.bin,12288,true
2,fileB.bin,5767168,false
3,fileC.bin,1258291,false
```