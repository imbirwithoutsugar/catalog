# LoRa Transmitter - Walkie-Talkie Module for Lilka

This project contains schematics and firmware for a walkie-talkie module on ESP32 with AES256(GCM) encryption for the [Lilka v2](https://github.com/and3rson/lilka) board. The firmware for the main board and transmitter module is built on the [Meowui](https://github.com/Kolodieiev/meowui) framework. Audio codec: codec2.

## Project Features

- Encrypted voice transmission over 250+ meters with 5dbi antennas
- Enable/disable encryption
- Channel switching (in Ukraine, only 433 MHz — channel 23 — is permitted for general use)
- Key generation and settings exchange between Lilka boards

## Main Module Components

- Transmitter — LoRa E220-400T22D (UART version)
- MCU — ESP32 WROOM on an adapter board
- Microphone — INMP441
- DC-DC step-down converter — Mini560 3.3V
- Single-sided 5×7 cm PCB

## Usage Requirements

To use the walkie-talkie module with Lilka v2, you need: a battery pack, a memory card for settings storage, and an audio kit or a PCM5102A sound card module.

The walkie-talkie module has its own power supply separate from the Lilka board. Communication uses the I2C bus via a 4-wire cable under 50 cm long.

## Discussion

Ask questions to the author in the [Lilka community Discord server](https://discord.com/channels/1202315568846213172/1354083451531427920).
