# SortMate
AI-Powered Smart Waste Sorting Bin
# Our Objectives
Our main objective is to design and build an AI-based smart bin that can detect the type of waste placed on it, sort it into the correct bin automatically, and notify the relevant staff when the bin is full.
# Features
- Real-time waste classification using TensorFlow
- Dual ESP32 architecture for distributed control
- Automated Sorting detects and sorts waste automatically
- Scalable and reprogrammable design for adding new waste types
# Tech Stack
Hardware: ESP32-CAM, ESP32, Servo Motors, Ultrasonic Sensor, LCD Display
Software: TensorFlow, Arduino IDE, Python, Flask
# How it works
The smart waste sorting system uses an ESP32-CAM with an HC-SR04 ultrasonic sensor to detect objects at 4-25 cm. Upon trigger, the OV2640 camera captures VGA JPEG frames, encodes them to base64 MIME-prefixed strings, and POSTs as JSON to a Flask server via WiFi. The Python 3 server employs TensorFlow/Keras and OpenCV to detect and return class and confidence of the captured image.

![esp32_cam_bb](https://github.com/user-attachments/assets/06899733-747a-4dac-868a-d93a3c5f1517)

On the ESP32-CAM, sends the class via ESP-NOW. The receiver ESP32 (WiFi STA + ESP-NOW) handles data in OnDataRecv, mapping to two servo motors physically tilts/rotates the bin to drop the item into the correct compartment.. It displays on LCD, monitors bins with three HC-SR04 and show the bin fill level as a percentage, also provides a web based dashboard for monitoring and manual control.

