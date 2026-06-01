# BMP280 for Lilka

A Lua application for displaying temperature and pressure from the BMP280 sensor on the [Lilka](https://lilka.dev) console.

## Wiring

| BMP280 | Lilka  |
|--------|--------|
| VCC    | 3.3V   |
| GND    | GND    |
| SCL    | pin 14 |
| SDA    | pin 13 |

> If the sensor is not detected — try address `0x77` (SDO connected to VCC)

## Features

- Automatic measurement every 60 seconds
- Log of up to 100 measurements
- Scrollable temperature history chart
- Debug screen with detailed intermediate compensation formula values

## Controls

**Main screen**
- `A` — measure now
- `B` — exit
- `C` — measurement log
- `D` — temperature chart

**Chart**
- `LEFT / RIGHT` — scroll through time
- `B` — back

**Log**
- `UP / DOWN` — scroll list
- `A` — detailed debug of measurement
- `B` — back

## Technical Details

The sensor runs in **forced mode** — it powers on only during the measurement (~13 ms) and immediately goes back to sleep. This minimizes self-heating and gives more accurate temperature readings.

Compensation formulas use 32-bit integers from the Bosch datasheet (section 8.2). Bitwise shifts `>>` are replaced with `//` (floor division) due to a Lua quirk: the `>>` operator is logical (unsigned), which gives wrong results on negative intermediate values.
