# bag_to_depth_image
Save depth information in png image file from bagfile

This package has been tested using:

*  ROS Indigo
*  Ubuntu 14.04
*  Asus Xtion Pro Live
*  Kinect v1

The purpose of this package is to get save depth images for visualization purposes or processing ..etc

Quick Start:
===============

To use this package, clone the repository to your disc and build it:

    $ cd catkin_ws/src 
    $ git clone https://github.com/JaouadROS/bag_to_depth_image
    $ cd ..
    $ catkin_make
    $ source devel/setup.bash

Open a new shell and start the Openni driver or freenect driver:

Kinect:

     $ roslaunch freenect_launch freenect.launch

Asus:

     $ roslaunch openni2_launch openni2.launch


Open a new shell and record the rgb and depth information from the sensor

    $ roslaunch recordbag.launch

```sh
      ... logging to /home/jros/.ros/log/e1d7849a-3d20-11e6-b006-5c260a35b6aa/roslaunch-jros-17405.log
Checking log directory for disk usage. This may take awhile.
Press Ctrl-C to interrupt
Done checking log file disk usage. Usage is <1GB.

started roslaunch server http://jros:41339/

SUMMARY
========

PARAMETERS
 * /rosdistro: indigo
 * /rosversion: 1.11.19

NODES
  /
    recorddepth (rosbag/record)
    recordrgb (rosbag/record)

auto-starting new master
process[master]: started with pid [17417]
ROS_MASTER_URI=http://localhost:11311

setting /run_id to e1d7849a-3d20-11e6-b006-5c260a35b6aa
process[rosout-1]: started with pid [17430]
started core service [/rosout]
process[recordrgb-2]: started with pid [17433]
process[recorddepth-3]: started with pid [17448]
[ INFO] [1467112213.104747142]: Subscribing to /camera/rgb/image_raw
[ INFO] [1467112213.105328606]: Subscribing to /camera/depth/image
[ INFO] [1467112213.115601890]: Recording to /home/jros/catkin_ws/src/bag_to_depth_image/bagfile/newrgb.bag.
[ INFO] [1467112213.116899645]: Recording to /home/jros/catkin_ws/src/bag_to_depth_image/bagfile/newdepth.bag.

```

Enter ctrl-C to end recording. In bagfile there will be two bag files for depth and rgb.

Use export.launch to extract images from newrgb.bag and newdepth.bag

    $ roslaunch export.launch

The images will be saved into the folder of the executable's directory

    /home/jros/catkin_ws/devel/lib

You can move them to other directory, to bag_to_depth_image/images for example:

    mv /home/jros/catkin_ws/devel/lib/frame*.png /home/jros/catkin_ws/src/bag_to_depth_image/images/
    mv /home/jros/catkin_ws/devel/lib/dframe*.png /home/jros/catkin_ws/src/bag_to_depth_image/images/
