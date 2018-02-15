# **PID Controller** 

**PID Controller Project**

The goals / steps of this project are the following:
* Implement the PID controller as taught in lesson 16 "PID Control"
* Tune the PID controller parameters such that the vehicle safely drives through the simulated race track
* Summarize the results with a written report


[//]: # (Video References)

Unfortunately, I was not able to record videos.
I was not able to start recording in the simulator by pressing "R" as described in the menu - please let me how recording is done, and I will create videos and submit.
In addition, and since I used my company's notebook for the lesson, it might be, that installed protection software needed by the company's policy, prevents screen captuting.

## Rubric Points

## Implementation of PID Controller

#### Effect of P component

The P component is needed for steering the car back to the middle of the road if it deviates from it (based on the cross track error).
Using this control gain only (as described in lessons), the car oscillates around the middle of the road.
When utilizing only the P component in the simulation the oscilation becomes really wide and the car finally end up off the road.
With throttle control of 0.3 and  K_p = 0.22 that can be easily observed  and we do not make through the first (any) curve.

#### Effect of D component

Adding the D component to a P controller (resulting in a PD controller) results into stronger steering when the cross track error is increasing and to a weaker stearing while the cross track error is decreasing. This reduces the oscillation of the car around the road center observed with the P controller.
With throttle at .3 and a PD controller with gains K_p = 0.22 and K_d = 3.1 we make it through the simulation track - that is really impressive.

#### Effect of I component

The I component is needed for eliminating bias and drift errors of the system.
Playing with this parameter (on a low level: 0.00009 - 0.006), did not result in a significantly different behavior of the  vehicle.


## Parameter tuning

The parameter tuning was done by test and error and using the twiddle algorithm - though the time limitations that I had made it difficult to check and test the twiddle implementation itselt. P - gain was tried out a few iteration but the D component was added pretty early, since the car would not otherwise stay on the road.
Twiddle was run and the coefficient recalculated and retested. After some iterations the "basic" setup with K_p = 0.22 and K_d = 3.1 was found and proven to be good and some iteration for K_i tuning were done, resulting to the final setup.