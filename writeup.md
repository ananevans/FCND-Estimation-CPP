### Building an Estimator

In this project, I implemented an Extended Kalman Filter that uses measurements from a GPS and a magnometer. I followed the process described below.

Step 1: To calculate the standard deviation of the GPS and accelerometer X data, I wrote a Python script 
that reads the population values from the log files (`config/log/Graph1.txt` and `config/log/Graph2.txt`). 
Next, I use the `statistics.stdev` function to calculate the standard deviation for the population.

Step 2: I implemented the `UpdateFromIMU` using the function `FromEuler123_RPY` to translate the roll, pitch and yaw to a 
quaternion, and the used the `Quaternion` method `IntegrateBodyRate`.

Step 3: I implemented the `PredictState` function. First I transform the acceleration from body frame to inertial frame.
Next, I calculate the predicted state using the kinematic equations for distance and velocity.

Step 4: I implemented `GetRbgPrime` function using the equation (52) from the Estimation for Quadrotors.

Step 5: I implemented the `Predict` function using equation (51) for `gPrime` and the `PREDICT` pseudocode from Algorithm 2.

Step 6: I increased `QPosXYStd` and `QVelXYStd` until I got images similar to the ones shown in Tips and Tricks, step 3.5.

Step 7: I increased `QYawStd` until I got images similar to the ones in Tips and Tricks step 4.1.

Step 8: I implemented `UpdateFromMag` function using equations (57) and (58).

Step 9: I debugged the code for a few hours until the scenario `10_MagUpdate` passed.

Step 10: I implemented the function `UpdateFromGPS`.

Step 11: I copied the code and configuration file from the Control project.
