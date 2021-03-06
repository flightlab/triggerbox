# triggerbox

camera triggering with clock synchronization to host PCs

## firmware build and install

This firmware can be compiled and installed with the Arduino IDE or at
the command line.

### Arduino IDE compilation

The file `triggerbox.ino` in the folder `firmware/triggerbox` can be opened
directly in the [Arduino IDE](http://arduino.cc/en/main/software).

### Command-line compilation

To build this firmware for an Arduino Nano or Arduino Uno board on Ubuntu linux, do
the following steps.

Install the required software:

    sudo apt-get install arduino-mk

Make the firmware and upload it onto your Arduino device:

    make -f Makefile.nano upload # <- Do this for Arduino Nano
    make -f Makefile.uno upload # <- Do this for Arduino Uno

## Device setup

After building and uploading firmware to the device, its name must be saved
to it with the [arduino-udev](https://github.com/strawlab/arduino-udev)
package.

Unplug and replug the triggerbox:

    arduino-udev-name --set-name trig1 --verbose /dev/ttyUSB0
    udevadm control --reload-rules
    udevadm trigger --attr-match=subsystem=tty
    ls /dev/trig1
