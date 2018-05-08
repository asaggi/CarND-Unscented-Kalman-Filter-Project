# Unscented Kalman Filter Project
Self-Driving Car Engineer Nanodegree Program

The main goal of the project is to apply Unscented Kalman Filter to fuse data from LIDAR and Radar sensors of a self driving car using C++.

The main program can be built and ran by doing the following from the project top directory.

1. mkdir build
2. cd build
3. cmake ..
4. make
5. ./UnscentedKF

## Content of this repo
* `scr` a directory with the project code:  
 * `main.cpp` - reads in data, calls a function to run the Kalman filter, calls a function to calculate RMSE. 
 * `ukf.cpp` - the UKF filter itself, defines the predict function, the update function for lidar, and the update function for radar
 * `tools.cpp` - a function to calculate RMSE

## Initialization paramaters

This project included the option to tune various initialization parameters to improve the final calculated RMSE (root mean squared error). In the ukf.cpp file, I noted which portions I tuned, which included std_a, std_yawd, the initialized x_ (separately for Radar and Lidar) and P_ (also separate for each sensor type).

`std_a_`: process noise standard deviation longitudinal acceleration in m/s^2. I settled on a value of 1.5 here, as for a bike (which is what we are detecting in this project) I would not expect very high acceleration.  
`std_yawd_`: process noise standard deviation yaw acceleration in rad/s^2. A big would have to swerve pretty heavily for a big acceleration in yaw, so I settled for 0.57 radians here.  


## Other Important Dependencies
* cmake >= 3.5
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Results

Based on the provided data set, my Unscented Kalman Filter will produce the below results. The x-position is shown as 'px', y-position as 'py', velocity in the x-direction is 'vx', while velocity in the y-direction is 'vy'. Residual error is calculated by mean squared error (MSE).

### INPUT I 

Input  | MSE
------------- | -------------
px  | 0.0698
py  | 0.0697
vx  | 0.6197
vy  | 0.2756


![Test One Visualization](https://github.com/asaggi/CarND-Unscented-Kalman-Filter-Project/blob/master/data/Screen-I.png "Test One Visualization")

---

### INPUT II

Input  | MSE
------------- | -------------
px  | 0.0696
py  | 0.0819
vx  | 0.8232
vy  | 0.3438

![Test Two Visualization](https://github.com/asaggi/CarND-Unscented-Kalman-Filter-Project/blob/master/data/Screen-II.png "Test One Visualization")

---

