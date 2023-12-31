# ROS2
## 1.Introduction for ros2-Humble Hawksbill

### What is ROS? 
Robot Operating System 

### Version of ros?
**Ros** : 1st version. 
 
**Ros 2**: 2nd version (is now stable).
- In this tutorial, we use Humble Hawksbill version

### Why ros?
- Provided a standard for robotic application 
- Use on any robot
- Code separation and communication tools 
- Save you a huge amount of time and prevent you from reinventing the wheel 
- Is a language agnostic, so we can program in diferents languages like python or c++

### When to use ROS2?

Help you develop powerful and scalable robot applications, so when you need a lot of communicaction 

## 2.Tools we use 

**Terminal window**
 - Command prompt

**Visual studio**
- Code editor redefined and optimized for building and debugging modern web and cloud applications
- You can also install Microsoft Visual Studio Code from your Ubuntu's GUI
  
**Terminator**
- Its a improved terminal where you can split easily in four any layout
- To install it `sudo apt install terminator`

**Pip3**
- The official package manager and pip command for Python 3
- To install it `sudo apt install python3-pip`

**Colcon**
- Is a build tool and was created specify for ros2 
- To install it `sudo apt install python3-colcon-common-extensions`
- Put this line in your bashrc file

```
source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash
```


## 3.language libraries 
### rlc ### 
 - Is a ros library and it means Ross Client Library also is a  library which contains all the functionalities 

rclpy 
 - python

rclcpp 
 - c++

## 4.Debug and monitor the nodes
cat ~/.bashrc - line to service our cross to global installation and the line to service our cross to workspace 
make sure you have this lines, if you don´t added to the bashrc file 

```
source /opt/ros/humble/setup.bash
source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash
source ~/catkin_ws/install/setup.bash
```

you can also source directly if you are not sure that the new version you made was source

```
source ~/.bashtc
```

if you put ros2 with tab, you can see all the commands that you get 
remember ros pkg is for create a package 
run is for running a program with this you need a package and executable 


ros run -h is for get some help about the command
ros2 node list -> allow you to see all the nodes 

ros2 node info /node -> will you give you some information about subscribers

### Remame a Node at Runtime 

if you have differents nodes but with the same name, you will have problems when you run o get information,so for change the name you need to do 

run the package and then you will add 

ros2 run my_py_pkg py_node --ros-args --remap __node:=name of the node

ros2 run  my_cpp_pkg cpp_node --ros-args --remap __node:=prueba 

you can see the node have the original name when you run it, but with this line you change the name temporaly 


## 6.Colcon 

to build your workspace you need 

```
colcon build
```
if you want to build a specific package 
```
colcon build --packages-select #+name of the package 
```
for every change in the programm we need to build it
```
colcon build --packages-select #+name of the package --symlink-install 
```
it simply create a symbolic link to your file, so you dont build every change 


## 7.Rqt and rqt_graph 
its a node inside in to a package
we can use the command rqt because it was installed 
```
rqt
```
you will have a white screen, its normal because it is a collection of plugins 

first we need to run the package 

you can directly start accurately graph with ouput graph executable 
```
rqt_graph 
```

## 8.Turtlesim 
is a packages providing a simplified to the simulation of a robot
```
sudo apt install ros-humble-turtlesim 
```
for run the simulation 

```
ros2 run turtlesim
```
## 9.Debug ROS2 topics with command line tools 
To handle topics
```
ros2 topic 
```
yo can use

list,info,echo, interface show, find, hz, pub 

For see all the topic that is running
```
ro2 topic list
```
To see the atributes

```
ros2 topic info /name of the topic, to se the atributes 
```
Create a subscriber in the terminal 

```
ros2 topic echo /name of the topic
```

Print the definition and see what you will send to communicate 
```
ros2 interface show /type
```
Print the adverage of the heartz
```
ros2 topic hz /name of the topic 
```
Public in the node
```
ros2 topic pub -r (hz) /topic type "{data: message}" /name of the topic
```

## 10.Remap a Topic at Runtime
we can rename a node

```
ros2 run package, program, --ros-args -r __node:=my_station

```
you can rename diferrente topic in the same time
```
ros2 run package, program, --ros-args -r __node:=my_station -r robot_news:=my_news 
```
You can rename the package
```
 ros2 run package executable --ros-args -r __node:=my station --for change the name 
``` 

### 11.Experiment on topics with turtlesim 
To see the topic
```
ros2 node list
```
To see the parameter we want to see or modify
```
ros2 node info /turtlesim
```
To see the attributes 
```
ros2 interface show geometry_msgs/msg/Twist  
```
To see the atributes that compond
```
ros2 interface show geometry_msgs/msg/Vector3
```
To make a subscriber
```
ros2 topic echo /turtle1/cmd_vel
``` 
## 4.References 
 - [Ros2-Humble/Documentation](https://docs.ros.org/en/rolling/index.html)

