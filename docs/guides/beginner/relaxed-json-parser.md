---
layout: default
title: "Beginner: Relaxed JSON parser"
parent: Guides
grand_parent: OpenAF docs
---

# Relaxed JSON parser

In OpenAF, when using the _jsonParser_ function, the parsing sticks to the strict JSON definition.

For example the following behaves as expected:

````javascript
> jsonParser("{ \"a\": 1 }");
{
   "a": 1
}
> JSON.parse("{ \"a\": 1 }");
{
   "a": 1
}
````

But using a more "relaxed" JSON definition, the same functions will fail:

````javascript
> jsonParser("{ a: 1 }");
{ a: 1 }
> JSON.parse("{ a: 1 }");
-- SyntaxError: Unexpected token in object literal
````

The _jsonParser_ function will return the text string representation as it's unable to parse the JSON string. The native _JSON.parse_ will actually throw an execption.

## Using GSON

OpenAF includes the [GSON library](https://github.com/google/gson) which can parse more "relaxed" JSON definitions. Since OpenAF version 20200108, the OpenAF _jsonParser_ function can also use the GSON library. There is a new second boolean argument that if _true_ alternates to GSON for parsing the string provided on the first argument:

````javascript
> jsonParse("{ a: 1 }", true);
{
   "a": 1
}
````