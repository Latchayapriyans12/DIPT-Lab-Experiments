# Experiment 05: Image Filtering Using OpenCV

**Name:** Latchaya Priyan S  
**Register Number:** 212224230139  
**Experiment Number:** 05

## AIM

To perform different image filtering techniques using OpenCV, including average filtering, weighted average filtering, Gaussian filtering, median filtering, Laplacian filtering, bilateral filtering, box filtering, sharpening, unsharp masking, and high-pass filtering.

## SOFTWARE REQUIRED

- Python
- Jupyter Notebook
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## ALGORITHM

1. Import the required libraries.
2. Read the input image `spi.png`.
3. Convert the image from BGR to RGB and display the original image.
4. Apply an average filter using a convolution kernel.
5. Apply a weighted average filter.
6. Apply Gaussian blur to smooth the image.
7. Apply median filtering to reduce noise.
8. Apply a Laplacian kernel and Laplacian operator to detect image details and edges.
9. Apply bilateral filtering to smooth the image while preserving edges.
10. Apply a box filter and a smaller median filter.
11. Perform unsharp masking to enhance image details.
12. Apply a sharpening kernel to make edges more prominent.
13. Apply high-pass filtering using the difference between the original and Gaussian-blurred images.
14. Display and compare the original and filtered images.

## PROGRAM DEVELOPED BY

**Name:** Latchaya Priyan S  
**Register Number:** 212224230139

## PROGRAM

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the input image
image1 = cv2.imread("spi.png")

if image1 is None:
    print("Image not found. Check the filename.")
else:
    image2 = cv2.cvtColor(image1, cv2.COLOR_BGR2RGB)

    # Original Image
    plt.imshow(image2)
    plt.title("Original Image")
    plt.axis("off")
    plt.show()

    # Average Filter
    kernel = np.ones((11, 11), np.float32) / 121
    average = cv2.filter2D(image2, -1, kernel)

    plt.figure(figsize=(9, 5))
    plt.subplot(1, 2, 1)
    plt.imshow(image2)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 2, 2)
    plt.imshow(average)
    plt.title("Average Filter Image")
    plt.axis("off")
    plt.show()

    # Weighted Average Filter
    kernel1 = np.array([
        [1, 2, 1],
        [2, 4, 2],
        [1, 2, 1]
    ], dtype=np.float32) / 16

    weighted = cv2.filter2D(image2, -1, kernel1)
    plt.imshow(weighted)
    plt.title("Weighted Average Filter Image")
    plt.axis("off")
    plt.show()

    # Gaussian Blur
    gaussian_blur = cv2.GaussianBlur(image2, (33, 33), 0)
    plt.imshow(gaussian_blur)
    plt.title("Gaussian Blur")
    plt.axis("off")
    plt.show()

    # Median Filter
    median = cv2.medianBlur(image2, 13)
    plt.imshow(median)
    plt.title("Median Blur")
    plt.axis("off")
    plt.show()

    # Laplacian Kernel
    kernel2 = np.array([
        [-1, -1, -1],
        [2, -2, 1],
        [2, 1, -1]
    ])

    laplacian_kernel = cv2.filter2D(image2, -1, kernel2)
    plt.imshow(laplacian_kernel)
    plt.title("Laplacian Kernel")
    plt.axis("off")
    plt.show()

    # Laplacian Operator
    laplacian = cv2.Laplacian(image2, cv2.CV_64F)
    laplacian = cv2.convertScaleAbs(laplacian)

    plt.imshow(laplacian)
    plt.title("Laplacian Operator")
    plt.axis("off")
    plt.show()

    # Bilateral Filter
    bilateral = cv2.bilateralFilter(image2, 15, 75, 75)

    plt.figure(figsize=(8, 4))
    plt.subplot(1, 2, 1)
    plt.imshow(image2)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 2, 2)
    plt.imshow(bilateral)
    plt.title("Bilateral Filter")
    plt.axis("off")
    plt.show()

    # Box Filter
    box = cv2.blur(image2, (11, 11))
    plt.imshow(box)
    plt.title("Box Filter")
    plt.axis("off")
    plt.show()

    # Median Filter (3x3)
    median3 = cv2.medianBlur(image2, 3)
    plt.imshow(median3)
    plt.title("Median Filter (3x3)")
    plt.axis("off")
    plt.show()

    # Unsharp Masking
    blur = cv2.GaussianBlur(image2, (5, 5), 0)
    unsharp = cv2.addWeighted(image2, 1.5, blur, -0.5, 0)

    plt.figure(figsize=(8, 4))
    plt.subplot(1, 2, 1)
    plt.imshow(image2)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 2, 2)
    plt.imshow(unsharp)
    plt.title("Unsharp Masking")
    plt.axis("off")
    plt.show()

    # Sharpening Filter
    kernel3 = np.array([
        [0, -1, 0],
        [-1, 5, -1],
        [0, -1, 0]
    ])

    sharpened = cv2.filter2D(image2, -1, kernel3)
    plt.imshow(sharpened)
    plt.title("Sharpening Filter")
    plt.axis("off")
    plt.show()

    # High-Pass Filtering
    blur = cv2.GaussianBlur(image2, (5, 5), 0)
    high_pass = (
        image2.astype(np.float32) -
        blur.astype(np.float32)
    )

    high_pass_display = cv2.normalize(
        np.abs(high_pass),
        None,
        0,
        255,
        cv2.NORM_MINMAX
    ).astype(np.uint8)

    plt.figure(figsize=(12, 4))

    plt.subplot(1, 3, 1)
    plt.imshow(image2)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(1, 3, 2)
    plt.imshow(blur)
    plt.title("Gaussian Blurred Image")
    plt.axis("off")

    plt.subplot(1, 3, 3)
    plt.imshow(high_pass_display)
    plt.title("High-Pass Filter Result")
    plt.axis("off")

    plt.tight_layout()
    plt.show()
