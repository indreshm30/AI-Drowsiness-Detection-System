# Drowsiness Detection System

A real-time drowsiness detection system using computer vision and facial landmark detection to monitor driver alertness and prevent accidents caused by fatigue.

## 🎯 Project Overview

This system uses a webcam to monitor a person's eyes in real-time and detects signs of drowsiness by calculating the Eye Aspect Ratio (EAR). When drowsiness is detected (eyes closed for a specified duration), the system triggers an audio alarm to alert the user.

## 🔬 How It Works

The system operates on the principle of **Eye Aspect Ratio (EAR)**:

1. **Face Detection**: Uses dlib's frontal face detector to locate faces in the video stream
2. **Facial Landmark Detection**: Identifies 68 facial landmarks, focusing on eye regions
3. **EAR Calculation**: Computes the ratio of eye height to eye width
4. **Drowsiness Detection**: When EAR falls below threshold for consecutive frames, triggers alarm
5. **Alert System**: Plays audio alarm and displays visual warning

### Eye Aspect Ratio Formula
```
EAR = (|p2 - p6| + |p3 - p5|) / (2 * |p1 - p4|)
```
Where p1, p2, p3, p4, p5, p6 are the eye landmark coordinates.

## 🚀 Features

- **Real-time Detection**: Processes video feed in real-time
- **Visual Feedback**: Green contours around detected eyes
- **Audio Alert**: Plays alarm sound when drowsiness detected
- **Visual Alert**: Displays "ALERT!" text on screen
- **Adjustable Sensitivity**: Customizable threshold and frame count parameters

## 📋 Requirements

### Prerequisites
- Python 3.6 or higher
- Webcam/Camera

### Required Libraries
```
opencv-python (cv2)
dlib
imutils
scipy
pygame
numpy
```

## 🛠️ Installation

### Step 1: Clone the Repository
```bash
git clone https://github.com/yourusername/drowsiness-detection-system.git
cd drowsiness-detection-system
```

### Step 2: Install Dependencies
```bash
pip install opencv-python
pip install dlib
pip install imutils
pip install scipy
pip install pygame
pip install numpy
```

**Note**: Installing dlib might require additional setup:
- **Windows**: `pip install dlib` (may need Visual Studio Build Tools)
- **Linux**: `sudo apt-get install cmake` then `pip install dlib`
- **macOS**: `brew install cmake` then `pip install dlib`

### Step 3: Download Required Model
The project requires the dlib facial landmark predictor model:
- File: `shape_predictor_68_face_landmarks.dat`
- This file is already included in the repository
- If missing, download from: http://dlib.net/files/shape_predictor_68_face_landmarks.dat.bz2

## 🎮 Usage

### Running the Application
```bash
python detection.py
```

### Controls
- **'q' key**: Quit the application
- The system will automatically start detecting faces and monitoring for drowsiness

### Configuration Parameters
You can modify these parameters in `detection.py`:

```python
thresh = 0.25      # EAR threshold (lower = more sensitive)
frame_check = 20   # Consecutive frames below threshold before alert
cap = cv2.VideoCapture(1)  # Camera index (0 for default camera)
```

## 📁 Project Structure

```
drowsiness-detection-system/
│
├── detection.py                           # Main application script
├── alarm.wav                             # Alert sound file
├── shape_predictor_68_face_landmarks.dat # Dlib facial landmark model
├── README.md                             # Project documentation
├── reports/                              # Project reports and documentation
│   ├── Final report _merged.pdf
│   ├── REPORT DDS.pdf
│   └── Team_No77.pptx
└── requirements.txt                      # Python dependencies (to be created)
```

## 🔧 Technical Details

### Algorithm Workflow
1. Initialize camera and load facial landmark predictor
2. Capture video frame
3. Convert to grayscale for processing
4. Detect faces in the frame
5. For each face:
   - Extract facial landmarks
   - Calculate EAR for both eyes
   - Average the EAR values
   - Check if EAR < threshold
   - Increment counter if below threshold
   - Trigger alert if counter exceeds frame_check
6. Display processed frame with eye contours
7. Repeat until 'q' is pressed

### Key Parameters
- **EAR Threshold (0.25)**: Below this value indicates closed/closing eyes
- **Frame Check (20)**: Number of consecutive frames below threshold before alert
- **Camera Index (1)**: Adjust based on your camera setup

## 🚨 Troubleshooting

### Common Issues

1. **Camera not detected**
   - Change camera index in `cv2.VideoCapture(0)` (try 0, 1, 2...)
   - Ensure camera permissions are granted

2. **Dlib installation fails**
   - Install Visual Studio Build Tools (Windows)
   - Install cmake and boost libraries (Linux/macOS)

3. **Model file error**
   - Ensure `shape_predictor_68_face_landmarks.dat` is in the same directory
   - Download from official dlib website if missing

4. **No sound alert**
   - Check if `alarm.wav` file exists
   - Verify pygame installation and audio drivers

5. **Poor detection accuracy**
   - Ensure good lighting conditions
   - Adjust EAR threshold value
   - Clean camera lens

## 🎯 Applications

- **Driver Monitoring Systems**: Prevent accidents due to driver fatigue
- **Workplace Safety**: Monitor operators in critical environments
- **Medical Monitoring**: Assist in sleep disorder studies
- **Educational Tools**: Demonstrate computer vision concepts

## 📊 Performance Notes

- **Processing Speed**: ~15-30 FPS depending on hardware
- **Accuracy**: ~90-95% in good lighting conditions
- **False Positives**: May occur with glasses, poor lighting, or rapid eye movements

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit changes (`git commit -am 'Add new feature'`)
4. Push to branch (`git push origin feature/improvement`)
5. Create Pull Request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 👥 Authors

- **Team No. 77** - Initial development
- **Indresh** - Project lead and development

## 🙏 Acknowledgments

- **dlib library** - For facial landmark detection
- **OpenCV** - For computer vision operations
- **imutils** - For image processing utilities
- **scipy** - For mathematical computations

## 📞 Support

If you encounter any issues or have questions:
1. Check the troubleshooting section
2. Open an issue on GitHub
3. Contact the development team

---

**⚠️ Safety Notice**: This system is designed for educational and demonstration purposes. For critical safety applications, additional testing and validation are recommended.
