Image-Handling-and-Pixel-Transformations-Using-OpenCV
AIM:
Write a Python program using OpenCV that performs the following tasks:

Read and Display an Image.
Adjust the brightness of an image.
Modify the image.
Generate the modified image.
Software Required:
Anaconda - Python 3.7
Jupyter Notebook (for interactive development and execution)
Algorithm:
Step 1:
Load an image from your local directory and display it.

Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.
Display the original, brighter, and darker images.

Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).
Display the original, lower contrast, and higher contrast images.

Step 5:
Split the image into B, G, R components and display the channels

Program Developed By:
Name: A PRAVEEN KISHORE

Register Number: 212225220074

Ex. No. 01
1. Load an image from your local directory and display it.
import cv2
import matplotlib.pyplot as plt

# Read the image using OpenCV
img = cv2.imread('My_Ph1.jpg', cv2.IMREAD_COLOR)

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Display the image using Matplotlib
plt.imshow(img_rgb, cmap='viridis')  # You can change 'viridis' to another cmap or use None for RGB images
plt.title("Original Image")
plt.axis('off')  # Removes axis ticks and labels
plt.show()
2. Draw a line from the top-left to the bottom-right of the image.
# Draw a line from top-left to bottom-right
line_img = cv2.line(img_rgb, (0, 0), (768, 600), (0, 255, 0), 2) # cv2.line(image, start_point, end_point, color, thickness)

plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('off')  
plt.show()
3. Draw a circle at the center of the image..
circle_img = cv2.circle(img_rgb,(200,200),150,(255,25,0),10) # cv2.circle(image, center, radius, color, thickness)

plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('off')  
plt.show()
4. Draw a rectangle around the whole image.
# Draw a rectangle around the Whole image
rectangle_img = cv2.rectangle(img_rgb, (0, 0), (800, 500), (0, 145, 255), 10)  # cv2.rectangle(image, start_point, end_point, color, thickness)

plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('off')  
plt.show()
5. Add the text "Your text" at the top-left corner of the image.
# Add text to the image
text_img = cv2.putText(img_rgb, "ambassador", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 255, 0), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)

plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('off')  
plt.show()
6. onvert the image from RGB to HSV and display it..
# Convert RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)
7. Convert the image from RGB to GRAY and display it. .
# Convert RGB to GRAY
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)
8. Convert the image from RGB to YCrCb and display it.
# Convert RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)
9. Convert the HSV image back to RGB and display it..
# Convert HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)
10. Access and print the value of the pixel at coordinates (100, 100).
# Modify a block of pixels (300x300) to white, starting from (200, 200)
image[200:500, 200:500] = [255, 255, 255]  # Rows: 200-499, Columns: 200-499

# Convert BGR to RGB for displaying with Matplotlib
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Display the modified image
plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis("off")
plt.show()
11. Resize the original image to half its size and display it :
# Resize the image to half its size
resized_image = cv2.resize(image, (768 // 2, 600 // 2))  # (new_width, new_height)

# Convert BGR to RGB for displaying with Matplotlib
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

resized_image_rgb.shape

# Display the resized image
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
12. Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it..
# Crop a 300x300 region starting from (50, 50)
roi = image[50:350, 50:350]  # Rows: 50-349, Columns: 50-349

# Convert BGR to RGB for displaying with Matplotlib
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

# Display the cropped region (ROI)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
13. Flip the original image horizontally and vertically display it..
# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)

# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)

# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")

# Flip the image vertically (up-down)
flipped_vertically = cv2.flip(image, 0)

# Convert BGR to RGB for displaying with Matplotlib
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)

# Vertical flip
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
14. Merged another image displays along with original image.
# 1. Read your second image
overlay_img = cv2.imread('2.png', cv2.IMREAD_COLOR)

# 2. Resize the second image so it fits nicely
# Let's make it 150x150 pixels
h_overlay, w_overlay = 100, 150
overlay_resized = cv2.resize(overlay_img, (w_overlay, h_overlay))

# 3. Convert it to RGB (matching your Matplotlib workflow)
overlay_rgb = cv2.cvtColor(overlay_resized, cv2.COLOR_BGR2RGB)

# 4. Define where you want to place it (Top-left corner coordinates)
y_offset = 40
x_offset = 40

# 5. Insert the overlay image into the base image matrix
# This modifies 'img_rgb' in place
img_rgb[y_offset:y_offset+h_overlay, x_offset:x_offset+w_overlay] = overlay_rgb

# 6. Display as usual
plt.imshow(img_rgb)
plt.axis('off')
plt.show()
Output:
i) Original image
<img width="417" height="378" alt="image" src="https://github.com/user-attachments/assets/5f737fc1-ffd9-4c9c-b2ce-7181ee7d67ef" />

ii) Image with line , circle,rectangle, text.
<img width="396" height="408" alt="image" src="https://github.com/user-attachments/assets/14959e78-7a65-460a-902d-fc25308a71a4" />
 <img width="396" height="403" alt="image" src="https://github.com/user-attachments/assets/cc3f646a-ce1d-4b66-8837-753080549b2b" />
 <img width="412" height="402" alt="image" src="https://github.com/user-attachments/assets/3aef71d2-766c-4295-80a2-7366e5fd153e" />
 <img width="421" height="400" alt="image" src="https://github.com/user-attachments/assets/63995109-5274-4a24-b815-3bb1aa2dcf98" />

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
