# Nextage Wave Demo
Face detection wave demo for the [Kawada Nextage bi-manual robotics platform](http://nextage.kawada.jp/en/). Uses uEye cameras in the head of the robot to run an [OpenCV Haar feature-based cascade classifier](https://docs.opencv.org/3.4/db/d28/tutorial_cascade_classifier.html) to detect anybody staring at it. If they stare at the robot for a fixed time limit, the Nextage will commence a wave trajectory greeting.

This project makes use of [ROS](https://www.ros.org) for communication between nodes and [OpenCV](https://opencv.org) for computer vision. Motion was pre-planned using the inverse kinematics solver included in the [EXOTica motion planning library](https://ipab-slmc.github.io/exotica/overview.html).

## Video
[![Nextage Wave Demo](http://img.youtube.com/vi/-q6xLpI4pFU/0.jpg)](https://www.youtube.com/watch?v=-q6xLpI4pFU&feature=youtu.be "Nextage Video")

## Installation Instructions
To run this demo:

## Technical Details
* Use robot.launch when running on the real hardware - use demo.launch when running in simulation using the Intel RealSense camera

## Observations
* Demo uses ~60% of CPU of the small Intel NUC powering the Nextage

### About
This demo was created by Matt Timmons-Brown (and with the help of Vladimir Ivan and the Robotics Lab at the University of Edinburgh) as part of an internship at the [Edinburgh Centre for Robotics, School of Informatics, The University of Edinburgh](https://www.edinburgh-robotics.org).
