# 📌 OpenCV GPU Installation Guide

## 🔹 Step 1: Download OpenCV GPU Package
📥 **Download the ZIP file from GitHub Releases:**  
🔗 [OpenCV GPU Package v4.12.0](https://github.com/VisionDepth/openCV-GPU/releases/download/v4.12.0/opencv_gpu_custom-4.12.0.zip)

---

## 🔹 Step 2: Extract the ZIP
Once downloaded, **extract** `opencv_gpu_custom-4.12.0.zip` to any folder on your system.  
Ensure the extracted folder contains:

- **opencv_gpu_custom-4.12.0/**
  - **cv2/** → Contains OpenCV files
  - **install_cv2.bat** → Installs OpenCV into Conda environment
  - **README.txt** → Installation guide

and once you extracted to destination change directory in conda by 
```
cd path/to/opencv_gpu_custom-4.12.0
```
---
## 🔹 Step 3: Create Conda Environment
1. **Enter** this into Conda Prompt
```
conda create -n openCVGPU python=3.12
conda activate openCVGPU
```
---
## 🔹 Step 4: Install OpenCV GPU
1. **Run** `install_cv2.bat` (Double-click the file).
2. This script **installs OpenCV into the `openCVGPU` environment**.

✅ **Now, OpenCV GPU is installed!** 🚀
