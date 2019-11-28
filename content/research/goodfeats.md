+++
showonlyimage = false
draft = false
image = ""
date  = "2019-11-20"
title = "Good Features for SLAM"
+++

**Abstract:** SLAM is an overdetermined online estimation problem whose
size grows with time, as new measurements are collected with each new
image.  Most overdetermined problems can be converted to smaller sized
overdetermined problems without suffering a loss in accuracy.  The
question is: how can we determine what visual features to keep or to
remove to preserve accuracy?  If we can answer that question, then we
can start to bound the computational time of SLAM for real-time
operation in large-scale and uncertain environments.
<!--more-->

Our first stab at this question was the 2015 CVPR paper "Good Features
to Track for Visual SLAM" 
(abstract [here](https://ieeexplore.ieee.org/document/7298743),
pdf [here](https://ieeexplore.ieee.org/document/7298743)). Since this
was our first foray into SLAM after having studied 3D reconstruction and
point cloud processing, it was applied to an EKF-based SLAM method 
(1pt RANSAC EKF-SLAM). EKF-SLAM algorithms are the easiest and quickest
to get running. However, for robustness they typically require something
like RANSAC or some other outlier rejection method.  Here, we employed
the observability conditioning of the SLAM estimation problem as a proxy
for the typical RANSAC scoring of model reprojection error.  the better
the observability conditioning a point provided, the higher ranking it
should have.  Selecting points based on this criteria provides a
mechanism to be robust to error because observability conditioning is
related to estimation convergence and error rejection.

