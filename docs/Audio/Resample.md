---
layout: default
title: Resample
parent: Audio
---

Resample changes the sample rate of the input to any other positive sample rate.

```c++
Audio bah( "Bah.wav" ); // Bah.wav may have a sample rate of 44100
Audio bar = bah.resample( 48000 ); // Bar will sound exactly the same as bah, but with more samples per second.
```
