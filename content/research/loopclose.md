+++
showonlyimage = false
draft = false
image = "imgs/BFL_LC/ImTests_01.png"
date  = "2016-05-20"
title = "Online Binary Feature Learning for Loop Closure"
tags  = ["LoopClose"]
+++

**Abstract:** 
Loop closure is an essential module in long-term SLAM, as detecting and recognizing
re-visited locations serves to bound localization drift and correct for
geometric map distortions. It also provides a mechanism to recover from
track loss. However, most methods employ offline learnt maps that cannot
be customized to the feature space of new environments. This work explores
a means to generate a loop closing map with online adaptive properties.
<!--more-->

#### Motivation and Background 
Loop closure is what I would call the _the lost robot problem_ (in the vein 
of the _kidnapped robot problem_).  No matter how much one wishes for
a SLAM system to succeed, there are times when it just might fail. 
The local map process, if there is one, usually prevent track loss by
maintaining a sense of location. This sense of location is achieved by
recognizing and exploiting high-frequency or low time interval
re-visits; imagine going to another room then back right away.  Keeping
a short term _memory_ of recent observations to generate the data
re-association will improve localization.
However, if the re-visit spans a long enough distance or time, such that
the _memory_ component cannot succeed, then more global data
re-association methods are needed; imagine going from home to
work/school/grandma's/etc.  Welcome to _loop closure_.

Loop closure is a tricky problem to solve. Make a mistake and it is over
for your map; unless you have a really good way of detecting mistakes
during map re-optimization.
Miss a re-visit and you stay lost; that's certainly happened to me lots
of times while driving!
Robots just don't have the corrective strategies humans have, so we
roboticists have to balance the trade-off between detection and error
rate.  In our language, that's called a precision-recall trade-off. 
As someone whose background is control and dynamical systems and whose
lab likes to think in these terms, we thought it would benefit the
loop-closure process if there were a way to incorporate motion
insensitivity into the detection process (full credit goes to Guangcong
for the initial idea during brainstorming sessions). 
Mathematically, the ideal outcome would be to have motion invariance, but
theoeretically proving and then deriving an algorithm for this may or may not
provide dividends per my colleague Stefano Soatto's findings.[^1] [^2]
Sometimes the answer leads to an efficient algorithm, sometimes the
computational complexity is too high.  More importantly, insensitivity
is often much easier to implement in practice and has nice computational
or numerical properties arising from the fact that insensitivity is like
an _approximate invariance_ (my words).  In controls, we love
insensitivity to nuisance signals. Unlike invariance, insensitivity can
be dialed up or down. Furthermore, there is usually a computational
relationship with insensitivity level, which means that both can be
modulated together to identify the best operating point across these two
factors.  That idea fundamentally motivates and describes our SLAM
research.

#### Learning Descriptors for Loop-Closure 

The loop-closure solution builds from ideas found in the IBuiLD [^3]
loop closure implementation, as well as from empirically-adaptive
descriptors like BOLD [^4].  Whereas BOLD aims for affine invariance of
the binary descriptor by masking out bit coordinates sensitive to affine
transformations, we mask out the ones that are sensitive across frames
(i.e., temporal motion insensitivity).
While BOLD is backed up by empirical evidence for its design, we focused
on establishing core properties of the masked descriptors in order to
confirm that the necessary topological properties of the masked Hamming
space supported the data association needs of loop closure.  In this
case, that meant _descriptor distances_ had the right properties and
behaviors as binary coordinates were masked out. The final result led to
a method with decent loop-closure performance.[^5] Though others have
surpassed this, this technique had pretty strong performance at the
time. We are currently working on a method that incorporates additional
forms of insensitivity and a more efficient querying structure to arrive
at an efficient, online method with very high precision at 100% recall
for common benchmark loop closure data sets.


[^1]: S. Soatto. "Steps Towards a Theory of Visual Information: Active
Perception, Signal-to-Symbol Conversion and the Interplay Between
Sensing and Control." 2011-2017.
[arXiv](https://arxiv.org/abs/1110.2053). He keeps changing the title
and the document. :-)
[^2]: S. Soatto and A. Chiuso. "Visual Representations: Defining Properties and Deep Approximations." 2014-2016. [arXiv](https://arxiv.org/abs/1411.7676). Also a living manuscript.
[^3]: S. Khan and D. Wollherr. "IBuILD: Incremental Bag of Binary Words
for Appearance Based  Loop  Closure  Detection." _ICRA_, pp 5441-5447, 2015.
[^4]: V. Balntas, L. Tang, and K. Mikolajczyk. "BOLD - Binary Online
learned Descriptor  for  Efficient  Image  Matching. _CVPR_, pp 2367-2375, 2015.
[^5]: G. Zhang, M.J. Lilly, and P.A. Vela. "Learning Binary Features Online from Motion Dynamics for Incremental Loop-Closure Detection and Place Recognition." _ICRA_, pp. 765-772, 2016.  [Abstract](https://ieeexplore.ieee.org/document/7487205). IEEE [pdf](https://ieeexplore.ieee.org/document/7487205). [arXiv](https://arxiv.org/abs/1601.03821). _Best Robotic Vision Paper Award Finalist_.
