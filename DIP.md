# Practical 1 : Perform image filtering using Fourier Transform (Low-Pass & High-Pass Filtering).

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load image in grayscale
img = cv2.imread('demo_image.jpg', 0)

# Step 2: Perform Fourier Transform
f = np.fft.fft2(img)
fshift = np.fft.fftshift(f)

# Step 3: Create mask for Low-Pass Filter (LPF)
rows, cols = img.shape
crow, ccol = rows // 2, cols // 2
mask = np.zeros((rows, cols), np.uint8)
r = 50
cv2.circle(mask, (ccol, crow), r, 1, thickness=-1)

# Step 4: Apply LPF
fshift_lpf = fshift * mask
lpf_img = np.fft.ifft2(np.fft.ifftshift(fshift_lpf))
lpf_img = np.abs(lpf_img)

# Step 5: Create mask for High-Pass Filter (HPF)
mask_hpf = 1 - mask

# Step 6: Apply HPF
fshift_hpf = fshift * mask_hpf
hpf_img = np.fft.ifft2(np.fft.ifftshift(fshift_hpf))
hpf_img = np.abs(hpf_img)

# Step 7: Display results
plt.figure(figsize=(12, 8))
plt.subplot(1, 3, 1)
plt.imshow(img, cmap='gray')
plt.title('Original Image')

plt.subplot(1, 3, 2)
plt.imshow(lpf_img, cmap='gray')
plt.title('Low-Pass Filtered Image (Blurred)')
plt.subplot(1, 3, 3)
plt.imshow(hpf_img, cmap='gray')
plt.title('High-Pass Filtered Image (Edges)')
plt.tight_layout()
plt.show()
```

## Steps :
- The image is first loaded in grayscale to simplify processing and reduce computational complexity.
- Using Fast Fourier Transform (FFT), the image is converted from the spatial domain to the frequency domain, where low and high frequencies represent smooth and detailed regions, respectively.
- A Low-Pass Filter (LPF) mask is created to retain low frequencies (blurring the image), while a High-Pass Filter (HPF) mask is created to retain high frequencies (highlighting edges).
- These masks are multiplied with the Fourier-transformed image to selectively pass or block certain frequencies.
- The Inverse FFT is then applied to bring the filtered images back to the spatial domain . Finally, the original, low-pass, and high-pass filtered images are displayed side by side for visual comparison.

---

# Practical 2 : Load and display an image in different color models (RGB, CMY, HSV, Grayscale).

```python
%pip install opencv-python matplotlib numpy

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load image in RGB color model
img_bgr = cv2.imread('demo_image.jpg')     
img_rgb = cv2.cvtColor(img_bgr, cv2.COLOR_BGR2RGB)

# Step 2: Convert RGB to other color models
img_hsv = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2HSV)      
img_gray = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2GRAY)     
img_cmy = 1 - (img_rgb / 255.0)                       

# Step 3: Display all color models
titles = ['RGB Image', 'CMY Image', 'HSV Image', 'Grayscale Image']
images = [img_rgb, img_cmy, img_hsv, img_gray]

plt.figure(figsize=(10, 8))
for i in range(4):
    plt.subplot(2, 2, i + 1)
    plt.imshow(images[i], cmap='gray' if i == 3 else None)
    plt.title(titles[i])
    plt.axis('off')
plt.tight_layout()
plt.show()
```

## Steps :
- The image is loaded using OpenCV in BGR format and converted to RGB for correct color display.
- The RGB image is then transformed into HSV (Hue, Saturation, Value) and Grayscale using OpenCV’s cvtColor() function.
- The CMY (Cyan, Magenta, Yellow) model is manually derived by subtracting the RGB values (normalized to 0–1) from 1.
- Each color space highlights different image characteristics — RGB shows natural colors, HSV separates intensity from color, and Grayscale shows brightness.
- All versions are displayed using Matplotlib for side-by-side comparison.
- This helps in understanding how various color models represent the same image differently for different image processing tasks.

---

# Practical 2 : Load and display an image in different color models (RGB, CMY, HSV, Grayscale).

```python
%pip install opencv-python matplotlib numpy

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load image in RGB color model
img_bgr = cv2.imread('demo_image.jpg')     
img_rgb = cv2.cvtColor(img_bgr, cv2.COLOR_BGR2RGB)

