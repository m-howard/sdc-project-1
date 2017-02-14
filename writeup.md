#**Finding Lane Lines on the Road** 

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 10 steps. First, I made two copies of the image being worked on. Second, I set thresholds to find the yellow in the image and an white in image, set the pixels that meet the threshold white, and black out the rest of the image. I did because lsne lines are usually yellow or white and setting color thresholds first helps remove soem of the noise. After I had a 2 images that identified the yellow and white found in the image, I merged the images into one image, so one image has both the yellow and white lines identified. Once, I had my color selection image, I converted it to grayscale. Following that, I ran Canny on the image to the grayscale image to detect the edges. Once I have detected the edges I identified my region of interest and removed the edges that were not in that region. Finally, I used hough_lines to draw the lines on the region image and then merged that with the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by taking the image shape and dividing the image in half along the x-axis and dividing into thirds along the y-axis. When I have those dimensions iterated through the lines and put the points of the line in two different buckets, left and right lane line buckets. Line points were put into the left line bucket if the slope was negative and the x value was on the left side of the image, and went into the right line bucket if the slope was positive and on the right side of the image. Once I had the line points in their respective buckets, I used the points to average/extrapolate the lines and draw them.


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when a sharp curve comes about about

Another shortcoming could be that the drawn lines are not very long and if something in the road, it when mess up the average of the lines.


###3. Suggest possible improvements to your pipeline

A possible improvement would be to do some type of prediction of the line from previous image.

Another potential improvement could be to set up a better area of interest or a moving area of interest somehow.

---

### Images
**solidWhiteCurve.jpg**
![Solid White Curve][image1]
[image1] ./test_images/line_solidWhiteCurve.jpg "SolidWhiteCurve"
**solidWhiteRight.jpg**
![Solid White Right][image2]
[image2] ./test_images/line_solidWhiteRight.jpg "SolidWhiteRight"
**solidYellowCurve.jpg**
![Solid Yellow Curve][image3]
[image3] ./test_images/line_solidYellowCurve.jpg "SolidYellowCurve"
**solidYellowCurve2.jpg**
![Solid Yellow Curve 2][image4]
[image4] ./test_images/line_solidYellowCurve2.jpg "SolidYellowCurve2"
**solidYellowLeft.jpg**
![Solid Yellow Left][image5]
[image5] ./test_images/line_solidYellowLeft.jpg "SolidYellowLeft"
**whiteCarLineSwitch.jpg**
![White Car Line Switch][image6]
[image6] ./test_images/line_whiteCarLineSwitch.jpg "WhiteCarLineSwitch"