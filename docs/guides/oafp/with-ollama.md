---
layout: default
title: oafp with Ollama
parent: oafp
grand_parent: Guides
---

# oafp with Ollama

List of examples of use of oafp using Ollama API to access LLM models:

### Setting up access to Ollama and ask for data

```bash
export OAFP_MODEL="(type: ollama, model: 'mistral', url: 'https://models.local', timeout: 900000)"
echo "Output a JSON array with 15 cities where each entry has the 'city' name, the estimated population and the corresponding 'country'" | oafp input=llm output=json > data.json
oafp data.json output=ctable sql="select * order by population desc"
```

Result:
```
   city    │population│ country  
───────────┼──────────┼──────────
Shanghai   │270584000 │China     
Tokyo      │37436958  │Japan     
Delhi      │30290936  │India     
São Paulo  │21935296  │Brazil    
Beijing    │21516000  │China     
Mexico City│21402981  │Mexico    
Mumbai     │20712874  │India     
Cairo      │20636449  │Egypt     
Osaka      │19365701  │Japan     
Dhaka      │18568373  │Bangladesh
[#10 rows]
```