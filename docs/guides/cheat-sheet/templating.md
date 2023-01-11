---
layout: default
title: Templating
parent: cheat-sheet
grand_parent: Guides
---

# Templating

Template in OpenAF uses the [HandleBars](https://handlebarsjs.com/guide/) javascript library which has very good documentation. Nevertheless here is a collection of tricks that might be useful and most used helpers.

| Name | Expression | Description |
|------|------------|-------------|
| Escaping content | ````{% raw %}{{{text}}}{% endraw %}```` | Without three braces HandleBars will replace '&' with the HTML escape sequence as well as other characters. |
| Escaping expression | ````{% raw %}\{{something}}{% endraw %}```` | To escape a HandleBars expression just add ´\´ before the first character | 
| Accessing an element of an array | ````{% raw %}{{lst.[0]}}{% endraw %}```` | Accessing a position of a provided array. |
| Accessing an object property with symbols | ````{% raw %}{{obj.[something else].[item-name]}}{% endraw %}```` | To access any object property with a space or other symbols use '[]'. |
| Accessing a property from a different level | ````{% raw %}{{#each list}}Name = {{name}}, Company = {{../company}}\n{{/each}}{% endraw %}```` | Consider the following map = ````{ company: "myC", list: [ { name: "john", name: "anne" } ]}````. You can access "parent" levels as if they were a folder hierarchy (e.g. concatenating "../" as needed) |
| Using helpers within helpers | ````{% raw %}{{$f '%20s' ($env 'LANG')}}{% endraw %}```` | The first helper '$env' will run retrieving the current value for the environment variable 'LANG' and the result is used by the second helper, '$f', that will format the resulting string in a right-justified line with 20 characters long ('%20s') |

## OpenAF helpers

| Helper | Example | Description |
|--------|---------|-------------|
| $$     | ````{% raw %}{{$$ aProperty aDefaultValue}}{% endraw %}```` | Outputs the value of aProperty or, if not defined, returns the defaultValue. |
| $debug | ````{% raw %}{{$debug __flags}}{% endraw %}```` | The same as stringifyInLine for the provided argument. |
| $stringify | ````{% raw %}{{{$stringify __flags}}}{% endraw %}```` | Given a map will output the stringify version of it. |
| $stringifyInLine | ````{% raw %}{{{$stringifyInLine __flags}}}{% endraw %}```` | Given a map will output the stringify version without new-lines. |
| $toYAML | ````{% raw %}{{$toYAML __flags}}{% endraw %}```` | Given a map will output the YAML version of it. |
| $env | ````{% raw %}{{$env 'PATH'}}{% endraw %}```` | Given an environment variable will output the corresponding value. |
| $escape | ````{% raw %}{{{$escape aString}}}{% endraw %}```` | Given a string value will return the escaped version of it. |
| $f | ````{% raw %}[{{$f '%20s' aString}}]{% endraw %}```` | Performs a [$f operation](/docs/guides/cheat-sheet/string-formatter.md) with the provider parameter for the provided aString. |
| $ft | ````{% raw %}[{{$ft '%20s' aString}}]{% endraw %}```` | Performs a [$ft operation](/docs/guides/cheat-sheet/string-formatter.md) with the provider parameter for the provided aString. |
| $path | ````{% raw %}{{$path '@' anArray}}{% endraw %}```` | Executes the function [$path](/docs/concepts/OpenAF-path.md) over the provided element. |
| $toSLON | ````{% raw %}{{$toSLON aMap}}{% endraw %}```` | Given a map will output the SLON version of it. |
| $get | ````{% raw %}{{$get 'res'}}{% endraw %}```` | Performs the equivalent operation to OpenAF's $get. |
| $getObj | ````{% raw %}{{$getObj 'res' 'elements'}}{% endraw %}```` | Performs the equivalent operation to OpenAF's $get and applies the function $path using the second parameter. |
| $dateDiff | ````{% raw %}{{$dateDiff aDate 'days'}}{% endraw %}```` | Given aDate will output the time difference (using the third optional argument (seconds (default), minutes, hours, days, months, weeks or years)) |

## Adding a helper

Example of adding a simple template helper:

````javascript
ow.template.addHelper("publicip", (aIP, aElement) => $$(ow.loadNet().getPublicIP(aIP)).get(aElement) )

templify("{% raw %}{{ip}} is in {{publicip ip 'country'}}{% endraw %}", { ip: "1.1.1.1" })
// 1.1.1.1 is in Australia
````