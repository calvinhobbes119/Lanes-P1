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

My pipeline consisted of 6 steps. 

* First, I applied a mask to extract yellow and white markers in the image.
* Next, I converted the images to grayscale.
* Then I applied a Gaussing blur with a kernel size of 3. 
* Next, I applied Canny edge detection on the blurred image and applied a 4-gon mask to localize around my region of iterest. 
* Then I applied the Hough transform to extract lines corresponding to lane markings. 
* I modified the draw_lines method as follows. I grouped the lines based on whether their slopes were positive or negative, excluded outlier (slope, intercept) points from each group and took the average of the surviving (slope, intercept) values to arrive at the estimate for the (slope, intercept) of the left and right lane markings. I extrapolated these to draw lane markings which extended to the edges of my region of interest.

### 2. Shortcomings with current pipeline
* Lane markings move jerkily from one frame to the next.
* Somtimes no lanes are detected in a frame.

### 3. Possible improvements to your pipeline

* Optimize settings for Hough transform parameters for better performance.
* Limit how much the slope and intercept for lane markings can change from one frame to the next.