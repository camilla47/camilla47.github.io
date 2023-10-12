---
layout: post
title:  "Exploring Image Processing in Python"
author: "Camilla McKinnon"
description: "A brief overview of image processing packages in python"
image: "/assets/images/camera.jpg"
--- 

## Why Image Processing?

Image processing is the manipulation of digital images to extract useful information or to enhance visual quality. I was first exposed to image processing this summer at my internship. We were analyzing the composition of nuclear fuel plates (fancy pieces of metal). The raw radiography scan images were nearly solid gray. We wanted to analyze the differences in color (because that correlated to density). Blalla, used histogram qualization to enhance hte color contrast. 

Image processing covers a variety of something, enhancement of image quality, image compression, pattern recognition, remote sensing, document analysis, biology, science, astronomy, weather, computer science, research in any field, etc. 

## What's out there?

My mentor and I this summer hard coded a histogram equalization functino that scanned each image one pixel at a time. Needless to say, this took FOREVER. Then there was the fateful day we realized opencv had a built in package to do exactly what we wanted (and in like 2 seconds). Bottom line is: Know before you dig! ...oh wait... know before you "code"!

* OpenCV
efficient and complex and computationally intensive tasks, large community/activre user community, so lots of oncline resources/documentation available

high performance and optimization

* PIL

is straight forward and user friendly, simple, ideal 4 beginners and si mple tasks

more intuitive interface for basic image operations like resizing, cropping, and filtering


* Scikit-image (skimage)

---
---

### OpenCV

---
---

### PIL

---
---

### Scikit-image

---
---
## Conclusion

There are powerful packages in python you can use to do cool stuff woo!

