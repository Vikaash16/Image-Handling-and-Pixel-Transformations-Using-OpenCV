# Image-Handling-and-Pixel-Transformations-Using-OpenCV 
## NAME : Vikaash P
## REG NO : 212223240180

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


## Ex. No. 01

#### ```python
```
import cv2
import matplotlib.pyplot as plt
```
# Read the image using OpenCV
```
img = cv2.imread('TK.JPG', cv2.IMREAD_COLOR)
```
# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
```
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
plt.imshow(img_rgb, cmap='viridis')  
plt.title("Original Image")
plt.axis('off') 
plt.show()
```

# Load the image
```
image = cv2.imread('TK.JPG')
```
# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)

```
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```
# Draw a line from top-left to bottom-right

```
line_img = cv2.line(img_rgb, (0, 0), (768, 600), (255, 0, 0), 2) # cv2.line(image, start_point, end_point, color, thickness)
plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('off')  
plt.show()
```
# Draw a circle at the center of the image.
```
image = cv2.imread('TK.JPG') 
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
circle_img = cv2.circle(img_rgb,(400,300),150,(255,0,0),10) # cv2.circle(image, center, radius, color, thickness)
plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('off')  
plt.show()
```

# Draw a rectangle around  the whole image
```
image = cv2.imread('TK.JPG') 

img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img.shape
rectangle_img = cv2.rectangle(img_rgb, (0, 0), (768, 600), (0, 0, 255), 10)  # cv2.rectangle(image, start_point, end_point, color, thickness)
plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('off')  
plt.show()
```

# Add the text "OpenCV Drawing" at the top-left corner of the image.
```
image = cv2.imread('TK.JPG') 
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)
plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('off')  
plt.show()
```
    

    

```

image = cv2.imread('TK.JPG')
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("off")
```
#  Convert the image from RGB to HSV and display it.
```
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)
plt.imshow(image_hsv)
plt.title("HSV Image")
plt.axis("off")
```
# Convert the image from RGB to GRAY and display it. 
```
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")
```

# Convert the image from RGB to YCrCb and display it. 
```
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("off")
```
# Convert the HSV image back to RGB and display it.
```
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)
plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("off")
```
# Modify a block of pixels (300x300) to white, starting from (200, 200)
```
image[200:500, 200:500] = [255, 255, 255]  # Rows: 200-499, Columns: 200-499

```
# Convert BGR to RGB for displaying with Matplotlib
```
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis("off")
plt.show()
```
# Resize the original image to half its size and display it.

```
image = cv2.imread('TK.JPG')
image.shape
resized_image = cv2.resize(image, (768 // 2, 600 // 2))  # (new_width, new_height)
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)
resized_image_rgb.shape
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
```

# Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.

```
image = cv2.imread('TK.JPG')
image.shape
roi = image[50:350, 50:350]  # Rows: 50-349, Columns: 50-349
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
```

# Flip the image vertically (up-down)
```
flipped_vertically = cv2.flip(image, 0)
```
# Convert BGR to RGB for displaying with Matplotlib

```
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
```
## Output:
 # Read the image using OpenCV

<img width="719" height="400" alt="image" src="https://github.com/user-attachments/assets/28400ce6-b268-428d-b804-f166405534ff" />




2.  Draw a line from top-left to bottom-right


   
<img width="684" height="403" alt="image" src="https://github.com/user-attachments/assets/c71ff36d-4a29-49de-b342-20406fd8e5fa" />




3)Draw a circle at the center of the image.


<img width="669" height="406" alt="image" src="https://github.com/user-attachments/assets/7418183f-a544-4167-824b-b6a0b7b8f9b7" />




4)Draw a rectangle around  the whole image

<img width="706" height="417" alt="image" src="https://github.com/user-attachments/assets/6c8e3d03-3457-48b6-a274-5d193a1d5d0f" />




5)Add the text "OpenCV Drawing" at the top-left corner of the image.

<img width="652" height="405" alt="image" src="https://github.com/user-attachments/assets/0cea5f89-fac8-4f56-8644-34b7651bc9ef" />


6)Convert the image from RGB to HSV and display it.

<img width="696" height="454" alt="image" src="https://github.com/user-attachments/assets/b47986b2-20f3-4aed-80b4-2821f7f26982" />



7) Convert the image from RGB to GRAY and display it. 


<img width="692" height="425" alt="image" src="https://github.com/user-attachments/assets/9514aa75-0b70-4549-93c9-ff51687375d8" />




8) Convert the image from RGB to YCrCb and display it. 

<img width="695" height="443" alt="image" src="https://github.com/user-attachments/assets/db1678ec-da34-4d88-be0f-89f59a0e875c" />



9)Convert the HSV image back to RGB and display it.

<img width="750" height="441" alt="image" src="https://github.com/user-attachments/assets/24296cb6-2cce-46b6-a5a9-f3df264eaa91" />




10) Modify the color of the pixel at (300, 300) to white.


<img width="703" height="405" alt="image" src="https://github.com/user-attachments/assets/364e6d54-7a7e-4d80-aa9f-dfb827ae6979" />

11)  Resize the original image to half its size and display it.
    
<img width="630" height="520" alt="image" src="https://github.com/user-attachments/assets/1701b3f6-addb-4099-956a-f05b9ac5d37c" />



12)Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.




<img width="534" height="528" alt="image" src="https://github.com/user-attachments/assets/903201d3-4fd5-4960-8480-3278319c4f17" />


13) Flip the original image horizontally and display it.

<img width="715" height="409" alt="image" src="https://github.com/user-attachments/assets/c22ec6e8-8ae9-4020-a000-d96711b35597" />



14) Flip the original image vertically and display it.

<img width="697" height="434" alt="image" src="https://github.com/user-attachments/assets/d415b444-9ed8-46a5-a3bc-54d11688da37" />


## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
