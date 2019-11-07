---
layout: post
title: "GNU Radio data analysis program"
subtitle: 'SDR Radio study.'
author: "WT"
header-img: "img/post-bg-2015.jpg"
catalog: true

tags:
  - GNU Radio
---

## Foreword
After collecting the data through USRP and GNU Radio, we have to analyze the data.
I search for how to get the data after GNU Radio and USRP.
There are two methods.

### Through MATLAB or GNU Octave
We can use [**read_complex_binary**](https://github.com/zhouwt612/Files-for-Posts/blob/master/Files/Data%20capture/read_complex_binary.m) and [**read_float_binary**](https://github.com/zhouwt612/Files-for-Posts/blob/master/Files/Data%20capture/read_float_binary.m) to get the transmission data.

### In MATLAB

```
data = fopen(file_name,'r');
data = fread(data);
fclose(file_name);
```

## Reference
[Capturing Signals in GNU Radio](http://www.csun.edu/~skatz/katzpage/sdr_project/sdr/capture_sigs.pdf).
