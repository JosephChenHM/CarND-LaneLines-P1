# **Finding Lane Lines on the Road** 

## Overview

### In this project, I use Open Computer Vision to detect lane lines and Python for development 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a image processing pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. 
1.  Converted image to grayscale
2.  Apply gaussian blur to reduice noise
3.  Use OpenCV canny function to detect contour 
4.  Apply region of interest to fouse on lane line
5.  Use OpenCV Hough transform for finding line segment
    1.  Filter inconsist slope of line by average all the slope  
    2.  Use average slope to extrapolate line
6.  Draw lane line onto image


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by 

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when line line is covered by shadow. Lane line will place in wrong position. 

Another shortcoming could be curve lane line. My pipeline can't correctly mapping on image/video.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to using HSL color space to identify lane line. Removing lightness condition for stable detection

Another potential improvement could be to rewrite my Hough line average function. Instead of recalculating new slope of lane line, try to weight previous slope and new slope proportional for new slope.
