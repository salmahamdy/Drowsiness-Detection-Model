# 🚨 Real-Time Drowsiness & Head-Down Detection

### Using **OpenCV**, **MediaPipe Face Mesh**, and **MediaPipe Pose**

This project implements a **real-time driver drowsiness detection system** using standard RGB webcam input. It combines **Eye Aspect Ratio (EAR)**–based blink detection with **head-position monitoring** to identify signs of fatigue or inattention.

The system is lightweight, runs in real time, and can be deployed on edge devices such as **Jetson Nano** or standard laptops.

---

## ✨ Features

### 👁️ Eye Aspect Ratio (EAR) Drowsiness Detection

- Uses **MediaPipe Face Mesh** to extract 468 facial landmarks.
- Detects when the user's eyes remain closed for a sustained period.
- Triggers a **"Drowsy!"** alert when EAR falls below the threshold for a configurable number of frames.

### 🧍 Head-Down / Nodding Detection

- Uses **MediaPipe Pose** to track the **nose landmark**.
- Detects when the user's head drops below a safe visibility threshold.
- Displays **"Head Down!"** when the nose Y-coordinate indicates head tilt or nodding.

### 🎥 Real-Time Processing

- Operates on live webcam input.
- Displays detection overlays on the video stream.

---

## 🛠️ Technologies Used

| Library / Framework      | Purpose                                           |
|-------------------------|---------------------------------------------------|
| **OpenCV**              | Webcam capture, image preprocessing, visualization |
| **MediaPipe Face Mesh** | Facial landmark extraction (eyes)                  |
| **MediaPipe Pose**      | Head-position estimation (nose tracking)           |
| **NumPy**               | EAR calculations                                   |

---

## 🧠 Core Algorithm Overview

### 🔹 Eye Aspect Ratio (EAR)

EAR calculates the ratio between the vertical and horizontal distances of the eye:

$$EAR = \frac{A + B}{2C}$$

Where:

- **A** = distance between eye landmarks (1, 5)
- **B** = distance between eye landmarks (2, 4)
- **C** = horizontal distance (0, 3)

A low EAR indicates that the eyes are closed.

### 🔹 Drowsiness Logic

- If **EAR < 0.25** for **30 consecutive frames**, the system flags the user as drowsy.

### 🔹 Head-Down Logic

- Monitors pose nose landmark Y-coordinate.
- If **nose position > 70%** of frame height → **Head Down** alert.

---

## ▶️ How to Run

### 1️⃣ Install Dependencies

```bash
pip install opencv-python mediapipe numpy
# OR using requirements file
pip install -r requirements.txt
```

### 2️⃣ Run the Application

```bash
python drowsiness_detection.py
```

### 3️⃣ Exit

Press **'q'** to quit the program.
