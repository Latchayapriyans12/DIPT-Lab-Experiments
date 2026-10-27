# Image-Handling-and-Pixel-Transformations-Using-OpenCV

**Name:** Latchaya Priyan S

**Reg. No:** 212224230139

**EX:** 01

## AIM:

Write a Python program using OpenCV to read and display an image and perform the following operations:

1. Read and display an image.
2. Draw lines, circles, and rectangles on the image.
3. Add text to the image.
4. Convert the image into different colour spaces.
5. Modify selected image pixels.
6. Resize and crop the image.
7. Flip the image horizontally and vertically.

## Software Required:

- Anaconda – Python 3
- Jupyter Notebook
- OpenCV
- NumPy
- Matplotlib

Install the required libraries using:

```bash
pip install opencv-python numpy matplotlib
```

## Algorithm:

### Step 1:

Import the required libraries and read the input image `bmw.png` using OpenCV.

### Step 2:

Display the original image using Matplotlib.

### Step 3:

Draw a line, circle, and rectangle on the image using OpenCV drawing functions.

### Step 4:

Add the text `OpenCV Drawing` to the image and display the result.

### Step 5:

Convert the image into HSV, grayscale, and YCrCb colour spaces.

### Step 6:

Convert the HSV image back to RGB and display the converted image.

### Step 7:

Modify a selected 300 × 300 pixel region by setting its pixel values to white.

### Step 8:

Resize the image to half of its original dimensions.

### Step 9:

Crop a region of interest (ROI) from the original image.

### Step 10:

Flip the image horizontally and vertically and display both results.

## Program Developed By:

- **Name:** Latchaya Priyan S
- **Register Number:** 212224230139
- **Experiment No.:** 01

## Program:

The following program consolidates the image-processing operations demonstrated in the notebook.

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# 1. Read and display the original image
img = cv2.imread('bmw.png', cv2.IMREAD_COLOR)

if img is None:
    raise FileNotFoundError(
        "Could not find bmw.png. Keep it in the notebook folder."
    )

img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis('off')
plt.show()

# 2. Draw a line
line_img = img_rgb.copy()
cv2.line(line_img, (0, 0), (768, 600), (255, 0, 0), 2)

plt.imshow(line_img)
plt.title("Image with Line")
plt.axis('off')
plt.show()

# 3. Draw a circle
circle_img = img_rgb.copy()
cv2.circle(circle_img, (400, 300), 150, (255, 0, 0), 10)

plt.imshow(circle_img)
plt.title("Image with Circle")
plt.axis('off')
plt.show()

# 4. Draw a rectangle
rectangle_img = img_rgb.copy()
cv2.rectangle(
    rectangle_img, (10, 10), (720, 400), (0, 255, 0), 8
)

plt.imshow(rectangle_img)
plt.title("Image with Rectangle")
plt.axis('off')
plt.show()

# 5. Add text to the image
text_img = img_rgb.copy()
cv2.putText(
    text_img,
    "OpenCV Drawing",
    (10, 30),
    cv2.FONT_HERSHEY_SIMPLEX,
    1,
    (255, 255, 255),
    10
)

plt.imshow(text_img)
plt.title("Image with Text")
plt.axis('off')
plt.show()

# 6. Convert the image into different colour spaces
image = cv2.imread('bmw.png')
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis('off')
plt.show()

# RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis('off')
plt.show()

# RGB to Grayscale
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
plt.show()

# RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis('off')
plt.show()

# HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis('off')
plt.show()

# 7. Modify a 300 x 300 pixel region
image = cv2.imread('bmw.png')
image[200:500, 200:500] = [255, 255, 255]

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis('off')
plt.show()

# 8. Resize the image to half its original dimensions
image = cv2.imread('bmw.png')
height, width = image.shape[:2]

