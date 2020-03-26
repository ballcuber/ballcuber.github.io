---
layout: page
title: Project history
permalink: /Project-History/
---

<style>
  
/* The actual timeline (the vertical ruler) */
.timeline {
  position: relative;
  max-width: 1200px;
  margin: 0 auto;
}


/* The actual timeline (the vertical ruler) */
.timeline::after {
  content: '';
  position: absolute;
  width: 6px;
  background-color: gray;
  top: 0;
  bottom: 0;
  left: 50%;
  margin-left: -3px;
}

/* Container around content */
.container {
  padding: 10px 40px;
  position: relative;
  background-color: inherit;
  width: 50%;
}

/* The circles on the timeline */
.container::after {
  content: '';
  position: absolute;
  width: 25px;
  height: 25px;
  right: -17px;
  background-color: white;
  border: 4px solid #FF9F55;
  top: 15px;
  border-radius: 50%;
  z-index: 1;
}

/* Place the container to the left */
.left {
  left: 0;
}

/* Place the container to the right */
.right {
  left: 50%;
}

/* Add arrows to the left container (pointing right) */
.left::before {
  content: " ";
  height: 0;
  position: absolute;
  top: 22px;
  width: 0;
  z-index: 1;
  right: 30px;
  border: medium solid Silver ;
  border-width: 10px 0 10px 10px;
  border-color: transparent transparent transparent Silver ;
}

/* Add arrows to the right container (pointing left) */
.right::before {
  content: " ";
  height: 0;
  position: absolute;
  top: 22px;
  width: 0;
  z-index: 1;
  left: 30px;
  border: medium solid Silver;
  border-width: 10px 10px 10px 0;
  border-color: transparent Silver  transparent transparent;
}

/* Fix the circle for containers on the right side */
.right::after {
  left: -16px;
}

/* The actual content */
.content {
  padding: 20px 30px;
  background-color: Silver ;
  position: relative;
  border-radius: 6px;
}

/* Media queries - Responsive timeline on screens less than 600px wide */
@media screen and (max-width: 600px) {
  /* Place the timelime to the left */
  .timeline::after {
  left: 31px;
  }
  
  /* Full-width containers */
  .container {
  width: 100%;
  padding-left: 70px;
  padding-right: 25px;
  }
  
  /* Make sure that all arrows are pointing leftwards */
  .container::before {
  left: 60px;
  border: medium solid white;
  border-width: 10px 10px 10px 0;
  border-color: transparent white transparent transparent;
  }

  /* Make sure all circles are at the same spot */
  .left::after, .right::after {
  left: 15px;
  }
  
  /* Make all right containers behave like the left ones */
  .right {
  left: 0%;
  }
}
</style>

Long story short, here is a short timeline of all our development steps. 

<br><br>

<div class="timeline">
  <div class="container left">
    <div class="content">
      <h2>2000s</h2>
      <p>Since I was young I had this idea of a multi-dimentionnal cube solver based on a cube inside a sphere.</p>
    </div>
  </div>
  <div class="container right">
    <div class="content">
      <h2>2010s</h2>
      <p>The idea was still in my mind but I didn't have the skills to developp it.</p>
    </div>
  </div>
  <div class="container left">
    <div class="content">
      <h2>November 2017</h2>
      <p>I had a look on all solving machine. The 3x3x3 cube is solved by a machine in less than 1 second, so I decide to focus the project on the 4x4x4 cube</p>
    </div>
  </div>
  <div class="container right">
    <div class="content">
      <h2>December 2017</h2>
      <p>I looked for an algorithm to solve the 4x4x4 cube.</p>
    </div>
  </div>
  <div class="container left">
    <div class="content">
      <h2>January 2018</h2>
      <p>I talked about this project to a friend who is mechanical engineer, he presented me OnShape, and we began the mechanical developpement.</p>
    </div>
  </div>
  <div class="container right">
    <div class="content">
      <h2>February 2018</h2>
      <p>First proof of concept 3D printed prototype with two motors that move the cube with gears (version name : Fetus). We started developping the complete version.</p>
    </div>
  </div>
  <div class="container left">
    <div class="content">
      <h2>March 2018</h2>
      <p>Developpement of the supervisor software (Real time 3D view, resolution sequencing, image processing)</p>
    </div>
  </div>
  <div class="container right">
    <div class="content">
      <h2>May 2018</h2>
      <p>First entire machine with 9 motors (version name : Obese) and gears. Very disapointed, a lot a mechanical frictions. The servo motors are not reliable to prevent internal pieces from falling when the sphere is opened.</p>
    </div>
  </div>
  <div class="container left">
    <div class="content">
      <h2>June 2018</h2>
      <p>Looking for improvements and a more simple kinematic.</p>
    </div>
  </div>
  <div class="container right">
    <div class="content">
      <h2>July 2018</h2>
      <p>Developpement of Sharer, an arduino library to facilitate communication with a PC software.</p>
    </div>
  </div>
  <div class="container left">
    <div class="content">
      <h2>August 2018</h2>
      <p>Idea of a kinematic based on a geneva drive rather than a gear.</p>
    </div>
  </div>
  <div class="container right">
    <div class="content">
      <h2>September 2018</h2>
      <p>Developpement of the scan tower to identify the initial state of the cube. Developpement of the image processing software.</p>
    </div>
  </div>
  <div class="container left">
    <div class="content">
      <h2>October 2018</h2>
      <p>Modification of fetus version with a matlted cross in order to validate it.</p>
    </div>
  </div>
  <div class="container right">
    <div class="content">
      <h2>November 2018</h2>
      <p>Add an electric cabinet with the electronics and power.</p>
    </div>
  </div>
  <div class="container left">
    <div class="content">
      <h2>January 2019</h2>
      <p>Second entire 3D printed machine with 9 motors and magnets (version name : Elegant).</p>
    </div>
  </div>
  <div class="container right">
    <div class="content">
      <h2>February 2019</h2>
      <p>Add epicycloidale reducer on all motors (version name : Compact), test of an industrial motor to replace steppers.</p>
    </div>
  </div>
  <div class="container left">
    <div class="content">
      <h2>April 2019</h2>
      <p>Redaction and patent application.</p>
    </div>
  </div>
  <div class="container right">
    <div class="content">
      <h2>June 2019</h2>
      <p>Adding of a shaft encoder, central support, cable guides, new electronic cabinet (version name : not yet defined).</p>
    </div>
  </div>
</div>