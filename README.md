# MC Resizer (Linux)

A simple Minecraft window toggle tool for Linux (X11).

## Why?

I noticed there wasn’t a simple, easy-to-install Minecraft window resizer for Linux.

On Windows, **Jingle** is widely used in the speedrunning community and provides great functionality.  
However, it is not supported on Linux.

While this script does not aim to replicate all of Jingle’s features, in practice most players primarily use it for thin window resizing and boat eye setups.

This project focuses on providing that core functionality in a lightweight and simple way for Linux users.

## What it does

Cycles between:

- Fullscreen
- 1920x200 (Thin mode, centered)
- 450x1080 (Wide mode, centered)

Each key press moves to the next mode:

Fullscreen → Thin → Wide → Fullscreen

## Competitive Fairness

Thin mode significantly improves visibility when locating structures such as fortresses.  
Without access to similar tools, Linux players can be at a disadvantage compared to Windows players using Jingle.

Although this is a minimal script, combining it with OBS allows Linux players to create a fair and competitive speedrunning setup.

## Requirements

- X11 session (Wayland is not supported)
- wmctrl
- xdotool
- xprop
- xdpyinfo

## Installation

```bash
chmod +x mc-resizer
mv mc-resizer ~/.local/bin/
```

## Usage

Bind mc-resizer to a keyboard shortcut in your desktop environment.

Example (GNOME):

```
Open Settings

Go to Keyboard → Keyboard Shortcuts

Add a new custom shortcut

Command: mc-resizer

Assign your preferred key
```

Each time you press the key, the window will cycle:

Fullscreen → Thin → Wide → Fullscreen

## Notes

This is a lightweight Bash implementation using standard X11 tools.
It is not intended to replace Jingle, but to provide a practical alternative for Linux users.
