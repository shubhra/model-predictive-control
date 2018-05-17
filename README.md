# CarND-Controls-MPC
Self-Driving Car Engineer Nanodegree Program

Implement Model Predictive Control to drive a car around a track in a simulated environment.

---

## The Model

I have descrived the model great detail in this [article](https://medium.com/@shubhra.pandit/model-predictive-control-for-autonomous-vehicles-1dc18348f651)

## N and dt

The values for N and dt are finally set to 10 and 0.1 respectively. I started with a value of 25 for N and 0.05 for dt and that resulted in a very wavering kind of driving. Reducing the value of N and increasing the value of dt finally got me to 10 and 0.1 which gives a good result.

## Polynomial fitting
 
A 3rd order polynomial is fitted to the given waypoints after they are first transformed to the vehicle's coordinate system.

## Handling latency

A latency of 100ms is handled before MPC::Solve is called and new predicted values for x, y, psi, v, cte and epsi are calculated based on this latency. These predicted values are then sent to the solver.

## Cost function weights

Various weights for the different components of the cost function were calculated by trial and error. 

## Result

[Here's](https://youtu.be/iIvq3h2kbFk) a video of the car driving around the lake track.


## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1(mac, linux), 3.81(Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `install-mac.sh` or `install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.

* **Ipopt and CppAD:** Please refer to [this document](https://github.com/udacity/CarND-MPC-Project/blob/master/install_Ipopt_CppAD.md) for installation instructions.
* [Eigen](http://eigen.tuxfamily.org/index.php?title=Main_Page). This is already part of the repo so you shouldn't have to worry about it.
* Simulator. You can download these from the [releases tab](https://github.com/udacity/self-driving-car-sim/releases).
* Not a dependency but read the [DATA.md](./DATA.md) for a description of the data sent back from the simulator.


## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./mpc`.

