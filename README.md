# myzebo
My Gazebo PX4 SITL test project

# Tools
- Gazebo Harmonic
- PX4 SITL

# Setup

## Gazebo Harmonic

https://gazebosim.org/docs/harmonic/install_ubuntu/

On an ubuntu machine:

```bash
# install necessary tools
sudo apt-get update
sudo apt-get install curl lsb-release gnupg
```
```bash
# install gazebo harmonic
sudo curl https://packages.osrfoundation.org/gazebo.gpg --output /usr/share/keyrings/pkgs-osrf-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/pkgs-osrf-archive-keyring.gpg] https://packages.osrfoundation.org/gazebo/ubuntu-stable $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/gazebo-stable.list > /dev/null
sudo apt-get update
sudo apt-get install gz-harmonic
```

All libraries should be ready to use and the `gz sim` app ready to be executed.

## PX4

https://github.com/PX4/PX4-Autopilot
https://docs.px4.io/main/en/sim_gazebo_gz/

Outside of this repo:
```bash
git clone https://github.com/PX4/PX4-Autopilot.git --branch v1.17.0 --recursive
```
This clones PX4 at that version with all its submodules pulled in too.

Then:
```bash
cd PX4-Autopilot
bash ./Tools/setup/ubuntu.sh # for system deps
```

To compile and optionally run:
```bash
make px4_sitl gz_x500 # runs with x500 quadcopter
```

# ROS2 Stuff

## Quick Access Docs (learning)
- [First steps docs](https://docs.ros.org/en/jazzy/First-Steps.html)
- [Nodes](https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Nodes/Understanding-ROS2-Nodes.html)
- [Topics](https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Topics/Understanding-ROS2-Topics.html)
- [Services](https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Services/Understanding-ROS2-Services.html)
- [Actions](https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Actions/Understanding-ROS2-Actions.html)
- [Parameters](https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Parameters/Understanding-ROS2-Parameters.html)
- Launching many nodes at once with [ros2 launch](https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools/Launching-Multiple-Nodes/Launching-Multiple-Nodes.html)
- Recording / playing back data with [ros2 bag](https://docs.ros.org/en/jazzy/Tutorials/Beginner-CLI-Tools/Recording-And-Playing-Back-Data/Recording-And-Playing-Back-Data.html)

## Setup

clone repo, then:
```bash
vcs import src < workspace.repos
rosdep install --from-paths src --ignore-src -y
colcon build
```