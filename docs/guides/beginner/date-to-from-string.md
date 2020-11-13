---
layout: default
title: "Beginner: Date to/from string"
parent: Guides
grand_parent: OpenAF docs
---

# Date to/from string

To help with javascript Date manipulation in OpenAF there are several helper functions in the ow.format library. To use them do load the format library first:

````javascript
ow.loadFormat();
````

One of the most used date functions is the ow.format.toDate and the ow.format.fromDate. These helper functions let you convert strings into Dates and Dates into strings.

````javascript
var someDate = ow.format.toDate("20170504", "yyyyMMdd");
print(someDate); // "2017-05-04T00:00:00.000Z"

var aString = ow.format.fromDate(new Date(), "yyyyMMdd-HHmmss");
print(aString); // "20190730-000000"
````

They are very similar, in spirit, to the SQL to_date and to_char functions but you have to be careful that they use the Java mask format: 

````yaml
  G - Era descriptor (AD)
  y - Year (1996; 96)
  Y - Week year (2009; 09)
  M - Month in year (July; Jul; 07)
  w - Week in year (27)
  W - Week in month (2)
  D - Day in year (189)
  d - Day in month (10)
  F - Day of week in month (2)
  E - Day name in week (Tuesday; Tue)
  u - Day number of week (1 = Monday, ..., 7 = Sunday) (1)
  a - Am/pm number (PM)
  H - Hour in day (0-23)
  k - Hour in day (1-24)
  K - Hour in am/pm (0-11)
  h - Hour in am/pm (1-12)
  m - Minute in hour (30)
  s - Second in minute (55)
  S - Millisecond (978)
  z - Time zone (Pacific Standard Time; PST; GMT-08:00)
  Z - Time zone (-0800)
  X - Time zone (-08; -0800; -08:00)
````