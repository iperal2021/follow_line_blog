---
layout: default
title: IoT comunication
nav_exclude: false
---

1. The ping task has the highest pryority because of it must be send without the minimun delay. This task, like the following one, uses serial communication to send the value corresponding to the message that must be sent from the ESP32.

```cpp
static void pingCallBack( void *pvParameters)  // This is a Task.
{
  TickType_t xLastWakeTime, aux;
  while (1)
  {
    xLastWakeTime = xTaskGetTickCount();

    while ( (aux - xLastWakeTime)*portTICK_PERIOD_MS < COMPUTATION_TIME_ON_T1) {
      aux = xTaskGetTickCount();
    }
[...]
      if (!printed)
      {
        Serial.print("4;");
        Serial.print(String(time_since_start) + ";");
        printed = true;
      }
[...]
    xTaskDelayUntil(&xLastWakeTime, (PING_IDLE/portTICK_PERIOD_MS));
  }
}
```