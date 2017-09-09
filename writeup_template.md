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

My Lane Lines Detection pipeline consisted of 6 sequential steps. They are as follows:

1) Convert the image to grayscale. Most of the extra data that makes up color in the picture will not help us a lot but will slow down the pipeline.

2) Using Gaussian Blur, smooth out the lines in the image. This step is helpful for our next step.

3) Apply Canny Edge detection to the image to produce a near black and white image of just lines and outlines. This helps further reduce the amount of data the pipeline needs to process and leaves the most essential for our purposes -- the lines!

4) Next we created an image mask to just focus on the trapezoidal part of the image that we know will contain the lane lines we want to analyze and not other superfluous line data.

5) We then use a Hough Transformation on the image mask to 'vote' on the 'things' we think most look like lines.

6) No we have finally isolated the left and right lane lines from our image and we re-apply these now 'highlighted' lines back to the original image and see how we did!


### 2. Identify potential shortcomings with your current pipeline

This pipeline is great for long, mostly-straight highways. One potential shortcoming is that the image mask would make a windy-curvy road very hard to detect lane lines as the mask is mostly focused straight ahead.

Also, some roads have only reflectors as the the lane divider. This pipeline wouldn't do a great job in detecting only those.

### 3. Suggest possible improvements to your pipeline

With faster computing power, I could play with the parameters of the Hough Transformation, selecting for the parameters that produced the best selection of lines.
