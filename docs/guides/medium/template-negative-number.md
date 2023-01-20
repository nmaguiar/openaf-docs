---
layout: default
title: Template negative number
parent: Medium
grand_parent: Guides
---

# Template negative number

When using [OpenAF's template](../cheat-sheet/templating.md) functionality you might find yourself with the following situation involving negative values:

````javascript
ow.loadTemplate()
ow.template.addOpenAFHelpers()

var someDateInTheFuture = new Date(now() + (1000*60*60))

tprint("Something is going to happen in {{$dateDiff d 'minutes'}} minutes", { d: someDateInTheFuture })
// Something is going to happen in -59 minutes
````

Althought the _$dateDiff_ OpenAF template helper did it's job it returns a negative value since the provided date is in the future. Nevertheless you would probably like to use the absolute value, instead of the literal value, for you sentence to make sense.

That's possible using other OpenAF template helpers in chain:

````javascript
ow.loadTemplate()
ow.template.addOpenAFHelpers()

var someDateInTheFuture = new Date(now() + (1000*60*60))

tprint("Something is going to happen in {% raw %}{{$path ($dateDiff d 'minutes') 'abs(@)'}} minutes{% endraw %}", { d: someDateInTheFuture })
// Something is going to happen in 59 minutes
````

The _$path_ helper provides several functions over values, even when not applied to an existing map/array. In this case it's applied to the result of running the _$dateDiff_ helper.