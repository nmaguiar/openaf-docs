---
layout: default
title: "Medium: Function profiling"
parent: Guides
grand_parent: OpenAF docs
---

# Function profiling

When coding/scripting there are two important things to do depending on the use the code is going to have: debugging and profiling.

In OpenAF there is an included mini test library that it's actually also used to perform the OpenAF's own build automated tests: _ow.test_.

In this article we are going to show how to use the _ow.test_ to perform quick code profiling.

## Example

Let's take a simple exercise. Imagine you have a 10K entries array and you don't know what to use: _$from(array).select()_ or _array.map()_. 

Let's create the array and load _ow.test_:

````javascript
ow.loadTest();
var ar = [];
for(let i = 0; i < 10000; i++) {
    ar.push(i);
}
````

Let's create now the sample function for _$from_:

````javascript
function fromTest() {
    $from(ar)
    .select((r) => {
        return r + 1;
    });
}
````

And _map_:

````javascript
function mapTest() {
    ar
    .map((r) => {
        return r + 1;
    });
}
````

We have the array and we have the test functions now let's use _ow.test_ to understand how each function behaves during 400 executions:

````javascript
for(let i = 0; i < 400; i++) {
    ow.test.test("$from", fromTest);
    ow.test.test("map", mapTest);
}
````

Now for the results:

````javascript
print("Results:\n" + printMap(ow.test.getProfile()));
print("Averages:\n" + printMap(ow.test.getAllProfileAvg()));
````

![Profile test resutls](profile-test-results.png)

So, clearly, in this case, _map_ won to the _$from_. The average execution time is better and even the minimum time for _$from_ is worse than the max for _map_.

Of course each case is different and that's the reason that there never is a "silver bullet" solution. You just have to test it.