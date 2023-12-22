---
layout: default
title: IoT comunication
nav_exclude: false
---

# Comunication
The comunications of the robot consists of two parts: the serial communication between the arduino and the esp32 and the MQTT messages sent by the esp32 via wifi.

### Serial communication
For this part both the arduino and the esp32 both send short messages to each other via the serial port. This is made by using the functions Serial.print() and Serial.read() on the arduino and Serial2.print() and Serial2.read() on the esp32.
