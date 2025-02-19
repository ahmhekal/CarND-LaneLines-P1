# **Finding Lane Lines on the Road** 

## Writeup Template

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteCurve.jpg_gray.jpg "Grayscale"
[image2]: ./test_images_output/solidWhiteCurve.jpg_gaussian.jpg "Grayscale"
[image3]: ./test_images_output/solidWhiteCurve.jpg_canny.jpg "Grayscale"
[image4]: ./test_images_output/solidWhiteCurve.jpg_masked.jpg "Grayscale"
[image5]: ./test_images_output/solidWhiteCurve.jpg_hough.jpg "Grayscale"
[image6]: ./test_images_output/solidWhiteCurve.jpg_output.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps:
#### 1. I converted the images to grayscale.
#### 2. I used gaussian blur to smooth the images.
#### 3. I used canny function to detect the edges in the images.
#### 4. I used a polygon mask to select a certain region of interest (that contains lane lines) by using four appropriate vertices.
#### 5. I used hough_lines() function which reterns an image with the two lines (one line on the left and another one on the right to represent the lane lines) by:
  - calling "cv2.HoughLinesP" function that reterns a list of all lines in the image
  - creating a zero dark image to draw the lines on
  - calling draw_lines() function which takes the list of lines. Each line is known by two points (x1, y1), (x2, y2) and this function is used to draw only one line to the right and one line to the left by :
     - _looping through all the lines and extend all the lines to reach the borders of the interest area_
     - _To end up with one line on the left and one line on the right we need two points on the right and two points on the left. We already know the y1, y2 for all the lines which are the start and end y dimension of the region of interest. Now we want to calculate x1, x2 for the line on the right and x1, x2 for the line on the left. And we have a punch of points for each line; so I took the average of x1's and x2's on the right, and x1's and x2's on the left and named them as x1, x2, x11, x22 repectively. Now I have x1 and x2 for the line on the right (and also I have already y1 and y2). and the same thing for the left line._
      - _Finally I drew the two lines using cv2.line() function_


---


Images to show how the pipeline works: 
### grayscale Image
![alt text][image1]



### After gaussian blur
![alt text][image2]



### After canny edge detection
![alt text][image3]



### After masking to the interest rate
![alt text][image4]



### After hough drawing lines
![alt text][image5]



## The Final Output !!
![alt text][image6]






### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the lane line become curvy because I'm setting a fixed value of y1 of the line and I draw only one straight line to the right and another one to the left.

Another shortcoming could be when the color changing due to a shadow od a tree or something.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to change the fixed value of y1 of the line

Another potential improvement could be to use color correction or something to overcome the change of the color

