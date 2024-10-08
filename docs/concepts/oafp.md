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

or you can check it here:

| Document |
|----------|
| [oafp usage documentation](../guides/oafp/oafp-usage) |
| [oafp filters documentation](../guides/oafp/oafp-filters) |
| [oafp templates documentation](../guides/oafp/oafp-template) |
| [oafp basic examples](../guides/oafp/oafp-basic-examples) |

If you have internet access you can also access a library of examples:

```bash
oafp -examples
oafp examples=unix::
oafp examples=kubernetes::kubectl
oafp examples=env
```

You can also check the library of examples in [oafp examples](../guides/oafp/oafp-examples.md).

---

You can check more examples of usage in the [oafp guides](../guides/oafp/).

---

## Concepts

![oafp concepts](oafp-diagram.png)
