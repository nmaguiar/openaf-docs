---
layout: default
title: oafp with JSON schemas
parent: oafp
grand_parent: Guides
---

# oafp with JSON schemas

List of examples of use of oafp with JSON schemas:

### Get a list of schemas

```bash
oafp cmd="curl https://raw.githubusercontent.com/SchemaStore/schemastore/master/src/api/json/catalog.json" path="schemas[].{name:name,description:description,files:to_string(fileMatch)}" out=ctable
```

Result:

```
                             name                              │                                                description                                                 │                                         files                                          
───────────────────────────────────────────────────────────────┼────────────────────────────────────────────────────────────────────────────────────────────────────────────┼────────────────────────────────────────────────────────────────────────────────────────
1Password SSH Agent Config                                     │Configuration file for the 1Password SSH agent                                                              │["**/1password/ssh/agent.toml"]                                                         
Application Accelerator                                        │Application Accelerator for VMware Tanzu                                                                    │["accelerator.yaml"]                                                                    
AnyWork Automation Configuration                               │AnyWork Automation Configuration used to configure automation scripts on AnyWork                            │[".awc.yaml",".awc.yml",".awc.json",".awc.jsonc",".awc"]                                
[...]
```