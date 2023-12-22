---
layout: default
title: Follow Line
nav_exclude: false
---

The follow line uses a 3 infrared sensor's array wich are used to determine the position of the black line.

To configure the different tasks executed we used the FreeRTOS library wich acts like a scheduler for Arduino.

The two tasks:
* Ping: sends a ping every four seconds.
* Follow line: executes a finite state machine wich controls the movement.

1. Finite State Machine

To control the line follower we use a finite state machine which determines the next state through the readings of the three infrared sensors.These values ​​range from 0 to 1000, the value being higher the darker the line. This is the reasoning followed to resolve wich state is chosen. Each state is represented by a number:

* If the the middle sensor is the only one on the line, the state will be Forward or **STATE 1**. This state calls the function *forward()*.
* When the middle sensor and one of the laterals are there two options depending on which side the car came off. These state are 2 or 3, that are *left()* or *right()*. In these two *If-else* sentences we store the value of both laterals sensor to calculate the next state
