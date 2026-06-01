# Snake (Keira OS)

Classic Snake game in pseudo-graphic style, written in Lua for Keira OS.

## Gameplay

The player controls the snake using arrow buttons:
- **↑** — move up
- **↓** — move down
- **←** — move left
- **→** — move right

The goal: collect food and avoid hitting walls or your own body.

## Game Menu

Pressing button **D** opens a menu with:
- **Continue** — return to the game
- **New Game** — start over
- **Records** — view the high score table
- **Exit** — exit the game

## Features

The high score table is saved in a `.state` file and persists between sessions.

## Technical Details

- Written in **Lua**
- Runs on **Keira OS**
- Pseudo-graphic style
- Progress saving
