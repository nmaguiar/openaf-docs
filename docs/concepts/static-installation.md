---
layout: default
title: Static installation
parent: Concepts
grand_parent: OpenAF docs
---

# Static installation

For a quick simple use of OpenAF it's possible to download a single executable file ready to run (currently only in Linux, MacOS and Windows WSL). To download there is two options:

With 'curl', 'bash', 'tar' and 'gzip' available:

```bash
curl https://ojob.io/getStatic.sh | sh
```

With just 'bash', 'tar' and 'gzip available:

```bash
/bin/bash -c "exec 3<>/dev/tcp/ojob.io/80 && echo -e \"GET /getStatic.sh HTTP/1.1\nHost: ojob.io\nUser-Agent: curl\nConnection: close\n\n\" >&3 && cat <&3" | sed '1,/connection: close/d' | tail -n +2 > getStatic.sh && sh getStatic.sh && rm getStatic.sh
```

Afterwards, on the current folder, the *oaf*, *oafc*, *ojob* and *opack* will be available and ready to run.

You can check the available release per Linux and Mac OS release in: [GitHub OpenAF sh](https://github.com/OpenAF/sh/blob/main/README.md)

## How to download a specific OpenAF distribution

To specify an OpenAF distribution different from the *stable* you will just need to use the **DIST** environment variable:

```bash
curl https://ojob.io/getStatic.sh | DIST=nightly sh
```

With just 'bash', 'tar' and 'gzip available:

```bash
/bin/bash -c "exec 3<>/dev/tcp/ojob.io/80 && echo -e \"GET /getStatic.sh HTTP/1.1\nHost: ojob.io\nUser-Agent: curl\nConnection: close\n\n\" >&3 && cat <&3" | sed '1,/connection: close/d' | tail -n +2 > getStatic.sh && DIST=nightly sh getStatic.sh && rm getStatic.sh
```

## How it works

After download of the single executable file, it will uncompress to the temporary folder a Java JRE and the OpenAF runtime. Once all files are available on the temporary folder it will create symlinks for *oaf*, *oafc*, *ojob* and *opack* on the current folder. Any subsequent calls using the symlinks will use the same runtime.

To delete the temporary folder, for any reason, search on the temporary folder (e.g. /tmp) for a *_oaf* prefixed folder.

For more details check the GitHub repository https://github.com/openaf/sh.

## List of direct links

To download directly for a specific distribution, OS and/or architecture choose one of the following available builds:

| OpenAF distribution | OS | Architecture | Link |
|---------------------|----|--------------|------|
| stable | Linux | x86_64 | [openaf.io/oaf-linux-x86_64](https://openaf.io/oaf-linux-x86_64) |
| stable | Linux | aarch64 | [openaf.io/oaf-linux-aarch64](https://openaf.io/oaf-linux-aarch64) |
| stable | Alpine Linux | x86_64 | [openaf.io/oaf-alpine-x86_64](https://openaf.io/oaf-alpine-x86_64) |
| stable | Alpine Linux | aarch64 | [openaf.io/oaf-alpine-aarch64](https://openaf.io/oaf-alpine-aarch64) |
| stable | Mac | x64_64 | [openaf.io/oaf-mac-x86_64](https://openaf.io/oaf-mac-x86_64) |
| stable | Mac | aarch64 | [openaf.io/oaf-mac-aarch64](https://openaf.io/oaf-mac-aarch64) |
| nightly | Linux | x86_64 | [openaf.io/nightly/oaf-linux-x86_64](https://openaf.io/nightly/oaf-linux-x86_64) |
| nightly | Linux | aarch64 | [openaf.io/nightly/oaf-linux-aarch64](https://openaf.io/nightly/oaf-linux-aarch64) |
| nightly | Alpine Linux | x86_64 | [openaf.io/nightly/oaf-alpine-x86_64](https://openaf.io/nightly/oaf-alpine-x86_64) |
| nightly | Alpine Linux | aarch64 | [openaf.io/nightly/oaf-alpine-aarch64](https://openaf.io/nightly/oaf-alpine-aarch64) |
| nightly | Mac | x64_64 | [openaf.io/nightly/oaf-mac-x86_64](https://openaf.io/nightly/oaf-mac-x86_64) |
| nightly | Mac | aarch64 | [openaf.io/nightly/oaf-mac-aarch64](https://openaf.io/nightly/oaf-mac-aarch64) |
| t8 | Linux | x86_64 | [openaf.io/t8/oaf-linux-x86_64](https://openaf.io/t8/oaf-linux-x86_64) |
| t8 | Linux | aarch64 | [openaf.io/t8/oaf-linux-aarch64](https://openaf.io/t8/oaf-linux-aarch64) |
| t8 | Alpine Linux | x86_64 | [openaf.io/t8/oaf-alpine-x86_64](https://openaf.io/t8/oaf-alpine-x86_64) |
| t8 | Alpine Linux | aarch64 | [openaf.io/t8/oaf-alpine-aarch64](https://openaf.io/t8/oaf-alpine-aarch64) |
| t8 | Mac | x64_64 | [openaf.io/t8/oaf-mac-x86_64](https://openaf.io/t8/oaf-mac-x86_64) |
| t8 | Mac | aarch64 | [openaf.io/t8/oaf-mac-aarch64](https://openaf.io/t8/oaf-mac-aarch64) |