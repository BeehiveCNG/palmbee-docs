
# YOLO Setup (Jetson)

This guide explains how to install YOLO on NVIDIA Jetson using the provided installation package.

---

## Prerequisites

Before proceeding, ensure you have completed the main installation:

👉 Follow:  
https://github.com/BeehiveCNG/palmbee-docs/blob/main/docs/setup/installation.md

---

## Installation Steps

### 1. Extract YOLO Installation Package

Place the file:

```
yolo_installation.zip
```

Then extract it:

```bash
unzip yolo_installation.zip
```

---

### 2. Navigate to Installation Folder

```bash
cd "Yolo Installation"
```

---

### 3. Run Setup Script

Make the script executable:

```bash
chmod +x setup_yolo_jetson.sh
```

Run the installation:

```bash
./setup_yolo_jetson.sh
```

---

## Expected Output

If the installation runs correctly, you should see output similar to:

```bash
===============================
 YOLO + JETSON SETUP START
===============================

[1/8] Checking Python version...
Python 3.10.12

[2/8] Upgrading pip...
Requirement already satisfied: pip in ...

[3/8] Removing conflicting packages...
WARNING: Skipping opencv-python as it is not installed.
Successfully uninstalled torch-2.x.x
Successfully uninstalled numpy-1.x.x

[4/8] Installing compatible numpy (ZED safe)...
Successfully installed numpy-1.26.4

[5/8] Installing Jetson PyTorch (GPU support)...
Downloading torch-2.8.0...
Successfully installed torch-2.8.0 torchvision-0.23.0

[6/8] Installing Ultralytics (without dependencies)...
Requirement already satisfied: ultralytics ...

[7/8] Installing YOLO tracking dependency (lap)...
Successfully installed lap-0.5.12

[8/8] Verifying installation...

===== SYSTEM CHECK =====
Torch Version: 2.8.0
CUDA Available: True
GPU: Orin
NumPy Version: 1.26.4
OpenCV Version: 4.5.4

YOLO model loaded successfully

===============================
 INSTALLATION COMPLETE
===============================
```

---

## Notes

- Some warnings during installation are **expected and safe to ignore**.

Examples:

```bash
UserWarning: A NumPy version >=1.17.3 and <1.25.0 is required
ERROR: pip's dependency resolver does not currently take into account...
WARNING: Skipping opencv-python as it is not installed.
```

---

## Important Considerations

- Do **NOT** install `opencv-python` via pip (can break Jetson setup)
- Use **NumPy version 1.26.4** for compatibility with ZED SDK
- SciPy-related warnings can be safely ignored

---

## Summary

Steps performed:

1. Extract YOLO installation package  
2. Enter installation directory  
3. Run setup script  
4. Verify installation output  

After completion, YOLO is ready for use on Jetson with GPU acceleration.
