# Pixeler for Lilka v2

Alternative firmware for the Lilka v2 board based on the Pixeler framework.

## Features

The firmware is built using the `Pioarduino` plugin and cannot be built with `Platformio`.

Prebuilt binary firmware files ready to flash are located in the `pixeler4lilkav2\bin\parts` directory.

To flash from `Keira OS` — copy `firmware.bin` to the memory card and flash it.

To install without rollback in `Keira OS` — flash `pixeler.bin` directly using the `esptool` utility.

## Documentation

Framework documentation is located in `pixeler4lilkav2\src\pixeler\doc`.
It can be built and run locally by following the steps in the Readme.
