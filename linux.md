# Linux Notes
Useful linux commands and environment setup.

---

## tmux
tmux commands and configuration.

### set tmux color
```bash
echo 'set -g default-terminal "screen-256color"' >> ~/.tmux.conf
```

---

## Language Input

### install japanese input (fcitx)

```bash
# install fcitx
sudo apt install fcitx-mozc fcitx-config-gtk fcitx-imlist

# create/add to file
$ cat ~/.pam_environment 
XMODIFIERS DEFAULT=@im=fcitx
GTK_IM_MODULE DEFAULT=fcitx
QT_IM_MODULE DEFAULT=fcitx

# auto start
# for i3: add to ~/.config/i3/config file
exec --no-startup-id fcitx-autostart
# for gnome: add to 'Startup Application Preferences'
Name: Fcitx
Command: /usr/bin/fcitx-autostart
Comment: Start fcitx
```

### fcitx(mozc) shortcuts

| Command             | Shortcut     |
|:------------------- |:------------ |
| switch input        | ctrl + space |
| hiragana            | F6           |
| katakana            | F7           |
| half-width katakana | F8           |

---

## Unsorted
Yet to be sorted...

### volume control (for keybinding)
```bash
# increase volume
amixer -D pulse -R sset Master 3277+
# decrease volume
amixer -D pulse -R sset Master 3277-
# toggle mute
amixer -D pulse sset Master toggle
```
