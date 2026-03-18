# Yolo installation

Here are the script used to for setting up yolo

before running it , make sure it's located in the same path as yolo_ws / inside of it
and if it's being run as .sh script, make sure to chmod +x it's first so it became a executable

```bash
#!/bin/bash

echo "==============================="
echo " YOLO + JETSON SETUP START"
echo "==============================="

==============================

0. CHECK PYTHON

==============================

echo "[1/8] Checking Python version..."
python3 --version

==============================

1. UPGRADE PIP

==============================

echo "[2/8] Upgrading pip..."
python3 -m pip install --upgrade pip

==============================

2. REMOVE CONFLICT PACKAGES

==============================

echo "[3/8] Removing conflicting packages..."
python3 -m pip uninstall -y opencv-python opencv-python-headless torch torchvision numpy

==============================

3. INSTALL NUMPY (ZED SAFE)

==============================

echo "[4/8] Installing compatible numpy..."
python3 -m pip install numpy==1.26.4

==============================

4. INSTALL TORCH (JETSON GPU)

==============================

echo "[5/8] Installing Jetson PyTorch (GPU)..."
python3 -m pip install
--index-url https://pypi.jetson-ai-lab.io/jp6/cu126
torch==2.8.0 torchvision==0.23.0

==============================

5. INSTALL ULTRALYTICS (NO DEPS)

==============================

echo "[6/8] Installing Ultralytics..."
python3 -m pip install ultralytics --no-deps

==============================

6. INSTALL OPTIONAL DEPENDENCY

==============================

echo "[7/8] Installing YOLO tracking dependency..."
python3 -m pip install lap

==============================

7. VERIFY INSTALLATION

==============================

echo "[8/8] Verifying installation..."

python3 <<EOF
import torch
from ultralytics import YOLO
import cv2
import numpy as np

print("===== CHECK =====")
print("Torch:", torch.version)
print("CUDA Available:", torch.cuda.is_available())

if torch.cuda.is_available():
print("GPU:", torch.cuda.get_device_name(0))

print("Numpy:", np.version)
print("OpenCV:", cv2.version)

test YOLO load

model = YOLO("yolo11n.pt")
print("YOLO loaded successfully")

EOF

echo "==============================="
echo " INSTALLATION DONE"
echo "==============================="

echo "NOTE:"
echo "- SciPy warning boleh diabaikan"
echo "- Jangan install opencv-python lagi"
echo "- Gunakan numpy 1.26.4 saja"
```
