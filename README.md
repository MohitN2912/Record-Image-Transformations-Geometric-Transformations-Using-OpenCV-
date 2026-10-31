# Record-Image-Transformations-Geometric-Transformations-Using-OpenCV-

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
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("mht.png")

if img is None:
    print("Error: Image not found")
    exit()

img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

height, width = img.shape[:2]


translation_matrix = np.float32([
    [1, 0, 50],
    [0, 1, 80]
])

translated = cv2.warpAffine(img, translation_matrix, (width, height))

translated_rgb = cv2.cvtColor(translated, cv2.COLOR_BGR2RGB)


plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(translated_rgb)
plt.title("Translated Image")
plt.axis("off")

plt.show()

downscaled = cv2.resize(img, None, fx=0.5, fy=0.5)

upscaled = cv2.resize(img, None, fx=2, fy=2)


plt.figure(figsize=(12,5))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(downscaled, cv2.COLOR_BGR2RGB))
plt.title("Downscaled 0.5x")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(upscaled, cv2.COLOR_BGR2RGB))
plt.title("Upscaled 2x")
plt.axis("off")

plt.show()

shear_horizontal = np.float32([
    [1, 0.5, 0],
    [0, 1, 0]
])

horizontal_shear = cv2.warpAffine(
    img,
    shear_horizontal,
    (width + int(height*0.5), height)
)


shear_vertical = np.float32([
    [1, 0, 0],
    [0.5, 1, 0]
])

vertical_shear = cv2.warpAffine(
    img,
    shear_vertical,
    (width, height + int(width*0.5))
)


plt.figure(figsize=(12,5))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(horizontal_shear, cv2.COLOR_BGR2RGB))
plt.title("Horizontal Shearing")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(vertical_shear, cv2.COLOR_BGR2RGB))
plt.title("Vertical Shearing")
plt.axis("off")

plt.show()


horizontal_flip = cv2.flip(img, 1)

vertical_flip = cv2.flip(img, 0)

both_flip = cv2.flip(img, -1)


plt.figure(figsize=(12,5))

plt.subplot(1,4,1)
plt.imshow(img_rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(1,4,2)
plt.imshow(cv2.cvtColor(horizontal_flip, cv2.COLOR_BGR2RGB))
plt.title("Horizontal Flip")
plt.axis("off")

plt.subplot(1,4,3)
plt.imshow(cv2.cvtColor(vertical_flip, cv2.COLOR_BGR2RGB))
plt.title("Vertical Flip")
plt.axis("off")

plt.subplot(1,4,4)
plt.imshow(cv2.cvtColor(both_flip, cv2.COLOR_BGR2RGB))
plt.title("Both Axis Flip")
plt.axis("off")

plt.show()


center = (width//2, height//2)


rotation_45_matrix = cv2.getRotationMatrix2D(
    center,
    45,
    1
)

rotated_45 = cv2.warpAffine(
    img,
    rotation_45_matrix,
    (width,height)
)


rotation_90_matrix = cv2.getRotationMatrix2D(
    center,
    90,
    1
)

rotated_90 = cv2.warpAffine(
    img,
    rotation_90_matrix,
    (width,height)
)


plt.figure(figsize=(10,5))

plt.subplot(1,3,1)
plt.imshow(img_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(rotated_45, cv2.COLOR_BGR2RGB))
plt.title("45 Degree Rotation")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(rotated_90, cv2.COLOR_BGR2RGB))
plt.title("90 Degree Rotation")
plt.axis("off")

plt.show()
```

### Developed By:
### **Name: MOHIT N**  

### **Register No: 212225040255**


---

##  Output
### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed



<img width="1146" height="602" alt="image" src="https://github.com/user-attachments/assets/4c48049f-7632-41a0-b1c6-045d2bbd639c" />



### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed  


<img width="1347" height="576" alt="image" src="https://github.com/user-attachments/assets/61426983-abba-4d44-95d4-abbaa4ac957a" />

### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed


  


<img width="1352" height="600" alt="image" src="https://github.com/user-attachments/assets/0d8bf1b8-6c08-4a74-b8ec-348b4a27df73" />



### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed


<img width="1370" height="431" alt="image" src="https://github.com/user-attachments/assets/fdec63d5-63b8-470e-b221-04ed66733b94" />




### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  


<img width="1177" height="486" alt="image" src="https://github.com/user-attachments/assets/e9816704-1485-4737-83cf-24a45162f040" />


---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
