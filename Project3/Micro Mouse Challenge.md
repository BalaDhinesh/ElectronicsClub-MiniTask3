# Project3 : Micro Mouse Challenge

## Problem Statement:
To build an autonomous self-contained robot, Micromouse, which can get to the center of the maze in the shortest time.

## Design:
We can use any cardboard rectangular board or any general purpose circuit board for mounting the bot. The chassis is held intact by four nut screws and protected using bolts.
Above the chassis is mounted the Arduino board, motor driver and 3 sensors for obstacle detection(one on left, one on right, one on left). Under the chassis there are housed of two servo motors which
control the direction of the fully autonomous robot. Then the microcontroller is programmed according to our needs.

## Hardware Components used:

- Arduino UNO

- Ultrasonic ranging sensor(HC-SR04)

- iBall Power Bank 5V

- L298 Motor driver 

- Voltage Regulator 

- Two DC Gear motors with wheels

- A Ball caster wheel


## Robot Implementaion:
The power section can been placed at the top part of the chassis(Power bank and voltage regulator). Three ultrasonic sonar sensors have also been placed on the top chassis. Arduino and motor driver circuit can been placed on the middle part of the robot chassis. At the bottom part two DC wheels and a ball caster wheel for the sides and front respectively are placed.


## Software part:

For algorithm part, I suggest the below mentioned algorithm rather than Flooffill algorithm.

This algorithm that designed has a technique in which
the robot will traverse or visit almost every block of maze
and finds all the available paths to destination. Each path
will be compared the previously found path and the
shortest path is selected. It guarantees to find the shortest
path. 

__For the algorithm rules, refer this article:__

https://arxiv.org/pdf/1410.4145.pdf


The are some algorithms available to be
implemented like Wall Followers, Tremaux’s method
and Flood fill method. The wall followers are not that
efficient because they never gaurantees to find the
destination , sometimes they are caught in a loop. The
Flood fill method is the most efficient one. 

Using Flood fill algorithm, the robot will travel each and every possible way to find the shortest path which takes __high amount of processing and memory and complex calculations__. So the algorithm presented here can be used at considerably low memory and processing
power. By that, we can reduce the amount of power required to run the robot. 


For controlling the motors speed, pulse width modulation (PWM) is used.The power loss in PWM switching devices is very low. In many cases it is near to 0. So, this is the main advantage of PWM. While being used, resistors will tend to loss more power because of its heat dissipation. So, PWM is efficient in controlling motors.


Ultrasonic ranging sensor HC-SR04 is used since it is relatively much cheaper(costs around 170INR). Operating voltage and current are 5V DC and 15mA which can be acheived by using a Power Bank of 5V. Ranging distance is between 2cm to 4metre which is well sufficient.


The voltage regulator is used to supply constant 5V to the ultrasonic sensors. A very common voltage regulator IC is 7805 which has been used in this project.




