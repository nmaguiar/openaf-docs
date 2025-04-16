---
layout: default
title: oJob S3 browse functionality
parent: oJob
grand_parent: Guides
---

# S3 browse functionality

Starting on oJob-common oPack version 20250415 it's possible to use the common browse functionality to list the contents of a directory or a file. This functionality is generic enough to be applied to different scenarios like: browsing a local filesystem; browsing an object storage bucket; browsing an AWS ECR; browsing a Maven repository; etc.

> To install oJob-common either refer to it on an oJob (ojob > opacks > oJob-common) or install it directly by executing ``opack install ojob-common````

This S3 implementation also requires to install the 'S3' oPack:

```bash
opack install S3
```

Example:

```yaml
ojob:
  daemon: true   # we want to run it as a daemon 
  opacks: 
  - oJob-common  # we want to install/include oJob-common
  - S3           # we want to install/include S3

include:
- oJobS3.yaml  # we want to add the oJob S3 browse functionality

todo:
- (S3Browse): 8888
  ((uri   )): /browse
  ((bucket)): my-bucket
```

> If the `url`, `accessKey`, `secretKey` and `region` are not provided, the S3 oPack will use the default credentials from the environment. This is useful when running on AWS or other cloud providers that support IAM roles.

Other arguments available:

| Argument | Type | Description |
| -------- | ---- | ----------- |
| `url` | String | The URL of the S3 endpoint. |
| `accessKey` | String | The access key to use to connect to the S3 endpoint. |
| `secretKey` | String | The secret key to use to connect to the S3 endpoint. |
| `region` | String | The region to use to connect to the S3 endpoint. |
| `path` | String | The path to the S3 bucket. |
| `browse` | Boolean | If true, the S3 bucket will be browsed. |
| `default` | String | The default path to use when browsing the S3 bucket. |
| `logo` | String | The logo to use when browsing the S3 bucket. |
| `sortTab` | String | The tab to use when sorting the S3 bucket. |
| `options` | Map | The options to use when browsing the S3 bucket. |
| `cache` | Number | The cache time in ms for the S3 object lists |
| `restrict` | Array | A regular expression (or list) that if matched won't be listed or accessible. |
| `incURI` | Boolean | If true, the URI will be included in the S3 object list. |

