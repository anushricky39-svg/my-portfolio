# 🛡️ SentinelVision AI — Smart Surveillance & Threat Detection Terminal

[![TensorFlow.js](https://img.shields.io/badge/TensorFlow.js-4.20.0-FF6F00?logo=tensorflow&logoColor=white)](https://www.tensorflow.org/js)
[![COCO-SSD](https://img.shields.io/badge/Model-COCO--SSD-blue)](https://github.com/tensorflow/tfjs-models/tree/master/coco-ssd)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3.3-7952B3?logo=bootstrap&logoColor=white)](https://getbootstrap.com/)
[![Web Audio API](https://img.shields.io/badge/Audio-Web_Audio_API-green)](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

An in-browser, real-time smart surveillance and threat detection terminal. Powered by **TensorFlow.js**, **COCO-SSD**, multi-color-space facial segmentation (**YCbCr + HSV**), and **temporal flicker heuristics**, SentinelVision AI operates completely client-side inside the browser with zero backend latency and full user privacy.

---

## 🌟 Key Features

### 1. 🧍‍♂️ Exact Human & Masked Subject Detection
* **Dual Facial Region Segmentation**: Evaluates the upper head region (forehead and eyes) against the lower facial zone (mouth, nose, and chin).
* **Multi-Color Space Skin Modeling**: Analyzes skin pigments across **YCbCr** (`60 <= Y <= 235`, `77 <= Cb <= 133`, `133 <= Cr <= 178`), **HSV** (`H in [0°, 28°] or [335°, 360°]`, `0.15 <= S <= 0.75`), and RGB channels.
* **Mask & Cloth Identification**: Recognizes surgical blue, black fabric, and N95 masks. If the lower face is covered while head features are present, the system flags the subject as `HUMAN: MASKED (SUSPICIOUS)`.
* **Loitering Security Timer**: Automatically initiates a timer when suspicious/masked individuals enter the frame, raising automated security alerts (5s warning, 12s critical escalation).

### 2. 🔥 Exact Fire Detection (Multi-Space + Temporal Flicker Analysis)
* **Flame Core & Envelope Analysis**: Simultaneously scans for bright yellow/white core heat and orange/red outer flame signatures.
* **Temporal Luminance Flicker Variance**: Measures frame-to-frame pixel luminance shifts (intensity delta > 12%). Because real flames rapidly flicker and change shape while static objects (red clothing, orange walls, signs) remain stationary, false positives are virtually eliminated.

### 3. 🌫️ Volumetric Smoke & Plume Detection
* **Plume Geometry Scanning**: Tracks expanding, rising haze directly above detected heat and flame sources.
* **Neutral Chromatic Scattering Model**: Detects low saturation (`S <= 0.18`), balanced RGB scattering (`|R-G| < 18`, `|G-B| < 18`), and calculates real-time smoke density percentages.

### 4. 🚗 Vehicle Classification
* **2-Wheelers**: Real-time detection and bounding boxes for motorcycles and bicycles.
* **4-Wheelers**: Instant recognition of cars, trucks, and buses.

### 5. 🚨 Tactical HUD & Audio Synthesizer
* **Web Audio API Siren**: Generates realistic dual-tone audio alarms dynamically without external sound files.
* **Live System Console**: Real-time timestamped event logging with severity indicators.
* **Interactive Control Matrix**: Individual hardware toggles for each detection category and manual alarm silencing cooldowns.

---

## 🛠️ Tech Stack

* **Front-End**: HTML5, CSS3, JavaScript (ES6+), Bootstrap 5, Bootstrap Icons
* **Machine Learning**: TensorFlow.js v4.20.0 & COCO-SSD v2.2.3
* **Computer Vision**: HTML5 Canvas, Offscreen Pixel Buffering, YCbCr / HSV Color Space Transforms
* **Audio Synthesis**: Web Audio API (OscillatorNode & GainNode)

---

## 📂 Project Structure

```text
sentinel/
├── index.html        # Complete application (HUD, styles, AI engine & detection pipelines)
└── README.md         # Documentation & setup guide
```

---

## 🚀 Quick Start (Local Setup)

1. **Clone or Download the Repository**:
   `ash
   git clone https://github.com/anushricky39-svg/portfolio.git
   cd portfolio/projects/sentinel
   `

2. **Open the Project**:
   * Double-click index.html to open it in any modern browser (Chrome, Edge, Firefox, Brave).
   * Or run a local HTTP server:
     `ash
     # Using Python
     python -m http.server 3000
     
     # Or using Node.js
     npx serve .
     `
3. Allow camera access when prompted by the browser and click **Start Live Webcam**!

---

## 🌐 Deploy to GitHub Pages (Live in 2 Minutes)

1. Push this folder or your portfolio to a GitHub repository:
   `ash
   git init
   git add .
   git commit -m feat: Add SentinelVision AI
   git branch -M main
   git remote add origin https://github.com/anushricky39-svg/sentinel-vision-ai.git
   git push -u origin main
   `
2. Navigate to your repository on GitHub -> **Settings** -> **Pages**.
3. Under **Branch**, select main and root folder / -> Click **Save**.
4. Your terminal will be live at:
   `	ext
   https://anushricky39-svg.github.io/sentinel-vision-ai/
   `

---

## 🔒 Privacy & Performance

* **100% Client-Side**: All video processing and inference runs locally on the client's device using WebGL hardware acceleration.
* **Zero Video Uploads**: Video feeds never leave your machine or get transmitted to any cloud servers.

---

## 👤 Author

* **GitHub**: [@anushricky39-svg](https://github.com/anushricky39-svg)
