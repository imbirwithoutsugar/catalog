# ⏱️ Timer for Lilka

A simple and convenient timer for the **Lilka (ESP32-S3)** handheld console, with button controls and a sound notification.

## ✨ Features

- Set the time (hours, minutes, seconds)
- Start / pause the timer
- Real-time countdown
- Sound notification when finished
- Intuitive button controls
- Minimalist interface

## 🎮 Controls

| Button | Action |
|--------|--------|
| ⬅️ / ➡️ | Switch between fields (h / m / s) |
| ⬆️ / ⬇️ | Change the value |
| 🅰️ | Start / Pause / Reset |
| 🅱️ | Exit the app |

## 🖥️ Interface

- Time format: `HH:MM:SS`
- The active field is highlighted
- Dynamic hints for the **A** button:
  - `Start` — begin
  - `Stop` — pause
  - `Reset` — after the countdown ends

## 🔊 Sound

When the timer finishes, a melody is played through the buzzer.

## ⚙️ How it works

- The time is set in three fields: hours, minutes, seconds
- On start, the total number of seconds is calculated
- The timer subtracts `delta` (the time between frames)
- When it reaches zero:
  - the timer stops
  - the melody starts playing
  - it switches to the `finished` state
