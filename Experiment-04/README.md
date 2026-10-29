# Experiment 04: Geometric Transformations of Images Using OpenCV

**Name:** Latchaya Priyan S  
**Register Number:** 212224230139  
**Experiment:** 04

## AIM
To perform geometric transformations on an image using OpenCV, including translation, scaling, shearing, reflection, rotation, and cropping.

## SOFTWARE REQUIRED
- Python
- Jupyter Notebook
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## ALGORITHM
1. Import the required libraries.
2. Read and display the original image `b.png`.
3. Perform image translation by shifting the image horizontally and vertically.
4. Perform image scaling by increasing the image dimensions.
5. Apply shearing using a transformation matrix.
6. Reflect the image using the OpenCV flip function.
7. Rotate the image by 45 degrees around its center.
8. Crop a selected region from the original image.
9. Display the output of each transformation.
10. Verify the results.

## PROGRAM DEVELOPED BY
**Name:** Latchaya Priyan S  
**Register Number:** 212224230139

## PROGRAM

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load the image
image = cv2.imread('b.png')

if image is None:
    print("Error: Image not found")
else:
    # Display the original image
    plt.figure()
    plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
    plt.title("Original Image")
    plt.axis('off')
    plt.show()

    # Step 2: Image Translation
    tx, ty = 100, 50
    M_translation = np.float32([
        [1, 0, tx],
        [0, 1, ty]
    ])
    translated_image = cv2.warpAffine(
        image, M_translation,
        (image.shape[1], image.shape[0])
    )

    plt.figure()
    plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))
    plt.title("Translated Image")
    plt.axis('off')
    plt.show()

    # Step 3: Image Scaling
    fx, fy = 5.0, 2.0
    scaled_image = cv2.resize(
        image, None, fx=fx, fy=fy,
        interpolation=cv2.INTER_LINEAR
    )

    plt.figure()
    plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))
    plt.title("Scaled Image")
    plt.axis('off')
    plt.show()

    # Step 4: Image Shearing
    shear_matrix = np.float32([
        [1, 0.5, 0],
        [0.5, 1, 0]
    ])
    sheared_image = cv2.warpAffine(
        image, shear_matrix,
        (image.shape[1], image.shape[0])
    )

    plt.figure()
    plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))
    plt.title("Sheared Image")
    plt.axis('off')
    plt.show()

    # Step 5: Image Reflection
    reflected_image = cv2.flip(image, 2)

    plt.figure()
    plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))
    plt.title("Reflected Image")
    plt.axis('off')
    plt.show()

    # Step 6: Image Rotation
    height, width = image.shape[:2]
    angle = 45
    center = (width // 2, height // 2)

    M_rotation = cv2.getRotationMatrix2D(
        center, angle, 1
    )
    rotated_image = cv2.warpAffine(
        image, M_rotation, (width, height)
    )

    plt.figure()
    plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))
    plt.title("Rotated Image")
    plt.axis('off')
    plt.show()

    # Step 7: Image Cropping
    x, y, w, h = 100, 100, 200, 150
    cropped_image = image[y:y+h, x:x+w]

    plt.figure()
    plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))
    plt.title("Cropped Image")
    plt.axis('off')
    plt.show()
```

## OUTPUT

The following outputs are obtained by executing the program:

1. **Original Image:** Displays the input image.
2. **Translated Image:** Shifts the image 100 pixels horizontally and 50 pixels vertically.
3. **Scaled Image:** Enlarges the image by a factor of 5 horizontally and 2 vertically.
4. **Sheared Image:** Applies horizontal and vertical shearing.
5. **Reflected Image:** Displays the reflected image.
6. **Rotated Image:** Rotates the image by 45 degrees.
7. **Cropped Image:** Displays the selected region of size 200 × 150 pixels, starting at coordinates (100, 100), provided the region lies within the image boundaries.

## RESULT

Thus, the geometric transformations of an image, including translation, scaling, shearing, reflection, rotation, and cropping, were performed successfully using Python and OpenCV.
