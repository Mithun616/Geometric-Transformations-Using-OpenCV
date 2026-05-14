# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program

### Developed By:
**Name:** Mithun Kumar G

### Register No:
212224230160 

```
# Import 
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the image using OpenCV
img = cv2.imread("baseball.jpg")

# Display the image using Matplotlib
plt.imshow(img[:,:,::-1])
plt.title("Original Image")
plt.axis("off")
```
```
# Translation 
M = np.float32([[1, 0, 50],
                [0, 1, 80]])
translated = cv2.warpAffine(img, M, (img.shape[1], img.shape[0]))

# Display original and translated images
plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(img[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(translated[:,:,::-1])
plt.title("Translated Image")
plt.axis("off")

plt.show()
```
```
# Downscale image (0.5x)
small_img = cv2.resize(img, None, fx=0.5, fy=0.5)
# Upscale image (2x)
large_img = cv2.resize(img, None, fx=2, fy=2)

# Display images
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(img[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(small_img[:,:,::-1])
plt.title("Downscaled Image")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(large_img[:,:,::-1])
plt.title("Upscaled Image")
plt.axis("off")

plt.show()
```
```
# Image Shearing
# Get image height and width
h, w = img.shape[:2]
# Horizontal shearing matrix
M1 = np.float32([[1, 0.5, 0],
                 [0, 1, 0]])

# Vertical shearing matrix
M2 = np.float32([[1, 0, 0],
                 [0.5, 1, 0]])

# Apply shearing
h_shear = cv2.warpAffine(img, M1, (w, h))
v_shear = cv2.warpAffine(img, M2, (w, h))

# Display images
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(img[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(h_shear[:,:,::-1])
plt.title("Horizontal Shear")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(v_shear[:,:,::-1])
plt.title("Vertical Shear")
plt.axis("off")

plt.show()
```
```
# Image Reflection
# Horizontal reflection
h_flip = cv2.flip(img, 1)

# Vertical reflection
v_flip = cv2.flip(img, 0)

# Both-axis reflection
hv_flip = cv2.flip(img, -1)
# Display images
plt.figure(figsize=(10,10))

plt.subplot(2,2,1)
plt.imshow(img[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(2,2,2)
plt.imshow(h_flip[:,:,::-1])
plt.title("Horizontal Reflection")
plt.axis("off")

plt.subplot(2,2,3)
plt.imshow(v_flip[:,:,::-1])
plt.title("Vertical Reflection")
plt.axis("off")

plt.subplot(2,2,4)
plt.imshow(hv_flip[:,:,::-1])
plt.title("Both-axis Reflection")
plt.axis("off")

plt.show()
```
```
# Image Rotation
 image height and width
h, w = img.shape[:2]
# Find center of image
center = (w//2, h//2)
# Rotation matrix for 45 degree
M1 = cv2.getRotationMatrix2D(center, 45, 1)
# Rotation matrix for 90 degree
M2 = cv2.getRotationMatrix2D(center, 90, 1)
# Rotate images
rotated_45 = cv2.warpAffine(img, M1, (w, h))
rotated_90 = cv2.warpAffine(img, M2, (w, h))
# Display images
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(img[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(rotated_45[:,:,::-1])
plt.title("45° Rotated Image")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(rotated_90[:,:,::-1])
plt.title("90° Rotated Image")
plt.axis("off")

plt.show()
```
---

##  Output

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed  

### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed  

### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed  

### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed  

### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  

---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
