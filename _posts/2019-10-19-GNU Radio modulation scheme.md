---
layout: post
title: "GNU Radio modulation scheme"
subtitle: 'Code'
author: "WT"
header-img: "img/post-bg-2015.jpg"
catalog: true

tags:
  - GNU Radio
---

## Foreword

In GNU Radio, we can build and run the flow graphs. But the there is no specific module of the QAM and PSK.
Through the 'Variable' module and codes, we can set the order of the modulation schemes.

## Code

### PSK

#### BPSK

```
digital.constellation_bpsk()
```
Digital constellation for BPSK .
