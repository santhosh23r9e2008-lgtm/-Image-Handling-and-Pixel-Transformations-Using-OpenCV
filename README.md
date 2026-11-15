# Experiment 1 : Image Handling and Pixel Transformations Using OpenCV Assignment
### Developed By : SANTHOSH G
### Register Number : 212225100044
### Aim :
To perform image handling and pixel transformations using OpenCV in Python, including image loading, displaying, drawing shapes, color space conversion, pixel manipulation, resizing, cropping, flipping, and saving images.

### Requirements :
- Python
- Anaconda prompt
- Jupyter Notebook
- OpenCV (`cv2`)
- Matplotlib
- Input image (`image.jpeg`)

### Procedure :
1. Import the required libraries, OpenCV and Matplotlib.
2. Load the input image using `cv2.imread()`.
3. Display the original image using Matplotlib.
4. Draw a line, circle, rectangle, and text on the image using OpenCV functions.
5. Convert the image into RGB, HSV, grayscale, and YCrCb color spaces.
6. Access the pixel value at coordinate `(100, 100)` and modify the pixel at `(200, 200)` to white.
7. Resize the image to half its original dimensions.
8. Crop a region of interest from the image.
9. Flip the image horizontally and vertically.
10. Save the modified image using `cv2.imwrite()`.

### Program :
### Step1 : Load an image from your local directory and display it.

```python
import cv2
import matplotlib.pyplot as plt

# Read the image using OpenCV
img = cv2.imread('image.jpeg', cv2.IMREAD_COLOR)

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Display the image using Matplotlib
plt.imshow(img_rgb, cmap='viridis')  # You can change 'viridis' to another cmap or use None for RGB images
plt.title("Original Image")
plt.axis('on')  # Removes axis ticks and labels
plt.show()
```

### Step2 :
* Draw a line from the top-left to the bottom-right of the image.
  
```python
# Load the image
image = cv2.imread('image.jpeg')

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape

# Draw a line from top-left to bottom-right
line_img = cv2.line(img_rgb, (0, 0), (768, 600), (255, 0, 0), 2) # cv2.line(image, start_point, end_point, color, thickness)
plt.imshow(line_img, cmap='viridis')  
plt.title("Image with Line")
plt.axis('on')  
plt.show()
```

* Draw a circle at the center of the image.

```python
# Load the image
image = cv2.imread('image.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

img_rgb.shape

circle_img = cv2.circle(img_rgb,(270,200),150,(255,0,0),10) # cv2.circle(image, center, radius, color, thickness)

plt.imshow(circle_img, cmap='viridis')  
plt.title("Image with Circle")
plt.axis('on')  
plt.show()
```

* Draw a rectangle around  the whole image.

```python
# Load the image
image = cv2.imread('image.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

img.shape

# Draw a rectangle around the Whole image
rectangle_img = cv2.rectangle(img_rgb, (10,10), (500, 600), (0, 0, 255), 10)  # cv2.rectangle(img,s_pt,e_pt,color,thickness)

plt.imshow(rectangle_img, cmap='viridis')  
plt.title("Image with Rectangle")
plt.axis('on')  
plt.show()
```

* Add the text "OpenCV Drawing" at the top-left corner of the image.

```python
# Load the image
image = cv2.imread('image.jpeg') 

# Convert BGR (OpenCV's default) to RGB (Matplotlib's expected color order)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Add text to the image
text_img = cv2.putText(img_rgb, "OpenCV Drawing", (10, 30), cv2.FONT_HERSHEY_SIMPLEX, 1, (0,0,0), 10)  ## cv2.putText(image, text, position, font, font_scale, color, thickness)

plt.imshow(text_img, cmap='viridis')  
plt.title("Image with Text")
plt.axis('on')  
plt.show()
```

### Step3 :
* Convert the image from RGB to HSV and display it.

```python
image = cv2.imread('image.jpeg')

image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

plt.imshow(image_rgb)
plt.title("Original RGB Image")
plt.axis("on")
```

```python
image_hsv = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2HSV)

plt.imshow(image_hsv)
```

* Convert the image from RGB to GRAY and display it.

```python
# Convert RGB to GRAY
image_gray = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2GRAY)

# Grayscale Image
plt.imshow(image_gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("on")
```

* Convert the image from RGB to YCrCb and display it.

```python
# Convert RGB to YCrCb
image_ycrcb = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2YCrCb)

# YCrCb Image
plt.imshow(image_ycrcb)
plt.title("YCrCb Image")
plt.axis("on")
```

* Convert the HSV image back to RGB and display it.

```python
# Convert HSV back to RGB
image_hsv_to_rgb = cv2.cvtColor(image_hsv, cv2.COLOR_HSV2RGB)

plt.imshow(image_hsv_to_rgb)
plt.title("HSV to RGB Image")
plt.axis("on")
```

