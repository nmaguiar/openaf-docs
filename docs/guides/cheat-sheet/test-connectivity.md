---
layout: default
title: Test connectivity
parent: cheat-sheet
grand_parent: Guides
---

# Test connectivity cheat-sheet

You can do any of these tests on an openaf-console (e.g. ./oafc or ./openaf-console)

| Test | Command | Results |
|------|---------|---------|
| **Test port** | ow.loadNet().testPort("some.host", 12345) | if _false_ the host couldn't be reached. _true_  |
| **Test port with timeout** | ow.loadNet().testPort("some.host", 12345, 15000) | if _false_ the host couldn't be reached. _true_ otherwise |
| **Test host (ping)** | ow.loadNet().testHost("127.0.0.1") | { time: 0, reachable: true } |
| **Test port latency (socket)** | ow.loadNet().testPortLatency("1.1.1.1", 443) | 3 |
| **Test URL latency** | ow.loadNet().testURLLatency("https://google.com") | 118 |
| **Get IP address from hostname** | ow.loadNet().getHost2IP("one.one.one.one") | 1.1.1.1 |
| **Get hostname from IP address** | ow.loadNet().getIP2Host("1.1.1.1") | one.one.one.one |

