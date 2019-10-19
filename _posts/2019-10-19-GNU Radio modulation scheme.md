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

# Foreword

In GNU Radio, we can build and run the flow graphs. But the there is no specific module of the QAM and PSK.
Through the 'Variable' module and codes, we can set the order of the modulation schemes.

# Code

## PSK

### BPSK

```
digital.constellation_bpsk()
```
Digital constellation for BPSK .

### QPSK

```
digital.constellation_qpsk()
```
Digital constellation for QPSK.

```
digital.constellation_dqpsk() 
```
Digital constellation for DQPSK.

```
digital.qpsk.qpsk_constellation(mod_code='gray')
```
Creates a QPSK constellation.

### 8PSK

```
digital.constellation_8psk()
```
Digital constellation for 8PSK.

### PSK (any order)

```
digital.psk.psk_constellation(m=4, mod_code='gray', differential=True)
```
Creates a PSK constellation object.

## QAM

```
digital.qam.qam_constellation(constellation_points=16, differential=True, mod_code='none', large_ampls_to_corners=False)
```
Creates a QAM constellation object.

If large_ampls_to_corners=True then sectors that are probably occupied due to a phase offset, are not mapped to the closest constellation point. Rather we take into account the fact that a phase offset is probably the problem and map them to the closest corner point. It’s a bit hackish but it seems to improve frequency locking.

## Other important codes

###  Euclidian distance for any constellation.

```
digital.constellation_calcdist(pmt_vector_cfloat constell, std::vector< int, std::allocator< int > > pre_diff_code, unsigned int rotational_symmetry, unsigned int dimensionality)
```
Calculate Euclidian distance for any constellation.
Constellation which calculates the distance to each point in the constellation for decision making. Inefficient for large constellations.
Constructor Specific Documentation:
Make a general constellation object that calculates the Euclidean distance for hard decisions.

|Parameters|
|   ----   |
|          |

