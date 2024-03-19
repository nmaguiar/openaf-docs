---
layout: default
title: oafp with ElasticSearch
parent: oafp
grand_parent: Guides
---

# oafp with ElasticSearch

List of examples of use of oafp with ElasticSearch:

## Health

### Get an overview of the cluster health
```bash
curl -s "http://elastic.search:9200/_cat/health?format=json" | oafp out=ctable
```

### Get indices overview
```bash
curl -s "http://elastic.search:9200/_cat/indices?format=json&bytes=b" | oafp sql="select * order by index" out=ctable
```

### Get cluster nodes overview
```bash
curl -s "http://elastic.search:9200/_cat/nodes?format=json" | oafp sql="select * order by ip" out=ctable
```

### Get per host data allocation
```bash
curl -s "http://elastic.search:9200/_cat/allocation?format=json&bytes=b" | oafp sql="select * order by host" out=ctable
```

### Get current cluster settings flat
```bash
curl -s "http://elastic.search:9200/_cluster/settings?include_defaults=true&flat_settings=true" | oafp out=ctree
```

### Get current cluster settings non-flatted
```bash
curl -s "http://elastic.search:9200/_cluster/settings?include_defaults=true" | oafp out=ctree
```

### Get stats per node
```bash
curl -s "http://127.0.0.1:9200/_nodes/stats/indices/search" | oafp out=ctree
```

## Index related

### Get the settings for a specific index
```bash
curl -s "http://127.0.0.1:9200/kibana_sample_data_flights/_settings" | oafp out=ctree
```

### Get count per index
```bash
curl -s "http://127.0.0.1:9200/kibana_sample_data_flights/_count" | oafp
```