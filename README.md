# PID Controller - Autonomous Car

This project is an implementation of a PID controller for autonomous driving on a given track using C++.

## What is a PID Controller?

PID controller is a widely used simple reactive controller. 

A PID controller aims at generating a control output that would drive the error signal as close as to zero. The error signal is the difference between actual value and the desired value of a control variable.

In this scenario, the driving simulator considers the error signal to be the distance between the current car position and a reference trajectory. A PID controller is designed to minimize this error. I implemented two PID controllers, one for the steering angle and one for the throttle.

The proportional term (P) generates the output signal proportional to the error signal. A pure P controller is unstable and results in oscillations at the set point. Ideally, a pure P can not achieve a stable set point. The Integrator term (I) sums up the error signal over time. This provides a boost to the error signal to reach the desired set point. However, the I term can also result in overshooting the set point if not tuned correctly. The Differential term (D) corresponds to the rate of change of error signal over time. This is used to mitigate or dampen the oscillations. 

In short,
* 'P' helps steer the vehicle in proportion to the error.
* 'I' helps steer the vehicle in proportion to the total accumulated error from the start time.
* 'D' helps steer the vehicle in proportion to the difference in error from the previous time step.

## Results

After a lot of experimentation, my final values for PID were:
* Steering PID: 0.2, 0.004, 2.5
* Throttle PID: 0.15, 0.0075, 9.5

As seen from the values, Ki is very small or negligible as the 'I' controller is generally required in scenarios where the system has some kind of bias. Increasing Ki results in the car going off track.

[Video](https://youtu.be/G_NqE6z88Bs)
