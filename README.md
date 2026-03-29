# RKS-Keyboard

A mechanical keyboard build on YD-RP2040 with an OLED display and backlights

Build for **MX** switches

A sligthly modified 96% keyboard layout with 4 extra keys for managing onboard firmware (103 keys total)

![Keyboard CAD assembly](/CAD/assembly.png)

![Keyboard layout](/keyboard-layout.svg)

![Keyboard parts](/CAD/parts.png)

## Why is this one special

It's a keyboard with a customisable OLED that helps to manage, and control parts of the firmware like changing backlighting color, showing typing speed and much more

The firmware is also open-source so anyone can customise and add features to their keyboard

## PCB

![PCB](/PCB/PCB.png)


The keyboard uses a custom PCB with the YD-RP2040 attached to it providing a USB-C connection along with power to the board

The YD-RP2040 is the devboard with a chip running this project. You may be able to use a standard Raspberry PI pico but that was not tested

## Case

The keyboard is comprised out of 3 parts. The panel which holds the switches, a back panel and a front panel

Due to their size its impossible to print an entire piece at once, thats why there are sliced versions in the `CAD/Sliced` folder. You can print them separately and then weld them with a soldering iron together. You should weld the front and the back piece but not the panels as they are held together by the frame anyway

![Sliced case](/CAD/Sliced/slided-parts.png)

> [!WARNING]
> Due to the size of the keyboard, even the sliced version requires 216 x 139 mm or larger printing plate

## Compiling & flashing firmware

> [!NOTE]
> You should have CMAKE and GCC installed along with Arm embedded GNU Toolchain `arm-none-eabi-gcc`

For compilation run the following commands in the project folder:
Note that the first command may take a while as it is downloading the SDK from git

> cmake -S Firmware -B Firmware/build -G "Ninja"

> cmake --build Firmware/build --target Keyboard_Firmware

To load the firmware into the RP2040 chip, press the **BOOT** button on the YD-RP2040 devboard and plug it into your computer. It should appear as a drive in which you insert the `Keyboard_Firmware.uf2` file inside the `Firmware/build/` folder. The keyboard should reboot itself and load the active firmware

To reflash the board just repeat the steps above

#BOM is a seperate file
