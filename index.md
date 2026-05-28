---
layout: default
title: "Teleoperation of Unmanned Ground Vehicles Using Human Foot-Based Interface"
---

## Abstract

<div style="text-align: justify;">
This paper presents a wearable foot-based teleoperation interface for a small-scale unmanned ground vehicle. The proposed interface uses a Bluetooth Low Energy inertial sensor attached to the operator's foot and converts foot orientation into Ackermann steering and speed commands in a ROS 2-based vehicle control architecture. The method is evaluated on a RoboRacer-type indoor test vehicle and compared with conventional manual joystick teleoperation. Experimental results show that the foot controller enabled continuous vehicle operation over the complete test run, with a more conservative speed profile than manual control. The manual joystick produced a higher average speed and longer travelled distance, while the foot interface resulted in lower maximum yaw rate and a narrower speed distribution. The results indicate that foot-based teleoperation is feasible for ground vehicle control, but further tuning of longitudinal command generation and steering sensitivity is required to improve driving efficiency and reduce operator workload.
</div>

---

## Links

- 📄 **Paper**: coming soon
- 💻 **Code**: coming soon
- 📊 **Rosbags / Data**: [Assets/Data](Assets/Data)

---

## Method

<div style="text-align: justify;">
The proposed system uses a foot-mounted BLE inertial sensor as a wearable teleoperation interface. The measured foot orientation is decoded on the operator-side computer, calibrated around a neutral pose, passed through a deadzone and low-pass filter, and converted into Ackermann speed and steering commands. The generated commands are published to the RoboRacer control stack through the same teleoperation input topic used by the reference manual controller.
</div>

<br>

<div style="display:flex; justify-content:center; align-items:center; gap:20px; flex-wrap:wrap; text-align:center;">
  <div style="width:80%; max-width:800px;">
    <img src="Assets/Figures/system.png" style="width:100%;"><br>
    <em>System architecture of the proposed foot-based teleoperation interface.</em>
  </div>
</div>

<br>


---

## Test Run

<div style="text-align: justify;">
The following recordings show the RoboRacer vehicle's steering and throttle functionalities with the proposed foot-based teleoperation interface.
</div>

<br>

<div style="display:flex; justify-content:center; align-items:flex-start; gap:20px; flex-wrap:wrap; text-align:center;">

  <div style="width:30%; min-width:250px;">
    <img src="Assets/Figures/steering.gif" style="width:100%;"><br>
    <em>Example test run using the foot-based teleoperation interface.</em>
  </div>

  <div style="width:30%; min-width:250px;">
    <img src="Assets/Figures/throttle.gif" style="width:100%;"><br>
    <em>Steering functionality test using foot-based commands.</em>
  </div>

  <div style="width:30%; min-width:250px;">
    <img src="Assets/Figures/combined.gif" style="width:100%;"><br>
    <em>Throttle functionality test using foot-based commands.</em>
  </div>

</div>

<!-- If you prefer MP4 instead of GIF, use this block and remove the GIF block above:

<div style="display:flex; justify-content:center; gap:20px; flex-wrap:wrap; text-align:center;">
  <video autoplay loop muted playsinline controls style="width:80%; max-width:800px;" src="Assets/Figures/foot_test_run.mp4"></video>
</div>

-->

---

## Results

<div style="text-align: justify;">

</div>

<br>

## Results

<div style="text-align: justify;">
The recorded runs were trimmed to equal length before comparison. The evaluation interval was approximately 216 seconds for both control methods. The foot controller completed the full run and generated continuous vehicle commands throughout the experiment. Compared with manual joystick control, it produced a more conservative speed profile and lower peak yaw-rate values.
</div>

<br>

<div style="display:flex; justify-content:center; width:100%;">

<table style="border-collapse: collapse; text-align: center;">
  <thead>
    <tr>
      <th style="padding: 6px 12px;">Metric</th>
      <th style="padding: 6px 12px;">Foot control</th>
      <th style="padding: 6px 12px;">Manual control</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 6px 12px; text-align:left;">Duration [s]</td>
      <td style="padding: 6px 12px;">215.93</td>
      <td style="padding: 6px 12px;">215.96</td>
    </tr>
    <tr>
      <td style="padding: 6px 12px; text-align:left;">Integrated distance [m]</td>
      <td style="padding: 6px 12px;">143.37</td>
      <td style="padding: 6px 12px;">186.02</td>
    </tr>
    <tr>
      <td style="padding: 6px 12px; text-align:left;">Mean speed [m/s]</td>
      <td style="padding: 6px 12px;">0.664</td>
      <td style="padding: 6px 12px;">0.861</td>
    </tr>
    <tr>
      <td style="padding: 6px 12px; text-align:left;">Maximum speed [m/s]</td>
      <td style="padding: 6px 12px;">0.698</td>
      <td style="padding: 6px 12px;">0.996</td>
    </tr>
    <tr>
      <td style="padding: 6px 12px; text-align:left;">Mean absolute yaw rate [rad/s]</td>
      <td style="padding: 6px 12px;">0.459</td>
      <td style="padding: 6px 12px;">0.485</td>
    </tr>
    <tr>
      <td style="padding: 6px 12px; text-align:left;">Maximum absolute yaw rate [rad/s]</td>
      <td style="padding: 6px 12px;">0.795</td>
      <td style="padding: 6px 12px;">1.181</td>
    </tr>
  </tbody>
</table>

</div>


<br>

<div style="display:flex; justify-content:center; align-items:flex-start; gap:20px; flex-wrap:wrap; text-align:center;">
  <div style="width:45%; max-width:500px;">
    <img src="Assets/Figures/03_speed_equal_length.png" style="width:100%;"><br>
    <em>Odometry speed comparison over equal-length runs.</em>
  </div>
  <div style="width:45%; max-width:500px;">
    <img src="Assets/Figures/04_yaw_rate_equal_length.png" style="width:100%;"><br>
    <em>Yaw-rate comparison over equal-length runs.</em>
  </div>
</div>

<br>

<div style="display:flex; justify-content:center; align-items:flex-start; gap:20px; flex-wrap:wrap; text-align:center;">
  <div style="width:45%; max-width:500px;">
    <img src="Assets/Figures/05_integrated_distance_equal_length.png" style="width:100%;"><br>
    <em>Integrated distance calculated from odometry speed.</em>
  </div>
  <div style="width:45%; max-width:500px;">
    <img src="Assets/Figures/06_speed_distribution_equal_length.png" style="width:100%;"><br>
    <em>Speed distribution over equal-length runs.</em>
  </div>
</div>

<br>

<div style="display:flex; justify-content:center; align-items:center; gap:20px; flex-wrap:wrap; text-align:center;">
  <div style="width:70%; max-width:750px;">
    <img src="Assets/Figures/07_speed_vs_turning_equal_length.png" style="width:100%;"><br>
    <em>Speed versus absolute yaw rate for foot-based and manual control.</em>
  </div>
</div>



---