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

![image](https://user-images.githubusercontent.com/86505558/184559434-6d95c292-83e8-4e35-a92a-954491e7ac0d.png)


1. Connect PC to a WiFi device and find the assigned IP address with the command below.
 
$ ifconfig

![image](https://user-images.githubusercontent.com/86505558/184559458-041cb658-cf84-42b9-807e-ffae656571cc.png)

2. Open the file and update the ROS IP settings with the command below.

$ nano ~/.bashrc

3. Press Ctrl+END or Alt+/ to move the cursor to the end of line.
Modify the address of localhost in the ROS_MASTER_URI and ROS_HOSTNAME with the IP address acquired from the above terminal window.

![image](https://user-images.githubusercontent.com/86505558/184559465-ca30660f-204b-4ca3-ad7e-702b710bdff9.png)

4. Source the bashrc with below command.

$ source ~/.bashrc

Navigation:

Run Navigation Nodes
1. If roscore is not running on the Remote PC, run roscore. Skip this step if roscore is already running.

$ roscore

2. If the Bringup is not running on the TurtleBot3 SBC, launch the Bringup. Skip this step if you have launched bringup previously.
Open a new terminal from Remote PC with Ctrl + Alt + T and connect to Raspberry Pi with its IP address. The default password is turtlebot. Please use the proper keyword among burger, waffle, waffle_pi for the TURTLEBOT3_MODEL parameter.

$ ssh ubuntu@{IP_ADDRESS_OF_RASPBERRY_PI}

$ export TURTLEBOT3_MODEL=${TB3_MODEL}

$ roslaunch turtlebot3_bringup turtlebot3_robot.launch

3. Launch the Navigation.
Please use the proper keyword among burger, waffle, waffle_pi for the TURTLEBOT3_MODEL parameter.

$ export TURTLEBOT3_MODEL=burger

$ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
