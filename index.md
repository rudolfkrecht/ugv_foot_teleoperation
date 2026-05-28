# Teleoperation of Unmanned Ground Vehicles Using Human Foot-Based Interface

## Rudolf Krecht, Miklós Unger, Balázs Szőnyi, Bálint Varga

[View on GitHub](https://github.com/rudolfkrecht/foot_teleoperation_ugv)

---

## Abstract

This paper presents a wearable foot-based teleoperation interface for a small-scale unmanned ground vehicle. The proposed interface uses a Bluetooth Low Energy inertial sensor attached to the operator's foot and converts foot orientation into Ackermann steering and speed commands in a ROS 2-based vehicle control architecture.

The method is evaluated on a RoboRacer-type indoor test vehicle and compared with conventional manual joystick teleoperation. Experimental results show that the foot controller enabled continuous vehicle operation over the complete test run, with a more conservative speed profile than manual control. The manual joystick produced a higher average speed and longer travelled distance, while the foot interface resulted in lower maximum yaw rate and a narrower speed distribution.

The results indicate that foot-based teleoperation is feasible for ground vehicle control, but further tuning of longitudinal command generation and steering sensitivity is required to improve driving efficiency and reduce operator workload.

---


## System Architecture


## Foot-Based Teleoperation Method

The control pipeline consists of the following steps:

1. Connect to the BLE inertial sensor.
2. Decode roll and pitch orientation values.
3. Store the initial foot pose as the neutral position.
4. Subtract the neutral offset from incoming measurements.
5. Map corrected foot angles to steering and speed commands.
6. Apply saturation, deadzone, and low-pass filtering.
7. Publish Ackermann drive commands to the `/teleop` topic.
8. Stop the vehicle if BLE packets are lost.

---

## Experimental Setup

![Wearable devices](figures/devices.jpg)

The experiment compared two input methods:

- Foot-based teleoperation using the BLE inertial sensor
- Manual teleoperation using a conventional joystick

Both methods controlled the same RoboRacer vehicle through the same ROS 2 control stack.

![Indoor test track](figures/indoortrack.jpg)

The measurements were carried out on an indoor track with straight and curved sections. ROS 2 bags were recorded during both runs and analysed offline.

---

## Results

The recorded runs were trimmed to equal length before comparison. The evaluation interval was approximately 216 seconds for both control methods.

| Metric | Foot control | Manual control |
|---|---:|---:|
| Duration [s] | 215.93 | 215.96 |
| Integrated distance [m] | 143.37 | 186.02 |
| Mean speed [m/s] | 0.664 | 0.861 |
| Maximum speed [m/s] | 0.698 | 0.996 |
| Mean absolute yaw rate [rad/s] | 0.459 | 0.485 |
| Maximum absolute yaw rate [rad/s] | 0.795 | 1.181 |

---

## Speed Comparison

![Speed comparison](figures/03_speed_equal_length.png)

The foot controller produced a nearly constant and conservative speed profile, while the manual joystick allowed higher vehicle speeds.

---

## Yaw-Rate Comparison

![Yaw-rate comparison](figures/04_yaw_rate_equal_length.png)

The manual joystick produced higher peak yaw-rate values, indicating more aggressive turning manoeuvres. The foot controller showed lower peak turning activity.

---

## Integrated Distance

![Integrated distance](figures/05_integrated_distance_equal_length.png)

The manual joystick covered a longer distance during the same time interval, mainly due to its higher average speed.

---

## Speed Distribution

![Speed distribution](figures/06_speed_distribution_equal_length.png)

The foot controller concentrated most speed samples in a narrow range, while the manual joystick produced a wider speed distribution.

---

## Speed Versus Turning Intensity

![Speed versus yaw rate](figures/07_speed_vs_turning_equal_length.png)

The manual joystick contains samples at both higher speed and higher yaw rate. The foot controller remains in a more conservative operating region.

---

## Commanded Speed

![Commanded speed](figures/08_commanded_speed_equal_length.png)

The implemented foot controller mostly generated a constant forward speed command, which explains the narrow speed distribution observed in the odometry data.

---

## Commanded Steering

![Commanded steering](figures/09_commanded_steering_equal_length.png)

The steering command shows frequent changes and repeated operation near the configured steering limits.

---

## Commanded Steering Distribution

![Commanded steering distribution](figures/10_commanded_steering_distribution.png)

The steering distribution indicates that further calibration and tuning of the foot-control mapping is required.

---

## Conclusion

The experiment demonstrates that a BLE inertial-sensor-based foot interface can be used for continuous teleoperation of a small unmanned ground vehicle. Compared with manual joystick control, the current foot controller resulted in slower but more conservative driving. The results support the feasibility of foot-based teleoperation, while also highlighting the need for improved throttle mapping, steering calibration, and user evaluation in future work.

---
