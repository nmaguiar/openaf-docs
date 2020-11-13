# Comparing maps and arrays

In javascript it's easy to compare simple types but the same doesn't apply to maps or arrays. Let's take some examples:

````javascript
var a = {
  "name": "Line",
  "points": {
    "start": {
      "x": 5,
      "y": 10
    },
    "end": {
      "x": 15,
      "y": 25
    }
  }
};

var b = {
  "name": "Line",
  "points": {
    "start": {
      "x": 5,
      "y": 10
    },
    "end": {
      "x": 15,
      "y": 25
    }
  }
}
````

The map _a_ and _b_ are almost equal but if you compare them:

````javascript
> a == b
false
> 1 == 1
true
> "a" = "a"
true
````

The reason is that _a_ and _b_ are different objects despite having the same keys, strutucture and values. The only way to compare is to compare key by key and value by value. In OpenAF the function **_compare_** does just that:

````javascript
> compare(a, b)
true
>
> p.points.start.x = 0
> p.points.start.y = 0
>
> compare(a, b)
false
````

Using the openaf console you can actually see the difference:

````javascript
> diff a with b
 -      "x": 5,
 -      "y": 10
 +      "x": 0,
 +      "y": 0
````

## Comparing arrays

What about arrays? Well, they are also objects. Alone (e.g. [1, 2, 3]) or mixed (e.g. { a: 1, b: [ 1, 2, 3]}). So you can use the _compare_ function in the same way:

````javascript
> compare([1, 2, 3], [1, 2, 3])
true
> compare([0, 1, 2, 3, 4], [1, 2, 3])
false
````