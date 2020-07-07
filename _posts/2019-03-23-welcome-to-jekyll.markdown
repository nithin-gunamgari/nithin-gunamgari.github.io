---
layout: post
title:  "KUKA's Youbot Manipulation"
date:   2019-09-23 21:03:36 +0530
categories: Vrep Python
---
<img src="/assets/featured.gif" alt="path" align="center" style="height: 400px; width:400px;"/>
This project programed the youBot mobile manipulator to pick and place a block.

The project includes:

- Simulation: Calculate the configuration of the robot given the robot's current configuration and joint speeds. It includes an omnidirectional robot odometry which calculate the base configuration (x, y, phi) given the wheel speed.

- Trajectory generation: Generate a smooth reference trajectory for the end-effector. The trajectory generated is a screw motion about a constant screw axis with fifth-order polynomial time scaling

- Feedforward and Feedback controller: A PI controller was designed to follow the desired end-effector trajectory using five arm-joints and four base-wheels. The equation of the control law is shown below. The end-effector twist $V$ calculated is then turned into the commanded wheel and arm joint speeds using the pseudoinverse of the mobile manipulator Jacobian.


This project is the final project of ME449: Robot Manipulation, Northwestern University, Evanston.

## Modules:

*The code is removed due to copyright of the capstone. Please contact me if you are interested in this project.*

The program takes the initial cube position, desired final cube position, the actual initial configuration of youBot, and reference initial configuration of youBot as inputs. It outputs a `csv` file which drives the youBot picking and placing the block, and the end-effector error as a function of time.

The youBot has nine degrees of freedom in total, where J1 to J5 are the arm joint angles, and W1 to W4 are the four wheel-angles. The figure below shows the the robot at its home configuration and the frames {s}, {b}, {0}, and {e}.


The project is divided into four python scripts:

- `ref_traj.py` would generate the desired reference trajectory for the end-effector.
- `feedback.py` defines the FeedbackControl class:
  - Calculate the command with feedforward and feedback components
  - Calculate the jacobian matrix of the manipulator
  - Calculate the joint speeds for controlling the mobile manipulator
- `simulator.py` will do the simulation. 
  - Given the current configuration and joint speeds, it will calculate the next configuration.
- `run.py` would use all other python scripts to generate the trajectory.

## Enhancement implemented

- Singularity avoidance
    - Ignore requested twist components in directions that is near singularity to avoid unreasonable large joint speeds.
- Add joint limits to avoid self-collision.
- Acceleration limis
    - Add maximun acceleration limitation to avoid jerky motion.

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
