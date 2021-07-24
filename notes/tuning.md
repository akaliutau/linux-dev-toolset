# solving the bluetooth mouse issue:

* an occasional lag of around 0.5 seconds where the pointer completely stopped moving,
* the mouse pointer generally became much more fluid, there were many micro-stutters before.

```
echo "options iwlwifi bt_coex_active=0" | sudo tee /etc/modprobe.d/iwlopt.conf
```

```
sudo nano /etc/default/grub
```

Completely replace line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
```

With:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash btusb.enable_autosuspend=n usbcore.autosuspend=-1 usbcore.autosuspend_delay_ms=-1"
```

Type

```
sudo nano /etc/bluetooth/input.conf
```
and set idleTimeout=0

# removing useless applications:

```
sudo apt remove aisleriot gnome-mahjongg gnome-mines gnome-sudoku
```


