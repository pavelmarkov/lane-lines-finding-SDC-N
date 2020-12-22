# UdacitySelf-DrivingCar
![GitHub Logo](/foo.png)

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
[image2]: ./foo.png "Test my my pipeline on test images"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 
1. Convert image to grayscale
2. Use GaussianBlur with parameter kernel_size=5 to blur the grayscale image
3. Apply the Canny transform to the blur image to find edges
4. Keep only the region with lane lines by applying an image mask
5. Find lines on region of interest using HoughLinesP with parameters rho=1, theta=1/180, threshold=30, min_line_len=10, max_line_gap=10.
After applying these steps to test images I've got the following result:
![alt text][image2]


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
