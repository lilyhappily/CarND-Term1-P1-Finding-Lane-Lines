# **Finding Lane Lines on the Road** 

## Overview

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on my work in a written report

---

## Reflection

### 1. My Pipeline

* My pipeline consisted of 6 steps. First, I converted the images to grayscale. Second, I used Gaussian blur to  filter out the image noise so that the edges are more easily and accurately detected. Third, the gray image from Gaussian blur  was given to canny detection to find the edges of the image. Fourth, I used cv2.fillpoly to get the real interesting region including the land lines. Fifth, in order to detect the lines, Hough Transform was used. At last, I drew the detected lane lines on the original images.

* In order to draw a single left line and right line on the original images,  I added a new function called `extrapolate_lines`. Lines from  Hough Transform and original image were the inputs and image drawn left and right lane lines was the output. I separated line segments by their slope `((y2-y1)/(x2-x1))` to decide which segments are part of the left line vs. the right line.  Then, I average the position of each of the lines and extrapolate to the top and bottom of the line.



![whiteCarLaneSwitch](E:\udacity_term1\CarND-LaneLines-P1-master\test_images_output\whiteCarLaneSwitch.jpg)


### 2. Potential Shortcomings 


One potential shortcoming  is that my pipeline is only apt for extremely simple conditions such that  the lanes are straight.  When I used it to the challenge task,  the error appeared that left line's slop was nan. That means my pipeline didn't find the left line .


### 3. Possible Improvements

A possible improvement would be to use Polynomial Fitting to find the left lines and right lines, so that it could be used to detect curve lane lines .