# Step 2: Convert RGB to other color models
img_hsv = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2HSV)      
img_gray = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2GRAY)     
img_cmy = 1 - (img_rgb / 255.0)                       

# Step 3: Display all color models
titles = ['RGB Image', 'CMY Image', 'HSV Image', 'Grayscale Image']
images = [img_rgb, img_cmy, img_hsv, img_gray]

plt.figure(figsize=(10, 8))
for i in range(4):
    plt.subplot(2, 2, i + 1)
    plt.imshow(images[i], cmap='gray' if i == 3 else None)
    plt.title(titles[i])
    plt.axis('off')
plt.tight_layout()
plt.show()
```

## Steps :
- The image is loaded using OpenCV in BGR format and converted to RGB for correct color display.
- The RGB image is then transformed into HSV (Hue, Saturation, Value) and Grayscale using OpenCV’s cvtColor() function.
- The CMY (Cyan, Magenta, Yellow) model is manually derived by subtracting the RGB values (normalized to 0–1) from 1.
- Each color space highlights different image characteristics — RGB shows natural colors, HSV separates intensity from color, and Grayscale shows brightness.
- All versions are displayed using Matplotlib for side-by-side comparison.
- This helps in understanding how various color models represent the same image differently for different image processing tasks.

---

# Practical 3 : Perform image downsampling and upsampling, analyzing the effects on resolution.

```python
%pip install opencv-python matplotlib

import cv2
import matplotlib.pyplot as plt

# Step 1: Load the original image
img = cv2.imread('demo_image.jpg')
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Step 2: Downsampling (reduce size)
downsampled = cv2.pyrDown(img)  # reduces resolution by factor of 2

# Step 3: Upsampling (increase size)
upsampled = cv2.pyrUp(downsampled)  # increases resolution by factor of 2

# Step 4: Display images
plt.figure(figsize=(12, 6))
plt.subplot(1, 3, 1)
plt.imshow(img)
plt.title('Original Image')

plt.subplot(1, 3, 2)
plt.imshow(downsampled)
plt.title('Downsampled Image (Reduced Resolution)')

plt.subplot(1, 3, 3)
plt.imshow(upsampled)
plt.title('Upsampled Image (Blurry / Lost Details)')

plt.tight_layout()
plt.show()
```

## Steps :
- The image is first loaded in RGB format for proper color representation.
- Using cv2.pyrDown(), the image is downsampled, effectively reducing its size and resolution by a factor of two.
- The downsampled image is then upsampled using cv2.pyrUp() to increase its size back to the original dimensions.
- Due to information loss during downsampling, the upsampled image appears blurry and lacks fine details.
- Downsampling reduces storage and computation needs, while upsampling tries to reconstruct details but cannot fully recover lost information.
- The results are displayed to visually compare how resolution and sharpness change across the three versions.

---

# Practical 4 : Implement pixel adjacency and connectivity to identify connected components in an image.

```python
%pip install opencv-python matplotlib numpy

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load the image and convert to grayscale
img = cv2.imread('demo_image.jpg', 0)

# Step 2: Convert grayscale to binary (thresholding)
_, binary = cv2.threshold(img, 127, 255, cv2.THRESH_BINARY)

# Step 3: Find connected components (using 8-connectivity)
num_labels, labels = cv2.connectedComponents(binary)

# Step 4: Apply random colors to visualize connected components
label_hue = np.uint8(179 * labels / np.max(labels))
blank_ch = 255 * np.ones_like(label_hue)
colored_img = cv2.merge([label_hue, blank_ch, blank_ch])
colored_img = cv2.cvtColor(colored_img, cv2.COLOR_HSV2RGB)
colored_img[label_hue == 0] = 0 

# Step 5: Display results
plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(binary, cmap='gray')
plt.title('Binary Image')

