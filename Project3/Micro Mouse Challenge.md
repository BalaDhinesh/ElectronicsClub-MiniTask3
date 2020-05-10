# Project3 : Micro Mouse Challenge

## Problem Statement:
To come with a better solution to the problem of solving maze using robot.

For algorithm part, I suggest 

The algorithm that designed has a technique in which
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
Flood fill method is the most efficient one. Using Flood fill algorithm, the robot will travel each and every possible way to find the shortest path which takes high amount of processing and memory and complex calculations. So the algorithm presented here can be used at considerably low memory and processing
power. By that, we can reduce the amount of power required to run the robot. 


Instead of Ultrasonic sensor, we can use an Infrared sensor since the size factor is smaller and it is more accurate than the Ultrasonic sensor. Also Infrared sensor are cheaper than Ultrasonic sensors.
