---
layout: posts
title: "Lecture Notes: Introduction to Adaptive and Reactive Control for Robots"
date: 2024-10-31
categories: [lecturenotes]
tags: [notes, adaptive learning, control system]
---

Real-time planners face challenges in dynamic, partially predictable, and partially observable environments. Highly non-linear dynamics make throw and catch motions difficult for robots. These factors often lead to a lack of precise equations, necessitating the use of machine learning to predict dynamics. Control systems, however, can handle worst-case scenarios, enabling effective and safe robot control.

Unlike Position Control, **Compliance Control** allows robots to actively absorb shocks. When bumped, the robot generates motion in the opposite direction to mitigate impact, requiring it to find a safe path.

Perception often lacks accuracy—for instance, when a camera loses a frame. While Kalman Filters can handle noise, they require an already good model. An alternative is the **Coupling Method**. Moving with the object—naturally slowing down as it does—is effective in many applications. The simplest coupling approach treats the target as the origin. As the target moves, the state space moves with it, allowing us to consistently locate the robot's position in this state space.

### Traditional Planning Approaches in Robotics

Path planning or motion planning directly controls robot motion. Its complexity primarily depends on three factors: whether the vehicle is holonomic (able to move in any direction), whether the environment is fully known, and whether it's deterministic or stochastic.

**Global Path Planning** focuses on feasibility and optimality but can't be applied to continuous world representations.

**Local Path Planning** requires only local knowledge of the world, enabling fast, reactive control adapted to real-time control and local robot perception. However, it typically relies on heuristics to determine paths.

In typical potential energy methods, robots are attracted to the goal and repelled by obstacles. We combine these two energy types to calculate the path.

For dynamical systems, we must ensure convergence and fast, reactive control to the goal. A complete path planning procedure with dynamical systems includes: 1) generating potential field methods, 2) offering closed-form/analytical descriptions of all feasible paths, 3) combining with machine learning to learn the vector field, and 4) generating non-linear dynamics for the robot's paths with stability guarantees.

### Motion Planning for an Articulated Robot Arm

**Configuration Space**: The space where joints can be represented.

**Workspace**: The area an end effector can reach, usually combining position in Cartesian space $(x, y, z)$ and orientation $(pitch, yaw, and roll)$.

We typically represent motion in Cartesian space, so after generating a motion, we need an inverse kinematic solver to obtain the joint space representation.

### Path Planning Using Optimal Control

The question is whether the optimal path is the shortest in joint space or Cartesian space. Energy is key, but the most energy-efficient way isn't always the most time-efficient. The cost function determines the solution.

Obstacles create non-trivial constraints. We can construct a wrapper for these obstacles, representing them as multiplicative, so the state space appears as a hole in a contiguous space.

When the robot is moving, there's no closed-form solution because all data are sampled. One solution is **discretization**, though this is challenging in multidimensional space.

If there's no feasible solution, finding an alternative becomes crucial, as stopping isn't ideal for most robots. For example, if a self-driving car stops in the middle of the road due to uncertainty, it creates a hazardous situation.

### Learning Dynamical Systems-based Control Laws

When using Support Vector Regression (SVR) to learn from data, we minimize epsilon loss. While near-zero loss is desirable, in real scenarios, a non-exact zero can cause drift, potentially preventing the robot from stopping at the target.

A possible stable estimator could be a Gaussian Mixture Model or **Gaussian Mixture Regression**, with energy function constraints to ensure the control process is considered.

For robots to react continuously and immediately, we need to combine **Impedance Control** and online trajectory planning with dynamical systems. For robots working around humans, we need **Force Control** combined with dynamical systems.

## reference

https://learningadaptivereactiverobotcontrol.github.io/book-website.io//documentation/L1-Introduction.html
