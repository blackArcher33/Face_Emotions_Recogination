# 🎭 Face Emotion Recognition with Deep Learning

![Banner](https://img.shields.io/badge/Maintained%3F-yes-green.svg) ![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg) ![Flask](https://img.shields.io/badge/Flask-2.0%2B-orange.svg) ![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-red.svg)

A robust, real-time Facial Emotion Recognition (FER) system built using Convolutional Neural Networks (CNN) and deployed as a web application using Flask.

---

## 🚀 Key Features

- **Real-time Detection**: Seamlessly detect emotions through your webcam.
- **Image Analysis**: Upload and analyze facial expressions in static images.
- **High Accuracy**: Powered by a deep learning model trained on the FER2013 dataset.
- **Interactive UI**: User-friendly web interface with live feedback.
- **Visual Feedback**: Real-time bounding boxes and emotion labels with confidence percentages.

---

## 🔄 Project Flow & Logic

The project follows a modular architecture, separating the core AI logic from the web interface.

### 1. Data Processing
The model expects a 48x48 pixel grayscale image. The input is normalized (divided by 255.0) before being fed into the CNN.

### 2. Model Architecture
- **Input Layer**: Grayscale frames (48x48x1).
- **CNN Layers**: Extract spatial features like eye position, mouth shape, and brow furrows.
- **Output Layer**: Softmax activation predicting 7 emotions: `Angry`, `Disgust`, `Fear`, `Happy`, `Sad`, `Surprise`, `Neutral`.

### 3. Execution Logic
```mermaid
graph TD
    A[Start Application] --> B[Web Interface Load]
    B --> C{Select Mode}
    C -->|Static Image| D[Upload Image]
    C -->|Live Camera| E[Open Webcam Stream]
    
    D --> F[Detect Faces using Haar Cascades]
    E --> F
    
    F --> G[Precompute Region of Interest - ROI]
    G --> H[Resize to 48x48 & Grayscale]
    H --> I[Deep Learning Model Prediction]
    I --> J[Overlay Emotion Label]
    
    J --> K[Display Result to User]
```

---

## 📂 Project Structure

- `app.py`: The heart of the web server (Flask).
- `FER_Camera.py`: Handles the video stream and real-time inference logic.
- `Live_FER.py`: Utility script for running detection on local files or testing.
- `model.json`: The saved architecture of our Neural Network.
- `model_weights.h5`: The "brain" of the project containing pre-trained weights.
- `templates/`: HTML files for the front-end.
- `static/`: CSS and Images used in the UI.

---

## 🛠️ Installation & Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/blackArcher33/Face_Emotions_Recogination.git
   cd Face_Emotions_Recogination
   ```

2. **Install dependencies**:
   ```bash
   pip install flask opencv-python tensorflow numpy
   ```

3. **Run the application**:
   ```bash
   python app.py
   ```
   Open `http://127.0.0.1:5000` in your browser.

---

## 🖼️ Preview

![Detection Example](static/images/All_Emotions_Detection.jpg)

> **Pro Tip**: Ensure your face is well-lit for the best real-time accuracy!

---

## 👨‍💻 Author
**Udit Singh**
[GitHub Profile](https://github.com/blackArcher33)

---
*Developed for research and educational purposes.*
