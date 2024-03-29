---
layout: default
title: oafp with ElasticSearch
parent: oafp
grand_parent: Guides
---

# oafp with ElasticSearch

List of examples of use of oafp with ElasticSearch.

Set environment variables to use with the examples:

```bash
export ES_URL=http://elastic.search:9200
export ES_EXTRA="--insecure"
```

## Health

### Get an overview of the cluster health
```bash
curl -s "$ES_URL/_cat/health?format=json" $ES_EXTRA | oafp out=ctable
```

### Get indices overview
```bash
curl -s "$ES_URL/_cat/indices?format=json&bytes=b" $ES_EXTRA | oafp sql="select * order by index" out=ctable
```

### Get cluster nodes overview
```bash
curl -s "$ES_URL/_cat/nodes?format=json" $ES_EXTRA | oafp sql="select * order by ip" out=ctable
```

### Get per host data allocation
```bash
curl -s "$ES_URL/_cat/allocation?format=json&bytes=b" $ES_EXTRA | oafp sql="select * order by host" out=ctable
```

### Get current cluster settings flat
```bash
curl -s "$ES_URL/_cluster/settings?include_defaults=true&flat_settings=true" $ES_EXTRA | oafp out=ctree
```

### Get current cluster settings non-flatted
```bash
curl -s "$ES_URL/_cluster/settings?include_defaults=true" $ES_EXTRA | oafp out=ctree
```

### Get stats per node
```bash
curl -s "$ES_URL/_nodes/stats/indices/search" $ES_EXTRA | oafp out=ctree
```

## Index related

### Get the settings for a specific index
```bash
curl -s "$ES_URL/kibana_sample_data_flights/_settings" $ES_EXTRA | oafp out=ctree
```

### Get count per index
```bash
curl -s "$ES_URL/kibana_sample_data_flights/_count" $ES_EXTRA | oafp
```