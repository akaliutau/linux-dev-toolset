# Poor quality sound on HP notebooks running on the latest Ubuntu 20.04 LTS

1. Install pulseaudio

```
sudo apt install pulseaudio-equalizer
```

2. Add 2 lines to configuration: `sudo gedit /etc/pulse/default.pa`

```
load-module module-equalizer-sink
load-module module-dbus-protocol
```

3. reboot
