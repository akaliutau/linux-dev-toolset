# Slow WiFi on the latest Ubuntu 20.04 LTS

1. Turn off wifi power management: open the file with power saving configuration for OS:

```
sudo gedit /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

and change the following line (or add the secton if not present):

```
[connection]
wifi.powersave = 2
```

2. Remove package `backport-iwlwifi-dkms` if installed, due to [bug](https://bugs.launchpad.net/ubuntu/+source/backport-iwlwifi-dkms/+bug/1869588):

```
sudo apt purge backport-iwlwifi-dkms
```

3. This could be an IPv6 related problem. If true then disable IPv6 with

```
sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
sudo sysctl -w net.ipv6.conf.default.disable_ipv6=1
```

4. Save and reboot

# Poor quality of sound for Bang and Olufsen Audio subsystem

install alsa and alsa-tools package :

```
sudo apt-get install -y alsa alsa-tools
```
 then
 
```
printf '#!/bin/bash
hda-verb /dev/snd/hwC0D0 0x20 SET_COEF_INDEX 0x67
hda-verb /dev/snd/hwC0D0 0x20 SET_PROC_COEF 0x3000
' > sound-script.sh
```

``` 
sudo chmod +x ./sound-script.sh && sudo ./sound-script.sh
```

To auro-run script:

```
sudo mv ./sound-script.sh /lib/systemd/system-sleep/
```

and add this script as a job:

```
sudo crontab -e
@reboot /lib/systemd/system-sleep/sound-script.sh
```


