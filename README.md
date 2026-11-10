<div align="center">

# 🏋️ FitMantra — Exercise Pose Correction

**Real-time AI-powered fitness tracker that detects exercises and corrects your form — live.**

[![Python](https://img.shields.io/badge/Python-3.7%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![YOLOv8](https://img.shields.io/badge/YOLOv8-Ultralytics-purple?logo=github)](https://github.com/ultralytics/ultralytics)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-Pose-green?logo=google)](https://mediapipe.dev/)
[![Streamlit](https://img.shields.io/badge/Streamlit-App-red?logo=streamlit)](https://streamlit.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)


</div>

---

## � Overview

**FitMantra** is a computer vision system that tracks your workouts in real time and gives instant feedback on your exercise form. It uses **YOLOv8** for lightning-fast exercise classification and **MediaPipe Pose** for landmark-based posture analysis.

> 💡 Think of it as a **personal trainer on your screen** — no gym membership needed.

---

## 🎯 Supported Exercises

| Exercise | What's Analyzed |
|---|---|
| 💪 **Bicep Curls** | Elbow angle, shoulder stability, elbow drift |
| 🤸 **Push-Ups** | Back alignment, knee position, up/down phase detection |
| 🏋️ **Squats** | Knee-toe alignment, back angle, hip-knee-ankle angle |

---

## 🛠️ How It Works

### 1. 📹 Data Collection & Annotation
- Exercise videos were recorded at **60 FPS**
- Frames were extracted using a custom Python script
- **Roboflow** was used for annotation and data augmentation


### 2. 🤖 Model Training (YOLOv8)
- Dataset split: **70% Train / 20% Validation / 10% Test**
- Trained with **YOLOv8** for fast and robust exercise detection

| Metric | Score |
|---|---|
| 🎯 Precision | **99%** |
| 🔁 Recall | **89%** |
| 📊 mAP50-95 | **92.7%** |

### 3. 🦴 Pose Estimation & Form Analysis
**MediaPipe Pose** identifies 33 body landmarks in real time. Based on the detected exercise, custom geometry logic evaluates posture:

- **Push-Ups** → Detects up/down phases, checks back alignment via shoulder-hip-knee angle
- **Squats** → Evaluates knee-toe alignment, back angle, and hip-knee-ankle angle
- **Bicep Curls** → Monitors elbow movement, shoulder stability, and elbow-to-body distance

### 4. 🚀 Deployment
Deployed as an interactive **Streamlit** web app with three input modes:

| Mode | Description |
|---|---|
| 🎥 Webcam | Standard PC or external webcam |
| 📱 DroidCam USB | Use your smartphone as a webcam via USB |
| 📂 Video Upload | Upload pre-recorded exercise videos for analysis |

---

---

## ⚙️ Installation & Setup

### Prerequisites
- Python **3.7+**
- GPU *(optional but recommended for real-time performance)*

### 1. Clone the Repository
```bash
git clone https://github.com/prayagadage/FitMantra.git
cd FitMantra
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the App
```bash
streamlit run excercise_pose_correction.py
```

---

## 📦 Tech Stack

| Tool | Purpose |
|---|---|
| [YOLOv8](https://github.com/ultralytics/ultralytics) | Exercise classification |
| [MediaPipe](https://mediapipe.dev/) | Pose estimation & landmark detection |
| [OpenCV](https://opencv.org/) | Video processing & frame annotation |
| [Streamlit](https://streamlit.io/) | Web app interface |
| [Roboflow](https://roboflow.com/) | Dataset annotation & augmentation |

---

## 📁 Project Structure

```
FitMantra/
├── excercise_pose_correction.py   # Main Streamlit application
├── best.pt                        # Trained YOLOv8 model weights
├── requirements.txt               # Python dependencies
├── packages.txt                   # System packages
└── README.md
```

---
