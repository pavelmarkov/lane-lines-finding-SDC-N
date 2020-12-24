# UdacitySelf-DrivingCar

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

[image2]: ./images_for_report/extrapolated_lines.png "Test my my pipeline on test images"
[image3]: ./images_for_report/test_on_video.gif "Test my my pipeline on test video"

---

### Reflection

### 1. Describing a pipeline and the draw_lines() function.

My pipeline consisted of 5 steps:
1. Convert image to grayscale

![grayscale_image](/images_for_report/gray.png)

2. Use GaussianBlur with parameter kernel_size=5 to blur the grayscale image

![blured_image](/images_for_report/blur.png)

3. Apply the Canny transform to the blur image to find edges

![edges](/images_for_report/edges.png)

4. Keep only the region with lane lines by applying an image mask

![region_of_interest](/images_for_report/region.png)

5. Find lines on region of interest using HoughLinesP with parameters rho=1, theta=1/180, threshold=30, min_line_len=10, max_line_gap=10.

After applying these steps to test images I've got the following result:

![pipeline_result](/images_for_report/image_with_lines.png)


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by dividing all lines by their slope into two groups: "left lane lines" (slope is less than zero) and "right lane lines" (slope is greater than zero), then calculating average slope and intercect for each group and using this data to draw only two lines from the bottom of the image (top of coordinate plane) to the center.

Such method gives good results on test images:

![test on image][image2]

Also, test this method on video:

<img src="./images_for_report/test_on_video.gif" width="426" height="240" />

### 2. Identifying potential shortcomings with the current pipeline


One potential shortcoming would be what would happen when there are other objects in the region of interest, parts of which could detected like lines by "HoughLinesP" function. For example, car ahead or roadside edge. Such lines can affect position and angle of the lane lines.

Another shortcoming could be winding road. By using "HoughLinesP" function we're looking for straight lines, it could be difficult to find them on winding road with curved lines.


### 3. Suggesting possible improvements to the pipeline

A possible improvement would be to filter detected lines by their slope, since absolute value of lane lines slope lies between 0.5 and 1.5. Such approach allow us to eliminate "noise lines" detected on other objects (cars, sidewalk, roadside) in the region of interest. 

Another potential improvement could be implementing a method for finding curved lines on image.
