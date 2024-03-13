# Real-Time-HandGesture-DigitRecognition-MediaPipe-OpenCV

This Python script performs real-time digit detection based on the position of the index finger tip using MediaPipe Hands and OpenCV.

Here's a breakdown of what the script does:

1. It defines constants for digit-color mapping and a threshold value for detecting the top of the frame as a digit.

2. The script initializes MediaPipe Hands and drawing utilities.

3. It starts video capture from the default camera.

4. Within the main loop:
   - It reads frames from the camera and processes them using MediaPipe Hands.
   - The detected hand landmarks are used to determine the position of the index finger tip.
   - If the index finger tip is located close to the top of the frame, it is considered a digit, and the corresponding color is assigned.
   - Hand landmarks are drawn on the frame for visualization (optional).
   - The detected digit is displayed on the frame.

5. The loop continues until the user presses the 'q' key to exit.

6. Finally, it releases the camera and closes all OpenCV windows.

This script demonstrates a simple application of hand landmark detection for digit recognition in real-time video streams. It can serve as a foundation for building more complex gesture-based interfaces or interactive applications. 
