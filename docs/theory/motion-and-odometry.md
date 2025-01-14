## Robotic Motion and Odometry

The following section describes the theory of robotic motion and odometry, which is part of the book [Elements of Robotics](https://link.springer.com/book/10.1007/978-3-319-62533-1). The section focuses on a detailed look on the quadrature encoders that are
attached to the robot wheels. For DiffBot the encoders are part of the [motors DG01D-E](https://www.sparkfun.com/products/16413). 

This section reviews the basic concepts of distance, time, velocity and acceleration. 
The physics of motion can be described using calculus, but a computer cannot deal with continuous functions; 
instead, discrete approximations must be used.

Odometry, the fundamental algorithm for computing robotic motion. 
An approximation of the location of a robot can be obtained by repeatedly computing the distance moved and 
the change direction from the velocity of the wheels in a short period of time. 
Unfortunately, odometry is subject to serious errors. 
It is important to understand that errors in direction are much more significant than errors in distance.

See the following video explaining odometry:

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/3S8MXsnNe3U" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


In the simplest implementation, the speed of the wheels of a robot is assumed to be proportional to 
the power applied by the motors. To improve the accuracy of odometry wheel encoders can be used, 
which measure the actual number of revolutions of the wheels.

The following video from Sparkfun gives an overview of Encoders

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/oLBYHbLO8W0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Distance, Velocity and Time

In general, if a robot moves at a constant applied to the motors it causes the wheels to rotate, which in turn causes the robot velocity $v$ for a period of time $t$, the distance $s$ it moves is $s = v \cdot t$. When power is to move at some velocity. However, we cannot specify that a certain power causes a certain velocity

- No two electrical or mechanical components are ever precisely identical.
- The environment affects the velocity of a robot because of different friction of the surface
- External forces can affect the velocity of a robot. It needs more power to sustain a specific velocity when moving uphill and less power when moving downhill, because the force of gravity decreases and increases the velocity.


!!! note
    Velocity is speed in a direction. A robot can be moving 10cm/s forwards or backwards; in both cases, the speed is the same but the velocity is different.


### Acceleration as Change in Velocity

To get a true picture of the motion of a robot, we need to divide its motion into
small segments $s_1,s_2,\dots$ and measure the distance and time for each segment individually. 
Then, we can compute the velocities for each segment. In symbols, if we denote the length of the
segment si by $\Delta s_i = x_{i+1} − x_i$ and the time it takes the robot to cross segment si by
$\Delta t_i = t_{i+1} − t_i$ , then $v_i$ , the velocity in segment $s_i$ is given by:

$$
v_i = \frac{\Delta s_i}{\Delta t_i}
$$


Acceleration is defined as the change in velocity over a period of time

$$a_i = \frac{\Delta v_i}{\Delta t_i}$$

