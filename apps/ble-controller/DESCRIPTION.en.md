# Lilka BLE Controller

Multi-mode Bluetooth HID Controller for Lilka v2.

**Modes: Gamepad • Mouse • Keyboard**

## Features

- **Gamepad Mode**: D-pad + 6 buttons, works with games and emulators
- **Mouse Mode**: D-pad moves cursor, A/B for clicks, C/D for scroll, Start for middle click
- **Keyboard Mode**: On-screen keyboard with 5 rows including special keys
- **Language Switch**: Press SELECT in keyboard mode to switch language (WIN+SPACE)
- **Battery Level**: Displayed on screen and reported via BLE

## Controls

| Button | Gamepad | Mouse | Keyboard |
|--------|---------|-------|----------|
| D-pad | Axes | Move cursor | Navigate keys |
| A | Button 1 | Left click | Type character |
| B | Button 2 | Right click | Backspace |
| C | Button 3 | Scroll up | Toggle layer (abc/ABC/!@#) |
| D | Button 4 | Scroll down | Space |
| Start | Button 5 | Middle click | Enter |
| Select | Button 6 | - | Switch language (WIN+Space) |

**Hold START + SELECT for 3 seconds to switch mode**

## How to Flash

### Option 1: Flash from release

1. Download firmware from [Releases](https://github.com/lilka-dev/BLE_Controller/releases)
2. Open [ESPTool Web Flasher](https://espressif.github.io/esptool-js/) (Chrome/Chromium only)
3. Connect Lilka via USB
4. Click "Erase Flash", then "Program"
5. Select file and address `0x0`

### Option 2: Build from source

```bash
git clone https://github.com/lilka-dev/BLE_Controller.git
cd BLE_Controller
pio run -e en -t upload  # English version
```

## Authors

- [@black-ghost-off](https://github.com/black-ghost-off)

## License

MIT License
