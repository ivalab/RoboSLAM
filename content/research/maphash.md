+++
showonlyimage = false
draft = false
image = "imgs/MapHash/overview.png"
date  = "2019-05-30"
title = "Map-Hash for Fast Local-Map Queries"
tags  = ["Map2Frame","GoodFeats"]
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

#### Motivation and Background 
Much of our earlier work on _Good Features for SLAM_ has exploited the
property of submodularity in order to obtain favorable compute vs
performance trade-off curves that are then optimized for the SLAM
implementation being modified. Turns out that the same idea can apply to
the map-to-frame data association when the underlying data structure is
a hash table. The map-to-frame process can be costly when considering
that all points in the local map must be tested to matching against
unmatched descriptors in the current frame.  The Good Features matching
method simplified some of this processing, but still required iterating
over all of the points.  A more promising approach would actually be to
pre-select what points would be more valuable to match against before
even performing the matching.  That's exactly what Map-Hash does and a
little more. 

#### Map-Hash Approach
First, some analysis determines what a good hash table quantity is relative
to our performance demands (here, looking at query matching versus table
memory). The quantity of tables is due to the fact that the hashing
structure is a multi-index hash. It breaks the binary descriptor into
smaller chunks and creates table for them. This chunking improves the
robustness and tolerance to bit errors. The trade-off is that more
tables are used and more tables are queried since each table acts like a
redundant check (that is not so redundant given that we expect there to
be noise in the binary descriptor).  Also unlike a normal hash table,
there will be many matches (probability of hash duplication is high) in
each chunk's hash table.  Now, rather than query against the entire set
of tables, Map-Hash prioritizes the tables based on the overall
conditioning of the points in each table. During the map-to-frame
associated, only the best conditioned table is selected for querying.
The rest are discarded.  As long as we can get some hits, it doesn't
matter that we leave some point unmatched from the map. Combining the
Map-Hash concept with [_Good Features_ matching](../gfmatch) will limit the amount of matches
sought anyhow, so there is nominal loss.  The paper was presented at
ICRA. [^1]


[^1]: Y. Zhao, W. Ye, and P.A. Vela. "Low-Latency Visual SLAM with Appearance-Enhanced Local Map Building,"
_ICRA_, 2019. [Abstract](https://ieeexplore.ieee.org/document/8794046), IEEE [paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8794046), [arXiv](https://arxiv.org/pdf/1905.07797.pdf)
