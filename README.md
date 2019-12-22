# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

## Project Basics
The goal of this project is:
Implement a PID controller in C++ to maneuver the vehicle around the track.

## Implementation
I implemented the PID algorithm procedure taught in the lessons.

## Reflection

### Effect of the P, I, D components
The proportional portion of the controller tries to steer the car toward the center line (against the cross-track error). If used along, the car overshoots the central line very easily and go out of the road very quickly. An example video where this component is used along is "./videos/Only-P-Controller.mov".

The differential portion helps to counteract the proportional trend to overshoot the center line by smoothing the approach to it. An example video where this component is used along is "./videos/Only-D-Controller.mov".

The integral portion tries to eliminate a possible bias on the controlled system that could prevent the error to be eliminated. If used along, it makes the car to go in circles. In the case of the simulator, no bias is present. An example video where this component is used along is "./videos/Only-I-Controller.mov".

### How the final hyperparameters were chosen
The parameters were chosen manually by try and error. First, make sure the car can drive straight with zero as parameters. Then add the proportional and the car start going on following the road but it starts overshooting go out of it. Then add the differential to try to overcome the overshooting. The integral part only moved the car out of the road; so, it stayed as 0.005. After the car drove the track without going out of it, the parameters increased to minimize the average cross-track error on a single track lap. 
Finally, the chosen hyperparameters (P, I, D coefficients) is [P: 0.22, I: 0.005, D: 7.0]. The vehicle can successfully drive around the track using this set of parameters under the condition that 'throttle' parameter is 0.3.

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
  * Run either `./install-mac.sh` or `./install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.
* Simulator. You can download these from the [project intro page](https://github.com/udacity/self-driving-car-sim/releases) in the classroom.