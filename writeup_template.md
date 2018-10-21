# **Finding Lane Lines on the Road** 

## Writeup Template

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

My pipeline consisted of 5 steps:
#### 1. I converted the images to grayscale.
#### 2. I used gaussian blur to smooth the images.
#### 3. I used cany function to detect the edges in the images.
#### 4. I used a polygon mask to select a certain region of interest (that contains lane line) by using four appropriate vertices.
#### 5. I used hough_lines() function which reterns an image with the two lines (one line on the left and one line on the right to represent the lane lines) by:
  * calling "cv2.HoughLinesP" function that reterns a list of all lines in the image
  * creating a zero dark image to draw the lines on
  * calling draw_lines() function which takes the list of lines each line is known by two points (x1, y1), (x2, y2) and this function is used to draw only one line to the right and one line to the left by :
        - looping through all the lines and extend all the lines to reach the borders of the interest area
        - To end up with one line on the left and one line on the right we need two points on the right and two points on the left. We already know the y1, y2 for all the lines which are the start and end y dimension of the region of interest. Now we want to calculate x1, x2 for the line on the right and x1, x2 for the line on the left. And we have a punch of points for each line; so I took the average of x1's and x2's on the right, and x1's and x2's on the left and named them as x1, x2, x11, x22 repectively. Now I have x1 and x2 for the line on the right (and also I have already y1 and y2). and the same thing for the left line.
        - Finally I drew the two lines using cv2.line() function

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
