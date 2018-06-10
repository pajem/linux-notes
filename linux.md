# Linux Notes
Useful linux commands.

## Volume Control
```bash
# increase volume
$ amixer -D pulse -R sset Master 3277+
# decrease volume
$ amixer -D pulse -R sset Master 3277-
# toggle mute
$ amixer -D pulse sset Master toggle
```