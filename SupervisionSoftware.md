---
layout: page
title: Supervision Software
permalink: /Supervision-Software/
---

<video width="100%" autoplay loop muted playsinline>
  <source src="/assets/IMG_5257.MOV" type="video/mp4" />
</video>

* table of contents
{:toc}

# Introduction
The software that drives the BallCuber is mainly developed in .NET framework, with some aditional javascript and java. But a part also runs in each of the two Arduino MEGA boards (C++ language).

Its sources are available on Github : [https://github.com/ballcuber/ballcuber-source-code](https://github.com/ballcuber/ballcuber-source-code).

# Grab images
[This page](/Color-Detection) describes the procedure to grab and process image in order to get the initial state of the 4x4x4 Rubik's Cube.

# Resolution algorithm
The resolution algorithm is, with the mechanical design, the most difficult part of the project.

Fortunately, the Github user cs0x7f has published a TPR-4x4x4-Solver that is based on a Three-Phase-Reduction Solver and a 3x3x3 Solver. You can find its sources here :
[https://github.com/cs0x7f/TPR-4x4x4-Solver](https://github.com/cs0x7f/TPR-4x4x4-Solver).

The Ballcuber .NET software call the java solver and parse its output to identify the solving sequence. Then, geometric transformations are applied to make its movements compatible with the kinematics of the BallCuber, which has a fixed corner. 

On average, this algortithm solves the cube in about 60 moves (quarter turns).


# 3D real time display
The supervision program has a real time 3D view of the 4x4x4 Rubik's Cube. It is rendered by a chromium browser (cef sharp), that hosts a Twisty.js player : [https://github.com/cubing/twisty.js](https://github.com/cubing/twisty.js). The .NET code remote execute javascript to animate the cube.

![3D supervision view](/assets/3d-supervision.png){: .center-image}


# Embedded Arduino software
The embedded part has been designed to be simple and slave to the .NET program. The same code runs in both Arduino boards. Communication takes place via a serial link (RS232) and is facilitated by the Sharer library. The 9 stepper motors are controlled simultaneously by the AccelStepper and MultiStepper libraries.

* Sharer : [https://github.com/Rufus31415/Sharer](https://github.com/Rufus31415/Sharer) 
* Stepper : [https://www.airspayce.com/mikem/arduino/AccelStepper/](https://www.airspayce.com/mikem/arduino/AccelStepper/) 

BallCuber embeded sources are available on Github : [https://github.com/ballcuber/ballcuber-source-code/blob/master/Arduino/Arduino.ino](https://github.com/ballcuber/ballcuber-source-code/blob/master/Arduino/Arduino.ino).


# Resolution sequences
The movements resulting from the resolution algorithm are converted into a motor movement sequence. A runner allows to see the progress of the execution of the instructions, but also to set breakpoints.

![3D supervision view](/assets/runner.png){: .center-image}


# Machine maintenance
For maintenance and tuning purposes, setting screens allow to adjust the machine (calibration, COM port, camera, ...), as well as to control each motor individually.

![3D supervision view](/assets/maintenance-screen1.png){: .center-image}

![3D supervision view](/assets/maintenance-screen2.png){: .center-image}
