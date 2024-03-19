---
layout: default
title: oafp
parent: Concepts
grand_parent: OpenAF docs
---
# oafp

OpenAF processor (oafp) is a command-line utility, distributed with OpenAF (since version 20240318), that takes an input, usually a data structure such as json, and transforms it to an equivalent data structure in another format or visualization. The output data can be filtered through JMESPath, SQL or OpenAF's nLinq and provided transformers can also be applied to it.

The tool comes with it's own built-in documentation that can be accessed by executing:

```bash
oafp -h
```

You can check several example of usage in the [oafp guides](../guides/oafp/)