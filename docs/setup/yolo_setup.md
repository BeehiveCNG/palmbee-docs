
# YOLO Setup (Jetson)

This guide explains how to install YOLO on NVIDIA Jetson using the provided installation package.  
The installation process is **fully script-driven**, ensuring reproducibility and minimal manual configuration.

---

## Prerequisites

Before proceeding, ensure you have completed the main installation:

👉 https://github.com/BeehiveCNG/palmbee-docs/blob/main/docs/setup/installation.md

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

## Dependency Handling (Managed by Script)

The installation script ensures a consistent and compatible environment:

- **NumPy (1.26.4)**  
  Selected for compatibility with ZED SDK and Jetson ecosystem.

- **PyTorch (Jetson build)**  
  Installed with GPU (CUDA) support enabled for optimal performance.

- **OpenCV**  
  Uses the pre-installed Jetson system version instead of pip packages to maintain compatibility with hardware acceleration.

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

During installation, you may encounter warnings such as:

```bash
UserWarning: A NumPy version >=1.17.3 and <1.25.0 is required
ERROR: pip's dependency resolver does not currently take into account...
WARNING: Skipping opencv-python as it is not installed.
```

These are expected and do not affect functionality:

- **pip dependency conflict warning**  
  Occurs due to Jetson-specific package combinations

- **SciPy / NumPy warning**  
  Triggered by version constraints, but does not impact YOLO usage

- **Ultralytics auto-install messages**  
  Part of internal dependency handling

---

## Optional: YOLO Test

After installation, you may optionally test YOLO inference using the provided model.

> This step is optional and depends on your testing workflow.  
> The model can be placed in any directory as long as the path is correctly specified.

---

## Common Pitfalls After Installation

After a successful setup, certain changes to the environment may introduce issues:

- **Upgrading NumPy manually**  
  May break compatibility with ZED SDK

- **Installing OpenCV via pip**  
  Can override Jetson-optimized OpenCV and affect performance

- **Reinstalling PyTorch from pip**  
  May replace the Jetson-specific GPU-enabled build

> In general, it is recommended to keep the environment consistent with the script configuration unless specific changes are required and understood.

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
