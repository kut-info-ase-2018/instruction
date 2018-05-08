# References

* Raspberry Pi Starter Kit: learning course of sensors in the startar kit http://osoyoo.com/2017/07/13/raspberry-pi-3-starter-learning-kit-introduction/#3

* Raspbian OS (variant of Ubuntu Linux)
https://www.raspberrypi.org/downloads/raspbian/

# Item List

* In PL-2 Raspberry Pi Container
  * Raspberry Pi
  * USB power cable
  * Raspbian OS installed SD card (installed in Rapsberry Pi)
  * Raspberry Pi paper box (DO NOT DAMAGE)
  * PL-2 SD card (inside the box. DO NOT TOUCH)
  * USB SD card adapter
  * IO board for PL-2

* In Raspberry Pi Starter Kit
  * Raspberry Pi 3 Starter Learning Kit Packing List
  * items listed on the Packing List

# Preparation
(You can skip this section. The SD card set in the Raspberry Pi is ready. Refer to this section when you want to prepare your own SD card or re-install Raspbian OS.)

Raspberry Pi boots from an SD card. Here, we write the disk image of Raspbian to an SD card.

1. Download disk image (RASPBIAN STRETCH WITH DESKTOP) from: https://www.raspberrypi.org/downloads/raspbian/

2. Insert SD card to PC.

3. Unmount the SD card if it is automatically mounted.  For Mac, check the device name by ``diskutil list`` command, and unmount the disk with ``sudo diskutil unmountDisk <device name>``. Device name is like ``/dev/disk3``.

4. Write the image to the SD card.
```
sudo dd if=<image file name> of=<raw device name> bs=1m
```
where ``<image file name>`` is the file name of the one that is downloaded in step 1, and ``<raw device name>`` is the device name with ``rdisk``.  For example, raw device name of ``/dev/disk3`` is ``/dev/rdisk3``.


# Getting started

(read Raspberry Pi Starter Kit Lesson 1
  http://osoyoo.com/2017/06/20/raspberry-pi-3-basic-tutorial/)

* Connect Raspberry pi
  * keyboard (USB)
  * display (HDMI)
  * power cable (USB micro)
* Log in
  * user: pi, password: raspberry
* Set-up SSH (Section B. Remotely in the on-line material)
  * Type `sudo systemctl enable ssh` in a terminal.
  * Type `sudo systemctl start ssh` in a terminal.
  * Find the IP address assigned to your Raspberry Pi by `ifconfig`.
  * Log in though SSH from your laptop: `ssh pi@<IP address>`
* Power off
  * Type `sync` to ensure all data is written to the SD card.
  * Unplug the power cable.

# Light LED

(read Raspberry Pi Starter Kit Lesson 4 http://osoyoo.com/2017/06/23/python-light-led/)

*REMARK: Be careful not to destroy devices.  DO NOT connect 5V/3V/GND pins each other or directly to a signal pin.   LED has virtually no resistance.  Insert a register.*

## Preliminaries

### GPIO

We use GPIO (General Purpose I/O) of Raspberry Pi to control peripherals such as LED and sensors.  Raspberry Pi has multiple GPIO pin, each is identified by either BCM pin number or Physical in number.  BCM pin number is printed on the Raspberry Pi case. We use BCM pin number in this course.

GPIO pin can be controlled with `Pi.GPIO` module from Python programs.

### breadboard

We use a breadboard to construct a circuit.  Hols on a breadboard are connected as shown in the following picture.
<img src="BREADBOARD.png">

## Instruction

* Connect Raspberry Pi to a bread board
* Construct a circuit on the bread board (connection graph:
http://osoyoo.com/wp-content/uploads/2017/06/Untitled-Sketch_bb.jpg)
  * connect BCM Pin#17 to the longer pin of LED
  * connect the sorter pin with either pin of a register (200 ohm)
  * connect the other pin of the register to GND pin of Raspberry pi.
* Plug the power of your Raspberry Pi and log in.
* Download a test program from the following URL and execute it.
 http://osoyoo.com/driver/pi3_start_learning_kit_lesson_4/pythontest.py

# Temperature and humidity sensor module

(read Raspberry Pi Starter Kit Lesson 17 http://osoyoo.com/2017/07/06/dht11/)

DHT11 module is a sensor module on which necessary registers are implemented.  All you have to do is to connect to appropriate pins of  Raspberry pi.

## Instruction

* Unplug the power cable of your Raspberry Pi
* Construct a circuit on the breadboard (connection graph:http://osoyoo.com/wp-content/uploads/2017/07/Untitled-Sketch_bb.png)
* Plug the power cable of your Raspberry Pi and log in.
* Execute the python program found at the folloing URL: http://osoyoo.com/driver/pi3_start_learning_kit_lesson_17/dht11.py
