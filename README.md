# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
## Name: SELVAGANESH B
## Register Number: 212224230258

  ### Ex. No. 01

#### 1. Read the image ('exp 1.jpeg.jpeg') using OpenCV imread() as a grayscale image.
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
img = cv2.imread('My_Ph1.jpg', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```

#### 2. Print the image width, height & Channel.
```python
img.shape
```

#### 3. Display the image using matplotlib imshow().
```python
img_gray = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2GRAY)
plt.imshow(img_gray,cmap='gray')
plt.show()
```
#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
img=cv2.imread('exp 1.jpeg.jpeg')
cv2.imwrite('dipt_image.png',img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
img=cv2.imread('exp 1.jpeg.jpeg')
img_rgb = cv2.cvtColor(img,cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(img)
plt.show()
img.shape
```
#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
crop = img_rgb[0:450,200:550] 
plt.imshow(crop[:,:,::-1])
plt.title("Cropped Region")
plt.axis("off")
plt.show()
crop.shape
```
#### 8. Resize the image up by a factor of 2x.
```python
res= cv2.resize(crop,(200*2, 200*2))
```

#### 9. Flip the cropped/resized image horizontally.
```python
flip= cv2.flip(res,1)
plt.imshow(flip[:,:,::-1])
plt.title("Flipped Horizontally")
plt.axis("off")
```
#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
img=cv2.imread('diptimage2.png',cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```
#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = cv2.putText(img_rgb, "Apollo 11 Saturn V Launch, July 16, 1969", (300, 700),cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 2)  
plt.imshow(text, cmap='gray')  
plt.title("New image")
plt.show()
```
#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
rcol= (255, 0, 255)
cv2.rectangle(img_rgb, (400, 100), (800, 650), rcol, 3)
```
#### 13. Display the final annotated image.
```python
plt.title("Annotated image")
plt.imshow(img_rgb)
plt.show()
```
#### 14. Read the image ('Boy.jpg').
```python
img =cv2.imread('diptimage3.png',cv2.IMREAD_COLOR)
img_rgb= cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
#### 15. Adjust the brightness of the image.
```python
m = np.ones(img_rgb.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(img_rgb, m)  
img_darker = cv2.subtract(img_rgb, m)
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img_rgb), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_brighter), plt.title("Brighter Image"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_darker), plt.title("Darker Image"), plt.axis("off")
plt.show()
```
#### 18. Modify the image contrast.
```python
matrix1 = np.ones(img_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(img_rgb.shape, dtype="float32") * 1.2
img_higher1 = cv2.multiply(img.astype("float32"), matrix1).clip(0,255).astype("uint8")
img_higher2 = cv2.multiply(img.astype("float32"), matrix2).clip(0,255).astype("uint8")
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_higher1), plt.title("Higher Contrast (1.1x)"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_higher2), plt.title("Higher Contrast (1.2x)"), plt.axis("off")
plt.show()
```
#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
b, g, r = cv2.split(img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(b, cmap='gray'), plt.title("Blue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(g, cmap='gray'), plt.title("Green Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(r, cmap='gray'), plt.title("Red Channel"), plt.axis("off")
plt.show()
```
#### 21. Merged the R, G, B , displays along with the original image
```python
merged_rgb = cv2.merge([r, g, b])
plt.figure(figsize=(5,5))
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv_img = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv_img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(h, cmap='gray'), plt.title("Hue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(s, cmap='gray'), plt.title("Saturation Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(v, cmap='gray'), plt.title("Value Channel"), plt.axis("off")
plt.show()
```

#### 23. Merged the H, S, V, displays along with original image.
```python
merged_hsv = cv2.cvtColor(cv2.merge([h, s, v]), cv2.COLOR_HSV2RGB)
combined = np.concatenate((img_rgb, merged_hsv), axis=1)
plt.figure(figsize=(10, 5))
plt.imshow(combined)
plt.title("Original Image  &  Merged HSV Image")
plt.axis("off")
plt.show()
```
Output:
i) Original image
<img width="417" height="378" alt="image" src="https://github.com/user-attachments/assets/5f737fc1-ffd9-4c9c-b2ce-7181ee7d67ef" />

ii) Image with line , circle, rectangle, text.
<img width="396" height="408" alt="image" src="https://github.com/user-attachments/assets/14959e78-7a65-460a-902d-fc25308a71a4" />
 <img width="396" height="403" alt="image" src="https://github.com/user-attachments/assets/cc3f646a-ce1d-4b66-8837-753080549b2b" />
 <img width="412" height="402" alt="image" src="https://github.com/user-attachments/assets/3aef71d2-766c-4295-80a2-7366e5fd153e" />
 <img width="442" height="412" alt="Screenshot 2026-07-27 160307" src="https://github.com/user-attachments/assets/c41f1422-84dc-4f14-aa94-e6fb696077df" />


iii) Image - HSV , Grayscale , YCeCb and HSV to RGB . 
<img width="557" height="425" alt="image" src="https://github.com/user-attachments/assets/94cadc63-b834-402f-aa34-0a5c4d9caadf" />
<img width="563" height="417" alt="image" src="https://github.com/user-attachments/assets/ed8ed592-59a3-4ac6-afb1-8d46413b071a" />
<img width="562" height="422" alt="image" src="https://github.com/user-attachments/assets/ed07fceb-487b-444c-be23-9256375b1f60" />
<img width="567" height="428" alt="image" src="https://github.com/user-attachments/assets/7735c160-973a-40fd-b9e5-751019cb5125" />
<img width="576" height="427" alt="image" src="https://github.com/user-attachments/assets/ae41cb7d-bf4b-47e6-a2cd-2c3649c45eef" />

iv) Image with block .
<img width="457" height="415" alt="image" src="https://github.com/user-attachments/assets/5ed5c933-1ec7-49b1-92ca-b86224ae04b9" />

v) Image - Resized Image (Half Size) , Cropped Region of Interest (ROI),Flipped Horizontally ,Flipped Vertically 
<img width="537" height="410" alt="image" src="https://github.com/user-attachments/assets/82cd755e-1402-47e5-bb51-1bdc411aab93" />
<img width="408" height="415" alt="image" src="https://github.com/user-attachments/assets/2f136d94-b7b3-44e8-98ed-2452c8ffdba9" />
<img width="560" height="436" alt="image" src="https://github.com/user-attachments/assets/0c0b0ec2-a546-41ee-a0da-a17d681f3a2d" />
<img width="558" height="418" alt="image" src="https://github.com/user-attachments/assets/a92a700c-948a-4042-acdd-09a22bdf4f04" />

Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
