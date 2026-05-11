This project implements a **Real-Time Parking Space Counter** using Computer Vision. It identifies available and occupied parking spots in a video feed by analyzing pixel counts within manually predefined regions of interest (ROI).

## 🚀 Overview

The system provides a robust way to track parking availability without complex deep learning models. It uses image processing techniques like adaptive thresholding, blurs, and dilations to differentiate between an empty spot (low pixel density) and an occupied spot (high pixel density).

---

## ✨ Features

* **Real-time Detection:** Updates the status of parking spots instantly as cars enter or leave.
* **Manual ROI Selection:** Includes a utility script to pick and save parking spot coordinates specifically for any static camera view.
* **Visual Indicators:** Draws green rectangles for free spots and red for occupied ones.
* **Live Counter:** Displays a HUD showing the total number of free spaces out of the total spots available.
* **Robust to Noise:** Designed to ignore smaller moving objects like pedestrians, only triggering for car-sized objects.

---

## 🏗️ System Architecture & Workflow

The system is split into two primary phases: configuration and execution.

### Methodology Workflow

1. **Spot Picking:** Run `parking_space_picker.py` to manually define the rectangles for each parking spot on a reference image. These coordinates are saved as a `.pkl` file.
2. **Processing Pipeline:**
* **Gray Scaling & Blur:** Converts frames to grayscale and applies Gaussian blur to reduce high-frequency noise.
* **Adaptive Thresholding:** Converts the image to a binary (black and white) format to highlight edges and features.
* **Median Blur & Dilation:** Removes salt-and-pepper noise and thickens features to make detection more reliable.


3. **Pixel Counting:** The system counts non-zero (white) pixels within each saved ROI.
4. **Classification:** If the pixel count is below a specific threshold, the spot is marked as "Free"; otherwise, it is "Occupied".

### Architecture Diagram

---

## 🛠️ Technology Stack

* **Language:** Python
* **Core Library:** OpenCV (Computer Vision)
* **Utilities:** * `cvzone` (for easier text and shape rendering)
* `pickle` (for saving/loading spot coordinates)
* `numpy` (for kernel operations)



---

## 📂 Project Structure

```text
Parking-Space-Counter/
│
├── templates/               # Web layout files (if applicable)
├── car_test.mp4             # Sample video feed for testing
├── carposition.pkl          # Saved coordinates of parking spots
├── main.py                  # Core logic for detection and counting
├── model_final.h5           # Pre-trained deep learning weights (optional)
├── requirements.txt         # Project dependencies
└── README.md                # You are here

```

---

## 🚀 Getting Started

### 1. Define Parking Spots

First, you must define where the spots are in your specific video feed.

* **Left Click:** Add a new spot.
* **Right Click:** Remove an existing spot.
* The spots are automatically saved to `carposition.pkl`.

### 2. Run Detection

Execute the main script to start the live counter:

```bash
python main.py

```

---

## 👨‍💻 Author

**Bharath Chilaka**
*AI/ML Researcher & Software Engineer*
[GitHub Profile](https://www.google.com/search?q=https://github.com/Bobby-111)

---

*Inspired by the Computer Vision tutorials by Murtaza's Workshop.*
