# Real-Time-HandGesture-DigitRecognition-MediaPipe-OpenCV

1. **Importing Libraries**:
    - `cv2`: OpenCV library for computer vision tasks.
    - `mediapipe as mp`: MediaPipe library for hand tracking and gesture recognition.

2. **Constants for Digit-Color Mapping**:
    - `COLORS`: A list of colors, where each color corresponds to a digit from 0 to 10. The colors are represented as tuples of RGB values.
    - `DIGIT_THRESHOLD`: A threshold value for digit recognition based on the Y-coordinate of the index finger tip.

3. **Initializing MediaPipe Hand Tracking**:
    - `mp_hands`: An instance of the MediaPipe Hand Tracking solution.
    - `mp_draw`: Utility functions for drawing landmarks on the image.

4. **Starting Video Capture**:
    - `cap`: A VideoCapture object to capture frames from the default camera (index 0).

5. **Hand Tracking Loop**:
    - The code enters a loop to continuously capture frames from the camera and perform hand tracking.

6. **Processing Each Frame**:
    - Inside the loop, each frame is read from the camera (`cap.read()`), and the success flag indicates whether the frame was read successfully.
    - The frame is then converted from BGR to RGB format (`cv2.cvtColor(image, cv2.COLOR_BGR2RGB)`) as MediaPipe processes RGB images.

7. **Hand Landmark Detection**:
    - The `hands.process()` method detects hand landmarks in the frame using MediaPipe's Hand Tracking solution.
    - If hand landmarks are detected (`results.multi_hand_landmarks`), the code proceeds to analyze the landmarks.

8. **Digit Recognition**:
    - For each detected hand (`for hand_landmarks in results.multi_hand_landmarks`), the Y-coordinate of the index finger tip (`index_finger_tip.y`) is checked against the `DIGIT_THRESHOLD`.
    - If the Y-coordinate is below the threshold, it's mapped to a digit between 0 and 10 (`detected_digit = round(index_finger_tip.y * 10)`).

9. **Drawing Hand Landmarks**:
    - Hand landmarks are drawn on the image using `mp_draw.draw_landmarks()`.

10. **Displaying Digit on Screen**:
    - If a digit is detected (`detected_digit` is not `None`), its corresponding color is retrieved from the `COLORS` list.
    - The digit is then drawn on the image using `cv2.putText()` with the corresponding color.

11. **Displaying the Image**:
    - The processed image with hand landmarks and detected digit is displayed using `cv2.imshow()`.

12. **Exiting the Loop**:
    - The loop continues until the user presses the 'q' key (`if cv2.waitKey(1) == ord('q')`), at which point the loop is exited.

13. **Releasing Resources**:
    - After the loop ends, the video capture object is released (`cap.release()`) and all OpenCV windows are destroyed (`cv2.destroyAllWindows()`).

This code provides a real-time visualization of hand landmarks and recognizes digits based on the movement of the index finger tip.

## Fingertips movement corresponds to the recognition of different digits based on the position of the index finger tip relative to the camera's view.

Here's how the code works:

1. **Hand Tracking**: The code uses MediaPipe's Hand Tracking module to detect and track the landmarks of the hand, including the index finger tip.

2. **Digit Recognition**: The Y-coordinate of the index finger tip is used to determine which digit to recognize. The Y-coordinate is normalized between 0 and 1, where 0 corresponds to the top of the screen and 1 corresponds to the bottom. The code then maps this normalized Y-coordinate to a range of digits (0 to 4 in the provided code).

3. **Color Mapping**: Each recognized digit is associated with a color from the `COLORS` list. For example, digit 0 corresponds to the color `(0, 255, 0)`, digit 1 to `(0, 255, 255)`, and so on.

4. **Displaying Digits**: When a digit is recognized, its corresponding color is retrieved from the `COLORS` list, and the digit is displayed on the screen using OpenCV's `cv2.putText()` function.

Therefore, the movement of fingertips triggers the recognition of different digits, which in turn leads to the display of different colors on the screen based on the recognized digit. 

## The COLORS list now includes 11 colors, corresponding to digits from 0 to 10.

The digit recognition mechanism has been adjusted to round the Y-coordinate of the index finger tip multiplied by 10 to get an integer value between 0 and 10. When a digit is recognized, its corresponding color is retrieved from the COLORS list and used to display the digit on the screen. The code can now recognize and display digits from 0 to 10 based on the movement of the fingertips.