plt.subplot(1, 2, 2)
plt.imshow(colored_img)
plt.title(f'Connected Components (Count: {num_labels - 1})')
plt.show()
```

## Steps :
- The image is first loaded in grayscale and then binarized using a threshold to separate objects from the background.
- Using cv2.connectedComponents(), the algorithm labels groups of connected pixels based on 8-connectivity, where diagonal neighbors are also considered connected.
- Each connected component receives a unique label, allowing identification of distinct objects in the image.
- The labeled regions are colored differently for visual distinction and displayed using Matplotlib.
- This process demonstrates how pixel adjacency and connectivity help identify and segment distinct regions in an image.
- 4-connectivity or 8-connectivity can be chosen depending on whether diagonal connections are allowed or not.

---

# Practical 5 : Apply histogram equalization and contrast stretching on low-contrast images.

```python
%pip install opencv-python matplotlib numpy

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load a low-contrast image
img = cv2.imread('compressed_demo_image (1).jpg', 0)

# Step 2: Apply Histogram Equalization
equalized = cv2.equalizeHist(img)

# Step 3: Apply Contrast Stretching
min_val, max_val = np.min(img), np.max(img)
stretched = ((img - min_val) / (max_val - min_val) * 255).astype(np.uint8)

# Step 4: Display Results
plt.figure(figsize=(12, 6))
plt.subplot(1, 3, 1)
plt.imshow(img, cmap='gray')
plt.title('Original Low-Contrast Image')

plt.subplot(1, 3, 2)
plt.imshow(equalized, cmap='gray')
plt.title('Histogram Equalized Image')

plt.subplot(1, 3, 3)
plt.imshow(stretched, cmap='gray')
plt.title('Contrast Stretched Image')
plt.tight_layout()
plt.show()
```

## Steps :
- The low-contrast image is loaded in grayscale for easier intensity manipulation.
- Histogram Equalization (cv2.equalizeHist) redistributes the pixel intensities to cover the full range (0–255), enhancing global contrast.
- Contrast Stretching linearly scales the intensity values between the image’s minimum and maximum brightness levels to improve visibility.
- Both methods aim to enhance image contrast — histogram equalization works nonlinearly, while contrast stretching is linear.
- The results are displayed to visually compare improvements in brightness and detail.
- After enhancement, the image appears sharper and more balanced, especially in darker or faded regions.

---

# Practical 6 : Implement Gaussian, Median, and Salt & Pepper noise removal on a noisy image.

```python
%pip install opencv-python matplotlib numpy

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load the image and add synthetic Salt & Pepper noise
img = cv2.imread('demo_image.jpg', 0)
noisy_img = img.copy()
prob = 0.02  # noise probability
salt_pepper = np.random.rand(*img.shape)
noisy_img[salt_pepper < prob / 2] = 0
noisy_img[salt_pepper > 1 - prob / 2] = 255

# Step 2: Apply Gaussian Blur
gaussian_filtered = cv2.GaussianBlur(noisy_img, (5, 5), 0)

# Step 3: Apply Median Filter
median_filtered = cv2.medianBlur(noisy_img, 5)

# Step 4: Apply Bilateral Filter (effective for salt & pepper + edges)
bilateral_filtered = cv2.bilateralFilter(noisy_img, 9, 75, 75)

# Step 5: Display all images
plt.figure(figsize=(12, 8))
titles = ['Original Image', 'Noisy Image', 'Gaussian Filter', 'Median Filter', 'Bilateral Filter']
images = [img, noisy_img, gaussian_filtered, median_filtered, bilateral_filtered]

for i in range(5):
    plt.subplot(2, 3, i + 1)
    plt.imshow(images[i], cmap='gray')
    plt.title(titles[i])
plt.axis('off')
plt.tight_layout()
plt.show()
```

## Steps :
- The image is loaded in grayscale, and Salt & Pepper noise is artificially added to simulate real-world noisy conditions.
- A Gaussian filter (cv2.GaussianBlur) is applied to reduce high-frequency noise and smooth the image.
- The Median filter (cv2.medianBlur) effectively removes Salt & Pepper noise while preserving edges better than Gaussian filtering.
- A Bilateral filter (cv2.bilateralFilter) is used to remove noise while keeping edges sharp, suitable for fine details.
- All filtered images are displayed for comparison to observe how each filter affects noise and sharpness.
- The Median filter usually performs best for Salt & Pepper noise, while Gaussian and Bilateral filters are ideal for random and Gaussian noise.

---

# Practical 7 : Use Inverse and Wiener filtering to restore degraded images.

```python
%pip install opencv-python numpy matplotlib scipy

import cv2
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import wiener

