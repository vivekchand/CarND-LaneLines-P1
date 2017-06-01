# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consists of the following steps:

1. Convert RGB image to Grayscale image
2. Apply a slight Gaussian blur to smooth the image by setting a kernel size of 3
3. Perform Canny Edge detection
4. Define region of interest & mask away undesired portions of the image
5. Retrieve Hough lines
6. Apply lines to the original image

In order to draw a single line on the left and right lanes, I modified the draw_lines() function. This function works as follows:
 
1. Classify left & right lanes based on the slope.
2. Compute average of lines each side
3. Calculate the slope & intercept of each average line 
4. Using the slope & intercept, extrapolate the line to the bottom and apex of the lane
5. Plot the extrapolated line

[![SolidWhiteRight](https://img.youtube.com/vi/T0DzKimgPYw/0.jpg)](https://www.youtube.com/watch?v=T0DzKimgPYw)

[![SolidYellowLeft](https://img.youtube.com/vi/xU154sBDc-Q/0.jpg)](https://www.youtube.com/watch?v=xU154sBDc-Q)


### 2. Identify potential shortcomings with your current pipeline

Although the pipeline works on the first two videos, Some changes are required for third video to work.
It currently works only for straight lanes. If the road has bends / curves, the lane detection fails. 
I will resubmit the solution, if I could tweak to get the challenge video lane detection working.

### 3. Suggest possible improvements to your pipeline

* A lot of improvements can be done, If I take an example of lane lines here in Bangalore, India.
They are'nt well maintained. Optimizing lane detection for low-contrast images is important.
Also rather than detecting lane lines, it should probably make / suggest a lane line given a car dimensions & available area
around the car.

* Also applying ML to this problem could optimize it by looking at the past frames.

* The tuning of hough transform & edge detection has to be improved & should be automated.

* Calculation of region & color mask range can be automated

