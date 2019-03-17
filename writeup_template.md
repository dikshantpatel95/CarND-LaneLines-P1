#Finding Lane Lines on the Road

Finding Lane Lines on the Road

The goals / steps of this project are the following:

Make a pipeline that finds lane lines on the road
Reflect on your work in a written report


My pipeline consisted of the following steps:

Reading the original image.


RGB Thresholding to get all the colours aboove yellow.


Gray scaling.


Gaussian Smoothing.


Canny Edge Detection.


Region Of Interest Selection.


Hough Transform Detection.


Hough Transform Detection - with Solid lines


Overlaying the detected lane(s) on top of the original image.


Output Video(s) :

solidWhiteRight.mp4
solidYellowLeft.mp4
challenge.mp4
For the challenge video, I had to update the region of interest, I select only the region of the lanes i have two areas of interest in the image one area for left lane marker and another for the right lane marker.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by :

Categorizing the line segment(s) from hough transform within the region of interest, into left lane, or right lane, using the slope. ( > 0, or < 0).
I use slope threshold to find lines with slopes between the thresholds to make sure i only have the lane lines. (m>0.45 and m<0.8-right_slope)
I find the mean left and right slope from the all the available then compute x1 when y=Ymax and x2 when y=340 and  of image then draw line from (x1,Ymax) to (x2,340).

Potential shortcomings:

Currently towards the far end of the pipeline if there is a car within the region of interest, it shows up. I need to find a better way of excluding such objects from region of interest.
The lane lines drawn jitter a lot due to the mean slope variation.
The pipeline does't work for extremely curved roads 

Potential improvements:

Dynamic region of interest generation - currently this is hard coded.
Draw lines functions need to be made smarter by connecting different hough lines unlike by taking mean slope like i implemented.
The output can be smoothened further.
Better handling of curved line(s).