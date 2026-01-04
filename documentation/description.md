# Description

The CARL Air Brake computer is comprised of the following three circuit boards.
These boards are loaded with their respective software and connected by stacking
on top of each other, to make up the computer.

- Peripheral devices module.
- Power supply module.
- Raspberry Pi 3 model A+.

This repository contains the electronic design for the first of the above three
boards. Other electronic designs and software are contained in different
repositories (for more details, see [CARL Air Brake][cab-repo]).

## Overview

The peripheral devices module contains the necessary sensors and the brake
actuator for the CARL Air Brake computer. It also has status LEDs to indicate
which of its onboard power lines are live. An onboard microcontroller is
connected to the brake actuator. After being flashed with its associated
software, it drives the brake actuator by receiving control commands from the
Raspberry Pi. The Raspberry Pi, thus, controls the brake actuator through the
microcontroller, but interfaces directly with the sensors.

## Servo

The peripheral devices module is intended for use with a brake servo actuator
capable of running at 6V power supply. Additionally, its current consumption
must not exceed 5A, and must also be compatible with the battery's continuous
current limits. For details about the intended battery, see
[CARL Air Brake Power Supply Hardware][cab-psup-hw-repo].

## Components

The relevant circuit components on the board are marked on the following diagram
and described below.

![Relevant components of the peripheral devices module](
  ./images/relevant_components.png
)

| **Designation** | **Description**                                 |
| --------------- | ----------------------------------------------- |
| J1              | Port for ICSP cable for programming.            |
| J2              | Port for USB cable for programming.             |
| J3              | Socket header for connecting other boards.      |
| J4              | Header for drawing 6V from power supply module. |
| J5              | Port for brake actuator cable.                  |
| D6-D9           | Power line status LEDs.                         |
| TP1-TP5         | Test points for measuring power line voltages.  |

## Working

The following is a simple block diagram of the peripheral devices module.

![Block diagram of the peripheral devices module](
  ./images/block_diagram.png
)

As seen in the above diagram, the board contains the following four power lines.
Note that the line voltages listed below are nominal values. It is normal for
the actual voltages to deviate slightly.

| **Name**  | **Description**                                 | **Voltage** |
| --------- | ----------------------------------------------- | ----------- |
| 3.3V      | Output of 3.3V regulator on Raspberry Pi.       | 3.3V        |
| 5V        | Output of 5V regulator on power supply module.  | 5V          |
| 6V        | Output of 6V regulator on power supply module.  | 6V          |
| VMCU      | Power line for onboard microcontroller.         | 5V          |

When the power supply module is connected, the VMCU, 5V, and 6V lines become
live. If, in addition to the power supply module, the Raspberry Pi is also
connected, then the 3.3V line also becomes live. If any or both of the two
programming cables are connected, the VMCU line becomes live regardless of
whether or not the power supply module is connected. Thus, the VMCU line has
three power sources - the power supply module, and two programming cables. It is
safe to simultaneously connect more than one of these power sources as the board
has protection diodes that will prevent any short circuit.

The brake actuator draws power from the 6V line and the sensors draw power from
the 3.3V line. The VMCU line supplies power to the onboard microcontroller.
Each regulated power line is also connected to a separate status LED (D6-D9) to
visually indicate which lines are live. Additionally, all power and GND lines
are connected to separate test points (TP1-TP5) for measuring their voltages
with a multimeter. For brevity, status LEDs and test points are omitted from the
above diagram.

The Raspberry Pi interfaces with the sensors and the onboard microcontroller via
its I2C bus. The sensors include two BNO055 IMUs and two BMP388 barometers.
There are two of each to provide a backup in the event that one fails. The
microcontroller drives the brake actuator by following commands received from
the Raspberry Pi.

The onboard microcontroller is programmable from the ICSP port J1 and the USB
port J2. The ICSP connection is required only once, for installing the
bootloader. Subsequently, the microcontroller can be conveniently programmed
from the USB port. When flashed with the appropriate software (see 
[flashing.md][fsh]), it receives commands from the Raspberry Pi and accordingly
drives the brake actuator.

[fsh]:              ./flashing.md

[cab-repo]:         https://github.com/Kenneth-Goveas/CARL-Air-Brake
[cab-psup-hw-repo]: https://github.com/Kenneth-Goveas/CARL-Air-Brake-Power-Supply-Hardware
