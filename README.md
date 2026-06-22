# ✋ Hand Gesture - Controlled Screen Brightness

> Adjust your screen brightness with a pinch - no keyboard, no mouse, just your hand and a webcam.

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-5C3EE8.svg)](https://opencv.org/)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-Hand%20Tracking-00897B.svg)](https://developers.google.com/mediapipe)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 📖 Overview

This project enables **touch-free screen brightness control** using real-time hand gesture recognition. A webcam feed is processed to track your hand, and the distance between your **thumb** and **index finger** is mapped directly to your display's brightness level — pinch your fingers together to dim the screen, spread them apart to brighten it.

It combines **computer vision**, **gesture recognition**, and **human-computer interaction (HCI)** principles into a simple, interactive demo, and is easily extendable to control other system settings like volume or media playback.

## ✨ Features

- 🖐️ Real-time hand tracking using **MediaPipe's Hands module**
- 📏 Measures Euclidean distance between thumb tip and index fingertip
- 💡 Dynamically adjusts system brightness via **Screen Brightness Control (SBC)**
- 🎥 Live visual feedback - draws landmarks, a connecting line, and a midpoint circle on the video feed
- ⌨️ Simple exit control - press **`q`** to quit
- 🧩 Lightweight, dependency-minimal, and easy to extend to other gesture-based controls

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| Hand & Finger Tracking | [MediaPipe](https://developers.google.com/mediapipe) (Hands module) |
| Video Capture / Image Processing | [OpenCV](https://opencv.org/) |
| Brightness Control | [`screen-brightness-control`](https://pypi.org/project/screen-brightness-control/) |
| Numeric Interpolation | [NumPy](https://numpy.org/) |
| Language / Environment | Python 3, Jupyter Notebook |

## ⚙️ How It Works

```
Webcam Frame
    │
    ▼
Detect hand landmarks (MediaPipe Hands)
    │
    ▼
Extract thumb tip (landmark 4) & index tip (landmark 8)
    │
    ▼
Compute Euclidean distance (math.hypot)
    │
    ▼
Map distance range (≈15–220 px) → brightness range (0–100%) via np.interp
    │
    ▼
Apply brightness (Screen Brightness Control) + draw visual feedback
```

1. The webcam is initialized to capture live video frames.
2. Each frame is processed through MediaPipe's **Hands** module to detect hand landmarks.
3. The coordinates of the **thumb tip** (landmark 4) and **index fingertip** (landmark 8) are extracted.
4. The distance between these two points is calculated using the Euclidean distance formula (`hypot`).
5. This distance is interpolated from a fixed pixel range (e.g., 15–220 px) to a brightness range (0–100%) using `numpy.interp`.
6. The resulting brightness value is applied in real time using the `screen-brightness-control` library.
7. Lines and circles are drawn between the thumb and index finger on the live feed as visual feedback.
8. The loop continues until the user presses **`q`** to quit.

## 📂 Project Structure

```
Hand_Gesture_Recognition/
├── Hand Gesture.ipynb    # Main notebook: hand tracking + brightness control logic
├── app.py                # app.py script for easier reuse
├── requirements.txt      # Python dependencies
└── README.md
```

## 🚀 Getting Started

### Prerequisites
- Python 3.9+
- A working **webcam**
- Jupyter Notebook / JupyterLab (or VS Code with Jupyter extension)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/Gayathri-Reddy874/Hand_Gesture_Recognition.git
cd Hand_Gesture_Recognition

# 2. Create a virtual environment (recommended)
python -m venv venv
venv\Scripts\activate      # Windows
source venv/bin/activate   # macOS/Linux

# 3. Install dependencies
pip install -r requirements.txt
```

### Run the Project

```bash
jupyter notebook "Hand Gesture.ipynb"
```

Run all cells in order. A window will open showing your webcam feed — bring your thumb and index finger into view to start controlling brightness.

## 💡 Usage

1. Launch the notebook and run all cells.
2. Hold your hand up in front of the webcam so your thumb and index finger are clearly visible.
3. **Pinch fingers together** → brightness decreases.
4. **Spread fingers apart** → brightness increases.
5. Watch the on-screen line and circle for live feedback on the tracked distance.
6. Press **`q`** on the video window to exit.

## ⚠️ Notes & Limitations

- Requires good, even lighting for reliable hand detection.
- `screen-brightness-control` support varies by OS and hardware — it works most reliably on Windows and Linux; external/some laptop displays on macOS may not be controllable via software.
- The 15–220 px distance range is calibrated generally; you may need to tune it for your webcam's resolution and distance from the camera.
- Currently detects a single hand; behavior with multiple hands in frame is not explicitly handled.

## 🔭 Future Improvements

- [ ] Auto-calibrate the pixel distance range at startup
- [ ] Add on-screen brightness percentage overlay
- [ ] Extend gestures to control volume, media playback, or other system settings
- [ ] Add support for multi-hand detection and gesture disambiguation
- [ ] Package as an executable for non-technical users

## 🤝 Contributing

Contributions, issues, and feature requests are welcome. Feel free to check the [issues page](https://github.com/Gayathri-Reddy874/Hand_Gesture_Recognition/issues) or open a pull request.

## 📄 License

This project is open source. Consider adding a `LICENSE` file (e.g. MIT) to clarify usage rights for others.

## 👩‍💻 Author

**Mallareddygari Gayathri**

AI & ML Engineer 

GitHub: [@Gayathri-Reddy874](https://github.com/Gayathri-Reddy874)

---
⭐ If you found this project useful, consider giving it a star!
