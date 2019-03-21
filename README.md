# Linux Notes
Useful linux commands and environment setup.

---

Base applications

```bash
sudo apt install -y tmux git tig tmux cmake taskwarrior
```

---

## i3 Window Manager

Install [i3 window manager](https://i3wm.org/). This [video](https://youtu.be/j1I63wGcvU4) shows a good introduction to the installation and basic features of i3. There is also a [handy reference card](https://i3wm.org/docs/refcard.html).

```bash
sudo apt install i3
```

disable 'ctrl + d' exit on terminal. ('mod + d' is so close to it...XD)
```bash
# add 
set -o set -o ignoreeof
```

add startup applications to  ~/.config/i3/config file
```bash
# language input
exec --no-startup-id fcitx-autostart
# for gnome systems
exec --no-startup-id gnome-settings-daemon
# network manager applet
exec --no-startup-id nm-applet
```

custom script to lock|logout|suspend|hibernate|reboot|shutdown
```bash
# cp i3/i3exit ${HOME}/.local/bin/
i3exit (lock|logout|suspend|hibernate|reboot|shutdown)

# use i3exit script
set $mode_system System (l) lock, (e) logout, (s) suspend, (h) hibernate, (r) reboot, (Shift+s) shutdown
mode "$mode_system" {
    bindsym l exec --no-startup-id i3exit lock, mode "default"
    bindsym e exec --no-startup-id i3exit logout, mode "default"
    bindsym s exec --no-startup-id i3exit suspend, mode "default"
    bindsym h exec --no-startup-id i3exit hibernate, mode "default"
    bindsym r exec --no-startup-id i3exit reboot, mode "default"
    bindsym Shift+s exec --no-startup-id i3exit shutdown, mode "default"

    # back to normal: Enter or Escape
    bindsym Return mode "default"
    bindsym Escape mode "default"
}
bindsym $mod+x mode "$mode_system"
```

audio control

```bash
# Based from https://faq.i3wm.org/question/3747/enabling-multimedia-keys/?answer=3759#post-id-3759
# audio controls
bindsym XF86AudioRaiseVolume exec --no-startup-id amixer -D pulse -R sset Master 3277+ # increase volume
bindsym XF86AudioLowerVolume exec --no-startup-id amixer -D pulse -R sset Master 3277- #decrease volume
bindsym XF86AudioMute exec --no-startup-id amixer -D pulse sset Master toggle # toggle mute
```

wallpaper

```bash
# install feh
sudo apt install feh

# i3 config
exec_always --no-startup-id feh --bg-scale [/path/to/image.extenstion]
```

multiple display settings

```bash
#install arandr
sudo apt install arandr

# run application, then save settings (that contains xrandr command with arguments) and add to i3 config file using exec_always
arandr
```

rename workspaces

```bash
# set a variable for the workspace names in i3 config
set $ws1 "1"
```

assign to workspace

```bash
# add the lines below to i3 config
# the class name can be known using 'xprop'
assign [class="Google-chrome"] $ws1
assign [class="Gnome-terminal"] $ws2
```

auto start applications on workspaces
```bash
exec --no-startup-id i3-msg "workspace $ws1; exec /usr/bin/google-chrome"
exec --no-startup-id i3-msg "workspace $ws2; exec /usr/bin/gnome-terminal"
exec --no-startup-id i3-msg "workspace $ws3; exec /usr/bin/code"
```

launch a working gnome-control-center

```bash
# add the script to ${HOME}/.local/bin
env XDG_CURRENT_DESKTOP=GNOME gnome-control-center
```

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