resized_image = cv2.resize(
    image, (width // 2, height // 2)
)

resized_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

plt.imshow(resized_rgb)
plt.title("Resized Image (Half Size)")
plt.axis('off')
plt.show()

# 9. Crop a region of interest (ROI)
image = cv2.imread('bmw.png')
roi = image[50:350, 50:350]

roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis('off')
plt.show()

# 10. Flip the image horizontally
image = cv2.imread('bmw.png')
flipped_horizontally = cv2.flip(image, 1)

horizontal_rgb = cv2.cvtColor(
    flipped_horizontally, cv2.COLOR_BGR2RGB
)

plt.imshow(horizontal_rgb)
plt.title("Flipped Horizontally")
plt.axis('off')
plt.show()

# 11. Flip the image vertically
flipped_vertically = cv2.flip(image, 0)

vertical_rgb = cv2.cvtColor(
    flipped_vertically, cv2.COLOR_BGR2RGB
)

plt.imshow(vertical_rgb)
plt.title("Flipped Vertically")
plt.axis('off')
plt.show()

# 12. Display Python and library versions
import sys
import matplotlib

print("Python path:", sys.executable)
print("NumPy:", np.__version__)
print("OpenCV:", cv2.__version__)
print("Matplotlib:", matplotlib.__version__)

plt.imshow(np.zeros((100, 100)), cmap='gray')
plt.title("DIPT Test")
plt.show()
```

## Output Images:

Upload the 16 images into an `outputs` folder beside this README. The following relative links will display them on GitHub.

### 1. Original Image

<img width="518" height="322" alt="image" src="https://github.com/user-attachments/assets/c137a6b8-525d-4af5-bbbd-261805c7c5ce" />

### 2. Image with Line
<img width="527" height="320" alt="image" src="https://github.com/user-attachments/assets/84d74632-53d0-41b3-b96e-ec9de4407a3b" />


### 3. Image with Circle

<img width="530" height="320" alt="image" src="https://github.com/user-attachments/assets/7df18a2b-2f74-4e9b-bb25-1d696ded804f" />

### 4. Image with Rectangle

<img width="530" height="321" alt="image" src="https://github.com/user-attachments/assets/618827c0-85d1-45af-9f70-07848df346bf" />

### 5. Image with Text

<img width="523" height="327" alt="image" src="https://github.com/user-attachments/assets/90b0cbe0-169c-4d24-bb6f-5868c9e0e08e" />

### 6. Original RGB Image

<img width="511" height="322" alt="image" src="https://github.com/user-attachments/assets/2c20f50c-1d18-46c4-a84b-40c5fb972c28" />

### 7. HSV Image

<img width="526" height="323" alt="image" src="https://github.com/user-attachments/assets/b0b7b917-300f-4b36-b28f-52c4e1dbc158" />

### 8. Grayscale Image

<img width="535" height="320" alt="image" src="https://github.com/user-attachments/assets/3c16df85-ef4a-4b32-98f4-7e2d71c55259" />

### 9. YCrCb Image

<img width="527" height="327" alt="image" src="https://github.com/user-attachments/assets/3ed08758-ba7b-406c-8aad-610080126d2c" />

### 10. HSV to RGB Image

<img width="515" height="325" alt="image" src="https://github.com/user-attachments/assets/133b7998-0e50-467a-b190-f435b2c1bba1" />

### 11. Image with 300 × 300 White Block

<img width="531" height="332" alt="image" src="https://github.com/user-attachments/assets/5536ca7a-b69d-4b93-b25f-c6e5ea7c1466" />

### 12. Resized Image (Half Size)

<img width="417" height="415" alt="image" src="https://github.com/user-attachments/assets/8c5c1b8d-fec4-4028-85c5-c310d92897ce" />

### 13. Cropped Region of Interest (ROI)

<img width="496" height="423" alt="image" src="https://github.com/user-attachments/assets/f6abe6e8-dbcd-4f38-9148-ed952bbf5c06" />

### 14. Horizontally Flipped Image

<img width="521" height="323" alt="image" src="https://github.com/user-attachments/assets/a99f99a6-0e37-44e1-b1aa-4c2b5a68d3f8" />

### 15. Vertically Flipped Image

<img width="515" height="322" alt="image" src="https://github.com/user-attachments/assets/c1c9ed1b-f8a1-4c74-92bb-35921f48f0e3" />



## Result:

Thus, the input image was read and displayed, drawing operations and colour-space conversions were performed, selected pixels were modified, and resizing, cropping, and flipping operations were demonstrated successfully using Python and OpenCV.
