---
layout: default
title: "Beginner: Date diff"
parent: Guides
grand_parent: OpenAF docs
---

# Date diff

Continuing on the javascript Date manipulation functions available in the OpenAF's ow.format library when it comes to comparing date objects. Usually the question between to dates is how many milliseconds, seconds, minutes, hours, days, weeks, months and/or years the date differ. So there is a set of functions, just for date, under ow.format.dateDiff.in*(dateBefore, dateAfter):

````javascript
ow.loadFormat();

// Get a date last year
var beforeDate = ow.format.toDate("20180503 025401", "yyyyMMdd HHmmss");
var afterDate = ow.format.toDate("20190701 152012", "yyyyMMdd HHmmss");

print(ow.format.dateDiff.inYears(beforeDate, afterDate)); // 1
print(ow.format.dateDiff.inMonths(beforeDate, afterDate)); // 14
print(ow.format.dateDiff.inWeeks(beforeDate, afterDate)); // 60
print(ow.format.dateDiff.inDays(beforeDate, afterDate)); // 424
print(ow.format.dateDiff.inHours(beforeDate, afterDate)); // 10188
print(ow.format.dateDiff.inMinutes(beforeDate, afterDate)); // 611306
print(ow.format.dateDiff.inSeconds(beforeDate, afterDate)); // 36678371
print(afterDate - beforeDate); // in ms, 36678371000
````

If you don't provide an afterDate it will just default to the current date.