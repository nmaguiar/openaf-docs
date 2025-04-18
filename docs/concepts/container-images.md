---
layout: default
title: OpenAF container images
parent: Concepts
grand_parent: OpenAF docs
---

# OpenAF container images

OpenAF is a framework that allows you to run your scripts or oJobs in a containerized environment. This means that you can package your scripts and their dependencies into a single container image, which can be easily shared and deployed across different environments.

This is particularly useful for deploying OpenAF scripts in production environments, where you want to ensure that your scripts run consistently and reliably.

## Base images avaiable

OpenAF provides a set of base images that you can use to build your own container images or to use directly. These base images are designed to be lightweight and efficient, while still providing all the necessary dependencies for running OpenAF scripts.

| Base image | Description |
|------------|-------------|
| `openaf/oaf:<tag>` | OpenAF base image |
| `openaf/ojobrt:<tag>` | OpenAF oJob runtime image suitable for running oJobs |
| `openaf/ojob:<tag>` | Legacy similar to OpenAF base image to run oJobs (use ojobrt instead) |
| `openaf/ojobc:<tag>` | Legacy similar to openaf/ojob with the oJob-common oPack installed (use ojobrt instead)  |
| `openaf/oafc:<tag>` | Legacy similar to OpenAF base image but centered on the OpenAF console |
| `openaf/pyoaf:<tag>` | Similar to OpenAF base image + latest Python 3.x |

There are several combinations of tags available for theses images:

| Tag | Description | Based on | OpenAF distribution | JRE version | Update frequency |
|-----|-------------|----------|---------------------|-------------|------------------|
| `latest` | The latest stable version of the image. | Alpine | stable | 21 | Whenever a new stable version is released or Critical/High vulnerabilities are fixed |
| `nightly`| The latest nightly version of the image | Alpine | nightly | 21 | Daily |
| `t8` | The latest development version of the image | Alpine | t8 | 21 | Daily |
| `edge` | The latest edge version of the image | Alpine Edge | t8/nightly | 24 | Daily |
| `yyyyMMdd` | The version of the image corresponding to the date of the release | Alpine | stable | 21 | Fixed. No updates. |
| `ubi` | The latest stable version of the image. | UBI | stable | 21 | Whenever a new stable version is released or Critical/High vulnerabilities are fixed |
| `ubi-nightly` | The latest nightly version of the image | UBI | nightly | 21 | Daily |
| `ubi-t8` | The latest development version of the image | UBI | t8 | 21 | Daily |
| `ubi-yyyyMMdd` | The version of the image corresponding to the date of the release | UBI | stable | 21 | Fixed. No updates. |
| `deb` | The latest stable version of the image. | Debian | stable | 21 | Whenever a new stable version is released or Critical/High vulnerabilities are fixed |
| `deb-nightly` | The latest nightly version of the image | Debian | nightly | 21 | Daily |
| `deb-t8` | The latest development version of the image | Debian | t8 | 21 | Daily |
| `deb-yyyyMMdd` | The version of the image corresponding to the date of the release | Debian | stable | 21 | Fixed. No updates. |

> openaf/pyoaf is currently limited to 'latest', 'edge', 'nightly' and 't8'

