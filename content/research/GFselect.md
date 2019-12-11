+++
showonlyimage = false
draft = false
image = ""
date  = "2019-11-20"
title = "Good Feature Selection in BA-SLAM"
+++

**Abstract:** SLAM condition scoring as a means to derive robust camera pose
estimation methods for bundle-adjustment based SLAM are explored and shown
to improve pose accuracy by 30% while increasing runtime by only 2%.
The key idea is to perform _inlier selection_ of tracked feature points so
that the local pose optimization has strong conditioning. Combining this
geometric conditioning with appearance-based match scoring leads to the
stated outcomes.
<!--more-->

This work is a spiritual extension of an earlier [ICRA paper](SELF) that
sought to improve the robustness and run-time properties of an EKF-SLAM
method.  It explores the same idea but applied to a popular
bundle-adjustment SLAM (BA-SLAM) method,
[ORB-SLAM](https://github.com/raulmur/ORB_SLAM).  Though implemented for
ORB-SLAM, the technique is general and can be applied to most any
feature-based, BA-SLAM method employing a local pose optimization step for
the fast front-end thread.

More text needed here.  Add pictures too.
