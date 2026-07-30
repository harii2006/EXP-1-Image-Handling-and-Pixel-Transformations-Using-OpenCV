# EXP-1-Image-Handling-and-Pixel-Transformations-Using-OpenCV
# AIM :
Write a Python program using OpenCV that performs the following tasks:

Read and Display an Image.
Adjust the brightness of an image.
Modify the image contrast.
Generate a third image using bitwise operations.
# SOFTWARE REQUIRED :
```
--> Anaconda - Python 3.7
--> Jupyter Notebook (for interactive development and execution)
```
# ALGORITHM :
Step 1:
Load an image from your local directory and display it.

Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image. Display the original, brighter, and darker images.

Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix). Display the original, lower contrast, and higher contrast images.

Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

# PROGRAM :
Load an image from your local directory and display it.
```
import cv2
import matplotlib.pyplot as plt

# Read the image using OpenCV
img = cv2.imread('p.jpeg', cv2.IMREAD_COLOR)

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Display the image using Matplotlib
plt.imshow(img_rgb, cmap='viridis')  # You can change 'viridis' to another cmap or use None for RGB images
plt.title("Original Image")
plt.axis('on')  # Removes axis ticks and labels
plt.show()
```
 Draw a line from the top-left to the bottom-right of the image. 
```
# Load the image
image = cv2.imread('p.jpeg')

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape

# Draw a line from top-left to bottom-right
line_img = cv2.line(img_rgb, (0, 0), (1064, 1279), (0, 255, 0), 10) # cv2.line(image, start_point, end_point, color, thickness)
plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('on')  
plt.show()
```
Draw a circle at the center of the image.
```
# Load the image
image = cv2.imread('p.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape

circle_img = cv2.circle(img_rgb,(532,600),500,(0,0,255),10) # cv2.circle(image, center, radius, color, thickness)

plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('off')  
plt.show()

```
Draw a rectangle around the whole image.
```
# Load the image
image = cv2.imread('p.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img.shape

# Draw a rectangle around the Whole image
rectangle_img = cv2.rectangle(img_rgb, (0, 0), (1064, 1279), (255, 0, 0), 30)  # cv2.rectangle(image, start_point, end_point, color, thickness)

plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('off')  
plt.show()
```
Add the text "OpenCV Drawing" at the top-left corner of the image.
```
# Load the image
image = cv2.imread('p.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Add text to the image
text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 255), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)

plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('on')  
plt.show()
```
Original RGB image and display it.
```
# Load the image
image = cv2.imread('p.jpeg') 
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Original RGB Image
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("on")
```
Convert the image from RGB to HSV and display it.
```
# Convert RGB to HSV
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

# HSV Image
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("on")
```
Convert the image from RGB to GRAY and display it.
```
# Convert RGB to GRAY
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

# Grayscale Image
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("on")
```
Convert the image from RGB to YCrCb and display it.
```
# Convert RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

# YCrCb Image
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("on")
```
Convert the HSV image back to RGB and display it.
```
# Convert HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("on")
```
Modify a block of pixels (300x300) to white, starting from (200, 200).
```
# Modify a block of pixels (300x300) to white, starting from (200, 200)
image[200:500, 200:500] = [255, 255, 255]  # Rows: 200-499, Columns: 200-499

# Convert BGR to RGB for displaying with Matplotlib
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Display the modified image
plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis("on")
plt.show()
```
Resize the original image to half its size and display it.
```
# Load the image
image = cv2.imread('p.jpeg') 
image.shape

# Resize the image to half its size
resized_image = cv2.resize(image, (1280 // 2, 1065 // 2))  # (new_width, new_height)

# Convert BGR to RGB for displaying with Matplotlib
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)
resized_image_rgb.shape

# Display the resized image
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("on")
plt.show()
```
Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.
```
# Load the image
image = cv2.imread('p.jpeg') 
image.shape

# Crop a 300x300 region starting from (50, 50)
roi = image[50:350, 50:350]  # Rows: 50-349, Columns: 50-349

# Convert BGR to RGB for displaying with Matplotlib
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)

# Display the cropped region (ROI)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("on")
plt.show()
```
Flip the original image horizontally and display it.
```

# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)

# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)

# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("on")
```
Flip the original image vertically and display it.
```
# Flip the image vertically (up-down)
flipped_vertically = cv2.flip(image, 0)

# Convert BGR to RGB for displaying with Matplotlib
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)

# Vertical flip
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("on")

```
# OUTPUT:

<img width="496" height="336" alt="image" src="https://github.com/user-attachments/assets/58d7f4ea-be66-4ab5-a394-cd2462cf993a" />

<img width="495" height="342" alt="image" src="https://github.com/user-attachments/assets/a30cafa8-0117-48df-b9a9-c12fd09a1edb" />

<img width="492" height="335" alt="image" src="https://github.com/user-attachments/assets/5bc6d3fa-47f7-40d4-802c-e5c65dde2bdc" />

<img width="497" height="341" alt="image" src="https://github.com/user-attachments/assets/8b7bc614-8a04-4215-9497-79e03f4f5c02" />

<img width="507" height="347" alt="image" src="https://github.com/user-attachments/assets/89cfcfa3-ae3b-478b-b63c-2fa910b45ff0" />

<img width="493" height="336" alt="image" src="https://github.com/user-attachments/assets/18faa2aa-709d-4841-af6d-69cdb7fbc28c" />

<img width="496" height="332" alt="image" src="https://github.com/user-attachments/assets/de308faa-9c56-44ea-8596-6c3d59c8e54a" />

<img width="492" height="333" alt="image" src="https://github.com/user-attachments/assets/dc898fdf-e65b-4b02-a98b-1971ba7746cb" />

<img width="492" height="337" alt="image" src="https://github.com/user-attachments/assets/1f0b4c40-2273-4f85-b0c9-c5f04df317ed" />

<img width="488" height="331" alt="image" src="https://github.com/user-attachments/assets/c20ad89c-e67d-4c9b-a466-6781b8bcb146" />

<img width="487" height="332" alt="image" src="https://github.com/user-attachments/assets/0525cce6-5d41-4fc7-a086-bae604386601" />

<img width="465" height="393" alt="image" src="https://github.com/user-attachments/assets/31714177-7aac-4b4c-9c68-9a81193e70b3" />

<img width="363" height="392" alt="image" src="https://github.com/user-attachments/assets/4cc175c5-579a-4bf6-bc7f-daee4398d05c" />

<img width="488" height="328" alt="image" src="https://github.com/user-attachments/assets/5f864a2f-e8a6-4411-8c4b-8553689ca80b" />

<img width="486" height="337" alt="image" src="https://github.com/user-attachments/assets/4b668226-47c0-4f0b-ad5c-153cb2b41ec2" />

# RESULT :
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
