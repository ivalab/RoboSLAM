+++
showonlyimage = false
draft = false
image = ""
date  = "2019-12-05"
title = "Good Feature Matching in BA-SLAM"
+++

**Abstract:** Active map-to-frame matching using SLAM condition scoring 
is proposed for balancing time cost and accuracy in indirect, BA-SLAM.
Exploiting the submodularity property of pose optimization condition scoring
leads to an algorithm for deciding when to employ map-to-frame matching,
how many points to select, and how to prioritize the data association
to best benefit pose estimation outcomes. When applied to ORB-SLAM,
the algorithmic modification lowers run-time costs without impacting
localization performance.  
<!--more-->

This work stemmed from the _good features_ [selection strategy](../gfselect),
but rather than actively filter the points for pose-optimization _after_
data association, the method aims to do so _before_ data association.
The map-to-frame data association step is fairly costly in ORB-SLAM as it grows
with the size of the map.

Though implemented for ORB-SLAM, the technique is general and can be applied to
most any feature-based, BA-SLAM method employing a local pose optimization step
for the fast front-end thread.

[^1]: Y. Zhao and P.A. Vela. "Good Feature Matching: Towards Accurate, Robust Vo/VSLAM with Low-Latency." _under review_, 2019.
