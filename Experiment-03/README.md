# Histogram-Equalization-and-RGB-Channel-Analysis-Using-OpenCV

**Name:** Latchaya Priyan S

**Reg. No:** 212224230139

**EX:** 03

## AIM:

Write a Python program using OpenCV, NumPy, and Matplotlib to perform the following operations:

1. Read and display a grayscale image.
2. Plot the original grayscale histogram.
3. Perform histogram equalization and display the equalized image and histogram.
4. Perform histogram equalization on a colour image using the HSV colour space.
5. Separate the RGB channels and display each channel.
6. Plot individual and combined RGB histograms.
7. Display the red, green, and blue colour components.

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

Import OpenCV, NumPy, and Matplotlib.

### Step 2:

Read the image `mtl.jpeg` in grayscale and display it.

### Step 3:

Calculate and display the original grayscale histogram using `plt.hist()`.

### Step 4:

Apply histogram equalization using `cv2.equalizeHist()` and display the equalized histogram and image.

### Step 5:

Read the image in colour and convert it from BGR to RGB for display.

### Step 6:

Convert the colour image from RGB to HSV and apply histogram equalization to the Value (V) channel.

### Step 7:

Convert the equalized HSV image back to BGR and compare it with the original colour image.

### Step 8:

Separate the RGB image into Red, Green, and Blue channels using `cv2.split()`.

### Step 9:

Plot the individual histograms of the Red, Green, and Blue channels.

### Step 10:

Display the combined RGB histogram and compare the original image with its individual colour channels.

### Step 11:

Create and display the red, green, and blue colour components separately.

## Program Developed By:

- **Name:** Latchaya Priyan S
- **Register Number:** 212224230139
- **Experiment No.:** 03

## Program:

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# 1. Read and display the original grayscale image
img = cv2.imread('mtl.jpeg', cv2.IMREAD_GRAYSCALE)

if img is None:
    raise FileNotFoundError("Image mtl.jpeg not found")

plt.imshow(img, cmap='gray')
plt.title('Original Grayscale Image')
plt.axis('off')
plt.show()

