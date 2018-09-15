# **Finding Lane Lines on the Road** 

---

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road

---

### 1. Approach to the lane detection
The codes are consisted of 5 steps:
1. Apply grayscale on the extracted image
2. Use Gaussian Blur to suppress noise and spurious gradients
3. Use Canny Edge detection to detect points potentially relevant to the lane lines
4. Select the region of interest based on the image processed by the Canny Edge detection
5. Connect the detected points to construct lane lines by Hough Transform
6. Show the detected lane lines on the origial image

Besides, the function draw_lines is modified as follows:
1. Segment the lines achieved by Hough Transporf into left and right lane lines by their slopes
2. Find the first degree polynomial equation to fit points of the left and right lane lines repectively
3. Extrapolate the lines to the top and bottom of the lanes

### 2. Potential shortcomings

The approach stated before may have following shortcomings:
1. The position of detected lane lines don't always change smoothly
2. This method cannot detect curved lane lines
3. This approach isn't robust when the camera is adjusted

### 3. Possible improvements

In order to resolve the problems above, there are some potential improvements:
1. Preprocess the image using HSV,RGB or InRange to extract certain features so that Canny Edge Detection works more effectively
2. Kalman-Filter could be used to identify the current lane line based on the detected lane line of the last time step
3. Use higher degree polynomial equation or other methods to process pointes detected by Hough Transform
4. Use parameters relavent to the size of the image instead of concrete numbers in the algorithm
