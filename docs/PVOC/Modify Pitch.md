---
layout: default
title: Modify Frequency
parent: PVOC
---

PVOC::modifyFrequency modifies the frequency at each time/frequency based on a user input function.

```c++
// Load Bah.wav from disk and convert to mid-side PVOC
PVOC bahPV = Audio( "Bah.wav" ).convertToMidSidePVOC();

// As time increases, shift all frequencies up by 40hz/sec.
PVOC modified = bahPV.modifyFrequency( []( Time t, Frequency f ){ return f + t * 40.0f; } );
```
