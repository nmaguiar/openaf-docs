# Is defined or undefined

Two of the most common functions used in OpenAF are: _isDef_ and _isUnDef_. The reason is because javascript variables, when created, are "undefined" and only become defined after a value is assigned to it. So, before using that javascript variable is common to test if it's defined or not.

````javascript
> var abc
> isDef(abc)
false
> abc = 123
123
> isDef(abc)
true
````

Ok, what happens if it's undefined?

````javascript
> var xyz
> isUnDef(xyz)
true
> String(xyz + 123)
NaN
````