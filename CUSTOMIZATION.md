# GlazeWM Customization Guide

This guide will help you personalize your GlazeWM configuration to match your workflow and preferences.

## Configuration File Location

Your GlazeWM configuration is stored in:
- **Default**: `%USERPROFILE%\.glzr\glazewm\config.yaml`
- **Windows Path Example**: `C:\Users\YourName\.glzr\glazewm\config.yaml`

After making any changes, reload the configuration with `Alt + Shift + R`.

## Table of Contents

1. [Changing Keybindings](#changing-keybindings)
2. [Customizing Visual Effects](#customizing-visual-effects)
3. [Adjusting Window Gaps](#adjusting-window-gaps)
4. [Managing Workspaces](#managing-workspaces)
5. [Creating Window Rules](#creating-window-rules)
6. [Startup Commands](#startup-commands)
7. [Terminal Integration](#terminal-integration)
8. [Multi-Monitor Setup](#multi-monitor-setup)

---

## Changing Keybindings

### Understanding the Structure

Each keybinding in `config.yaml` follows this format:

```yaml
- commands: ['command-name --flags']
  bindings: ['key+combination', 'alternative']
```

### Example: Change Close Window to Alt+W

**Current** (config.yaml:235):
```yaml
- commands: ['close']
  bindings: ['alt+q']
```

**Modified**:
```yaml
- commands: ['close']
  bindings: ['alt+w']
```

### Common Keybinding Customizations

#### Use Windows Key Instead of Alt

Replace `alt` with `win` in any keybinding:

```yaml
# Original
- commands: ['focus --direction left']
  bindings: ['alt+h']

# Modified to use Windows key
- commands: ['focus --direction left']
  bindings: ['win+h']
```

#### Add Multiple Alternatives

```yaml
- commands: ['close']
  bindings: ['alt+q', 'alt+w', 'ctrl+alt+c']
```

#### Change Terminal Launcher to Ctrl+Alt+T

Find the terminal launcher (config.yaml:253) and modify:

```yaml
- commands: ['shell-exec cmd']
  bindings: ['ctrl+alt+t']
```

### Available Modifiers

- `alt` - Alt key
- `ctrl` - Control key
- `shift` - Shift key
- `win` - Windows key

Combine them: `ctrl+alt+shift+x`

### Finding Unused Keybindings

Common unused combinations in this config:
- `alt+b`, `alt+c`, `alt+e`, `alt+g`, `alt+n`, `alt+w`, `alt+x`, `alt+y`, `alt+z`
- Any `ctrl+` combinations
- Any `win+` combinations (except Windows defaults)

**Important**: Avoid these common system shortcuts:
- `Ctrl+Alt+L` - Screen lock on many Linux systems
- `Ctrl+Alt+Del` - Windows security menu
- `Win+L` - Windows screen lock
- `Alt+F4` - Close application
- `Alt+Tab` - Window switcher

---

## Customizing Visual Effects

### Window Borders

#### Change Border Colors

Located in `config.yaml:64-88`:

```yaml
window_effects:
  focused_window:
    border:
      enabled: true
      color: '#8dbcff'  # Light blue - change to your preference

  other_windows:
    border:
      enabled: true
      color: '#a1a1a1'  # Gray - change to your preference
```

**Color Suggestions**:
- **Green accent**: `'#a6e3a1'`
- **Purple accent**: `'#cba6f7'`
- **Red accent**: `'#f38ba8'`
- **Orange accent**: `'#fab387'`
- **No border**: Set `enabled: false`

#### Enable Window Transparency

Make windows slightly transparent (config.yaml:78-82):

```yaml
focused_window:
  transparency:
    enabled: true
    opacity: '95%'  # 95% opaque (5% transparent)
```

**Note**: Lower values = more transparent
- `'100%'` or `'1'` - Fully opaque (no transparency)
- `'95%'` or `'0.95'` - Slightly transparent
- `'80%'` or `'0.8'` - Noticeably transparent
- `'0%'` or `'0'` - Fully transparent (unusable)

#### Change Window Corners

Windows 11 only (config.yaml:72-75):

```yaml
corner_style:
  enabled: true
  style: 'rounded'  # Options: 'square', 'rounded', 'small_rounded'
```

#### Remove Title Bars

Hide window title bars (config.yaml:67-68):

```yaml
hide_title_bar:
  enabled: true
```

**Warning**: May cause rendering issues with some applications.

---

## Adjusting Window Gaps

### Change Gap Sizes

Located in `config.yaml:50-58`:

```yaml
gaps:
  # Gap between adjacent windows
  inner_gap: '2px'    # Increase for more spacing

  # Gap between windows and screen edge
  outer_gap:
    top: '2px'        # Can be different for each edge
    right: '2px'
    bottom: '2px'
    left: '2px'
```

### Popular Gap Configurations

#### No Gaps (Maximalist)
```yaml
inner_gap: '0px'
outer_gap:
  top: '0px'
  right: '0px'
  bottom: '0px'
  left: '0px'
```

#### Medium Gaps (Balanced)
```yaml
inner_gap: '8px'
outer_gap:
  top: '8px'
  right: '8px'
  bottom: '8px'
  left: '8px'
```

#### Large Gaps (Minimalist)
```yaml
inner_gap: '16px'
outer_gap:
  top: '16px'
  right: '16px'
  bottom: '16px'
  left: '16px'
```

#### Status Bar Configuration
```yaml
# Leave space at top for Zebar or similar
outer_gap:
  top: '40px'    # Adjust based on your bar height
  right: '8px'
  bottom: '8px'
  left: '8px'
```

### DPI Scaling

Control whether gaps scale with monitor DPI (config.yaml:51):

```yaml
scale_with_dpi: true   # Recommended for mixed DPI setups
scale_with_dpi: false  # Fixed size regardless of DPI
```

---

## Managing Workspaces

### Add More Workspaces

Located in `config.yaml:143-152`:

```yaml
workspaces:
  - name: '1'
  - name: '2'
  # ... existing ...
  - name: '9'
  - name: '10'  # Add workspace 10
  - name: '0'   # Add workspace 0
```

Then add keybindings for the new workspaces in the keybindings section:

```yaml
# Focus workspace 10
- commands: ['focus --workspace 10']
  bindings: ['alt+0']

# Move to workspace 10
- commands: ['move --workspace 10', 'focus --workspace 10']
  bindings: ['alt+shift+0']
```

### Named Workspaces

Use descriptive names instead of numbers:

```yaml
workspaces:
  - name: 'web'
  - name: 'code'
  - name: 'terminal'
  - name: 'chat'
  - name: 'music'
```

Update keybindings accordingly:

```yaml
- commands: ['focus --workspace web']
  bindings: ['alt+w']
- commands: ['focus --workspace code']
  bindings: ['alt+c']
```

### Workspace Display Options

Default: `name` (show workspace name)

You can modify GlazeWM's general settings if you want different display behavior.

---

## Creating Window Rules

Window rules automatically configure how specific applications behave.

### Rule Structure

Located in `config.yaml:159-175`:

```yaml
window_rules:
  - commands: ['command1', 'command2']
    match:
      - window_process: { equals: 'app.exe' }
```

### Ignore Specific Windows

Prevent GlazeWM from managing certain windows:

```yaml
window_rules:
  - commands: ['ignore']
    match:
      # Ignore by process name
      - window_process: { equals: 'rainmeter' }

      # Ignore by window title (regex)
      - window_title: { regex: 'Settings' }

      # Ignore by window class
      - window_class: { equals: 'ConsoleWindowClass' }
```

### Force Windows to Float

Make specific applications always open as floating:

```yaml
window_rules:
  - commands: ['set-floating']
    match:
      - window_process: { equals: 'calculator' }
      - window_process: { equals: 'mspaint' }
```

### Send Windows to Specific Workspaces

Automatically move applications to designated workspaces:

```yaml
window_rules:
  - commands: ['move --workspace 1']
    match:
      - window_process: { equals: 'firefox' }

  - commands: ['move --workspace 2']
    match:
      - window_process: { equals: 'Code' }

  - commands: ['move --workspace 3']
    match:
      - window_process: { equals: 'WindowsTerminal' }
```

### Advanced Matching

Combine multiple conditions:

```yaml
window_rules:
  # Match Spotify and make it float on workspace 9
  - commands: ['set-floating', 'move --workspace 9']
    match:
      - window_process: { equals: 'Spotify' }

  # Match any window with "Visual Studio" in title
  - commands: ['move --workspace 2']
    match:
      - window_title: { regex: 'Visual Studio' }
```

### Common Window Rule Commands

- `ignore` - Don't manage this window
- `set-floating` - Make window floating
- `set-tiling` - Make window tiling
- `move --workspace N` - Move to workspace N
- `resize --width X` - Set width
- `resize --height Y` - Set height

---

## Startup Commands

Commands to run when GlazeWM starts (config.yaml:9):

```yaml
general:
  startup_commands:
    - 'shell-exec zebar'
    - 'shell-exec C:\Path\To\wallpaper-app.exe'
```

### Examples

#### Launch Multiple Applications

```yaml
startup_commands:
  - 'shell-exec zebar'
  - 'shell-exec rainmeter'
  - 'shell-exec "C:\Program Files\Everything\Everything.exe"'
```

#### Run PowerShell Script

```yaml
startup_commands:
  - 'shell-exec powershell -File C:\Scripts\setup-workspace.ps1'
```

#### Set Wallpaper

```yaml
startup_commands:
  - 'shell-exec "C:\Program Files\Wallpaper Engine\wallpaper32.exe"'
```

### Shutdown Commands

Run commands when GlazeWM exits (config.yaml:13):

```yaml
shutdown_commands:
  - 'shell-exec taskkill /IM zebar.exe /F'
  - 'shell-exec taskkill /IM rainmeter.exe /F'
```

### Config Reload Commands

Run commands when configuration is reloaded (config.yaml:16):

```yaml
config_reload_commands:
  - 'shell-exec echo Config reloaded > C:\logs\glazewm.log'
```

---

## Terminal Integration

### Change Default Terminal

Located in `config.yaml:253`:

#### Windows Terminal
```yaml
- commands: ['shell-exec wt']
  bindings: ['alt+enter']
```

#### PowerShell 7
```yaml
- commands: ['shell-exec pwsh']
  bindings: ['alt+enter']
```

#### Git Bash
```yaml
- commands: ['shell-exec "%ProgramFiles%/Git/git-bash.exe"']
  bindings: ['alt+enter']
```

#### WSL (Windows Subsystem for Linux)
```yaml
- commands: ['shell-exec wt wsl']
  bindings: ['alt+enter']
```

#### Alacritty
```yaml
- commands: ['shell-exec alacritty']
  bindings: ['alt+enter']
```

#### Custom Path
```yaml
- commands: ['shell-exec "C:\\Tools\\Terminal\\terminal.exe"']
  bindings: ['alt+enter']
```

### Multiple Terminal Bindings

```yaml
# Alt+Enter for Windows Terminal
- commands: ['shell-exec wt']
  bindings: ['alt+enter']

# Ctrl+Alt+T for PowerShell
- commands: ['shell-exec pwsh']
  bindings: ['ctrl+alt+t']

# Alt+Shift+Enter for Git Bash
- commands: ['shell-exec "%ProgramFiles%/Git/git-bash.exe"']
  bindings: ['alt+shift+enter']
```

---

## Multi-Monitor Setup

### Cursor Jump Behavior

Control when the cursor moves automatically (config.yaml:25-32):

```yaml
cursor_jump:
  enabled: true
  trigger: 'monitor_focus'  # Options: 'monitor_focus', 'window_focus'
```

**Options**:
- `monitor_focus` - Cursor jumps only when switching monitors (recommended)
- `window_focus` - Cursor jumps every time you change window focus

### Focus Follows Cursor

Enable/disable automatic focus when cursor moves (config.yaml:19):

```yaml
focus_follows_cursor: false  # Default: manual focus
focus_follows_cursor: true   # Automatic focus under cursor
```

### Move Workspace Between Monitors

The default configuration includes keybindings for moving workspaces (config.yaml:288-295):

```yaml
- commands: ['move-workspace --direction left']
  bindings: ['alt+shift+a']
- commands: ['move-workspace --direction right']
  bindings: ['alt+shift+f']
```

---

## Testing Your Changes

### Reload Configuration
1. Edit `config.yaml`
2. Press `Alt + Shift + R` to reload
3. Test your changes

### If Reload Fails
1. Check for syntax errors in YAML (indentation matters!)
2. Look for error messages in GlazeWM logs
3. Restart GlazeWM completely

### Common Mistakes

#### Incorrect YAML Indentation
```yaml
# WRONG
window_effects:
focused_window:
  border:
  enabled: true

# CORRECT
window_effects:
  focused_window:
    border:
      enabled: true
```

#### Missing Quotes
```yaml
# WRONG - needs quotes for hex colors
color: #8dbcff

# CORRECT
color: '#8dbcff'
```

#### Invalid Key Names
```yaml
# WRONG - 'option' is not a valid key name
- commands: ['close']
  option: ['alt+q']

# CORRECT
- commands: ['close']
  bindings: ['alt+q']
```

---

## Example: Complete Custom Configuration

Here's a sample customization combining multiple changes:

```yaml
# Use Windows key instead of Alt
# Larger gaps for visual breathing room
# Named workspaces
# Custom terminal (Windows Terminal)
# Transparent focused windows
# Nord color scheme for borders

general:
  startup_commands: ['shell-exec zebar', 'shell-exec rainmeter']
  focus_follows_cursor: true

gaps:
  inner_gap: '12px'
  outer_gap:
    top: '48px'
    right: '12px'
    bottom: '12px'
    left: '12px'

window_effects:
  focused_window:
    border:
      enabled: true
      color: '#88c0d0'  # Nord blue
    transparency:
      enabled: true
      opacity: '95%'
  other_windows:
    border:
      enabled: true
      color: '#4c566a'  # Nord gray

workspaces:
  - name: 'web'
  - name: 'code'
  - name: 'term'
  - name: 'chat'

keybindings:
  # Use Win key for navigation
  - commands: ['focus --direction left']
    bindings: ['win+h']

  # Launch Windows Terminal
  - commands: ['shell-exec wt']
    bindings: ['win+enter']

  # Focus named workspaces
  - commands: ['focus --workspace web']
    bindings: ['win+1']
```

---

## Additional Resources

- **GlazeWM Documentation**: [https://github.com/glzr-io/glazewm](https://github.com/glzr-io/glazewm)
- **GlazeWM Discord**: [https://discord.gg/ud6z3qjRvM](https://discord.gg/ud6z3qjRvM)
- **YAML Syntax Guide**: [https://yaml.org/](https://yaml.org/)
- **Example Configs**: [GlazeWM Examples](https://github.com/glzr-io/glazewm/tree/main/resources/assets/sample-config)

---

**Remember**: After any change, reload with `Alt + Shift + R` to test immediately!
