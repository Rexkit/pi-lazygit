# pi-lazygit

A [Pi](https://pi.dev) package that opens [Lazygit](https://github.com/jesseduffield/lazygit) directly inside Pi as a floating overlay window.

## Features

- `/lazygit` slash command in Pi.
- Real pseudo-terminal via `@homebridge/node-pty-prebuilt-multiarch`.
- Lazygit screen rendering inside a Pi overlay using `@xterm/headless`.
- Automatic resize when the Pi terminal/overlay size changes.
- Optional keyboard shortcut through `PI_LAZYGIT_SHORTCUT`.

## Requirements

- Node.js `>=20 <25`.
- Pi interactive TUI mode.
- `lazygit` installed and available on `PATH`.

Install Lazygit with your platform package manager, for example:

```bash
# macOS
brew install lazygit

# Arch Linux
sudo pacman -S lazygit

# Ubuntu/Debian users can follow Lazygit's official install docs:
# https://github.com/jesseduffield/lazygit#installation
```

## Installation

From npm, once released:

```bash
pi install npm:@rexkit/pi-lazygit
```

From GitHub:

```bash
pi install git:github.com/Rexkit/pi-lazygit
```

For local development from this checkout:

```bash
npm install
pi -e .
```

## Usage

Inside Pi, run:

```text
/lazygit
```

Pass Lazygit arguments after the command when needed:

```text
/lazygit --path ./packages/app
```

Key handling:

- Use Lazygit's normal keybindings inside the overlay.
- Press `q` to quit Lazygit normally.
- Press `Ctrl+Q` to force-close the overlay/process if Lazygit is stuck.

## Configuration

Environment variables:

| Variable                | Default   | Description                                                   |
| ----------------------- | --------- | ------------------------------------------------------------- |
| `PI_LAZYGIT_COMMAND`    | `lazygit` | Binary/command to run. Useful for wrappers.                   |
| `PI_LAZYGIT_WIDTH`      | `90%`     | Overlay width. Accepts a number of columns or a percentage.   |
| `PI_LAZYGIT_MAX_HEIGHT` | `90%`     | Overlay max height. Accepts a number of rows or a percentage. |
| `PI_LAZYGIT_MIN_WIDTH`  | `60`      | Minimum overlay width in columns.                             |
| `PI_LAZYGIT_MIN_ROWS`   | `10`      | Minimum Lazygit pseudo-terminal rows.                         |
| `PI_LAZYGIT_MAX_ROWS`   | `45`      | Maximum Lazygit pseudo-terminal rows.                         |
| `PI_LAZYGIT_SHORTCUT`   | unset     | Optional Pi shortcut, for example `ctrl+g`.                   |

Example:

```bash
PI_LAZYGIT_SHORTCUT=ctrl+g pi -e .
```

Then press `Ctrl+G` in Pi to open Lazygit.

## Development

```bash
npm install
npm run lint
npm run build
npm run format
```

## License

MIT
