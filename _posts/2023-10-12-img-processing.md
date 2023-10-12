---
layout: post
title:  "Intro to Image Processing in Python"
author: "Camilla McKinnon"
description: "A brief overview of popular python image processing libraries"
image: "/assets/images/photo_dev.jpg"
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

The most popular image processing libraries include OpenCV, PIL, and Scikit-image.

#### OpenCV

efficient and complex and computationally intensive tasks, large community/activre user community, so lots of oncline resources/documentation available

high performance and optimization

#### PIL - Python Imaging Library (also has a popular fork called pillow)

is straight forward and user friendly, simple, ideal 4 beginners and si mple tasks

more intuitive interface for basic image operations like resizing, cropping, and filtering


#### Scikit-image (Also called skimage)

---
---

## Conclusion

There are powerful packages in python you can use to do cool stuff woo!

