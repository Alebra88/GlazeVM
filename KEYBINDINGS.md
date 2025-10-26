# GlazeWM Keybindings Reference

Complete reference for all keyboard shortcuts in this GlazeWM configuration.

## Modifier Key

All keybindings use `Alt` as the primary modifier:
- `Alt` - Basic actions (focus, resize, toggle)
- `Alt + Shift` - Advanced actions (move, system controls)

## Navigation

### Focus Window
Move keyboard focus between windows.

| Keybinding | Action | Config Line |
|------------|--------|-------------|
| `Alt + H` | Focus window to the left | config.yaml:169 |
| `Alt + J` | Focus window below | config.yaml:175 |
| `Alt + K` | Focus window above | config.yaml:173 |
| `Alt + L` | Focus window to the right | config.yaml:171 |
| `Alt + Left Arrow` | Focus window to the left | config.yaml:169 |
| `Alt + Down Arrow` | Focus window below | config.yaml:175 |
| `Alt + Up Arrow` | Focus window above | config.yaml:173 |
| `Alt + Right Arrow` | Focus window to the right | config.yaml:171 |

### Focus Cycling
| Keybinding | Action | Config Line |
|------------|--------|-------------|
| `Alt + Space` | Cycle focus: tiling → floating → fullscreen | config.yaml:215 |

### Workspace Focus
Switch between virtual desktops.

| Keybinding | Action | Config Line |
|------------|--------|-------------|
| `Alt + 1` | Focus workspace 1 | config.yaml:267 |
| `Alt + 2` | Focus workspace 2 | config.yaml:269 |
| `Alt + 3` | Focus workspace 3 | config.yaml:271 |
| `Alt + 4` | Focus workspace 4 | config.yaml:273 |
| `Alt + 5` | Focus workspace 5 | config.yaml:275 |
| `Alt + 6` | Focus workspace 6 | config.yaml:277 |
| `Alt + 7` | Focus workspace 7 | config.yaml:279 |
| `Alt + 8` | Focus workspace 8 | config.yaml:281 |
| `Alt + 9` | Focus workspace 9 | config.yaml:283 |

### Advanced Workspace Navigation
| Keybinding | Action | Config Line |
|------------|--------|-------------|
| `Alt + A` | Focus previous active workspace | config.yaml:259 |
| `Alt + S` | Focus next active workspace | config.yaml:257 |
| `Alt + D` | Focus most recently used workspace | config.yaml:263 |

## Window Movement

### Move Window Within Workspace
| Keybinding | Action | Config Line |
|------------|--------|-------------|
| `Alt + Shift + H` | Move window left | config.yaml:179 |
| `Alt + Shift + J` | Move window down | config.yaml:185 |
| `Alt + Shift + K` | Move window up | config.yaml:183 |
| `Alt + Shift + L` | Move window right | config.yaml:181 |
| `Alt + Shift + Left Arrow` | Move window left | config.yaml:179 |
| `Alt + Shift + Down Arrow` | Move window down | config.yaml:185 |
| `Alt + Shift + Up Arrow` | Move window up | config.yaml:183 |
| `Alt + Shift + Right Arrow` | Move window right | config.yaml:181 |

### Move Window to Workspace
Move the focused window to a specific workspace and follow it.

| Keybinding | Action | Config Line |
|------------|--------|-------------|
| `Alt + Shift + 1` | Move window to workspace 1 (and focus) | config.yaml:298 |
| `Alt + Shift + 2` | Move window to workspace 2 (and focus) | config.yaml:300 |
| `Alt + Shift + 3` | Move window to workspace 3 (and focus) | config.yaml:302 |
| `Alt + Shift + 4` | Move window to workspace 4 (and focus) | config.yaml:304 |
| `Alt + Shift + 5` | Move window to workspace 5 (and focus) | config.yaml:306 |
| `Alt + Shift + 6` | Move window to workspace 6 (and focus) | config.yaml:308 |
| `Alt + Shift + 7` | Move window to workspace 7 (and focus) | config.yaml:310 |
| `Alt + Shift + 8` | Move window to workspace 8 (and focus) | config.yaml:312 |
| `Alt + Shift + 9` | Move window to workspace 9 (and focus) | config.yaml:314 |

### Move Workspace Between Monitors
Move the entire workspace to a different monitor.

| Keybinding | Action | Config Line |
|------------|--------|-------------|
| `Alt + Shift + A` | Move workspace to left monitor | config.yaml:288 |
| `Alt + Shift + D` | Move workspace to monitor above | config.yaml:292 |
| `Alt + Shift + S` | Move workspace to monitor below | config.yaml:294 |
| `Alt + Shift + F` | Move workspace to right monitor | config.yaml:290 |

## Window States

