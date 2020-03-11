# Nextage Wave Demo
Face detection wave demo for the [Kawada Nextage bi-manual robotics platform](http://nextage.kawada.jp/en/). Uses uEye cameras in the head of the robot to run an [OpenCV Haar feature-based cascade classifier](https://docs.opencv.org/3.4/db/d28/tutorial_cascade_classifier.html) to detect anybody staring at it. If they stare at the robot for a fixed time limit, the Nextage will commence a wave trajectory greeting.

This project makes use of [ROS](https://www.ros.org) for communication between nodes and [OpenCV](https://opencv.org) for computer vision. Motion was pre-planned using the inverse kinematics solver included in the [EXOTica motion planning library](https://ipab-slmc.github.io/exotica/overview.html).

## Video
[![Nextage Wave Demo](http://img.youtube.com/vi/-q6xLpI4pFU/0.jpg)](https://www.youtube.com/watch?v=-q6xLpI4pFU&feature=youtu.be "Nextage Video")

Better video coming soon.

## Installation & Running Instructions
This demo has been tested in both simulation and on the real Nextage robotic platform. In simulation, the demo.launch script operates on the host PC assuming an Intel RealSense camera has been plugged in via USB. The waving motion can then be observed in the Kawada simulator. On the hardware, the robot.launch script operates on the Intel NUC inside the Nextage and uses one of the uEye webcams in the head of the robot. Waving motion is then triggered with the *right* arm.

### ROS Prerequisites
In order to install ROS, follow the official installation guide here: http://wiki.ros.org/Installation/Ubuntu

### Setting up the Kawada Docker
First, you must install Docker. To do this, follow the "Install using the repository" official guide here: https://docs.docker.com/install/linux/docker-ce/ubuntu/ Check with ```docker --version``` that the version you have installed is the latest. Older versions of Docker known to have issues. Tested with Docker version 19.03.

With Docker installed, now clone the Kawada docker. The Kawada simulator is packaged here: https://github.com/ipab-slmc/kawada-docker

```git clone https://github.com/ipab-slmc/kawada-docker```

To run the Kawada docker, change to the kawada-docker directory and use the command:

```./run-nvidia.sh```

### Setting up Intel RealSense
To install the Intel RealSense software, follow the IPAB Wiki guide here: https://github.com/ipab-slmc/wiki/wiki/Intel-RealSense2 (ROS integration steps are unnecessary to follow)

### Setup a Catkin Workspace and installing Demo
Setup a catkin workspace using the following cheat sheet: https://catkin-tools.readthedocs.io/en/latest/cheat_sheet.html

After this, navigate to the src directory and install the demo with the command:

```git clone https://github.com/the-raspberry-pi-guy/nextage-robot-wave-demo```

Build the workspace after this with the command:

```catkin build```

### Running in Simulation
To run the wave demo in simulation, ensure that the Intel Realsense is plugged into the host computer. In one window run the Kawada docker (as above), then start the simulator with the command:

```./startsim.sh```

![](https://raw.githubusercontent.com/the-raspberry-pi-guy/nextage-robot-wave-demo/master/img/sim.png)

After this, ensure that your workspace is properly sourced (see guide above) and run the demo with the command:

```roslaunch wave_demo demo.launch```

### Running on the Nextage Platform
To run on the physical Nextage platform, setup the demo in a workspace on the internal Intel NUC inside one of the Nextages. Follow the Wiki here with how to operate the Nextage:

Ensure there is enough space around the robot and run the demo with the command:

```roslaunch wave_demo robot.launch```

Step at least 1.5 metres in front of the robot. It will detect your face and after the time limit, a wave will be triggered with the right arm.

## Notes
* Demo uses ~60% of CPU of the small Intel NUC powering the Nextage
* Edit the rospy rate in detect and the other scripts to change the refresh rate of the camera. Also can edit the number of seconds the person needs to look at the Nextage before a wave is triggered.

### About
This demo was created by Matt Timmons-Brown (with the help of Vladimir Ivan and the Robotics Lab at the University of Edinburgh) as part of an internship at the [Edinburgh Centre for Robotics, School of Informatics, The University of Edinburgh](https://www.edinburgh-robotics.org).
