+++
showonlyimage = false
draft = false
image = ""
date  = "2019-11-20"
title = "Optimal Observability and Maximal Cardinality"
+++

**Abstract:** Methods to address robustness and time-cost of filter-based 
SLAM tended to be at odds, whereby improving one would compromise the other.
As a case in point, robustness using randomized model fitting in the form of
RANSAC-based methods increases the computational cost and variance through
repeated model fitting tests. Using the observability conditionin outcomes
of GF-SLAM, we proposed a deterministic process for inlier estimation that
matches RANSAC performance while having a consistent time const relative to
RANSAC.  The outcomes demonstrate that outlier rejection can be performed in
a principled manner using feature condition scoring functions and hypothesis
testing. It suggests that randomized methods can be superceded by bounded or
fixed time-cost deterministic methods based on available feature point score
values.
<!--more-->


This work extended the Good Feature study to 

The resulting publication was the ICRA 2015 paper "Optimally Observable and
Minmal Cardinality Monocular SLAM" 
(abstract [here](https://ieeexplore.ieee.org/document/7139925),
pdf [here](https://ieeexplore.ieee.org/document/7139925)). 

A similar concept was applied to the bundle-adjustment based SLAM method
known as ORB-SLAM. After feature matching, the BA optimization conditioning
of feature points was tested to identify the most robust set for camera pose
estimation. Again, the aim was to improve the pose estimation error by
identifying the best set of feature points to use in the local pose
optimization step. Unlike outlier rejection methods, we consider the
technique to be an _inlier selection_ method.  More details can be found 
[here](ADD)
