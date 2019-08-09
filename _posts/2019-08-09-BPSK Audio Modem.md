---
layout: post
title: "BPSK Audio Modem"
subtitle: 'GNU Radio study.'
author: "WT"
header-img: "img/post-bg-2015.jpg"
catalog: true

tags:
  - GNU Radio
---

## Foreword

Recently, i found an interesting GNU Radio flow graph and post that flow graph on my blog.  [This](http://aaronscher.com/GNU_Radio_Companion_Collection/Audio_modem.html) is the source of this flow graph. It was made by Dr. Aaron Scher. You can also download this file [here](http://aaronscher.com/GNU_Radio_Companion_Collection/GNU_Radio_Companion_Collection_docs/audio_modem1.grc).

## Flow graph

BPSK Audio Modem Flow Graph (both transmitter and receiver are in the same flow graph).

![BPSK Audio Modem Flow Graph](http://aaronscher.com/GNU_Radio_Companion_Collection/GNU_Radio_Companion_Collection_docs/audio_modem_schematic.png)

## Operation step

1. Set up a simple client to listen to port 9989. I do this with my mac by opening up a new Terminal window and using the nc (or ncat) utility:

```
nc -l 9989
```

2. Execute the flow graph in GNU Radio Companion.

3. (Quickly) Set up a simple server to connect to 127.0.0.1 port 1234 I do this with my mac by opening up another Terminal window and using the nc utility:

```
nc 127.0.0.1 1234
```

4. If everything works (sometimes you need to try the above methods a few times before it works - not sure why), you should be able to send text message from the server terminal to the client terminal by sound. Here is a demo:


<iframe width="420" height="315" src="https://www.youtube.com/embed/LYNg9oNtE60" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
