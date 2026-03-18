# STARTING
**TO START AUTOMATION / OPERATION**

# 1. Run the Stack Script

The stack script is a `.sh` file used to simplify launching multiple ROS2 packages simultaneously. In this system, it runs approximately **6 packages** (including `rosbag` for logging).

**Location:**

```
~/script/start_pb_stack.sh
```

### Steps:

```
chmod +x ~/script/start_pb_stack.sh
~/script/start_pb_stack.sh
```

### Notes:

* Wait until all ROS2 terminal windows finish launching
* Ensure the script has fully completed execution
* Check Mission Planner / GCS:

  * Make sure there is no "Bad Vision" warning

---

## 2. Start YOLO Detection Package

The YOLO ROS2 node is responsible for object detection and coordinate publishing.

**Source location:**

```
~/yolo_ws/src/yolov11_ros/yolov11_ros/yolo_node.py
```

### Build the workspace:

```
cd ~/yolo_ws
colcon build
source install/setup.bash
```

### Run the node:

```
ros2 launch yolob11_ros yolo_v11_ros_launch.py
```

### Notes:

* Wait until:

  * No new logs appear in terminal OR
  * Detected object coordinates start appearing
* If objects are not detected while stationary:

  * Detection may still work during drone movement
* Be cautious:

  * YOLO continuously publishes detected object coordinates
  * This may affect control behavior if detection is unstable

---

## 3. Start Control Manager Package

The control manager handles vehicle movement logic based on commands and detection input.

**Source location:**

```
~/palmbee_ws/src/PalmBee/pb_control/src/cm_setpoint.cpp
```

### Build the workspace:

```
cd ~/palmbee_ws
colcon build
source install/setup.bash
```

### Run the control node:

```
ros2 launch pb_control cm_setpoint.launch.py
```

### Notes:

* Alternative executables are available in `pb_control` if needed
* After launching:

  * Wait until terminal shows:

    ```
    waiting for arm
    ```
* Arm the vehicle using Mission Planner / GCS

### Behavior After Arming:

* The drone will:

  * Take off automatically
  * Execute predefined motion (e.g., circular trajectory)
  * React to detected object coordinates

---

## Additional Reference

For more detailed documentation, please reference ROS2 Humble documentation:
[Ros2 Humble Documentation](https://docs.ros.org/en/humble/index.html)
or check on Mission Planner Documentation ( GCS that being used )
[Mission Planner GCS Wiki](https://ardupilot.org/planner/docs/mission-planner-overview.html)

---

## Summary Flow

1. Run stack script
2. Start YOLO detection
3. Start control manager
4. Arm via GCS
5. Drone operates autonomously
