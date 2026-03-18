
# YOLO Setup (Jetson)

This guide explains how to install YOLO on NVIDIA Jetson using the provided installation package.  
The installation process is **fully script-driven**, ensuring reproducibility and minimal manual configuration.

**Estimated time:** ~10–20 minutes  
**Disk usage:** ~1–2 GB  

---

## Prerequisites

Before proceeding, ensure you have completed the main installation:

👉 https://github.com/BeehiveCNG/palmbee-docs/blob/main/docs/setup/installation.md

### System Requirement

This setup is tested on:

- **JetPack 6.x (L4T r36.x)**
- CUDA 12.x
- Jetson Orin series

> Using JetPack 5.x or other versions may result in incompatibility with PyTorch and CUDA.

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

> The script will automatically handle all dependencies, environment setup, and compatibility adjustments.

---

## Python Environment Note (Important)

The installation uses:

```bash
python3 -m pip
```

which installs packages into the **system Python environment**.

Ensure that ROS 2 uses the same Python environment (typically system Python on Jetson).  
Otherwise, you may encounter:

```bash
ModuleNotFoundError: ultralytics
```

even though the installation was successful.

---

## Dependency Handling (Managed by Script)

The installation script ensures a consistent and compatible environment:

- **NumPy (1.26.4)**  
  Selected for compatibility with ZED SDK and Jetson ecosystem.

- **PyTorch (Jetson build)**  
  Installed with GPU (CUDA) support enabled for optimal performance.

- **OpenCV (system version)**  
  OpenCV is already provided by Jetson via system libraries (apt).  
  Installing `opencv-python` via pip may override this and break compatibility.

> These dependencies are configured automatically by the script.  
> Modifying them manually after installation may affect system stability or compatibility.

---

## Expected Output / Verification

If the installation is successful, you should see output similar to:

```bash
===== SYSTEM CHECK =====
Torch Version: 2.8.0
CUDA Available: True
GPU: Orin
NumPy Version: 1.26.4
OpenCV Version: 4.5.4

YOLO model loaded successfully
```

Key indicators of success:

- `CUDA Available: True` → GPU acceleration is active  
- `GPU: Orin` → Jetson GPU detected correctly  
- YOLO model loads without error  

---

## Known Warnings (Safe to Ignore)

These warnings are **EXPECTED and SAFE**:

- pip dependency resolver warning  
- SciPy requires numpy <1.25 warning  
- ultralytics missing dependency warning (opencv)  

Example:

```bash
UserWarning: A NumPy version >=1.17.3 and <1.25.0 is required
ERROR: pip's dependency resolver does not currently take into account...
WARNING: Skipping opencv-python as it is not installed.
```

> Do **NOT** attempt to fix these unless you fully understand the dependency chain.

---

## Optional: YOLO Test

You may optionally test YOLO inference after installation.

> This step is **only for verification**.  
> The model file (e.g. `yolo11n.pt`) is **not required** if you plan to use your own model later.

---

## Common Pitfalls After Installation

After a successful setup, certain changes may introduce issues:

- Upgrading NumPy manually  
- Installing OpenCV via pip  
- Reinstalling PyTorch from pip  

These actions may override the compatible environment created by the script.

---

## 🔧 Common Runtime Issues

1. **Torch import error (libcudss.so missing)**  
   → Caused by incorrect PyTorch build (not Jetson-compatible)

2. **GPU not detected**  
   → Wrong PyTorch build or CUDA mismatch

3. **ROS node cannot find ultralytics**  
   → Python environment mismatch between ROS and system Python

---

## Summary

The installation process is designed to be:

- Fully automated (script-driven)  
- Reproducible across Jetson devices  
- Compatible with ZED SDK and GPU acceleration  

Steps:

1. Extract package  
2. Enter directory  
3. Run setup script  
4. Verify output  

After completion, YOLO is ready for use with GPU acceleration on Jetson.