```

## OUTPUT

The following results are obtained:

<img width="397" height="417" alt="image" src="https://github.com/user-attachments/assets/cbe9e94e-b1a6-462d-a0c5-e93ee2a4ca4b" />

<img width="627" height="335" alt="image" src="https://github.com/user-attachments/assets/5d8843d0-1114-4ee3-983a-388c8bede205" />

<img width="422" height="420" alt="image" src="https://github.com/user-attachments/assets/6cd4fb33-a3e9-4b8a-a22d-74e502957ea6" />

<img width="373" height="406" alt="image" src="https://github.com/user-attachments/assets/6ac41569-6c58-492a-abc8-a09a2f4063ae" />

<img width="425" height="417" alt="image" src="https://github.com/user-attachments/assets/897356fc-3afe-4047-89b2-2ff5bd4ab046" />

<img width="423" height="417" alt="image" src="https://github.com/user-attachments/assets/007d2e1f-f444-455e-8e86-1c336f67e4c6" />

<img width="417" height="405" alt="image" src="https://github.com/user-attachments/assets/eab636b0-0932-4eab-a113-be1a6915ba44" />

<img width="612" height="562" alt="image" src="https://github.com/user-attachments/assets/b4ac75a4-6433-4d5d-b244-31a27012b657" />

<img width="627" height="227" alt="image" src="https://github.com/user-attachments/assets/e2d96a00-5b2e-4753-ab81-b3a183c5415b" />

<img width="640" height="452" alt="image" src="https://github.com/user-attachments/assets/c6951e41-232e-4df8-8d68-d897ec5df5cb" />

## RESULT

Thus, different image filtering techniques were implemented using Python, OpenCV, NumPy, and Matplotlib. The results demonstrate image smoothing, noise reduction, edge enhancement, sharpening, and high-pass filtering.
