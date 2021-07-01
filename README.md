# Create-and-Save-Map-Using-Turtlebot3-with-SLAM
These will be the steps to install the tools needed for simulating, mapping, and controlling a turtlebot robot.

*These packages were applied under ROS melodic and Ubuntu 18.04*

## 1- Install TurtleBot3 Packages

`$ sudo apt-get install ros-melodic-dynamixel-sdk`<br/>
`$ sudo apt-get install ros-melodic-turtlebot3-msgs`<br/>
`$ sudo apt-get install ros-melodic-turtlebot3`<br/>



## 2- Set TurtleBot3 Model Name
`
$ echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
`

# Gazebo Simulation
## 3- Install Simulation Package
`$ cd ~/catkin_ws/src/`<br/>
`$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git`<br/>
`$ cd ~/catkin_ws && catkin_make`


## 4- Launch TurtleBot3 World

`$ export TURTLEBOT3_MODEL=burger`<br/>
`$ roslaunch turtlebot3_gazebo turtlebot3_world.launch`


## 5- Operate TurtleBot3
`
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
`

# SLAM Simulation
For every step open a new terminal 
## 6- Launch TurtleBot3 World
`$ export TURTLEBOT3_MODEL=burger`<br/>
`$ roslaunch turtlebot3_gazebo turtlebot3_world.launch`<br/>
![image](https://user-images.githubusercontent.com/85858256/124057048-73707500-da2f-11eb-86ed-6804ec2c4477.png)


**I get an ERROR: cannot launch node of type [gmapping/slam_gmapping]: gmapping**<br/>
**I solve it By using this commend:**<br/>
`
sudo apt install ros-melodic-gmapping
`

## 8- Run SLAM Node
`$ export TURTLEBOT3_MODEL=burger`<br/>
`$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping`

## 9- Run Teleoperation Node
`$ export TURTLEBOT3_MODEL=burger`<br/>
`$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch`<br/>
![image](https://user-images.githubusercontent.com/85858256/124059899-918ca400-da34-11eb-9fc1-1dc65fdecac4.png)



## 10- Save Map
`$ rosrun map_server map_saver -f ~/map`<br/>
![image](https://user-images.githubusercontent.com/85858256/124059969-abc68200-da34-11eb-993e-ad98c761f17d.png)
