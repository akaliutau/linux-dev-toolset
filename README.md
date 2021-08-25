# About

This repository contains references to useful dev instruments and recipes for performance tuning up of linux.

As an example I am using Ubuntu 20.04 LTS

# Before installation

Check out UEFI settings on your laptop/desktop computer - USB installation media created from linux bootable iso image must be in appropriate format, 
overwise it either does not boot or will fail to install grub loader after

For example, when using [Rufus](https://rufus.ie/) for UEFI-compatible system, choose UEFI (non CSM) option.


# After fresh installation

## Install new themes:

1. Find a theme you want to use on your system, f.e. [GTK3/4 Themes](https://www.opendesktop.org/s/Gnome/browse?cat=135&ord=latest)
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
sudo apt update
sudo apt install gnome-tweak-tool
gnome-tweaks
```

6. Select the Appearance tab and choose the installed theme.


## Turn off animations and special effects for GUI (will increase performance by 2-5%)

Install extra features to tweak effects:

```
sudo apt update
sudo apt install gnome-tweaks
gnome-tweaks
```

Will be available under Appearance tab


# Minimal dev toolkit

For backend development it should be like this:

* Git

```
sudo apt update
sudo apt install git
git --version
```

* JDK
To install Openjdk 11 in Ubuntu, the following commands should work:

```
sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt-get update
sudo apt install openjdk-11-jdk
```

* Maven

```
sudo apt update
sudo apt install maven
mvn -version
```

* Python

```
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt install python3.9
python --version
```

* Docker

1. First, Uninstall old versions. Older versions of Docker were called docker, docker.io, or docker-engine

```
sudo apt-get remove docker docker-engine docker.io containerd runc
```

2. Update the apt package index and install packages to allow apt to use a repository over HTTPS:

```
sudo apt-get update
sudo apt-get install apt-transport-https  ca-certificates curl gnupg lsb-release
```
	
3. Add Docker’s official GPG key:

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

4. Use the following command to set up the stable repository. To add the nightly or test repository, add the word nightly or test (or both) after the word stable in the commands below.

```
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

5. Install engine

```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

testing:

```
sudo docker run hello-world
sudo docker ps
```


# Web

* Chrome

```
sudo apt install wget
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

Setup alternative browser like SlimJet:

Download a package manually from https://www.slimjet.com/en/postdl.php?version=lnx64&type=deb, and install it:

```
sudo apt install ./slimjet_amd64.deb
```

* Curl

```
sudo apt update
sudo apt install curl
curl --version
```

* OpenVPN

```
sudo apt-get -y install network-manager-openvpn
sudo service network-manager restart
```

After installation condifure the VPN-connection.

1. Go to settings -> network -> add VPN
2. Choose a saved VPN configuration in a .ovpn file

# Dev tools

* [Eclipse](https://www.eclipse.org/downloads/)
* [PyCharm](https://www.jetbrains.com/pycharm/download/#section=linux)

# Data science

* Anaconda

1. Check the developer’s download page to view the newest version. Let's say it's 2020.02

```
cd /tmp
curl -O https://repo.anaconda.com/archive/Anaconda3-2020.02-Linux-x86_64.sh
sha256sum Anaconda3-2020.02-Linux-x86_64.sh
```

The Anaconda installer is a bash script. To run the installation script, use the command:

```
bash Anaconda3-2020.02-Linux-x86_64.sh
```

# Text editors

* Sublime

Add the official Sublime Text repository:

```
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
```

Installing package:

```
sudo apt update
sudo apt install sublime-text
```

* Geany

```
sudo apt-get update -y
sudo apt-get install -y geany
```


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

set default settings for mpv in /etc/mpv/mpv.conf

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

Download the DEB installer file from [Download Center](https://zoom.us/download?os=linux)

```
sudo apt update
sudo apt install ./zoom_amd64.deb
```


# VCS related

* Meld

```
sudo apt update
sudo apt install meld
```

# Uninstalling packages

```
sudo apt-get remove package_name
sudo apt-get purge package_name
sudo apt-get autoremove
sudo apt-get clean
``` 

