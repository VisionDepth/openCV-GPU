# 🚀 **Guide: Building OpenCV with CUDA Support**

This guide will walk you through **building OpenCV with CUDA support** on Windows using **CMake and Visual Studio**. This allows OpenCV to **leverage NVIDIA GPUs** for optimized image processing.

---

## **1️⃣ Prerequisites**

### ✅ **Required Software**
Before starting, ensure you have the following installed:

| Software | Version |
|----------|---------|
| **CUDA Toolkit** | Latest (e.g., 12.8) |
| **cuDNN** | Compatible with CUDA |
| **NVIDIA Video Codec SDK** | [Latest](https://developer.nvidia.com/downloads/designworks/video-codec-sdk/secure/13.0.19/video_codec_sdk_13.0.19.zip) |
| **CMake** | 3.24+ |
| **Miniconda** | [Latest](https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe) |
| **Visual Studio 2019/2022** | With C++ Build Tools |
| **Git** | Latest |
| **Python** | Installed (preferably via Miniconda) |
| **OpenCV Source Code** | Latest **opencv + opencv_contrib** |

---

## **2️⃣ Download OpenCV Source Code**

First, clone the OpenCV repository and its extra modules:
```bash
cd C:\Users\YOUR_USERNAME\openCVGPU

git clone --branch 4.x https://github.com/opencv/opencv.git

git clone --branch 4.x https://github.com/opencv/opencv_contrib.git
```

---

## **3️⃣ Configure OpenCV with CMake**

### 🔹 **Set CMake Build Options**

1. **Open CMake GUI** and set:
   - **Source code directory** → `C:/Users/YOUR_USERNAME/openCVGPU/opencv`
   - **Build directory** → `C:/Users/YOUR_USERNAME/openCVGPU/Build`

2. **Click "Configure"** and choose **Visual Studio 16 2019** or **Visual Studio 17 2022**, then set:
   - **Optional platform: x64**
   - **CUDA Support: ENABLED**

3. **Modify the following variables:**

| CMake Variable | Value |
|---------------|-------|
| `OPENCV_EXTRA_MODULES_PATH` | `C:/Users/YOUR_USERNAME/openCVGPU/opencv_contrib/modules` |
| `WITH_CUDA` | ✅ ON |
| `WITH_CUDNN` | ✅ ON |
| `WITH_CUBLAS` | ✅ ON |
| `WITH_NVCUVID` | ✅ ON |
| `WITH_NVCUVENC` | ✅ ON |
| `CUDA_ARCH_BIN` | **Set based on your GPU** (see Step 4) |
| `PYTHON3_EXECUTABLE` | `C:/Users/YOUR_USERNAME/miniconda3/envs/YOUR_ENV/python.exe` |
| `PYTHON3_LIBRARY` | `C:/Users/YOUR_USERNAME/miniconda3/envs/YOUR_ENV/libs/python312.lib` |
| `PYTHON3_INCLUDE_DIR` | `C:/Users/YOUR_USERNAME/miniconda3/envs/YOUR_ENV/include` |
| `PYTHON3_PACKAGES_PATH` | `C:/Users/YOUR_USERNAME/miniconda3/envs/YOUR_ENV/Lib/site-packages` |

4. **Click "Configure" again**, then **"Generate"**.

---

## **4️⃣ Set CUDA Architecture for Your GPU**

Run the following to find your CUDA compute capabilities:
```bash
nvcc --list-gpu-arch
```
For **RTX 3000+ GPUs**, set:
```bash
CUDA_ARCH_BIN=75;80;86;89;90
CUDA_ARCH_PTX=75;80;86;89;90
```

---

## **5️⃣ Build OpenCV with CUDA**

After generating CMake files, **compile OpenCV** with:
```bash
cmake --build "C:/Users/YOUR_USERNAME/openCVGPU/Build" --target INSTALL --config Release
```
This will install OpenCV with CUDA support.

---

## **6️⃣ Verify OpenCV Installation**

Activate your Python environment and check OpenCV installation:
```bash
conda activate YOUR_ENV
python -c "import cv2; print(cv2.getBuildInformation())"
```
Expected output:
- **CUDA enabled:** `YES`
- **cuDNN found:** `YES`

---

## **7️⃣ Add OpenCV to Python**
If OpenCV is not found, manually link it:
```bash
python -c "import sys; sys.path.append('C:/Users/YOUR_USERNAME/miniconda3/envs/YOUR_ENV/Lib/site-packages'); import cv2; print(cv2.__file__)"
```

✅ **Success! OpenCV is now running with CUDA acceleration.** 🚀🎉