The base images are available on [Docker Hub](https://hub.docker.com/r/openaf) and can be pulled using the following command:

```bash
docker pull openaf/oaf:latest
```

## Base images options

### openaf/oaf options

OpenAF base image options allow you to customize the behavior of the container. You can specify environment variables, mount volumes, and set resource limits.

| Environment variable | Description | Example |
|----------------------|-------------|---------|
| OPENAF | A path to a script to run in the container filesystem | `-e OPENAF=/scripts/my-script.js` |
| OJOB | A url or path to a oJob to run in the container filesystem | `-e OJOB=ojob.io/oaf/envs` |
| OPACKS | A comma-separated list of oPacks to install in the container | `-e OPACKS=Mongo,oJob-common` |
| OPACKS_DB | A comma-separated list of additional oPack databases to consider | `-e OPACKS_DB=http://my.opack.server/opack.db` |
| OPACKS_DIR | A container based folder with .opack files or folders to be installed during the first execution. | `-e OPACKS_DIR=/opacks` |
| OAFP | If defined will run oafp command instead of oaf | `-e OAFP=yes` |

#### Examples:

**Running 'oaf' options:**

```bash
docker run --rm -ti --pull=always openaf/oaf -c 'print("Hello World!")'
```

**Running 'ojob' options:**

```bash
docker run --rm -ti --pull=always -v $(pwd):/browse -p 8080:8080 -e OJOB=ojob.io/httpServers/EasyHTTPd openaf/oaf port=8080 path=/browse
```

> Open the browser and go to [http://localhost:8080](http://localhost:8080) to see the result.

**Running 'oafp':**

```bash
docker run --rm -ti --pull=always -e OAFP=yes openaf/oaf -v
```

**Running 'opack' options:**

```bash
docker run --rm -ti --pull=always -e OPACKS=AsciiMo openaf/oaf -c 'load("asciimo.js"); print((new AsciiMo()).write("test", "thin"))'
```

### openaf/ojobrt options

The OpenAF oJob runtime image is designed to run oJobs in a containerized environment. It provides all the necessary dependencies for running oJobs, including the OpenAF runtime and basic required libraries (e.g. S3, oJob-common)

| Environment variable | Description | Example |
|----------------------|-------------|---------|
| OJOB_CONFIG | A path to a oJob configuration file (a single YAML file or a ZIP file) to run within the container filesystem OR within a configured S3 bucket OR from a web server | `-e OJOB_CONFIG=ojobs/jobABC-20250315.zip` |
| OJOB_METHOD | The OJOB_CONFIG retrieval method. It can be 'local' (default), 's3' or 'http' | `-e OJOB_METHOD=s3` |
| OJOB_JSONLOG | Boolean string value to enable JSON logging | `-e OJOB_JSONLOG=true` |

> OJOB_JSONLOG doesn't set how logs from the corresponding oJob are output. This should be defined on the oJob itself.

#### S3 method

For the S3 method you might also need to set the following environment variables:

| Environment variable | Description | Example |
|----------------------|-------------|---------|
| url | The S3 bucket URL | `-e url=http://minio:9000` |
| bucket | The S3 bucket name | `-e bucket=mybucket` |
| accessKey | The S3 access key | `-e accessKey=myaccesskey` |
| secret | The S3 secret key | `-e secret=mysecretkey` |

> The accessKey, secret and url are not mandatory if another AWS authentication method is used (e.g. IAM roles, etc.). In this case, the container will use the default AWS credentials provider chain to authenticate with S3.

Example:

```bash
docker run --rm -ti -e OJOB_METHOD=s3 -e OJOB_CONFIG=test.zip -e bucket=test -e url=http://minio:9000 -e accessKey=minioadmin -e secret=minioadmin --net test openaf/ojobrt
```

These values can also be provided using [OpenAF SBuckets](sBuckets.md):

By default, the secrets.yaml is expected to be in /secrets/secrets.yaml. If no secBucket environment variable is provided it will default for searching the main key "ojob". If no secKey environment variable is provided it will default for searching the key "s3_config" in the OpenAF secBucket.

```bash
docker run --rm -ti -e OJOB_METHOD=s3 -e OJOB_CONFIG=test.zip -v "$(pwd)"/secrets:/secrets --net test openaf/ojobrt
```

Example using a different secBucket and/or secKey:

```bash
docker run --rm -ti -e OJOB_METHOD=s3 -e OJOB_CONFIG=test/test.zip -e secBucket=mySBucket -e secKey=myS3 -v "$(pwd)"/secrets:/secrets --net test openaf/ojobrt 
```

> To use a different secrets file the environment variable secFile can be provided

#### HTTP method

For the HTTP method the OJOB_CONFIG environment variable can be a URL to a ZIP file or a YAML file. The container will download the file and run the oJob.

Example:

```bash
docker run --rm -ti -v "$(pwd)"/examples:/test -e OJOB_METHOD=http -e OJOB_CONFIG=http://minio:9000/test/test.zip -v "$(pwd)"/secrets:/secrets --net test openaf/ojobrt
```

> It's possible also to provide a "login" and a "pass" enviroment variable for HTTP(s) basic authentication.

#### oJob ZIP package

For some retrieval methods (OJOB_METHOD) it's possible to point to a ZIP file instead of a single file. The ZIP file can have all the necessary files to run the corresponding oJob but the main execution requires a "main.yaml" file. Optionally a secrets.yaml can be provided for testing proposed.

The ZIP file can have the following structure:

| Filepath | Description |
|----------|-------------|
| main.yaml | The main execution oJob |
| secrets.yaml | An optional secrets.yaml file (OpenAF $sec/SBuckets based) |
