# MC Resizer (Linux)

A simple Minecraft window toggle tool for Linux (KDE Wayland + X11).

## Why?

I noticed there wasn't a simple, easy-to-install Minecraft window resizer for Linux.

On Windows, **Jingle** is widely used in the speedrunning community and provides great functionality.
However, it is not supported on Linux.

While this script does not aim to replicate all of Jingle's features, in practice most players primarily use it for thin window resizing and boat eye setups.

This project focuses on providing that core functionality in a lightweight and simple way for Linux users.

## What it does

Cycles between:

- Fullscreen
- 1920x200 (Thin mode, centered)
- 450x1080 (Wide mode, centered)

Each key press moves to the next mode:

Fullscreen → Thin → Wide → Fullscreen

## How it works

On first run, the script generates a KWin JavaScript file at `~/.local/share/mc-resizer/resize.js` with the configured dimensions baked in. On each keypress, it loads the JS into KDE's window manager via DBus (`org.kde.kwin.Scripting`), where it finds the Minecraft window by title (`Minecraft*` or `MCSR`), checks the current state, and cycles to the next mode. Size matching uses a ±10px tolerance to account for window manager adjustments.

## Competitive Fairness

Thin mode significantly improves visibility when locating structures such as fortresses.
Without access to similar tools, Linux players can be at a disadvantage compared to Windows players using Jingle.

Although this is a minimal script, combining it with OBS allows Linux players to create a fair and competitive speedrunning setup.

## Requirements

- KDE Plasma (Wayland or X11)
- `qdbus6` (included with KDE)

## Installation

```bash
chmod +x mc-resizer
cp mc-resizer ~/.local/bin/
```

## Usage

### KDE Plasma

1. Go to **System Settings → Shortcuts → Add Application**
2. Select `mc-resizer` (or create a `.desktop` file pointing to it)
3. Assign your preferred key (e.g. `Meta+H`)

### Custom .desktop entry (optional)

Place this in `~/.local/share/applications/net.local.mc-resizer.desktop`:

```ini
[Desktop Entry]
Exec=/home/YOUR_USER/.local/bin/mc-resizer
Name=mc-resizer
NoDisplay=true
StartupNotify=false
Type=Application
X-KDE-GlobalAccel-CommandShortcut=true
```

Then assign a global shortcut to it in **System Settings → Shortcuts**.

Each time you press the key, the window will cycle:

Fullscreen → Thin → Wide → Fullscreen

## Configuration

To change the window sizes, edit the values at the top of the `mc-resizer` script and delete `~/.local/share/mc-resizer/resize.js` — it will regenerate on the next run.

## Notes

This is a lightweight Bash script that uses KWin's built-in scripting engine via DBus.
It is not intended to replace Jingle, but to provide a practical alternative for Linux users.
