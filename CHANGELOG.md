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
- Assembly and product photos ([images/](images/)).
- "Design Philosophy" and "Nobs FS Companion App" sections in [README.md](README.md), including a short VR-friendly note (no looking needed to know a switch's state).

### Changed
- Renamed `docs/nobs_panel_wiring_diagram.pdf` to `docs/wiring_diagram.pdf` and updated the links in the README and build instructions.
- Cropped the front-panel product photo ([images/nobs_panel_front.png](images/nobs_panel_front.png)) to remove excess blank canvas above and below the panel.
- Removed em-dash and bare-hyphen sentence connectors and `---` dividers across the docs, in favor of plainer punctuation.

[Unreleased]: https://github.com/ibovegar/nobs-fs-panel/commits/main
