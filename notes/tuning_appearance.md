# Change the login screen background (Ubuntu 20.04 only).

## Approach 1

'scripts/gdm3' can be used to change the login screen background.

1. Install libglib2 package with the command

```
sudo apt-get update
sudo apt install libglib2.0-dev
```

2. Set chmod +x for the script scripts/gdm3.


To set the background made from some image:

```
sudo ./gdm3 /absolute/path/to/image
```

To set the background with color(replace `#RRGGBB` with any vaid hex color code): 

```
sudo ./gdm3 \#RRGGBB
```


to reset everything that the script
  
```
sudo ./gdm3 --reset
```

## Approach 2 (hack)

```
sudo cp ~/Desktop/mybackground.png /usr/share/backgrounds
xhost +local: && sudo nautilus /usr/share/backgrounds/
xhost +local: && sudo gedit /etc/alternatives/gdm3.css
```

Update the following line:

```
#lockDialogGroup{
	background: url(file:///usr/share/backgrounds/mybackground.png); 
	background-repeat: no-repeat;
	...
	}
```
