---
layout: single
published: true
title: Face and Eye Tracking Application
collection: cv
author_profile: false
read_time: true
categories: [project] #[tutorials]
excerpt : " This project is a fun and exciting computer vision project for anyone out there wishing to have a taste of what computer vision is. Who know? Your journey might start here."
header :
    overlay_image: "https://beltus.github.io/vision/images/galaxy.png"
    teaser: "https://beltus.github.io/vision/images/eye_face.jpeg"
comments : true
toc: true
toc_sticky: true
---

![](https://beltus.github.io/vision/images/eye_face.jpeg)

By the end of this project, you have a cool face and eye tracking project you will be proud of.

![Alt Text]((https://beltus.github.io/vision/images/eye.gif)


In my previous article, I implemented a face detector using the famous HAARCASCADE classifier. So, this time around, I decided to spice things up a little bit by implementing a simple face and eye tracker using my webcam. For those who are unfamiliar with HAARCASCADE Classifier or OpenCV you can [click here](https://beltus.github.io/vision/project/face-detection/) for more information

This project is a simple yet exciting computer vision project for any one out there wishing to get their hands dirty on some cool stuff. So, if you are as excited as I am, then lets get down to business.

## Requirements
For this project, the core library I am using is openCV. The methods you will see shortly have been implemented in the OpenCV package. In addition, I am running my code on jupyter notebook. The code is written using python 3. Feel free to use what ever environment is suitable for you, but make sure that, opencv has been installed properly.
[install opencv]

## Step 1: Import relevant Libraries
```python
import cv2
import numpy as np
```
We need access to openCV. So we import it and also numpy library is always handy for mathematical manipulations.

## Step 2: Initialize HAAR CASCADE Classifier.
```python
#path to face and eye haarcascades  XML files respectively
facePath = '/home/beltus/image/frontalFace10/haarcascade_frontalface_default.xml';
eyePath = '/home/beltus/image/frontalEyes35x16XML/haarcascade_eye.xml'

#Initialize the classifiers
faceCascade = cv2.CascadeClassifier(facePath)
eyeCascade = cv2.CascadeClassifier(eyePath)
```
OpenCV has implemented the Haarcascade classifier which can be used to detect many different objects. In our case, we are interested in tracking faces and eyes. For the classifier to know what it will be classifying, we need to initialize with the correct XML serialized file. You can download the XML files from [opencv github repository](https://github.com/opencv/opencv/tree/master/data/haarcascades).
The first 2 lines point to the directory of the XML files for both the face and eye respectively.
The *cv2.CascadeClassifier()* method is used to deserialize the classifier, load it into memory, and allows us to detect faces and eyes in images as we will see in the next step.

## Step 3: Tracking Face and Eyes.
The code block below is implemented based on the steps I am going to explain below. Before looking at the code, it is important to get an understanding of the flow of the project. So lets get to it.

*  The webcam in our computers is first activated. Note you could load any video file using same function by passing the file name of the video as argument to the function below

```python
capture = cv2.VideoCapture(0)
```
*  Note that a video is simply a sequences of images called frames, displayed at a particular frame rate. So the idea is that, we are actually detecting faces and eyes in each frame in the video stream. Frames are extracted from the video with the code.

```python
ret, frame = capture.read()

```
* Resize the frame to increase the speed of processing of the images.

```python
resize_frame = cv2.resize(frame, None, fx = 0.5, fy = 0.5, interpolation = cv2.INTER_AREA)
```
* Convert the resized frame to gray scale to increase the efficiency of HAARCASCADE classifier

```python
gray_frame = cv2.cvtColor(resize_frame, cv2.COLOR_BGR2GRAY)
```
* Detect Faces found in the gray scale frame using face HAARCASCADE classifier initialize earlier. the ***detectMultiScaler()*** method returns a list of [turples](https://www.tutorialspoint.com/python/python_tuples.htm). Each turple contains contains the (x,y) coordinates and width and height of a detected face. Click [here](https://docs.opencv.org/2.4/modules/objdetect/doc/cascade_classification.html) for more information. Play aroud with the parameters and see how that affects your classifier.

```python
face_rects = faceCascade.detectMultiScale(gray_frame, scaleFactor = 1.05, minNeighbors = 5 , minSize = (30,30))
```
*  Eyes can only be found where there is a face, so it is smart that we try to detect eyes only in the regions of the frames where a face has been detected. For every detected face, we extract the region of the image with the face, then call our eye HAARCASCADE classifier detectMultiScale method to do its job.

```python
eye_rects = eyeCascade.detectMultiScale(face, scaleFactor = 1.1 , minNeighbors = 10 , minSize = (15,15))
```
*  Draw Bounding boxed around the detected faces and eyes.

```python
drawFace  = cv2.rectangle(resize_frame , (fx, fy) , (fx+fw , fy + fh) , (255, 0, 0), 2)

drawEye = cv2.rectangle(resize_frame , (fx + ex , fy + ey) , (fx + ex + ew , fy + ey + eh) , (0 , 255, 0) , 2)

```

* Finally we can display the faces and eyes being tracked.

```python
cv2.imshow("Tracking...", resize_frame)
```
Here is the complete block code for all the steps explained in this section.

```python
## activate webcam
capture = cv2.VideoCapture(0)

## iterate through all the frames (image)
while True:

    #read video frame by frame
    ret, frame = capture.read()

    #resize frame to half its width and height
    resize_frame = cv2.resize(frame, None, fx = 0.5, fy = 0.5, interpolation = cv2.INTER_AREA)

    #convert resized image to grayscale
    gray_frame = cv2.cvtColor(resize_frame, cv2.COLOR_BGR2GRAY)

    ## detect faces in each image
    face_rects = faceCascade.detectMultiScale(gray_frame, scaleFactor = 1.05, minNeighbors = 5 , minSize = (30,30))

    #loop over all the detected faces
    for (fx, fy, fw , fh) in face_rects:

        #Extract the region of image for which face was detected
        face = gray_frame[fy: fy+fh ,  fx: fx+fw ]

        # draw a bounding box around the detected face
        drawFace  = cv2.rectangle(resize_frame , (fx, fy) , (fx+fw , fy + fh) , (255, 0, 0), 2)

        #detect the eyes found in the detected faces
        eye_rects = eyeCascade.detectMultiScale(face, scaleFactor = 1.1 , minNeighbors = 10 , minSize = (15,15))

        #loop over each detected eye
        for (ex, ey, ew , eh) in eye_rects:

            #draw a bounding box around the detected eye
            drawEye = cv2.rectangle(resize_frame , (fx + ex , fy + ey) , (fx + ex + ew , fy + ey + eh) , (0 , 255, 0) , 2)
            #fX + eX, fY + eY, fX + eX + eW, fY + eY + eH

    #show output video
    cv2.imshow("Tracking...", resize_frame)


    #press ESC key to end video
    k = cv2.waitKey(30) & 0xff # press ESC to exit
    if k == 27:
            break

#release camera            
capture.release()
cv2.destroyAllWindows()
```


For the complete code, visit my github page.

I hope you had fun implementing this cool project. If you have any questions, please, leave a comment below, I will be happy to help. Make sure you subscribe so you can get notified immediately I drop another fun project.

Stay save.
