# Installing Eclipse

1. Go to the link below to download the installer.

https://www.eclipse.org/downloads/

After downloading, continue below to extract the downloaded file and install.

Run the commands below to extract the downloaded file in your Downloads folder of your Home directory.

```
cd ~
tar xfz ~/Downloads/eclipse-inst-linux64.tar.gz
~/Downloads/eclipse-installer/eclipse-inst
```

The last command will start GUI installer.

2. Choose the tools and language you wish to be developing in. Accept the licensing terms and choose the default installation folder.
Once downloaded and installed, click the Launch button to start the program.

3. To create a desktop icon to launch the program, run the commands below to create a simple desktop icon for Eclipse.

```
gedit ~/.local/share/applications/eclipse.desktop
```

Next, copy and paste the content below into the file and save

```
[Desktop Entry]
Name=Eclipse Eclipse
Type=Application
Exec=/<installation dir>/eclipse/eclipse
Terminal=false
Icon=/<installation dir>/eclipse/icon.xpm
Comment=Eclipse IDE
NoDisplay=false
Categories=Development;IDE;
Name[en]=Eclipse
```

```
chmod +x ~/.local/share/applications/eclipse.desktop
```