# Step 1: Load and blur (degrade) the image
img = cv2.imread('demo_image.jpg', 0)
kernel_size = 9
psf = np.ones((kernel_size, kernel_size)) / (kernel_size ** 2) 
degraded = cv2.filter2D(img, -1, psf)

# Step 2: Apply Inverse Filtering (in frequency domain)
f = np.fft.fft2(degraded)
psf_padded = np.zeros_like(img)
psf_padded[:kernel_size, :kernel_size] = psf
H = np.fft.fft2(psf_padded)
H_inv = np.where(H != 0, 1 / H, 0)
restored_inverse = np.abs(np.fft.ifft2(f * H_inv))

# Step 3: Apply Wiener Filtering
restored_wiener = wiener(degraded, (5, 5))

# Step 4: Display results
plt.figure(figsize=(12, 6))
titles = ['Original Image', 'Degraded (Blurred)', 'Restored - Inverse Filter', 'Restored - Wiener Filter']
images = [img, degraded, restored_inverse, restored_wiener]

for i in range(4):
    plt.subplot(2, 2, i + 1)
    plt.imshow(images[i], cmap='gray')
    plt.title(titles[i])
    plt.axis('off')
plt.tight_layout()
plt.show()
```

## Steps :
- The original image is blurred using a low-pass filter kernel to simulate degradation caused by motion or defocus.
- The Inverse Filter is applied in the frequency domain by dividing the Fourier transform of the degraded image by the system’s degradation function (PSF).
- However, Inverse Filtering is sensitive to noise, often amplifying it during restoration.
- The Wiener Filter (scipy.signal.wiener) is then used, which optimally balances noise suppression and detail preservation by estimating local variance.
- Both methods attempt to reconstruct the original image — Inverse Filtering focuses on deblurring, while Wiener Filtering adds noise resilience.
- The results show that Wiener filtering generally produces smoother, more natural restorations under noisy conditions.

---

# Practical 8 : Implement Sobel, Prewitt, and Canny edge detection on sample images.

```python
%pip install opencv-python matplotlib scipy

import cv2
import numpy as np
import matplotlib.pyplot as plt
from scipy import ndimage

# Step 1: Load image and convert to grayscale
img = cv2.imread('demo_image.jpg', 0)

# Step 2: Apply Sobel edge detection
sobel_x = cv2.Sobel(img, cv2.CV_64F, 1, 0, ksize=3)
sobel_y = cv2.Sobel(img, cv2.CV_64F, 0, 1, ksize=3)
sobel_edges = cv2.magnitude(sobel_x, sobel_y)

# Step 3: Apply Prewitt edge detection (using ndimage filters)
prewitt_x = ndimage.prewitt(img, axis=0)
prewitt_y = ndimage.prewitt(img, axis=1)
prewitt_edges = np.hypot(prewitt_x, prewitt_y)

# Step 4: Apply Canny edge detection
canny_edges = cv2.Canny(img, 100, 200)

# Step 5: Display results
titles = ['Original Image', 'Sobel Edge Detection', 'Prewitt Edge Detection', 'Canny Edge Detection']
images = [img, sobel_edges, prewitt_edges, canny_edges]

plt.figure(figsize=(12, 6))
for i in range(4):
    plt.subplot(2, 2, i + 1)
    plt.imshow(images[i], cmap='gray')
    plt.title(titles[i])
    plt.axis('off')
plt.tight_layout()
plt.show()
```

## Steps :
- The input image is converted to grayscale to simplify edge detection by analyzing intensity variations.
- The Sobel operator calculates image gradients in both X and Y directions, highlighting strong edges and transitions.
- The Prewitt operator (similar to Sobel but simpler) detects edges by computing differences in intensity using predefined kernels.
- The Canny edge detector applies Gaussian smoothing, gradient computation, and hysteresis thresholding for precise and noise-resistant edge detection.
- Each method provides a different level of accuracy and noise sensitivity — Sobel and Prewitt emphasize edges, while Canny provides cleaner, well-defined boundaries.
- The results are displayed side by side to visually compare edge clarity and detection precision.

---

# Practical 9 : Apply dilation, erosion, opening, and closing operations on binary images.

```python
%pip install opencv-python matplotlib

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load image and convert to binary
img = cv2.imread('demo_image.jpg', 0)
_, binary = cv2.threshold(img, 127, 255, cv2.THRESH_BINARY)

