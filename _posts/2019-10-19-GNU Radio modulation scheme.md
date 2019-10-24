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

|Parameters|Note|
|  ----    | ----  |
|constell|List of constellation points (order of list matches pre_diff_code).|
|pre_diff_code|List of alphabet symbols (before applying any differential coding) (order of list matches constell).|
|rotational_symmetry|Number of rotations around unit circle that have the same representation.|
|dimensionality|Number of dimensions to the constellation.|

### Constellation space is divided into pie slices sectors

```
digital.constellation_psk(pmt_vector_cfloat constell, std::vector< int, std::allocator< int > > pre_diff_code, unsigned int n_sectors)
```
Constellation space is divided into pie slices sectors.
Each slice is associated with the nearest constellation point.
Works well for PSK but nothing else.
Assumes that there is a constellation point at 1.x

### Rectangular digital constellation

```
digital.constellation_rect(pmt_vector_cfloat constell, std::vector< int, std::allocator< int > > pre_diff_code, unsigned int rotational_symmetry, unsigned int real_sectors, unsigned int imag_sectors, float width_real_sectors, float width_imag_sectors)
```

Only implemented for 1-(complex)dimensional constellation.
Constellation space is divided into rectangular sectors. Each sector is associated with the nearest constellation point.
Works well for square QAM.
Works for any generic constellation provided sectors are not too large.
Constructor Specific Documentation:
Make a rectangular constellation object.


|Parameters|Note|
|  ----    | ----  |
|constell|List of constellation points (order of list matches pre_diff_code).|
|pre_diff_code|List of alphabet symbols (before applying any differential coding) (order of list matches constell).|
|rotational_symmetry|Number of rotations around unit circle that have the same representation.|
|real_sectors|Number of sectors the real axis is split in to.|
|imag_sectors|Number of sectors the imag axis is split in to.|
|width_real_sectors|width of each real sector to calculate decision boundaries.|
|width_imag_sectors|width of each imag sector to calculate decision boundaries.|


# REFERENCE
[gnuradio.digital: Constellations](https://www.gnuradio.org/doc/sphinx-3.7.3/digital/constellations.html#gnuradio.digital.qam.qam_constellation).

