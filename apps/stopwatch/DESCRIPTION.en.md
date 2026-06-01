# Stopwatch for Lilka

A simple stopwatch app for the [Lilka](https://lilka.dev) gaming console. Written in Lua as a beginner example.

## Features

- Start and stop the stopwatch
- Record laps with lap time and total time
- Scroll through laps using up/down buttons
- Reset to zero

## Controls

| Button | Action |
|--------|--------|
| **A** | Start / Stop |
| **B** | Exit |
| **D** | Record lap (while running) / Reset to zero (when stopped) |
| **UP** | Scroll laps up |
| **DOWN** | Scroll laps down |

## Installation

1. Copy `stopwatch.lua` to the SD card
2. Select the file in the Lilka SD card browser
3. Run the app

## Code Structure

The app consists of a single file `stopwatch.lua` built on three standard Lilka functions:

- `lilka.update(delta)` — app logic, button handling
- `lilka.draw()` — screen rendering each frame
- helper functions `format_time()` and `draw_button()`
