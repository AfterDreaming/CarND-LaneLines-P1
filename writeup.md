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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, 

[image2]: ./step_images_output/gray.png "Grayscale"

then I applied Gasussion filter to the image to make the image smoother,

[image3]: ./step_images_output/gaussian.png "Gaussian"

Then I used Canny algorithm to detect edges in the image. 

[image4]: ./step_images_output/canny.png "Canny Edges"

Because there are many non-insterested edges in the processed image, I clipped necessary area using region_of_interest()
function. 

[image4]: ./step_images_output/interest.png "Canny Edges"

To draw the lane based on the edges in the image, I leverage Hough Transformation and merge the lane image with origin image finallly. 

[image5]: ./step_images_output/lines.png "Lane Lines"

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by finding the left/right lane(line) coefficients and drawing the lanes by passing 
absolute points with respected to the image.


### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be what would happen when the road absolute position is in the image changed dramatically. Because the lane interested area is fixed, we might not be able to 
find the lane in the insterested area if such situation happens.

Another shortcoming could be the lane has to be a straight line. The pipeline cannot draw curve lines without improvement. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to add an algorithm to detect the insterested area dynamically. The implementation can be K-mean clustering.

Another potential improvement could be to add fitted line degrees in the draw_lines function. Currently, we are using degree 1 to draw a lane. If we can use degree 2 or higher to fit the lane, we are able to draw lanes with much more complex shape.
