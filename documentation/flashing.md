# Flashing

The software for the peripheral devices module can be found in the
[CARL Air Brake Peripheral Devices Software][cab-pdev-sw-repo] repository. This
repository contains two programs - a tuning program, and a main program - that
can be flashed onto the board. The tuning program is used to calibrate the
actuator positions corresponding to the fully retracted and fully deployed brake
positions. The main program is used to drive the brake actuator following the
commands from the Raspberry Pi as described in [description.md][des]. For
detailed instructions for flashing the software, see
[CARL Air Brake Peripheral Devices Software][cab-pdev-sw-repo].

[des]:              ./description.md

[cab-pdev-sw-repo]: https://github.com/Kenneth-Goveas/CARL-Air-Brake-Peripheral-Devices-Software