# Step 2: Define the kernel (structuring element)
kernel = np.ones((5, 5), np.uint8)

# Step 3: Apply Morphological Operations
dilated = cv2.dilate(binary, kernel, iterations=1)
eroded = cv2.erode(binary, kernel, iterations=1)
opened = cv2.morphologyEx(binary, cv2.MORPH_OPEN, kernel)
closed = cv2.morphologyEx(binary, cv2.MORPH_CLOSE, kernel)

# Step 4: Display results
titles = ['Original Binary Image', 'Dilation', 'Erosion', 'Opening', 'Closing']
images = [binary, dilated, eroded, opened, closed]

plt.figure(figsize=(12, 8))
for i in range(5):
    plt.subplot(2, 3, i + 1)
    plt.imshow(images[i], cmap='gray')
    plt.title(titles[i])
    plt.axis('off')
plt.tight_layout()
plt.show()
```

## Steps :
- The binary image is loaded and thresholded to ensure it contains only black and white pixels.
- A structuring element (kernel) is defined, which determines how the morphological transformations affect pixel neighborhoods.
- Dilation enlarges the white regions, filling small holes, while Erosion shrinks them, removing noise or thin edges.
- Opening (Erosion → Dilation) removes small white noise, and Closing (Dilation → Erosion) fills small black gaps within objects.
- These operations are performed using OpenCV functions like cv2.dilate(), cv2.erode(), and cv2.morphologyEx().
- The output images clearly demonstrate how each morphological operation modifies the shape and structure of objects in the binary image.

---

# Practical 10 : 1: Implement Huffman Coding and JPEG compression on an image. 2: Detect objects in an image using template matching and feature-based methods (ORB/SIFT).

## 1. Implement Huffman Coding and JPEG compression on an image. 
```python
%pip install opencv-python numpy matplotlib imageio

import cv2
import numpy as np
import matplotlib.pyplot as plt
import imageio
import heapq
from collections import Counter

img = cv2.imread('demo_image.jpg', 0)
if img is None:
    raise ValueError("Error: Image not found! Please check the path or filename.")

class Node:
    def __init__(self, freq, symbol=None, left=None, right=None):
        self.freq = freq
        self.symbol = symbol
        self.left = left
        self.right = right
    def __lt__(self, other):
        return self.freq < other.freq

freq = Counter(img.flatten())

heap = [Node(freq=f, symbol=sym) for sym, f in freq.items()]
heapq.heapify(heap)

while len(heap) > 1:
    left = heapq.heappop(heap)
    right = heapq.heappop(heap)
    new_node = Node(left.freq + right.freq, None, left, right)
    heapq.heappush(heap, new_node)

root = heap[0]

def generate_codes(node, current_code="", codes={}):
    if node is None:
        return
    if node.symbol is not None:
        codes[node.symbol] = current_code
        return
    generate_codes(node.left, current_code + "0", codes)
    generate_codes(node.right, current_code + "1", codes)
    return codes

codes = generate_codes(root)
print("✅ Huffman Coding Completed. Total unique symbols:", len(codes))

encode_param = [int(cv2.IMWRITE_JPEG_QUALITY), 30]
cv2.imwrite('compressed.jpg', img, encode_param)
jpeg_img = cv2.imread('compressed.jpg', 0)

plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.imshow(img, cmap='gray')
plt.title('Original Image')
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(jpeg_img, cmap='gray')
plt.title('JPEG Compressed Image')
plt.axis('off')

plt.tight_layout()
plt.show()

print("JPEG Compression and Huffman Coding Simulation Successful!")
```

## Steps :
- The image is converted to grayscale for easier compression analysis.
- Huffman Coding is simulated by computing frequency counts of pixel values and constructing a Huffman tree, which assigns shorter codes to frequent symbols.
- JPEG compression is applied using OpenCV’s cv2.imwrite() with a lower quality factor to reduce file size.
- JPEG compression combines quantization and entropy encoding (Huffman) to achieve efficient storage.
- The original and compressed images are displayed side by side to visualize loss in detail.
- JPEG achieves high compression but introduces minor blurring or artifacts due to lossy encoding.

## 2. Detect objects in an image using template matching and feature-based methods (ORB/SIFT). 
```python
%pip install opencv-python matplotlib

