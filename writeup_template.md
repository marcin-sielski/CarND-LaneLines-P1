# **Finding Lane Lines on the Road** 

## Writeup

### Computer Vision is just a first step towards self driving cars. Finding Lane Lines on the Road is one of primarly issues autonomous system must address (e.g. lane assistant).

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteCurve.jpg "Original image"
[image2]: ./test_images_output/filter_solidWhiteCurve.jpg "Filter lane lines by color"
[image3]: ./test_images_output/grayscale_solidWhiteCurve.jpg "Grayscale"
[image4]: ./test_images_output/blur_solidWhiteCurve.jpg "Gaussian blur"
[image5]: ./test_images_output/canny_solidWhiteCurve.jpg "Canny transform"
[image6]: ./test_images_output/region_solidWhiteCurve.jpg "Region selection"
[image7]: ./test_images_output/hough_solidWhiteCurve.jpg "Hough lines"
[image8]: ./test_images_output/weighted_solidWhiteCurve.jpg "Augmented image"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 8 steps as listed below:
* convert the images from BGR to RGB,
![alt text][image1]
* filter white and yellow color lanes,
![alt text][image2]
* covert images to the grayscale,
![alt text][image3]
* smooth the images with Gaussian blur,
![alt text][image4]
* detect edges with Canny algorithm,
![alt text][image5]
* narrow the immages to the area of interest,
![alt text][image6]
* apply hough lines to the images,
![alt text][image7]
* convert resulted images from RGB to BGR and combine with orginal image
![alt text][image8]

In order to draw a single line on the left and right lanes I have:
* modified the draw_lines() function by filter out vertical lines and lines with inappropriate slopes (0.5 < | slope | < 0.8),
* extrapolated all the detected lines in the image into single line,
* averaged it with lines calculated for previous images if configured 

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when test data include images with blue lines used in some countries.

Another shortcoming could be what would happen if the test data include images with sharp tunrs or intersections


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to filter blue lines.

Another potential improvement could be to potentially use Polynomial regression instead of straight lines.
