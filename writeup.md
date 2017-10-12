## Reflection

My pipeline consists of the following:
1. Convert image into grayscale
2. Blur image with kernel size of 5
3. Find edges using canny with low_threshold of 150 and high_threshold of 200
4. Create a trapezoid as region of interest
5. Pass the image into hough transform
6. Finally apply the original image to the output image after hough transform

During the hough transform (in step 5), the following is performed:
1. Call (OpenCV) HoughLinesP
2. Create a new blank image
3. Draw line. For each line do the following:
    1. Calculate the slope between 2 points
    2. Check for the following:
        1. Is slope 0
        2. Are positive slopes on the right half side of the screen
        3. Are positive slopes between 0.52 and 0.75
        4. Are negative slopes on the left half side of the screen
        5. Are positive slopes between -0.88 and -0.63
4. Once we did that, we have an array of points belonging to left and right of screen
5. Find the min and max y coordinate points in those respective list
6. We can now find the line equation from the two point
7. We can now draw a line from mid-screen to end of the screen

## Shortcomings
The lines are very sensitive. It’s very shaky.

## Improvements
Figure out how to average the lines between each frame
