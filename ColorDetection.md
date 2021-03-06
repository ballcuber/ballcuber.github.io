---
layout: page
title: Color detection
permalink: /color-detection/
---

Defining the 96 facets colors is possible by hand in the supervisor, but it is a very <b>laborious</b> task, as you can see :


<div class="col-12"><span class="image fit"><img src="/assets/cube-manual-definition.gif" alt="Manual color definition of the cube"></span></div>

That's why we decided to develop an <b>automatic color detection</b> with a camera. First, we want this to be independent of the robot in order not to disturb mechanical tunings. Moreover, image processing is very empirical and dependent of the brightness, so we have created a dark enclosure with controlled lightning and designed so that the camera can scan 3 faces at a time. Then, the cube is flipped in order to scan the 3 other faces.
That's why we decided to develop an <b>automatic color detection</b> with a camera. First, we want this to be independent of the robot in order not to disturb mechanical tunings. Moreover, image processing is very empirical and dependant of the brightness, so we have created a dark enclosure with controlled lightning and designed so that the camera can scan 3 faces at a time. Then, the cube is flipped in order to scan the 3 other faces.
The camera is a low-cost 640x320 Logitech USB webcam, but it's sufficient.

<div class="box alt">
    <div class="row uniform 50%">
        <div class="6u"><span class="image fit"><img src="/assets/scan-tower-CAD-model-annotated.png" alt="Scan tower CAD model" /></span></div>
        <div class="3u"><span class="image fit"><img src="/assets/scan-tower-with-cube-photo.png" alt="Scan tower photo" /></span></div>
        <div class="3u"><span class="image fit"><img src="/assets/scan-tower-photo.png" alt="Scan tower photo" /></span></div>
        <div class="3u"><span class="image fit"><img src="/assets/scan-tower-inside-photo.jpg" alt="Scan tower photo" /></span></div>        
    </div>
</div>


Capture and image processing are done with [OpenCV](https://opencv.org/), and more precisely a C# wrapper called [EmguCV](http://www.emgu.com).

<center><div class="6u"><span class="image fit"><img src="/assets/opencv-emgucv.png" alt="Scan tower CAD model" /></span></div></center>


The image is captured, then the perspective of the 3 visible faces is projected so that it is possible to get the color of each 16 facets. This process is repeated after turning the cube to capture the 3 other faces.

<div class="col-12"><span class="image fit"><img src="/assets/image-processing.png" alt="Image processing"></span></div>

Mean RGB color of each facets are presented in this 2D scatter plot :

<div class="col-12"><span class="image fit"><img src="/assets/unclassified-colors.png" alt="Unclassified colors"></span></div>


Here is how to read the color value of a point (A point appears both in RG and RB graph) :
<div class="col-12"><span class="image fit"><img src="/assets/color-projection.png" alt="Color projection"></span></div>

Color <b>regions are not clearly separated</b>, so we cannot apply a simple threshold on each RGB component to discriminate the real color. We will need a <b>smarter algorithm</b>.

The final algorithm works as following :
* The euclidean color distance between all points is calculated
* The 2 nearest points are selected and they now belong to the same group (face). A group is composed of 16 points. So, lets find the 14 others that also belong to this group.
* All points that still not belong to a group are browsed and the point with the smallest distance to the group now belong to the group.
* The distance between a point and a group is the smallest distance between this point and all group points.
* One the group has 16 points, we begin a new group by finding again the 2 nearest points among the remaining points, and calculating the distance between each point and the new group.


<div class="col-12"><span class="image fit"><img src="/assets/color-classification-algorithm.gif" alt="Color classification algorithm"></span></div>

In the end, we now have 6 groups, but we still don't know their color. We only know that they are the same color. So, we apply this rules :
* Blue group is the group with smallest red component
* Green group is the second one with smallest red component
* Red group is the remaining group with the smallest green component
* Orange group is the second remaining group with the smallest green component
* Yellow and white groups are discriminated by saying that yellow group has less blue component than white

<div class="col-12"><span class="image fit"><img src="/assets/classified-colors.png" alt="Color classification algorithm"></span></div>



