#**Finding Lane Lines on the Road** 


### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline(the function process_image) consisted of 6 steps:

1. Converted the images to hsv scale. I used the hsv scale instead of grayscale as it is more effective in different lighting conditions, especially in the bonus videos. I defined the ranges to detect the colors yellow and white.
2. Blurred the image with the Gaussian Noise Kernel.
3. Applied Canny transform to detect the edges.
4. Defined and applied the region of interest by setting four vertices.
5. Modified the draw_lines function to draw a thick single line on each side by averaging the points detected in one frame and attempted to smooth the lines shown in the videos by averaging the points with the points from the previous frame.
6. Drew lines with apopropriate hough parameters.



###2. Identify potential shortcomings with your current pipeline

Currently, the draw_lines function only works on the first video. The "ValueError: cannot convert float NaN to integer" seems to come up when a frame does not detect all four points, thus failing to calculate the average points. Also, the lines are still shaking a lot in the videos. 
I am also guessing that the current pipeline can be affected by white or yellow cars within the hsv color threshold values if they are close enough.

###3. Suggest possible improvements to your pipeline

I still need to figure out a way to fix the ValueError. 
As for the shaking lines in the videos, the lines will be smoother if averaged over more frames, such as the previous 10 frames.