### Step4 : 
* Access and print the value of the pixel at coordinates (100, 100). 
* Modify the color of the pixel at (200, 200) to white.

```python
# Modify a block of pixels (300x300) to white, starting from (200, 200)
image[100:420, 100:420] = [255, 255, 255]  # Rows: 200-499, Columns: 200-499

# Convert BGR to RGB for displaying with Matplotlib
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Display the modified image
plt.imshow(image_rgb)
plt.title("Image with 300x300 White Block")
plt.axis("on")
plt.show()
```

### Step5 : Resize the original image to half its size and display it.

```python
# Load the image
image = cv2.imread('image.jpeg')

image.shape

# Resize the image to half its size
resized_image = cv2.resize(image, (768 // 2, 600 // 2))  # (new_width, new_height)
# Convert BGR to RGB for displaying with Matplotlib
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)

resized_image_rgb.shape

# Display the resized image
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("on")
plt.show()
```

### Step6 : Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.

```python
# Load the image
image = cv2.imread('image.jpeg')

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

### Step7:
* Flip the original image horizontally and display it. 

```python
# Load the image
image = cv2.imread('image.jpeg')

# Flip the image horizontally (left-right)
flipped_horizontally = cv2.flip(image, 1)

# Convert BGR to RGB for displaying with Matplotlib
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)

# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("on")
```

* Flip the original image vertically and display it.

```python
# Flip the image vertically (up-down)
flipped_vertically = cv2.flip(image, 0)

# Convert BGR to RGB for displaying with Matplotlib
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)

# Vertical flip
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("on")
```

### Output

* Original image display
  
   <img width="439" height="291" alt="image" src="https://github.com/user-attachments/assets/795f4ec2-bd71-4d16-8830-d530ad93f069" />

* Draw a line from the top-left to the bottom-right of the image.

   <img width="421" height="287" alt="image" src="https://github.com/user-attachments/assets/2da0f96c-7c9c-4c5b-a94a-c9dade6c487c" />

* Draw a circle at the center of the image.

   <img width="432" height="290" alt="image" src="https://github.com/user-attachments/assets/b54965c2-d5b7-43b2-8662-f4f5ddceec81" />

* Draw a rectangle around  the whole image

   <img width="437" height="292" alt="image" src="https://github.com/user-attachments/assets/7cca3ad7-5388-45a4-8192-3a11856fa2ba" />

* Add the text "SANTHOSH G" at the top-left corner of the image.

   <img width="437" height="285" alt="image" src="https://github.com/user-attachments/assets/b5da11fe-3282-43b7-905c-1905a5ab871f" />

* Convert the image from RGB to HSV and display it.

    <img width="543" height="313" alt="image" src="https://github.com/user-attachments/assets/2d2ae90b-cab9-4b53-b1ab-392fd7c3a8bb" />

* Convert the image from RGB to GRAY and display it. 

    <img width="486" height="298" alt="image" src="https://github.com/user-attachments/assets/041c9d28-2fdd-41b4-bccf-158a06772ed2" />

* Convert the image from RGB to YCrCb and display it. 

    <img width="467" height="302" alt="image" src="https://github.com/user-attachments/assets/53288131-39f0-4e37-b17e-b77d6edc794f" />

* Convert the HSV image back to RGB and display it.

     <img width="970" height="603" alt="image" src="https://github.com/user-attachments/assets/9ad694d8-5a2d-4f86-b8e6-ce7b4caf34ca" />

* Access and print the value of the pixel at coordinates (100, 100) and Modify the color of the pixel at (200, 200) to white.

     <img width="430" height="288" alt="image" src="https://github.com/user-attachments/assets/6dfac4ab-8848-4992-af5d-1bcb139959e3" />

* Resize the original image to half its size and display it.

     <img width="425" height="289" alt="image" src="https://github.com/user-attachments/assets/c0e2288d-bbb3-47d3-b99a-18199133d558" />

* Crop a region of interest (ROI) from the image (e.g., a 100x100 pixel area starting at (50, 50)) and display it.

     <img width="462" height="290" alt="image" src="https://github.com/user-attachments/assets/679f6db2-9f77-46e7-a897-f667d45ff346" />

* Flip the original image horizontally and display it. 

     <img width="459" height="307" alt="image" src="https://github.com/user-attachments/assets/a3bb9057-b8f3-4288-bea4-618e6c1075b4" />

* Flip the original image vertically and display it.

     <img width="513" height="304" alt="image" src="https://github.com/user-attachments/assets/f7a9f179-078e-421c-aae8-f849a07b4df8" />


### Result

Thus, image handling and pixel transformations were implemented using Python and OpenCV. The experiment demonstrates image loading, drawing, color space conversion, pixel manipulation, resizing, cropping, flipping, and saving images successfully.
