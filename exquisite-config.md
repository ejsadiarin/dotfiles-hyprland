# Userprefs Hyprland config

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



----------------------------------------------------------------------------
## Details:
- monitor change to 1920x1080@60
- commented: changed path where to save screenshots (commented out the official hyprland.conf, can lead to conflicts)
  - FIXED by overriding it in `userprefs.conf`
- Waybar config:
  - just change height in `config.ctl` (second slot in |)
    - where `|` is the delimiter and column,
      1. is `0` or `1`, where `1` indicates the current mode in use
      2. is to set height of the bar (use `0` for default min height or `<blank>` to auto-scale for 3% of monitor res)
      3. is postition of bar top/bottom
      4. is the left modules
      5. is the center modules
      6. is the right modules
  - add a waybar theme or new layout in `config.ctl`
- use this layout in `config.ctl`: 
```
1|37|top|( wlr/workspaces hyprland/window )|( clock )|( cpu memory battery ) ( network bluetooth pulseaudio pulseaudio#microphone custom/updates ) ( tray ) ( custom/wallchange custom/mode custom/wbar custom/cliphist custom/power )
```

## Useful commands
- df -h --> check disk space
- acpi -V --> check battery
- paccache -r --> removes pacman cache and retains last 3 package verions
  - paccache -d --> dryrun, find candidate packages before removing them
- sudo ufw enable --> enable firewall
- nmcli device wifi list --> check wifi connections
  - nmcli device wifi connect "wifi_name" password "password"
    - can remove password parameter if there is no password
- CHECK battery health:
  - ls /sys/class/power_supply/BAT0 --> list battery
  - cat /sys/class/power_supply/BAT0/charge_full --> print current battery health capacity when full
  - cat /sys/class/power_supply/BAT0/charge_full_design --> print the original battery health capacity (its designed to be)
  - if the numbers are close to each other then battery health is GREAT
- systemctl --> check system active
- xinput --> check input devices

## Flatpak things
- Discord:
  - Rich presence isn't enabled by default with Flatpak, to enable run:
  `ln -sf {app/com.discordapp.Discord,$XDG_RUNTIME_DIR}/discord-ipc-0`

# Fonts (Nerd Fonts)
- run `fc-list` -> to check currently installed fonts
- Install the following fonts:
  - JetBrainsMono Nerd Font
  - CascadiaCove
  - MapleMono
  - MaterialDesign
    - MaterialDesignIcons.ttf
  - Mononoki
- extract to `~/.local/share/fonts/` -> can use unzip cli
- cd to `~/.local/share/fonts/` -> to check fonts folder
- then run fc-cache -fv -> to install downloaded fonts

# Waybar (Status Bar) Additions
- Battery module:
  - in battery.jsonc (in hypr modules directory):
    - manually added bat and interval properities (as of 2023-07-22: might be fixed soon as well as showing battery support natively in future updates)
  - add battery in `config.ctl`



  https://github.com/csharpfritz/csharp_with_csharpfritz/tree/main/sessions
  https://github.com/Jacksaur/Gorgeous-GRUB
  https://www.pling.com/p/1420727/
  https://github.com/ejsadiarin/exercise-tracker-app

# Firefox CSS
- enable options in about:config (see specifics here):
https://github.com/Aris-t2/CustomCSSforFx
- remote-debugging: ctrl shift alt i -> see firefox css tags


-----------------------------------------------------------------------------
# --- IGNORE THIS ----

### Monitor
Summary:
- I want the preferred 1920x1080@60 setting (~/.config/hypr/userprefs.conf): `monitor = eDP-1, 1920x1080@60, 0x0, 1` 

- mostly about scaling issues
- all about UI problems (all the functionality works as intended)
- specific problems on `monitor = eDP-1, 1920x1080@60, 0x0, 1`: 
  - some apps are very "far away" (tolerable, but for waybar it makes it unreadable)
  - waybar small size making it unreadable,
  - theme-switch UI (super shift t),
  - wlogout is not on center, overlapping text

## Details:
- most bearable config for 1920x1080 resolution (single screen):
`monitor = eDP-1, 1920x1080@60, 0x0, 1.2` (not preferred, since it causes blur issues on apps that can only be solved by setting the scale to 1)
- preferred setting should be: `monitor = eDP-1, 1920x1080@60, 0x0, 1`

### scale of `1.2` results to:
- theme-switch (super shift t) pictures is not showing (its just a blank slate, but the functionality works)
- waybar is small (but more readable than when scale is `1`)
- rofi shows icons
- wlogout is not on the center
  - overlapping text and icons (same as when scale is `1`)
- flatpak apps like discord is "blurry"

### scale of `1` (classic 1920x1080 display, preferred) results to:
- rofi doesn't show left icons
  - text is not fully showing
  - very "near"
- waybar is very small (unreadable)
- wlogout is not on the center
  - overlapping text and icons
  - doesn't look great for smaller resolution displays
- theme-swtich is showing but the text is cut out (shows "...")
- flatpak apps like discord works as intended (not blurry, highres)

