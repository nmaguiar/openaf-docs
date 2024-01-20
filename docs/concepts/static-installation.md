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