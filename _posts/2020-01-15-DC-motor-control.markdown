---
layout: post
title:  "DC Motor Control with PIC32 and MATLAB"
date:   2020-01-15 21:03:36 +0530
categories: C Microchip
---
Building an intelligent motor driver which can accept a desired motor trajectory, execute that trajectory, and send the results back for error analysis.
<p align="center">
  <img src="/assets/featured.gif" alt="path" align="center" style="height: 200px; width:200px;"/>
</p>

The client, written in MATLAB, communicates with the PIC32 on the NU32 development board via serial port, sending control gains and desired setpoints and motion trajectories, and tracking results are sent back to the MATLAB client for plotting. The PIC32 manages a nested control loop system consisting of a PID outer motion control loop and a high-speed PI inner current (torque) control loop:

control system

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
