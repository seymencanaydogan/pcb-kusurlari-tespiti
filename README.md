# 🔌 PCB Defect Detection Using Image Processing

This project is an **image processing–based application** developed to automatically detect defects on **Printed Circuit Boards (PCBs)**. The system compares a reference PCB image with test PCB images and highlights manufacturing defects using computer vision techniques.

The implementation is written in **Python** and mainly relies on **OpenCV** for image processing and feature matching.

---

## 📌 Project Objectives

The main goals of this project are to:

* Detect defects on PCB images by comparing them with a reference PCB
* Support multiple defect types:

  * **Open Circuit**
  * **Missing Hole**
  * **Mouse Bite**
* Align test PCB images with the reference image
* Highlight defect locations visually
* Compare detected defect coordinates with provided annotation data

---

## 🧠 System Overview

The program follows a **reference-based defect detection approach**:

1. A clean PCB image is used as the **reference**.
2. A defective PCB image is selected by the user.
3. The test image is aligned with the reference image using feature matching.
4. Differences between the processed reference and test images are extracted.
5. These differences are interpreted as PCB defects and visualized.

---

## 🛠 Libraries and Technologies

The following libraries are used in the project:

* **OpenCV (cv2)** – Image processing, feature detection, image alignment
* **NumPy** – Numerical and matrix operations
* **Matplotlib** – Visualization of intermediate steps and final results

---

## ⚙️ Image Processing Pipeline

### 1. User Input

* The user selects:

  * Defect type (Open Circuit, Missing Hole, Mouse Bite)
  * Test image index

### 2. Image Loading

* Reference PCB image is loaded from the `Reference` folder
* Test PCB image is loaded from the dataset
* Images are read in both **color** and **grayscale** formats

### 3. Preprocessing

* Grayscale conversion
* Gaussian blur for noise reduction
* Adaptive thresholding to generate binary templates

### 4. Feature Detection & Matching

* **ORB (Oriented FAST and Rotated BRIEF)** is used to detect keypoints
* Keypoints are matched using **Brute-Force matcher with Hamming distance**

### 5. Image Alignment

* A **homography matrix** is computed from matched keypoints
* Test image is warped to align with the reference PCB

### 6. Defect Extraction

* Binary images of reference and aligned test PCB are subtracted
* Median blur is applied to suppress noise
* Remaining regions represent detected PCB defects

---

## 📂 Project Structure

```
pcb-kusurlari-tespiti/
├── Reference/
│   └── 01.jpg
├── rotation/
│   ├── open_circuit/
│   ├── missing_hole/
│   └── mouse_bite/
├── Annotations/
├── src/
│   └── pcb_defect_detection.py
├── results/
│   └── defect_visualizations.png
├── README.md
```

> Folder names may vary depending on implementation.

---

## 🚀 How to Run

1. Clone the repository:

   ```bash
   git clone https://github.com/seymencanaydogan/pcb-kusurlari-tespiti
   ```

2. Install required dependencies:

   ```bash
   pip install opencv-python numpy matplotlib
   ```

3. Run the program:

   ```bash
   python pcb_defect_detection.py
   ```

4. Follow on-screen instructions to select defect type and test image.

---

## 📊 Results & Evaluation

* The detected defect coordinates are compared with the provided **annotation tables**.
* Experimental results show consistent alignment between detected points and annotation data.
* The system successfully detects all three defect types under given dataset conditions.

---

## ⚠️ Limitations & Improvements

* Some defects may appear duplicated due to image scaling issues.
* Resizing reference and test images to smaller resolutions (e.g., 750×450) can improve sharpness.
* Annotation tables must be scaled accordingly if resizing is applied.

Future improvements may include:

* Morphological post-processing for cleaner defect regions
* Deep learning–based PCB inspection
* Real-time inspection support

---

## 👤 Author

**Seymen Can Aydoğan**

---

