# Manipulate-with-turtlesim-package-in-ROS2
Basic interaction with the `turtlesim` package in ROS2, using topics, services, and parameters to control a virtual turtle.

## Requirements:
- Ubuntu 22.04 or compatible.
- ROS2 (e.g. Humble).
- turtlesim package installed: from Ubuntu terminal `sudo apt update` `sudo apt install ros-humble-turtlesim`

## Running and Simulation:
1. Run `turtlesim` (the simulation window):
   Open a new terminal and type `ros2 run turtlesim turtlesim_node`
2. Start teleoperation (keyboard control):
   Open a new terminal and type: `ros2 run turtlesim turtle_teleop_key` Use arrow keys to move the turtle manually.

## Interaction via ROS 2 Concepts:
# Topics: 
**To send and receive data continuously (send movement and receive position):**
- View available topics: `ros2 topic list`
- Monitor the turtle’s position: `ros2 topic echo /turtle1/pose`
- Send movement commands manually: `ros2 topic pub /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 1.0}}"`

# Services:
**To execute a specific operation on demand only (reset, clear, or spawn turtles)**
- View available services: `ros2 service list`
- Clear the background: `ros2 service call /clear std_srvs/srv/Empty`
- Reset the turtle to default position: `ros2 service call /reset std_srvs/srv/Empty`
- Spawn a second turtle: `ros2 service call /spawn turtlesim/srv/Spawn "{x: 2.0, y: 3.0, theta: 0.0, name: 'turtle2'}"`
- Teleport turtle1 to a specific position: `ros2 service call /turtle1/teleport_absolute turtlesim/srv/TeleportAbsolute "{x: 5.0, y: 5.0, theta: 0.0}"`

# Parameters: 
**To adjust node settings and configure environment behavior (Adjust the background color, or turn on/off the turtle effect)**
- List parameters: `ros2 param list`
- Change background color (e.g., yellow): `ros2 param set /turtlesim background_r 255
ros2 param set /turtlesim background_g 255
ros2 param set /turtlesim background_b 0
ros2 service call /clear std_srvs/srv/Empty`







``
