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


# solving bluetooth issue on dual system

  1. Pair with the device in linux 
  
  2. Reboot 
  
  3. Pair with the device in windows 
  
  4. Extract the link key 
  
  5. Turn off the BlueTooth device and reboot into linux 
  
Make sure to have your device turned off when booting linux.

Otherwise it will try to connect to the device repeatedly with the old (and now invalid) link key. This might trigger anti brute-forcing measures rendering the device unreachable.

Go to the subfolder that is named after the device's address. You should find a file named 'info' there. 

```
sudo nano /var/lib/bluetooth/XX:XX:XX:XX:XX:XX/YY:YY:YY:YY:YY:YY/info
```

In the [LinkKey] section set the Key. Example:
Key=3E717C5B8735C1984B71636D7B941DEE

Now check the [General] section and set
Trusted=false

Save, and restart bluetoothd:

```
sudo service bluetooth restart
```

Obtaining key (option 1):

When you turn on the device, a popup should appear, asking if you want to authorize the connecting bluetooth device.

Swithch off mouse before starting Windows and do not reconnect. The finger/touch pad will be the only means to proceed.

1. Login with normal user password

2. Search for regedit

3. In the result left click to enable administrator rights.

4. Go to HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\BTHPORT\Parameters\keys\computer MAC\device MAC

Obtaining key (option 2):

Some devices may have a different set of hives at different locations (see the slide\bluetooth.png):

The first number is the MAC address of the Bluetooth adapter, which can also be written in standard format as 

d2:2e:73:48:17:09

And the second  number is the mouse address that was assigned during the pairing. We will need those numbers in the next steps.

98:2c:bc:72:bd:a6

Now boot again to Linux. The mouse wont paired automatically, because it is now assigned to a different address and with different keys. Let's fix it.

$ cd /var/lib/bluetooth/d2:2e:73:48:17:09/
$ ls
cache 84:AB:D4:A2:5F:E1 settings
If you look closely, the mouse address is not the same as in Windows. In this case each group is different. We need the device addresses to match, so rename the file.



Settings on Linux side:

1. Switch to root: su -

2. cd to your Bluetooth config location /var/lib/bluetooth/[bth port MAC addresses]

3. Here you'll find folders for each device you've paired with. The folder names being the Bluetooth devices MAC addresses and contain a single file info. In these files, you'll see the link key you need to replace with your Windows ones, like so:

```
[LinkKey]
Key=B99999999FFFFFFFFF999999999FFFFF
```

5. Once updated, restart your Bluetooth service in one of the following ways. 

Here is an example of Windows' registry section for the paired mouse
```
[General]
Name=Logitech Pebble
Appearance=0x03c2
AddressType=static
SupportedTechnologies=LE;
Trusted=true
Blocked=false
Services=00001800-0000-1000-8000-00805f9b34fb;00001801-0000-1000-8000-00805f9b34fb;0000180a-0000-1000-8000-00805f9b34fb;0000180f-0000-1000-8000-00805f9b34fb;00001812-0000-1000-8000-00805f9b34fb;00010000-0000-1000-8000-011f2000046d;

[ConnectionParameters]
MinInterval=6
MaxInterval=9
Latency=44
Timeout=216

[IdentityResolvingKey]
Key=211FC2ACCCE247ECD292D87B332CA7DA

[LongTermKey]
Key=6ED9D0EDA63EF1623EFA7EDABB1BA188
Authenticated=0
EncSize=16
EDiv=21050
Rand=13897211094044290655

[DeviceID]
Source=2
Vendor=1133
Product=45089
Version=7
```



