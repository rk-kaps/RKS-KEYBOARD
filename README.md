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

#BOM 

| Ref | Component | Qty | Unit Price (₹) | Total (₹) | Store |
|-----|-----------|-----|---------------|-----------|-------|
| MCU | [YD-RP2040](https://probots.co.in/yd-rp2040-4mb-flash-usb-type-c-pico-compatible.html) | 1 | ₹326.54 | ₹326.54 | Probots |
| IC1 | [74AHCT125DR — Logic Level Shifter](https://evelta.com/sn74hct125dr-buffer-line-driver-4ch-non-inverting-3-st-cmos-soic-14/) | 1 | ₹328.72 | ₹328.72 | Evelta |
| C | [100nF 0805 Ceramic Capacitor (≥ 6.3V)](https://robu.in/product/100nf-0805-surface-mount-multilayer-ceramic-capacitor-pack-of-40/) | 105 | ₹2.18 | ₹228.90 | Robu.in |
| R | [10kΩ 0805 Resistor](https://robu.in/product/10k-ohm-1-4w-0805-surface-mount-chip-resistor-pack-of-10/) | 2 | ₹2.18 | ₹4.36 | Robu.in |
| D | [1N4148W Diode (SOD-123)](https://robu.in/product/1n4148w-7-f-diodes-inc-1n4148w-7-f-small-signal-diode-single-100-v-300-ma-1-25-v-4-ns-2-a/) | 103 | ₹2.18 | ₹224.54 | Robu.in |
| HS | [Kailh Hot-Swap Sockets](https://meckeys.com/shop/accessories/keyboard-accessories/key-switches/kailh-hot-swap-socket/) | 103 | ₹899.89 | ₹899.89 | Meckeys |
| SW | [Gateron G Pro 3.0 Switch (MX)](https://meckeys.com/shop/accessories/keyboard-accessories/key-switches/gateron-g-pro-3-0-switch/) | 103 | ₹40.41 | ₹4,162.23 | Meckeys |
| OLED | [1.5" OLED Display 128×128 I2C](https://robu.in/product/0-91-inch-128x32-i2c-iic-serial-blue-oled-lcd-display-module/) | 1 | ₹464.14 | ₹464.14 | Robu.in |
| LED | [SK6812 Mini-E RGB LED ×200](https://stackskb.com/store/) | 2 | ₹369.13 | ₹738.26 | StacksKB |
| KP | [Keycap Set (MX compatible)](https://meckeys.com/category/accessories/keyboard-accessories/keycaps/) | 1 | ₹1,848.93 | ₹1,848.93 | Meckeys |
| SCR | [M3×8 Socket Head Cap Screw](https://robu.in/product/easymech-set-m3-x-8mm-socket-head-cap-allen-bolt-nut-12-pcs/) | 8 | ₹5.46 | ₹43.68 | Robu.in |
| INS | [Hot Melt Insert M3 L4 OD4.2](https://robu.in/product/m3-x-8-mm-brass-heat-set-threaded-round-insert-nut-25-pcs/) | 8 | ₹12.01 | ₹96.08 | Robu.in |
| FEET | [Silicone Feet 12×3mm ×4](https://www.amazon.in/s?k=silicone+feet+12mm+self+adhesive) | 1 | ₹78.63 | ₹78.63 | Amazon.in |
| PCB | [Custom PCB — no assembly](https://jlcpcb.com) | 1 | ₹4,368.40 | ₹4,368.40 | JLCPCB |
| | | | **TOTAL** | **₹13,813.30** | |

