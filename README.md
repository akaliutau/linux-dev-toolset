# About

This repository contains references to useful dev instruments and recipes for performance tuning up of linux.

As an example I am using Ubuntu 20.04 LTS

# Before installation

Check out UEFI settings on your laptop/desktop computer - USB installation media created from linux bootable iso image must be in appropriate format, 
overwise it either does not boot or will fail to install grub loader after

For example, when using [Rufus](https://rufus.ie/) for UEFI-compatible system, choose UEFI (non CSM) option.


# After fresh installation

## Install new themes:

1. Find a theme you want to use on your system, f.e. [OpenDesktop.org](https://OpenDesktop.org)
2. Download a tar-archive with theme
3. When you find the file, use tar to unpack it f.e.

```
tar xJpf Dark-Theme-GTK_2.8.tar.xz
```

4. There are two places where you can move your theme folder. If you just want to install the theme for yourself, you can place it in your /home directory at ~/.local/share/themes.
   If you’d rather install the theme system-wide so everyone can use it, place the theme folder in /usr/share/themes.

The commands to copy it over looks like this:

```
cp -r ~/Downloads/Dark-Theme-GTK_2.8 ~/.local/share/themes/
sudo cp -r ~/Downloads/Dark-Theme-GTK_2.8 /usr/share/themes/
```

5. Open your desktop environment’s settings. Look for the Appearance/Themes option. If you’re on GNOME, you’ll need to install gnome-tweak-tool. Open a terminal and install it:

```
sudo apt install gnome-tweak-tool
```

6. Select the Appearance tab and choose the installed theme.


## Turn off animations and special effects for GUI (will increase performance by 2-5%)

Install extra features to tweak effects:

```
sudo apt install gnome-tweaks
```

Will be available under Appearance tab


# Minimal dev toolkit

For backend development it should be like this:

* Git
* Maven
* JDK
* Python

```
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt install python3.9
python --version
```

* Docker

# Web

* Chrome

```
sudo apt install wget
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

* Curl
* OpenVPN

# Dev tools

* Eclipse
* PyCharm

# Data science

* Anaconda

# Text editors

* Sublime
* Geany


# File managers

* Double Commander

```
sudo apt install doublecmd-qt
```

# Image managers

* Nomacs

```
sudo apt update
sudo apt install nomacs
```

# Multimedia

* mpv player

```
sudo apt install mpv
```

* ffmpeg

```
sudo apt update
sudo apt install ffmpeg
ffmpeg -version
```

* youtube-dl

```
sudo apt update
sudo apt-get install youtube-dl
```

* simple screen recorder (screen recorder)

```
sudo apt install simplescreenrecorder
```

# Messengers

* Skype

```
wget https://go.skype.com/skypeforlinux-64.deb
sudo apt install ./skypeforlinux-64.deb
sudo apt update
sudo apt upgrade
```

* Zoom


# VCS related

* Meld

```
sudo apt update
sudo apt install meld
```



 

