# Experiment 07: Line Detection Using Hough Transform

## Aim
To detect straight lines in an image using the Hough Transform technique in OpenCV.

## Software Requirements
- Python
- OpenCV (`cv2`)
- NumPy
- Matplotlib
- Jupyter Notebook / Google Colab

## Input Image
`Qn_7_.jpg`

Name: Latchaya Priyan S
Register Number: 212224230139

## Algorithm
1. Import the required libraries: OpenCV, NumPy, and Matplotlib.
2. Load the input image using `cv2.imread()`.
3. Convert the original image into a grayscale image using `cv2.cvtColor()`.
4. Display the original and grayscale images.
5. Apply the Canny edge detector using `cv2.Canny()` with threshold values 50 and 150.
6. Detect line coordinates using the Probabilistic Hough Line Transform (`cv2.HoughLinesP()`).
7. Use a `for` loop to extract the endpoints of the detected lines.
8. Draw the detected lines on the original image using `cv2.line()`.
9. Display the final image containing the detected lines.

## Python Program

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load the input image
image = cv2.imread('Qn_7_.jpg')

# Convert the image to grayscale
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Display the input image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Input Image")
plt.axis('off')
plt.show()

# Display the grayscale image
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
plt.show()

# Detect edges using Canny edge detector
edges = cv2.Canny(gray_image, 50, 150)

# Display Canny edge detector output
plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')
plt.show()

# Detect lines using HoughLinesP()
lines = cv2.HoughLinesP(
    edges, 1, np.pi / 180, 100,
    minLineLength=50, maxLineGap=10
)

# Draw detected lines on the original image
if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line.flatten()
        cv2.line(image, (x1, y1), (x2, y2), (0, 255, 0), 2)
else:
    print("No lines detected")

# Display the result of Hough Transform
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Result of Hough Transform")
plt.axis('off')
plt.show()
```

## Output
<img width="593" height="387" alt="image" src="https://github.com/user-attachments/assets/f318c3ae-0f11-4150-a8c8-314f59c97577" />

<img width="602" height="391" alt="image" src="https://github.com/user-attachments/assets/dda141a9-016e-4355-8dee-af361f006799" />

<img width="567" height="416" alt="image" src="https://github.com/user-attachments/assets/655d55a1-3806-406f-a084-27b35074e8eb" />

<img width="557" height="386" alt="image" src="https://github.com/user-attachments/assets/625f3881-8a8a-4920-b8f0-7788eeef612a" />

## Result
Thus, straight lines in the input image were detected successfully using Canny edge detection and the Probabilistic Hough Transform in OpenCV.
