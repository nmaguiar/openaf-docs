---
layout: default
title: Templating
parent: cheat-sheet
grand_parent: Guides
---

# Templating

Template in OpenAF uses the [HandleBars](https://handlebarsjs.com/guide/) javascript library which has a very good documentation. Nevertheless here is a collection of tricks that might be useful:

| Name | Expression | Description |
|------|------------|-------------|
| Escaping content | ````{% raw %}{{{text}}}{% endraw %}```` | Without three braces HandleBars will replace '&' with the HTML escape sequence as well as other characters. |
| Escaping expression | ````{% raw %}\{{something}}{% endraw %}```` | To escape a HandleBars expression just add ´\´ before the first character | 
| Accessing an element of an array | ````{% raw %}{{lst.[0]}}{% endraw %}```` | Accessing a position of a provided array. |
| Accessing an object property with symbols | ````{% raw %}{{obj.[something else].[item-name]}}{% endraw %}```` | To access any object property with a space or other symbols use '[]'. |
| Accessing a property from a different level | ````{% raw %}{{#each list}}Name = {{name}}, Company = {{../company}}\n{{/each}}{% endraw %}```` | Consider the following map = ````{ company: "myC", list: [ { name: "john", name: "anne" } ]}````. You can access "parent" levels as if they were a folder hierarchy (e.g. concatenating "../" as needed) |
| Using helpers within helpers | ````{% raw %}{{$f '%20s' ($env 'LANG')}}{% endraw %}```` | The first helper '$env' will run retrieving the current value for the environment variable 'LANG' and the result is used by the second helper, '$f', that will format the resulting string in a right-justified line with 20 characters long ('%20s') |