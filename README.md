# Install_Turtlebot3_with_SLAM_approach

PC Setup:

1) Download and Install Ubuntu on PC

- Download the proper Ubuntu 20.04 LTS Desktop image for your PC from the links below.
  https://releases.ubuntu.com/20.04/
  
- Follow the instruction below to install Ubuntu on PC.
  https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview

2) Install ROS on Remote PC
Open the terminal with Ctrl+Alt+T and enter below commands one at a time.
In order to check the details of the easy installation script, please refer to the script file (https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_noetic.sh)

$ sudo apt update
$ sudo apt upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_noetic.sh
$ chmod 755 ./install_ros_noetic.sh 
$ bash ./install_ros_noetic.sh

If the above installation fails, please refer to the official ROS1 Noetic installation guide (http://wiki.ros.org/noetic/Installation/Ubuntu)

3) Install Dependent ROS Packages

$ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
  ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
  ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
  ros-noetic-rosserial-python ros-noetic-rosserial-client \
  ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
  ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
  ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
  ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers
  
4) Install TurtleBot3 Packages
Install TurtleBot3 via Debian Packages.

$ sudo apt install ros-noetic-dynamixel-sdk
$ sudo apt install ros-noetic-turtlebot3-msgs
$ sudo apt install ros-noetic-turtlebot3

5) Network Configuration
https://emanual.robotis.com/assets/images/platform/turtlebot3/software/network_configuration.png 
https://emanual.robotis.com/assets/images/platform/turtlebot3/software/network_configuration.png

1. Connect PC to a WiFi device and find the assigned IP address with the command below.
 
$ ifconfig
https://emanual.robotis.com/assets/images/platform/turtlebot3/software/network_configuration2.png

2. Open the file and update the ROS IP settings with the command below.

$ nano ~/.bashrc

3. Press Ctrl+END or Alt+/ to move the cursor to the end of line.
Modify the address of localhost in the ROS_MASTER_URI and ROS_HOSTNAME with the IP address acquired from the above terminal window.

https://emanual.robotis.com/assets/images/platform/turtlebot3/software/network_configuration3.png

4. Source the bashrc with below command.

$ source ~/.bashrc
