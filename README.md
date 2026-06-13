# My I3 Dotfiles

Arch Linux i3 dotfiles with niri-style keybindings.

## About

These dotfiles are built around **i3wm** with keybindings ported from **niri** (scrollable-tiling window manager). The config provides a familiar niri experience using i3 underneath.

Inspired by [Keyitdev/dotfiles](https://github.com/Keyitdev/dotfiles).

## Files

```
.
├── home
│   ├── .config
│   │   ├── i3
│   │   │   └── config
│   │   ├── polybar
│   │   │   ├── colors.ini
│   │   │   ├── config.ini
│   │   │   └── launch.sh
│   │   └── rofi
│   │       ├── colors.rasi
│   │       ├── dmenu.rasi
│   │       ├── main.rasi
│   │       └── main_without_icons.rasi
│   ├── Pictures
│   │   └── Wallpapers
│   │       └── background.jpg
│   └── .local
│       ├── bin
│       │   ├── lock              # i3lock-color with blurred wallpaper
│       │   ├── rofi-powermenu    # Shutdown, reboot, lock, logout, suspend
│       │   └── screenshot        # Fullscreen & area screenshot script
│       └── share
│           └── fonts
│               └── Feather.ttf
```

## Installation (fresh Arch)

### 1. Install yay (AUR helper)

```sh
sudo pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay-bin.git /tmp/yay && cd /tmp/yay && makepkg -si
```

### 2. Install packages

```sh
# pacman packages
sudo pacman -S --needed i3-wm polybar rofi feh nautilus kitty slop xclip ttf-opensans ttf-iosevka-nerd picom xorg-xrandr xorg-xsetroot

# AUR packages
yay -S --needed i3lock-color ffcast
```

### 3. Clone and copy files

```sh
git clone https://github.com/<your-user>/My-I3-Dotfiles.git
cp -ri My-I3-Dotfiles/home/. ~/
```

### 4. Install Feather font

```sh
fc-cache -fv
```

### 5. Fix i3lock-color authentication (PAM)

i3lock-color may not accept your password on Arch. Fix:

```sh
sudo sed -i 's/system-local-login/system-auth/' /etc/pam.d/i3lock
```

### 6. Reload i3 config

Press `$mod+Shift+c` (or `Super+Shift+c`) inside i3.

### 7. Set wallpaper

```sh
feh --bg-fill ~/Pictures/Wallpapers/background.jpg
```
Add `exec feh --bg-fill ~/Pictures/Wallpapers/background.jpg` to your i3 config if you want it on every login.

### Additional notes

- **Picom**: If enabled, picom may draw a shadow/underline below the polybar. Press `Ctrl+F4` to toggle picom, or configure picom to exclude polybar from shadows.
- **Network**: The wireless module uses `wlp0s20f3` — change it in `~/.config/polybar/config.ini` if your interface is different (`ip link` to check).
- **Backlight**: Uses `intel_backlight` — change in polybar config if you have a different GPU.
- **Battery**: Uses `BAT0` / `AC` — adjust in polybar config if needed.

## Keybindings

| Key | Action |
|---|---|---|
| `Mod + Return` | Terminal |
| `Mod + Space` | App launcher (rofi) |
| `Mod + B` | Firefox |
| `Mod + E` | Nautilus |
| `Mod + Q` | Kill window |
| `Mod + F` | Toggle fullscreen |
| `Mod + H` / `J` / `K` / `L` | Focus left / down / up / right |
| `Mod + Shift + H` / `J` / `K` / `L` | Move window left / down / up / right |
| `Mod + W` | Tabbed layout |
| `Mod + U` / `Mod + I` | Workspace prev / next |
| `Mod + Tab` | Previous workspace |
| `Mod + Alt + L` | Lock screen |
| `Mod + Shift + S` | Area screenshot |
| `Mod + X` | Power menu |
| `Mod + Shift + E` | Exit i3 |
| `Mod + Shift + C` | Reload config |
| `Print` | Full screenshot |
| `Pause` | Area screenshot |

## Color Palette

| Bg | Bg 2 | Border | Fg | Gray |
|:---:|:----:|:------:|:--:|:----:|
| `#1b1b25` | `#282A36` | `#343746` | `#dedede` | `#727480` |
| ![#1b1b25](https://placehold.co/60x15/1b1b25/1b1b25.png) | ![#282A36](https://placehold.co/60x15/282A36/282A36.png) | ![#343746](https://placehold.co/60x15/343746/343746.png) | ![#dedede](https://placehold.co/60x15/dedede/dedede.png) | ![#727480](https://placehold.co/60x15/727480/727480.png) |

| Red | Green | Yellow | Blue | Purple | Cyan | Orange |
|:---:|:-----:|:------:|:----:|:------:|:----:|:------:|
| `#cb5760` | `#999f63` | `#d4a067` | `#6c90a8` | `#776690` | `#528a9b` | `#c87c3e` |
| ![#cb5760](https://placehold.co/60x15/cb5760/cb5760.png) | ![#999f63](https://placehold.co/60x15/999f63/999f63.png) | ![#d4a067](https://placehold.co/60x15/d4a067/d4a067.png) | ![#6c90a8](https://placehold.co/60x15/6c90a8/6c90a8.png) | ![#776690](https://placehold.co/60x15/776690/776690.png) | ![#528a9b](https://placehold.co/60x15/528a9b/528a9b.png) | ![#c87c3e](https://placehold.co/60x15/c87c3e/c87c3e.png) |

## Dependencies

- `i3-wm` — window manager
- `polybar` — status bar
- `rofi` — app launcher & powermenu
- `i3lock-color` — lock screen (AUR)
- `feh` — wallpaper setter
- `nautilus` — file manager
- `kitty` — terminal
- `slop`, `xclip`, `ffcast` — screenshots (AUR)
- `picom` — compositor
- `xorg-xrandr` — display resolution detection (needed by lock script)
- `xorg-xsetroot` — reset cursor after unlock
- `ttf-opensans`, `ttf-iosevka-nerd` — fonts
