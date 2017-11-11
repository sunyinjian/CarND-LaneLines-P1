# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

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

My pipeline consisted of 5 steps. 

1) Apply COLOR_RGB2BGR to the image, and apply the Grayscale transform;
2) Apply a Gaussian Noise kernel, and apply the Canny transform;
3) Apply an image masked region using trapezoid-shaped polygon;
4) Run HoughLinesP on masked image
5) Draw lane lines by averaging and extrapolate the line segments


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

1) Filter all the lines by slopes, if abs(slope) > slope_threshold, retain the pipeline
2) Find fitted line for left and right lane line, set the max and min x and y of lane line 
3) Run the linear regression to find the best fit line for right and left lane lines 

If you'd like to include images to show how the pipeline works, here is how to include an image: 

1) call the process_image function, run white_clip = clip1.fl_image(process_image)
![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...
The method of pipeline detection works not well in the following situation:
1) when the lane line is curve
2) when the lane line is covered by the vehicle
3) when the lane line is detected at night
Also, the result of pipeline detection is sensitive to parameter tuning, which works well in specific scenarios 



### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...

Machine learning could be suggested to train the pipeline detection in large quantities of sample, so that the pipeline detection is applicable in any scenarios.
