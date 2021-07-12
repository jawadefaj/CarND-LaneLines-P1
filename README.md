# **Finding Lane Lines on the Road** 

## Writeup 

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


My pipeline consist of 6 major steps. I named the function detectLines that takes in the image, and two threshold value for cropping ROI. In the first step 
I am creating a grayscale image of the given image. The output of the grayscale then get blurred by using gaussian blur. The blurred image then goes into the 
openCV canny edge detection part. I used lower threshold = 50 and upper threshold = 150. I am then creating a mask using the threshold parameter. The output 
of this phase goes into the hough_lines function. In the hough_lines function I am calling the draw_lines method. This method filters some of the outlier lines and 
separate the left and right lines based on positive and negative slope. I used polyfit from numpy to determine the slope and y_intercept. The final left and right lines 
are created by avaraging the slope and y_intercept.  


### 2. Identify potential shortcomings with your current pipeline
One major shortcoming of the pipeline is that it is not robust. It performs really bad in curved roads. Also if the color of the asphalt changes (different shades of black/gray)
it detects that changed color as a road marking and outputs abnormal lines.  



### 3. Suggest possible improvements to your pipeline

One possible improvement can be to track the parameters in subsequent frames of the video. That way the line detection will be improved. Another 
improvement could be to use adaptive parameter for different algorithms used for the line detection, such as canny, hough transform, etc. 
