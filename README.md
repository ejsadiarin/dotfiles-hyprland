# Userprefs Hyprland config
- more details on `exquisite-config.md`

## Checklist:

install this Dots with its install script:
https://github.com/prasanthrangan/hyprdots

### Hyprland configs
Simply copy and paste own conf `userprefs.conf`
contains:
- Monitor change
- Change Path to screenshots
- Night light bind and exec (using wl-gammarelay)
  - Install wl-gammarelay via AUR: `yay -S wl-gammarelay`

### Waybar configs
- Add battery module in waybar (in `config.ctl`)
  - also change the height for readable font size (in second |)
  - this waybar layout config:
  ```
  1|37|top|( wlr/workspaces hyprland/window )|( clock )|( cpu memory battery ) ( network bluetooth pulseaudio pulseaudio#microphone custom/updates ) ( tray ) ( custom/wallchange custom/mode custom/wbar custom/cliphist custom/power )
  ```

### Fonts
- Download fonts and `fc-cache -fv` it
- Use JetBrainsMono Nerd Font for everything configurable because it's exquisite

### Firefox
- Firefox Sync for account
- Firefox change homepage to nightTab with custom json file
  - Install nightTab extension
  - copy paste the json file for nightTab layout (in Data options import file or just copy paste)

### Developer Environment
VSCode:
- get own `settings.json` and `keybindings.json`

JetBrains (Rider, etc.):
- get own `.ideavimrc`

Neovim:
- Install via pacman
- Install LazyVim
- Clone own configs and move to config and plugins directory 


### Other essentials
Discord:
- Enable Discord rich presence with `ln -sf {app/com.discordapp.Discord,$XDG_RUNTIME_DIR}/discord-ipc-0`

Printer:
- CUPS

Battery Management:
- install auto-cpufreq (https://github.com/AdnanHodzic/auto-cpufreq)
- if have GPUs like Nvidia: install optimus-manager
- for maximum battery life:
  - set refresh rate to 60Hz
  - brightness to <=20%
