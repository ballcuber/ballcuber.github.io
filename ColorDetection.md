---
layout: page
title: Color detection
permalink: /Color-Detection/
---

Defining the 96 facets colors is possible by hand in the supervisor, but it is a very <b>laborious</b> task, as you can see :

![Manual color definition of the cube](/assets/cube-manual-definition.gif){: .center-image}

That's why we decided to developp an <b>automatic color detection</b> with a camera. First, me want this to be independant of the robot in order not to disturb mechanical tunings. Moreover, image processing is very empirical and dependant of the brightness, so we have created a dark enclosure with controlled lightning and designed so that the camara can scan 3 faces at a time. Then, the cube is flipped in order to scan the 3 other faces.
The camera is a low-cost 640x320 Logitech USB webcam, but it's sufficient.

![Scan tower CAD model](/assets/scan-tower-CAD-model-annotated.png){: .center-image}

![Scan tower photo](/assets/scan-tower-with-cube-photo.jpg){: .center-image}

![Scan tower photo](/assets/scan-tower-photo.jpg){: .center-image}

![Scan tower photo](/assets/scan-tower-inside-photo.jpg){: .center-image}


Capture and image processing are done with [OpenCV](https://opencv.org/), and more precisely a C# wrapper called [EmguCV](http://www.emgu.com).

![OpenCV and EmguCV](/assets/opencv-emgucv.png){: .center-image}


The image is cuptured, then the perspective of the 3 visible faces is projected so that it is possible to get the color of each 16 facets. This process is repeated after turning the cube to capture the 3 other faces.

![Image processing](/assets/image-processing.png){: .center-image}

Mean RGB color of each facets are prepresented in this 2D scatter plot :

![Unclassified colors](/assets/unclassified-colors.png){: .center-image}


Here is how to read the color value of a point (A point appears both in RG and RB graph) :
![Color projection](/assets/color-projection.png){: .center-image}

Color <b>regions are not clearly separated</b>, so we cannot apply a simple threshold on each RGB component to discriminate the real color. We will need a more <b>intelligent algorithm</b>.

The final algorithm works as following :
* The euclidian color distance between all points is calculated
* The 2 nearest points are selected and they now belong to the same group (face). A group is composed of 16 points. So, lets find the 14 others than also belong to this group.
* All points that still not belong to a group are browsed and the point with the smallest distance to the group now belong to the group.
* The distance between a point and a group is the smallest distance between this point and all group points.
* One the group has 16 points, we begin a new group by finding again the 2 nearest points among the remaining points, and calculating the distance between each point and the new group.


![Color classification algorithm](/assets/color-classification-algorithm.gif){: .center-image}

In the end, we now have 6 groups, but we still don't know their color. We only know that they are the same color. So, we apply this rules :
* Blue group is the group with smallest red component
* Green group is the second one with smallest red component
* Red group is the remaining group with the smallest green component
* Orange group is the second remaining group with the smallest green component
* Yellow and white groups are discriminated by saying that yellow group has less blue component than white

![Color classification algorithm](/assets/classified-colors.png){: .center-image}



