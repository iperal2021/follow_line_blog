---
layout: default
title: IoT comunication
nav_exclude: false
---

# Comunication
The comunications of the robot consists of two parts: the serial communication between the arduino and the esp32 and the MQTT messages sent by the esp32 via wifi.

### Serial communication
For this part both the arduino and the esp32 both send short messages to each other via the serial port. This is made by using the functions Serial.print() and Serial.read() on the arduino and Serial2.print() and Serial2.read() on the esp32. 
When the messages are received we process them using a buffer. When there is information to read, one character is saved in the buffer, then if that character is ';' then it means it is the end of the message so it can be process and at the end that character is added to the buffer.

```cpp
if (Serial2.available()) {

    char c = Serial2.read();
    
    if (c == ';')  {            
      [...]
      switch (sendBuff.toInt()) {
        [...]
      }

      [...]

      sendBuff = "";
    } else {
      sendBuff += c;
    }

  }
```
