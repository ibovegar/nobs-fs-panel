# Nobs Panel: Arduino Nano ESP32 Firmware (left-mount variant)

This is the **left-mount** version of the Nobs Panel firmware, for a panel mounted on the **left**
side of a track-racer T-profile aluminium frame. It is identical to the standard (right-mount)
firmware in [`../arduino_eps32_nano/`](../arduino_eps32_nano/) except for the switch-to-pin map:
SW1/SW2 and SW7/SW8 trade pin groups so the switches read in the correct order from the left,
SW3–SW6 are unchanged. It exposes the same **16 buttons**. Wiring is in
[`docs/arduino-esp-32-wiring-left.md`](../../docs/arduino-esp-32-wiring-left.md).

Because a left panel is built to share a rig with a standard (right) panel, this firmware defaults
to the **2nd panel instance** of the panel PID block: PID **`80F1`** / name **"Nobs Panel 2"**
(the standard panel is instance 1, `80F0` / "Nobs Panel"). The two then never collide, so the
simulator keeps their bindings separate. Add it on the Nobs app's **Devices** page with the **+**
on the panel product, which tracks it as the 2nd panel. (If a left panel is your *only* panel, you
can move it onto `80F0` / "Nobs Panel" with the config app.) See
[`docs/board-identity.md`](../../docs/board-identity.md) for the full ID scheme.

> Flash this sketch only if you built the panel for a **left** mount. For a standard (right) mount,
> use [`../arduino_eps32_nano/`](../arduino_eps32_nano/) instead. The two are not interchangeable:
> they expect the switches wired to different pins.

> 👍 Everything you need is in this folder. You don't edit any Arduino files. Keep
> [`build_opt.h`](./build_opt.h) next to the sketch: the IDE uses it automatically, and the build
> fails on purpose without it. Tested with the Arduino ESP32 board package `2.0.18-arduino.5`.

## One-time setup

1. Install the **Arduino IDE** (free, from arduino.cc).
2. Add the board: **Tools → Board → Boards Manager…**, search **Arduino ESP32 Boards**, click
   **Install** (big download). Then pick **Tools → Board → Arduino ESP32 Boards → Arduino Nano ESP32**.
3. In **Tools**, set **USB Mode → `Normal mode (TinyUSB)`** and **Pin Numbering → `By Arduino pin (default)`**.

> If the board install fails ("platform not installed"), close the IDE, reopen it **as
> administrator**, and try again.

## Flashing the first time

1. Open [`arduino_eps32_nano_left.ino`](./arduino_eps32_nano_left.ino) in the Arduino IDE.
2. Plug in the board with a **data** USB cable (not charge-only), straight into the PC.
3. Click **Upload** (the round arrow).

On a fresh board this just works. 🎉 When it's done, the board reconnects as **"Nobs Panel 2"** and
the app picks it up automatically.

## Re-flashing (after firmware is already on it)

This is **different**, and expected. Once the firmware is running, the board reports a custom USB
ID and no longer auto-enters upload mode, so a normal Upload fails with:

```
No DFU capable USB device available — exit status 74
```

Put the board into **update mode** by hand first:

1. Press the **RESET** button **twice, quickly** (like a mouse double-click, ~0.3–0.5 s apart).
2. You're in update mode when the **green LED breathes slowly in and out and stays there**.
   A quick red→blue→green flash that stops is just a normal reset; try the double-tap again.
3. With the green breathing, click **Upload** right away.
4. When it finishes, press **RESET once** to start the firmware.

> **If upload still can't find the board:** it's almost always the **cable or USB port**. Swap to
> a known-good data cable and a different port (this is the most common cause). The double-tap
> timing is the other one; keep trying the rhythm.

## Check it works

- **Nobs app:** the panel is detected automatically; flip switches and watch them light up.
- **Windows:** press `Win`, type **Set up USB game controllers**, open the device's **Properties**,
  and flip switches to see the 16 buttons react.

## Changing the board's name / ID

The name and product ID aren't compiled in; they're stored on the board, so the same firmware can
become any Nobs profile. Out of the box this variant is **"Nobs Panel 2"** (`303A` / `80F1`). The
configuration app changes it over the board's serial port. See
[`docs/board-identity.md`](../../docs/board-identity.md) for how that works and the full profile list.
