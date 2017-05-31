# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

---

## Effects of P, I, D
- A PID controller is a control loop feedback mechanism that continuously calculates an error and applies a correction based on proportional, integral, and derivative terms. In our case, the Cross Track Error (CTE) is used to determine how far off the car is from the target position. Each of the 3 error terms are multipled by their respective constants (Kp, Ki, Kd) and combined to produce the steering angle the car should take in the next time step. 

- P: Proportional. the proportional term produces an output value that is proportional to the CTE. A high proportional term results in a large change in the ouput and will often overshoot the target position, causing the car to oscillate back and forth faster.

- I: Integral. The contribution from the integral term is proportional to both the magnitude of the error and the duration of the error. This term causes the car to converge on the target position more quickly and eliminates the steady-state error produced by the purely proportional controller. 

- D: Derivative. The derivative of the CTE is calculated by determining the slope of the error over time and multiplying this rate of chance by the derivative gain, Kd. This term predicts system behavior and thus improves settling time and stability of the system. Essentially, when the car turns its steering angle to correct for the CTE, the car will not keep driving at that angle all the way to the target position and therefore overshooting. Rather, the car will turn counterturn and therefore smooth the transition to the target position. 

## Choosing hyperparamters
- I manually tuned the PID constants and Kp, Ki, Kd. To start, I set all terms equal to 1.0. This resulted in the car drastiaclly oscillating, overshooting the target position, and driving off of the road. To mitigate the oscillations, I lowered the P and I terms to 0.1. The car was still overshooting and so, as a test, I set the I term equal to 0, and the car was able to stay on the road for a lap around the track. I then increased D to smoothen the corrections and make the driving more stable. After a few more minor tweaks I ended at a the following PID terms: P = 0.1 I = 0.00001 D = 3.0.


## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 

