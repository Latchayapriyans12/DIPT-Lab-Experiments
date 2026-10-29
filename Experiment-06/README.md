# Experiment 06: Edge Detection Techniques Using OpenCV

**Name:** Latchaya Priyan S  
**Register Number:** 212224230139  
**Experiment Number:** 06

## AIM

To implement and compare different edge detection techniques, including Sobel, Prewitt, Roberts, Laplacian, and Canny, using Python and OpenCV.

## SOFTWARE REQUIRED

- Python
- Jupyter Notebook
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## ALGORITHM

1. Import the required libraries.
2. Read the input image `edge.png`.
3. Convert the original image into grayscale.
4. Display the original and grayscale images.
5. Apply the Sobel operator to detect horizontal and vertical edges.
6. Apply the Prewitt operator using horizontal and vertical kernels.
7. Apply the Roberts operator using two 2 × 2 kernels.
8. Apply the Laplacian operator to detect rapid intensity changes.
9. Apply the Canny edge detector with threshold values 50 and 150.
10. Display all the edge detection results together for comparison.
11. Save the output images using `cv2.imwrite()`.
12. Display a message confirming that the output images have been saved.

## PROGRAM DEVELOPED BY

**Name:** Latchaya Priyan S  
**Register Number:** 212224230139

## PROGRAM

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the input image
image = cv2.imread("edge.png")

if image is None:
    raise ValueError("Image not found. Check the filename and path.")

# Convert to grayscale
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

print("Image loaded successfully")
print("Image shape:", image.shape)

# Display original and grayscale images
plt.figure(figsize=(10, 4))

plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(gray, cmap="gray")
plt.title("Grayscale Image")
plt.axis("off")

plt.tight_layout()
plt.show()

# Sobel Edge Detection
sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)

sobel = cv2.magnitude(sobel_x, sobel_y)
sobel = cv2.normalize(sobel, None, 0, 255, cv2.NORM_MINMAX)
sobel = sobel.astype(np.uint8)

plt.imshow(sobel, cmap="gray")
plt.title("Sobel Edge Detection")
plt.axis("off")
plt.show()

# Prewitt Edge Detection
prewitt_x_kernel = np.array([
    [-1, 0, 1],
    [-1, 0, 1],
    [-1, 0, 1]
], dtype=np.float32)

prewitt_y_kernel = np.array([
    [-1, -1, -1],
    [0, 0, 0],
    [1, 1, 1]
], dtype=np.float32)

prewitt_x = cv2.filter2D(
    gray.astype(np.float32), -1, prewitt_x_kernel
)
prewitt_y = cv2.filter2D(
    gray.astype(np.float32), -1, prewitt_y_kernel
)

prewitt = cv2.magnitude(prewitt_x, prewitt_y)
prewitt = cv2.normalize(prewitt, None, 0, 255, cv2.NORM_MINMAX)
prewitt = prewitt.astype(np.uint8)

plt.imshow(prewitt, cmap="gray")
plt.title("Prewitt Edge Detection")
plt.axis("off")
plt.show()

# Roberts Edge Detection
roberts_x_kernel = np.array([
    [1, 0],
    [0, -1]
], dtype=np.float32)

roberts_y_kernel = np.array([
    [0, 1],
    [-1, 0]
], dtype=np.float32)

roberts_x = cv2.filter2D(
    gray.astype(np.float32), -1, roberts_x_kernel
)
roberts_y = cv2.filter2D(
    gray.astype(np.float32), -1, roberts_y_kernel
)

roberts = cv2.magnitude(roberts_x, roberts_y)
roberts = cv2.normalize(roberts, None, 0, 255, cv2.NORM_MINMAX)
roberts = roberts.astype(np.uint8)

plt.imshow(roberts, cmap="gray")
plt.title("Roberts Edge Detection")
plt.axis("off")
plt.show()

# Laplacian Edge Detection
laplacian = cv2.Laplacian(gray, cv2.CV_64F, ksize=3)
laplacian = np.abs(laplacian)
laplacian = cv2.normalize(
    laplacian, None, 0, 255, cv2.NORM_MINMAX
)
laplacian = laplacian.astype(np.uint8)

plt.imshow(laplacian, cmap="gray")
plt.title("Laplacian Edge Detection")
plt.axis("off")
plt.show()

# Canny Edge Detection
canny = cv2.Canny(gray, 50, 150)

plt.imshow(canny, cmap="gray")
plt.title("Canny Edge Detection")
plt.axis("off")
plt.show()

# Display all results together
titles = [
    "Original Image",
    "Sobel",
    "Prewitt",
    "Roberts",
    "Laplacian",
    "Canny"
]

images = [
    cv2.cvtColor(image, cv2.COLOR_BGR2RGB),
    sobel,
    prewitt,
    roberts,
    laplacian,
    canny
]

plt.figure(figsize=(14, 9))

for i in range(6):
    plt.subplot(2, 3, i + 1)

    if i == 0:
        plt.imshow(images[i])
    else:
        plt.imshow(images[i], cmap="gray")

    plt.title(titles[i])
    plt.axis("off")

plt.tight_layout()
plt.show()

# Save the output images
cv2.imwrite("sobel_output.png", sobel)
cv2.imwrite("prewitt_output.png", prewitt)
cv2.imwrite("roberts_output.png", roberts)
cv2.imwrite("laplacian_output.png", laplacian)
cv2.imwrite("canny_output.png", canny)

print("All edge detection images saved successfully.")
```

## OUTPUT

The program produces the following outputs:

1. Original image.
2. Grayscale image.
3. Sobel edge detection.
4. Prewitt edge detection.
5. Roberts edge detection.
6. Laplacian edge detection.
7. Canny edge detection.
8. A combined comparison of the original image and all five edge detection results.

The output images are saved as:

- `sobel_output.png`
- `prewitt_output.png`
- `roberts_output.png`
- `laplacian_output.png`
- `canny_output.png`

## RESULT

Thus, Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques were implemented using Python and OpenCV. The results were displayed and compared to identify edges and boundaries in the image.
