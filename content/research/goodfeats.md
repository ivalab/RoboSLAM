+++
showonlyimage = false
draft = false
image = ""
date  = "2015-11-20"
title = "Good Features for SLAM"
+++

**Abstract:** SLAM is an overdetermined online estimation problem whose
size grows with time, as new measurements are collected with each new
image.  Most _highly_ overdetermined problems can be converted to _smaller_ 
overdetermined problems without suffering a loss in accuracy.  In that spirit,
good features for SLAM investigates the question: How can we determine what
visual features to keep or to remove to preserve accuracy?  
<!--more-->

If we can answer the question above, then we can start to bound the
computational time of SLAM for real-time operation in large-scale and uncertain
environments.  Our first stab at this question was the 2015 CVPR paper "Good
Features to Track for Visual SLAM" [^1]
Since this
was our first foray into SLAM after having studied 3D reconstruction and
point cloud processing, it was applied to an EKF-based SLAM method 
(1pt RANSAC EKF-SLAM). Filter-based, indirect SLAM algorithms are the easiest
and quickest to get running. However, for robustness they typically require
RANSAC or some other outlier rejection method.  Here, we employed the
observability conditioning of the SLAM estimation problem as a filter for the
RANSAC process.  Rather than randomly selecting points, the algorithm rank orders
the points according to a conditioning score, then tests the resulting hypotheses.
The scoring here is the observbility condition number associated to the minimum
singular value of the observability matrix for the discrete time SLAM process.
For more efficient calculations, a special version of the observability matrix is
computed (the stripped observability matrix) whose rank and spectral properties
agree with the observability matrix.
The better the observability conditioning a point provides, the higher ranking
it should have.  Selecting points based on this criteria provides a mechanism
to be robust to error because observability conditioning is related to
estimation convergence and error rejection.

The approach was intended to provide proof-of-concept for the idea that the
features being tracked could be actively managed and incorporated into pose
estimation based on how they influence or condition the SLAM estimation.
As a concept, there are many ways to implement the approach. Furthermore,
it was meant to complement existing SLAM solutions.  Thus we anticipated that
_good features_ as a concept connected to solution conditioning would naturally
translate to other SLAM solution. 

[^1]: G. Zhang and P.A. Vela. "Good Features to Track for Visual SLAM." _CVPR_, pp 1373-1382, 2015.  [Abstract](https://ieeexplore.ieee.org/document/7298743), IEEE [pdf](https://ieeexplore.ieee.org/document/7298743),Open Access [pdf](https://www.cv-foundation.org/openaccess/content_cvpr_2015/papers/Zhang_Good_Features_to_2015_CVPR_paper.pdf).
