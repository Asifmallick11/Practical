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