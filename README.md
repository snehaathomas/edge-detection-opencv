# edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Developed By

- **Name:** Sneha Sara Thomas
- **Register No:** 212225230269  

```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

```
image = cv2.imread("lilly.jpg")
```

```
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
```

```
sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)
sobel = cv2.magnitude(sobel_x, sobel_y)
sobel = cv2.convertScaleAbs(sobel)
```

```
prewitt_x = np.array([
    [-1, 0, 1],
    [-1, 0, 1],
    [-1, 0, 1]
])
prewitt_y = np.array([
    [-1, -1, -1],
    [0, 0, 0],
    [1, 1, 1]
])

prewitt_x_result = cv2.filter2D(gray, cv2.CV_64F, prewitt_x)
prewitt_y_result = cv2.filter2D(gray, cv2.CV_64F, prewitt_y)
prewitt = cv2.magnitude(prewitt_x_result, prewitt_y_result)
prewitt = cv2.convertScaleAbs(prewitt)
```

```
roberts_x = np.array([
    [1, 0],
    [0, -1]
])

roberts_y = np.array([
    [0, 1],
    [-1, 0]
])

roberts_x_result = cv2.filter2D(gray, cv2.CV_64F, roberts_x)
roberts_y_result = cv2.filter2D(gray, cv2.CV_64F, roberts_y)
roberts = cv2.magnitude(roberts_x_result, roberts_y_result)
roberts = cv2.convertScaleAbs(roberts)
```

```
laplacian = cv2.Laplacian(gray, cv2.CV_64F)
laplacian = cv2.convertScaleAbs(laplacian)
```

```
canny = cv2.Canny(gray, 100, 200)
```

```
plt.figure(figsize=(12, 8))

plt.subplot(2, 3, 1)
plt.imshow(gray, cmap="gray")
plt.title("Original Grayscale")
plt.axis("off")

plt.subplot(2, 3, 2)
plt.imshow(sobel, cmap="gray")
plt.title("Sobel")
plt.axis("off")

plt.subplot(2, 3, 3)
plt.imshow(prewitt, cmap="gray")
plt.title("Prewitt")
plt.axis("off")

plt.subplot(2, 3, 4)
plt.imshow(roberts, cmap="gray")
plt.title("Roberts")
plt.axis("off")

plt.subplot(2, 3, 5)
plt.imshow(laplacian, cmap="gray")
plt.title("Laplacian")
plt.axis("off")

plt.subplot(2, 3, 6)
plt.imshow(canny, cmap="gray")
plt.title("Canny")
plt.axis("off")

plt.tight_layout()
```


---

## Output

<img width="218" height="418" alt="image" src="https://github.com/user-attachments/assets/3138a3f4-f380-4228-b7bc-35e1839ef30b" />


###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map

<img width="227" height="423" alt="image" src="https://github.com/user-attachments/assets/d6f98de8-9362-4604-b305-8efe91b8a978" />


###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges  

<img width="220" height="418" alt="image" src="https://github.com/user-attachments/assets/12534652-45e9-4771-bfb1-53aa5040fdba" />


###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise

<img width="234" height="419" alt="image" src="https://github.com/user-attachments/assets/d2df8dd4-ef4c-43b6-b23c-dbcc376da1fc" />
  

###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes

<img width="211" height="412" alt="image" src="https://github.com/user-attachments/assets/328ea71d-bfb3-4b5c-82b0-ee54c06606f1" />
  

###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges

<img width="209" height="418" alt="image" src="https://github.com/user-attachments/assets/098d221d-524e-4841-ab94-f850ff01015d" />


---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
