# Project2: Hexapod
## Problem Statement:
To recreate an exact orientation of the 18 DOF Hexapod on a computer screen using the data obtained from the sensors attached in the Hexapod.

## Pipeline of this project:

Getting Data from IMU Sensors => Microcontroller => Receiving data to the computer => 3D model using a software.

We need to simulate the exact movement of the Hexapod. This can be sensed by using Accelerometer, Gyroscope and Magnetometer. We can connect these sensors induvidually in the Hexapod. But this consumes a lots of space. Since magnetometers, accelerometers, and gyroscopes all respond to different forces, it makes sense to combine two or even all three of these sensors to create an inertial measurement device (IMU). The data from multiple devices makes it possible to accurately depict the sensor’s orientation. Then these datas should be communicated to the computer via microcontroller and produce 3D model using some software.

## What type of IMU do I really need?

There are many different types of IMU available in the market. There are IMUs that have an integrated processor that performs the math operations for you. Such devices are far easier to use, but (as you would expect) the convenience comes at a much higher cost. But our project do not need an integrated processors which will require you to write the code to fuse the data from multiple sensors into usable information. We only need to track the motion and coordinates of the Hexapod. Hence we would preferably go with an IMU which is of low cost having no integrated processors. Also the communication between the sensor and the computer should be simple to send the data(like the sensor is compatible with Arduino, Raspberry Pi, etc).

Based on the above requirements, we can use any of the two IMU's below:

- MPU 6050
__Specification:__
The MPU-6050 devices combine a 3-axis gyroscope and a 3-axis accelerometer on the same silicon die, together with an onboard Digital Motion Processor™ (DMP™), which processes complex 6-axis MotionFusion algorithms. The device can access external magnetometers or other sensors through an auxiliary master I²C bus, allowing the devices to gather a full set of sensor data without intervention from the system processor. The devices are offered in a 4 mm x 4 mm x 0.9 mm QFN package.


   __Approximate cost:__ 150 INR


   __Datasheet of this IMU:__ [Datasheet](https://invensense.tdk.com/wp-content/uploads/2015/02/MPU-6000-Datasheet1.pdf)
        


- MPU 9150:
__Specification:__
The MPU-9150 is a System in Package (SiP) that combines two chips: the MPU-6050, which contains a 3-axis gyroscope, 3-axis accelerometer, and an onboard Digital Motion Processor™ (DMP™) capable of processing complex MotionFusion algorithms; and the AK8975, a 3-axis digital compass. The part’s integrated 6-axis MotionFusion algorithms access all internal sensors to gather a full set of sensor data. The part is offered in a 4x4x1mm LGA package and is upgrade-compatible with the MPU-6050™ integrated 6-axis MotionTracking device, providing a simple upgrade path and making it easy to fit on space constrained boards.

   __Approximate cost:__ 400 INR


   __Datasheet of this IMU:__[Datasheet](https://invensense.tdk.com/wp-content/uploads/2015/02/MPU-9150-Datasheet.pdf
)



The advantages of MPU-9150 over MPU-6050 is that it has an additional 3-axis digital compass. This IMU can be used especially if the Hexapod need to operate over rough terrain. Point to note that this IMU costs some more money than 6050 IMU.
We need to buy six IMU sensors for each leg in the Hexapod. Based on our requirements and availbilty we can choose either of one.

## What type of microcontroller do I need to use?

 These chips use I2C (inter-integrated circuit) protocol for communication. Hence the communication between the sensor and the computer can be easily implemented by communicating the Arduino through the I2C protocol. Also Arduino provides separate libraries for each of the above sensor and therefore coding part becomes reduced.

![Arduino MPU 6050 connections](https://github.com/BalaDhinesh/ElectronicsClub-MiniTask3/blob/master/Project2/Arduino%20MPU6050%20connections.png)


## 3D modelling:

__To model the values from the Arduino compatible MPU-6050 in 3D:__
We use a software called Processing. Processing is mainly used for visualizing data and rendering it in 2D/3D models.


__GIF showing 3d model processing:__


![GIF-img](https://media.giphy.com/media/kbbeWC23w4sPW4oHrU/giphy.gif)



__Tutorial on how to upload the Code and Test the Arduino MPU 6050 and 3D Processing:__

Web link:

https://maker.pro/arduino/tutorial/how-to-interface-arduino-and-the-mpu-6050-sensor


__To change the 3d shape to our needs,__ we need to code some more information in the Processing Software. To see more details on how to code, refer this link:
[Drawing 3D Shapes With Processing](https://vormplus.be/full-articles/drawing-3d-shapes-with-processing)


## How to manage the wires?
From the above idea, we can be able to connect only one IMU sensor to the Arduino. But we need to send 6IMU's to the Arduino.Well an I2C bus is capable of communicating with 127 different sensors. But those sensors should have differnent address. Since we use six of the same IMU-6050 sensors, all have the same address(0X68 if AD0 is low and 0X69 if high). One way is that we can convert all the six sensors to different addresses. This can be acheived using a multiplxer with an I2C interface. We can use TCA9548A 1-to-8 I2C multiplexer for our purpose.


Using it is fairly straight-forward: The multiplexer itself is on I2C address 0x70 (but can be adjusted from 0x70 to 0x77) and you simply write a single byte with the desired multiplexed output number to that port, and bam - any future I2C packets will get sent to that port. In theory, you could have 8 of these multiplexers on each of 0x70-0x77 addresses in order to control 64 of the same-I2C-addressed-part.


![Multiplexer](https://cdn-learn.adafruit.com/assets/assets/000/027/696/medium800/adafruit_products_2717_kit_ORIG.jpg?1442011561)



![Diagram of I2C communication](https://i5j2k7b8.rocketcdn.me/wp-content/uploads/2017/06/I2C-Communication-How-It-Works.png)


By this way, we can connect all 6 IMU sensors to any one of the 8 pins(SD0 to SD7). There are two pins in each SD0 to SD7. One for SCL and another for SDA. The SCL and SDA pin of the multiplexer should be connected to the A5 and A4 pin of the Arduino respectively(these pins have inbuilt I2C bus interface communication). The Arduino here acts as master and the IMU's acts as slave for I2C communication.


__Datasheet of this multiplexer:__
[Datasheet](https://www.ti.com/lit/ds/symlink/tca9548a.pdf?&ts=1589076351652)




