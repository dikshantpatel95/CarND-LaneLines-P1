#Finding Lane Lines on the Road

Finding Lane Lines on the Road

The goals / steps of this project are the following:

1. Make a pipeline that finds lane lines on the road
2. Reflect on your work in a written report


My pipeline consisted of the following steps:

Step1: Reading the original image.

<img src="https://github.com/dikshantpatel95/CarND-LaneLines-P1/blob/master/test_images/solidWhiteCurve.jpg" width="450">


Step2: RGB Thresholding to get all the colours aboove yellow.

<img src="https://github.com/dikshantpatel95/CarND-LaneLines-P1/blob/master/color_thresh_images/solidWhiteCurve.jpg" width="450">


Step3: Gray scaling.

<img src="https://github.com/dikshantpatel95/CarND-LaneLines-P1/blob/master/grayscale_images/solidWhiteCurve.jpg" width="450">


Step4: Gaussian Smoothing.

Step5: Canny Edge Detection and Region Of Interest Selection.
I updated the region of interest, I select only the region of the lanes i have two areas of interest in the image one area for left lane marker and another for the right lane marker.

<img src="https://github.com/dikshantpatel95/CarND-LaneLines-P1/blob/master/canny_images/solidWhiteCurve.jpg" width="450">


Step6: Hough Transform Detection with overlay on original image.

<img src="https://github.com/dikshantpatel95/CarND-LaneLines-P1/blob/master/output_images/no_pipeline/outputsolidwhite.jpg" width="450">


Step7: Hough Transform Detection - with Solid lines overlay on image

<img src="https://github.com/dikshantpatel95/CarND-LaneLines-P1/blob/master/output_images/solid_lines/solidWhiteRight.jpg" width="450">



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