# 2. Display the original grayscale histogram
plt.hist(img.ravel(), 256, range=[0, 256])
plt.title('Original Grayscale Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.show()

# 3. Perform histogram equalization
img_eq = cv2.equalizeHist(img)

# Display the equalized histogram
plt.hist(img_eq.ravel(), 256, range=[0, 256])
plt.title('Equalized Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.show()

# Display the equalized grayscale image
plt.imshow(img_eq, cmap='gray')
plt.title('Equalized Grayscale Image')
plt.axis('off')
plt.show()

# 4. Read and display the original colour image
img_color = cv2.imread('mtl.jpeg', cv2.IMREAD_COLOR)

if img_color is None:
    raise FileNotFoundError("Image mtl.jpeg not found")

img_hsv = cv2.cvtColor(img_color, cv2.COLOR_BGR2HSV)

plt.imshow(cv2.cvtColor(img_color, cv2.COLOR_BGR2RGB))
plt.title('Original Color Image')
plt.axis('off')
plt.show()

# 5. Equalize the Value channel in HSV
img_hsv[:, :, 2] = cv2.equalizeHist(img_hsv[:, :, 2])

# Convert the equalized HSV image back to BGR
img_eq_color = cv2.cvtColor(img_hsv, cv2.COLOR_HSV2BGR)

# Compare original and equalized colour images
plt.figure(figsize=(10, 5))

plt.subplot(121)
plt.imshow(cv2.cvtColor(img_color, cv2.COLOR_BGR2RGB))
plt.title('Original Color Image')
plt.axis('off')

plt.subplot(122)
plt.imshow(cv2.cvtColor(img_eq_color, cv2.COLOR_BGR2RGB))
plt.title('Equalized Color Image')
plt.axis('off')

plt.tight_layout()
plt.show()

# 6. Compare images and grayscale histograms
plt.figure(figsize=(12, 10))

plt.subplot(221)
plt.imshow(cv2.cvtColor(img_color, cv2.COLOR_BGR2RGB))
plt.title('Original Color Image')
plt.axis('off')

plt.subplot(222)
plt.imshow(cv2.cvtColor(img_eq_color, cv2.COLOR_BGR2RGB))
plt.title('Equalized Color Image')
plt.axis('off')

plt.subplot(223)
plt.hist(
    cv2.cvtColor(img_color, cv2.COLOR_BGR2GRAY).ravel(),
    256, range=[0, 256]
)
plt.title('Original Grayscale Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')

plt.subplot(224)
plt.hist(
    cv2.cvtColor(img_eq_color, cv2.COLOR_BGR2GRAY).ravel(),
    256, range=[0, 256]
)
plt.title('Equalized Grayscale Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')

plt.tight_layout()
plt.show()

# 7. Read and display the RGB image
img = cv2.imread('mtl.jpeg')
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.imshow(img_rgb)
plt.title('Original RGB Image')
plt.axis('off')
plt.show()

# 8. Split the RGB channels
R, G, B = cv2.split(img_rgb)

plt.figure(figsize=(12, 4))

plt.subplot(131)
plt.imshow(R, cmap='gray')
plt.title('Red Channel')
plt.axis('off')

plt.subplot(132)
plt.imshow(G, cmap='gray')
plt.title('Green Channel')
plt.axis('off')

plt.subplot(133)
plt.imshow(B, cmap='gray')
plt.title('Blue Channel')
plt.axis('off')

plt.tight_layout()
plt.show()

# 9. Display individual RGB histograms
plt.figure(figsize=(10, 5))
plt.hist(R.ravel(), 256, range=(0, 256), color='red')
plt.title('Red Channel Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.show()

plt.figure(figsize=(10, 5))
plt.hist(G.ravel(), 256, range=(0, 256), color='green')
plt.title('Green Channel Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.show()

plt.figure(figsize=(10, 5))
plt.hist(B.ravel(), 256, range=(0, 256), color='blue')
plt.title('Blue Channel Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.show()

# 10. Display the combined RGB histogram
plt.figure(figsize=(12, 5))

plt.hist(
    R.ravel(), 256, range=(0, 256),
    color='red', alpha=0.5, label='Red'
)
plt.hist(
    G.ravel(), 256, range=(0, 256),
    color='green', alpha=0.5, label='Green'
)
plt.hist(
    B.ravel(), 256, range=(0, 256),
    color='blue', alpha=0.5, label='Blue'
)

plt.title('Combined RGB Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.legend()
plt.show()

# 11. Display the original image and RGB channels
plt.figure(figsize=(12, 8))

plt.subplot(221)
plt.imshow(img_rgb)
plt.title('Original RGB Image')
plt.axis('off')

plt.subplot(222)
plt.imshow(R, cmap='gray')
plt.title('Red Channel')
plt.axis('off')

plt.subplot(223)
plt.imshow(G, cmap='gray')
plt.title('Green Channel')
plt.axis('off')

plt.subplot(224)
plt.imshow(B, cmap='gray')
plt.title('Blue Channel')
plt.axis('off')

plt.tight_layout()
plt.show()

# 12. Display individual colour components
zeros = np.zeros_like(R)

red_img = cv2.merge([R, zeros, zeros])
green_img = cv2.merge([zeros, G, zeros])
blue_img = cv2.merge([zeros, zeros, B])

plt.figure(figsize=(12, 4))

plt.subplot(131)
plt.imshow(red_img)
plt.title('Red Component')
plt.axis('off')

plt.subplot(132)
plt.imshow(green_img)
plt.title('Green Component')
plt.axis('off')

plt.subplot(133)
plt.imshow(blue_img)
plt.title('Blue Component')
plt.axis('off')

plt.tight_layout()
plt.show()
```

## Output:

### 1. Original Grayscale Image

<img width="652" height="463" alt="image" src="https://github.com/user-attachments/assets/ced1f860-d291-416d-84ec-d64a7d5fbb41" />

### 2. Original Grayscale Histogram

<img width="622" height="462" alt="image" src="https://github.com/user-attachments/assets/1572401b-c639-46a4-b2b0-9191ba7c6994" />

### 3. Equalized Histogram

<img width="610" height="230" alt="image" src="https://github.com/user-attachments/assets/5c5c1c04-0a5d-4ccf-9517-acff6ab2db66" />

### 4. Equalized Grayscale Image

<img width="532" height="378" alt="image" src="https://github.com/user-attachments/assets/14b0ce7e-f198-42a7-af20-b1e65b38bc0a" />

### 5. Original Colour Image

<img width="551" height="380" alt="image" src="https://github.com/user-attachments/assets/b2ca8faf-78ab-449c-adf7-384afa949505" />

### 6. Equalized Colour Image

<img width="632" height="501" alt="image" src="https://github.com/user-attachments/assets/51a85c96-ceb9-42ab-86fb-635ab2c04b6d" />

### 7. Original and Equalized Grayscale Histograms

<img width="632" height="501" alt="image" src="https://github.com/user-attachments/assets/62b3ea5f-a389-47a6-9418-c80624229d7f" />


### 8. Original RGB Image
<img width="557" height="383" alt="image" src="https://github.com/user-attachments/assets/90bece7a-7d89-465a-bc7d-649c8f6f8eb3" />


### 9. Red, Green, and Blue Channels

<img width="622" height="161" alt="image" src="https://github.com/user-attachments/assets/f30bf44c-1fae-4f28-91ad-d0ac6b612a58" />

### 10. Individual RGB Histograms

<img width="645" height="326" alt="image" src="https://github.com/user-attachments/assets/d90a3737-075c-4384-9e9a-d6fe18c75f9c" />

<img width="625" height="457" alt="image" src="https://github.com/user-attachments/assets/8df6c122-296a-41c7-b6f9-9aadd13ed22c" />

<img width="630" height="452" alt="image" src="https://github.com/user-attachments/assets/6b5984a2-12b5-4f7f-b23b-e5f33136032d" />

### 11. Combined RGB Histogram

<img width="675" height="286" alt="image" src="https://github.com/user-attachments/assets/6843d288-b1e4-4308-aa36-b9acb393de0c" />

### 12. RGB Channel Comparison

<img width="635" height="445" alt="image" src="https://github.com/user-attachments/assets/1adba94b-76e0-45a9-918a-4709a42724cd" />

### 13. Individual Colour Components

<img width="638" height="153" alt="image" src="https://github.com/user-attachments/assets/03fd155f-7f32-4a46-ba1c-9a4debefc717" />

## Result:

Thus, histogram equalization was performed on grayscale and colour images, and the RGB channels and their histograms were analysed using Python, OpenCV, NumPy, and Matplotlib.