### Toggle Window States
| Keybinding | Action | Config Line |
|------------|--------|-------------|
| `Alt + Shift + Space` | Toggle floating mode (centered) | config.yaml:219 |
| `Alt + T` | Toggle tiling mode | config.yaml:223 |
| `Alt + F` | Toggle fullscreen | config.yaml:227 |
| `Alt + M` | Minimize window | config.yaml:231 |
| `Alt + Q` | Close window | config.yaml:235 |

### Tiling Behavior
| Keybinding | Action | Config Line |
|------------|--------|-------------|
| `Alt + V` | Toggle tiling direction (horizontal ↔ vertical) | config.yaml:211 |

## Window Resizing

### Quick Resize
Resize by 2% increments.

| Keybinding | Action | Config Line |
|------------|--------|-------------|
| `Alt + U` | Decrease window width | config.yaml:189 |
| `Alt + I` | Decrease window height | config.yaml:195 |
| `Alt + O` | Increase window height | config.yaml:193 |
| `Alt + P` | Increase window width | config.yaml:191 |

### Resize Mode
Enter a dedicated mode for precise resizing.

| Keybinding | Action | Config Line |
|------------|--------|-------------|
| `Alt + R` | Enter resize mode | config.yaml:201 |

**In Resize Mode:**
| Keybinding | Action | Config Line |
|------------|--------|-------------|
| `H` or `Left Arrow` | Decrease width by 2% | config.yaml:155 |
| `J` or `Down Arrow` | Decrease height by 2% | config.yaml:161 |
| `K` or `Up Arrow` | Increase height by 2% | config.yaml:159 |
| `L` or `Right Arrow` | Increase width by 2% | config.yaml:157 |
| `Enter` or `Escape` | Exit resize mode | config.yaml:164 |

## Application Launcher

| Keybinding | Action | Config Line |
|------------|--------|-------------|
| `Alt + Enter` | Launch CMD terminal | config.yaml:253 |

**Note**: You can modify this to launch other terminals:
- Windows Terminal: `shell-exec wt`
- Git Bash: `shell-exec %ProgramFiles%/Git/git-bash.exe`
- PowerShell: `shell-exec powershell`

## System Controls

### GlazeWM Management
| Keybinding | Action | Config Line |
|------------|--------|-------------|
| `Alt + Shift + R` | Reload configuration | config.yaml:243 |
| `Alt + Shift + W` | Redraw all windows | config.yaml:247 |
| `Alt + Shift + E` | Exit GlazeWM | config.yaml:239 |
| `Alt + Shift + P` | Pause/unpause window management | config.yaml:206 |

**Pause Mode:**
When paused (`Alt + Shift + P`), all GlazeWM keybindings are disabled. This is useful when:
- Using applications with conflicting keybindings
- Playing games that use Alt key
- Temporarily disabling window management

Press `Alt + Shift + P` again to unpause.

## Keybinding Philosophy

### Design Principles
1. **Vim-style Navigation**: `H/J/K/L` for directional movement
2. **Arrow Key Alternatives**: Every vim-style binding has an arrow key equivalent
3. **Progressive Modifiers**:
   - `Alt` alone for viewing/focusing
   - `Alt + Shift` for modifying/moving
4. **Number-based Workspaces**: Direct access to workspaces 1-9
5. **Mnemonic Keys**:
   - `R` for Resize
   - `Q` for Quit/Close
   - `F` for Fullscreen
   - `T` for Tiling
   - `M` for Minimize
   - `V` for Vertical/horizontal toggle

### Conflict Avoidance
This configuration avoids conflicts with common Windows shortcuts:
- `Alt + Tab` (window switcher) - not used
- `Alt + F4` (close window) - not used
- `Ctrl` combinations - completely unused
- `Win` key - completely unused

## Customization Tips

### Changing Keybindings
Edit `config.yaml` in the `keybindings` section. Each entry has:
```yaml
- commands: ['command-name --flags']
  bindings: ['key+combination', 'alternative+combo']
```

### Adding New Keybindings
1. Choose an unused key combination
2. Add a new entry to the `keybindings` section
3. Reload with `Alt + Shift + R`

### Testing Changes
1. Edit `config.yaml`
2. Press `Alt + Shift + R` to reload
3. Test the new keybinding
4. If it doesn't work, check for conflicts or syntax errors

## Quick Reference Card

### Most Used Commands
```
Navigation:        Alt + HJKL / Arrows
Move Window:       Alt + Shift + HJKL / Arrows
Workspaces:        Alt + [1-9]
Move to Workspace: Alt + Shift + [1-9]
Close Window:      Alt + Q
Floating:          Alt + Shift + Space
Fullscreen:        Alt + F
Resize Mode:       Alt + R
Terminal:          Alt + Enter
Reload Config:     Alt + Shift + R
```

---

**Tip**: Print this reference or keep it handy while learning GlazeWM. After a few days, the vim-style keybindings will become muscle memory!
