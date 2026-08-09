# Build
```
colcon build from ros2_sw directory
source install/setup.bash

#Window 1
ros2 launch my_box_bot_gazebo start_world.launch.py

#Window 2
ros2 launch my_box_bot_gazebo spawn_robot_ros2_control_velocity.launch.xml

# Window 3
ros2 topic info /velocity_controller/commands
ros2 interface proto std_msgs/msg/Float64MultiArray

# speed value to start moving the lidar
 
ros2 topic pub /velocity_controller/commands std_msgs/msg/Float64MultiArray "layout:
  dim: []
  data_offset: 0
data: [20.0]
"

# Move in another direction

ros2 topic pub /velocity_controller/commands std_msgs/msg/Float64MultiArray "layout:
  dim: []
  data_offset: 0
data: [-20.0]
"

To stop:

ros2 topic pub /velocity_controller/commands std_msgs/msg/Float64MultiArray "layout:
  dim: []
  data_offset: 0
data: [0.0]
"
