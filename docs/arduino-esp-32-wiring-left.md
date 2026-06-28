# Wiring Map (Left Mount): Which Wire Goes Where

This is the wiring table for the **left-mount** version of the panel, mounted on the **left** side
of a track-racer T-profile aluminium frame. It pairs with the left firmware in
[`firmware/arduino_eps32_nano_left/`](../firmware/arduino_eps32_nano_left/). For a standard (right)
mount, use [arduino-esp-32-wiring.md](arduino-esp-32-wiring.md) and its firmware instead.

Compared with the standard wiring, the panel is **mirrored for a left mount**, which changes the
map in two ways:

1. **The switch order is reversed** so the switches read in the correct order from the left: SW1/SW2
   trade their pin groups with SW8/SW7, and the middle four mirror too (**SW3 swaps with SW6, SW4
   swaps with SW5**).
2. **Each switch's two positions are flipped.** The switch sits rotated in a left mount, so its Pin
   1 and Pin 3 terminals map to the opposite position (and HID button) than on the standard mount.
   Without this the switches would read upside down (flipping up shows as down).

The board pin each terminal connects to is the actionable column and is the same as how the switch
is physically wired; the switch types and the set of 16 HID buttons are unchanged.

This button box has **8 toggle switches**: SW1–SW6 are **ON-ON** (2-position) and SW7–SW8 are
**ON-OFF-ON** (3-position, with the center position doing nothing). Every switch has three
terminals: the two outer terminals (pin 1 and pin 3) each go to a signal pin, and the center
terminal (pin 2) goes to **GND**.

**How to read a row:** find the switch (e.g. "SW1"), look at which terminal it is ("Pin 1"), then
run a wire from that terminal to the pin listed in the board's column. Pin names like `D13` or
`A0` are printed on the board itself. Every switch's center terminal (pin 2) connects to **GND**
(ground), see the last row.

The "Virtual HID Button" column is just for reference: it's the button number the sim sees when
you flip that switch into that position. You don't wire anything for it.

> 💡 Each switch terminal has one wire to its signal pin (from this table) and the center terminal
> wires to **GND**. No resistors or extra parts needed; the firmware handles that.

| Component Group | Component Label | Hardware Connection | Arduino Nano ESP32 Pin | Virtual HID Button | Action Type |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **SW1** (ON-ON) | Switch 1 | Pin 1 Terminal | **D8** | Button 2 | Position 2 |
| | Switch 1 | Pin 3 Terminal | **D7** | Button 1 | Position 1 |
| **SW2** (ON-ON) | Switch 2 | Pin 1 Terminal | **D6** | Button 4 | Position 2 |
| | Switch 2 | Pin 3 Terminal | **D5** | Button 3 | Position 1 |
| **SW3** (ON-ON) | Switch 3 | Pin 1 Terminal | **D10** | Button 6 | Position 2 |
| | Switch 3 | Pin 3 Terminal | **D9** | Button 5 | Position 1 |
| **SW4** (ON-ON) | Switch 4 | Pin 1 Terminal | **D12** | Button 8 | Position 2 |
| | Switch 4 | Pin 3 Terminal | **D11** | Button 7 | Position 1 |
| **SW5** (ON-ON) | Switch 5 | Pin 1 Terminal | **A6** | Button 10 | Position 2 |
| | Switch 5 | Pin 3 Terminal | **A7** | Button 9 | Position 1 |
| **SW6** (ON-ON) | Switch 6 | Pin 1 Terminal | **A4** | Button 12 | Position 2 |
| | Switch 6 | Pin 3 Terminal | **A5** | Button 11 | Position 1 |
| **SW7** (ON-OFF-ON) | Switch 7 | Pin 1 Terminal | **A2** | Button 14 | Position 2 |
| | Switch 7 | Pin 3 Terminal | **A3** | Button 13 | Position 1 |
| **SW8** (ON-OFF-ON) | Switch 8 | Pin 1 Terminal | **A0** | Button 16 | Position 2 |
| | Switch 8 | Pin 3 Terminal | **A1** | Button 15 | Position 1 |
| **Ground Loop** | All Switches | Pin 2 / Center Terminals | **GND** | *None* | System Ground |
| **Status LED** | Status LED | Anode, via 120 Ω resistor | **D4** | *None* | Boot/Connect Status |
| | Status LED | Cathode | **GND** | *None* | Boot/Connect Status |

> 💡 **Status LED:** wired with a 120 Ω current-limiting resistor from **D4** to **GND**. It blinks
> while the board is booting/waiting for USB enumeration, and lights steady once the host PC has
> enumerated it. (Same as the standard mount — the LED isn't affected by the left-mount pin swap.)
