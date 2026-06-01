# PicoPico for Lilka

A port of the PicoPico project for Lilka on ESP32-S3. PicoPico is a Pico-8 game player.

> **Pico-8** is property of **Lexaloffle Games**. This project is an unofficial player and is not affiliated with Lexaloffle.

## Features

- Play Pico-8 games (`.p8` text format)
- Load cartridges from SD card `/Pico8/` folder
- Built-in games flashed into the binary (if no SD card or folder is empty)
- Display scaled to 240×240 on the Lilka screen
- Graphics, sound, and controls support
- Optimized for ESP32-S3 with PSRAM
- Sound via I2S

## Loading Games from SD Card

1. Create a `Pico8` folder in the SD card root (capital `P`)
2. Place cartridges in **text** `.p8` format (not `.p8.png`). Download from [Lexaloffle BBS](https://www.lexaloffle.com/bbs/?cat=7) — click «Cart» → `.p8` file
3. Insert the card into Lilka and launch PicoPico. The first **32** found cartridges appear in the menu

## Controls

In the **cartridge selection menu**:

| Button | Action |
|---|---|
| ↑ / ↓ | Select cartridge |
| A or B | Launch selected cartridge |

In **game**:

| Lilka | Pico-8 |
|---|---|
| D-Pad ←→↑↓ | D-Pad |
| A / C | 🅾️ |
| B / D | ❎ |
| Start or Select | Return to menu |

## Build

```bash
cd lilka
pio run
pio run --target upload
```

## Known Limitations

- `fillp()` — not implemented
- `music()` — stub, background music doesn't play (SFX works)
- `.p8.png` cartridges are not supported

## Authors

- [@black-ghost-off](https://github.com/black-ghost-off)
- Original project: [@DavidVentura](https://github.com/DavidVentura)
