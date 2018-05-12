# **Finding Lane Lines on the Road** 

## Writeup by zhong

### This is zhong's writeup file. It described somethings about what I do in this project.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe my pipeline. 
My pipeline consisted of 6 steps . 

First, I converted the images to grayscale.

Second, I apply Gaussian_blur for smoothing the image.

Third, I used the canny to find the edges.

Fourth, I created a masked edges image, let the computer only detect certain areas.

Fifth, Find the pipeline with the Hough transform, It is the most important part, and I will show the details below.

Sixth, Draw the lines on the edges images.

The most important part of find the pipeline is the hough_lines() function, and I modified the draw_lines() function.
In the draw_lines function, First, find the find the longest line which was found by cv2.HoughLinesP() and calculate the line's slope and intercept 
,the slope is greater than 0 is the line on the left ,and the slope is less than 0 is the line on the right.
and then find the latest ten pictures and calculate the mean of the longest straight line found in ten pictures.


### 2. Identify potential shortcomings with my current pipeline


One potential shortcoming would be what would happen when the road is not in the middle of
the image, the program will find the line outside the road.

Another shortcoming could be when a part of the vehicle appears below the image,there will be some disturbing lines.

Cannot automatically locate the effective position of road

### 3. Suggest possible improvements 

A possible improvement would be to remove the interference from the lower line in the image, because if the bottom
of the image has a fixed line of interference, that will probably the body of the vehicle

Another potential improvement could be to let the program take a smaller picture to determine where the road might be.
