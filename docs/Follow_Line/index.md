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

