Overview

Face Privacy Layer is a real-time computer vision application that detects faces from a webcam feed and automatically blurs all faces except the primary subject. The primary face is determined based on size and position relative to the center of the frame.

This project is designed to enhance privacy in live video scenarios such as video calls, recordings, or public environments.

Features
Real-time face detection using MediaPipe
Automatic identification of the primary face
Blurring of non-primary faces
Two blur modes:
Gaussian blur
Pixelation
Frame-skipping optimization for improved performance
Live FPS and system information display
Keyboard controls for interaction
How It Works
The webcam captures video frames continuously.
MediaPipe detects faces in selected frames.
Each detected face is scored based on:
Face size (larger faces are prioritized)
Distance from the center (closer faces are prioritized)
The face with the highest score is marked as the primary face.
All other faces are blurred.
The processed frame is displayed in real-time.
Scoring Logic

The primary face is selected using the following formula:

score = area - (PRIMARY_ALPHA × distance_from_center)
Larger faces increase the score.
Faces closer to the center increase the score.
Faces far from the center are penalized.
Requirements
Python 3.x
OpenCV
MediaPipe
Installation
Clone the repository:
git clone https://github.com/your-username/face-privacy-layer.git
cd face-privacy-layer
Install dependencies:
pip install opencv-python mediapipe
Usage

Run the script:

python face_privacy_blur_fixed.py
Controls
Press p to toggle blur mode (Gaussian / Pixel)
Press q or Esc to quit the application
Configuration

You can modify the following parameters in the code:

DETECTION_CONFIDENCE
Minimum confidence required to detect a face
PRIMARY_ALPHA
Weight given to center distance in scoring
BLUR_TYPE
Default blur mode ("gaussian" or "pixel")
DETECT_EVERY_N_FRAMES
Number of frames to skip between detections (higher value improves performance but may reduce accuracy)
Performance Optimization
Face detection is not run on every frame to improve FPS.
Previous detections are reused between frames.
Adjustable detection interval allows balancing between speed and accuracy.
Known Limitations
The primary face may switch if another face becomes larger or more centered.
Frame skipping may cause slight lag or flickering in detection.
No identity recognition; the system does not distinguish between known and unknown faces.
Future Improvements
Face tracking for smoother detection
Identity-based filtering (blur only unknown faces)
Background blur instead of face blur
Multi-person priority selection
Integration with video conferencing tools
License

This project is open-source and available under the MIT License.
