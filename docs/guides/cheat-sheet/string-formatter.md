---
layout: default
title: String formatter
parent: cheat-sheet
grand_parent: Guides
---

# String formatter

The following combinations of "$f" can be used whenever you need to build a string (equivalent to Java's java.util.Formatter).

Basics:

````
%[argument_index$][flags][width][.precision]conversion
````

## Flags

* '-' (left-justified)
* '#'; '+' (include sign)
* ' ' (leading space)
* '0' (zero-padded)
* ',' (separators)
* '(' (enclose negative values)

## Conversion

* b/B (boolean)
* h/H (hash)
* s/S (string)
* "-" (left justify)
* c/C (character)       

| Adding | Command | Results |
|--------|---------|---------|
| **Time**   | $f("Time: %1$tD %1t$tT", new Date()) | "Time 05/30/22 01:02:03" |
| **Date**   | $f("Date: %1$ty/%1$tm/%1$td %1$tH:%1$tM:%1$tS", new Date()) | "Date: 22/05/30 01:02:03" |
| **Date full year** | $f("Year: %tY", new Date()) | "2022" |
| **Number round** | $f("Decimals: %.2f %.2f", 1.9, 1.999) | "decimals: 1.90 2.00" |
| **Number space pad** | $f("%10.2f", 1.9) | (with 6 spaces) "1.90" |
| **Number left space pad** | $f("%-10.2f", 1.9) | "1.90" (with 6 spaces) |
| **Number zero pad** | $f("%010.2f", 1.9) | "0000001.90" |
| **Number sign** | $f("%+.2f %+.2f", 1.9, -1.9) | "+1.90 -1.90" |
| **Number sign enclosure** | $f("%+.0f %(.0f", 1, -1) | "+1 (1)" |
| **String space pad** | $f("%10s", "hello") | (with five spaces) "hello" |
| **String left space pad** | $f("%-10s", "hello") | "hello" (with five spaces) |
| **Boolean uppercase** | $f("%B %B", true, false) | "TRUE FALSE" |
