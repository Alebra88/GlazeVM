# GlazeVM Configuration

A comprehensive and well-organized configuration for [GlazeWM](https://github.com/glzr-io/glazewm), a tiling window manager for Windows.

## What is GlazeWM?

GlazeWM is a tiling window manager for Windows that automatically arranges your windows in non-overlapping layouts. It brings the efficiency of tiling window managers (commonly found in Linux) to the Windows platform, allowing you to navigate and manage windows entirely via keyboard shortcuts.

## Features

This configuration provides:

- **Tiling Window Management**: Automatic window arrangement with customizable gaps
- **9 Workspaces**: Organize your windows across multiple virtual desktops
- **Vim-style Keybindings**: Navigate using `h/j/k/l` or arrow keys
- **Visual Effects**: Colored borders for focused windows (Windows 11)
- **Zebar Integration**: Built-in status bar support
- **Resize Mode**: Dedicated mode for precise window resizing
- **Smart Window Rules**: Automatic handling of special windows (PiP, PowerToys, etc.)

## Quick Start

### Installation

1. **Install GlazeWM**:
   - Download from [GlazeWM Releases](https://github.com/glzr-io/glazewm/releases)
   - Or install via package manager: `scoop install glazewm` or `winget install glzr-io.GlazeWM`

2. **Install Zebar** (optional, for status bar):
   - Download from [Zebar Releases](https://github.com/glzr-io/zebar/releases)

3. **Apply This Configuration**:
   ```bash
   # Clone this repository
   git clone <your-repo-url> glazevm-config

   # Copy config to GlazeWM config directory
   # Default location: %USERPROFILE%\.glzr\glazewm\config.yaml
   cp glazevm-config/config.yaml %USERPROFILE%\.glzr\glazewm\config.yaml
   ```

4. **Start GlazeWM**: Launch GlazeWM from the Start menu or your preferred launcher

## Configuration Overview

### Window Behavior

- **Initial State**: New windows open in tiling mode
- **Floating Windows**: Centered by default when toggled
- **Focus**: Does not follow cursor (manual focus changes only)
- **Hide Method**: Uses Windows 11's "cloak" API for smooth workspace switching

### Visual Styling

- **Focused Window Border**: Light blue (`#8dbcff`)
- **Unfocused Border**: Gray (`#a1a1a1`)
- **Window Gaps**: 2px inner and outer gaps (scales with DPI)
- **Compatibility**: Borders require Windows 11

### Workspaces

Nine workspaces numbered `1` through `9`:
- Switch with `Alt + [1-9]`
- Move windows with `Alt + Shift + [1-9]`
- Workspaces toggle back-and-forth when refocused

## Essential Keybindings

### Window Navigation
| Keybinding | Action |
|------------|--------|
| `Alt + H/J/K/L` or `Alt + Arrow Keys` | Move focus left/down/up/right |
| `Alt + Space` | Cycle focus between tiling/floating/fullscreen windows |
| `Alt + [1-9]` | Switch to workspace 1-9 |
| `Alt + A/S` | Previous/next active workspace |
| `Alt + D` | Focus recently used workspace |

### Window Management
| Keybinding | Action |
|------------|--------|
| `Alt + Shift + H/J/K/L` or `Alt + Shift + Arrow Keys` | Move window left/down/up/right |
| `Alt + Shift + [1-9]` | Move window to workspace 1-9 and follow |
| `Alt + Q` | Close focused window |
| `Alt + M` | Minimize window |

### Window States
| Keybinding | Action |
|------------|--------|
| `Alt + Shift + Space` | Toggle floating mode (centered) |
| `Alt + T` | Toggle tiling mode |
| `Alt + F` | Toggle fullscreen |
| `Alt + V` | Toggle tiling direction (horizontal/vertical) |

### Window Resizing
| Keybinding | Action |
|------------|--------|
| `Alt + U/I/O/P` | Resize window (decrease width/height, increase height/width) |
| `Alt + R` | Enter resize mode (use arrow keys or HJKL, then Enter/Esc to exit) |

### System Controls
| Keybinding | Action |
|------------|--------|
| `Alt + Enter` | Launch CMD terminal |
| `Alt + Shift + R` | Reload GlazeWM configuration |
| `Alt + Shift + W` | Redraw all windows |
| `Alt + Shift + E` | Exit GlazeWM |
| `Alt + Shift + P` | Pause/unpause GlazeWM (disable all keybindings) |

For the complete keybinding reference, see [KEYBINDINGS.md](KEYBINDINGS.md).

## Customization

This configuration is designed to be easily customizable. See [CUSTOMIZATION.md](CUSTOMIZATION.md) for detailed guides on:

- Changing keybindings
- Adjusting window gaps and borders
- Adding custom workspaces
- Creating window rules
- Modifying visual effects
- Integration with other tools

## File Structure

```
.
├── config.yaml          # Main GlazeWM configuration file
├── README.md            # This file
├── KEYBINDINGS.md       # Complete keybinding reference
└── CUSTOMIZATION.md     # Customization guide
```

## Integrated Tools

### Zebar
A status bar for GlazeWM. This config automatically starts Zebar on launch and kills it on exit.

- **Startup**: `zebar` (automatically launched)
- **Config Location**: Usually `%USERPROFILE%\.glzr\zebar\`

### PowerToys Integration
Windows PowerToys tools are configured to be ignored by the window manager:
- PowerAccent (character picker)
- Peek (file previewer)

## IDE Compatibility

**Important for DataGrip and JetBrains IDE users:**

This configuration uses `Alt` key shortcuts that conflict with DataGrip and other JetBrains IDEs. 

**Quick Fix:**
1. Open `config.yaml`
2. Find the `window_rules` section (around line 159)
3. Uncomment the DataGrip line:
   ```yaml
   - window_process: { equals: 'datagrip64' }  # Remove the # at start
   ```
4. Reload: `Alt + Shift + R`

See [CUSTOMIZATION.md](CUSTOMIZATION.md#ide-and-developer-tool-conflicts) for detailed solutions.

## Troubleshooting

### Keybindings Not Working
1. Ensure GlazeWM is running (check system tray)
2. Check if keybindings conflict with other applications (especially IDEs)
3. Try `Alt + Shift + R` to reload the configuration
4. Verify you haven't pressed `Alt + Shift + P` (pause mode)

### Borders Not Showing
- Window borders require Windows 11
- Check that `window_effects.focused_window.border.enabled` is `true` in config.yaml

### Zebar Not Launching
- Ensure Zebar is installed and in your PATH
- Check `general.startup_commands` in config.yaml
- Manually test: run `zebar` in a terminal

### Window Gaps Too Large/Small
- Edit `gaps.inner_gap` and `gaps.outer_gap` values in config.yaml
- Reload configuration: `Alt + Shift + R`

## Resources

- [GlazeWM Documentation](https://github.com/glzr-io/glazewm)
- [GlazeWM Discord Community](https://discord.gg/ud6z3qjRvM)
- [Zebar Documentation](https://github.com/glzr-io/zebar)

## Contributing

Feel free to fork this configuration and adapt it to your needs! If you make improvements or discover useful configurations, consider sharing them.

## License

This configuration is provided as-is for personal use. GlazeWM itself is licensed under GPL-3.0.

---

**Tip**: Start with the default keybindings and gradually customize them to match your workflow. The vim-style navigation (`hjkl`) provides an efficient way to manage windows without leaving the home row!
