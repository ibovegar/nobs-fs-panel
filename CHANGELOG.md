# Changelog

All notable changes to the Nobs Panel project (hardware, firmware, and documentation) are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Build instructions guide ([docs/build-instructions.md](docs/build-instructions.md)): controller-board assembly (stripboard, pin headers, terminal blocks, Arduino Nano ESP32) and enclosure assembly, each step illustrated with a photo.
- Bill of Materials ([docs/bill-of-materials.md](docs/bill-of-materials.md)): core electronics and switches, structural/enclosure hardware, connectors and wiring, plus a per-panel project cost estimate.
- Board identity guide ([docs/board-identity.md](docs/board-identity.md)).
- Arduino Nano ESP32 firmware sketch ([firmware/arduino_eps32_nano/arduino_eps32_nano.ino](firmware/arduino_eps32_nano/arduino_eps32_nano.ino)).
- Left-mount firmware variant ([firmware/arduino_eps32_nano_left/arduino_eps32_nano_left.ino](firmware/arduino_eps32_nano_left/arduino_eps32_nano_left.ino)) and its wiring map ([docs/arduino-esp-32-wiring-left.md](docs/arduino-esp-32-wiring-left.md)), for mounting the panel on the left side of a frame. The map is mirrored for a left mount: the switch order is reversed (SW1/SW2 swap pin groups with SW8/SW7, SW3 with SW6, SW4 with SW5) and each switch's two terminals are swapped so the rotated mount doesn't invert up/down; same 16 buttons as the standard variant. So a left and right panel can share a rig without their MSFS bindings colliding, the left variant defaults to the 2nd panel instance of the PID block (`80F1` / "Nobs Panel 2") instead of `80F0`. Documented in the README "Mounting orientation" section, [docs/board-identity.md](docs/board-identity.md), and cross-linked from the build instructions and standard wiring map.
- Assembly and product photos ([images/](images/)).
- "Design Philosophy" and "Nobs FS Companion App" sections in [README.md](README.md), including a short VR-friendly note (no looking needed to know a switch's state).

### Changed
- Renamed `docs/nobs_panel_wiring_diagram.pdf` to `docs/wiring_diagram.pdf` and updated the links in the README and build instructions.
- Cropped the front-panel product photo ([images/nobs_panel_front.png](images/nobs_panel_front.png)) to remove excess blank canvas above and below the panel.
- Removed em-dash and bare-hyphen sentence connectors and `---` dividers across the docs, in favor of plainer punctuation.

[Unreleased]: https://github.com/ibovegar/nobs-fs-panel/commits/main
