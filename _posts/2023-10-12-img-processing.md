---
layout: post
title:  "Intro to Image Processing in Python"
author: "Camilla McKinnon"
description: "A brief overview of popular python image processing libraries"
image: "/assets/images/film_roll.jpg"
--- 

## Why Image Processing?

Image processing is the manipulation of digital images to extract useful information or to enhance visual quality. Image processing can assist with anything from basic photo manipuilation to complex image analysis for research. 

I was first exposed to image processing this summer at my internship. We were analyzing radiography scans of metal fuel plates. We wanted to analyze minute differences in density, but the color difference wasnt' showing up in the scans. We used an image processing technique called histogram equalization to enhance the color contrast. This turned the original solid gray images to a range from black and white, and we were able to continue our analysis. 


## What's out there?

This summer, my mentor and I originally hard-coded our histogram equalization function. It scanned each image one pixel at a time, several times over...needless to say, the function took *forever* to run. Then there was the fateful day I discovered python had an existing library that could do exactly what we wanted. The improved code went down from 100 lines to less than 5, and run time improved greatly. Moral of the story: do your research first before jumping into a project!

#### What kinds of image processing techniques already exist?

Python has several libraries with numerous packages for your image processing needs. With these you can do a variety of thihngs to your images, including:

* Resizing and cropping
* Rotation, flipping, transposing
* Convert files to different formats
* Contour detection (identify boundaries of objects)
* Edge detection
* Feature detection and matching
* Image filtering (techniques to blur, smooth, or sharpen images)
* Image segmentation (divides image into distinct regions or objects
* Color conversion (change between color spaces, such as RGB, BGR, grayscale, etc.)
* Erosion and dilation (used for noise removal, object extraction)
* Thresholding (convert to binary images, partition image to threshold and background)

---
---

## What are the best libraries?

The most popular image processing libraries include OpenCV, PIL, and Scikit-image. There is a lot of overlap between the libraries, but they each have their unique perks.

### PIL

PIL (Python Imaging Library), is part of the Pillow library, and is a great image processing library for beginners. It is simple and straightforward. It has an intuitive interface for basic image operations such as resizing, cropping, and filtering images. 

Here is an example of how to read in an image with PIL:
```
pip install Pillow   # install Pillow if you don't already have it
from PIL import Image

# Open image file
image = Image.open("path_to_your_image.jpg")

# Display information about the image
print("Image format: ", image.format)
print("Image mode: ", image.mode)
print("Image size: ", image.size)

# Display the image
image.show()
```

### OpenCV

OpenCV (Open Source Computer Vision Library) is a popular and versatile library. It has a wide range of packages for tasks related to computer vision, image processing, and machine learning. It also has an active user community, so there are lots of online resources and documentation available.  OpenCV is the best at efficiently running copmlex and computationally intensive tasks, and is known for it's high performance. That being said, OpenCV has a steeper learning curve than PIL, and might be overkill for simple tasks like resizing and cropping photos.  

Here is an example of how to do histogram equalization with OpenCV:
```
import cv2
import numpy as np

# Load image
image = cv2.imread("path_to_your_image.jpg", 0)  # 0 loads the image in grayscale

# Apply histogram equalization
equalized_image = cv2.equalizeHist(image)

# Display the original and equalized images
cv2.imshow('Original Image', image)
cv2.imshow('Equalized Image', equalized_image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

### Scikit-image (Also called skimage)

---
---

## Conclusion

There are powerful packages in python you can use to do cool stuff woo!

