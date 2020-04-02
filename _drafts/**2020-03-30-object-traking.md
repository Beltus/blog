---
layout: single
published: true
title: Object Tracking OpenCV
collection: cv
author_profile: false
read_time: true
categories: [project] #[tutorials]
excerpt : " Tracking any object using your webcam, how cool is that. Let me show how."
header :
    overlay_image: "https://beltus.github.io/vision/assets/images/galaxy.png"
    teaser: "https://beltus.github.io/vision/assets/images/object_small.jpg"
comments : true
toc: true
toc_sticky: true
---

![Photo by Immo Wegmann on Unsplash](https://beltus.github.io/vision/assets/images/object.jpg)

If you are stuck home like the rest of world, and sick of counting the number of new corona virus cases like I am. Then it's time to a break from the chaos and apocalyptic news on social media. Join me lets build a fun computer vision object tracking application.

Here is youtube video demonstration of our final project.

{% include video id="6nJH1mtJrJU" provider="youtube" %}

If you are fired up like I am then let's do this!

## Requirements
For this project, the core library I am using is openCV. The methods you will see shortly have been implemented in the OpenCV package. In addition, I am running my code on jupyter notebook.

The code is written using python 3. Feel free to use whatever environment is suitable for you, but make sure that, opencv has been installed properly depending on the computer system you are using.

## Step 1: Import relevant Libraries
```python
import cv2
import numpy as np
```
We need access to openCV built-in methods, so we import it as above. Numpy library is always handy for mathematical manipulations.

## Step 2: Set Color Thresholds.
```python
#sets lower threshold for blue color
color_lower = np.array([150 , 50 , 0] , dtype = 'uint8');

 #sets upper threshold for blue color
color_upper = np.array([255, 150 , 100] , dtype = 'uint8');
```
First we need to set the lower and upper threshold of the color of the object we want to track. In this project, I am tracking a blue object, that is why my  values for the blue color channel are much higher than the others. Here is a link to help you select color of your own object to track.

## Step 3: Tracking the Object.
At the end of this step, I have provided the entire code block. However, to ease understanding, I will explain sections of the code allowing you to have an in-depth feel of what is going on. So lets get to it.

* **Capture Video** from our WebCam. If you have a pre-recorded  video, you could load it using same function by passing the file name of the video as argument to the function like this ***cv2.VideoCapture('video_filename')***

```python
capture = cv2.VideoCapture(0)
```
*  It is important to know that a video is simply a sequence of images called frames, displayed at a particular frame rate. So the idea is that, we are actually detecting faces and eyes in each frame in the video stream. Frames are extracted from the video with the code.

```python
ret, frame = capture.read()

```
* **Threshold Video Frame** based on the lower and upper color threshold limits set above. The **cv2.inRange()** returns a binary image with pixels that fall with the color range set to white(255) and the rest set to black(0)

```python
color_threshold = cv2.inRange(frame, color_lower, color_upper)
```
* **Filter thresholded image** by applying **Gaussian Blur** to the binary image to reduce noise resulting from the thresholding operation and improve object tracking.

```python
 = cv2.GaussianBlur(color_threshold, (3,3) , 0)
```

* **Find Contours of Object** using the ***cv2.findContours()*** method that returns a list of contours each corresponding to detected object boundaries. Note a copy of the original binary image is made as this function is destructive.

```python
(cnts , _)  = cv2.findContours(blur.copy() , cv2.RETR_EXTERNAL , cv2.CHAIN_APPROX_SIMPLE)
```
* **Find Minimum Bounding Box** around the detected object using the ***cv2.minAreaRect()*** function.

```python
bbox = cv2.minAreaRect(cnt)
```
* Next we draw Bounding boxes around the detected object using the ***cv2.drawContours()*** method back unto the original video frame

```python
cv2.drawContours(frame, [rects] , -1 , (0,255,0) , 2 )
```

* Finally display the **Tracking of Object**

```python
cv2.imshow("Tracking...", frame)
```
Here is the complete block code for all the steps explained in this section.

```python
capture = cv2.VideoCapture(0)

while True:

    ret, frame = capture.read()

    #threshold based on color
    color_threshold = cv2.inRange(frame , color_lower , color_upper);

    blur = cv2.GaussianBlur(color_threshold , (3, 3) , 0); # to reduce noise and increase detection of the tracking of our object

    #cv2.findContours is used to get the contours corresponding to the object.
    (cnts , _)  = cv2.findContours(blur.copy() , cv2.RETR_EXTERNAL , cv2.CHAIN_APPROX_SIMPLE);


    if len(cnts) > 0:

      # sorts the list of contours from largest to smallest and returns the largest based on area
        cnt = sorted(cnts , key = cv2.contourArea , reverse = True)[0] (cv2.contourArea)

        #cv2.minAreaRect() computes the mininimum bounding box around the contour,
        bbox = cv2.minAreaRect(cnt)

        # BoxPoints()converts these bounding box to list of points #
        rects = np.int0(cv2.boxPoints(bbox))

        # Draw a bounding around object.
        cv2.drawContours(frame , [rects] , -1 , (0, 255, 0) , 2);

    #Tracking object    
    cv2.imshow('Tracking In Progress'  , frame) ;

    #show the thresholded image
    #cv2.imshow('Threshold' , color_threshold);

    #time.sleep(0.0025);

    key = cv2.waitKey(30) & 0xff

    if key == 27:
        break;

capture.release();

cv2.destroyAllWindows()
```


For the complete code, visit my [github page](https://github.com/Beltus/Computer-Vision-Projects/tree/master/EYE%20TRACKING).


## The Takeaway
In this post, we have seen how to track an object based on it's color in a video stream using a combination of some interesting opencv functions. The project will more fun
I hope you had fun implementing this cool project. If you have any questions, please, leave a comment below, I will be happy to help. Make sure you subscribe so you can get notified immediately I drop another fun project.

Stay safe.
