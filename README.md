# GUI or ROS with Docker
This is the instruction for ROS installation with the docker container and docker image in VScode.
Here is a key issue for enabling gui with docker container


For different system isolation, I recommend using the docker environment to install the ROS system.

## Prepare the docker files to build the container
Create a new folder named ".devcontainer" with Dockerfile, docker-compose.yml, and devcontainer.json

In VScode, to build the container with "open folder (last directory which holds .devcontainer) in container"

## in bash
Desktop-Full Install: (Recommended): Everything in Desktop plus 2D/3D simulators and 2D/3D perception packages
Don't forget to pick your timezone and keyboard layout.

```
apt install ros-noetic-desktop-full
```

if failed
```
ps aux | grep apt
kill -9 720
dpkg --configure -a
apt install ros-noetic-desktop-full
```
And then source this script in every bash terminal you use ROS in automatically with
```
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### catkin
Catkin is the official build system for ROS (Robot Operating System). It is responsible for building, compiling, and managing the dependencies of ROS packages. It replaces the older build system in ROS, called rosbuild, and is designed to work with CMake to handle the building process.

after catkin_make or catkin_build
Source your workspace: After building a workspace, you need to "source" the workspace to update your environment so that ROS knows about the packages you've built. This is done by running:
```
source ~/catkin_ws/devel/setup.bash
```
### GUI
1.on mac
 open a terminal in Xquartz and SSH the server.

 <img width="486" alt="Screenshot 2024-10-14 at 22 55 00" src="https://github.com/user-attachments/assets/34801481-62d8-4c3b-a22f-d48f1654f340">

run ```echo $DISPLAY``` to see what is the display id like localhost:13.0
*This indicates which display ID is being used with Xquartz.

<img width="246" alt="Screenshot 2024-10-14 at 22 55 56" src="https://github.com/user-attachments/assets/c7e586bc-b442-4831-ba41-666f38b365b5">

 
2. now we can on mac terminal and ssh the server to run xeyes to see the GUI.
   if you meet this,
   
<img width="728" alt="Screenshot 2024-10-14 at 23 02 40" src="https://github.com/user-attachments/assets/66ddc71b-4710-4c8d-86f1-f5a5ac42f71e">

   in mac terminal, you should change your display ID with ```export DISPLAY=:16.0```
   and then run ```xeyes```
   it will display with Xquartz with sshed to server.
   
3.To Enable GUI in docker container

in Xquartz, we ssh server and connect to an established container

```docker exec -it ros /bin/bash```
and change the display id with mac's IP:0

<img width="734" alt="Screenshot 2024-10-14 at 23 24 51" src="https://github.com/user-attachments/assets/67e66b35-24b0-40a4-bf24-a64ff4697c42">

run ```xeyes```

