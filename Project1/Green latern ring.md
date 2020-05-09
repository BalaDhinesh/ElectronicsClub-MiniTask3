# Project1: Green Latern Ring

## Problem Statement:
To design a simple ring which emits green light when worn and doesn't when not worn.

## Implementation:

### 1.Sensor:
We can use BH1603FVC analog current output ambient light sensor.


__Dimesions:__ 3mm in height and 1.8mm in width. 


__Datasheet of this Sensor:__
http://rohmfs.rohm.com/en/products/databook/datasheet/ic/sensor/light/bh1603fvc-e.pdf

### 2.Microcontroller:
ATTiny microcontroller can be used since as the name suggests, a very small chip. Programming can be done using Arduino.


__For more details on how to program ATtiny microcontroller using Arduino, visit:__


https://create.arduino.cc/projecthub/arjun/programming-attiny85-with-arduino-uno-afb829


__Datasheet of ATtiny45:__


http://ww1.microchip.com/downloads/en/DeviceDoc/Atmel-2586-AVR-8-bit-Microcontroller-ATtiny25-ATtiny45-ATtiny85_Datasheet.pdf






## Power:
This sensor and the microcontroller needs a minimum power of 3V. We need to place batteries in the ring which should not disturb the shape of the ring. So two button cell batteries of 1.5V each can be used since this is the best way of reducing the size.


## Design part:
We need to design the ring in such a way that it should light up only when it is worn. This can be acheived by coating the inner side of the ring with a photoconductive material like silicon with dopants(even cellotape is fine) and soldering the material to the sensor at the required pin. The threshold light value range can be obtained by hit and trial method and is programmed to the microcontroller. Now one or more LED is connected depending on the availability of size.
 We can coat the outer surface by opaque material like rubber. This doesn't allow light to pass through thereby increasing more accuracy of the LED lighting. The coatings should be evenly distributed and thin such that it doesn't feel big and disturb the other fingers.
