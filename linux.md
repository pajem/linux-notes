# Linux Notes
Useful linux commands and environment setup.

## tmux
tmux commands and configuration.

### set tmux color
```bash
echo 'set -g default-terminal "screen-256color"' >> ~/.tmux.conf
```

## Unsorted
Yet to be sorted...

### volume control (for keybinding)
```bash
# increase volume
$ amixer -D pulse -R sset Master 3277+
# decrease volume
$ amixer -D pulse -R sset Master 3277-
# toggle mute
$ amixer -D pulse sset Master toggle
```
