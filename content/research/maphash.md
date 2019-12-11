+++
showonlyimage = false
draft = false
image = ""
date  = "2019-05-30"
title = "Map-Hash for Fast Local-Map Queries"
+++

**Abstract:** Long-term, large-area SLAM performance is best when it
is possible to match previously seen (but subsequently lost) map points
when they re-enter the field-of-view and are visible once more.
However, the time cost associated to matching against an ever increasing map
undermines real-time performance. We combine hashing and condition scoring
to arrive at a fast, bounded map-to-frame method we call _Map-Hash_.
The value of _Map-Hash_ is shown on a modified ORB-SLAM implementation
relative to baseline ORB-SLAM.
<!--more-->

More details soon.

[^1]: Y. Zhao, W. Ye, and P.A. Vela. "Low-Latency Visual SLAM with Appearance-Enhanced Local Map Building,"
_ICRA_, 2019. [Abstract](https://ieeexplore.ieee.org/document/8794046), IEEE [paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8794046), [arXiv](https://arxiv.org/pdf/1905.07797.pdf)
