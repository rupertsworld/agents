# System

Rupert's local machine setup. macOS (Darwin).

## System repo

`~/Repos/system` — manages system configs (ghostty, cron, obsidian, shell) via symlinked install scripts. Each component has its own directory with a `config` and `install.ts`. Top-level `install.ts` runs all components.

```
npm run install      # install everything
npm run uninstall    # remove all symlinks
```

## Terminal — Ghostty

Config: `~/Repos/system/ghostty/config` → symlinked to `~/.config/ghostty/config`

- Black background (`background = 000000`)
- macOS titlebar style: tabs (`macos-titlebar-style = tabs`)
- Window size: 90×38
- Quick terminal: center position, toggled with `Ctrl+/` (global keybind)

### Quick terminal options

| Option | Values | Notes |
|--------|--------|-------|
| `quick-terminal-position` | `top`, `bottom`, `left`, `right`, `center` | Where it appears |
| `quick-terminal-size` | e.g. `50%`, `300px` | One or two axes (v1.2.0+) |
| `quick-terminal-screen` | `main`, `mouse`, `macos-menu-bar` | Which monitor (macOS) |
| `quick-terminal-animation-duration` | seconds (0 = off) | macOS only |
| `quick-terminal-autohide` | `true`/`false` | Hide on focus loss |
| `quick-terminal-space-behavior` | `move`, `remain` | macOS spaces behavior |

### Rounded corners (as of early 2025)

Not yet in stable config reference. Two approaches under discussion:

1. `quick-terminal-corner-radius` — manual corner masking (PR #9960)
2. `quick-terminal-decoration` — native macOS window decoration (OS-level rounded corners)

Workaround: `macos-titlebar-style = hidden` keeps native window frame (including rounded corners) while hiding title bar content.

Status: https://github.com/ghostty-org/ghostty/discussions/8666