import cv2
import matplotlib.pyplot as plt

# Step 1: Load target and template images
img = cv2.imread('demo_image.jpg', 0)
template = cv2.imread('demo_image_crop.jpg', 0)
h, w = template.shape

# Step 2: Template Matching
res = cv2.matchTemplate(img, template, cv2.TM_CCOEFF_NORMED)
threshold = 0.8
loc = np.where(res >= threshold)
img_tm = img.copy()
for pt in zip(*loc[::-1]):
    cv2.rectangle(img_tm, pt, (pt[0]+w, pt[1]+h), 255, 2)

# Step 3: ORB Feature Matching
orb = cv2.ORB_create()
kp1, des1 = orb.detectAndCompute(template, None)
kp2, des2 = orb.detectAndCompute(img, None)
bf = cv2.BFMatcher(cv2.NORM_HAMMING, crossCheck=True)
matches = bf.match(des1, des2)
matches = sorted(matches, key=lambda x: x.distance)
img_orb = cv2.drawMatches(template, kp1, img, kp2, matches[:20], None, flags=2)

# Step 4: Display results
plt.figure(figsize=(12,6))
plt.subplot(1,2,1)
plt.imshow(img_tm, cmap='gray')
plt.title('Template Matching Result')

plt.subplot(1,2,2)
plt.imshow(img_orb)
plt.title('ORB Feature Matching')
plt.show()
```

## Steps :
- The scene and template images are loaded in grayscale for easy processing.
- Template Matching (cv2.matchTemplate) slides the template over the image and identifies regions with high correlation, marking matches with rectangles.
- For more robust detection, ORB (Oriented FAST and Rotated BRIEF) detects keypoints and computes descriptors that are rotation and scale invariant.
- The Brute-Force Matcher (BFMatcher) finds the best matches between keypoints in both images.
- Matched regions are visualized using cv2.drawMatches(), showing correspondences between template and scene.
- Template Matching works well for fixed-size patterns, while ORB/SIFT handles scale, rotation, and lighting variations effectively.

---

# Practical 11 : Train and test a simple deep learning model for object recognition using OpenCV and TensorFlow

```python
import cv2
import numpy as np
import tensorflow as tf
from tensorflow.keras import layers, models
import matplotlib.pyplot as plt

# Step 1: Load CIFAR-10 dataset
(x_train, y_train), (x_test, y_test) = tf.keras.datasets.cifar10.load_data()
x_train, x_test = x_train / 255.0, x_test / 255.0 

# Step 2: Define CNN model
model = models.Sequential([
    layers.Conv2D(32, (3,3), activation='relu', input_shape=(32,32,3)),
    layers.MaxPooling2D(2,2),
    layers.Conv2D(64, (3,3), activation='relu'),
    layers.MaxPooling2D(2,2),
    layers.Flatten(),
    layers.Dense(64, activation='relu'),
    layers.Dense(10, activation='softmax')
])

# Step 3: Compile and train
model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])
model.fit(x_train, y_train, epochs=3, validation_split=0.2, verbose=1)

# Step 4: Evaluate
loss, acc = model.evaluate(x_test, y_test)
print(f"Test Accuracy: {acc:.2f}")

# Step 5: Predict and display (no cv2.cvtColor needed)
img = x_test[5] 
pred = np.argmax(model.predict(img.reshape(1, 32, 32, 3)))
plt.imshow(img)
plt.title(f"Predicted Label: {pred}")
plt.axis('off')
plt.show()
```

## Steps :
- The CIFAR-10 dataset (10 object classes) is loaded and normalized for training and testing.
- A simple Convolutional Neural Network (CNN) is defined with convolution, pooling, and dense layers for feature extraction and classification.
- The model is compiled using Adam optimizer and trained for a few epochs to learn object patterns.
- After training, it is evaluated on test data to check accuracy and generalization.
- An image from the test set is preprocessed using OpenCV and passed to the model for prediction.
- The system successfully performs basic object recognition, identifying objects like cars, animals, or ships from the dataset.

---

# Practical 12 : 1:Capture and display real-time video frames using OpenCV. 2:Implement motion detection and object tracking in a video feed

```python
%pip install opencv-python

