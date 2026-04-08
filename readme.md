<img src="https://raw.githubusercontent.com/cybrcore/cybrcore/refs/heads/main/assets/repo-banners/cybr-rofi-banner.png" height=200px/>

# Showcase
<img src="https://raw.githubusercontent.com/cybrcore/cybrcore/refs/heads/main/assets/showcase/cybr-rofi.png"/>
<p align="center">
  <em>rofi ↗ (top-left to bottom-right: launcher, clipboard, emoji; powermenu, screenshot menu, wallpaper switcher)</em>
</p>

> ![WARNING]
> For Wallpaper switcher to work as intended, you need latest hyprpaper.  
> `CTRL + SUPER + W` launches the Wallpaper switcher, `ENTER` confirms the selection.
> If the selected wallpaper gets stuck, you can reset the timer by repeatedly selecting the wallpaper again.

# Steps
## 0. Before you start
- Make sure [Geist Mono Nerd Font](https://www.nerdfonts.com/font-downloads) is installed, you can do that from terminal with:
```bash
curl -L https://github.com/ryanoasis/nerd-fonts/releases/latest/download/GeistMono.zip -o GeistMono.zip
mkdir -p ~/.local/share/fonts
unzip GeistMono.zip -d ~/.local/share/fonts/GeistMono
fc-cache -fv
```
- Make sure hyprland is installed: `sudo pacman -S hyprland` and [cybrcore theme](https://github.com/cybrcore/cybrland) is applied
- Make sure swaync is installed: `sudo pacman -S swaync`
- See [Installation Guide](../INSTALL.md) if you haven't set up prerequisites yet
- [rofi Github](https://github.com/davatorium/rofi) | [Arch Wiki](https://wiki.archlinux.org/title/Rofi)

## 1. Download rofi configs
```sh
git clone --depth=1 --filter=blob:none --no-checkout https://github.com/cybrcore/cybr-rofi.git && cd cybr-rofi && git sparse-checkout init --cone && git sparse-checkout set rofi && git checkout main && mv rofi ~/.config/ && cd ~ && rm -rf cybr-rofi
```
↑ Unsure what this does? [Explanation](https://github.com/cybrcore/cybrland/blob/main/INSTALL.md#How-sparse-checkout-works)  

## 2. Verify installation
```sh
ls -R ~/.config/rofi
```
You should see: `config.rasi`, `launcher.rasi`, `style.rasi`, `theme/`, `scripts/`

Make all scripts executable:
```sh
chmod +x \
  ~/.config/rofi/scripts/clipboard/clipboard \
  ~/.config/rofi/scripts/emoji/emoji \
  ~/.config/rofi/scripts/keybindings/keybindings \
  ~/.config/rofi/scripts/powermenu/powermenu \
  ~/.config/rofi/scripts/screenshot/screenshot \
  ~/.config/rofi/scripts/screenshot/screenshot_selection \
  ~/.config/rofi/scripts/wallpaper/wallpaper \
```

<details>
<summary>Expected file structure</summary>

```
~/.config/rofi/
├── config.rasi             # main settings
├── style.rasi              # visual styling
├── theme/
│   └── cybrcore.rasi       # global style settings
└── scripts/                # graphical elements
    ├── clipboard
	│   ├── clipboard
	│   └── style.rasi
    ├── emoji
	│   ├── emoji
	│   └── style.rasi
	├── game-launcher
	│   └── style.rasi
	├── keybindings
	│   └── keybindings
	├── powermenu
	│   ├── powermenu
	│   └── style.rasi
	├── screenshot
	│   ├── screenshot
	│   ├── screenshot_selection
	│   ├── screenshot-style.rasi
	│   └── style.rasi
	└── wallpaper
	    ├── style.rasi
        └── wallpaper

```
</details>

## 3. Test notifications
```sh
notify-send "Notification" "Basic notification body text, medium length"
notify-send -u low "Low priority" "Priority: Low"
notify-send -u normal "Normal priority" "Priority: Normal"
notify-send -u critical "Critical" "Critical notification!"
```