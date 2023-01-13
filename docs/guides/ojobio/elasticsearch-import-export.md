---
layout: default
title: ElasticSearch Import/Export
parent: oJobIO
grand_parent: Guides
---

# ElasticSearch Import/Export

There are several ways to import/export indexes from ElasticSearch but over the years some OpenAF scripts were made for the same that were captured in two ojob.io ojobs:

* ojob.io/es/export
* ojob.io/es/import

As the name implies one should be used to export data from ElasticSearch and the other to import data. The data is stored in ndjson to make it easier to "transport it" between different ElasticSearch environments and versions (with some limitations depending on the version).

> To move data within the same ElasticSearch cluster you should use other available features from ElasticSearch like reindex.

## Exporting data

The _ojob.io/es/export_ ojob currently has the following possible options (you can check them also be executing ````ojob ojob.io/es/export -jobhelp````):

| Option | Mandatory | Description |
|--------|-----------|-------------|
| url | yes | The ElasticSearch/OpenSearch instance URL |
| output | no | The output folder where the ndjson files will be created |
| user | no | The user credential, if necessary, to access the cluster |
| pass | no | The password credential, if necessary, to access the cluster |
| idx | no | A regular expression filter for the indices to export (otherwise all will be exported) |
| force | no | If force=true it will not check if there is a previous ndjson file for each index |
| filter | no | Comma separated pairs of field value filters (for example: "field1:abc,field2:xyz") |
| notfilter | no |Comma separated pairs of field value not filters (for example: "field1:abc,field2:xyz") |
| from | no | Date greater-than or equal (for example: 2022-03-04T01:02:03) |
| to | no | Date lower-than or equal (for example: 2022-03-02T02:03:04) |

Everytime that it runs (without the force option) _ojob.io/es/export_ will check if there is previous data for a specific index. In scenarios that, for example, you have a new daily index and you run _ojob.io/es/export_ also daily it will not try to export again data from previous indexes found on the same folder.

> Note: output files will be automatically gziped to save space.

### Examples:

Export data to folder 'out' from all indices that start with 'my-data':

````
ojob ojob.io/es/export url=https://my.elastic.search.cluster:9200 output=out idx=my-data*
````

Export data to folder 'out' from all indices that start with 'my-data' where the corresponding documents have a field 'type' with the value 'audit':

````
ojob ojob.io/es/export url=https://my.elastic.search.cluster:9200 output=out idx=my-data* filter=type:audit
````

Export data to folder 'out' from all indices that start with 'my-data' where the corresponding documents have a field '@timestamp' between 1st of October 2022 and the end of the 2nd of October 2022:

````
ojob ojob.io/es/export url=https://my.elastic.search.cluster:9200 output=out idx=my-data* from=2022-10-01T00:00:00 to=2022-10-02T23:59:59
````

## Importing data

After exporting data you might need to import it. To do this you can use ojob.io/es/import ojob:

````
ojob ojob.io/es/import url=http://my.elastic2.search.cluster:9200 file=out/my-data-22.ndjson.gz index=their-data-22
````

The _ojob.io/es/import_ ojob currently has the following possible options (you can check them also be executing ````ojob ojob.io/es/import -jobhelp````)

| Option | Mandatory | Description |
|--------|-----------|-------------|
| url | yes | The ElasticSearch/OpenSearch instance URL |
| user | no | The user credential, if necessary, to access the cluster |
| pass | no | The password credential, if necessary, to access the cluster |
| index | yes | The index to which data will be imported to |
| file | yes | The ndjson (.gz or not) with the data to import (usually result of ojob.io/es/export) |

## Using them in an air gap environment

To use these in an air gap enviroment (without Internet) you will need:

* the latest OpenAF version
* the ojob.io/es/export yaml file (````ojob ojob.io/get job=ojob.io/es/export airgap=true````)
* the ojob.io/es/import yaml file (````ojob ojob.io/get job=ojob.io/es/import airgap=true````)