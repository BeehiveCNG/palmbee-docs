# Installation

To install the PalmBee package, follow these steps:

---

#### 1. Install and setup ROS2 Humble First:


using this Ros2 Humble documentation
[Ros2 Humble Documentation](https://docs.ros.org/en/humble/Installation.html)


---

#### 2. Install and setup this specific Zed SDK:

[Zed2i SDK 4.2](https://www.stereolabs.com/en-id/developers/release/4.2)
note : this repository is based on wrapper 4.2.5 and tested on ZED SDK for JetPack 6.1 and 6.2 (L4T 36.4)


---

#### 3. Create the workspace directory:

```bash
mkdir -p palmbee_project
cd palmbee_project
```

---

#### 4. Clone the repository:

```bash
git clone https://github.com/BeehiveCNG/PalmBee
```

---

#### 5. Extract the 3 Zip File ( it's already in workspace form )

```bash
unzip palmbee_ws.zip -d palmbee_ws
unzip script.zip -d script
unzip yolo_ws.zip -d yolo_ws
```

---

#### 6. Install dependencies for palmbee_ws:

```bash
cd palmbee_ws
rosdep install --from-paths src --ignore-src -r -y
```

---

#### 7. Build the package:

```bash
colcon build
or build specific package (for example, pb_perception) using
colcon build --packages-select pb_perception
```
Note : there's will be some package that are missing and the ros2 build will encounter error if it's a clean install, please read the error message to know what package are missing and install it ( example : python3. . . or some other package like that)

---

#### 8. Source the setup file:

```bash
source install/setup.bash
```
or set it up on ~/.bashrc using the source command
note : for yolo_ws / u can also build it on different workspace and build it too ( but u must install / set yolo first and any package that yolo needed )
