# Multiple TurtleBot3 Navigation Environment
Literally as title, this package provides launch files allowing turtlebots to navigate in "the house". 


## Installation
1. Install ROS. (Hey Google, what is ROS?)
2. Clone all relative packages into <your_ws>/src/.
```
source /opt/ros/melodic/setup.bash
cd <your_ws>
wget https://gist.githubusercontent.com/airuchen/db3ee4f57b0f4ce97affac5beb5065d3/raw/9f6e2d1ed86d372f4116b6ea7a4195b7b623e115/multiple_turtlebot3_env.repos
vcs import src/ < multiple_turtlebot3_env.repos
catkin_make
source devel/setup.bash
```

## Usage 
1. First terminal -- Launch the simulation

* Source setup file.
```
source /opt/ros/melodic/setup.bash
source <your_ws>/devel/setup.bash
export TURTLEBOT3_MODEL=waffle_pi
```
* Launch multiple turtlebot3 in Gazebo simulation.
```
roslaunch turtlebot3_gazebo multi_turtlebot3.launch
```
There, there, you'll see the Gazebo window showing house model and three turtlebot3 -- tb3_0, tb3_1, tb3_2
![](resources/gazebo.png)
***To save the usage of your CPU usage, killall gzclient can close the GUI, which consumes lots of resource.***

2. Second terminal -- Launch navigation stacks
* Source setup file.
```
source /opt/ros/melodic/setup.bash
source <your_ws>/devel/setup.bash
```
* Launch Navigation for three turtlebot3.
```
roslaunch turtlebot3_navigation multi_nav_bringup.launch
```
Rviz shows up.
![](resources/rviz_all.png)

By changing topics in Tool properties, set Pose estimation of each bot.
![](resources/rviz_tool_properties.png)

After setting each of their pose, Rviz would be like this.
![](resources/rviz_set_pose.png)

Now, the way to set goal is identical with how you set the pose estimation. Try to give each robot a different goal. 
![](resources/rviz_set_goal.png)

## Control with Behavior Tree
TODO: multibot BT
