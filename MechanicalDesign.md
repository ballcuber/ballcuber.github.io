---
layout: page
title: Mechanical design
permalink: /Mechanical-Design/
---

The mechanical design is the most complicated part of this project.

## Introduction

The spirit of this was to be able to solve the cube as fast as possible. Knowing that the mechanical design had to be thinked this way. That means we had to think about a solution that needs less steps to solve and be able to do these steps fast.

We decided to put one actuator on each row of the cube except one on each direction (explained on this page). That means (4-1)rows * 3 axes = 9 actuators.  

## Kinematic

Let's dive into the current kinematic of the ballcuber.

# Holding the cube

The cube is hided inside the ballcuber. The yellow outer frame has an inner spherical surface where 3 types of parts can slide. Thos 3 types of part hold the cube at the center and contribute to "build" a pivot mate between each row of the cube and the spherical surface.
On the following images the higlighted surfaces are the one that slide on the inner spherical surface of the outer frame.  
![Edge](/assets/kinematic/Arete.png "Edge part")
![Coin](/assets/kinematic/Coin.png "Corner Part")
![Face](/assets/kinematic/Face.png "Face part")
Those parts are all around the cube and it looks like this with the cube and the surronding parts without the frame :
![Sphere](/assets/kinematic/Sphere.png){: .center-image}
This sphere can slide inside the frame which is this yellow part :
![Outer frame 3D](/assets/kinematic/Outer_Frame.png){: .center-image}
Here is the frame with all the parts inside :
![Mounted_base](/assets/kinematic/Mounted_base.png){: .center-image}

All the parts presented in the previous pictures have been [3D printed](https://ballcuber.github.io/3d-print/).

# Rotating a cube's row

The rotation of a cube's row is done with a mechanism inspired by the [Geneva drive](https://en.wikipedia.org/wiki/Geneva_drive).

Here is a quick Gif of the current Geneva drive inspired mechanism.
![KinematicCrossSection](/assets/kinematic/KinematicCrossSection.gif){: .center-image}

On the previous GIF we can see that the stepper drives an epicyclic gear that, at the end drives a driving rod (Rotation speed is a 1/4 of the stepper's speed and so the available torque is 4 times what the stepper can give). This driving rod has a small pin at the tip of each branch. This pin goes into a slot and push one part that is between the frame and the cube. By pushing this part the cube's row starts to rotate around its centre.  

Here is another GIF to show the kinematic with all the parts except the hood in order to be able to see parts moving.
![KinematicWithoutHood](/assets/kinematic/KinematicWithoutHood.gif){: .center-image}

The kinematic we designed let us move perpendicular rows one after another as we can see there :
![KinematicCrossRows](/assets/kinematic/KinematicCrossRows.gif){: .center-image}

## Other cool mechanical stuff to come

More content is coming soon...