---
layout: default
title: oafp to manipulate text
parent: oafp
grand_parent: Guides
---

# oafp to manipulate text

### Get a json with the lyrics of a song

```bash
curl -s https://api.lyrics.ovh/v1/Coldplay/Viva%20La%20Vida | oafp path="substring(lyrics,index_of(lyrics, '\n'),length(lyrics))"
```

Result:
```
I used to rule the world
[...]
Oooooh Oooooh Oooooh
```
