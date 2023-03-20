---
layout: default
title: PVOC
has_children: true
---

The PVOC class represents Phase VOCoder data. This is a 2d sound format that contains spectral information over time. It is almost exactly a short time Forier transform, but it has an additional step that uses phase information to find accurate frequency estimations for partials in the input Audio. A fixed grid of bins covering a 2d rectangle with time and frequency axes is constructed. Each bin contains the magnitude and frequency estimation for the input Audio at that time and spectral region. The phase vocoder algorithm is, notably, invertible. The format is not without issues, as processing in the PVOC domain on stereo inputs tends to create coherence issues between channels. This can be partially avoided by using the "Audio::convertToMidSidePVOC" and "PVOC::convertToLeftRightAudio" processes. This replaces the channel coherence issue with a mid-side coherense issue. The latter just tends to sound wide, where the former is muddy.

