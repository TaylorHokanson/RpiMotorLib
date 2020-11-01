## Driving a [DRV8825](Documentation/Nema11DRV8825.md) with a Raspberry Pi


1. sudo apt-get update/upgrade
1. Change python3 to default
1. cd to script folder (necessary?)
1. ```sudo pip install rpimotorlib```
2. The library file RpiMotorLib.py contains the class which controls the motor. The class is called A4988Nema. This class handles both A4988 and Drv8825. 

```
import RPi.GPIO as GPIO

# import the library
from RpiMotorLib import RpiMotorLib

#define GPIO pins
GPIO_pins = (23, 22, 27) # Microstep GPIO Pins
direction= 17            # Direction -> GPIO Pin
step = 18                # Step -> GPIO Pin

# Declare an instance of class pass GPIO pins numbers and the motor type
mymotortest = RpiMotorLib.A4988Nema(direction, step, GPIO_pins, "DRV8825")

# Rotation        clockwise
# Microstepping   1/16 
# Number of steps 100
# Step delay      .01 second
# Verbose output  off
# Initial delay   50mS
mymotortest.motor_go(False, "1/16" , 100, .01, False, .05)

# good practise to cleanup GPIO at some point before exit
GPIO.cleanup()

```

This is a fork! The original author's info is below:
--------------------------------------------------

* Original Author: Gavin Lyons
* URL: https://github.com/gavinlyonsrepo/RpiMotorLib
* History: CHANGELOG.md is at repository in documentation.
* Contributers: [Erez Levanon](https://github.com/erezlevanon)
* Copyright: Copyright (C) 2018 Gavin Lyons. See LICENSE.md in documentation.
* Contact: github or glyons66@hotmail.com.

