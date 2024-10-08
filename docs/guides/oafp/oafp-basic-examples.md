---
layout: default
title: oafp basic examples
parent: oafp
grand_parent: Guides
---

# oafp basic examples

## Simple format conversions

| Description | Example |
|-------------|---------|
| Convert JSON to YAML | ```oafp a-json-file.json out=yaml``` |
| Convert YAML to JSON | ```oafp a-yaml-file.yaml out=json``` |
| Convert YAML to pretty JSON | ```oafp a-yaml-file.yaml out=pjson``` |
| Convert a NDJSON to a single JSON | ```oafp a-ndjson.ndjson in=ndjson ndjsonjoin=true out=json``` |
| Convert a JSON array to a multiple document YAML | ```oafp a-json-array.json out=mdyaml``` |
