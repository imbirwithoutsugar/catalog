# 🏓 Pong for Lilka

The classic arcade game Pong, ported to the Lilka console (mJS). One player versus a simple AI opponent.

## ✨ Features

- Left paddle controlled via D-pad
- CPU opponent that tracks the ball
- Ball speeds up after each paddle hit
- Score tracking for both sides
- Minimalist graphics: teal and red paddles, dashed center line

## 🎮 Controls

| Button | Action            |
|--------|-------------------|
| UP     | Move paddle up    |
| DOWN   | Move paddle down  |
| A      | Exit game         |

## 🧠 How It Works

- The ball bounces off the top and bottom walls
- After hitting a paddle, horizontal speed increases by `0.3`
- CPU moves the right paddle toward the ball position at `3` pixels per frame

## 🚀 Running

Copy `pong.js` to the apps directory on the Lilka SD card and launch it from the console menu.