import cv2
import numpy as np

# Step 1: Initialize the video capture (0 = default webcam)
cap = cv2.VideoCapture('demo_video.mp4')
if not cap.isOpened():
    raise Exception("Could not open video device")

# Step 2: Read first frame for background reference
ret, frame1 = cap.read()
ret, frame2 = cap.read()

while cap.isOpened():
    # Step 3: Compute absolute difference between frames
    diff = cv2.absdiff(frame1, frame2)
    gray = cv2.cvtColor(diff, cv2.COLOR_BGR2GRAY)
    blur = cv2.GaussianBlur(gray, (5,5), 0)
    _, thresh = cv2.threshold(blur, 25, 255, cv2.THRESH_BINARY)
    dilated = cv2.dilate(thresh, None, iterations=2)

    # Step 4: Find contours (moving objects)
    contours, _ = cv2.findContours(dilated, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
    for contour in contours:
        if cv2.contourArea(contour) < 900: 
            continue
        (x, y, w, h) = cv2.boundingRect(contour)
        cv2.rectangle(frame1, (x, y), (x+w, y+h), (0, 255, 0), 2)
        cv2.putText(frame1, "Motion Detected", (10, 30),
                    cv2.FONT_HERSHEY_SIMPLEX, 1, (0,0,255), 2)

    # Step 5: Display frames
    cv2.imshow("Live Feed", frame1)
    frame1 = frame2
    ret, frame2 = cap.read()
    if not ret or cv2.waitKey(20) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```

## Steps :
- Initialize webcam using cv2.VideoCapture(0) to capture real-time frames.
- The first two consecutive frames are read and compared to detect any pixel-level changes.
- The absolute difference between frames is computed, converted to grayscale, blurred, and thresholded to highlight motion regions.
- Contours of moving areas are extracted; bounding boxes are drawn around detected objects to track motion.
- The processed frames are displayed in real time using cv2.imshow(), and the loop continues until the user presses 'q'.
- This method forms the basis of motion detection and simple object tracking, often used in surveillance and monitoring systems.

---

# Practical 13 : Overlay virtual objects on a real-world scene using basic AR techniques.

```python
%pip install opencv-python numpy

import cv2
import numpy as np

# Step 1: Load the scene (video feed) and the virtual object
cap = cv2.VideoCapture('demo_video.mp4')  # or 'video.mp4' for custom video
overlay = cv2.imread('demo_image.jpg')  # image to overlay
overlay = cv2.resize(overlay, (200, 200))  # resize overlay

# Step 2: Create ORB detector for feature matching
orb = cv2.ORB_create()
ret, base_frame = cap.read()
gray_base = cv2.cvtColor(base_frame, cv2.COLOR_BGR2GRAY)
kp1, des1 = orb.detectAndCompute(gray_base, None)

# Step 3: Continuously process frames and find matches
while cap.isOpened():
    ret, frame = cap.read()
    if not ret:
        break
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
    kp2, des2 = orb.detectAndCompute(gray, None)
    bf = cv2.BFMatcher(cv2.NORM_HAMMING, crossCheck=True)
    if des2 is None:
        continue
    matches = bf.match(des1, des2)
    matches = sorted(matches, key=lambda x: x.distance)

    # Step 4: Overlay the virtual object on the detected area
    if len(matches) > 15:
        x, y, w, h = 100, 100, 200, 200
        frame[y:y+h, x:x+w] = cv2.addWeighted(frame[y:y+h, x:x+w], 0.5, overlay, 0.5, 0)

    cv2.imshow('Augmented Reality Overlay', frame)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
```

## Steps :
- The camera feed (or video) is captured using OpenCV and a virtual object image is loaded (e.g., logo, 3D marker, or shape).
- Feature detection is performed on the initial frame using ORB (Oriented FAST and BRIEF) to find distinct points for tracking.
- Each new frame is processed to detect and match features between the scene and the reference frame.
- When a sufficient number of matches are found, the virtual object is overlaid on the detected region using alpha blending (cv2.addWeighted).
- The overlay appears as if the virtual object is attached to the real-world scene, creating a simple AR effect.
- The feed updates continuously in real-time until the user presses ‘q’ to exit.

---