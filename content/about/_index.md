+++
title = "IVALab RoboSLAM Research"
+++

Our research is in SLAM for Robotics is geared towards establishing
accurate, real-time realization of SLAM systems. We are interested
in achieving accurate SLAM estimates during online pose estimation
and map building. So far, our focus has been on the pose estimation 
(or localization) part of SLAM and not on the map building. Pose
estimation is critical when navigating unknown environments since
these same estimates are required for feedback trajectory control
of the mobile robot. A poor pose estimate will only get worse under
feedback, thus it is important to have the best possible estimate
within a reasonable time (relative to the control feedback rate).
Nevertheless, we believe that the ideas supporting rapid and robust pose
estimation will translate to map building.

Key to our work has been the notion of provable approximations. SLAM
can run faster if measurements are thrown out, however success and
performance will vary based on which are kept and which are not.
Using tools from the numerical optimization and numerical methods community, 
we believe it is possible to actively keep some measurements and
ignore others when estimating pose during SLAM, without impacting
performance. If possible to achieve, then it will be possible to
enhance the runtime of slow but accurate SLAM methods in a way
that provides positive benefite during controlled trajectory
tracking through unknown environments.  Current evidence indicates
that our _good features_ approach will indeed support such an outcome.
The main tool from the numerical optimization and numerical methods community
is that of _submodularity_, greedy optimization algorithms exploiting
submodularity, and proven near-optimality outcomes associated to these
algorithms. The work is a nice blend of control theory and approximation 
theory in support of efficient optimization algorithms.

We believe that the idea behind the work is quite general and can be applied
in many parts of the SLAM pipeline where there are data-induced computational
bottlenecks. In bundle-adjustment based SLAM methods, the problem size grows
with time, so active mechanisms to curate the measurements are needed
to preserve real-time operation. Both the front-end and back-end components
suffer from this problem, thus we have embarked on a journey to better
understand just how many components could be enhanced, how they could be
enhanced, and how general the concept is relative to existing SLAM solutions.
Our intent is to complement these solutions be leveraging their strengths
and addressing their computational weaknesses, but just enough that they
can function for mobile robot deployments and provide strong, high performance
solutions that do not degrade in the closed-loop. A consequence of the
nature of our investigation is that a lot of this work will use the
_good features_ descriptor in it, or some variant thereof, as we
explore SLAM from many angles, but with the same lens.

### Investigators Involved

- [Patricio A. Vela](http://pvela.gatech.edu)

#### Collaborators (Current and Former)

Former:

- [Panos Tsiotras](http://dcsl.gatech.edu/tsiotras.html)


### Former Investigators

- Wenkai Ye ([Linkedin](https://cn.linkedin.com/in/wenkai-ye-21b61a9b))
- Guangcong Zhang
  ([Linkedin](https://www.linkedin.com/in/gczhang?trk=people-guest_profile-result-card_result-card_full-click))
- [Yi-Pu Zhao](https://sites.google.com/site/zhaoyipu/home)
  ([Linkedin](https://www.linkedin.com/in/yipuzhao))
