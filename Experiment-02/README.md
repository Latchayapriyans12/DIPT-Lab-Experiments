# Video-Capture-and-Video-Processing-Using-OpenCV

**Name:** Latchaya Priyan S

**Reg. No:** 212224230139

**EX:** 02

## AIM:

Write a Python program using OpenCV to perform the following operations:

1. Capture a frame from the webcam and save it as a JPG image.
2. Read and display the captured image.
3. Display live video using the webcam.
4. Display the video after resizing the frame.
5. Rotate and display the video.

## Software Required:

- Anaconda – Python 3
- Jupyter Notebook
- OpenCV
- Matplotlib
- IPython

Install the required libraries using:

```bash
pip install opencv-python matplotlib
```

## Algorithm:

### Step 1:

Import the required libraries, including OpenCV, Matplotlib, IPython, and the `time` module.

### Step 2:

Access the webcam using `cv2.VideoCapture(0)` and capture a frame.

### Step 3:

Save the captured frame as `captured_frame.jpg` using `cv2.imwrite()`.

### Step 4:

Read the saved image using `cv2.imread()` and display it using Matplotlib.

### Step 5:

Capture and display live video frames from the webcam. Convert each frame from BGR to RGB before displaying it.

### Step 6:

Resize each video frame to 320 × 240 pixels using `cv2.resize()` and display the resized video.

### Step 7:

Rotate each video frame by 90 degrees clockwise using `cv2.rotate()` and display the rotated video.

### Step 8:

Release the webcam after completing each operation.

## Program Developed By:

- **Name:** Latchaya Priyan S
- **Register Number:** 212224230139
- **Experiment No.:** 02

## Program:

```python
# Import the required libraries
import cv2
import matplotlib.pyplot as plt
from IPython.display import clear_output
import time

# 1. Capture and save a frame as a JPG file
cap = cv2.VideoCapture(0)

ret, frame = cap.read()

if ret:
    cv2.imwrite("captured_frame.jpg", frame)
    print("Image saved successfully")
else:
    print("Unable to capture image. Check the webcam.")

cap.release()

# 2. Read and display the captured image
captured_image = cv2.imread("captured_frame.jpg")

if captured_image is not None:
    plt.imshow(cv2.cvtColor(captured_image, cv2.COLOR_BGR2RGB))
    plt.title("Captured Frame")
    plt.axis("off")
    plt.show()

# 3. Display the live video
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()

    if not ret:
        break

    frame_rgb = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)

    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.title("Live Video")
    plt.axis("off")
    plt.show()

    time.sleep(0.05)

cap.release()

# 4. Display the video after resizing the frame
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()

    if not ret:
        break

    resized_frame = cv2.resize(frame, (320, 240))
    frame_rgb = cv2.cvtColor(resized_frame, cv2.COLOR_BGR2RGB)

    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.title("Resized Video")
    plt.axis("off")
    plt.show()

    time.sleep(0.05)

cap.release()

# 5. Rotate and display the video
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()

    if not ret:
        break

    rotated_frame = cv2.rotate(
        frame, cv2.ROTATE_90_CLOCKWISE
    )

    frame_rgb = cv2.cvtColor(rotated_frame, cv2.COLOR_BGR2RGB)

    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.title("Rotated Video")
    plt.axis("off")
    plt.show()

    time.sleep(0.05)

cap.release()
```

## Output:

### 1. Captured Frame

<img width="505" height="370" alt="image" src="https://github.com/user-attachments/assets/343a4047-2629-4a96-b49c-7295b8602614" />

### 2. Live Video

<img width="530" height="417" alt="image" src="https://github.com/user-attachments/assets/f4ba9283-1949-424f-a65e-144f4cc4ceb5" />

### 3. Resized Video

<img width="642" height="417" alt="image" src="https://github.com/user-attachments/assets/ec1cec55-3042-4f99-8014-a196708e3806" />

### 4. Rotated Video

<img width="326" height="430" alt="image" src="https://github.com/user-attachments/assets/1a803787-2d63-49ea-b276-5de80ee9c174" />


## Result:

Thus, a webcam frame was captured and saved as a JPG image, and video display, resizing, and rotation operations were implemented using Python and OpenCV.
