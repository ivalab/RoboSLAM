+++
showonlyimage = false
draft = false
image = ""
date  = "2016-11-20"
title = "Optimal Observability and Maximal Cardinality"
+++

**Abstract:** 
Uses the _good features_ for SLAM concept to propose a deterministic process
for inlier estimation that matches RANSAC performance while having a more
consistent time cost relative to RANSAC.  
Measurement selection and outlier rejection use feature condition scoring
and hypothesis testing. The outcomes suggest that randomized methods can be
superceded by bounded or fixed time-cost deterministic methods based on
feature point scoring.
<!--more-->

Methods to address robustness and time-cost of filter-based, indirect SLAM
tended to be at odds, whereby improving one would compromise the other.  As a
case in point, robustness using randomized model fitting in the form of
RANSAC-based methods increases the computational cost and variance through
repeated model fitting tests.  The number of model estimation and fitting
iterations is unknown since RANSAC uses data-driven termination condition.
Bounding the iterations will bound the runtime, but without the same robusness
guarantees as meeting the termination condition. We were interested in
exploring whether _good features_ observability scoring could be used to
not only prioritize the points to test, but to provide a deterministic
selection process with a fixed set of tests for better runtime properties.

Our earlier work on [_good features_](../goodfeats) suggested that an
alternative scheme to RANSAC could be used to perform outlier rejection
within a model fitting framework.  The key result was related to the
observability analysis, which found that three features tracked over two frames
provided usfficient information to render the system observable (a
fact more generally known when seeking to solve camera translation with
known measured and associated world points). If we could establish a
fast mechanism to generate many tracked triplets with good observability
scores, then these triplets would serve as the model fitting elements
of the sampling process of RANSAC. If the mechanism was deterministic,
then the randomized nature could be removed without loss of performance
(given that the triplets have better estimation properties than randomly
selected points).  The resulting publication was the ICRA 2015 paper "Optimally
Observable and Minimal Cardinality Monocular SLAM" [^1].

##### Post-Facto 
Our intent behind _good features_ was to show that (1) using the conditioning
to actively manage the estimation process has value, and (2) the concept was
extensible and flexible regarding existing SLAM solutions. They both require
proof by overwhelming evidence, in that the bruden of proof is on us to
demonstrate the value and the flexibility. As a step in that direction,
a similar concept was applied to the bundle-adjustment based SLAM method
known as ORB-SLAM. After feature matching, the BA optimization conditioning
of feature points was tested to identify the most robust set for camera pose
estimation. Again, the aim was to improve the pose estimation error by
identifying the best set of feature points to use in the local pose
optimization step. Unlike outlier rejection methods, we consider the
technique to be an _inlier selection_ method.  More details can be found 
[here](../gfselect)

[^1]: G. Zhang And P.A. Vela. "Optimally Observable and Minimal Cardinality Monocular SLAM." _ICRA_, pp. 5211-5218, 2015.  [Abstract](https://ieeexplore.ieee.org/document/7139925). IEEE [pdf](https://ieeexplore.ieee.org/document/7139925). 
