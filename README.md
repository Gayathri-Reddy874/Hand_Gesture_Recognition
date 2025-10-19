# Hand_Gesture_Recognition
This project focuses on developing an intelligent hand gesture–controlled brightness adjustment system using Python, OpenCV, and MediaPipe. The system aims to provide a seamless and touch-free way to control screen brightness by detecting and analyzing hand movements in real time through a webcam.

The project employs computer vision and machine learning–based hand tracking techniques to identify specific finger landmarks. MediaPipe, a powerful framework by Google, is used for accurate hand and finger detection. OpenCV handles real-time video capture and image processing, while the Screen Brightness Control (SBC) library allows direct manipulation of the system’s brightness levels.

The workflow begins by initializing the webcam to capture live video frames. Each frame is processed to detect the position of the hand landmarks using MediaPipe’s Hands module. Once the hand is detected, the coordinates of the thumb tip (landmark 4) and index finger tip (landmark 8) are extracted. The distance between these two points is calculated using the Euclidean distance formula (hypot).

This distance acts as a control parameter — when the fingers move closer together, brightness decreases; when they move farther apart, brightness increases. To ensure smooth scaling, the system uses NumPy’s interpolation function to map the hand distance range (e.g., 15–220 pixels) to a brightness range (0–100%). The adjusted brightness value is then sent to the SBC library to update the screen brightness dynamically.

The system also provides real-time visual feedback by drawing lines and circles between the thumb and index finger, helping users understand how their gestures are being interpreted. The application continues running until the user presses the “q” key to quit.

This project demonstrates the integration of computer vision, gesture recognition, and human-computer interaction (HCI) principles. It can be extended to control other system settings like volume or media playback. The solution is especially useful for accessibility, automation, and smart device control applications.

By bridging vision-based interaction and real-time control, this project offers a modern, efficient, and user-friendly approach to system brightness management.
